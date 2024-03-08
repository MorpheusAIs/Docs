![Morpheuslogo](https://github.com/MorpheusAIs/Morpheus/assets/1563345/235b9c04-f3b1-4520-a328-2070c9c890ab)

# Morpheus


## Một Mạng Lưới để Tăng Cường Các Tác Nhân Thông Minh

### Tác Giả: Morpheus, Trinity và Neo
Xuất Bản - Ngày 2 tháng 9 năm 2023
Liên kết đến Chi Tiết Kỹ Thuật Yellow Paper: https://github.com/MorpheusAIs/Docs/blob/main/YellowPaper.md


## Giới Thiệu
Morpheus được thiết kế để khuyến khích mạng lưới ngang hàng đầu tiên của các Trí tuệ Nhân tạo mục đích tổng quát cá nhân có thể thực thi Hợp đồng Thông minh thay mặt cho người dùng, được biết đến là Smart Agents. Việc cung cấp Smart Agents mã nguồn mở cho người dùng để kết nối với ví của họ, Dapps, và hợp đồng thông minh hứa hẹn mở cánh cửa của thế giới Web3 cho mọi người.

Ví Web3 của người dùng để quản lý khóa và ký các giao dịch được khuyến nghị khi tương tác với Smart Agent. Một Mô hình Ngôn ngữ Lớn được đào tạo trên dữ liệu Web3 bao gồm các Blockchain, Ví, Dapps, DAOs, và Hợp đồng Thông minh. Thuật toán SmartContractRank để đánh điểm & khuyến nghị các Hợp đồng Thông minh tốt nhất cho người dùng. Bộ nhớ dài hạn về dữ liệu người dùng & ứng dụng đã được kết nối được lưu trữ cục bộ hoặc qua đám mây phi tập trung để cung cấp bối cảnh rộng hơn cho các hành động của Smart Agent.

Cuối cùng, người dùng bình thường có thể nói chuyện với Smart Agent của họ bằng ngôn ngữ thông thường và có thể cho nó hiểu câu hỏi và thực hiện một hành động dựa trên ý định/phê duyệt của họ. Việc này tương tự như cách công cụ tìm kiếm của Google mở rộng Internet sớm cho công chúng thông qua giao diện web dễ sử dụng của họ vào cuối những năm 1990.

Để làm cho Smart Agents trở nên dễ tiếp cận cho mọi người và tăng tính phi tập trung của cơ sở hạ tầng của họ, chúng tôi đề xuất phát triển mạng lưới Morpheus. Mạng lưới Morpheus sẽ bao gồm một token được phát hành một cách công bằng (token "MOR") để khuyến khích cả bốn nhóm đóng góp chính cho mạng lưới. Tức là, cộng đồng các nhà xây dựng tạo giao diện, các lập trình viên đóng góp vào phần mềm/agent của Morpheus, các nhà cung cấp vốn tạo thanh khoản và những người cung cấp tính toán, lưu trữ và băng thông. Đây đã được chứng minh rõ ràng qua lịch sử của Bitcoin và Ethereum rằng sự cạnh tranh tự do & mở về các token số hiếm có thể cung cấp cơ sở hạ tầng có thể mở rộng cho một blockchain công cộng trong thời gian dài.

![MorpheusNetworkDiagram](https://github.com/MorpheusAIs/Morpheus/assets/1563345/f0960e25-80e3-42ed-aa1f-ad9792eb672d)
## Bối cảnh & Lịch sử
Các nhà đương nhiệm như OpenAI, Microsoft và Google đều đang vận hành các mô hình ngôn ngữ mã nguồn , tính phí giấy phép cho khách hàng và tạo thu nhập từ dữ liệu của khách hàng. Những mô hình này bị kiểm duyệt, mỏng manh và hoạt động trong những hệ thống kín. Có một nhu cầu lớn cho một mô hình ngôn ngữ lớn mã nguồn mở có sẵn miễn phí. Llama, Falcon và các mô hình LLM mã nguồn mở khác đã được phát hành gần đây và đang nhanh chóng tiến dần đến độ chính xác của các đối thủ mã đóng của họ.

Những gì các mô hình LLM mã nguồn mở này hiện nay thiếu là một giao diện đồ họa tiêu chuẩn cho người dùng có thể trò chuyện với chúng, một API cho các nhà phát triển, một giải pháp dạng đám mây để di chuyển giữa các thiết bị và một cách để quản lý dữ liệu người dùng và quá trình phục hồi. Đây là nơi mà Giao thức Smart Agent xuất hiện, vì nó cung cấp một mô hình LLM mã nguồn mở được chạy cục bộ và được quản lý bởi ví Web3 của người dùng.

Tuy nhiên, phương pháp chỉ cục bộ vẫn thiếu một API cho các nhà phát triển để xây dựng và giải pháp đám mây nơi mà một mạng lưới người dùng có thể chạy phần mềm trên phần cứng mạnh để kích hoạt các trường hợp sử dụng như các khách hàng nhẹ, nơi mà người dùng không cần phải tải xuống toàn bộ node hoặc Smart Agent cục bộ.

## Tiến Vào Morpheus
Morpheus sẽ cung cấp các API và các chức năng đám mây phi tập trung này thông qua việc triển khai mạng lưới và một token để thưởng cho những người cung cấp cơ sở hạ tầng blockchain công cộng này cho cộng đồng Smart Agent. Là một phiên bản thực thi của Giao thức Smart Agent, Morpheus tìm kiếm thu thập các nguồn lực cần thiết cho Trí tuệ Nhân tạo cá nhân dựa trên mã nguồn mở để phù hợp và vượt qua khả năng của các công ty công nghệ đang cung cấp các mô hình GPT đóng ngày nay.

Morpheus có nhiều ưu điểm ngay từ đầu. Với tính chất Web3 nguyên bản, người dùng có thể mua bán tiền điện tử, gửi stablecoins, truy cập các hợp đồng thông minh và sử dụng các dịch vụ Dapps và DeFi, mà hiện tại không có LLM nào được kết nối. Các rào cản pháp lý được đối mặt bởi các công ty tập trung ngăn chúng khỏi việc cung cấp các công cụ này cho người dùng, để các mô hình của họ có thể trò chuyện về các nhiệm vụ nhưng không thể hành động thay mặt người dùng trong bối cảnh Web3. Việc chạy trên cơ sở hạ tầng công cộng phi tập trung rẻ hơn so với việc trả phí giấy phép cho Chat GPT cho mỗi người dùng mới.

Morpheus là sự lựa chọn kiểu Linux cho các nhà phát triển muốn có khả năng triển khai nhanh chóng các đại lý/ LLM mới mà không tốn phí. Người dùng có thể giữ quyền sở hữu của dữ liệu kinh doanh hoặc cá nhân của họ. Điều này tránh rò rỉ, hack và tấn công từ đối thủ. Bằng cách thưởng cho các nhà phát triển về việc đóng góp mã không chỉ cho Morpheus mà còn để xây dựng các Đại lý chuyên biệt hơn, một trải nghiệm kiểu Cửa hàng Ứng dụng/Đại lý cho người dùng sẽ phát triển. Với tính liên tục của dữ liệu, gợi ý và lịch sử do người dùng sở hữu, Giao thức Smart Agent trở thành giải pháp tốt nhất cho khả năng tương tác trong thế giới của các LLM và Đại lý.

Cuối cùng, việc Morpheus có một giao diện đồ họa và tận dụng Electron để đóng gói nó như một cài đặt chỉ với một cú nhấp chuột cho phép Morpheus trở thành trí tuệ nhân tạo mã nguồn mở đầu tiên vượt qua "Friedl test" nổi tiếng. Đây là một ngưỡng mốc đánh giá lần đầu khi tính dễ sử dụng của phần mềm khiến nó trở nên tiếp cận được với các thành viên không chuyên về kỹ thuật của công chúng chung.

## Phần thưởng & Kinh tế Token
Đề xuất của chúng tôi cung cấp điều này thông qua một token Morpheus (ký hiệu "MOR"). MOR được thưởng mỗi ngày 24% cho cộng đồng, 24% cho vốn, 24% cho tính toán, 24% cho các lập trình viên, và 4% cho quỹ bảo vệ.
Điều này phản ánh thực tế rằng để Morpheus phát triển, nó cần các yếu tố sau:

Cộng đồng: Người xây dựng tạo ra giao diện người dùng / công cụ và đưa người dùng vào hệ sinh thái của Morpheus.

Vốn: Mang lại nguồn vốn cho tính toán và mã nguồn.

Tính toán: Cung cấp thiết bị và năng lượng.

Các lập trình viên: Cung cấp sự thông minh để sử dụng giao diện người dùng, vốn và tính toán.

Tổng cung cấp token MOR được giới hạn tối đa là 42.000.000 token sẽ tồn tại. Phân phối sẽ bắt đầu với tất cả bốn nhóm đều kiếm được token bằng cách cung cấp các hình thức bằng chứng về lao động (labor) và bằng chứng về vốn (stake) cho mạng lưới. Không mine trước. Không có bán token sớm. Chỉ là một lần khai trương công bằng.

![MOREmissionsCurve2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/3514217c-50ed-4639-8c5d-87ca5cfb5d1b)

Phần thưởng khối sẽ bắt đầu từ 14.400 MOR mỗi ngày và sau đó sẽ giảm đi 2,468994701 MOR mỗi ngày cho đến khi phần thưởng giảm xuống 0 vào ngày thứ 5.833. Đến thời điểm đó (khoảng 16 năm nữa) miễn là Morpheus được sử dụng rộng rãi, phí sẽ trở thành động lực chính. Phí được trả cho người dùng cho dữ liệu của họ, phí cho các nhà cung cấp tính toán, phí cho các nhà cung cấp vốn và phí cho các lập trình viên.

**Có 42 triệu MOR tokens được giới hạn cung cấp.** 14.400 tokens mỗi ngày được phân phối đều giữa cộng đồng, vốn, mã nguồn và tính toán.

- 3.456 tokens cho tính toán. Bằng chứng cho các giao dịch API được phục vụ.
- 3.456 tokens cho mã nguồn. Bằng chứng cho mã nguồn được cam kết và được kết hợp vào repo của Morpheus.
- 3.456 tokens cho vốn. Bằng chứng cho lợi suất stETH được đóng góp, 50% được đổi sang MOR và kết hợp với 50% còn lại để khóa trong AMM như một Nguồn cung cấp thanh khoản của Giao thức (PoL).
- 3.456 tokens cho cộng đồng. Bằng chứng cho việc xây dựng các ứng dụng giao diện người dùng và công cụ mà thu hút người dùng tham gia. Phần còn lại được dành cho tài nguyên bảo vệ: 576 tokens mỗi ngày cho mục đích đó.
![5050version3](https://github.com/MorpheusAIs/Morpheus/assets/1563345/c9fe763f-d4e4-4069-b9c9-75e0a777c3ad)

## Tiện ích của token MOR
Mục tiêu là để MOR cung cấp tiện ích rộng rãi trong nhiều chức năng của mạng lưới Morpheus. Do đó, việc sử dụng token MOR cung cấp một cơ chế kế toán trên chuỗi để tính toán phần thưởng dựa trên việc sử dụng thực tế của phần mềm.

Các nhà phát triển thanh toán MOR các nhà cung cấp tính toán cho các chức năng vượt quá những gì phần cứng cục bộ có thể thực hiện. MOR này trả cho các cuộc gọi API của Morpheus cho các ứng dụng phi tập trung sử dụng Giao thức Smart Agent. Người dùng có thể trả MOR cho các Agent chuyên biệt được phát hành bởi các nhà phát triển. Lượt lại, các nhà phát triển có thể trả cho người dùng MOR để đào tạo dữ liệu cho các LLM/Agent mới.

Tất cả các dự án đều trải qua các giai đoạn phát triển. Quan trọng là ở giai đoạn ban đầu, các nguồn lưu thông như ETH được sử dụng để trả tiền cho các nhà phát triển và cho thiết bị. Ethereum đã làm điều tương tự khi họ sử dụng BTC từ cộng đồng của họ để trả tiền cho việc lập mã ban đầu cho blockchain của họ. Sự khác biệt ở đây là Giao thức Smart Agent đã được phát triển và Morpheus đang triển khai một phiên bản để mở rộng phạm vi của nó, vì vậy không cần thiết phải có một đợt bán cho công chúng trước khi dự án đi vào hoạt động. Token MOR chỉ được thưởng sau khi phần mềm đã hoạt động.
## Trong tương lai gần: Khi dự án được ra mắt
- Vốn - Nhà cung cấp vốn nhận phần thưởng MOR dựa theo tỷ lệ vào stETH mà họ đã đóng góp so với tổng số stETH được gửi.
- Tính toán - Nhà cung cấp tính toán nhận MOR cho những yêu cầu mà họ trả lời cho người dùng.
- Lập trình viên - Lập trình viên nhận MOR cho những đóng góp mà họ đưa vào phần mềm Morpheus và được kết hợp vào.
- Cộng đồng - Người xây dựng cộng đồng nhận MOR cho các giao diện người dùng, công cụ, sử dụng và giá trị mà họ mang vào mạng lưới Morpheus.

## Trung hạn: Khi MOR được Lan rộng hơn
- Vốn - Sự cân bằng giữa phần thưởng khối và phí kiếm được phát triển.
- Tính toán - Sự cân bằng giữa phần thưởng khối và phí kiếm được phát triển.
- Lập trình viên - Sự cân bằng giữa phần thưởng khối và phí kiếm được phát triển.
- Cộng đồng - Sự cân bằng giữa phần thưởng khối và phí kiếm được phát triển.

## Dài hạn: Khi MOR có Thanh khoản Sâu và Nhu cầu Tự nhiên Mạnh mẽ
- Vốn - Phí cho việc cung cấp thanh khoản cho token MOR sẽ cung cấp phần lớn phần thưởng của họ.
- Tính toán - Phí được trả cho các nhà cung cấp tính toán sẽ chiếm phần lớn phần thưởng của họ.
- Lập trình viên - Phí được trả cho các lập trình viên sẽ chiếm phần lớn phần thưởng của họ.
- Cộng đồng - Phí được trả bởi người dùng sẽ cung cấp phần lớn phần thưởng của họ.

Lưu ý rằng đây không phải là một kế hoạch thời gian. Thay vào đó, mỗi giai đoạn là một mô tả về một phần của chu trình đời sống. Có thể mất nhiều năm để cộng đồng phát triển và trưởng thành qua từng giai đoạn, và phần thưởng khối sẽ hết hạn sau khoảng 16 năm. Lịch phân phối dài hạn này nhằm mục đích để tạo ra thời gian cho các token được thưởng trên một cơ sở rộng lớn toàn cầu. Ngoài ra, việc giảm dần hàng ngày mịn màng trong phần thưởng khối qua nhiều năm sẽ mang lại thời gian cho tất cả các thành viên để đạt được quy mô và chuyển từ phần thưởng được tài trợ ban đầu sang hoạt động chỉ bằng các phí họ kiếm được.

![MOREmissionSchedule](https://github.com/MorpheusAIs/Morpheus/assets/1563345/94c96cb0-b6e4-4c63-be46-39088c91e168)

## Tích lũy cuối cùng của token MOR
Kể từ khi Bitcoin ra mắt, mọi người đã tranh luận về "diễn biến sẽ xảy ra khi phần thưởng khối cuối cùng dừng lại?" Để tránh cuộc tranh luận không có ích này trong bối cảnh của Morpheus và tiếp tục điều chỉnh các nhà lập trình mới, cộng đồng, nhà cung cấp tính toán & vốn vào dài hạn, chúng tôi đề xuất một "tích lũy cuối" của token MOR. Tích lũy cuối của MOR này sẽ bắt đầu sau khi tất cả các token MOR cuối cùng đã được phát hành vào ngày thứ 5.833 của lịch phân phối.

Tích lũy cuối sẽ được tính toán bằng cách xem xét số lượng token MOR đã bị đốt trong 5.833 ngày qua và thiết lập giá trị tích lũy cuối là 50% của số lượng đã bị đốt. Giá trị tích lũy cuối này sẽ được phát hành trong khoảng thời gian 5.833 ngày kế tiếp. Nhưng trong bất kỳ trường hợp nào, tích lũy cuối cũng sẽ không lớn hơn 16% của tổng số MOR đang lưu thông tại thời điểm đó.

Ví dụ, nếu trung bình 25% số lượng token MOR đã bị đốt trong 5.833 ngày đầu tiên thì 10.500.000 MOR sẽ đã bị đốt trong kế hoạch phát hành đầu tiên. Sau đó, bằng cách áp dụng giá trị tích lũy cuối 50%, chúng tôi tính được 5.250.000 MOR có thể được thưởng trong giai đoạn 5.833 ngày tiếp theo. Điều này tương đương với khoảng 16.6% của 31.500.000 MOR còn lại lưu thông. Do đó, số lượng này sẽ được giảm xuống thêm thành 5.040.000 MOR (16% của số lượng MOR lưu thông) để được thưởng trong giai đoạn 5.833 ngày tiếp theo hoặc khoảng ~864 MOR mỗi ngày.

Sau khi kỳ giai đoạn 5.833 ngày thứ hai kết thúc, quy trình này sẽ lặp lại. Tích lũy cuối sẽ được tính toán lại bằng cách xem xét số lượng token MOR đã bị đốt trong 5.833 ngày qua và thiết lập giá trị tích lũy cuối là 50% của số lượng đã bị đốt. Giá trị tích lũy cuối này sẽ được phát hành trong khoảng thời gian 5.833 ngày kế tiếp. Nhưng trong bất kỳ trường hợp nào, tích lũy cuối cũng sẽ không lớn hơn 16% của tổng số MOR lưu thông tại thời điểm đó.

Ví dụ, một lần nữa, nếu 25% số lượng token MOR đã bị đốt trong giai đoạn thứ hai, điều đó tương đương với 9.135.000 MOR đã bị đốt trong kế hoạch phát hành thứ hai. Sau đó, 4.567.500 MOR có thể được thưởng trong giai đoạn 5.833 ngày thứ ba. Tuy nhiên, vì số lượng này nhiều hơn 16% của tổng số 27.405.000 MOR còn lại lưu thông tại thời điểm đó, nó sẽ được giảm xuống thành 4.384.800 MOR để phù hợp với 1% phần thưởng hàng năm (tương đối với số lượng token lưu thông).

Quy trình này sẽ lặp lại mãi mãi trong tương lai. 

Kết quả dài hạn là khoảng 1% phần thưởng hàng năm MOR (tương đối với số lượng MOR lưu thông tại thời điểm đó) sẽ có sẵn cho các nhà lập trình, tính toán, cộng đồng & vốn trong tương lai.

![MaxMORScenario25](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/81c7794a-b5bc-4a9e-bb2d-1f28b98ea079)

> [!Chú ý] 
> Điều này không làm thay đổi bản chất của giới hạn cung cấp cứng là 42 triệu MOR.
> Vì lịch phát sinh đuôi theo định nghĩa chỉ là một phần của các token MOR đã bị đốt, do đó token MOR chỉ có thể trở nên ngày càng khan hiếm hơn với mỗi chu kỳ 5.833 ngày.

![MOR25ScenarioV9](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/4813cd02-b104-4a0c-893b-a7fd329fe2a3)

Dưới đây là đường cong cung MOR thống nhất, cho thấy giai đoạn 5.833 ngày đầu tiên và thêm các phát sinh dài hạn từ năm thứ 17 đến năm thứ 256 giả định ví dụ về tỷ lệ đốt trung bình 25% của MOR qua các kỷ nguyên.

![MORSupplyCurve20231019](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/8994c389-dad1-4e46-9b63-e048da8ef172)



## Bằng chứng về Cộng đồng, Mã nguồn, Tính toán & Vốn
Nút đầy đủ của Morpheus đi kèm với một ví hoặc người dùng có thể kết nối ví hiện tại của họ. Điều này cho phép người dùng ký và gửi các giao dịch được đề xuất bởi Smart Agent của họ. Do đó, người dùng sẽ có thể tham gia vào các bằng chứng thông qua phần mềm Morpheus. Tuy nhiên, các Nhà cung cấp Vốn không cần phải có một nút đầy đủ ví dụ. Họ có thể tương tác trực tiếp với các Hợp đồng Thông minh trên Ethereum / Arbitrum bằng cách sử dụng stETH.

## Chứng Tài vốn & Phần thưởng:
Định nghĩa về Nhà cung cấp Vốn là người cung cấp stETH tạo ra lợi suất cho mạng lưới Morpheus mà trở thành Tính chất Sở hữu của Giao thức (PoL). Hợp đồng Thông minh Nhà cung cấp Vốn sẽ cung cấp 50% lợi suất của stETH được tạo ra cho chức năng hoán đổi Morpheus. Giao dịch hoán đổi mua các token MOR từ một Trái đào tạo Tự động (AMM) sau đó ghép chúng với 50% còn lại của lợi suất stETH và khóa vào Hồ Chứng khoán AMM như PoL. Điều này sẽ cung cấp thanh khoản cho tất cả những lập trình viên, người xây dựng cộng đồng và nhà cung cấp tính toán. Các phí kiếm được từ vị trí thanh khoản được tái đầu tư vào hồ bảo đảm đảm bảo sự tăng trưởng thanh khoản ổn định.

Theo cách này, toàn bộ lợi suất kiếm được từ các khoản gửi stETH của người dùng được chuyển đổi thành tính chất sở hữu của giao thức (PoL). Lợi suất được giữ lại như PoL mãi mãi, nhưng người dùng có thể rút stETH của họ bất cứ lúc nào sau một thời gian khóa ban đầu là 7 ngày. Nếu stETH được rút, phần thưởng MOR sẽ ngừng được tích lũy.

Kết quả là, Nhà cung cấp Vốn sẽ nhận được token MOR (tính toán mỗi khối) phản ánh theo tỷ lệ với đóng góp stETH của họ so với tổng số stETH được gửi. Ví dụ, nếu có 100 Nhà cung cấp Vốn mỗi người đóng góp 1 stETH vào ngày 1 khi mạng lưới ra mắt, và tổng pool bằng 100 stETH, thì mỗi người sẽ nhận được 1% của 3.456 token MOR trong ngày đó = 34,56 MOR.

Đã được đề xuất gọi quá trình đóng góp lợi suất này, hoán đổi và thêm thanh khoản là "TCM". Viết tắt của "techno-capital machine" để tôn vinh nhà triết học e/acc [Beff Jezos](https://twitter.com/BasedBeffJezos).

Xem liên kết đến lời giải thích chi tiết của Tеchno Capital Machine tại đây: [TCM](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md)


## Chứng minh, Đăng ký & Phần thưởng Mã nguồn:
Định nghĩa về Lập trình viên là người đã tải xuống và chạy nút đầy đủ của Morpheus, kết nối ví của họ và đóng góp một trình điều khiển, hợp đồng thông minh hoặc phần mềm khác vào Mạng lưới Morpheus. Mã phải tuân thủ các Tiêu chuẩn Tốt nhất cho Đóng góp Mã.

Lập trình viên sẽ gửi một giao dịch MOR đến Hợp đồng Thông minh Lập trình viên để đăng ký trình điều khiển / hợp đồng thông minh hoặc phần mềm của họ. Lập trình viên sẽ bao gồm trong phần ghi chú của giao dịch các siêu dữ liệu sau đây.

- A. Một liên kết IPFS đến điểm cuối phần mềm của họ trong trường ghi chú của giao dịch MOR khi họ đăng ký.
- B. Một chữ ký mật mã, tương tự như cách các nhà phát triển ký xác thực ra mắt ứng dụng.
- C. Số phiên bản của phần mềm.
- D. Một mã băm của trạng thái của chương trình, để người dùng có thể kiểm tra đó là một bản sao hợp lệ và không thay đổi.

Những người đóng góp cho cơ sở mã nguồn của Morpheus được thưởng tỷ lệ với toàn bộ phát triển tích lũy trên kho lưu trữ, dựa trên công việc đầy đủ thời gian tương đương (FTE) đóng góp. Ví dụ, nếu có 10 lập trình viên mỗi người đã đóng góp 10% thời gian FTE (được định mức bằng trọng lượng) khi mạng lưới ra mắt, thì mỗi người sẽ nhận được 10% của 3.456 token MOR mỗi ngày = 345,6 MOR. Tính toán này được cập nhật hàng tháng dựa trên tổng thời gian FTE tích lũy (định mức bằng trọng lượng) đóng góp của phiên bản mainnet hiện tại của phần mềm Morpheus.

Khái niệm ở đây KHÔNG dựa trên Lý thuyết Lao động của Giá trị. Không quan trọng số giờ làm việc là bao nhiêu mà là giá trị mà công việc tạo ra. Đó là lý do tại sao chủ sở hữu kho lưu trữ phải thực sự hợp nhất mã (sản phẩm của công việc) để nó được tính vào phần thưởng. Chủ sở hữu kho lưu trữ hành động như "khách hàng" trong thị trường.

Nếu người đóng góp Mã yêu cầu quá nhiều trọng lượng cho Đóng góp, hoặc chất lượng của đóng góp không đủ điều kiện, hoặc có chất lượng thấp, nó có thể bị từ chối bởi chủ sở hữu kho lưu trữ. Và trong khi bất kỳ ai "có thể" tạo một kho lưu trữ nhưng cần rất nhiều công việc để duy trì và cũng thu hút người đóng góp để đóng góp vào kho lưu trữ của bạn hơn so với các kho lưu trữ khác, vì vậy thị trường có khả năng tập trung vào các kho lưu trữ tốt nhất với nhiều người đóng góp nhất và mã tốt nhất.

Kinh tế mã nguồn mở và thị trường tự do chiến thắng.

Khi có các trình điều khiển, công cụ hoặc chuỗi chuyển đổi (trình tự các lời nhắc/gọi đến LLM) chuyên biệt tương thích với Morpheus, thì nửa (50%) phần thưởng sẽ được trao cho các nhà phát triển của họ. Phần thưởng sẽ được tính toán tỷ lệ với việc sử dụng của các trình điều khiển đó. Ví dụ, nếu có 10 nhà phát triển đã xây dựng 10 trình điều khiển mỗi trình điều khiển tạo ra 10% của lưu lượng sử dụng trên mạng lưới Morpheus. Hợp đồng thông minh Morpheus sẽ tính toán các thống kê sử dụng đó thông qua các giao dịch MOR. Sau đó, các lập trình viên phần mềm Morpheus sẽ kiếm được 50% phần thưởng MOR và mỗi nhà phát triển của một trình điều khiển chuyên biệt sẽ nhận được 5% các token = 172,8 MOR cho mỗi nhà phát triển trong ví dụ này.

Nhiều nghiên cứu hàng đầu đã được thực hiện trong lĩnh vực "Bằng chứng về Đóng góp" bởi các người tốt lành tại Giao thức TEA. Bao gồm Max Howell - nhà phát triển của Home Brew. Thêm thông tin chi tiết có thể được tìm thấy [tại đây](https://docs.tea.xyz/tea-white-paper/white-paper). Morpheus có thể xem xét sử dụng TEA sau khi ra mắt vào năm 2024.

## Chứng minh Tính toán & Phần thưởng:
Một Nhà cung cấp Tính toán được định nghĩa là bất kỳ thực thể nào chạy một nút đầy đủ cung cấp các nguồn lực tính toán, có một địa chỉ MOR và cung cấp các lượt chào giá IPS (inferences per second, một đơn vị nguyên tử của suy luận trong trí tuệ nhân tạo) thông qua Router. Khi một Nhà cung cấp giành chiến thắng trong chào giá, nó cung cấp nguồn lực tính toán (GPU, v.v.) cho các mô hình trí tuệ nhân tạo khác nhau cho người dùng. Các nhà cung cấp chỉ cần chứng minh rằng họ có một LLM nhất định, bằng cách ký mã băm của mô hình LLM với chìa khóa của họ. Các Nhà cung cấp Tính toán chỉ được thanh toán khi có nhu cầu về tính toán của họ. Điều này ngăn chặn tình huống mà một phần lớn MOR được phát ra quá sớm khi mạng lưới không cần.

Để đủ điều kiện để nhận các yêu cầu Tính toán, địa chỉ của Nhà cung cấp Tính toán phải HODL các token MOR làm đơn vị ngăn chặn các cuộc tấn công Sybil.

Loại phần cứng của Nhà cung cấp không liên quan đến mạng lưới, miễn là họ đáp ứng được kiểm tra Pass/Fail của Người dùng. Bất kỳ Nhà cung cấp nào đặt chào giá trên số Lượt truy vấn mà họ không thể xử lý một cách hiệu quả sẽ bị phạt bằng cách thất bại trong kiểm tra này.

Router là một ứng dụng phần mềm có địa chỉ MOR và thực hiện thị trường hai bên giữa Người dùng và Nhà cung cấp. Router đăng ký và theo dõi các địa chỉ và các lượt chào giá của Nhà cung cấp, xử lý các Yêu cầu từ Người dùng, ghi lại [mili giây] và kiểm tra Pass/Fail của các Yêu cầu đã xử lý, và hướng dẫn Hợp đồng Tính toán để tín dụng các Nhà cung cấp đủ điều kiện cho việc thanh toán bằng MOR khi được yêu cầu. Router không bao giờ gửi hoặc nhận các giao dịch MOR (hoặc giao dịch trên bất kỳ blockchain nào). Router không bao giờ thấy nội dung của một Yêu cầu, cũng như phản hồi.

### Quy trình
1) Người dùng, Nhà cung cấp và Router đều tạo khóa pub MOR của họ (đây là danh tính của họ và tất cả các tin nhắn đều được ký như vậy).
2) Nếu Người dùng giữ bất kỳ số dư MOR nào, Người dùng có thể gửi một RFC đã ký cho Tính toán "RFC" cho Router.
3) Router ưu tiên các RFC dựa trên số dư MOR của Người dùng.
4) Router chọn Nhà cung cấp hỗ trợ [LLM], ưu tiên dựa trên Chào giá thấp nhất mỗi IPS trong MOR.
5) Router gửi kiểm tra sự sống cho Nhà cung cấp. Nếu Pass, sau đó:
6) Router kết nối Người dùng với Nhà cung cấp
7) Người dùng gửi Truy vấn ([LLM],[lời nhắc]) cho Nhà cung cấp
8) Nhà cung cấp tính toán Truy vấn, gửi Kết quả cho Người dùng
9) Người dùng báo cáo Thời gian [miligiây] giữa Bước 4 & 5, [IPS] được giao, và Pass/Fail cho Router
10) Router hướng dẫn Hợp đồng Tính toán để tín dụng Nhà cung cấp đủ điều kiện với MOR nếu [miligiây] trên [IPS] không tệ hơn X% so với trung bình của Z truy vấn trước đó cho [LLM] đó và nếu Người dùng báo cáo [Pass].
11) (Sau một thời gian nào đó) Nhà cung cấp yêu cầu thanh toán MOR từ Hợp đồng Tính toán và Hợp đồng Tính toán gửi thanh toán MOR nếu hợp lệ (giao dịch blockchain đầu tiên cho đến nay, có thể được gom nhóm).

![ComputeContractImage2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/e66ea20c-9851-4f9e-9caa-66c6d798c462)

### Khuyến khích khởi động tính toán
Trong năm đầu tiên sau giai đoạn khởi động của Hợp đồng Vốn, 100 nhà cung cấp Tính toán hàng đầu sẽ được quyền nhận một phần trăm theo tỷ lệ của 2,4% số lượng MOR phát ra. Điều này được tính bởi các router và được ghi nhận trong hợp đồng tính toán.

Để biết thông tin chi tiết, vui lòng truy cập [Yellowstone Compute Model paper](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Yellowstone%20Compute%20Model.md)



## Chứng minh, đăng ký & thưởng Xây dựng Cộng đồng:
Định nghĩa của một Người xây dựng Cộng đồng là họ đã tải xuống và chạy nút đầy đủ của Morpheus, kết nối ví của họ và đang sử dụng API của Morpheus để cung cấp giao diện người dùng và công cụ phát triển. Đóng góp của họ có thể được tính bằng cách bao gồm một giao dịch được ký do Smart Agent tạo ra với việc trả lại đầu ra từ giao dịch MOR.

Người xây dựng Cộng đồng sẽ gửi một giao dịch MOR đến Hợp đồng Thông minh Người xây dựng Cộng đồng để đăng ký điểm cuối API để nhận các yêu cầu. Người xây dựng Cộng đồng sẽ bao gồm trong phần ghi chú của giao dịch các siêu dữ liệu sau đây.

- A. Một liên kết IPFS đến giao diện hoặc công cụ của họ qua một điểm cuối trong trường ghi chú của giao dịch MOR khi họ đăng ký.
- B. Một chữ ký mật mã, tương tự như cách các nhà phát triển ký xác thực ra mắt ứng dụng.
- C. Số phiên bản của phần mềm Morpheus mà họ đang sử dụng.
- D. Một mã băm của trạng thái của giao diện / công cụ, để người dùng có thể kiểm tra đó là một bản sao hợp lệ và không thay đổi.
Số phí giao dịch MOR được đốt bởi mỗi Người xây dựng Cộng đồng phục vụ như bằng chứng về tình trạng của Người xây dựng Cộng đồng và kiếm được một phần của số lượng token MOR mỗi ngày.

Ví dụ, nếu có 100 Người xây dựng Cộng đồng vào ngày 1 khi mạng lưới ra mắt, thì mỗi người sẽ nhận được một phần thưởng theo tỷ lệ dựa trên số lượng MOR họ đã đốt bằng phí. Trong trường hợp này, giả sử mỗi trong số 100 Người xây dựng Cộng đồng đã đốt 100 MOR, sau đó 1% của 3.456 token MOR mỗi ngày = 34,56 MOR.

## Sơ đồ Người Dùng của Morpheus
![UpdatedDiagram2UserFlow](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a02468a7-9284-4ce5-b7e3-f32f476ff9f1)
## Phần thưởng của Morpheus được giao thông qua Hợp đồng Thông minh trên Ethereum Layer 2
Việc gửi stETH để nhận phần thưởng sẽ được thực hiện trên mainnet Ethereum, khi các token Morpheus (MOR) sẽ được trao tặng trên Ethereum Layer 2 Arbitrum, với mục đích thanh toán và các hoạt động liên quan đến tiện ích MOR khác.

Lưu ý rằng Morpheus không cần phải dành phần thưởng MOR cho sự nhất quán blockchain hoặc thực thi giao dịch trên một sổ cái phân tán nhờ vào việc xây dựng trên Ethereum và Layer 2 Arbitrum.

Các chủ sở hữu MOR sẽ có thể gửi một giao dịch đến Hợp đồng Thông minh MOR và nhận phần thưởng MOR của họ bất cứ lúc nào. Họ cũng có thể rút stETH của họ bất cứ lúc nào.

Thị trường tự do đặt các phí trên Morpheus

Các hệ thống tốt nhất chọn số lượng ít nhất các con số ma thuật và thay vào đó để thị trường tự do quyết định càng nhiều biến số càng tốt. Phí là một ví dụ tốt về điều này. Thay vì chọn một khoản phí tùy ý để thu thập, Morpheus để lại những con số này cho người dùng, nhà phát triển, cung cấp vốn và tính toán. Ví dụ, nếu một nhà cung cấp tính toán có thể cung cấp giá 0,02 đô la cho mỗi 1.000 IPS cho LLM của họ và một người dùng quyết định trả tiền cho nó, thì đó là điều thị trường sẵn lòng trả tiền. Khi tính toán tăng tốc, giá cả có khả năng thay đổi và vì vậy tốt hơn là để lại những biến số này và các biến số khác cho những người sử dụng phần mềm Morpheus.

## Phí cho Compute
Số tiền phí được đặt qua quá trình đấu giá cạnh tranh giữa người dùng và nhà cung cấp tính toán. Thị trường mở để phát triển theo thời gian. Thị trường tự do cho tính toán thay vì sự nhất quán hoặc các nút đặc quyền.

**Phí cho Code / Agent Intelligence**

Số tiền phí được đặt bởi người lập trình và được chấp nhận bởi người dùng. Tùy chọn trả phí và đốt MOR token với mỗi khoản phí. Thị trường mở để phát triển theo thời gian. Thị trường tự do cho mã hóa thay vì sự nhất quán trên các nhiệm vụ.

**Phí cho Vốn**

Số tiền phí được đặt bởi sự phát hành MOR hàng ngày và được chấp nhận bởi người dùng muốn cung cấp vốn. Thị trường mở để phát triển theo thời gian. Thị trường tự do cho vốn thay vì sự nhất quán trên ngân khoán.

**Phí cho Cộng đồng Người dùng**

Số tiền phí được đặt bởi người dùng và được chấp nhận bởi người mua dữ liệu. Tùy chọn trả phí và đốt MOR token với mỗi khoản phí. Thị trường mở để phát triển theo thời gian. Thị trường tự do cho dữ liệu.

Tất cả các khoản phí được thanh toán bằng MOR token gốc tạo ra nhu cầu tự nhiên trong hệ thống khi sử dụng tăng lên.

## Sử dụng các khoản phí để khuyến khích các Agent Chân thực và Khắc phục Thiệt hại trong Trường hợp Lỗi
Một ứng dụng quan trọng khác cho MOR & ETH trong mạng lưới Morpheus sẽ là bồi thường người dùng trong trường hợp Smart Agent / Smart Contract gặp sự cố. Chúng tôi tin rằng việc xây dựng và phát triển danh tiếng được hỗ trợ bằng tài nguyên kinh tế sẽ là chìa khóa để tăng sự tự tin vào Smart Agents và có nguồn tài trợ để giải quyết các lỗi, lỗi và vấn đề khác phát sinh. Sau một lỗi lớn và kết quả là fork cứng của Bitcoin vào năm 2010, một nhà phát triển lõi sớm tên là Gavin Andresen đã bước lên trả tiền Bitcoin cho các thợ mỏ đã mất phần thưởng do fork cứng. Hành động này quan trọng và nhanh chóng giải quyết fork cứng nhưng nó là tùy ý.

Nhận ra từ trước rằng phần mềm không bao giờ hoàn hảo, Morpheus đang dành 4% của tài nguyên MOR để hoàn trả cho những người bị ảnh hưởng bởi lỗi trong mã. Cộng đồng phát triển Morpheus sẽ phục vụ như một bộ lọc để nhận biết khi nào một lỗi hoặc sự cố đã có tác động kinh tế đối với một người dùng, nhà cung cấp tính toán hoặc nhà cung cấp vốn. Một tập hợp được xác định trước các lỗi sẽ được bảo vệ bằng các tài nguyên này để bao gồm lỗi trong Hợp đồng Thông minh Morpheus hoặc cài đặt cục bộ.

Để bảo vệ rộng lớn hơn, một tích hợp với Nexus Mutual hoặc mạng lưới bảo vệ thông minh / phân cấp tương tự có thể được xem xét để bảo vệ các trường hợp cạnh tranh với các agent / smart contract muốn được bao gồm trong một Morpheus Agent Store hoặc được xếp hạng tốt hơn bởi thuật toán SmartContractRank.

Chi tiết về quỹ bảo vệ có sẵn [tại đây](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md)
## Lưu trữ cho Sự kiên nhẫn & Ví để phục hồi
Thay vì lưu trữ dữ liệu cá nhân trong mạng lưới Morpheus chính mình, điều này sẽ làm tăng chi phí và là một lực lượng trung tâm, cá nhân sẽ giữ các khóa riêng tư kiểm soát quyền truy cập vào dữ liệu, gợi ý & ví. Dữ liệu chính sẽ được lưu trữ bằng tiêu chuẩn IPFS và mạng lưu trữ lâu dài phân tán Filecoin. Tận dụng EVM Filecoin và DeFi cho lợi suất một lần lặp lại lưu trữ có thể được sắp xếp. Theo cách tiếp cận này, người dùng có thể tiếp tục giữ Ví Web3 riêng tư như là khóa cho sự di chuyển / phục hồi của dữ liệu này đến các thiết bị khác nhau khi người dùng thay đổi máy tính hoặc điện thoại.

## Morpheus Tech Stack, Smart Contract & Phát triển
Việc triển khai của Morpheus của Giao thức Smart Agent sẽ là một fork trực tiếp của repo đang chạy cục bộ hiện tại. Thay đổi quan trọng nhất sẽ là cập nhật SmartContractRank để bao gồm kiến thức về token MOR và các chức năng của nó trong việc cung cấp năng lượng cho một mạng lưới các Smart Agent.

Token MOR của Morpheus đang được phát triển như là một Hợp đồng Thông minh trên Ethereum thông qua tiêu chuẩn ERC20 cho các token có thể trao đổi. Hầu hết các hợp đồng thông minh đều nằm trên Ethereum và Máy ảo Ethereum đã trở thành ngôn ngữ phổ thông của không gian Web3. Để giảm chi phí gas cho việc gửi phần thưởng hàng ngày, chúng tôi sẽ tận dụng layer 2 của Ethereum gọi là Arbitrum.

Chúng tôi tin rằng việc chọn blockchain Ethereum là điểm khởi đầu tốt nhất vì các hành động trên chuỗi như staking ETH chỉ có thể được xác nhận bằng một hợp đồng thông minh chạy trên cùng một chuỗi. Ngoài ra, việc xác minh trên chuỗi về mã hóa thông qua tên miền ENS hoặc địa chỉ công cộng Ethereum thêm một phương tiện khác để kết nối mã được đóng góp vào ví của người lập trình đã cung cấp nó. Một bản ghi mà Hợp đồng Thông minh Morpheus có thể truy cập hàng ngày.

Ngoài ra, bằng chứng không chứng minh cho tính có thể mở rộng và quyền riêng tư là chìa khóa cho nhiều trường hợp sử dụng. Vì vậy, bắt đầu với những khả năng này, ngày một sẽ đưa cộng đồng Smart Agent vào vị trí tốt nhất cho tương lai. Arbitrum đang trong quá trình thêm công nghệ ZK, một phần đã được triển khai.

Trong tương lai gần, việc lựa chọn ngăn xếp công nghệ này đảm bảo Morpheus trực tiếp trong bảo mật lớp 1 của Ethereum với chi phí gas giảm của lớp hai. Trong dài hạn, việc lựa chọn này cũng cung cấp một lộ trình để mở rộng Morpheus đến các lớp 2 khác của Ethereum và các blockchain tương thích với EVM.

Khi tính tương thích giữa các blockchain công cộng cải thiện, Morpheus sẽ cố gắng phục vụ tất cả các nhà xây dựng Smart Agent Web3 trên các cộng đồng nhà phát triển tương thích với EVM / solidity khác nhau. Chúng tôi nhận ra cộng đồng xây dựng mạnh mẽ trên Arbitrum, Polygon, OP Stack, Base, Arbitrum, Avalanche, Polkadot, Solana, Filecoin & Cosmos chia sẻ một tầm nhìn và giá trị tương tự. Morpheus chỉ có thể có ngày hôm nay nhờ vào các công cụ được xây dựng bởi các nhà phát triển trên nhiều chuỗi này.

## Bảo mật Dữ liệu Người dùng
Để tránh rò rỉ dữ liệu cá nhân khi gửi gợi ý đến mạng lưới ngang hàng Morpheus của Cung cấp Tính toán, phần mềm nên cố gắng tận dụng Các Ứng dụng Mã hóa Toàn diện (FHE) của các Mô hình Ngôn ngữ Lớn khi chúng được phát hành. Cũng với sự ra đời của việc tăng tốc phần cứng cho FHE vào năm 2024/2025, dự kiến chi phí cho việc tính toán này sẽ đạt đến sự cân bằng với việc xử lý văn bản thuần túy.
- Ví dụ LLM https://huggingface.co/blog/encrypted-llm 
- Ví dụ EVM https://www.fhenix.io/

## Mạch lưới Xuất hiện & Giai đoạn Bootstrapping 90 Ngày
Mạng lưới Morpheus bắt đầu với phiên bản cài đặt cục bộ 0.0.1, sau đó tiếp tục với các hợp đồng thông minh token MOR và sau đó là phần mềm nút đầy đủ.

Các hợp đồng thông minh tính toán phần thưởng MOR nên được thử nghiệm một cách cẩn thận thông qua một mạng thử trước trước khi triển khai lên mạng chính.

Ngoài ra sẽ có một thời gian trễ 90 ngày một lần (được biết đến là giai đoạn bootstrapping) giữa khi mainnet bắt đầu tính toán phần thưởng và khi các token MOR đó là có thể nhận được / gửi được bởi người dùng. Giai đoạn bootstrapping này sẽ đảm bảo có đủ token MOR sẵn sàng lưu thông để thực hiện các chức năng tiện ích của mạng lưới.

Để khởi động AMM, 4% của token MOR dành cho quỹ bảo vệ (51.444 MOR vào ngày thứ 90) sẽ được sử dụng cho mục đích này.

Những bước này sẽ cung cấp rằng 1.286.111 MOR có thể nhận được vào đầu ngày thứ 91 trên mainnet và do đó tránh được sự khan hiếm về token như đã xảy ra với việc ra mắt của Zcash, khi chỉ có một vài token đầu tiên có sẵn từ ngày khai thác đầu tiên. Vấn đề này mất thị trường tuần để đạt được sự cân bằng và thiết lập phát hiện giá hợp lý. Morpheus tránh được vấn đề này với giai đoạn boot strapping 90 ngày này, do đó chuẩn bị nguồn cung token với đủ số lượng token để thực hiện các chức năng tiện ích của nó và thiết lập phát hiện giá hợp lý.

Khi các token MOR có thể nhận được và gửi được, sau đó Mạng lưới Morpheus có thể kích hoạt các giao dịch MOR để thanh toán cho các cuộc gọi API, các agent tùy chỉnh và xác nhận phần thưởng của các thành viên trong mạng lưới.

## Kết luận
Chúng tôi đang gần đến một khoảnh khắc quan trọng trong lịch sử. Với Morpheus, mọi người sẽ có một trí tuệ nhân tạo cá nhân mạnh mẽ có khả năng suy nghĩ cùng họ và thực hiện các hành động để làm lợi cho họ. Giống như máy tính cá nhân và công cụ tìm kiếm đã tạo điều kiện cho người cá nhân, chúng ta có cơ hội tương tự với trí tuệ nhân tạo cá nhân ngày nay. Giao thức Smart Agent kết hợp đúng mức độ các khả năng với LLMs, Agent, và Web3. Morpheus mở rộng những khả năng này vào một mạng lưới công cộng có khả năng tăng tốc sự phân phối và sử dụng rộng rãi của Smart Agents.

Chúng tôi tin rằng việc căn chỉnh kinh tế của động lực cuối cùng là cách chúng tôi đảm bảo được những kết quả tốt nhất từ sự xuất hiện của AGI. Hãy giúp chúng tôi đảm bảo một tương lai mã nguồn mở, không cần phép và tự do cho tất cả mọi người.

_______________________
## Bối cảnh về Đề xuất:

Tôi đã nhận được một email từ một nhà phát triển tên Morpheus vào ngày 2 tháng 9 năm 2023 với đề xuất trên.

_______________________
David,

Dưới đây là một đề xuất để triển khai "Morpheus - Một Mạng Lưới để Tăng Cường Các Tác Nhân Thông Minh".

Bản tài liệu mô tả về kinh tế token, công nghệ cơ bản và phương tiện tính toán chứng minh để công bằng thưởng cho cộng đồng, các nhà lập trình, các nhà cung cấp vốn và cung cấp dịch vụ tính toán bằng token.

Tài liệu này được cung cấp miễn phí cho cộng đồng Tác nhân Thông minh và có sẵn trong miền công cộng.

Hãy thả mình.

Morpheus

--------------------------------------------------------------------
