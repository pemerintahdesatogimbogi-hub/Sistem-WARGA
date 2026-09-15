# Build APK WARGA v1.8 secara online dengan GitHub Actions

Paket ini sudah disiapkan agar APK Android dapat dikompilasi di server GitHub tanpa Android Studio di komputer.

## 1. Buat repository GitHub
Buka:
https://github.com/new

Buat repository baru, misalnya:
`Sistem-WARGA`

Boleh Public atau Private.

## 2. Upload ISI folder proyek
Penting: yang di-upload ke repository adalah **isi** folder `Sistem-Warga-v1.8-LiveChat`, bukan file ZIP-nya.

Struktur minimal harus terlihat seperti:

```text
Sistem-WARGA/
├── .github/
│   └── workflows/
│       └── android-apk.yml
├── android/
│   ├── app/
│   ├── build.gradle
│   ├── settings.gradle
│   └── gradle.properties
├── backend/
├── database/
├── frontend/
└── ...
```

Cara paling mudah di GitHub:
1. Buka repository.
2. **Add file → Upload files**.
3. Upload semua isi folder proyek hasil extract.
4. Klik **Commit changes**.

## 3. Jalankan build online
Setelah file masuk:
1. Buka tab **Actions**.
2. Pilih workflow **Build WARGA Android APK**.
3. Klik **Run workflow**.
4. Tunggu sampai status hijau **Success**.

Workflow juga otomatis berjalan setiap kali ada perubahan pada folder `android/`.

## 4. Ambil APK
Buka hasil workflow yang sudah **Success**.

Di bagian **Artifacts**, pilih:
`WARGA-v1.8.0-debug`

Di dalam artifact tersebut terdapat:
`WARGA-v1.8.0-debug.apk`

APK ini dapat dipasang untuk pengujian di Android.

## 5. Catatan
- Build memakai JDK 17, Android Gradle Plugin 8.5.2, dan Gradle 8.7.
- APK yang dihasilkan adalah **debug APK**, cocok untuk pengujian.
- Untuk distribusi resmi/Play Store, buat signing key dan workflow release terpisah.
- Backend Node.js + MySQL tetap harus berjalan pada server. APK WARGA mengakses URL server yang dimasukkan saat pertama kali dibuka.
- Video call produksi tetap memerlukan HTTPS dan konfigurasi STUN/TURN yang sesuai.
