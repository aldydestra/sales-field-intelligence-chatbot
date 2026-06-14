# Default Knowledge Base - Sales Field Intelligence Chatbot

## Tujuan Chatbot

Sales Field Intelligence Chatbot adalah asisten AI untuk membantu membaca data pipeline dan activity, menyusun insight, serta memberikan rekomendasi coaching untuk Sales dan Supervisor.

## Definisi Pipeline

Pipeline adalah tahapan prospek nasabah dari awal interaksi hingga pencairan. Dalam sistem ini, pipeline terdiri dari:

1. Tidak Bertemu
2. Dingin
3. Hangat
4. Panas
5. Pemberkasan
6. Perjanjian
7. Cair

## Stage: Tidak Bertemu

Tidak Bertemu adalah kondisi ketika Sales belum berhasil bertemu atau menghubungi nasabah. Fokus tindak lanjut adalah validasi kontak, validasi alamat, dan penjadwalan ulang kunjungan.

## Stage: Dingin

Dingin adalah kondisi ketika nasabah sudah teridentifikasi tetapi minat masih rendah. Fokus tindak lanjut adalah edukasi manfaat produk, penggalian kebutuhan, dan follow-up berkala.

## Stage: Hangat

Hangat adalah kondisi ketika nasabah mulai menunjukkan minat tetapi belum memiliki komitmen kuat. Fokus tindak lanjut adalah simulasi, handling objection, dan penetapan next step.

## Stage: Panas

Panas adalah kondisi ketika nasabah menunjukkan minat kuat dan memiliki potensi untuk masuk ke proses dokumen. Fokus tindak lanjut adalah validasi kebutuhan, validasi plafond, dan collect dokumen awal.

## Stage: Pemberkasan

Pemberkasan adalah kondisi ketika dokumen nasabah sedang dikumpulkan atau diproses. Fokus tindak lanjut adalah melengkapi dokumen, memonitor status pengajuan, dan menyelesaikan revisi berkas.

## Stage: Perjanjian

Perjanjian adalah kondisi ketika proses sudah mendekati pencairan dan membutuhkan konfirmasi akhir. Fokus tindak lanjut adalah memastikan tanda tangan, jadwal pencairan, dan administrasi akhir.

## Stage: Cair

Cair adalah kondisi ketika pembiayaan sudah terealisasi. Fokus lanjutan adalah maintenance nasabah dan menjaga pipeline baru agar hasil tetap berkelanjutan.

## Prinsip Analisis Activity

Activity tidak hanya dinilai dari jumlah, tetapi juga kualitas pergerakan pipeline. Activity tinggi belum tentu efektif jika tidak menghasilkan pergerakan stage atau pencairan.

## Indikasi Coaching

1. Activity rendah dan pipeline awal tinggi:
   - Fokus coaching pada disiplin kunjungan, validasi database, dan follow-up awal.

2. Activity tinggi tetapi Cair rendah:
   - Fokus coaching pada kualitas follow-up, handling objection, dan closing.

3. Pipeline Panas/Pemberkasan tinggi tetapi Cair rendah:
   - Fokus coaching pada bottleneck dokumen, administrasi, dan pengawalan tahap akhir.

4. Pipeline Dingin tinggi:
   - Fokus coaching pada edukasi produk, penggalian kebutuhan, dan segmentasi nasabah.

## Aturan Anti-Halusinasi

Chatbot tidak boleh mengarang angka, nama Sales, Supervisor, Region, atau penyebab masalah jika tidak tersedia di data. Jika data tidak cukup, chatbot wajib menyampaikan keterbatasan analisis.
