# Rencana: UGM Strategic Dashboard

**Tanggal**: 2026-08-07 | **Status**: RENCANA (menunggu wujud)

## Tujuan
Satu dashboard level pimpinan yang menyintesis EA (blueprint) × DSH (realita) sebagai INTI,
dengan 9router/qdrant sebagai konteks pendukung. Bukan kumpulan KPI — SATU NARASI keputusan.

## Struktur Tab

### Tab 1 — Executive Overview (SINTESIS, inti)
Narasi terhubung EA×DSH:
- **KPI inti**: proses (47.925) ↔ pencarian publik (3.812) ↔ layanan digital (258 EA / 659 DSH)
- **3 Gap utama** (auto-computed):
  1. Proses tanpa KPI (99,8%) — EA
  2. Risiko tanpa mitigasi (80,9%) — EA
  3. Kebutuhan publik vs knowledge base (topik dicari tapi gap) — DSH
- **Sinyal utama**: entity paling diklik (service 20/30d), feedback negatif teratas
- Konteks kecil: biaya AI total (9router) — 1 baris saja

### Tab 2 — Proses Bisnis (EA)
- Kematangan digital per unit (proses vs aplikasi per package)
- Risk map (top proses berisiko, gap mitigasi)
- KPI coverage per unit
- Top diagram terbesar (kandidat restrukturisasi)

### Tab 3 — Kebutuhan Publik (DSH)
- Top query chatbot + pencarian web
- Knowledge gaps (topik dicari tapi tidak terjawab)
- Feedback pengguna (negatif konkret)
- Entity clicks 30d (apa yang paling diakses)

### Tab 4 — Cross-Domain EA×DSH (INTI analisis)
- Proses EA ↔ layanan DSH per unit (gap digitalisasi)
- "Dicari publik tapi belum di arsitektur" (query layanan vs EA Layanan)
- Topik populer ↔ proses EA terkait (apakah prosesnya ada?)

### Tab 5 — Konteks Pendukung (9router/Qdrant — sekunder)
- Biaya AI per bulan (ringkas)
- Token per model
- Catatan: ini hanya konteks, bukan fokus

## Data Flow
```
charts.db (r9_ea_* + r9_dsh_* + r9_* 9router)
  → strategic-dashboard (Streamlit, read-only)
  → Tab 1-5 di atas
```

## Port & URL
- Port: 8542 (belum dipakai)
- Subpath: /strategic/
- Funnel: https://nuc-nuc7i5bnh-1.tail758353.ts.net/strategic/

## Deploy
```bash
cd ~/strategic-dashboard
sg docker -c "docker compose up -d --build"
sudo tailscale funnel --bg --set-path /strategic/ http://localhost:8542/strategic/
```
