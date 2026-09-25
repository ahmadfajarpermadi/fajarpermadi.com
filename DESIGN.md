# DESIGN.md — fajarpermadi.com

Arah visual untuk AI coding agent (dipakai bersama skill `antislop`). File ini yang mengisi bagian "keindahan" yang tidak diurus antislop — jadi setiap keputusan warna/tipografi/layout di bawah ini final kecuali kamu ubah sendiri.

## Kenapa arah ini yang saya pilih

Kamu security-minded (desain sistem anti-kecurangan presensi PKKMB), infra-minded (self-host di STB, Cloudflare Tunnel), dan data/AI-minded (CareerPath AI, backtesting HYPE Signal Analyzer). Identitas ini lebih dekat ke "engineer yang presisi dan bisa dipercaya" daripada "startup founder yang flashy". Jadi arahnya: **dark-mode-default, terminal/technical-inspired, minim dekorasi** — bukan gradient-heavy SaaS-landing-page look yang justru terasa generik untuk profil sepertimu. Kalau ini tidak sesuai selera kamu, ganti bagian palet & tipografi di bawah — strukturnya tetap valid.

---

## 1. Mood

Presisi, tenang, jujur. Bukan "hype startup", bukan juga "portofolio kampus yang penuh clip art". Referensi rasa (bukan untuk ditiru identik, cuma acuan level polish): halaman dokumentasi teknis yang dirawat baik (mis. dokumentasi Stripe, GitHub dark theme), bukan landing page marketing.

Tiga kata kunci kalau agent butuh satu baris: **precise, quiet, technical.**

## 2. Color Palette

Dark mode sebagai default (bukan cuma "ada opsi dark mode" — ini basis utamanya), karena cocok dengan tema teknikal/terminal dan portofolio developer pada umumnya dilihat oleh audiens yang nyaman di dark mode.

```
--bg:           #0A0B0D   /* nyaris hitam, bukan pure #000 — biar tidak "harsh" */
--bg-elevated:  #131417   /* untuk card/section yang perlu naik satu layer */
--border:       #24262B   /* border tipis, bukan shadow tebal */
--text:         #E8E9EB   /* teks utama, bukan pure white */
--text-muted:   #8A8D93   /* teks sekunder, caption, meta info */
--accent:       #4ADE80   /* satu warna aksen — hijau terminal, dipakai HEMAT */
--accent-dim:   #1F3D2C   /* versi redup accent untuk background badge/tag */
```

Aturan pakai:
- **Satu warna aksen saja** (`--accent`). Dipakai untuk: link aktif, CTA utama, status indicator ("open to work"), highlight angka/metrik penting di studi kasus proyek. Jangan dipakai untuk dekorasi/border yang tidak fungsional.
- Tidak ada gradient sebagai elemen dekoratif (hero background gradient, button gradient, dsb). Kalau butuh gradasi, hanya untuk subtle depth (mis. radial glow sangat halus di belakang hero, opacity rendah), bukan sebagai identitas visual utama.
- Light mode: opsional untuk v2, bukan prioritas v1. Kalau dibuat, cukup invert dasar (bg putih pucat `#FAFAFA`, text `#1A1B1E`, accent tetap sama tapi kontras disesuaikan).

## 3. Typography

```
--font-mono:  'JetBrains Mono', 'IBM Plex Mono', monospace   /* heading, label, badge stack, angka metrik */
--font-sans:  'Inter', 'Manrope', sans-serif                  /* body text, paragraf deskripsi */
```

- **Heading pakai monospace.** Ini elemen paling menentukan "rasa" technical-nya — h1/h2/nama proyek/label section semua monospace, huruf besar-kecil biasa (jangan all-caps kecuali untuk label kecil seperti eyebrow text).
- Body text (deskripsi proyek, about) pakai sans-serif supaya tetap nyaman dibaca panjang — monospace penuh di body itu salah satu pola "AI slop" yang justru harus dihindari (susah dibaca, terasa dipaksakan).
- Badge stack teknologi (Next.js, n8n, dst) pakai monospace ukuran kecil dalam bentuk tag/pill tipis, bukan icon logo berwarna-warni.
- Skala ukuran: jangan lebih dari 5 ukuran font di seluruh situs (h1, h2, body, small, micro). Konsistensi > variasi.

## 4. Layout & Spacing

- Grid berbasis 8px. Semua padding/margin kelipatan 8 (8, 16, 24, 32, 48, 64, 96).
- Max-width konten: ~720-800px untuk teks panjang (studi kasus proyek), lebih lebar untuk grid kartu proyek.
- Whitespace generos di antar-section — jangan padat. Bagian ini yang paling sering dilanggar hasil AI-generated default (semua ditumpuk rapat).
- Section dipisah dengan whitespace vertikal besar (min 96-128px antar section besar), **bukan** garis divider berat atau card berbayang tebal.
- Card proyek: border tipis 1px (`--border`), tanpa shadow tebal, radius kecil (6-8px) — bukan card "floating" dengan shadow besar khas template AI-generated.

## 5. Komponen

- **Hero:** teks kiri-align (bukan center-align generik), status badge kecil ("open to internship") dengan dot indicator warna accent yang berdenyut halus (opsional, subtle), tanpa ilustrasi 3D/blob/mesh gradient generik.
- **Project card:** judul (mono) → satu baris deskripsi problem→solusi (sans) → baris tag stack (mono, kecil) → link. Tanpa icon-icon dekoratif yang tidak fungsional.
- **Metrik/angka penting** (mis. "cosine similarity 50%+", "15 test case", "10.322 sampel"): tampilkan besar, monospace, warna accent — ini elemen paling kuat untuk menunjukkan hasil nyata ke recruiter, jangan dikubur dalam paragraf.
- **Tombol:** flat, border tipis atau solid accent untuk CTA utama saja (maksimal satu tombol solid-accent per layar), sisanya ghost/outline.
- **Kode/terminal snippet** (kalau ada, mis. potongan konfigurasi Cloudflare Tunnel): tampilkan sebagai block dengan bg `--bg-elevated`, font mono, tanpa syntax-highlighting norak — cukup satu-dua warna saja.

## 6. Imagery

- Tidak ada stock photo, tidak ada ilustrasi generic (orang-orangan flat design, ikon sparkle/AI-magic).
- Screenshot asli dari proyek (dashboard presensi PKKMB, notebook CareerPath AI, dsb.) adalah visual utama — bukan mockup device generik yang tidak menunjukkan apa-apa.
- Kalau butuh diagram (mis. alur sistem keamanan presensi QR), buat sebagai diagram teknikal sederhana (garis + label mono), bukan diagram infografis penuh warna.

## 7. Motion

- Minim. Transisi hover 150-200ms ease-out pada link/tombol, fade-in halus saat scroll masuk viewport (opsional, jangan berlebihan/staggered heboh).
- Tidak ada animasi partikel, typing-effect judul, atau confetti — pola ini biasanya justru terasa "AI slop" ketimbang impresif.

## 8. Do / Don't cepat

**Do:**
- Angka dan hasil nyata ditonjolkan
- Satu warna aksen, dipakai konsisten dan hemat
- Whitespace luas
- Copy jujur dan spesifik (biarkan `antislop-copywriting` yang jaga ini)

**Don't:**
- Gradient sebagai identitas visual
- Badge "AI-Powered" / "Next-Gen" / bahasa hype lain
- Card dengan shadow tebal ala template SaaS generik
- Statistik yang tidak bisa dibuktikan/tidak relevan (mis. "99.9% client satisfaction" tanpa sumber)
- Icon logo berwarna-warni untuk tiap tech stack (cukup teks mono dalam pill)
