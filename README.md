# SmartColl Clean — Public Build Orchestrator

Repository public: `pistislitae/SmartColl-v3`. Repository ini hanya berisi GitHub Actions manual. Source SmartColl tetap di repository private `pistislitae/SmartColl-v3-Priv`.

## Mengapa cocok tanpa VPS/laptop

Semua dapat dilakukan dari browser HP:

1. Buat repository private dan upload isi `SmartColl_Clean_Private_Source.zip`.
2. Buat repository public dan upload isi package ini.
3. Tambahkan repository secrets melalui GitHub Settings.
4. Buka tab **Actions** dan jalankan workflow secara manual.
5. Unduh APK dari **Artifacts**, atau buka hasil deploy pada `https://<project>.pages.dev`.

## Secrets repository public

- `SOURCE_REPO_TOKEN`: fine-grained token read-only untuk satu repository private.
- `CLOUDFLARE_API_TOKEN`: token Cloudflare dengan izin Pages deploy pada project terkait.
- `CLOUDFLARE_ACCOUNT_ID`: ID akun Cloudflare.

Untuk APK release bertanda tangan:

- `ANDROID_KEYSTORE_BASE64`
- `ANDROID_KEYSTORE_PASSWORD`
- `ANDROID_KEY_ALIAS`
- `ANDROID_KEY_PASSWORD`

Mulai dengan build `debug` jika belum memiliki keystore. APK debug dapat dipasang untuk pengujian tetapi bukan untuk Play Store.

## Keamanan

- Jangan simpan Aging, data debitur, token, keystore, atau database di repository public.
- Artifacts repository public dapat diunduh orang lain. APK tidak boleh berisi data operasional.
- Workflow tidak mencetak secret.
- Token source menggunakan `persist-credentials: false`.
