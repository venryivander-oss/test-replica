# Build log

- Tahap 1 — 2026-11-12 — done. Editor satu layar (`index.html`): impor, timeline kanvas multi-track, pratinjau WebGL, trim/split/urut/snap, kecepatan, volume, teks dasar, rasio, ekspor (WebCodecs + fallback MediaRecorder), autosave IndexedDB, undo/redo.
  - Tidak ada recon map di repo; dibangun langsung dari spesifikasi pengguna (clean-room, tanpa aset pihak lain).
  - Diuji di Chromium headless 390px & 1440px (mouse, keyboard, sentuh via CDP). Belum diuji di perangkat iOS/Android asli.
  - Lebih sulit dari perkiraan: sinkronisasi seek video saat scrub (frame harus digambar sebelum seek berikutnya).
  - Belum ada: auto-scroll saat menyeret klip ke tepi, pindah klip antar-trek secara manual (otomatis jika bertabrakan).
- Tahap 2 — 2026-11-12 — done. Keyframe + easing, 15 transisi, 17 filter, 9 penyesuaian, 6 efek pasca (trek efek), speed curve, freeze, reverse, flip, crop, latar blur/gambar.
  - Shader lapisan baru (warna, blur, sharpen, wipe) + shader pasca lewat framebuffer; hanya dipakai saat ada efek aktif.
  - Lebih sulit dari perkiraan: reverse. Tanpa dekode frame sendiri, pratinjaunya hanya bisa seek per frame (patah-patah); ekspor tetap akurat.
  - Ekspor dengan reverse/efek blur jauh lebih lambat di GL perangkat lunak (uji headless ±220 ms/frame); belum diukur di GPU nyata.
- Tahap 3 — 2026-11-12 — done. Chroma key + pipet, mask, 8 blend mode (salin latar ke tekstur lalu campur di shader), stiker emoji/bentuk, gaya teks lengkap, animasi masuk/keluar/berulang, 9 template judul.
  - Font Google dimuat dari 4 berkas CSS terpisah (28 keluarga); tidak bisa diverifikasi di lingkungan uji karena fonts.googleapis.com diblokir.
  - Belum ada: pegangan mask di pratinjau, wipe per-lapisan untuk animasi teks.
