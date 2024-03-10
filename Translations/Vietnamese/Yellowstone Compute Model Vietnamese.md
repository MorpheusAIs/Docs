![Image1forYellowstone](https://github.com/MorpheusAIs/Morpheus/assets/1563345/80a6c1cf-fe52-42ba-bfd4-91d9faf67f07)

# Mô hình Tính toán “Yellowstone” của Morpheus

### Erik Voorhees

### Ngày 3 tháng 1 năm 2024

Bản đề xuất sửa đổi cấu trúc tokenomics của Morpheus để khuyến khích tính toán trên mạng trí tuệ nhân tạo (AI) phi tập trung.

## Tóm tắt

Trong Mô hình Tính toán Yellowstone, mạng lưới Morpheus chỉ trả cho Nhà cung cấp dựa trên Tính toán thực sự được cung cấp thông qua quy trình đấu thầu cạnh tranh. Ngoài ra, hệ thống phân bổ sản lượng IPS (suy luận/giây) hiếm có theo tỷ lệ thuận với số dư token MOR mà người nắm giữ sở hữu, thay vì dựa trên khoản thanh toán. Điều này cải thiện đáng kể trải nghiệm người dùng (UX) đồng thời giảm thiểu lỗ hổng Sybil. Yellowstone cũng đưa vào các yếu tố đo lường quan trọng về thời gian và bài kiểm tra Đạt/Không đạt để đảm bảo Nhà cung cấp phản hồi nhanh chóng và chính xác. Yellowstone bảo mật quyền riêng tư bằng cách không bao giờ gửi yêu cầu hoặc kết quả thông qua Bộ định tuyến(Router) và giảm thiểu các giao dịch blockchain để cho phép hoạt động trên quy mô lớn. Thông qua mô hình này, MOR đạt được giá trị căn bản vì nó cho phép truy cập vĩnh viễn (mặc dù không phải là không có giới hạn) vào tính toán phi tập trung, mà không yêu cầu giao dịch cho mỗi suy luận.

Nếu được chấp thuận, tài liệu này sẽ thay thế phần “Bằng chứng tính toán, Đăng Ký và Phần Thưởng” của [Morpheus whitepaper](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md)

## Bối cảnh

Morpheus sử dụng tokenomics để khuyến khích cung cấp đủ nguồn tính toán theo mô hình mở rộng, phục vụ cho mục đích trí tuệ nhân tạo tổng hợp phi tập trung và không cần cấp phép. Trong khái niệm ban đầu, Morpheus phân bổ 24% lượng phát hành MOR trực tiếp cho các Nhà cung cấp Tính toán, tỷ lệ thuận với các yêu cầu tính toán nhận được và hệ thống ưu tiên các yêu cầu tính toán cho những nhà cung cấp nắm giữ nhiều MOR hơn.

### Trích từ white paper gốc:

`“Phí giao dịch MOR được đốt theo tỷ lệ tương ứng của từng Nhà cung cấp Tính toán, đóng vai trò như bằng chứng xác minh trạng thái của Nhà cung cấp và giúp họ kiếm được một phần token MOR mỗi ngày.`

`Ví dụ: Nếu có 100 Nhà cung cấp Tính toán vào ngày đầu tiên khi mạng lưới khởi chạy, thì mỗi nhà cung cấp sẽ nhận được phần thưởng theo tỷ lệ tương ứng dựa trên lượng MOR họ đã đốt thông qua phí. Trong trường hợp này, giả sử mỗi trong số 100 Nhà cung cấp Tính toán đã đốt 100 MOR, thì mỗi ngày 1% của 3.456 token MOR = 34,56 MOR sẽ được phân bổ cho các Nhà cung cấp.”`

### Có ba vấn đề chính của cách tiếp cận này::

1. Nó yêu cầu người dùng trả phí giao dịch cho mỗi lần tính toán. Ngay cả khi mức phí thấp, điều này vẫn gây ra khó khăn đáng kể và dẫn đến trải nghiệm người dùng kém (UX) và thua xa trải nghiệm người dùng của OpenAI. Ngoài ra, nó còn yêu cầu ít nhất một giao dịch blockchain cho mỗi lần tính toán, điều này có thể không khả thi ngay cả trên các giải pháp Layer 2 (L2). Mỗi yêu cầu tính toán có chi phí cực kỳ thấp và nếu yêu cầu giao dịch blockchain thì tính kinh tế sẽ không khả thi.
2. Mô hình này dễ bị khai thác đáng kể vì doanh thu dự kiến cho các nhà cung cấp tính toán cao hơn nhiều so với chi phí tính toán thực tế. Do đó, kẻ tấn công có thể tấn công mạng bằng cách gửi hàng loạt các yêu cầu tính toán spam đến nút Nhà cung cấp Tính toán của riêng mình và kiếm được một phần tương đối lớn token MOR mỗi ngày, ngay cả khi không cung cấp bất kỳ giá trị kinh tế nào cho bất kỳ ai. Điều này có thể dẫn đến một lượng lớn tài nguyên tính toán ban đầu (chưa sử dụng), sau đó biến mất khi cơ hội thu nhập khổng lồ tan biến và MOR chi cho khoản trợ cấp ban đầu đó sẽ bị lãng phí/mất mát.
3. Nếu các yêu cầu tính toán được ưu tiên dựa trên lượng MOR mà Nhà cung cấp nắm giữ, thì hiệu suất của các nhà cung cấp đó (thời gian phản hồi) và chi phí xử lý tính toán của họ sẽ bị mạng lưới bỏ qua, và chính xác là hai yếu tố này mà mạng lưới nên cố gắng tối ưu hóa (thời gian phản hồi và chi phí tính toán lý tưởng nên được giảm xuống mức thấp nhất có thể). Nếu nhà cung cấp nắm giữ MOR hàng đầu đang chạy một GPU $200 từ thời đại đại học, thì hiệu suất tính toán cho nhiều người dùng sẽ cực kỳ kém. Ưu tiên nên dựa trên giá thầu và hiệu suất, không phải lượng MOR nắm giữ.

Bên dưới là "Mô hình Yellowstone" được đề xuất để sửa đổi mô hình tokenomics của Morpheus cho việc cung cấp tính toán để giải quyết các vấn đề nêu trên. Mô hình này hoạt động bất kể phần phát hành nào được phân bổ cho tính toán, và chúng tôi sẽ giả định tình trạng hiện tại là 24% tổng lượng phát hành.

### Mục tiêu là:

1. Cho phép người dùng không phải trả phí tính toán theo yêu cầu (lý tưởng nhất là không phải trả phí gì cả).
2. Đạt được nguồn tài nguyên tính toán phi tập trung hiệu quả, có thể mở rộng và bền vững mà không phải trả quá nhiều cho nó.
3. Khuyến khích các Nhà cung cấp Tính toán cạnh tranh về thời gian phản hồi thấp và chi phí.
4. Giảm thiểu số lượng giao dịch blockchain (bao gồm cả L2).
5. Chứng minh nhu cầu cơ bản và lành mạnh về mặt kinh tế đối với MOR.

## Mô Hình Yellowstone

Four Components Involved:

### Người dùng

-   Có các truy vấn
-   Muốn tính toán nhanh/chính xác miễn phí và không bị kiểm duyệt/giám sát.

### Nhà cung cấp

-   Có tài nguyên tính toán
-   Muốn lợi ích (MOR)

### Bộ Định Tuyến

-   Công cụ xử lý năng suất cao.
-   Phi Tập Trung

### Hợp đồng Tính toán

-   Hợp đồng thông minh không phân quyền nhận phần phát hành MOR, theo dõi tín dụng và nợ cho Nhà cung cấp và thanh toán cho Nhà cung cấp khi được yêu cầu.

## Đơn vị đo lường chuẩn

Trong lĩnh vực Trí tuệ Nhân tạo (AI), có một đơn vị tính toán cơ bản được đo bằng số phép tính trên giây (IPS). Đơn vị này tương tự như Wei trên blockchain. IPS được sử dụng để xác định tỷ lệ trong bộ định tuyến Yellowstone. Do đó, trọng lượng của một đơn vị Trí tuệ Nhân tạo Morpheus tương đương với một phép tính. Tùy thuộc vào loại yêu cầu, đơn vị này có thể được áp dụng cho bất kỳ tác vụ tính toán nào.

Khi AI và blockchain ngày càng hòa nhập, Morpheus hướng đến việc cung cấp một tiêu chuẩn đo lường mã nguồn mở để làm rõ thuật ngữ được sử dụng bởi cả AI và Blockchain.

Có hai loại prompt, được xác định bởi kích thước của phản hồi được trả về bởi một mô hình:

**Prompt có độ dài xác định** tính đến chiều dài của phản hồi cần trả về. Ví dụ:

-   Trò chuyện/Tạo hình ảnh
-   Chẩn đoán bệnh
-   Nhận dạng đối tượng
-   Phát hiện gian lận

**Prompts có độ dài không xác định** yêu cầu tài nguyên để trả lời mà chỉ có thể biết được sau khi phản hồi được tạo. Ví dụ:

-   Soạn một bản sonata về mì spaghetti.
-   Tạo video Chúc mừng sinh nhật
-   Kết hợp mô hình X với mô hình Y
-   Cắt một mô hình 3D thành tệp .stl

Yellowstone tập trung vào các prompt có độ dài xác định. Bộ định tuyến được mô tả sẽ được xây dựng theo cách có thể xử lý các prompt không xác định trong tương lai, nhưng không phải hiện tại. Để thực hiện điều này, chúng tôi sử dụng một phép đo chuẩn hóa cho Trí tuệ Nhân tạo Phi tập trung.

## Bảng giá DeAI

### Đơn vị tính toán trên giây:

| Loại                                 | Phản Hồi                           | Giá                                          |
| ------------------------------------ | ---------------------------------- | -------------------------------------------- |
| Xác định                             | Ngôn ngữ                           | Số token được tính toán mỗi giây (TPS)       |
| Không xác định - media               | Âm thanh                           | Số mẫu được tính toán mỗi giây (ISPS)        |
| Không xác định - media               | Video                              | Số khung hình được tính toán mỗi giây (IFPS) |
| Không xác định - công nghệ tương lai | Định dạng tương lai không xác định | Chưa xác định (NA)                           |

Đơn vị tính toán đầu tiên cho bộ định tuyến Yellowstone sẽ là TPS (số token được tính toán mỗi giây). Các định dạng tính toán khác sẽ được cập nhật sau.

### Thời gian

Thời gian khối cho tính toán là 12 giây, có nghĩa là một khối các giao dịch tính toán được công bố và tính toán 5 lần mỗi phút.

## Định nghĩa

**“Người dùng”**: Được định nghĩa là bất kỳ thực thể nào có địa chỉ MOR và gửi Yêu cầu (Requests) đến Bộ định tuyến (Router) để sử dụng tài nguyên tính toán. Người dùng có thể là một cá nhân cụ thể gửi Yêu cầu từ nút máy tính để bàn Morpheus, hoặc có thể là một bot, hoặc một công ty hoặc trang web của bên thứ ba tương tác với mạng Morpheus thay mặt cho người dùng cuối của họ (trong trường hợp này, "người dùng cuối" của bên thứ ba không có ý nghĩa đối với mạng Morpheus và không nên nhầm lẫn với Người dùng được định nghĩa ở trên).

**“Nhà cung cấp”**: Được định nghĩa là bất kỳ thực thể nào, chạy một nút cung cấp tài nguyên tính toán, có địa chỉ MOR và đặt giá thầu IPS thông qua Bộ định tuyến. Khi một Nhà cung cấp thắng thầu từ Bộ định tuyến, Nhà cung cấp sẽ cung cấp tài nguyên tính toán (GPU, v.v.) cho mô hình AI được yêu cầu của Người dùng.

**“Bộ định tuyến”**: Được định nghĩa là một ứng dụng phần mềm có địa chỉ MOR và đàm phán thị trường hai chiều giữa Người dùng và Nhà cung cấp. Bộ định tuyến đăng ký và theo dõi địa chỉ và giá thầu của Nhà cung cấp, xử lý Yêu cầu từ Người dùng, ghi lại [mili-giây] và các bài kiểm tra Thành công/Thất bại của các Yêu cầu được xử lý, và hướng dẫn Hợp đồng Tính toán ghi nhận cho các Nhà cung cấp đủ điều kiện thanh toán bằng MOR. Bộ định tuyến không bao giờ gửi hoặc nhận giao dịch MOR (hoặc giao dịch trên bất kỳ blockchain nào). Bộ định tuyến không bao giờ nhìn thấy nội dung của Yêu cầu hoặc phản hồi.

**“Hợp đồng tính toán”**: Được định nghĩa là một hợp đồng thông minh có địa chỉ MOR, nhận tất cả MOR được phân bổ cho nhóm Tính toán, theo dõi số tiền nợ cho các Nhà cung cấp đủ điều kiện và thanh toán MOR cho các Nhà cung cấp đủ điều kiện khi Nhà cung cấp yêu cầu thanh toán.

**"Tính toán mỗi giây - Inferences per second" (IPS)**: Là đơn vị tính toán cơ bản trong Trí tuệ Nhân tạo. IPS được sử dụng để xác định tỷ lệ trong bộ định tuyến Yellowstone. Do đó, trọng lượng của một đơn vị Trí tuệ Nhân tạo Morpheus tương đương với một phép tính.

**“IPS Tối đa - IPSMax”**: Là số lượng phép tính trên giây tối đa được Bộ định tuyến chấp nhận thanh toán.

**“RFC”**: Viết tắt của “Request for Compute” (Yêu cầu Tính toán). Người dùng gửi RFC cho Bộ định tuyến và chỉ định [LLM] mà Người dùng mong muốn truy cập cũng như [IPSMax], đây là giới hạn trên của IPS chấp nhận được trong phản hồi. Người dùng sẽ muốn giới hạn điều này vì số lượng cao hơn = thời gian chờ đợi câu trả lời lâu hơn và tính nhiều hơn vào [UserMax], có giới hạn mỗi ngày.

### Thưởng khuyến khích khởi động cung cấp tính toán

Trong năm đầu tiên sau giai đoạn khởi động của Hợp đồng Vốn (Capital Contract), 100 Nhà cung cấp Tính toán hàng đầu có thể được hưởng một khoản tiền thưởng theo tỷ lệ tương ứng là 2,4% lượng MOR được phát hành. Điều này được tính toán bởi các bộ định tuyến và được ghi nhận trong hợp đồng tính toán.

## Quy trình hoạt động

1. Người dùng, Nhà cung cấp và Bộ định tuyến đều tạo khóa công khai MOR (đây là định danh của họ, tất cả các tin nhắn được ký bằng khóa này).
2. Nếu Người dùng nắm giữ bất kỳ số dư MOR nào, Người dùng có thể gửi tin nhắn được ký có tên "Yêu cầu Tính toán" (RFC) đến Bộ định tuyến. Người dùng chỉ định [Mô hình Ngôn ngữ Lớn] ([LLM]) và [IPSMax].
3. Bộ định tuyến ưu tiên RFC dựa trên số dư MOR của Người dùng (giải quyết vấn đề Sybil).
4. Bộ định tuyến chọn Nhà cung cấp hỗ trợ [LLM], được ưu tiên dựa trên Giá thầu thấp nhất tính theo IPS bằng MOR.
5. Bộ định tuyến gửi kiểm tra hoạt động đến Nhà cung cấp. Nếu thành công, thì
6. Bộ định tuyến kết nối Người dùng với Nhà cung cấp qua TCP/IP.
7. Người dùng gửi Truy vấn ([LLM], [prompt]) đến Nhà cung cấp.
8. Nhà cung cấp tính toán Truy vấn, gửi Kết quả cho Người dùng.
9. Người dùng báo cáo các số liệu thành công cho Bộ định tuyến (chẳng hạn như IPS nhận được hoặc thời gian thực hiện, hoặc phiếu bầu thành công/thất bại).
10. Bộ định tuyến hướng dẫn Hợp đồng Tính toán ghi nhận cho Nhà cung cấp bằng MOR nếu công việc hoàn thành thỏa đáng.
11. (Sau một khoảng thời gian nhất định) Nhà cung cấp yêu cầu thanh toán MOR từ Hợp đồng Tính toán và Hợp đồng Tính toán gửi thanh toán MOR nếu hợp lệ (giao dịch blockchain đầu tiên cho đến nay, có thể được xử lý theo lô).

![ComputeContractImage2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/e66ea20c-9851-4f9e-9caa-66c6d798c462)

## Kết quả

-   Người dùng nhận được Kết quả nhanh chóng cho Truy vấn của mình và không phải trả bất kỳ khoản phí nào (điều này sẽ dẫn đến trải nghiệm người dùng tuyệt vời và do đó thúc đẩy việc áp dụng). **Giải quyết Mục tiêu 1.**
-   Hợp đồng Tính toán đã thanh toán cho việc Tính toán thông qua quy trình đấu thầu cạnh tranh và kiểm tra chất lượng/sự hài lòng từ Người dùng đã đặt hàng. **Giải quyết Mục tiêu 2.**
-   Nhà cung cấp nhận được tiền (MOR) từ Hợp đồng Tính toán miễn là phản hồi đủ nhanh. Nhà cung cấp nhận được chính xác những gì họ yêu cầu để cung cấp tính toán. Nếu yêu cầu của họ quá cao, những nhà cung cấp khác sẽ đặt giá thầu thấp hơn, do đó hệ thống hoạt động hiệu quả và sẽ giảm giá Nhà cung cấp xuống gần bằng chi phí điện cơ bản. **Giải quyết Mục tiêu 3**
-   Số lượng giao dịch trên chuỗi được giảm thiểu (nhiều Truy vấn có thể chạy với ít Giao dịch trên chuỗi). **Giải quyết Mục tiêu 4**
-   Khả năng tính toán nhanh, miễn phí thúc đẩy nhu cầu nắm giữ token MOR của Người dùng. **Giải quyết Mục tiêu 5**
-   Bước 6 & 7 cung cấp quyền riêng tư hợp lý (Truy vấn không bao giờ chạm vào Bộ định tuyến, cũng như Kết quả). Các Nhà cung cấp được chọn ngẫu nhiên và không bao giờ biết danh tính của Người dùng ngoài địa chỉ IP. Quyền riêng tư tốt hơn có thể đạt được sau này với TOR và/hoặc FHE.
-   Số dư MOR được giảm từ Hợp đồng Tính toán. Hợp đồng sẽ có khả năng thanh toán miễn là MOR được thanh toán < MOR kiếm được mỗi kỳ từ việc phát hành.
-   Nếu Người dùng gửi RFC vượt quá UserMax của Người dùng, Bộ định tuyến sẽ từ chối yêu cầu.

—-------------

## Ngân sách Tính toán

Mạng Morpheus cần xác định lượng MOR mà mạng sẵn sàng chi tiêu cho tài nguyên tính toán trong một khoảng thời gian nhất định (chẳng hạn như mỗi ngày), được gọi là Ngân sách Tính toán. Trong mỗi khoảng thời gian, Hợp đồng Tính toán có thể chi tiêu tối đa số lượng MOR này. Con số này nhân với giá MOR sẽ cho chúng ta biết ngân sách bằng đô la để mua tài nguyên Tính toán mỗi ngày.

Ngân sách Tính toán = 1% số dư MOR của Hợp đồng Tính toán vào cuối ngày hôm trước.

-   Vì ngân sách là một tỷ lệ phần trăm cố định của nhóm, nên nó không bao giờ có thể hết (nó chỉ có thể giảm dần theo tiệm cận).
-   Ngoài ra, vì không có trường hợp thực tế nào mà tất cả MOR đều sử dụng hết công suất tối đa mỗi ngày, điều này có nghĩa là trong thực tế, ngân sách sẽ không bao giờ đạt đến giới hạn 1% số dư Hợp đồng Tính toán của ngày hôm trước. Điều này vẫn đúng miễn là có ít nhất một MOR nằm im lặng trong ví hoặc sàn giao dịch.

## Tỷ lệ truy cập (AccessRate)

Mạng Morpheus phân bổ tài nguyên khan hiếm là tính toán IPS thông qua khái niệm "AccessRate" (Tỷ lệ truy cập). AccessRate xác định số lượng IPS mà mỗi token MOR có thể truy cập mỗi ngày. Quyền truy cập không sử dụng sẽ không được tích lũy. AccessRate luôn được hiển thị dưới dạng số lượng IPS trên 1 token MOR (chẳng hạn như 1 MOR = 15.000 IPS). AccessRate được xác định một phần bởi MaxIPS, là số lượng IPS tối đa mà mạng có thể mua mỗi ngày.

**MaxIPS** = ((Ngân sách Tính toán MOR _ Giá MOR) / Giá IPS) _ 1000
**AccessRate** = (1 / Tổng cung MOR) _ MaxIPS
**UserMax** = AccessRate _ Số dư MOR của Người dùng

### Ví Dụ Minh Hoạ:

**Tổng cung MOR** = 10,000,000 token MOR  
**Số dư Hợp đồng Tính toán ngày hôm trước** = 300,000
**Ngân sách Tính toán MOR** = 3,000 token MOR mỗi ngày (1% số lượng phía trên)
**Giá MOR** = $20  
**Giá IPS** = $0.002 mỗi 1000 IPS  
**Số dư của người dùng** = 5 MOR tokens

### Kết quả ví dụ:

**MaxIPS** = 30,000,000,000 IPS (số lượng IPS tối đa mạng có thể mua/sản xuất mỗi ngày)  
**AccessRate** = 3,000 (mỗi token MOR cho phép truy cập 3000 IPS mỗi ngày)  
**UserMax** = 15,000 (Người dùng có 5 token MOR có thể truy cập tối đa 15000 IPS mỗi ngày)

-   Mỗi khoảng thời gian (mỗi ngày), mạng Morpheus có đủ tiền để mua một lượng IPS (X) nhất định từ các Nhà cung cấp tính toán. X phụ thuộc vào lượng MOR mà Hợp đồng Tính toán sẵn sàng chi tiêu ( "Ngân sách Tính toán") nhân với giá MOR hiện tại chia cho giá thị trường của IPS.
-   Ví dụ, nếu Ngân sách Tính toán là 3.000 MOR và mỗi MOR trị giá 20 đô la, thì mạng có thể mua (sản xuất) tới 60.000 đô la IPS trong ngày hôm đó. Nếu giá cho 1.000 IPS là 0,002 đô la, thì mạng có thể mua tới 30 tỷ IPS (30 tỷ x 1000 IPS).
-   Khả năng sản xuất 30 tỷ IPS đó được phân bổ theo tỷ lệ thuận với số dư MOR. Giả sử có 10.000.000 MOR đang lưu hành. Người dùng có 500 token MOR (chiếm 0,005% tổng số) có thể truy cập miễn phí tới 1,5 triệu IPS trong ngày hôm đó.
-   Miễn là Ngân sách Tính toán được đặt thành một tỷ lệ phần trăm của số dư Hợp đồng Tính toán, thì Hợp đồng Tính toán không thể hết MOR (nó chỉ có thể giảm dần theo tiệm cận).
-   Trong thực tế, hầu hết các token MOR sẽ nằm trong ví và sàn giao dịch, và chỉ một phần nhỏ sẽ được sử dụng để yêu cầu sản xuất IPS.

## Ghi chú

-   Nhu cầu cơ bản đối với MOR đến từ Người dùng, những người mong muốn truy cập miễn phí vào AI tổng hợp và các hình thức tính toán khác trên mạng Morpheus theo nhu cầu. Số MOR họ nắm giữ càng nhiều, lượng AI họ có thể truy cập mỗi ngày càng cao.

-   Loại phần cứng của Nhà cung cấp không liên quan đến mạng, miễn là chúng đáp ứng bài kiểm tra thành công/thất bại của Người dùng. Bất kỳ Nhà cung cấp nào đặt giá thầu cho nhiều Truy vấn hơn mức họ có thể xử lý hiệu quả sẽ bị phạt bằng cách không vượt qua bài kiểm tra này (họ sẽ không được thanh toán).

-   Quan trọng, mô hình trên chỉ thanh toán cho Nhà cung cấp KHI có nhu cầu tính toán của họ. Điều này ngăn chặn tình trạng một lượng lớn MOR được phát hành trước thời hạn khi mạng không cần.

-   Nhà cung cấp cần chứng minh họ có một LLM nhất định, bằng cách ký hash của model LLM bằng khóa của họ. Điều này không chứng minh họ đã sử dụng nó, nhưng nó chứng minh họ đã tải xuống và cài đặt nó, đại diện cho công việc, do đó ngăn chặn một số hình thức gian lận nhạy cảm với Sybil. Nếu Nhà cung cấp cung cấp kết quả rác cho Người dùng, Người dùng có thể gửi [Fail] (Thất bại) cùng với [mili-giây] trở lại Bộ định tuyến và Nhà cung cấp sẽ không được ghi nhận cho phép tính đó. Morpheus không cần tất cả câu trả lời phải hoàn hảo ... nó chỉ cần đủ câu trả lời đủ tốt so với các lựa chọn cạnh tranh.

-   Tấn công Sybil bằng cách làm ngập mạng với các RFC được ngăn chặn bởi AccessRate. "Chi phí" của việc gửi RFC là chi phí mua một token MOR chia cho số lượng RFC được gửi trên danh nghĩa của nó. Do đó, chi phí không bao giờ bằng 0, nhưng người dùng sẽ không cảm thấy mất mát mỗi khi thực hiện một RFC. Nó sẽ rẻ đối với tất cả người dùng thực sự và cực kỳ tốn kém đối với spammer. Thực tế, giống như phí đào Bitcoin, Morpheus có thể coi tất cả RFC đều hợp lệ và không cần phân biệt giữa spam và "hợp pháp". Trong mọi trường hợp, Người dùng đã nắm giữ một lượng MOR đủ để thực hiện yêu cầu ngay từ đầu, do đó có quyền thực hiện yêu cầu bất kể nội dung.

-   Pass/Fail được xác định bởi Người dùng và kiểm soát chất lượng ở một mức độ nhất định. Người dùng truyền kết quả Pass/Fail cùng với [mili giây] trở lại Bộ định tuyến. Nếu Thất bại, không có phần thưởng hoặc điểm phạt (chưa xác định). Không có động lực để đánh giá Thất bại cho Nhà cung cấp một cách sai lầm (không có động lực tài chính để làm như vậy). Cơ chế này ngăn chặn Nhà cung cấp gửi Kết quả nhanh nhưng vô dụng.

    Lưu ý: có lẽ Không có Phần thưởng xảy ra khi Thất bại chỉ khi MOR của Người dùng > MOR của Nhà cung cấp. Nếu không, chỉ là một điểm trừ mà Bộ định tuyến có thể sử dụng trong logic riêng tư của nó.

-   Cả bốn bên (Người dùng, Nhà cung cấp, Bộ định tuyến và Hợp đồng Tính toán) đều có địa chỉ MOR duy nhất làm ID của họ. Tất cả các tin nhắn giữa các bên đều yêu cầu chữ ký (nhưng hầu hết không yêu cầu giao dịch blockchain).

-   Nhà cung cấp phải có số dư khác 0 để ngăn chặn tấn công Sybil từ phía Nhà cung cấp.

-   Nếu tiêu chí [mili-giây] cao hơn, mạng thường sẽ nhanh hơn, nhưng lại không khuyến khích các Nhà cung cấp nhỏ hơn.

-   Có sự không khuyến khích cung cấp Kết quả chậm (không có doanh thu sau khi tính toán).
