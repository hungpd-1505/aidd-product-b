# Product B — backlog LAB-5 (chuỗi kho lạnh, khách hư cấu)

- Mã học viên: `hungpd-1505`
- Đề: **Product B** — hệ thống quản lý kho lạnh 3 dải nhiệt cho một công ty logistics hư cấu

Repo này chỉ chứa markdown và issue do tôi tự viết. Không có RFP, không có đề gốc, không có bộ spec LAB-4; mọi chỗ cần dẫn spec đều ghi bằng mã (ví dụ `SCR023_SPEC`, `ROUTE_EVALUATE_HOURS_TECH`, `ADR-002`).

## Tổng quan

- **Nguồn break:** bộ thiết kế LAB-4 (wireframe, kiến trúc, 8 ADR, DB/API, screen spec, technical design) **bản đã nộp ngày 2026-10-09**.
- **PREMISE có thay đổi:** 23 dòng sửa spec, 21 giả định bổ sung, 4 hướng chốt — chi tiết ở [PREMISE.md](PREMISE.md). Phần còn lại bám nguyên LAB-4.
- **Backlog:** 12 epic · 127 issue · 246 sub-issue, dựng bằng sub-issue native của GitHub. 75 chỗ hở / mâu thuẫn của spec phát hiện khi break được ghi ở [task-breakdown.md](task-breakdown.md) §4.
- **Ràng buộc đặc thù** (giờ lái xe tải từ 2024, 3 dải nhiệt, 賞味期限 / 消費期限, 1/3–1/2, 日付逆転禁止, FEFO, truy xuất gạo / thịt bò, HACCP) đều có issue riêng mang nhãn `constraint:*`.
- **Sprint giả lập:** chưa chạy — cập nhật ở phần 2 (chấm SWP, quy giờ, Iteration, báo cáo tiến độ).

## Link

- Repo: https://github.com/hungpd-1505/aidd-product-b
- GitHub Project: https://github.com/users/hungpd-1505/projects/3
- Báo cáo HTML chấm SWP: cập nhật ở phần 2
- Đã mở thử repo và Project bằng **cửa sổ ẩn danh** (không đăng nhập) ngày 2026-10-19: xem được board, issue và sub-issue.

## Cấu trúc repo

| File/thư mục | Nội dung |
|---|---|
| `README.md` | Tổng quan, link repo/Project/báo cáo, cấu trúc repo, bảng Spec → epic |
| `PREMISE.md` | Tiền đề: backlog khác bộ thiết kế LAB-4 đã nộp ở đâu (sửa spec, giả định, hướng chốt) |
| `task-breakdown.md` | Nguyên tắc chia task, Spec → issue, hạng mục ràng buộc đặc thù, chỗ hở của spec |
| `.gitignore` | Chặn file môi trường, tài liệu nguồn của khách (pdf/xlsx/docx) và file nháp |

Phần 2 sẽ thêm `estimate.md`, `progress-report.md`, `AI-report.md` và thư mục chứa báo cáo HTML.

## Spec → epic

| Spec (mã/file LAB-4, hoặc dòng PREMISE) | Epic trên Project (#số — tên) | Ghi chú (ràng buộc đặc thù) |
|---|---|---|
| `adr/` · `architecture/` · `specs/_common/` · `system-design/` (DB, API chung): `ADR-001`, `ADR-002`, `ADR-003`, `ADR-004`, `ADR-005`, `ADR-006`, `ADR-007`, `ADR-008`, `CORE_PLATFORM_DB`, `ERD_OVERVIEW_DB` · PREMISE P1-02, P1-04, P1-05, P1-06, P1-14, P2-01, P2-02, P2-03, P2-04, P2-05, P2-16, P3-04 | [#37](https://github.com/hungpd-1505/aidd-product-b/issues/37) — Thiết kế hệ thống & nền tảng (ADR, kiến trúc, NFR, đăng nhập, tích hợp) | — |
| `specs/master-data-approval/`: `APV_DECIDE_TECH`, `BAND_POLICY_PUBLISH_TECH`, `MASTER_DB`, `MST_PROPOSE_CHANGE_TECH`, `SCR005_SPEC`, `SCR006_SPEC`, `SCR007_SPEC` · PREMISE P1-02, P1-03, P1-10, P1-21, P2-06 | [#38](https://github.com/hungpd-1505/aidd-product-b/issues/38) — Dữ liệu chủ & duyệt thay đổi (maker-checker, ngưỡng dải nhiệt) | expiry-type, haccp-audit, shipping-window-1-3, temp-zone |
| `specs/receiving/`: `RCV_CHECK_LINE_TECH`, `RCV_CONFIRM_LOT_TECH`, `RECEIVING_DB`, `SCR010_SPEC` · PREMISE P1-03, P1-07, P1-17, P2-07, P2-08 | [#39](https://github.com/hungpd-1505/aidd-product-b/issues/39) — Nhập hàng & kiểm hàng tại dock | haccp-audit, temp-zone |
| `specs/inventory-quarantine/`: `INVENTORY_LOT_DB`, `QRN_DECIDE_TECH`, `SCR017_SPEC` · PREMISE P1-08, P1-09, P2-09, P2-14 | [#40](https://github.com/hungpd-1505/aidd-product-b/issues/40) — Tồn kho, cất hàng & cách ly | haccp-audit, temp-zone |
| `specs/order-allocation/`: `ALLOC_EXPLAIN_BLOCK_TECH`, `ALLOC_FUNC`, `ALLOC_ORDER_TECH`, `ORDER_DB`, `ORD_INTAKE_CSV_TECH`, `SCR019_SPEC` · PREMISE P1-10, P2-10 | [#41](https://github.com/hungpd-1505/aidd-product-b/issues/41) — Đơn hàng & phân bổ lô | date-reversal, expiry-type, fefo-allocation, shipping-window-1-3 |
| `specs/dispatch/`: `PICK_VERIFY_TECH`, `PRE_DISPATCH_CHECK_TECH`, `SCR021_SPEC`, `SCR022_SPEC` · PREMISE P1-11, P2-10 | [#42](https://github.com/hungpd-1505/aidd-product-b/issues/42) — Soạn hàng, xếp xe & kiểm trước xuất | date-reversal, expiry-type, temp-zone |
| `specs/route-planning/`: `DRIVER_HOURS_FUNC`, `ROUTE_BUILD_STOPS_TECH`, `ROUTE_EVALUATE_HOURS_TECH`, `ROUTE_INSERT_REST_TECH`, `ROUTE_PUBLISH_TECH`, `ROUTING_DB`, `SCR023_SPEC`, `SCR024_SPEC`, `SCR025_SPEC` · PREMISE P1-12, P1-13, P1-14, P1-20, P1-21, P2-11, P2-12, P2-13, P2-21 | [#1](https://github.com/hungpd-1505/aidd-product-b/issues/1) — Lập tuyến & giờ lái 2024 | driving-hours-2024 |
| `specs/delivery-pod/`: `POD_CAPTURE_TECH`, `POD_CLAIM_DB`, `POD_OFFLINE_SYNC_TECH`, `SCR028_SPEC` · PREMISE P1-15, P1-20, P1-22, P2-12, P2-14 | [#43](https://github.com/hungpd-1505/aidd-product-b/issues/43) — Giao hàng & bằng chứng giao (POD) | — |
| `specs/temperature-haccp/`: `ALARM_REVIEW_TECH`, `DEVIATION_ADVANCE_TECH`, `SCR032_SPEC`, `SCR033_SPEC`, `SCR034_SPEC`, `TEMPERATURE_DB`, `TEMP_EVALUATE_TECH`, `TEMP_INGEST_CSV_TECH` · PREMISE P1-08, P1-16, P1-23, P2-15 | [#44](https://github.com/hungpd-1505/aidd-product-b/issues/44) — Nhiệt độ, alarm, deviation & HACCP | haccp-audit, temp-zone |
| `specs/traceability-recall/`: `RECALL_DB`, `RECALL_RECONCILE_TECH`, `SCR036_SPEC`, `SCR037_SPEC`, `SCR038_SPEC`, `TRACE_LOT_TECH` · PREMISE P1-01, P1-17, P2-14, P2-16, P2-17, P3-01, P3-02 | [#45](https://github.com/hungpd-1505/aidd-product-b/issues/45) — Truy xuất nguồn gốc & thu hồi | haccp-audit, traceability-rice-beef |
| `specs/data-migration/`: `MIGRATION_INTERFACE_DB`, `MIG_APPLY_MAPPING_TECH`, `MIG_CLASSIFY_ROW_TECH`, `SCR046_SPEC` · PREMISE P2-17, P2-18, P2-19 | [#46](https://github.com/hungpd-1505/aidd-product-b/issues/46) — Di trú dữ liệu | traceability-rice-beef |
| `specs/administration/`: `RETENTION_DB`, `RET_PURGE_TECH`, `SCR047_SPEC` · PREMISE P1-02, P1-06, P1-18, P1-19, P1-23, P2-20 | [#47](https://github.com/hungpd-1505/aidd-product-b/issues/47) — Quản trị, báo cáo, audit & lưu trữ | haccp-audit |
