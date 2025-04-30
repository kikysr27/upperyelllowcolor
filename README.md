# Pemilih Warna Upper & Lower

Proyek ini mendemonstrasikan pemilih warna yang menyesuaikan kecerahan warna yang dipilih dan menampilkan variasi warna upper dan lower dari warna yang dipilih pada antarmuka yang ramah pengguna.

## Fitur

- **Pemilih Warna**: Memungkinkan pengguna untuk memilih warna melalui input warna.
- **Penyesuaian Kecerahan**: Ketika warna dipilih, dua variasi warna tersebut dibuat dengan tingkat kecerahan yang berbeda:
  - **Upper**: Versi warna yang lebih terang dari warna yang dipilih.
  - **Lower**: Versi warna yang lebih gelap dari warna yang dipilih.
- **Pembaruan Secara Real-time**: Warna pada kotak upper dan lower diperbarui secara real-time saat pengguna memilih warna baru.
- **Menampilkan RGB**: Nilai RGB untuk warna upper dan lower ditampilkan di bawah kotak masing-masing.

## Cara Kerja

1. **HTML**: Halaman ini berisi input pemilih warna (`<input type="color">`), dua kotak untuk menampilkan warna yang telah disesuaikan, dan label yang menunjukkan nilai RGB dari warna tersebut.
2. **CSS**: Tata letak halaman diatur agar konten berada di tengah dan memastikan kotak warna terlihat dengan jelas.
3. **JavaScript**:
   - Ketika pengguna memilih warna, JavaScript mendengarkan event `input`.
   - Fungsi `adjustLightness()` digunakan untuk menyesuaikan kecerahan warna yang dipilih. Dua versi warna dibuat:
     - **Upper**: Diterangi dengan faktor 1,3.
     - **Lower**: Diteduhkan dengan faktor 0,7.
   - Warna latar belakang pada kotak upper dan lower diperbarui dengan warna yang telah disesuaikan, dan nilai RGB-nya ditampilkan.

## Cara Menggunakan

1. Buka file `index.html` di browser Anda.
2. Gunakan pemilih warna untuk memilih warna.
3. Kotak warna upper dan lower akan menampilkan warna yang telah disesuaikan, dan nilai RGB akan ditampilkan di bawah kotak masing-masing.

## Instalasi

1. Clone atau unduh repositori ini.
2. Buka file `index.html` di browser.

## Ketergantungan

- Tidak ada

## Lisensi

Proyek ini dilisensikan di bawah Lisensi MIT - lihat file [LICENSE](LICENSE) untuk detail lebih lanjut.
