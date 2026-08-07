# Konsep Analisis Strategis UGM — Posisi Data & Prinsip

**Tanggal**: 2026-08-07 | **Status**: DISETUJUI user (konsep ditegaskan ulang)

## 1. Hierarki Data (core BTD)

| Tier | Data | Peran | Fokus narasi |
|---|---|---|---|
| **INTI (utama)** | **EA** (Sparx: proses bisnis, risiko, KPI, 132K elemen) | Blueprint — apa yang seharusnya | ✅ Utama |
| **INTI (utama)** | **DSH** (ugm_dsh: pencarian, AI logs, feedback, KB) | Realita — apa yang dicari/dikeluhkan | ✅ Utama |
| Pendukung | **9router** (AI usage/cost) | Konteks biaya — memperkaya analisis | ⚪ Sekunder |
| Pendukung | **Qdrant** (semantic search infra) | Konteks infrastruktur | ⚪ Sekunder |

**Prinsip**: EA + DSH = bercerita. 9router + Qdrant = konteks (dipakai untuk memperkaya, BUKAN fokus).

## 2. Core BTD = 3 Pilar

1. **Proses Bisnis** — EA: 132K elemen, 6.151 diagram, 2.604 risiko, 47.925 proses, 481 unit
2. **Data Universitas** — DSH: 3.812 pencarian, 2.362 AI query, 338 Q&A, 404 fasilitas, 89.774 KB
3. **Analisis Strategis** — membaca gap & sinyal → rekomendasi pengambilan keputusan

## 3. Pola Pikir Strategis

```
EA (blueprint)  ×  DSH (realita)  →  GAP & SINYAL  →  REKOMENDASI
  "seharusnya"      "kenyataan"        analisis           keputusan
```

- Proses X dirancang di EA ↔ permintaan Y di DSH → gap → rekomendasi
- Risiko Z tanpa mitigasi (EA) ↔ topik populer dicari (DSH) → prioritas perbaikan
- 9router: hanya dipakai saat relevan (mis. "perbaiki RAG butuh berapa token/cost")
- Qdrant: hanya konteks (mis. "knowledge gap karena index belum lengkap")

## 4. Overview = SINTESIS, bukan KPI berdampingan

Overview dashboard strategis harus SATU NARASI yang menghubungkan:
"proses X di EA ↔ permintaan Y di DSH → gap Z → rekomendasi"

BUKAN: deretan KPI per dashboard tanpa keterkaitan.

## 5. Konsekuensi Desain

- **Overview**: narasi sintesis EA×DSH (proses ↔ kebutuhan publik), 9router/qdrant sebagai konteks
- **Bagian EA**: proses bisnis, risiko, KPI, kematangan unit
- **Bagian DSH**: kebutuhan sivitas, kualitas layanan AI, knowledge base
- **Cross-domain**: gap proses vs layanan (INTI)
- **9router/qdrant**: lampiran pendukung, bukan bagian utama

## 6. Repositori

- Repo ini: https://github.com/dedieko-priyadi/ugm-strategic-analysis
- Data pipeline: collection-engine (charts.db — EA + DSH + 9router)
- Dashboard inti: ea-decision-dashboard, dsh-analytics-dashboard
