# BÀI TẬP LỚN MẠNG MÁY TÍNH (FIT4006) — NHÓM 10
**Đề tài 17:** VLAN cho ba phòng ban (`VLAN 10 KeToan`, `VLAN 20 NhanSu`, `VLAN 30 KyThuat`)  
**Giảng viên hướng dẫn:** ThS. Lê Văn Phong  
**Lớp:** CNTT 18-03  
**Sinh viên thực hiện:**
- Nguyễn Thành Đạt
- Nguyễn Hoàng Hải

---

## 1. Cấu trúc thư mục bàn giao
- `BaoCao/`
  - `FIT4006_CNTT18-03_Nhom10_DeTai17.docx` — Báo cáo Word hoàn chỉnh theo chuẩn Mẫu K18 (77 trang, 31 Hình, 37 Bảng)
  - `FIT4006_CNTT18-03_Nhom10_DeTai17.pdf` — Bản PDF xuất trực tiếp từ Word
- `PacketTracer/`
  - `DeTai17_VLAN_3PhongBan.pkt` — Tệp mô phỏng Cisco Packet Tracer 9 đã cấu hình VLAN, bảo mật và lưu `startup-config` vào NVRAM
- `CauHinh/`
  - `SW1_running-config.txt` — Toàn văn cấu hình `running-config` của Switch `SW1`
  - `SW1_startup-config.txt` — Toàn văn cấu hình `startup-config` trong NVRAM
- `MinhChung/` — Toàn bộ 39 ảnh chụp màn hình thật từ Cisco Packet Tracer (đã cắt gọn sạch viền) phục vụ kiểm thử `TC01–TC12`, `ipconfig` 9/9 PC, bảng địa chỉ MAC và Troubleshooting `3.6.1–3.6.3`

---

## 2. Tóm tắt quy hoạch mạng & Thông tin truy cập `SW1`
| Phòng ban | VLAN ID | Tên VLAN | Dải mạng / Subnet Mask | Cổng Switch (`SW1`) | Máy trạm & IP tĩnh (`GW: 0.0.0.0`) |
|---|---|---|---|---|---|
| Kế toán | `10` | `KeToan` | `192.168.10.0/24` (`255.255.255.0`) | `Fa0/1 – Fa0/3` | `KT1 (.10.11)`, `KT2 (.10.12)`, `KT3 (.10.13)` |
| Nhân sự | `20` | `NhanSu` | `192.168.20.0/24` (`255.255.255.0`) | `Fa0/4 – Fa0/6` | `NS1 (.20.11)`, `NS2 (.20.12)`, `NS3 (.20.13)` |
| Kỹ thuật | `30` | `KyThuat` | `192.168.30.0/24` (`255.255.255.0`) | `Fa0/7 – Fa0/9` | `KY1 (.30.11)`, `KY2 (.30.12)`, `KY3 (.30.13)` |
| Dự phòng | `1` (unused) | `default` | — | `Fa0/10–24, Gi0/1–2, Vlan1` | Đã vô hiệu hóa (`shutdown`) |

### Mật khẩu quản trị trên `SW1` (Cisco Catalyst 2960-24TT)
- **Console (`line con 0`):** `Console@123`
- **Privileged EXEC (`enable secret`):** `Cisco@123`
- **VTY (`line vty 0 15`):** `Vty@123`
- Cấu hình đã bật `service password-encryption` và lưu đồng bộ vào NVRAM (`copy running-config startup-config`).
