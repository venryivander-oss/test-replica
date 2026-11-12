# Build log

- Tahap 1 — 2026-11-12 — done. Editor satu layar (`index.html`): impor, timeline kanvas multi-track, pratinjau WebGL, trim/split/urut/snap, kecepatan, volume, teks dasar, rasio, ekspor (WebCodecs + fallback MediaRecorder), autosave IndexedDB, undo/redo.
  - Tidak ada recon map di repo; dibangun langsung dari spesifikasi pengguna (clean-room, tanpa aset pihak lain).
  - Diuji di Chromium headless 390px & 1440px (mouse, keyboard, sentuh via CDP). Belum diuji di perangkat iOS/Android asli.
  - Lebih sulit dari perkiraan: sinkronisasi seek video saat scrub (frame harus digambar sebelum seek berikutnya).
  - Belum ada: auto-scroll saat menyeret klip ke tepi, pindah klip antar-trek secara manual (otomatis jika bertabrakan).
