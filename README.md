# ColcheteDAO Plugins

Central repository for compiled Minecraft server plugin artifacts developed by ColcheteDAO.

---

## 📦 Plugins

| Folder | Source Repository | Description |
|---|---|---|
| [`DuneFall/`](./DuneFall) | [ColcheteDAO/DuneFall](https://github.com/ColcheteDAO/DuneFall) | Interactive Mini-Game and Live Interaction Manager for PaperMC |
| [`TikTokRetentionPlugin/`](./TikTokRetentionPlugin) | [ColcheteDAO/TikTokRetentionPlugin](https://github.com/ColcheteDAO/TikTokRetentionPlugin) | Minecraft Spigot/Paper plugin for live TikTok viewer survival challenge |
| [`VoteBattle/`](./VoteBattle) | [ColcheteDAO/VoteBattle](https://github.com/ColcheteDAO/VoteBattle) | Interactive Team Sand Tower & TNT Airstrike Battle for PaperMC 1.21+ |

---

## ⚙️ Automated CI (GitHub Actions)

This repository includes a GitHub Actions workflow [`.github/workflows/build-plugins.yml`](./.github/workflows/build-plugins.yml) that:
1. Checks out the source repositories (`ColcheteDAO/DuneFall`, `ColcheteDAO/TikTokRetentionPlugin`, `ColcheteDAO/VoteBattle`) using `actions/checkout@v6`.
2. Builds them using Apache Maven on OpenJDK 21.
3. Automatically places the compiled `.jar` artifact into its dedicated folder (`DuneFall/`, `TikTokRetentionPlugin/`, or `VoteBattle/`).
4. Commits and pushes the updated JARs back to `main`.
5. Uploads the build artifacts to the GitHub Actions run page.

---

## 🔑 Authentication Setup (for Private Repositories)

Since `ColcheteDAO/DuneFall`, `ColcheteDAO/TikTokRetentionPlugin`, and `ColcheteDAO/VoteBattle` are private repositories, GitHub Actions needs permission to clone them.

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
4. Choose whether to build `all`, `DuneFall`, `TikTokRetentionPlugin`, or `VoteBattle`.

### 2. Remote Trigger from Source Repositories (Webhook / Dispatch)
You can trigger this workflow automatically whenever you push code or release a new version in `DuneFall`, `TikTokRetentionPlugin`, or `VoteBattle` using a `repository_dispatch` event:

```bash
curl -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer <GH_PAT>" \
  https://api.github.com/repos/ColcheteDAO/plugins/dispatches \
  -d '{"event_type":"build-votebattle"}'
```
*(Use `build-dunefall` for DuneFall, `build-tiktokretention` for TikTokRetentionPlugin, `build-votebattle` for VoteBattle, or `build-plugins` to rebuild all)*
