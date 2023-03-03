# CS114
# Danh sách thành viên 
| STT | Họ và tên | MSSV | Email |
|-----|-------|------|-------|
| 1 | [Nguyễn Anh Dũng](https://github.com/NguyenDung278) | 20521209 | 20521209@gm.uit.edu.vn |
| 2 | [Võ Minh Trí](https://github.com/trivm12) | 20520821 | 20520821@gm.uit.edu.vn |

# Đề tài  AGERATUM CONYZOIDES DETECTION

## Bảng mục lục:
* [1. Lý do chọn đề tài](#1)
* [2. Xu hướng phát triển](#2)
* [3. Bài toán object detection](#3)
* [4. Phương pháp giải quyết bài toán](#4)
* [5. Về dữ liệu](#5)
* [6.Mô tả về thuật toán](#6)
  * [1.Yolo annotations](#1a)
  * [2.YOLOv5](#2a)
* [7.Đánh giá kết quả, kết luận](#7)

### 1. Lý do chọn đề tài:
<a name="1"></a>

Đây là một bài toán nhận diện cây hoa cứt lợn để dùng chữa bệnh trong y học cổ truyền như mụn nhọt, viêm họng, rong huyết, đau nhức xương khớp, phong thấp, viêm xoang và nhiều bệnh viện đã sử dụng các chế phẩm của cỏ cứt lợn để điều trị viêm xoang mũi mãn tính và dị ứng.
Ngoài ra người ta còn dùng cỏ cứt lợn phối hợp với bồ kết nấu nước gội đầu cho thơm, trơn tóc, sạch gàu.
Thậm chí khi tra trên google thì đến 90% nếu như không muốn nói hầu hết đang cho hai cái tên như kể trên chỉ một loại đó là cây cứt lợn.
Do đó nhóm chúng tôi mong muốn sử dụng máy học để phân biệt loại cây này dựa trên vào hoa và lá trên cây.
Đây cũng là lý do chúng tôi làm về đề tài này.


### 2. Xu hướng phát triển:
<a name="2"></a>

Đề tài có thể phát triển tiếp để người dân phát triển tiếp nhận biết cây cứt lợn và cây cỏ dại.bài toán này có thể mở rộng thành bài toán phát hiện giữa cây cỏ dại và cây thuốc cho các trẻ em và người thiếu kinh nghiệm nhìn loại cây để có thể dùng với các mục đích tốt nhất.
Hiện nay chưa có nhiều bài báo hay nhiều nguồn trích dẫn để phân biệt cây cứt lợn so với các loại cây khác như cây cỏ dại, cây ngũ sắc.  

### 3. Bài toán object detection:
<a name="3"></a>
+ Tổng quát bài toán Object Detection:
  * Input là  một ảnh màu có một hoặc nhiều đối tượng.
  * Output là một hoặc nhiều bounding box trong bức ảnh thể hiện nhãn và vị trí của đối tượng.

+ Trong đề tài:
  * Input là một ảnh màu gồm có một hay nhiều đối tượng cây cứt lợn.
  * Output là một hoặc nhiều bounding box trong bức ảnh thể hiện nhãn và vị trí của đối tượng như cây cứt lợn.
### 4. Phương pháp giải quyết bài toán:
<a name="4"></a>
Để giải quyết bài toán Object Detection, chúng ta cần phải chọn một model để thực hiện nó. Chúng em đã sử dụng mô hình YOLOv5 để giải quyết vấn đề này. 
### 5. Về dữ liệu:
<a name="5"></a>
 Để thực hiện đề tài, chúng em đã tự xây dựng bộ dataset riêng và có những ràng buộc, thông tin cụ thể là:
- Số lượng ảnh: 1025 tấm ảnh màu. 
- Vật thể trong bức hình: Gồm 1 hay nhiều cây cứt lợn
- Độ sáng: Trời sáng, ánh sáng đủ để nhìn thấy rõ vật thể, không bị chói.
- Background: Sau vườn gồm những loại cây khác 
- Góc chụp: hướng nhìn từ trên xuống, cách vật thể khoảng 1m, không quá 2m.
- Train: 918 ảnh.
- Val: 90 ảnh.
### 6.Mô tả về thuật toán:
<a name="6"></a>
#### 1.Yolo annotations:
<a name="1a"></a>
+ Mục đích: Yolo annotations giúp thể hiện được ground truth của các vật thể trong từng bức hình trước khi đưa vào training model.
+ Công cụ sử dụng: MakeSense.AI – một website hỗ trợ gán nhãn.
+ Nội dung của file ở định dạng txt, thể hiện các thông số:
  * id-class: Số nguyên từ 0 đến số lượng class - 1. Mỗi số nguyên tương ứng với 1 lớp.
  * center-x: x center của bounding box.
  * center-y: y center của bounding box.
  * width: Chiều rộng của bounding box.
  * height: Chiều cao của bounding box.

* Các giá trị center-x, center-y, width, height đều được chuẩn hoá về khoảng giá trị [0, 1]. Mục đích của việc tạo ra các giá trị trên để giúp tỉ lệ hóa kích thước vật thể so với bức hình trước khi đưa vào model học.
#### 2.YOLOv5:
<a name="2a"></a>
  Sử dụng mô hình YOLOv5: YOLOv5 là một mô hình Object Detection thuộc họ mô hình YOLO.
  YOLOv5 là sản phẩm của tác giả Glenn Jocher - nhà nghiên cứu, giám đốc điều hành của Ultralystic. Đây là tổ chức hướng tới việc giúp cho người học AI nói chung và những người đam mê công nghệ nói riêng có thể tiếp cận với các mô hình máy học một cách đơn giản, hiệu quả và trực quan hơn.
Mô hình cũng dựa trên kiến trúc Yolo và sử dụng chiến lược tối ưu hóa thuật toán trong mạng nơ-ron tích chập, chẳng hạn như tùy chỉnh kích thước anchor box với từng loại dataset, sử dụng mosaic data augmentation (mỗi input image là sự kết hợp của 4 ảnh giúp context của ảnh phong phú hơn), CSPNet (giữ được một phần thông tin từ các layer trước, vừa giảm độ phức tạp của mô hình),..
  YOLO còn là một mô hình mạng neural tích chập (CNN) dùng cho việc phát hiện, nhận dạng, phân loại đối tượng. YOLO được tạo ra từ việc kết hợp giữa các lớp phức tạp (convolutional layers) cho phép trích xuất ra các đặc tính của ảnh và lớp kết nối (connected layers) dự đoán ra xác suất xuất hiện và tọa độ của đối tượng.
### 7.Đánh giá kết quả, kết luận:
<a name="7"></a>
* Đã chạy thực nghiệm trên colab (https://colab.research.google.com/drive/1Fk5fRhZzXY4iVVtjUoc1cQJlUIqR11O-).
* Với bộ dataset chuẩn bị và việc áp dụng  mô hình YOLOv5, chúng tôi nhận thấy kết quả dự đoán khá cao, chúng tôi đã thử những tấm ảnh lấy từ nguồn trên mạng kết quả nó dự đoán được. Tuy nhiên khi có quá nhiều cây trong tấm ảnh thì có thể nó sẽ ko dự đoán được. 
* YOLO là một thuật toán rất phức tạp và bên trong nó có rất nhiều bước xử lý tính toán không đơn giản và áp dụng nhiều thuật toán máy học. Đối với đồ án này, về cơ bản đã thực hiện được mục tiêu đề ra ban đầu là cố gắng đọc hiểu và tóm tắt thuật toán, sử dụng mô hình YOLO để training và cuối cùng là đánh giá kết quả thực nghiệm.
* Như đã trình bày, đề tài không chỉ dừng lại vào việc phát hiện và phân loại một loại cây cứt lợn, nó còn có thể phát triển thêm nữa. Trong tương lai, chúng em sẽ cố gắng tối ưu các bước xử lý dữ liệu dataset cũng như mở rộng bài toán bằng các phương pháp máy học khác.

 










