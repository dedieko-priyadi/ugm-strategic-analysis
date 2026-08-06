# Analisis Strategis UGM — Enterprise Architecture × DSH × AI Usage

**Tanggal**: 2026-08-07 | **Repo**: https://github.com/dedieko-priyadi/ugm-strategic-analysis
**Tujuan**: Analisis level pimpinan (Rektorat & BTD) dari 3 sumber data terverifikasi.

---

## 1. Sumber Data (semua terverifikasi)

| Sumber | Data | Makna |
|---|---|---|
| **EA** (Sparx, eaugm_2025) | 132.183 elemen, 6.151 diagram, 2.604 risiko, 47.925 proses, 481 unit | Blueprint — "apa yang seharusnya" |
| **DSH** (ugm_dsh, search&dsh) | 3.812 pencarian web, 2.362 AI query, 338 Q&A, 41 feedback, 89.774 index | Realita — "apa yang dicari & dikeluhkan" |
| **9router** | 30K+ request AI, $704/minggu, per user/model | Ekonomi — "berapa biaya AI" |

## 2. Temuan Utama

### 2.1 Kualitas AI Chatbot Bermasalah (BTD — prioritas #1)
- **5 feedback negatif konkret**: "jawaban tidak sesuai", "informasi rancu", "text terputus dan penjelasan tercampur", "jawaban tidak relevan", "jawaban tidak match"
- Total 36 positif vs 5 negatif (88% puas) — tapi keluhan spesifik = RAG pipeline perlu perbaikan
- `ai_knowledge_gaps` (1 gap) + `failed_searches` (9) = query yang tidak terjawab

### 2.2 Chatbot Belum Diadopsi Publik (BTD)
- **Hanya 4 unik IP** di ai_search_logs (Mar–Agt 2026) — hampir tidak ada pengguna nyata
- Bandingkan search web 3.812 (kanal lain, lebih banyak) → chatbot AI belum dipublikasikan/dipromosikan
- Query/sesi 28 (2.362/84 sesi) = engagement TINGGI saat dipakai → potensi besar jika dipublikasi

### 2.3 Gap Kebutuhan vs Knowledge Base (University)
- Query populer: beasiswa (43), bencana (50), jokowi (49) — topik publik
- `popular_searches` + `search_trends` = sinyal konten yang harus diperbarui di knowledge base
- Entity clicks 30d: **service 20** (paling diklik!), news 11, publication 8 → layanan digital paling dicari

### 2.4 Optimasi Biaya AI (BTD)
- 1.147.769 token total; model qwen2.5:0.5b (65,3%) + gpt-4o-mini (32,1%)
- Action distribution: detect_intent 1.398 (59%) vs rag_answer 929 (39%)
- Cross-check 9router: total AI spend $704/minggu — DSH bagian dapat diukur per action

### 2.5 Manajemen Risiko UGM Gap Besar (University)
- EA: 2.604 risiko, hanya 498 (19,1%) ter-mitigasi, 2.106 tanpa mitigasi
- 47.851 proses (99,8%) tanpa KPI → manajemen kinerja belum terukur
- Hanya 15 proses terhubung regulasi eksplisit

### 2.6 Model AI: qwen lokal untuk intent detection = efisien
- qwen2.5:0.5b (65% action) = model lokal murah untuk detect_intent — arsitektur sudah efisien
- gpt-4o-mini hanya untuk rag_answer (jawaban) — tepat guna

## 3. Rekomendasi Prioritas

| # | Rekomendasi | Level | Data |
|---|---|---|---|
| 1 | Perbaiki kualitas RAG (5 feedback negatif konkret) | BTD | ai_feedback |
| 2 | Publikasikan chatbot (hanya 4 IP — belum diadopsi) | BTD | ai_search_logs |
| 3 | Isi knowledge gaps (beasiswa/bencana topik populer) | University+BTD | popular_searches, gaps |
| 4 | Optimasi model AI (qwen utk intent = hemat) | BTD | ai_search_analytics |
| 5 | Mitigasi risiko kritis (2.106 tanpa mitigasi) | University | EA r9_ea_* |
| 6 | Penetapan KPI proses (99,8% belum terukur) | University | EA |
| 7 | Cross-domain: proses EA vs layanan DSH (gap digitalisasi) | University | EA+DSH |

## 4. Arsitektur Data Pipeline (sudah jalan)

```
EA DB (SQL Server) → collect_ea_ugm.py → charts.db r9_ea_*
DSH DB (MySQL ugm_dsh) → collect_dsh.py → charts.db r9_dsh_*
9router (SQLite) → collect_9router_detail.py → charts.db r9_* (usage)
→ Dashboards (ea-decision :8540, dsh-analytics :8541, 9router-dash :8527)
```

## 5. Repositori Terkait
- ea-decision-dashboard: https://github.com/dedieko-priyadi/ea-decision-dashboard
- dsh-analytics-dashboard: https://github.com/dedieko-priyadi/dsh-analytics-dashboard
- ea-ugm-explorer: https://github.com/dedieko-priyadi/ea-ugm-explorer
- collection-engine: https://github.com/dedieko-priyadi/collection-engine
