# Bắt đầu nhanh.

Tất cả các bài hướng dẫn của Substrate đều yêu cầu build và run một node Substrate trong môi trường phát triển của bạn. Để giúp bạn cài đặt môi trường làm việc nhanh chóng, [Substrate Developer Hub](https://github.com/substrate-developer-hub/) duy trì một vài template để cho bạn sử dụng. Ví dụ, [substrate-node-template](https://github.com/substrate-developer-hub/substrate-node-template/tags/) là một snapshot chính của Substrate `node-template` bao gồm tất cả mọi thứ bạn cần để bắt đầu với một node chức năng và một tập các tính năng cốt lõi.

Giả định Quickstart này là lần đầu tiên thiết lập một môi trường phát triển và mong muốn chạy thử một node blockchain duy nhất trên máy tính local. Để giữ cho mọi thứ đơn giản, bạn sẽ kết nối tới local node đang sử dụng với một trình duyệt web và tra cứu số dư của các tài khoản mẫu được xác định trước.

## Trước khi bạn bắt đầu.
Trước khi bạn bắt đầu, hãy đảm bảo các điều sau:
- Bạn có một kết nối internet và quyền tương tác tới trên terminal trên máy tính local. 
- Bạn quen thuộc với việc phát triển phần mềm và sử dụng giao diện command-line.
- Bạn đã cài đặt trình biên dịch Rust và toolchain. 

Bạn có thể kiểm tra liệu bạn đã cài đặt Rust bằng cách chạy câu lệnh `rustup show`. Nếu bạn đã cài đặt, câu lệnh này sẽ hiện thị thông tin phiên bản của cả toolchain và trình biên dịch. Nếu Rust chưa được cài đặt, câu lệnh trên sẽ không trả về bất kì thông tin gì. Để biết thêm thông tin về cách cài đặt Rust, hãy ghé thăm [cài đặt](https://docs.substrate.io/install/) nhé.

## Build node template
1. Clone node template repository bằng cách chạy câu lệnh sau:
```bash
git clone https://github.com/substrate-developer-hub/substrate-node-template
``` 
Trong hầu hết các trường hợp, bạn có thể clone từ nhánh `main` để được phiên bản code mới nhất. Tuy nhiên, bạn có thể sử dụng câu lệnh `--branch` nếu bạn muốn làm việc với với một nhánh Substrate tương ứng với phiên bản cụ thể của Polkadot. Nhấn vào [tags](https://github.com/substrate-developer-hub/substrate-node-template/tags) để xem danh sách các nhánh tương ứng với các phiên bản Polkadot cụ thể.

2. Chuyển terminal tới thư mục 
vừa được clone.
```bash
cd substrate-node-template
```
Nếu bạn muốn lưu các thay đổi của mình và làm cho nhánh này dễ nhận biết, bạn có thể tạo một nhánh mới bằng cách chạy một câu lệnh tương tự sau:
```bash
git switch -c my-branch-v0.9.29
```
3. Biên dịch node template:
```bash
cargo build --package node-template --release
```
Bời vì số lượng các package liên quan khá nhiều, nên việc biên dịch node có thể sẽ mất tới vài phút.
## Bắt đầu với node
1. Đảm bảo rằng node của bạn đã sẵn sàng và hãy xem các thông tin về các command-line khác có sẵn bằng cách chạy câu lệnh sau: 
```bash
./target/release/node-template --help
```
Thông tin cách dùng hiện thị cùng với các command-line giúp bạn có thể sử dụng cho việc:
    - Bắt đầu node.
    - Làm việc với các tài khoản.
    - Sửa đổi các hành động của node.

2. Xem thông tin về tài khoản phát triển `Alice` được xác định trước như sau:
```bash
./target/release/node-template key inspect //Alice
```
Câu lệnh này sẽ hiện thị cách thông tin sau: 
```
Secret Key URI `//Alice` is account:
Network ID:        substrate 
Secret seed:       0xe5be9a5092b81bca64be81d212e7f2f9eba183bb7a90954f7b76361f6edb5c0a
Public key (hex):  0xd43593c715fdd31c61141abd04a99fd6822c8558854ccde39a5684e7a56da27d
Account ID:        0xd43593c715fdd31c61141abd04a99fd6822c8558854ccde39a5684e7a56da27d
Public key (SS58): 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
SS58 Address:      5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY
```
3. Trong chế độ phát triển, chain không yêu cầu bất kỳ máy tính ngang hàng nào để hoàn thiện các khối. Khi node bắt đầu, terninal sẽ hiển thị ở đầu ra về hành đồng được thực hiện. Nếu bạn thấy thông báo rằng các block đang được đề xuất và hoàn thiện, thì bạn đang có một node đang chạy.

## Kết nối tới node.
1. Tạo một file HTML đơn giản bằng Javascript và [Polkadot-Js API](https://polkadot.js.org/docs/) để tương tác với blockchain.

Ví dụ, tạo một file `index.html` sử dụng JavaScript và HTML để:
- Lấy địa chỉ tài khoản đầu vào.
- Tra cứu số dư tài khoản sử dụng onClick event.
- Hiển thị số dư cho các tài khoản ở đầu ra. 
Mẫu [index.html](https://docs.substrate.io/assets/quickstart/) này cung cấp một ví dụ đơn giản về cách sử dụng JavaScript, Polkadot-JS API, và HTML để nhận số dư của tài khoản. 

2. Sao chép và dán [code mẫu](https://github.com/substrate-developer-hub/substrate-docs/blob/main/static/assets/quickstart/index.htmlhttps://github.com/substrate-developer-hub/substrate-docs/blob/main/static/assets/quickstart/index.html) cho ứng dụng **Quick start: Get Balance** vào một tệp mới trong editor và lưu nó trên máy tính local của bạn.
3. Mở tệp `index.html` trong trình duyệt Web.
4. Sao chép và dán đỉa chỉ SS58 for tài khoản `Alice` trong trường đầu vào, sao đó click **Nhận số dư**.

## Dừng node.
1. Chuyển tới terninal đang hiện thị các hoạt động của blockchian.
2. Dừng local blockchain và hủy tất cả các trạng thái bằng cách nhấn `ctrl-c`.
## Tiếp theo
Trong Quick start này, bạn đã học về cách biên dịch và chạy một node blockchain duy nhất trên máy tính local của mình. Để học nhiều hơn về cách cách tối ưu các đặc tính đó, hãy khám phá các nguồn sau:
- [Kiến trúc]()
- [Phát triển runtime](https://docs.substrate.io/fundamentals/runtime-development/)
- [Rust cho Substrate](https://docs.substrate.io/fundamentals/rust-basics/)