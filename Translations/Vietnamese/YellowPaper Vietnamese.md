# Tài liệu kỹ thuật Morpheus (Yellow Paper)

Paper này này trình bày các chi tiết kỹ thuật của Morpheus full node, Hợp đồng thông minh Morpheus và các bằng chứng liên quan.
Trình bày như được viết trong whitepaper do các nhà phát triển ẩn danh Morpheus, Trinity & Neo đóng góp. Đường dẫn đến whitepaper tại đây: https://github.com/SmartAgentProtocol/SmartAgents/blob/main/MorpheusWP.md

## Phiên bản Local 0.0.5 của Morpheus được triển khai tại:

---

**Morpheus phiên bản 0.0.5 cho Mac**

-   Tải xuống từ Google Drive: https://drive.google.com/file/d/1x-wR4HWjKqT_g6VRjrWPXu3rVm9ukOc9/view?usp=sharing
-   Mã băm SHA-256 để xác thực: 9092d543023fb95086cf4a7039d42cbcbbdf5283d670c4de6396b3d89e57b064
-   Phiên bản: Morpheus-0.0.5-x64.dmg

---

**Morpheus Version 0.0.5 for Linux Debian**

-   Tải xuống: https://drive.google.com/file/d/1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB/view?usp=sharing
-   Hướng dẫn: Để tải xuống, chạy câu lệnh này:
    sudo dpkg -i /path/to/your/morpheus.deb
    Lưu ý: Trong câu lệnh trên, thay "/path/to/your/morpheus.deb" bằng đường dẫn đến file morpheus_0.0.5_amd64.deb.
-   Mã băm SHA-256 để xác thực:
    b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5
    Phiên bản: morpheus_0.0.5_amd64.deb

---

Lần đầu tương tác với Morpheus 22 tháng 11 2023.
![FirstInteractionWithMorpheus20231022](https://github.com/MorpheusAIs/Morpheus/assets/1563345/35509f3a-4346-4f58-bb60-f7881fd10f7e)

## Hợp Đồng Thông Minh Morpheus~

Các hành động trong chuỗi cần được xác thực bởi Hợp Đồng Thông Minh Morpheus.

1. Phân nhánh của Hợp Đồng Thông Minh lợi nhuận N2 được triển khai lại trên Arbitrum

-   A) Khoá ETH thông qua Thorchain, tặng lợi nhuận cho Những người viết mã + Những nhà cung cấp điện toán.
-   B) Tính toán tỷ lệ ETH được đóng góp

2. Minh chứng vĩnh viễn về sự phá huỷ của MOR:

-   A) Địa chỉ đốt hoặc hàm đốt cho đồng MOR.

3. ERC20 Template Contract For Issuing MOR

-   A) Đúc token MOR hằng ngày cho Người cấp vốn + cộng đồng tỷ lệ thuận với lợi nhuận ETH được đóng góp.
-   B) Đúc token MOR hàng ngày cho Người lập trình + Nhà cung cấp điện toán tỷ lệ thuận với lượng MOR được đốt thông qua phí.

4. Bằng chứng về Morpheus - Thể hiện tính riêng tư, mã nguồn mở và an toàn

-   A) Công bố danh sách các Agent đã được kiểm toán và điểm Smart Rank (Xếp hạng thông minh) của chúng.
-   B) Công bố danh sách các LLM đã được kiểm toán và điểm Smart Rank của chúng.
-   C) Công bố danh sách các Hợp đồng thông minh và điểm Smart Rank của chúng.
-   D) Công bố danh sách các Prompt (yêu cầu) và điểm Smart Rank của chúng.

5. Quỹ bảo vệ

-   A) Phân phối MOR và ETH trong trường hợp bị hack, lỗi, bug hoặc các trường hợp tấn công khác gây thiệt hại.
-   B) Bộ kịch bản được xác định trước để chi trả. Chính sách cho việc fork / rollback trong các trường hợp cực xấu.
-   C) Những nhà phát triển chịu trách nhiệm xác định các trường hợp tấn công và cách khắc phục.
-   D) Quỹ thưởng khi phát hiện lỗi / tin tặc mũ trắng.
-   E) Quỹ bảo vệ khỏi những thế lực Nhà nước (Nation State actors).

## Các biểu đồ Hợp đồng thông minh Morpheus

Các biểu đồ cùng mô tả về việc đúc và đốt MOR.
Mô tả về các hợp đồng thông minh cần thiết.
Biểu đồ chi tiết về việc phân phối ETH.

### Phân phối Thưởng Hợp đồng thông minh Morpheus MOR

![new-buckets](https://github.com/SmartAgentProtocol/SmartAgents/assets/76454555/cd57bae7-2a56-4a55-bf3e-1f810f3fba9c)

### Ví dụ về Phân phối Token MOR của Ngày 1 và Ngày 2.

![Untitled spreadsheet - Google Sheets 2023-10-15 13-28-08](https://github.com/MorpheusAIs/Morpheus/assets/76454555/6ff7869d-bbd6-46b5-8673-6a59b75906e1)

## Tính toán Ví dụ về Phân phối cho Người đóng góp ETH Địa chỉ ví 0x123

### Bước Một

![Diagram1ofETHDontator](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/fead528c-d628-449e-a3a3-2f53904f4a3d)

### Bước Hai

![ETHGivenDiagram2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/915020e8-d342-48bc-85ee-367de0325680)

### Bước Ba

![Diagram3ForETHGiven](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a3f455af-56de-4c6b-9688-5b9e91673e5a)

## Tính toán Ví dụ về Phân phối cho Nhà cung cấp điện toán Địa chỉ ví 0x123

### Bước Một

![MORForCompute](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/bef69c69-0420-441f-97f0-7e8195844f57)

### Bước Hai

![MORForCompute2](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a6f30da5-5441-4f0a-be80-c5798f5920cd)

### Biểu đồ Hình tròn Phân phối Token MOR

![mordist](https://github.com/MorpheusAIs/Morpheus/assets/76454555/4157efe7-6abf-404a-87f9-a8dc76cd4799)

## Công cụ phát triển và Morpheus Tech Stack.

-   Llama2 - LLM mã nguồn mở mạnh mẽ, có thể chạy cục bộ.
-   Ollama - Công cụ đóng gói giúp cài đặt Llama2 dễ dàng.
-   LangChain - Công cụ dành cho nhà phát triển để kết nối LLM với các kho lưu trữ Vector và API.
-   LangSmith Editor - Công cụ low-code để xây dựng các Agent trên LangChain.
-   Thuật toán SmartContractRank - Xếp hạng Hợp đồng thông minh dựa trên ý định của người dùng.
-   Thuật toán AgentRank - Xếp hạng các Agent chuyên biệt để thực hiện hành động cho người dùng.
-   PromptRank Algorithm - Thuật toán PromptRank: Xếp hạng các prompt cho người dùng dựa trên ý định / hành động dự kiến.
-   Filecoin - Cung cấp lưu trữ và điện toán đám mây.
-   Akash Network - Mạng điện toán mở để chạy LLM / agent.
-   Ví - Shapeshift, Exodus và các lựa chọn mã nguồn mở khác.

## Biểu đồ Full Node Morpheus cho Agent / LLM Thực hiện Hành động trên Web3.

Bản kiểm toán của các Agent được thực hiện bởi các Lập trình viên, tạo ra "Bằng chứng Agent" xác minh chức năng được nêu của Agent là chính xác và không chứa mã độc hại.

Lưu ý cần bổ sung thêm mô tả về quy trình kiểm toán, ai có thể thực hiện kiểm toán, cách chứng nhận kết quả và phần thưởng dành cho những người kiểm toán.

Bằng chứng Prompt được tạo ra tại thời điểm người dùng tương tác, hiển thị ý định được thể hiện, khớp với lựa chọn hợp đồng thông minh và giá trị giao dịch được xác nhận với người dùng.

## Biểu đồ Người dùng & Người đóng góp của Morpheus

![Morpheus User   Contributor Diagram](https://github.com/MorpheusAIs/Morpheus/assets/1563345/2cff8d70-c116-472f-a431-8a82bfa22f9b)

### Biểu đồ mô tả luồng UX từ yêu cầu của người dùng đến phê duyệt hành động Web3.

![UX flow for prompted web3 tasks and ticketing](https://github.com/MorpheusAIs/Morpheus/assets/76454555/942b20fb-d67e-4a57-af2c-cd24a89690a5)

### Biểu đồ minh họa phiên bản cài đặt Morpheus cục bộ.

![MorpheusLocalDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a0564914-cddb-42e4-b0f4-8c2310db6a66)

### Biểu đồ minh họa phiên bản cài đặt Morpheus P2P.

![MorpheusP2PDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a7eeb31f-3d38-4233-a45f-e9b91ad84ba2)

### Biểu đồ minh họa phiên bản phi tập trung của Morpheus.

![MorpheusDecentralized](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/1699f2de-cc18-42e8-a05c-32b3307baa20)

## Cộng Đồng

-   Các Agency Thông minh (Smart Agency) - Các nhà phát triển độc lập xây dựng các trường hợp sử dụng và agent cho người dùng Morpheus.
-   Cộng đồng Nhà phát triển Toàn cầu - Phát triển cộng đồng gồm các nhà phát triển, startup và người dùng.
-   Nhóm cộng đồng kêu gọi những người nắm giữ ETH đóng góp lợi nhuận cho các nhà phát triển, bộ máy tính và cộng đồng Morpheus.
-   Nhóm Phát triển Phân tán - Nhóm các nhà phát triển Hợp đồng thông minh xây dựng Hợp đồng thông minh cho Morpheus.
-   Những ứng dụng phi tập trung (Dapps) Morpheus - Thị trường cung cấp các tích hợp Morpheus với Smart Agent của người dùng.
