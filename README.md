# ColcheteDAO Plugins

Central repository for compiled Minecraft server plugin artifacts developed by ColcheteDAO.

---

## 📦 Plugins

| Folder | Source Repository | Description |
|---|---|---|
| [`DuneFall/`](./DuneFall) | [ColcheteDAO/DuneFall](https://github.com/ColcheteDAO/DuneFall) | Interactive Mini-Game and Live Interaction Manager for PaperMC |
| [`TikTokRetentionPlugin/`](./TikTokRetentionPlugin) | [ColcheteDAO/TikTokRetentionPlugin](https://github.com/ColcheteDAO/TikTokRetentionPlugin) | Minecraft Spigot/Paper plugin for live TikTok viewer survival challenge |

---

## ⚙️ Automated CI (GitHub Actions)

This repository includes a GitHub Actions workflow [`.github/workflows/build-plugins.yml`](./.github/workflows/build-plugins.yml) that:
1. Checks out the source repositories (`ColcheteDAO/DuneFall`, `ColcheteDAO/TikTokRetentionPlugin`) using `actions/checkout@v4`.
2. Builds them using Apache Maven on OpenJDK 21.
3. Automatically places the compiled `.jar` artifact into its dedicated folder (`DuneFall/` or `TikTokRetentionPlugin/`).
4. Commits and pushes the updated JARs back to `main`.
5. Uploads the build artifacts to the GitHub Actions run page.

---

## 🔑 Authentication Setup (for Private Repositories)

Since `ColcheteDAO/DuneFall` and `ColcheteDAO/TikTokRetentionPlugin` are private repositories, GitHub Actions needs permission to clone them.

1. Go to **GitHub Settings** -> **Developer Settings** -> **Personal Access Tokens** (Fine-grained or Classic).
2. Generate a token with `repo` (or read contents) permissions for the repositories.
3. In this repository (`ColcheteDAO/plugins`), go to **Settings** -> **Secrets and variables** -> **Actions**.
4. Add a New Repository Secret:
   - **Name:** `GH_PAT`
   - **Value:** `<Your Personal Access Token>`

---

## 🚀 How to Trigger Builds

### 1. Manual Trigger (GitHub UI)
1. Go to the **Actions** tab in this repository.
2. Select **Build and Update Plugins**.
3. Click **Run workflow**.
4. Choose whether to build `all`, `DuneFall`, or `TikTokRetentionPlugin`.

### 2. Remote Trigger from Source Repositories (Webhook / Dispatch)
You can trigger this workflow automatically whenever you push code or release a new version in `DuneFall` or `TikTokRetentionPlugin` using a `repository_dispatch` event:

```bash
curl -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer <GH_PAT>" \
  https://api.github.com/repos/ColcheteDAO/plugins/dispatches \
  -d '{"event_type":"build-dunefall"}'
```
*(Use `build-tiktokretention` for TikTokRetentionPlugin, or `build-plugins` to rebuild all)*
