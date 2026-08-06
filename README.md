# UGM Strategic Analysis

Analisis strategis level pimpinan (Rektorat & BTD) dari data Enterprise Architecture (EA), Digital Services Hub (DSH), dan AI usage (9router).

## Dokumen Utama
- [ANALISIS-STRATEGIS-20260807.md](ANALISIS-STRATEGIS-20260807.md) — 6 temuan + 7 rekomendasi prioritas

## Sumber Data
| Sumber | Pipeline | Dashboard |
|---|---|---|
| EA (Sparx, 132K elemen) | collect_ea_ugm.py → charts.db | ea-decision-dashboard (:8540 /ea-decision/) |
| DSH (ugm_dsh) | collect_dsh.py → charts.db | dsh-analytics-dashboard (:8541 /dsh-analytics/) |
| 9router (AI usage) | collect_9router_detail.py → charts.db | 9router-dashboard (:8527 /9router-dash/) |

## Temuan Kunci (ringkas)
1. **2.106 risiko (80,9%) tanpa mitigasi** — EA
2. **99,8% proses tanpa KPI** — EA
3. **Chatbot AI belum diadopsi** (4 unik IP) tapi engagement tinggi (28 query/sesi) — DSH
4. **5 feedback negatif konkret** = kualitas RAG perlu perbaikan — DSH
5. **Service entity paling diklik** (20/30d) = layanan digital paling dicari — DSH
6. Topik populer (beasiswa, bencana) = gap konten knowledge base — DSH

## Repo Terkait
- https://github.com/dedieko-priyadi/ea-decision-dashboard
- https://github.com/dedieko-priyadi/dsh-analytics-dashboard
- https://github.com/dedieko-priyadi/ea-ugm-explorer
- https://github.com/dedieko-priyadi/collection-engine
