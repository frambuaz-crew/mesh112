# GitHub Projects GraphQL Setup

## Sorun
GitHub Projects V2 (yeni Projects), REST API yerine **GraphQL** kullanıyor.
Workflow'da issue'ları otomatik taşımak için GraphQL sorguları gerekiyor.

---

## Project ID ve Field ID Bulma

### 1. Project Global ID Bul

```bash
gh api graphql -f query='
{
  organization(login: "frambuaz-crew") {
    projectV2(number: 1) {
      id
      title
      fields(first: 20) {
        nodes {
          ... on ProjectV2SingleSelectField {
            id
            name
            options {
              id
              name
            }
          }
        }
      }
    }
  }
}'
```

**Çıktı**:
```json
{
  "data": {
    "organization": {
      "projectV2": {
        "id": "PVT_kwDONBqKD84ApEWz",  // ← PROJECT GLOBAL ID
        "title": "MESH112 Development",
        "fields": {
          "nodes": [
            {
              "id": "PVTSSF_lADONBqKD84ApEWzzgXXXXX",  // ← STATUS FIELD ID
              "name": "Status",
              "options": [
                { "id": "xxxx", "name": "Backlog" },
                { "id": "yyyy", "name": "To Do" },
                { "id": "zzzz", "name": "In Progress" },
                { "id": "aaaa", "name": "Review" },
                { "id": "bbbb", "name": "Ready to Test" },  // ← BUNU KULLAN
                { "id": "cccc", "name": "Done" }             // ← BUNU KULLAN
              ]
            }
          ]
        }
      }
    }
  }
}
```

---

## Workflow'a Eklenecek Gerçek Kodlar

Bu ID'leri aldıktan sonra workflow'u şöyle güncelle:

```yaml
- name: Move linked issues to Ready to Test
  if: |
    github.event.action == 'closed' && 
    github.event.pull_request.merged == true &&
    github.event.pull_request.base.ref == 'develop'
  uses: actions/github-script@v7
  with:
    github-token: ${{ secrets.PROJECT_TOKEN }}
    script: |
      // BURAYA YUKARIDAKI GRAPHQL SORGUSUNDAN GELEN ID'LERİ YAPIŞTIRACAKSIN
      const PROJECT_ID = 'PVT_kwDONBqKD84ApEWz';  // ← Gerçek ID'yi yaz
      const STATUS_FIELD_ID = 'PVTSSF_lADONBqKD84ApEWzzgXXXXX';  // ← Gerçek ID'yi yaz
      const READY_TO_TEST_OPTION_ID = 'bbbb';  // ← Gerçek ID'yi yaz
      
      const prBody = context.payload.pull_request.body || '';
      const issueRegex = /(?:close[sd]?|fix(?:e[sd])?|resolve[sd]?)\s+#(\d+)/gi;
      const issueNumbers = [...prBody.matchAll(issueRegex)].map(m => m[1]);
      
      for (const issueNum of issueNumbers) {
        // Issue'nun project item ID'sini bul
        const result = await github.graphql(`
          query {
            repository(owner: "${context.repo.owner}", name: "${context.repo.repo}") {
              issue(number: ${issueNum}) {
                projectItems(first: 10) {
                  nodes {
                    id
                    project {
                      id
                    }
                  }
                }
              }
            }
          }
        `);
        
        const projectItem = result.repository.issue.projectItems.nodes
          .find(item => item.project.id === PROJECT_ID);
        
        if (!projectItem) {
          core.warning(`Issue #${issueNum} not in project`);
          continue;
        }
        
        // Status'u Ready to Test'e değiştir
        await github.graphql(`
          mutation {
            updateProjectV2ItemFieldValue(input: {
              projectId: "${PROJECT_ID}"
              itemId: "${projectItem.id}"
              fieldId: "${STATUS_FIELD_ID}"
              value: { 
                singleSelectOptionId: "${READY_TO_TEST_OPTION_ID}"
              }
            }) {
              projectV2Item {
                id
              }
            }
          }
        `);
        
        core.info(`✅ Moved issue #${issueNum} to Ready to Test`);
      }
```

---

## Hızlı Çözüm (Şimdilik)

GraphQL ID'leri almak karmaşık. **Geçici çözüm**:

### Manuel Taşıma + Otomatik Comment

Workflow şu anda:
- ✅ PR merge edilince issue'ya comment atar
- 👉 Issue'yu **manuel** Ready to Test'e taşırsın
- ✅ main'e merge edilince issue'yu kapatır

**Bundan sonra**: GraphQL ID'lerini alıp tam otomasyonu ekleriz.

---

## ID'leri Bulma Komutu (GitHub CLI)

```bash
# GitHub CLI kur (eğer yoksa)
# https://cli.github.com/

# Login ol
gh auth login

# Project ID'leri bul
gh api graphql -f query='
{
  organization(login: "frambuaz-crew") {
    projectV2(number: 1) {
      id
      title
      fields(first: 20) {
        nodes {
          ... on ProjectV2Field {
            id
            name
          }
          ... on ProjectV2SingleSelectField {
            id
            name
            options {
              id
              name
            }
          }
        }
      }
    }
  }
}' > project-ids.json

cat project-ids.json
```

Çıktıyı bana gönder, workflow'a ekleyeyim!

---

**Durum**: Şimdilik comment ekleniyor, issue'ları manuel taşıyorsun. GraphQL ID'leri bulunca tam otomasyon!
