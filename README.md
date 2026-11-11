# Akuisisi Data Akomodasi di Kecamatan Kintamani

Tugas Praktik BIFP-243 Akuisisi dan Manajemen Data, INSTIKI
Nama: Ach. Rafli Alfian syah | NIM: 2501010048

## Tujuan
Mengakuisisi data akomodasi (hotel, guest house, hostel, motel, apartemen, chalet) di Kecamatan Kintamani dari API publik, menyimpan respons mentah, mengubahnya menjadi dataset tabular terdokumentasi, dan menilai kelengkapannya terhadap data resmi BPS.

## Sumber data
- OpenStreetMap melalui Overpass API (https://overpass-api.de/api/interpreter), lisensi ODbL.
- Pembanding: angka BPS per kecamatan belum diperoleh (lihat laporan).

## Tanggal akses
11 November 2026 (waktu UTC lengkap di docs/provenance.json). Jumlah elemen yang diambil: 32.

## Metode akuisisi
1. Query Overpass untuk tag tourism hotel, guest_house, hostel, motel, apartment, chalet di dalam batas administratif Kecamatan Kintamani (docs/query_overpass.txt).
2. Pengambilan dengan Python (requests), memakai timeout dan retry berjeda untuk status 429/504.
3. Respons mentah disimpan apa adanya di data/raw/; hash MD5 dicatat di provenance.
4. Respons diratakan menjadi data/interim/akomodasi_kintamani.csv.
5. Pemeriksaan: duplikat, nama kosong, koordinat di luar wilayah, kolom hampir kosong.

## Batasan etika
- Hanya memakai sumber yang diizinkan; tidak memakai OTA maupun Google Maps.
- Data kontak (telepon, email, media sosial) tidak diambil.
- Query dijalankan seperlunya dengan User-Agent yang mengidentifikasi pengambil data.

## Atribusi
Data (c) OpenStreetMap contributors, tersedia di bawah lisensi ODbL.

## Cara menjalankan ulang
1. Buka notebooks/akuisisi_akomodasi.ipynb di Google Colab atau Jupyter.
2. Isi NAMA, NIM, EMAIL di sel Setup.
3. Jalankan semua sel dari atas ke bawah.
4. Hasil ada di data/, docs/, dan reports/.

## Struktur
data/raw (respons mentah), data/interim (CSV), notebooks, docs (query, provenance, data dictionary, checklist etika, perbandingan BPS), reports (laporan PDF).
