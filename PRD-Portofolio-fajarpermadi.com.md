# PRD — Website Portofolio fajarpermadi.com

**Pemilik:** Ahmad Fajar Permadi
**Versi:** 1.2 (revisi)
**Tujuan dokumen:** Jadi *source of truth* yang bisa langsung disuapkan ke AI coding agent (Claude Code, Cursor, dsb.) supaya hasilnya konsisten dan tidak "ngarang" struktur sendiri.

---

## 1. Ringkasan & Konteks

Fajar adalah mahasiswa Sistem Informasi (Universitas Nusantara PGRI Kediri), Ketua Divisi Internal HIROSI, dan sedang aktif melamar magang/kerja. Portofolio di `fajarpermadi.com` fokus tunggal sebagai **etalase teknis untuk recruiter/HRD** — bukan situs bisnis/agensi. Semua konten diarahkan untuk menjawab pertanyaan recruiter dalam waktu singkat: *skill apa yang dikuasai, bukti nyatanya apa, bisa dihubungi lewat mana.*

---

## 2. Tujuan Bisnis (Goals)

| # | Tujuan | Metrik keberhasilan |
|---|---|---|
| G1 | Naikkan peluang lolos seleksi magang/kerja | Recruiter bisa menemukan CV, kontak, dan proyek unggulan dalam <30 detik |
| G2 | Jadi hub tunggal untuk semua proyek teknis (riset, akademik, eksplorasi pribadi) | Setiap proyek besar punya halaman detail dengan cerita problem→solusi→hasil |
| G3 | SEO — nama "Ahmad Fajar Permadi" muncul di halaman 1 Google | Terindeks Google dalam 2 minggu setelah launch |

**Non-tujuan (scope out untuk v1):** blog panjang, sistem komentar, multi-bahasa penuh (cukup ID, opsional toggle EN nanti), CMS admin panel custom, konten promosi jasa/agensi.

---

## 3. Ruang Lingkup — Struktur Halaman (Sitemap)

Rekomendasi saya: **one-page scroll untuk landing** + **halaman detail per proyek** (bukan seluruhnya satu halaman panjang, bukan juga situs multi-page berat). Ini titik tengah yang paling umum dipakai portofolio developer karena recruiter suka scroll cepat, tapi proyek kompleks (CareerPath AI, Sistem Presensi PKKMB) butuh ruang cerita lebih dari 2 paragraf.

```
/                      → Landing (one-page): Hero, About, Featured Projects (3), Skills, Contact
/proyek                → Grid semua proyek (filter: Riset/Akademik / Eksplorasi Pribadi)
/proyek/[slug]         → Detail proyek (masalah → solusi → stack → hasil → link)
/tentang               → (opsional) cerita lebih panjang: perjalanan teknis, HIROSI, kuliah
CV.pdf                 → Download langsung (bukan halaman)
```

Kalau kamu ingin versi paling ramping untuk v1 pertama: **cukup `/` + `/proyek/[slug]`**, halaman `/tentang` dan filter grid menyusul di v1.1.

---

## 4. Konten per Section (Functional Requirements)

### 4.1 Hero
- Nama, satu kalimat positioning (contoh arah: *"Software Engineer — membangun sistem web, AI, dan otomatisasi dari riset kampus hingga eksplorasi pribadi"*)
- 2 CTA: "Lihat Proyek" (scroll) dan "Download CV" (PDF)
- Status ketersediaan (contoh: "Open to internship opportunities") — sinyal penting ke recruiter

### 4.2 Featured Projects (di landing, 3 proyek)

Berdasarkan revisimu, berikut susunan final, diurut dari yang paling kuat sebagai bukti kemampuan:

1. **Sistem Presensi QR PKKMB Prodi Sistem Informasi 2026** — proyek pembuka. Ini bukan sekadar tugas: sudah **direalisasikan dan benar-benar dipakai** untuk PKKMB SI 2026, punya desain keamanan berlapis (QR rotating HMAC-signed, one-time lock NPM, geolocation + rate-limit anomali), sudah melalui pengujian terkontrol (15 test case), dan sedang menuju publikasi jurnal SINTA 3. Cerita kuat untuk role software engineer/backend karena menunjukkan kamu paham *security tradeoffs* dan bisa mendokumentasikan limitasi sistem secara jujur.
2. **CareerPath AI** — ML/NLP, capstone Coding Camp DBS Foundation, ada metrik konkret (cosine similarity 30%→50%+ setelah eksperimen model). Kuat untuk role data/AI.
3. **HYPE Signal Analyzer** — sistem trading signal berbasis n8n dengan metodologi backtesting yang matang (v1–v12, ada slippage modeling, ATR filtering, bootstrap confidence interval). Saya sarankan **framing proyek ini eksplisit sebagai riset/eksplorasi metodologis**, bukan "sistem trading yang jalan" — karena statusnya memang masih paper-trading. Justru transparansi ini (hasil MTFA cuma ~55% probability of profitability setelah rigorous testing) menunjukkan kamu paham cara mengevaluasi klaim secara kritis, bukan asal klaim profit.

Dengan 3 proyek, komposisi skill yang terwakili sudah cukup seimbang: security/backend engineering (proyek 1), data science/ML (proyek 2), dan automation/n8n (proyek 3) — tiga kategori berbeda, bukan tiga proyek yang mirip.

### 4.3 Setiap kartu proyek berisi
- Judul, 1-2 kalimat deskripsi problem→solusi (bukan cuma nama tech)
- Badge stack (Next.js, n8n, TensorFlow, dst)
- Link: repo (kalau publik), demo (kalau ada), atau "Studi kasus →" ke halaman detail

### 4.4 Skills
Kelompokkan per kategori, jangan satu daftar panjang tanpa struktur:
- **Web Development**: Next.js, React, Express.js
- **AI/Data**: TensorFlow, ML pipeline, NLP, web scraping
- **Automation**: n8n, Puppeteer
- **Infrastructure**: Docker, self-hosted server (Linux/Armbian), Cloudflare Tunnel

### 4.5 About singkat
Kuliah, peran Ketua Divisi Internal HIROSI, minat teknis — 3-4 kalimat, jangan riwayat hidup lengkap (itu fungsi CV).

### 4.6 Contact
Email, LinkedIn, GitHub. Form kontak opsional — kalau AI coding agent tidak setup backend email, cukup `mailto:` link, jangan bikin form kompleks yang butuh backend/SMTP di v1.

---

## 5. Kebutuhan Non-Fungsional

| Aspek | Requirement | Alasan |
|---|---|---|
| **Performa** | Lighthouse score ≥90 (Performance & SEO) | Recruiter bounce cepat kalau lambat |
| **Responsif** | Mobile-first, breakpoint standar Tailwind | Banyak recruiter buka link dari HP |
| **SEO** | Meta tags, Open Graph image, sitemap.xml, structured data (Person schema) | Supaya nama kamu muncul saat di-Google |
| **Aksesibilitas** | Kontras warna AA, alt text gambar | Standar minimum yang wajar |
| **Analytics** | Plausible/Umami (self-hosted friendly) atau Google Analytics | Supaya tahu apakah recruiter benar-benar buka |
| **Keamanan** | HTTPS wajib via Cloudflare (bukan self-signed) | Domain baru harus langsung aman |
| **Uptime/Monitoring** | Wajib ada monitoring (lihat bagian 6) | Karena hosting self-managed, downtime tidak akan ada notifikasi otomatis dari provider seperti Vercel |

---

## 6. Rekomendasi Tech Stack & Hosting

**Framework & styling** — tetap dengan stack yang sudah kamu kuasai supaya AI coding agent bisa langsung produktif dan kamu bisa maintain sendiri setelahnya:
- **Framework:** Next.js (App Router) + TypeScript
- **Styling:** Tailwind CSS
- **Konten proyek:** disimpan sebagai data terstruktur (`data/projects.ts` atau MDX per proyek), **bukan** hardcode di JSX tersebar — supaya nambah proyek baru nanti cukup tambah satu entry.

**Hosting: STB (sesuai keputusanmu)**

Karena kamu sudah punya infrastruktur ini jalan untuk `repo.jayadevdigital.my.id` dan sistem presensi PKKMB, secara teknis ini realistis dan konsisten dengan cara kerjamu. Tapi saya perlu jujur soal tradeoff-nya supaya keputusan ini tetap sadar risiko, bukan cuma ikut kebiasaan:

| Aspek | Vercel (alternatif) | STB kamu |
|---|---|---|
| Uptime | ~99.9%, dikelola provider | Tergantung listrik rumah, koneksi ISP, dan STB itu sendiri tetap hidup |
| Downtime saat recruiter buka link | Sangat kecil kemungkinan | Ada risiko nyata — kalau listrik/internet rumah mati saat itu, first impression rusak |
| Kontrol penuh & bukti skill infra | Terbatas | Penuh — dan justru bisa jadi *talking point* di interview ("saya self-host portofolio saya sendiri") |
| Biaya | Gratis | Sudah ada, tapi ada biaya listrik/internet tersembunyi |

**Rekomendasi mitigasi supaya risiko downtime tidak jadi masalah nyata:**
1. Pasang **uptime monitoring** (UptimeRobot/Better Uptime — gratis) yang kirim notifikasi WhatsApp/email ke kamu kalau situs down, supaya kamu bisa segera cek.
2. Expose lewat **Cloudflare Tunnel** (sudah familiar kamu pakai) — ini juga otomatis kasih HTTPS dan sedikit proteksi DDoS gratis.
3. **Cache statis di Cloudflare** (Page Rules / Cache Everything untuk aset statis) supaya kalau STB sempat lambat, visitor tetap dapat versi ter-cache untuk beberapa saat.
4. Pertimbangkan build **static export** (`next export` atau ISR dengan revalidate panjang) daripada full SSR — beban ke STB jauh lebih ringan dan lebih tahan kalau ada traffic tiba-tiba (misal linknya dibagikan rame-rame).
5. **DNS/Domain:** arahkan `fajarpermadi.com` ke Cloudflare (nameserver Cloudflare), lalu tunnel ke STB — pola yang sama seperti proyek `repo-jayadev` sebelumnya.

Poin 4 ini saya tekankan karena portofolio recruiter-facing idealnya *tidak boleh* punya titik gagal di runtime server kalau bisa dihindari — static export memindahkan sebagian besar risiko ke Cloudflare CDN, STB tinggal jadi origin cadangan.

---

## 7. Skill untuk AI Coding Agent: `antislop`

Kamu menyebut ingin pakai [antislop](https://github.com/miqdadbadjuber/anti-slop) (miqdadbadjuber) supaya tampilannya bagus. Saya perlu koreksi ekspektasi di sini karena penting: **antislop bukan style guide, dan dokumentasinya sendiri menyebutnya secara eksplisit sebagai "filter, bukan sihir."** Fungsinya adalah mencegah agent menghasilkan pola *AI slop* yang generik/klise — logo sparkle, badge "NEXT-GEN AI 2.0", copy hype kosong, statistik palsu ("10.000% ROI"), komentar kode yang cuma mengulang nama variabel, dsb. Itu 38 rules (R-01 s/d R-38) plus beberapa skill tambahan (antislop-ui, antislop-copywriting, antislop-human, antislop-layoutmobile, antislop-code).

**Implikasi penting dari cara kerjanya:** kalau kamu pasang antislop saja tanpa arahan visual, hasilnya memang bersih dari pola klise tapi cenderung *plain/sterile* — repo-nya sendiri mendemonstrasikan ini di bagian "See the difference". Arah keindahan/visual harus datang dari file `DESIGN.md` yang kamu buat sendiri (palet warna, tipografi, mood, referensi). Tanpa `DESIGN.md`, "tampilan bagus" yang kamu mau justru **tidak akan otomatis muncul** — antislop cuma mencegah yang jelek generik, bukan menciptakan yang indah.

**Rekomendasi konkret:**
1. Install via cara yang cocok dengan agent yang kamu pakai (Claude Code → `npx antislop-ai` lalu pilih skill `antislop-ui`, `antislop-layoutmobile`, dan `antislop-copywriting` — tiga ini paling relevan untuk portofolio; skip `antislop-code` kalau tidak butuh audit komentar kode).
2. Buat `DESIGN.md` di root project **sebelum** mulai generate UI, isinya minimal: palet warna (2-3 warna + 1 aksen), tipografi (1-2 font), mood/referensi visual (misal: "minimal, dark mode default, teknikal/terminal-inspired" atau arah lain sesuai selera kamu), dan referensi situs yang kamu suka.
3. Gunakan mode **"During"** (bukan "After") — jalankan antislop sambil membangun, bukan cuma audit di akhir, karena PRD ini memang untuk build dari nol.
4. Delivery Gate bawaan antislop (laporan PASS/FAIL sebelum ship) bisa dijadikan checklist terakhir sebelum kamu deploy ke STB.

Kalau kamu belum punya arah visual yang jelas, saya bisa bantu susun draft `DESIGN.md` sekarang juga — beri tahu saja gaya yang kamu suka (minimal/clean, dark/terminal-style, playful, dsb).

---

## 8. Konten yang Perlu Kamu Siapkan Sebelum Development

AI coding agent butuh data asli, bukan lorem ipsum, supaya hasil pertama sudah mendekati final:

1. CV terbaru versi PDF
2. Untuk tiap proyek featured (3 proyek di atas): 1 screenshot/mockup, 2-3 kalimat problem-solusi, hasil/metrik konkret kalau ada
3. Foto profil (opsional tapi menaikkan kepercayaan recruiter)
4. Link aktif: GitHub, LinkedIn, email
5. `DESIGN.md` (lihat bagian 7) — arah visual sebelum masuk development

---

## 9. Roadmap Rilis (bertahap, bukan sekali jadi)

1. **v1 — MVP (target: bisa live dalam beberapa hari kerja):** Landing one-page + halaman detail 3 proyek featured + CV download + contact, di-deploy di STB via Cloudflare Tunnel dengan monitoring aktif
2. **v1.1:** Halaman `/proyek` grid lengkap dengan filter kategori
3. **v1.2:** Halaman `/tentang` cerita panjang + analytics + OG image dinamis per proyek
4. **v2 (opsional):** Toggle bahasa EN, mini-blog technical writing (bagus untuk SEO & personal branding jangka panjang)

---

## 10. Risiko & Hal yang Perlu Diputuskan

- **Downtime STB** — sudah dibahas di bagian 6, mitigasi wajib diterapkan sejak v1, bukan ditambahkan belakangan.
- **Repo publik atau tidak?** Pastikan repo yang di-link (terutama Sistem Presensi PKKMB, karena ada kredensial/skema keamanan) sudah dibersihkan dari secret/env sebelum dijadikan link publik.
- **Konsistensi data proyek** — data terstruktur (bagian 6) penting supaya kamu sendiri (tanpa AI agent) bisa update proyek baru dengan cepat.
- **`DESIGN.md` belum dibuat** — tanpa ini, hasil antislop berisiko terlalu polos (lihat bagian 7).

---

## 11. Instruksi Siap Pakai untuk AI Coding Agent

Setelah kamu isi bagian 8 dan install antislop + buat `DESIGN.md` (bagian 7), potongan berikut bisa langsung jadi prompt awal ke AI coding agent:

> Buatkan situs portofolio Next.js (App Router, TypeScript, Tailwind CSS) sesuai PRD berikut, ikuti rules dari skill antislop yang sudah terpasang dan arah visual di DESIGN.md. Struktur: landing one-page (`/`) dengan Hero, Featured Projects, Skills, About singkat, Contact; dan halaman dinamis `/proyek/[slug]` untuk detail tiap proyek. Data proyek disimpan di `data/projects.ts` sebagai array terstruktur (title, slug, category, stack[], summary, problem, solution, result, links). Gunakan static export/ISR (bukan full SSR) karena akan di-deploy di server self-hosted di belakang Cloudflare Tunnel. Styling mobile-first, Lighthouse target ≥90. Sertakan meta tags SEO dan Open Graph per halaman. [tempel data proyek dari bagian 8 di sini]

---

*Dokumen ini bisa diiterasi — beri tahu saya bagian mana yang mau diperdalam (misalnya: draft `DESIGN.md`, draft copywriting tiap section, struktur data `projects.ts` yang siap pakai, atau langkah konkret setup Cloudflare Tunnel untuk domain ini) dan saya bantu detailkan.*
