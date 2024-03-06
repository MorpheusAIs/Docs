# Bản Công Bố Kỹ Thuật Màu Vàng Morpheus

Tài liệu này mô tả chi tiết kỹ thuật của node đầy đủ Morpheus, Hợp Đồng Thông Minh Morpheus và các chứng minh liên quan.
Được trình bày như đã viết trong bản trắng do các nhà phát triển ẩn danh Morpheus, Trinity & Neo đóng góp. Liên kết đến bản trắng ở đây: https://github.com/SmartAgentProtocol/SmartAgents/blob/main/MorpheusWP.md 

## Phiên bản Cục bộ 0.0.5 của Morpheus đã được phát hành tại:

**Phiên bản Morpheus 0.0.5 cho Mac**
- Tải xuống từ Google Drive: https://drive.google.com/file/d/1x-wR4HWjKqT_g6VRjrWPXu3rVm9ukOc9/view?usp=sharing
- Mã băm SHA 256 cho việc xác thực: 9092d543023fb95086cf4a7039d42cbcbbdf5283d670c4de6396b3d89e57b064
- Phiên bản: Morpheus-0.0.5-x64.dmg

**Phiên bản Morpheus 0.0.5 cho Linux Debian**
- Tải xuống: https://drive.google.com/file/d/1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB/view?usp=sharing
- Hướng dẫn: Để cài đặt, chạy lệnh này:
sudo dpkg -i /đường/dẫn/tới/morpheus.deb
LƯU Ý: Trong lệnh trên, thay thế "/đường/dẫn/tới/morpheus.deb" bằng đường dẫn của bạn tới tệp morpheus_0.0.5_amd64.deb.

- Mã SHA cho Xác minh:
b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5
Phiên bản: morpheus_0.0.5_amd64.deb
---------

Tương tác đầu tiên với Morpheus vào ngày 22 tháng 10 năm 2023.
![FirstInteractionWithMorpheus20231022](https://github.com/MorpheusAIs/Morpheus/assets/1563345/35509f3a-4346-4f58-bb60-f7881fd10f7e)

## Hợp Đồng Thông Minh Morpheus
Các hành động trên chuỗi cần được xác thực bởi hợp đồng thông minh Morpheus.

1. Fork của Hợp Đồng Thông Minh Lợi Nhuận N2 Được Triển Khai Lại Trên Arbitrum
- A) Khóa ETH qua Thorchain, quyên góp lợi nhuận cho Lập trình viên + Nhà cung cấp Tính toán.
- B) Tính tỷ lệ pro-rata của ETH được quyên góp
2. Sự Hủy Diệt Vĩnh Viễn Của MOR Có Thể Chứng Minh:
- A) Địa chỉ đốt hoặc chức năng đốt cho token MOR.
3. Hợp Đồng Mẫu ERC20 Để Phát Hành MOR
- A) Tạo MOR hàng ngày cho Vốn + Cộng đồng tỷ lệ pro-rata với lợi nhuận ETH được quyên góp.
- B) Tạo MOR hàng ngày cho Lập trình viên + Nhà cung cấp Tính toán tỷ lệ pro-rata với MOR được đốt qua phí.
4. Chứng Minh Morpheus - Chứng minh Sự Riêng tư, Mã Nguồn Mở, & An toàn
- A) Xuất bản danh sách các Đại lý đã được kiểm toán và điểm Smart Rank của họ.
- B) Xuất bản danh sách các LLM đã được kiểm toán và điểm Smart Rank của họ.
- C) Xuất bản danh sách Hợp Đồng Thông Minh & điểm Smart Rank của họ.
- D) Xuất bản danh sách Câu hỏi & điểm Smart Rank của chúng.
5. Quỹ Bảo Vệ
- A) Phân phối MOR & ETH trong trường hợp hack, lỗi, bug, hoặc các cuộc tấn công khác gây thiệt hại.
- B) Bộ sưu tập các tình huống được định trước cho việc thanh toán. Chính sách cho việc fork / lùi lại trong trường h ợp cực đoan.
- C) Các nhà phát triển chịu trách nhiệm xác định trường hợp tấn công & biện pháp khắc phục.
- D) Quỹ cho bug bounty / hacker mũ trắng.
- E) Quỹ bảo vệ khỏi các diễn viên Quốc gia.

## Sơ Đồ Hợp Đồng Thông Minh Morpheus
Các sơ đồ cùng mô tả về việc tạo và đốt MOR.
Mô tả về các hợp đồng thông minh được yêu cầu.
Các sơ đồ chi tiết về sự phân phối ETH.

### Phân Phối Phần Thưởng Hợp Đồng Thông Minh MOR Morpheus
![new-buckets](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/1YP_.png)

### Ví dụ về Phân Phối Token MOR của Ngày 1 và Ngày 2.
![Untitled spreadsheet - Google Sheets 2023-10-15 13-28-08](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/YP2-4__1.png)

## Ví dụ Tính Toán Phân Phối cho Địa Chỉ 0x123 Người Đóng Góp ETH

## Bước Một
![Diagram1ofETHDontator](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/fead528c-d628-449e-a3a3-2f53904f4a3d)

### Bước Hai
![ETHGivenDiagram2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/915020e8-d342-48bc-85ee-367de0325680)

### Bước Ba
![Diagram3ForETHGiven](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a3f455af-56de-4c6b-9688-5b9e91673e5a)

## Ví dụ Tính Toán Phân Phối cho Địa Chỉ 0x123 Nhà Cung Cấp Tính Toán

### Bước Một
![MORForCompute](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/YP5_.png)

### Bước Hai
![MORForCompute2](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/YP6_.png)

### Biểu Đồ Tròn Phân Phối Token MOR
![mordist](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/1709712527509-5f6297fc-2e56-4cc0-8268-71b61ced4803_1.jpg)

## Công Cụ Phát Triển và Ngăn Xếp Công Nghệ của Morpheus.
- Llama2 - LLM mã nguồn mở mạnh mẽ chạy cục bộ.
- Ollama - Gói cài đặt dễ dàng cho Llama2.
- LangChain - Công cụ phát triển để kết nối LLM với cửa hàng Vector và API.
- LangSmith Editor - Lập trình low-code để xây dựng các đại lý trên LangChain.
- Thuật Toán SmartContractRank - Lựa chọn Hợp Đồng Thông Minh cho Người Dùng Dựa Trên Ý Định
- Thuật Toán AgentRank - Lựa chọn các đại lý chuyên biệt để thực hiện hành động cho người dùng.
- Thuật Toán PromptRank - Lựa chọn câu hỏi cho người dùng dựa trên ý định / hành động dự kiến.
- Filecoin - Lưu trữ & Cung cấp Tính toán Đám mây
- Akash Network - Mạng tính toán mở cho việc chạy LLMs / đại lý.
- Ví - Shapeshift, Exodus, các lựa chọn mã nguồn mở khác.

## Sơ Đồ Node Đầy Đủ Morpheus cho Đại Lý / LLMs cho Hành Động Web3.
Kiểm toán các Đại Lý được thực hiện bởi Lập trình viên, tạo ra "Bằng Chứng Đại Lý" xác nhận rằng các chức năng được trình bày của Đại Lý là chính xác. Và tất nhiên không chứa mã độc hại.

Chỗ trống cho mô tả quy trình kiểm toán, ai có thể thực hiện kiểm toán và cách chứng nhận kết quả của họ. Cũng như các khoản thưởng trả cho người kiểm toán.

Bằng Chứng Câu Hỏi được tạo ra vào thời điểm tương tác của người dùng cho thấy ý định được biểu đạt, phù hợp với sự lựa chọn hợp đồng thông minh và giá trị giao dịch được xác nhận với người dùng.

## Sơ Đồ Người Dùng & Người Đóng Góp Morpheus
![Morpheus User   Contributor Diagram](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/8yp.jpg)

### Sơ đồ cho thấy dòng chảy UX từ lời nhắc của người dùng đến việc phê duyệt hành động Web3.
![UX flow for prompted web3 tasks and ticketing](https://raw.githubusercontent.com/putraicipiyey/fsub-6/main/9yp.jpg)

### Sơ đồ cho thấy phiên bản cài đặt cục bộ của Morpheus.
![MorpheusLocalDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a0564914-cddb-42e4-b0f4-8c2310db6a66)

### Sơ đồ cho thấy phiên bản cài đặt P2P của Morpheus.
![MorpheusP2PDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a7eeb31f-3d38-4233-a45f-e9b91ad84ba2)

### Sơ đồ cho thấy phiên bản Phi Tập Trung của Morpheus.
![MorpheusDecentralized](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/1699f2de-cc18-42e8-a05c-32b3307baa20)

## Cộng Đồng

- Đại Lý Thông Minh - Các nhà phát triển tự do xây dựng trường hợp sử dụng / đại lý cho người dùng Morpheus.
- Cộng Đồng Phát Triển Toàn Cầu - Cộng đồng phát triển, startup & người dùng đang phát triển.
- Tuyển dụng cộng đồng người giữ ETH quyên góp lợi nhuận cho nhà phát triển Morpheus, tính toán & cộng đồng.
- Nhóm Phát Triển Phân Tán - Các nhà phát triển Hợp Đồng Thông Minh để lập trình Hợp Đồng Thông Minh Morpheus.
- Dapps Morpheus - Thị trường cho các tích hợp Morpheus với Đại Lý Thông Minh của người dùng.




