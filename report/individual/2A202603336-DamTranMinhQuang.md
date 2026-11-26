# Báo cáo Day 13 — Đàm Trần Minh Quang, 2A202603336

> **Cách dùng mẫu này:** đổi tên file thành `<MSSV>_<HoTen>.md` (họ tên không dấu, viết liền), ví dụ `2A202600123_NguyenVanAn.md`. Đổi tên, đừng chép thành file thứ hai.
>
> Xoá mọi dấu TODO và dòng gợi ý (dòng bắt đầu bằng `>`). Mỗi con số lấy từ **bảng A** hoặc **phiếu tự kiểm** trong `submission/`, kèm đơn vị (m, °). Ảnh để trong `report/individual/images/` (nộp LMS trong file zip, không commit); trong báo cáo chỉ ghi **tên file ảnh**. Báo cáo này nằm trên repo public: không chép biển số, chữ trên biển hiệu hay biển chỉ đường, tên đường, địa danh; nhắc tới bạn khác thì ghi MSSV, không ghi họ tên. Cả báo cáo ~2 trang.

## 1. Kết luận trước
Mã số: 2A202603336 
Task: `D13-2A202603336 `
10 frame của bạn: s01f17, s01f34, s02f06, s02f28, s03f04, s03f50, s04f23, s04f44, s05f07, s05f39.
Hệ điều hành: Windows 11.
Trình duyệt: Edge.
Phiên bản CVAT (tên tài khoản → About): v2.81.0.
MSSV bạn ngồi cạnh: 2A202603267.
Tổng bao nhiêu cuboid: 93.
Frame nào ít nhất và vì sao: s01f34, ít phương tiện và các phương tiện ở xa.
`selfcheck` cờ bao nhiêu cuboid trên tổng số: 8/93.
Bạn tin phần nào nhất: Các vật ở gần.
Phần nào còn yếu nhất: Vật xa.

Cách dùng CVAT, 3 dòng:

- Đổi góc nhìn (nhìn từ trên xuống, xoay, dời): con lăn để zoom, click trái để xoay, click phải để rời.

- Vẽ và chỉnh một cuboid (Shape, nháy đúp, Top/Side/Front): nhấn Cuboid, Shape rồi double click vào chỗ muốn vẽ thì sẽ hiện ra 3 hướng Top/Side/Front rồi điều chỉnh hộp để bao hết các điểm point cloud của vật đó.

- Bật mũi tên hướng (Cuboid orientation) và xem cuboid trên ảnh camera (`preview`).

## 2. Đọc frame (Bước 2)
Hai frame đọc kỹ. Ảnh: `t1-s01f17-3d`, `t1-s01f34-top` (ảnh nhìn từ trên xuống, có đánh dấu phía trước, +x, +y).

**Note: Frame 1 chỉ vẽ được 7 cuboid.

| Frame | Phía trước xe ở cạnh nào của ảnh nhìn từ trên xuống; +x, +y chỉ về đâu | Mặt đường (phẳng/dốc; thấp hơn LiDAR ~ m) | Vật xa nhất đọc được (~ m) | Loại vật thấy | Vật phía sau / hai bên | Cụm chưa đọc được |
|---|---|---|---|---|---|---|
| s01f17 | Phía trước xe hướng về cạnh đỏ (mũi tên xe chỉ từ đuôi lên đầu); +x (đỏ) sang trái, +y (xanh lá) về phía sau | Phẳng | 40 | car, bus | car | Không |
| s01f34 | Phía trước xe hướng về cạnh đỏ (mũi tên xe chỉ từ đuôi lên đầu); +x (đỏ) sang trái, +y (xanh lá) về phía sau | Phẳng | 40 | car | car | Không |

3 điều **chỉ camera** cho biết: màu sắc, bề mặt, bối cảnh.

3 điều **chỉ LiDAR** cho biết: tọa độ 3D theo mét, khoảng cách và vị trí tương đối của các vật, hình dạng không gian.

Tám frame lướt: s02f06, s02f28, s03f04, s03f50, s04f23, s04f44, s05f07, s05f39.

| Frame | Phía trước ở cạnh nào của ảnh nhìn từ trên xuống | Điều lạ (nếu có) |
|---|---|---|
| s02f06 | Cạnh xanh ngược lại | |
| s02f28 | Cạnh xanh ngược lại | |
| s03f04 | Cạnh xanh ngược lại | |
| s03f50 | Cạnh xanh ngược lại | |
| s04f23 | Cạnh xanh ngược lại | |
| s04f44 | Cạnh xanh ngược lại | |
| s05f07 | Cạnh xanh ngược lại | |
| s05f39 | Cạnh xanh ngược lại | |

## 3. Ba cuboid có hướng dẫn (Bước 3)
Ảnh: `t2-a-car`, `t2-b-bus-truck`, `t2-c-ped-cyclist`.

| Vật | Frame, idx | Class | Mũi tên yaw đúng hướng? | Đáy chạm đường? | Đã kiểm Top/Side/Front + ảnh? | Kích thước trong bảng 4.3? |
|---|---|---|---|---|---|---|
| (a) xe con gần | s01f17, 5 | car | Có | Có | Có | Dài 3,8 – 5,0 Rộng 1,70 – 1,90 Cao 1,40 – 1,60 |
| (b) xe buýt hoặc xe tải | s01f17, 4 | bus | Có | Có | Có |  Dài 10,0 – 12,5 Rộng 2,50 – 2,60 Cao	3,00 – 3,50 |
| (c) người đi bộ hoặc xe hai bánh | s02f06, 13 | cyclist | Có | Có | Có | Dài 1,8 – 2,3 Rộng 0,70 – 0,95 Cao 1,40 – 1,80 |

Vòng hiệu chuẩn: Không, Cả lớp chốt cách hiểu guideline: thấy vật trên ảnh 2D nhưng trên 3D không có point cloud thì không vẽ, Không có.

## 4. Bốn hiện tượng chất lượng (Bước 4)
Nguyên nhân ghi là **giả thuyết**. Frame mượn thì ghi rõ nguồn: task chung, hoặc MSSV của bạn cho mượn.

| Hiện tượng | Frame / tên ảnh / nguồn | Nguyên nhân (giả thuyết) | Thấy gì trên point cloud | Hệ quả khi gán (theo guideline) |
|---|---|---|---|---|
| 1. Bóng che | Frame 1/s01f17/cá nhân | Xe buýt che khuất một góc phía sau | Hai bên góc bị che vẫn có điểm dày, nhưng vùng ngay phía sau xe buýt ít hoặc không có điểm | Bật thuộc tính occluded; cuboid vẫn bao phần bị che nếu suy luận được, không xem vùng khuất là đường trống |
| 2. Thưa ở xa | Frame 1/s01f17/cá nhân | Vật ở xa nên LiDAR thu được ít điểm hơn | Phần đuôi xe chỉ có vài điểm point cloud | Chỉ gán khi thấy khoảng 15–20% thể tích cuboid hoặc có đủ cơ sở suy luận từ ảnh; cuboid sai vị trí/kích thước sẽ tạo nhãn nhiễu, làm giảm độ chính xác phát hiện |
| 3. Phản xạ thấp / ít điểm bất thường | Frame 7/s04f23/cá nhân | Bề mặt tối, kính hoặc góc phản xạ có thể làm tín hiệu LiDAR yếu hơn (giả thuyết) | Một vật có ít điểm hơn rõ rệt so với vật ở khoảng cách tương tự | Đối chiếu ảnh và hình dạng; chỉ gán khi đủ cơ sở, không nới cuboid để bao điểm nhiễu; nếu quá khó quan sát thì bỏ qua và ghi LOW_VISIBILITY |
| 4. Điểm lạ | Frame 6/s03f50/cá nhân | Có thể do nhiễu đo hoặc phản xạ từ bề mặt/vật ngoài vùng camera quan sát (giả thuyết, chưa xác định) | Xuất hiện một cụm điểm không khớp với vật nào quan sát được | Không gán cụm điểm thành vật/cuboid để tránh tạo nhãn giả |

## 5. Số từ cuboid của tôi (Bước 5)
Lấy từ `submission/D13-<MÃ SỐ>-bangA.csv`; số điểm lấy từ cột `points_in` của `-tukiem.csv`. Mặt đường khoảng −1,7 m: z đáy lệch hơn 0,3 m là lơ lửng hoặc chìm.

| Cuboid (frame, idx, class) | z | h | z đáy = z − h/2 | dist_m | r = √(x²+y²+z²) | yaw_deg | Nhận xét (lơ lửng / chìm / chạm đường) |
|---|---|---|---|---|---|---|---|
| s03f04, 6, Car | −1.024 m | 1.505 m | −1.777 m | 3.72 m | 3.86 m | 271.9° | Chạm đường |
| s04f23, 24, Cyclist | −0.874 m | 1.521 m | −1.635 m | 22.25 m | 22.27 m | 0.0° | Chạm đường |
| s01f17, 7, Car | −0.517 m | 1.669 m | −1.352 m | 46.72 m | 46.72 m | 269.6° | Hơi lơ lửng (lệch khoảng 0.35 m) |

Cuboid gần nhất là s03f04, idx 6 (Car), `dist_m` = 3.72 m và r = 3.86 m; xa nhất là s01f17, idx 7 (Car), `dist_m` = 46.72 m và r = 46.72 m. Cyclist s04f23, idx 24 có kích thước l × w × h = 1.953 × 0.955 × 1.521 m; nếu đối chiếu với xe máy có người trong bảng 4.3 thì chiều rộng nhỉnh hơn giới hạn trên 0.005 m. Car s04f23, idx 4 có kích thước 4.343 × 1.670 × 1.499 m; nếu đối chiếu với sedan/hatchback thì chiều rộng thấp hơn giới hạn dưới 0.030 m. Chênh lệch nhỏ có thể do kích thước vật hoặc sai số khi đặt hộp; cần kiểm lại với ảnh và point cloud, không kết luận chỉ từ bảng tham chiếu. Xe cùng chiều s01f17, idx 1 có `yaw_deg` = 270.2°; xe ngược chiều s02f28, idx 1 có `yaw_deg` = 90.0°, phù hợp gần 270° và 90°.

Mật độ theo khoảng cách (4 cuboid ở các `dist_m` khác nhau):

| Cuboid (frame, idx, class) | dist_m | Số điểm (`points_in`) |
|---|---|---|
| s01f17, 1, Car | 8.21 m | 1604 |
| s01f17, 4, Car | 14.47 m | 765 |
| s01f17, 5, Car | 21.91 m | 289 |
| s01f17, 6, Car | 34.35 m | 39 |

Ở các mẫu này, xe cách 34.35 m xa gấp khoảng 4.2 lần so với xe cách 8.21 m, nhưng số điểm giảm từ 1604 còn 39 (khoảng 2.4%, tức còn khoảng 1/41). Xu hướng giảm theo khoảng cách giống đường cong bài giảng; ở 30–40 m có 39 điểm, thấp hơn mốc tham chiếu khoảng 72 điểm. 

Hai cuboid đã sửa sau `preview`/`selfcheck`: 

- Frame 3/s02f06 có đáy vật bị chìm xuống, sửa lại để bằng với mặt đường.

- Frame 4/s02f28 có vật bị ngược hướng, sửa lại để đúng hướng.

MSSV bạn ngồi cạnh: 2A202603267. Hai con số đã đối chiếu và kết quả hầu hết khớp, chỉ lệch vài trường hợp do không đọc kĩ guideline.

## 6. Ý nghĩa của nhãn, cách dùng AI và điều còn chưa chắc
Mô hình học vị trí và kích thước của vật trong không gian thực, nên cuboid 3D được đo bằng mét chứ không phải pixel, vốn phụ thuộc vào góc nhìn và độ phân giải ảnh. Vật thưa điểm cần quy tắc riêng vì ít dữ liệu hình dạng để xác định ranh giới; chỉ gán khi có đủ bằng chứng, nếu không thì tránh tạo nhãn sai.

- Công cụ: Copilot trong VS Code hỗ trợ viết báo cáo.
- Câu hỏi chính: ảnh hưởng của point cloud thưa tới việc gán cuboid và cách diễn đạt các phần báo cáo.
- Cách dùng kết quả: tham khảo để biên tập câu chữ và giải thích.

Điều còn chưa chắc: nguyên nhân cụm điểm lạ ở s03f50 chưa được xác định; nhiễu đo hoặc phản xạ bất thường chỉ là giả thuyết. Thông tin về lỗi phát hiện sau hạn chưa được ghi lại.
