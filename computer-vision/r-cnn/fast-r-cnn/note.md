# Note Fast-R-CNN

## Tư tưởng

Fast R-CNN xây dựng trên R-CNN nhưng nó có cải thiện về tốc độ huấn luyện và tốc độ test. Không những thế nó còn có những cải thiện về độ chính xác
- Về tốc độ:
    - 9x (thời gian huẩn luyện), 213x (thời gian test) so với R-CNN.
    - 3x (thời gian huấn luyện), 10x (thời gian test) so với SPPnet.
    - 0.3s/image (trừ thời gian chạy object proposal).
- Về độ chính xác:
    - Có mAP cao hơn trên tập PASCAL VOC 2012 (66% so với 62% của R-CNN).

## Thách thức

Có 2 thách thức lớn đặt ra trong bài toán detect.

- Số lượng lớn các proposals cần phải xử lý.
- Phải điều chỉnh vị trí các propsosals để có vị trí chính xác.

## Nhược điểm của R-CNN và SPPnet

1. Việc huấn luyện là một chuỗi tuần tự các giai đoạn.
2. Việc training tốt thời gian và không gian bộ nhớ.
3. Tốc độ detect đối tượng chậm.

Đối với **R-CNN** nó chậm vì nó không chia sẻ việc tính toán. Với mỗi proposal được đưa vào mạng thì nó lại phải tính toán ra các đặc trưng mặc dù các proposal có các phần giao nhau. Nên khi có số lượng lớn các proposal thì tốc độ detect càng chậm.

Đối với **SPPNet** đã thấy nhược điểm của R-CNN nên đã cải thiện bằng cách là sẽ tính feature map cho toàn bộ bức ảnh thay vì từng proposal như R-CNN.