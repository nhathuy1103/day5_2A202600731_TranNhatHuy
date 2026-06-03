# Workshop — Mổ App AI Thật

**Thời gian:** 35-45 phút  
**Hình thức:** cá nhân trước, chia sẻ theo nhóm sau  
**Output:** finding note + sketch `as-is / to-be`

Mục tiêu không phải chấm "UI đẹp hay xấu". Mục tiêu là dùng sản phẩm thật như một bài needfinding: tìm chỗ product gãy trong workflow thật, rồi viết finding đó thành quyết định product.

## 1. Chọn một sản phẩm để dùng thử

| Sản phẩm | AI feature | Cách truy cập |
|---|---|---|
| Vietnam Airlines — NEO | Chatbot hỗ trợ vé, hành lý, khiếu nại | Website/Zalo VNA |

| App theo track nhóm | App thật nhóm đang chọn cho hackathon | Cần screenshot/link |

## 2. Dùng thử: promise vs reality

Ghi nhanh:
- Product hứa sẽ:
    + Tra cứu thông tin chuyến bay 
         Cung cấp cho người dung thông tin chuyến bay
         thông tin vé máy bay 
        +tìm kiếm giá vé và thông tin hành lý
    + Sẵn sàng giải đáp thắc mắc liên quan đến mua vé và hành lý
         Thông tin mua vé
         Thông tin hành lý
         Hướng dẫn làm thủ tục và các giấy tờ cần chuẩn bị trước chuyến bay
- User được giúp đỡ sẽ là những khách hành quan tâm đến các chuyến bay của hãng 
- Tôi kỳ vọng AI làm được task sẵn sàng giải đáp thắc mắc liên quan đến mua vé và hành lý
- Sau khi sử dụng, điểm gãy xuất hiện là:
    + Khi lần đầu đặt cầu hỏi về vấn đề ưu đãi, chatbot trả lời cách tìm thông tin đó ở đâu thay vì trực tiếp đưa thông tin ưu đãi
    + Khi hỏi lần thứ 2, chatbot đưa ra toàn bộ ưu đãi nhưng không bám sát thông tin nhu cầu người dùng đã cung cấp khi trước
    + Khi quan tâm đến những vật phẩm được phép và không được phép mang lên máy bay, tôi đưa thông tin vật phẩm là sạc dự phòng và công suất của sạc theo đơn vị mAh, thay vì chatbot trả ra kết quả được phép hay không thì chatbot bắt người dùng tự tính để đổi sang đơn vị Wh.
    + Khi tôi hỏi về vấn đề thời tiết hôm nay có ảnh hưởng gì đến chuyến bay không thì nó không thể trả lời và đưa ra giải pháp như check lại thông tin chuyến bay hoặc đề xuất gọi cskh
    + Không cho khách hàng số ghế còn trống 
- Khi dùng thật, điểm gãy xuất hiện ở đâu?

Evidence cần có:

- screenshot,
- quote từ app/web/review,
- prompt/input đã thử,
- hành vi quan sát được.

## 3. Vẽ 4 paths

| Path | Câu hỏi cần trả lời |
|---|---|
| Happy |Khi user hỏi "Tôi có được mang pin sạc dự phòng 20.000mAh lên máy bay không?", AI nhận diện đúng intent, xác định dung lượng pin và trả lời trực tiếp rằng pin được phép mang theo hành lý xách tay cùng các điều kiện liên quan. User nhận được câu trả lời ngay và tiếp tục sử dụng chatbot cho các câu hỏi khác.|
| Low-confidence | Khi user hỏi về pin dự phòng nhưng không cung cấp dung lượng pin, AI không đủ thông tin để kết luận. Hệ thống nên hỏi lại: "Pin của anh/chị bao nhiêu mAh?" hoặc đưa ra các lựa chọn phổ biến thay vì trả toàn bộ quy định hoặc yêu cầu người dùng tự tìm hiểu. |
| Failure | Khi AI trả về quy định dài hoặc yêu cầu người dùng tự đổi từ mAh sang Wh, user không biết chính xác pin của mình có được phép mang lên máy bay hay không. User phát hiện lỗi vì câu trả lời không giải quyết được nhu cầu thực tế và phải tìm Google hoặc gọi tổng đài để xác nhận.|
| Correction | Khi user phản hồi "Tôi không biết cách đổi từ mAh sang Wh" hoặc "Bạn hãy cho tôi biết có được mang hay không", AI giải thích lại hoặc yêu cầu thêm thông tin. Hiện tại correction này không được lưu lại để cải thiện các lần trả lời sau, nên cùng một lỗi có thể tiếp tục lặp lại với người dùng khác.|

## 4. Viết finding thành quyết định

Khi user hỏi "Tôi có được mang pin sạc dự phòng lên máy bay không?",

AI trả về một đoạn quy định dài hoặc link chính sách thay vì trả lời trực tiếp "Có" hoặc "Không" và các điều kiện kèm theo.

Hậu quả là user phải tự đọc và diễn giải quy định, làm tăng thời gian tìm kiếm thông tin và có thể hiểu sai quy định về pin dự phòng.

Lỗi thuộc layer Intent + UX Recovery.

Nên sửa bằng:
- Trả lời ngắn gọn trước (Có/Không).
- Tóm tắt các điều kiện quan trọng (dung lượng pin, hành lý xách tay hay ký gửi).
- Cho phép user chọn các câu hỏi tiếp theo như:
  + Pin 10.000mAh có được mang không?
  + Pin 20.000mAh có được mang không?
  + Có được để trong hành lý ký gửi không?


## 5. Sketch as-is / to-be

Vẽ 2 cột:

- **As-is:** flow hiện tại, đánh dấu điểm gãy.

USER
  |
  v
Hỏi:
"Tôi có được mang pin sạc dự phòng lên máy bay không?"
  |
  v
NEO Chat tìm FAQ
  |
  v
Trả nguyên đoạn quy định dài
  |
  +----------------------------+
  |                            |
  | User hiểu                  | User không hiểu
  |                            |
  v                            v
Thoát chat                Đọc tiếp FAQ
                                |
                                v
                      Tự tìm Google / gọi tổng đài
                               ^
                               |
                    ĐIỂM GÃY (BREAK POINT)

- **To-be:** flow đề xuất, đánh dấu path đã sửa.

USER
  |
  v
Hỏi:
"Tôi có được mang pin sạc dự phòng lên máy bay không?"
  |
  v
AI nhận diện intent:
"Hành lý / Pin dự phòng"
  |
  v
AI trả lời:

"Có thể mang.
Vui lòng cho tôi biết dung lượng pin."
  |
  v
USER
"20.000mAh"
  |
  v
AI kiểm tra quy định
  |
  +------------------------+
  |                        |
  | Tự tin                 | Không chắc
  |                        |
  v                        v
Trả kết luận         Hỏi lại hoặc
ngay lập tức         chuyển CSKH
  |
  v
USER xác nhận đã hiểu

## 6. Tự kiểm trước khi nộp

- [ ] Có ít nhất 1 screenshot hoặc observation cụ thể.
- [ ] Có đủ 4 paths hoặc nói rõ path nào chưa có trong product.
- [ ] Finding được viết thành product decision, không chỉ là nhận xét.
- [ ] Sketch có as-is và to-be.
- [ ] Có một câu nói rõ finding này sẽ đổi gì trong SPEC.
