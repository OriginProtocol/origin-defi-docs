# Bảng phân tích

{% hint style="info" %}
Truy cập [analytics.ousd.com](https://analytics.ousd.com) để xem cách thức phân bổ các quỹ, dữ liệu khai thác trong lịch sử và lợi nhuận của bạn.
{% endhint %}

[Bảng điều khiển](https://analytics.ousd.com/apy) đầu tiên được xây dựng nhằm mục đích phục vụ đội ngũ kỹ thuật, nhưng chúng tôi chúng tôi quyết định công bố ra công chúng vì [nguồn mở](http://github.com/OriginProtocol) luôn là mục tiêu mà chúng tôi hướng tới. Thật không may, điều dẫn tới hiểu nhầm về tính minh bạch và không nhất thiết phải dành thời gian để giải thích mọi thứ rõ ràng.

Trước khi đi sâu vào tính toán lãi suất, điều quan trọng bạn phải nắm rõ cách thức OUSD [tạo ra lợi nhuận](https://docs.ousd.com/core-concepts/yield-generation) và [rebase](https://docs.ousd.com/core-concepts/elastic-supply). Bạn có thể đọc tất cả về điều đó trong [tài liệu](https://docs.ousd.com/), bao gồm cả [về hợp đồng thông minh bị loại trừ khỏi lợi nhuận](https://docs.ousd.com/core-concepts/elastic-supply/rebasing-and-smart-contracts).

Để tóm tắt cách tính APY, đó là tỷ lệ thay đổi lãi suất hàng năm của số dư OUSD của người dùng giữa hai thời điểm. Để hiểu điều đó, hãy xem xét kỹ các cột trong bảng APY lịch sử (theo thứ tự ngược lại).

**Tỉ lệ**

Có hai loại số dư OUSD: Rebasing (hầu hết các tài khoản) và non-rebasing(hợp đồng thông minh chưa opt in). Hợp đồng OUSD duy trì phép tính riêng biệt cho từng loại số dư bằng cách sử dụng "credit". Tỷ lệ được hiển thị ở đây là cung OUSD rebase chia cho credit được rebase, cho chúng ta tỷ giá hối đoái giữa hai loại.

**Credit**

Một số hợp đồng thông minh nắm giữ OUSD có số dư credit duy nhất vì trạng thái phục hồi của chúng đã thay đổi ở một thời điểm nào đó trong quá khứ (bằng cách chọn opt in hoặc out). Ở đây chúng tôi hiển thị tổng của tất cả các credit rebasing và non-rebasing. Khi nhân với tỷ lệ, nó cho ra sự khác biệt giữa lượng đang hỗ trợ tổng cung và lượng cung non-rebase.

**Non-rebasing**

Đây là phần nguồn cung được giữ trong các hợp đồng thông minh khác mà chưa được rebase. Khi được thêm vào (credit* tỷ lệ) sẽ bằng lượng đang hỗ trợ tổng cung. Cũng lưu ý rằng cột **%** hiển thị phần trăm OUSD non-rebase.

**Boost**

APY được "thúc đẩy" cho các tài khoản rebase nhờ vào các OUSD non-rebasing. Hãy nghĩ về tất cả các stablecoin được sử dụng làm tài sản thế chấp để tạo ra đồng OUSD non-rebasing. Những stablecoin đó vẫn tạo ra lợi nhuận thông qua các chiến lược của chúng tôi nhưng phần lợi nhuận đó được phân bổ cho các tài khoản đang rebase. Kết quả là APY đạt mức cao hơn mức bình thương được nếu không áp dụng cơ chế này. Boost là thước đo của sự khác biệt này. Nếu boost có giá trị là 100%, thì những người nắm giữ OUSD thông thường đang được hưởng gấp đôi APY so với những gì họ đáng được hưởng.

**APR/APY calculation**

Chúng tôi hiện đo lường lợi nhuận bằng cách đo lường sự thay đổi trong [credit rebase cho mỗi token](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/token/OUSD.sol#L45) giữa hai thời điểm. Có một số điểm khác cần lưu ý ở đây. Đầu tiên, chúng ta phải đưa ra giả định về việc trung bình có bao nhiêu khối Ethereum được khai thác trong một ngày. Chúng tôi sử dụng [con số cố định là 6.500](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L43), nhưng số khối thực tế mỗi ngày có thể thay đổi. Thứ hai, chúng ta cần một khoảng thời gian hợp lý để đo lường. Chúng tôi chọn  [7 ngày](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L422) - số ngày được chứng minh là khoảng thời gian tương đối nhất quán để tạo một mẫu hoàn chỉnh về các hoạt động tạo ra lợi nhuận đã xảy ra. Thứ ba, chúng tôi chuyển đổi APR thành APY bằng cách giả sử [lãi kép hàng ngày không đổi](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L449-L451). Nói cách khác, lợi nhuận liên tục được tái đầu tư vào các chiến lược tương tự. Cuối cùng, có một đáng chú ý là sử dụng tỷ lệ rebase để đo lường năng suất. Vì các sự kiện rebase hiện diễn ra không thường xuyên (và không càng thường xuyên trong trường hợp phó gas cao), APY sẽ không phản ánh thu nhập chưa được chuyển sang số dư tài khoản. Ví dụ: nếu lãi suất trong Compound tăng cao hoặc khối lượng giao dịch trong Curve 3pool tăng đột biết, điều này sẽ khiến OUSD kiếm được nhiều lãi hơn mức bình quân thường ngày. APY ghi nhận sẽ thấp hơn các khoản thực tế cho tới kho [phương pháp rebase](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/vault/VaultCore.sol#L365-L370) được gọi. Trên thực tế, bất kỳ ai bán OUSD trong thời gian đó sẽ bỏ lỡ "[đợt rebase tiếp theo](https://analytics.ousd.com/)". Tin tốt là bạn sẽ có thể theo dõi sự thay đổi trong số dư của mình trong một tuần và nó sẽ xấp xỉ bằng APY được quảng cáo.

