# Sử dụng iptables để thiết lập tập lệnh shell để chuyển tiếp cổng

## Vai trò dự án

1. Đặt quy tắc chuyển tiếp lưu lượng truy cập iptables một cách thuận tiện
2. Khi địa chỉ phân giải tên miền thay đổi, quy tắc chuyển tiếp lưu lượng được cập nhật tự động mà không cần thay đổi thủ công (áp dụng với tên miền ddns)

## Cách sử dụng


```shell
# Nếu vps không thể truy cập raw.githubusercontent.com, bạn nên sử dụng cái này
wget --no-check-certificate -qO natcfg.sh https://www.arloor.com/sh/iptablesUtils/natcfg.sh && bash natcfg.sh
```
hoặc là

```
wget --no-check-certificate -qO natcfg.sh https://raw.githubusercontent.com/harryngne/iptablesUtils/master/natcfg.sh && bash natcfg.sh
```

Tập lệnh như sau:

```
#############################################################
# Usage: setup iptables nat rules for domian/ip             #
# Website:  http://www.arloor.com/                          #
# Author: ARLOOR <admin@arloor.com>                         #
# Github: https://github.com/arloor/iptablesUtils           #
#############################################################

Bạn sẽ làm gì (vui lòng nhập một số)? Ctrl + C thoát tập lệnh này
1) Thêm quy tắc chuyển tiếp  3) Liệt kê tất cả các quy tắc chuyển tiếp
2) Xóa quy tắc chuyển tiếp   4) Xem cấu hình iptables hiện tại
#?
```

Lúc này tùy theo nhu cầu mà nhập 1 số bất kỳ từ 1-4 rồi làm theo hướng dẫn

## Gỡ cài đặt

```shell
wget --no-check-certificate -qO uninstall.sh https://raw.githubusercontent.com/arloor/iptablesUtils/master/dnat-uninstall.sh && bash uninstall.sh
```

## Xem log

```shell
journalctl -exu dnat
```

## Sao lưu tệp cấu hình và nhập và xuất

Tệp cấu hình nằm trong

```shell
/etc/dnat/conf
```

## chuyển tiếp trojan

Một số người luôn nói rằng trojan không thể được chuyển tiếp Hầu hết những người nói điều này nói rằng cấu hình chứng chỉ là sai. Giải pháp đơn giản nhất là: khách hàng chọn không xác thực chứng chỉ. Điều phức tạp hơn là khớp chứng chỉ với tên miền của máy quá cảnh.

HarryNG chỉ nhớ một câu: khách hàng không xác minh chứng chỉ.

-----------------------------------------------------------------------------

## Đề xuất dự án mới - sử dụng nftables để thực hiện chuyển tiếp tự nhiên

Bản tiếp theo của iptables, nftables, đã được cung cấp như một công cụ sản xuất trong các hệ điều hành mới nhất của debain và centos. nftables cung cấp nhiều tính năng mới và giải quyết nhiều điểm khó khăn của iptables.

Vì vậy, một dự án mới [/arloor/nftables-nat-rust](https://github.com/arloor/nftables-nat-rust) đã được tạo. Dự án này sử dụng nftables làm triển khai chuyển tiếp tự nhiên, có những ưu điểm sau so với dự án này:

1. Hỗ trợ chuyển tiếp đoạn cổng
2. Quy tắc chuyển tiếp sử dụng các tệp cấu hình, có thể được sao lưu và nhập
3. Hiện đại hơn

Vì vậy, **rất khuyến khích** sử dụng [/arloor/nftables-nat-rust](https://github.com/arloor/nftables-nat-rust). Đừng lo lắng, dự án này vẫn có thể được sử dụng bình thường và ổn định.

PS: Dự án cũ và mới không tương thích, khi chuyển sang dự án mới, vui lòng gỡ cài đặt dự án này trước


# IptablesUtils
