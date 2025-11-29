---
title: "Kiểm tra Vector Store và Đồng bộ dữ liệu"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 5.3.2 </b> "
---

#### Mục tiêu

Trước khi AI có thể trả lời, dữ liệu phải được nạp vào kho lưu trữ vector (Vector Store). Chúng ta sẽ thực hiện quy trình kiểm tra "Trước và Sau" để thấy rõ dữ liệu được Bedrock tự động mã hóa và lưu trữ vào OpenSearch như thế nào.

#### Các bước thực hiện

**Bước 1: Kiểm tra Vector Store (Trạng thái Rỗng)**

Chúng ta sẽ truy cập trực tiếp vào Amazon OpenSearch Serverless để xác nhận rằng chưa có dữ liệu nào tồn tại.

1.  Tại thanh tìm kiếm AWS Console, gõ `OpenSearch` và chọn dịch vụ **Amazon OpenSearch Service**.
2.  Tại menu bên trái, mục **Serverless**, chọn **Collections**.
3.  Click vào tên Collection vừa được Bedrock tự động tạo (thường có tên dạng `bedrock-knowledge-base-...`).

> ![Ảnh minh họa danh sách Collections trong OpenSearch](link_anh_opensearch_collections)

4.  Tại trang chi tiết Collection, nhấn nút **Open Dashboard** (nằm ở góc trên bên phải màn hình).
    - _Lưu ý:_ Nếu được hỏi đăng nhập, hãy sử dụng thông tin đăng nhập AWS hiện tại.

> ![Ảnh minh họa nút Open Dashboard trong trang chi tiết Collection](link_anh_open_dashboard_btn)

5.  Trong giao diện OpenSearch Dashboard:
    - Click biểu tượng **Menu (3 gạch ngang)** ở góc trên cùng bên trái.
    - Chọn **Dev Tools** (thường nằm ở dưới cùng danh sách menu).

> ![Ảnh minh họa menu chọn Dev Tools trong Dashboard](link_anh_menu_devtools)

6.  Tại khung **Console** (bên trái), nhập lệnh sau để kiểm tra dữ liệu:
    ```
    GET _search
    {
      "query": {
        "match_all": {}
      }
    }
    ```
7.  Click nút **Play (Run)** (hình tam giác nhỏ bên cạnh dòng lệnh).
8.  **Kết quả:** Quan sát khung bên phải, phần `hits` -> `total` -> `value` là **0**.

> ![Ảnh minh họa kết quả Dev Tools trả về giá trị 0](link_anh_devtools_empty)

**Bước 2: Đồng bộ dữ liệu**

Bây giờ chúng ta sẽ kích hoạt Bedrock để đọc file từ S3 và đổ vào OpenSearch.

1.  Quay lại tab **Amazon Bedrock** trên trình duyệt.
2.  Chọn mục **Knowledge bases** ở menu trái và click vào tên KB bạn vừa tạo.
3.  Kéo xuống phần **Data source**, đánh dấu chọn (tick) vào ô tròn cạnh tên data source (`s3-datasource`).
4.  Click nút **Sync** (Màu cam).

> ![Ảnh minh họa chọn Data Source và nhấn nút Sync](link_anh_click_sync_btn)

5.  **Chờ đợi:**
    - Quá trình này sẽ mất từ **5 - 10 phút** tùy thuộc vào dung lượng tài liệu mẫu.
    - Hãy đợi đến khi cột **Sync status** chuyển từ `Syncing` sang `Available`.

> ![Ảnh minh họa trạng thái Sync thành công Available](link_anh_sync_status_available)

**3: Kiểm tra lại Vector Store (Có dữ liệu)**

Sau khi Bedrock báo Sync xong, chúng ta quay lại kho chứa để kiểm chứng dữ liệu đã được nạp thành công.

1.  Chuyển sang tab **OpenSearch Dashboard** (vẫn đang mở ở Bước 1).
2.  Tại **Dev Tools**, nhấn nút **Play (Run)** một lần nữa với lệnh cũ:
    ```
    GET _search
    {
      "query": {
        "match_all": {}
      }
    }
    ```
3.  **Kết quả:**
    - Phần `hits` -> `total` -> `value` sẽ lớn hơn **0** (ví dụ: 10, 20... tùy số lượng đoạn văn bản).
    - Bạn sẽ thấy chi tiết các vector (dãy số) và nội dung văn bản (text) được lưu trong mục `_source`.

> ![Ảnh minh họa kết quả Dev Tools hiển thị dữ liệu đã được sync](link_anh_devtools_populated)

**Chúc mừng!** Bạn đã hoàn thành việc xây dựng "bộ não" cho AI. Dữ liệu đã được mã hóa và nằm an toàn trong Vector Database, sẵn sàng để truy xuất.
