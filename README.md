# Data Togel 4D — Arsip Hasil Togel 5 Pasaran 2020–2026

Arsip **hasil togel** dan **keluaran togel** 4 digit untuk 5 pasaran — Singapore (`SG`), Hong Kong (`HK`), Sydney (`SDY`), Toto Macau (`MC`) dan Cambodia (`CAM`) — dari 2020-01-01 sampai 2026-10-28, terbuka dalam format JSON dan CSV.

**17,850 rekaman · 5 pasaran · 2020-01-01 s.d. 2026-10-28 · Creative Commons Attribution 4.0 International (CC BY 4.0)**

## Hasil togel terbaru (live hasil)

Arsip ini **snapshot bertanggal**, bukan umpan langsung. Untuk **hasil togel hari ini** beserta tabel keluaran yang diperbarui setiap undi, buka halaman pasarannya:

- **[Hasil Togel Singapore hari ini](https://rajahasil.co/hasil/singapore/)** — keluaran Singapore (`SG`) terbaru · Sen, Rab, Kam, Sab, Min · sesi 17:45 WIB
- **[Hasil Togel Hong Kong hari ini](https://rajahasil.co/hasil/hongkong/)** — keluaran Hong Kong (`HK`) terbaru · Setiap hari · sesi 23:00 WIB
- **[Hasil Togel Sydney hari ini](https://rajahasil.co/hasil/sydney/)** — keluaran Sydney (`SDY`) terbaru · Setiap hari · sesi 14:00 WIB
- **[Hasil Togel Toto Macau hari ini](https://rajahasil.co/hasil/toto-macau/)** — keluaran Toto Macau (`MC`) terbaru · Setiap hari · sesi 00:01, 13:00, 16:00, 19:00, 22:00, 23:00 WIB
- **[Hasil Togel Cambodia hari ini](https://rajahasil.co/hasil/cambodia/)** — keluaran Cambodia (`CAM`) terbaru · Setiap hari · sesi 11:50 WIB

Dokumentasi arsip dan rincian berkasnya ada di **[halaman data RajaHasil](https://rajahasil.co/data/)**.

> **Baca ini dulu.** Angka dihimpun dari situs arsip pihak ketiga yang tersedia publik. Ini **bukan angka resmi dari operator mana pun** dan **belum diverifikasi secara independen**. Field `session` adalah **label WIB (Asia/Jakarta), bukan cap waktu terverifikasi**.

**Status.** Rilis snapshot 1.1.0 (2026-10-28). Cakupan berakhir pada 2026-10-26 untuk SG, dan 2026-10-27 untuk HK, SDY dan CAM, dan 2026-10-28 untuk MC (MC hari parsial: hanya sesi 00:01 yang ada). Arsip tidak diperbarui otomatis; data baru diterbitkan sebagai rilis berversi (lihat [CHANGELOG](CHANGELOG.md)). Untuk angka terbaru, pakai tautan pasaran di atas.

## Cakupan per pasaran

| Pasaran | Kode | Rekaman | Mulai | Terakhir | Tahun | Hari undi | Sesi (label WIB) | Hasil terbaru |
|---|---|---:|---|---|---|---|---|---|
| Singapore | `SG` | 1,723 | 2020-01-01 | 2026-10-26 | 2020–2026 | Sen, Rab, Kam, Sab, Min | 17:45 | [hasil singapore](https://rajahasil.co/hasil/singapore/) |
| Hong Kong | `HK` | 2,492 | 2020-01-01 | 2026-10-27 | 2020–2026 | Setiap hari | 23:00 | [hasil hong kong](https://rajahasil.co/hasil/hongkong/) |
| Sydney | `SDY` | 2,126 | 2021-01-01 | 2026-10-27 | 2021–2026 | Setiap hari | 14:00 | [hasil sydney](https://rajahasil.co/hasil/sydney/) |
| Toto Macau | `MC` | 9,017 | 2021-01-01 | 2026-10-28 | 2021–2023, 2025–2026 | Setiap hari | 00:01, 13:00, 16:00, 19:00, 22:00, 23:00 | [hasil toto macau](https://rajahasil.co/hasil/toto-macau/) |
| Cambodia | `CAM` | 2,492 | 2020-01-01 | 2026-10-27 | 2020–2026 | Setiap hari | 11:50 | [hasil cambodia](https://rajahasil.co/hasil/cambodia/) |
| **Total** | | **17,850** | 2020-01-01 | 2026-10-28 | | | | |

## Isi arsip

```
data/
  index.json              manifes: cakupan, statistik per pasaran, celah data, SHA-256 tiap berkas
  latest.json             tanggal undi terbaru yang dimiliki tiap pasaran
  draws.csv               seluruh rekaman dalam satu CSV
  draws.json              seluruh rekaman dalam satu JSON
  SG/2020.json            satu berkas per pasaran per tahun, JSON dan CSV
  SG/2020.csv
  ...
schema/
  draw.schema.json            JSON Schema (2020-12) untuk satu rekaman
  results-file.schema.json    JSON Schema untuk berkas .json
  index.schema.json           JSON Schema untuk index.json
```

Halaman rilis juga memuat arsip zip (seluruhnya, atau per tahun) beserta berkas `SHA256SUMS`.

## Kamus data

| Field | Tipe | Keterangan |
|---|---|---|
| `market` | string | Kode pasaran: `SG`, `HK`, `SDY`, `MC`, `CAM`. |
| `draw_type` | string | Format undi. Selalu `4D` di rilis ini. |
| `draw_date` | string `YYYY-MM-DD` | Tanggal kalender yang dipakai arsip sumber untuk undi tersebut. |
| `session` | string `HH:MM` | **Label** jam undi sebagaimana diterbitkan arsip, dalam **WIB**. Lihat di bawah. |
| `session_timezone` | string | Zona waktu label. Selalu `Asia/Jakarta`. |
| `result` | string | Hasil empat digit, mis. `"0678"`. Selalu string; nol di depan bermakna. |

Kunci keunikan: (`market`, `draw_date`, `session`, `draw_type`). Rekaman diurutkan per pasaran (`SG`, `HK`, `SDY`, `MC`, `CAM`), lalu tanggal, lalu sesi. Di berkas per tahun, keenam field muncul dalam urutan di atas.

### Tentang `session`

`session` adalah label jam yang dicantumkan situs arsip di sebelah setiap undi, dinyatakan dalam **WIB** (Asia/Jakarta, UTC+7, tanpa daylight saving). Dia sebuah label: **bukan cap waktu terverifikasi**, dan **bukan jam lokal negara pasarannya**. Rilis ini tidak mengonversi label ke jam lokal, karena arsipnya tidak mencatat kapan undi benar-benar berlangsung. `market_timezone` di `index.json` adalah zona IANA tiap pasaran, sebagai rujukan saja.

### Membaca `result` dengan benar

1,883 dari 17,850 hasil (10.5%) diawali `0`, misalnya `0678`. Alat yang menebak tipe kolom mengubahnya menjadi angka 678 dan menghilangkan nolnya tanpa peringatan.

- **Berkas JSON** sudah menyimpan string; muat apa adanya.
- **CSV di pandas:** `pd.read_csv(path, dtype={"result": str})`.
- **Excel:** impor kolomnya sebagai *Text*; membuka CSV dengan klik ganda menghilangkan nolnya. **Google Sheets:** hilangkan centang "Convert text to numbers, dates, and formulas" saat impor.
- **Pemuat yang menyimpulkan tipe** (misalnya builder CSV `datasets` Hugging Face): nyatakan kolomnya sebagai `string`, atau muat berkas JSON-nya.

Pemeriksaan cepat setelah memuat `draws.csv`: jumlah nilai `result` yang diawali `0` harus 1,883.

## Catatan per pasaran

- **Singapore (`SG`).** Kalender lima hari (Sen, Rab, Kam, Sab, Min) sebagaimana dicantumkan arsip yang dihimpun. Ini bukan jadwal undi resmi operator. Label sesinya WIB. Jam lokal Singapura adalah WIB+1.
- **Hong Kong (`HK`).** Label sesi 23:00 adalah WIB. Jam lokal Hong Kong adalah WIB+1, jadi momen yang sama terbaca 00:00 pada hari kalender berikutnya di sana. Dataset ini mempertahankan tanggal dan label arsipnya apa adanya, tanpa konversi.
- **Sydney (`SDY`).** Label sesinya WIB. Selisih Sydney terhadap WIB berubah karena daylight saving (+3 atau +4 jam), jadi tidak ada satu jam lokal yang berlaku sepanjang tahun.
- **Toto Macau (`MC`).** Pasaran multi-sesi: setiap sesi adalah rekaman tersendiri. Himpunan sesi yang diterbitkan berubah antar tahun (lihat rincian sesi per tahun di index.json). Tidak ada baris placeholder yang disisipkan.
- **Cambodia (`CAM`).** Phnom Penh adalah UTC+7, sama dengan WIB, jadi label sesi dan jam lokalnya berimpit.

## Celah data dan rekaman yang ditahan

Celah dihitung dalam hari undi terjadwal pasaran itu (lihat kolom *Hari undi* di atas).

| Pasaran | Dari | Sampai | Hari undi terjadwal | Catatan |
|---|---|---|---:|---|
| `SG` | 2020-04-06 | 2020-06-22 | 56 | Tidak ada rekaman di arsip yang dihimpun untuk periode ini. |
| `SG` | 2023-10-23 | 2023-10-23 | 1 | Ditahan, lihat bagian rekaman yang ditahan. |
| `MC` | 2021-09-30 | 2021-09-30 | 1 | Tidak ada di arsip yang dihimpun. |
| `MC` | 2024-01-01 | 2024-12-31 | 366 | Arsip yang dihimpun tidak mencakup 2024 untuk pasaran ini. |

Seri yang mulai lebih lambat: `SDY` dan `MC` mulai 2021-01-01 (tidak ada rekaman sebelum itu).

Rekaman ditahan: `SG` 2023-10-23 17:45. Arsip yang dihimpun berselisih soal hasil undi ini, jadi angkanya ditahan alih-alih ditebak.

## Memakai data ini

```python
import json
import pandas as pd

# CSV: nyatakan `result` sebagai teks supaya nol di depan tidak hilang
df = pd.read_csv("data/draws.csv", dtype={"result": str})

# JSON: nilainya sudah berupa string
with open("data/SG/2024.json", encoding="utf-8") as f:
    sg_2024 = pd.DataFrame(json.load(f)["results"])
```

```js
const latest = await (await fetch("https://rajahasil.co/data/latest.json")).json();
console.log(latest.markets.HK.last_draw_date, latest.markets.HK.results);
```

## Lisensi dan atribusi

Diterbitkan di bawah [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Lisensi mencakup kompilasinya, strukturnya, dokumentasi, dan metadatanya. Tidak ada klaim atas faktanya sendiri, yaitu angka undi.

Atribusi berarti tautan balik. Sebutkan nama arsipnya dan tautkan ke halaman datanya ketika kamu menerbitkan grafik, model, atau dataset turunan, serta nyatakan kalau datanya kamu ubah:

- Teks: `Data: RajaHasil 4D Results Archive, https://rajahasil.co/data/ (CC BY 4.0)`
- HTML: `<a href="https://rajahasil.co/data/">RajaHasil</a>`

## Sitasi

Lihat [CITATION.cff](CITATION.cff). BibTeX:

```bibtex
@dataset{rajahasil_4d_results_archive,
  title   = {RajaHasil 4D Results Archive},
  author  = {{RajaHasil}},
  year    = {2026},
  version = {1.1.0},
  url     = {https://rajahasil.co/data/},
  license = {CC-BY-4.0}
}
```

## Versi

Versi mengikuti MAJOR.MINOR.PATCH: MAJOR untuk perubahan skema, MINOR untuk penambahan data, PATCH untuk koreksi. Setiap perubahan dicatat di [CHANGELOG](CHANGELOG.md).

## Penafian

Disediakan untuk keperluan statistik, riset, dan edukasi. Hasil undi bersifat acak; **hasil masa lalu tidak mengatakan apa pun tentang hasil berikutnya**, dan tidak ada apa pun di sini yang merupakan saran dalam bentuk apa pun. Arsip ini tidak berafiliasi dengan dan tidak didukung oleh operator mana pun; nama pasaran adalah label deskriptif yang dipakai sumber yang dihimpun. Data disediakan apa adanya, tanpa jaminan. Kesalahan bisa dilaporkan lewat issue tracker repo ini.

Hasil togel terbaru per pasaran: **[https://rajahasil.co/hasil/](https://rajahasil.co/hasil/hongkong/)**
