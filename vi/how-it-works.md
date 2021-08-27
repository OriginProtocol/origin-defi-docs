# Cơ chế hoạt động

#### Được hỗ trợ 100% và ổn định

Origin Dollar (OUSD) là token Erc-20 được xây dựng trên mạng Ethereum.

OUSD là tiền tệ ổn định được hỗ trợ 1:1 bởi các stablecoin khác như USDT, USDC và DAI. Do đó, 1 OUSD được duy trì gần ổn định với giá trị 1 USD.

{% hint style="success" %}
1 OUSD = 1 USD
{% endhint %}

#### Mua OUSD

Người dùng có thể chuyển đổi stablecoin hiện có của họ (hiện đang hỗ trợ USDT, USDC và DAI) sang OUSD thông qua  [Origin Dollar DApp](www.ousd.com). Sau đó, OUSD sẽ ngay lập tức tích luỹ lãi suất.

Origin DApp sẽ định tuyến các giao dịch của người dùng một cách thông minh, cung cấp cho họ mức giá chuyển đổi tốt nhất giữa OUSD và stablecoin cũng như cân nhắc trượt giá và phí gas. Điều này có nghĩa là DApp đôi khi sẽ khuyến khích người dùng mua OUSD trên thị trường thay vì mint OUSD mới từ vault. OUSD DApp sẽ chọn từ nhiều nguồn thanh khoản và sẽ đề xuất lựa chọn có tỉ giá tốt nhất.

**Bán OUSD**

Người dùng có thể chuyển đổi OUSD của họ sang các stablecoin khác bất kỳ lúc nào thông qua [Origin Dollar DApp](www.ousd.com). Origin DApp sẽ định tuyến các giao dịch của người dùng một cách thông minh, cung cấp cho họ mức giá chuyển đổi tốt nhất giữa OUSD và stablecoin cũng như cân nhắc trượt giá, phí gas và phí khi rời vault. Điều này có nghĩa là DApp thường sẽ giúp người dùng bán OUSD của họ trên AMM thay vì redeem OUSD từ kho tiền và chịu phí thoát của giao thức.

Nếu redeem trực tiếp từ kho tiền thì bạn sẽ phải trả khoản phí là 0,5%. Phí này được phân bổ như một lợi nhuận bổ sung cho những người còn lại (những người nắm giữ OUSD tại thời điểm đó). Phí này đóng vai trò như một tính năng bảo mật để khiến những kẻ tấn công khó lợi dụng tình trạng oracle bị gián đoạn, ngăn chúng đồng bộ hóa các stablecoin từ vault trong trường hợp định giá sai các tài sản cơ bản. Khoản phí nêu trên còn nhằm mục tiêu để khuyến khích những người nắm giữ dài hạn hơn là đầu cơ ngắn hạn.

Sau thực hiện lệnh quy đổi, hợp đồng thông minh sẽ xác định loại stablecoin sẽ được trả lại cho người dùng. Hiện tại, vault sẽ trả lại tiền theo tỉ lệ stablecoin trong vault ở thời điểm đó. Việc không cho người dùng có quyền lựa chọn sẽ bảo vệ được toàn bộ kho tiền trong khỏi tình huống 1 đồng stablecoin nào đó sẽ bị mất giá so với đồng Đô La.

{% hint style="warning" %}
Người dùng sẽ bị tính **0,5%** phí khi redeem từ OUSD sang stablecoins khác và sẽ không được lựa chọn stablecoin mà họ nhận được. Người dùng thường có thể tránh khoản phí này bằng cách bán OUSD cho AMM.
{% endhint %}

#### Tạo ra **lợi nhuận thụ động**

OUSD tạo ra lợi nhuận bằng cách chuyển các stablecoin được ký gửi vào hợp đồng thông minh OUSD tới các giao thức DeFi khác như Compound, Aave, Uniswap, Balancer và Curve. Các chiến lược mới sẽ tiếp tục được bổ sung trong tương lai. Tiền lãi thu được, phí giao dịch và token thưởng được tổng hợp lại và chuyển đổi thành stablecoin để tạo ra lợi tức bằng OUSD. Theo thời gian, giao thức sẽ di chuyển tài sản vào và ra khỏi các nhóm thanh khoản khác nhau để mang lại lợi nhuận tốt nhất cho người nắm giữ OUSD.

#### **Cung linh hoạt**

Lợi nhuận được tạo ra được chuyển cho người nắm giữ OUSD thông qua cơ chế cung tiền linh hoạt. OUSD liên tục điều chỉnh nguồn cung tiền để đáp ứng với lợi suất mà giao thức đã tạo ra. Điều này cho phép giá OUSD được cố định ở mức 1 đô la trong khi số dư trong ví của chủ sở hữu OUSD thay đổi theo thời gian thực, phản ánh lợi nhuận mà giao thức kiếm được.

Từ đó, Ousd trở thành 1 stablecoin dễ chi tiêu, tự động kiếm được lợi nhuận vượt trội và được nhiều người mong muốn nắm giữ hơn các loại stablecoin hiện có.

