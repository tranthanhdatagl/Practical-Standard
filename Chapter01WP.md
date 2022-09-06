# CHƯƠNG 01 WP

## File core WP
* index.php: Về cơ bản, tệp chỉ mục sẽ tải và khởi tạo tất cả các tệp WordPress của bạn khi một trang được người dùng yêu cầu.
* wp-config.php: Tệp này cho WordPress biết cách kết nối với cơ sở dữ liệu của bạn. Nó cũng đặt một số cài đặt chung cho trang WordPress của mình.
* .htaccess: Một tệp cấu hình máy chủ, WordPress sử dụng nó để quản lý các liên kết cố định và chuyển hướng.

## Connect DB
* Kết nối một hàm nào đó: 
function _need_connect_database() {
    global $wpdb;
}
* Kết nối một bảng nào đó, mình cần phải gọi Prefix kèm theo tên bảng, mọi bảng và mọi CMS đều cho phép người dùng thêm Prefix vào trong bảng dữ liệu để có thể cài được nhiều trang trong một bảng dữ liệu và để bảo mật:
function _need_connect_database() {
    global $wpdb;
    $prefix = $wpdb->prefix;
    $userDatabase = $prefix. 'OtherUsersTable';
}

## Loop 
* Vòng lặp là mã PHP được WordPress sử dụng để hiển thị các bài đăng. Sử dụng The Loop, WordPress xử lý từng bài đăng được hiển thị trên trang hiện tại và định dạng nó theo cách nó khớp với các tiêu chí được chỉ định trong thẻ The Loop. Mọi mã HTML hoặc PHP trong Vòng lặp sẽ được xử lý trên mỗi bài đăng.

## WP template - tệp cần thiết
### WP template
* Theme được tạm dịch là chủ đề, đây là một thư mục tổng hợp các yếu tố tạo nên giao diện cho một website như hình ảnh, màu sắc, bố cục..Có thể hiểu nôm na, Theme là bộ mặt của trang web, giúp trang của bạn trở nên đẹp, sinh động và đồng thời cung cấp nhiều tính năng độc đáo khác. Mỗi một Theme được xem như là một giao diện mẫu đã được thiết kế sẵn và người dùng chỉ việc đưa vào website của họ.

### Tệp cần thiết
* header.php: Phần đầu của trang web sẽ bao gồm thẻ mở <html>, phần <head> và phần tiêu đề (navigation). Đường dẫn tới file CSS, dùng lệnh wp_head() để gọi stylesheet, script hay các fucntion khác và được gọi ra bởi một hàm wp_get_header() có sẵn trong WordPress.
* index.php: HIển thị trang chủ của trang web
* sidebar.php: chứa các code về sidebar ở hai cạnh bên của trang web. Các code đó có thể mặc định hoặc sẽ được xuất hiện khi kích hoạt trong phần Appearance -> Widgets
* footer.php: Phần chân của website chứa các mã liên quan tới menu footer, đóng dấu bản quyền,..Chứa thẻ đóng </body> và </html> và được gọi ra bởi hàm wp_get_footer() có sẵn của WordPress.

## the_title(), get_the_title()
| the_title() | get_the_title() | 
|---|---|
| Tìm nạp tiêu đề bài đăng mà không lặp lại hàm. | Yêu cầu echo để hiển thị tiêu đề của bài đăng. | 
| Nhận ba tham số tùy chọn, hai tham số đầu tiên là tham số tùy chọn chuỗi, ví dụ: <? Php the_title ('<h1>', '</h1>');?> Và tham số thứ ba là boolean. | Chỉ nhận một tham số tùy chọn, đó là số của bài đăng (id bài đăng) hoặc đối tượng WP_Post để lấy dữ liệu khác của bài đăng như tiêu đề của bài đăng chính. | 
| Nên sử dụng trong vòng lặp. | Hữu ích bên ngoài vòng lặp để truy xuất một bài đăng. |

## get_stylesheet_directory_uri (), get_stylesheet_directory ()
| get_stylesheet_directory_uri () | get_stylesheet_directory () | 
|---|---|
| Truy xuất URI thư mục biểu định kiểu cho chủ đề đang hoạt động | Truy xuất đường dẫn thư mục biểu định kiểu cho chủ đề đang hoạt động. | 
| Trả về một URI được định dạng đúng; nói cách khác, nó sẽ là một địa chỉ web (bắt đầu bằng http: // hoặc https: // cho SSL). | Một ví dụ đầu ra của get_stylesheet_directory () là / home / user / public_html / wp-content / themes / my_theme. Trong trường hợp một chủ đề con đang được sử dụng, đó là thư mục sẽ được trả về, không phải thư mục chủ đề mẹ. | 