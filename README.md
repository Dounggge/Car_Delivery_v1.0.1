https://docs.google.com/document/d/1irU7zNE5DPvpSUbhjkfE3BoGf6dxIwlw5JNoj6OyhSg/edit?usp=sharing

# Car Delivery

**A 2D Top-Down Relaxing Driving Game**

*Prototype hoàn chỉnh sau khóa học Udemy — Lái xe, sống sót, tận hưởng nhạc chill.*

---

## Developer

- **Indie Developer:** Doung
- **Email:** hoangdoung123@gmail.com
- **GitHub:** [Dounggge](https://github.com/Dounggge)
- **Portfolio:** [Dounggg. - itch.io](https://dounggg.itch.io/)

---

## Tổng quan (Summary)

**Car Delivery** là một game đua xe 2D góc nhìn từ trên xuống (top-down) mang phong cách thư giãn, nơi người chơi chỉ cần lái, sinh tồn và đắm mình trong nền nhạc chill. Thử thách cốt lõi nằm ở việc giữ bình tĩnh, khéo léo né tránh chướng ngại vật và đưa ra những quyết định tức thời: đánh đổi tốc độ để an toàn, hay mạo hiểm thu thập vật phẩm nhằm đạt điểm số kỷ lục? Điểm được tính dựa trên tổng thời gian sống sót và số lượng vật phẩm thu thập – bạn trụ vững càng lâu, điểm số càng cao.

---

## Phân tích (Analysis)

### Ý tưởng (Idea)

Prototype được phát triển nhằm hoàn thiện kiến thức sau khóa học Udemy, tận dụng các tài nguyên (asset) có sẵn và bổ sung những phần còn thiếu. Dự án cũng là cơ hội để kiểm chứng ưu – nhược điểm của thể loại game “endless” chạy tuần hoàn.

#### Nhận định rút ra:
- Trong game endless, mỗi lượt chơi buộc phải có yếu tố ngẫu nhiên. Dù có thể tác động đến tính cân bằng (balance), lợi ích mà nó mang lại là duy trì sự bất ngờ một cách ổn định.
- Nên có nhiều hơn một bản đồ và tận dụng asset để tạo lời thoại (dialogue) cho xe sau một vài lần chơi – điều này giúp kiến tạo cảm giác tương tác liên tục.
- Cần đa dạng hóa vật phẩm và điều chỉnh độ khó theo từng màn chơi.

#### Vấn đề duy trì động lực với yếu tố ngẫu nhiên:
Khi hướng tới một bản demo có thể phát hành, câu hỏi then chốt cần giải quyết là: làm thế nào để yếu tố ngẫu nhiên – vốn được dùng để kích thích hứng thú – không trở thành nguyên nhân khiến người chơi rời bỏ? Nếu tính cân bằng thiếu đi cơ chế hỗ trợ ẩn (hay còn gọi là “thiên vị ngầm”) nhằm giảm thiểu cảm giác bất công, người chơi sẽ sớm nhận ra thành bại phụ thuộc quá nhiều vào may rủi, từ đó đánh mất động lực. Để “níu chân” người chơi lâu dài, cần giải quyết hai khía cạnh:

- **Risk and Reward:** Cấu trúc rủi ro – phần thưởng phải được thiết kế sao cho người chơi luôn có quyền lựa chọn lao vào thử thách để giành lợi ích lớn hơn, thay vì thụ động nhận kết quả từ xác suất.
- **Fun and Balance:** Trải nghiệm vui vẻ phải được duy trì thông qua sự cân bằng tinh tế, nơi ngẫu nhiên đóng vai trò tạo bất ngờ nhưng kỹ năng và phán đoán mới là yếu tố quyết định. Làm sao để game vẫn thú vị và công bằng ngay cả khi thiếu vắng sự thiên vị rõ rệt? Đây chính là trọng tâm cần phân tích và thử nghiệm.

### Góc nhìn người chơi (Player Viewpoint)

Mọi quyết định thiết kế đều xoay quanh câu hỏi: **“Người chơi mục tiêu sẽ cảm thấy gì, hiểu gì và làm gì trong từng khoảnh khắc?”** Các công cụ phân tích bao gồm: Chân dung người chơi (Player Personas), Hành trình cảm xúc (Emotional Journey Map) và Mô hình động lực người chơi (Player Motivation Model).

Do đây là bản prototype hoàn thiện theo ý tưởng có sẵn, không mang mục tiêu thương mại, việc nghiên cứu người chơi bài bản (yêu cầu tối thiểu 5–7 ngày và 3–4 phiên trải nghiệm) chưa được thực hiện. Phân tích được rút gọn thành hai yếu tố cốt lõi:

- **Độ tuổi:** 9+
- **Định hướng người chơi:** Một trò chơi đơn giản, giải trí nhẹ nhàng, phù hợp để thư giãn trong những khoảng thời gian rảnh.

Việc rút gọn không đồng nghĩa prototype thiếu đi nỗ lực hướng đến trải nghiệm chuyên nghiệp hay sự “vui” đích thực khi chơi. Ở hiện tại, chân dung người chơi được xây dựng dựa trên chính nhà phát triển – một mẫu hình tham khảo ban đầu.

---

## Thiết kế (Design)

### Core Loop
*(Sơ đồ hoặc mô tả vòng lặp chính sẽ được bổ sung trong các phiên bản sau)*

### Core Mechanic
Hai cơ chế chính:
1. **Di chuyển (Moving)**
2. **Nhặt vật phẩm (Collecting)**

#### Chi tiết hoàn thiện Mechanic:
- **GameDev.tv** cung cấp phần di chuyển cơ bản, tạo Collider2D, Rigidbody2D và sử dụng Material.
- **Hoàn thiện và bổ sung** *(khoảng 30–40% code được tối ưu với sự hỗ trợ của AI)*:
  - `CarMoving`: Thay thế `Input.GetKey` bằng **Input System** mới.
  - `CarHealth`: Quản lý máu và trạng thái sống sót.
  - `WindowPointer`: Học hỏi từ Code Monkey (YouTube), xử lý con trỏ.
  - `CollectableItem`, `ItemHeal`, `ItemSpeed`: Sử dụng **abstract class** làm khuôn mẫu chung cho các loại item.
  - `ItemSpawner`: Tạo sẵn các điểm (points) ngẫu nhiên, kích hoạt sự kiện spawn và xóa item trong khoảng thời gian nhất định.
  - `CameraMove`: Di chuyển nhẹ camera tại Menu Scene và End Scene để tạo cảm giác xe đang chạy.
  - `ScrollingView`: Thay đổi `offset.y` của Material để background trượt liên tục theo vòng lặp, tạo ảo giác di chuyển.
  - `UITime`: Quản lý và hiển thị thời gian qua TMP Text.
  - `UIScore`: Quản lý và hiển thị điểm số qua TMP Text.

### 🗺️ Level Design
- Hiện tại có **1 màn endless duy nhất**.
- Quản lý bởi hệ thống Manager:
  - `Level Manager`: Tải Scene, Reset vật phẩm.
  - `Audio Manager`: Quản lý Sound, Music xuyên suốt các Scene.
  - `Time Manager`: Bộ đếm thời gian.
  - `Score Manager`: Quản lý điểm thưởng người chơi thu thập được.

### UI/UX
Phong cách tối giản, tập trung vào trải nghiệm:
- **Menu Scene:** Play Button, Exit Button.
- **Gameplay Scene:** Score Board, Timer Board.
- **End Scene:** Kết quả (Time, Score), Try Again Button, Quit Button.

### Art Style & Audio

#### a) Art Style
- Sử dụng Asset có sẵn do **GameDev.tv Team** cung cấp.

#### b) Audio
- Nhạc nền không bản quyền (no license) được chọn lọc từ YouTube.
- Âm thanh khởi động và tăng tốc xe.

---

## MVP Scope

- **Thời gian hoàn thành:** 7 ngày (05/05 – 11/05/2026).
- **Mục tiêu:**
  - Hoàn thiện các cơ chế cơ bản.
  - Publish thành công prototype.
  - Cải thiện kỹ năng viết GDD và C# Script.
  - Sử dụng thành thạo GitHub, Unity Editor 6.004 và Aseprite.

> Do quy mô rất nhỏ, việc phân loại tính năng (Must-have, Should-have, Could-have) chưa thực sự cần thiết ở giai đoạn này.

### Tiêu chí thành công
- Prototype chạy mượt, không phát sinh bug nghiêm trọng.
- Nhận được phản hồi tích cực từ người chơi thử nghiệm.

---

## Kiểm thử (Testing)

- **Mục tiêu:** Bạn bè chơi thử, đưa ra nhận xét và ý kiến. Phát hiện và ghi nhận bug để cải thiện.

---

## 🚀 Phát hành (Publish)

- **Phiên bản hiện tại:** Car Delivery Prototype v1.0
- **Trạng thái:** Đã publish

---

*© 12/05/2026 Doung. All rights reserved.*
