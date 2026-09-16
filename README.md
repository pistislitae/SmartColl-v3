# SmartColl Clean — Public Build Orchestrator

Repository public: `pistislitae/SmartColl-v3`.

Repository ini hanya berisi GitHub Actions manual. Source aplikasi tetap private di `pistislitae/SmartColl-v3-Priv`.

## Workflow

- **Build SmartColl Clean APK**: checkout private source, test, Vite build, Capacitor sync, dan Gradle build menggunakan Node 20 + Java 17.
- **Deploy SmartColl Clean to Cloudflare Pages**: deploy UI `dist` dan Pages Functions/Workers JavaScript ke project `pages.dev` yang sudah dibuat.

Semua dapat dijalankan dari browser HP melalui tab **Actions → Run workflow**.

## Secret wajib

Buka **Settings → Secrets and variables → Actions**:

- `SOURCE_REPO_TOKEN`: fine-grained PAT baru, hanya untuk `SmartColl-v3-Priv`, permission **Contents: Read-only**. Jangan gunakan token full-scope atau token yang pernah dibagikan lewat chat.

Untuk workflow deploy Pages manual:

- `CLOUDFLARE_API_TOKEN`: token Cloudflare Pages deploy dengan least privilege.
- `CLOUDFLARE_ACCOUNT_ID`: ID akun Cloudflare.

Untuk APK release bertanda tangan:

- `ANDROID_KEYSTORE_BASE64`
- `ANDROID_KEYSTORE_PASSWORD`
- `ANDROID_KEY_ALIAS`
- `ANDROID_KEY_PASSWORD`

Mulai dengan build `debug` jika belum mempunyai keystore. APK debug bisa dipasang untuk uji operasional, tetapi bukan untuk distribusi Play Store.

## Keamanan

- Jangan simpan Aging, data debitur, token, keystore, atau database di repository public.
- Artifact repository public dapat diunduh orang lain; APK tidak boleh berisi data operasional ataupun token runtime.
- Workflow menggunakan `persist-credentials: false` dan tidak mencetak secret.
- Secret Apps Script dan token runtime SmartColl disimpan di Cloudflare, bukan repository public.

Panduan lengkap ada pada private source: `docs/PHONE_ONLY_DEPLOYMENT.md`.
