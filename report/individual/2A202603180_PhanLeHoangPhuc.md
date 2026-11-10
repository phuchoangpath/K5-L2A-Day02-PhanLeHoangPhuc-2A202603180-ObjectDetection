# Báo cáo cá nhân — Ngày 2 Object Detection

Đổi tên file theo `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md`. Điền kết quả thật, xóa dòng hướng dẫn khi nộp. Xem [quy định nộp](../../SUBMISSION.md).

## 1. Thông tin học viên

- Họ tên: Phan Lê Hoàng Phúc
- MSSV: 2A202603180
- Email: phuchoang.path@gmail.com
- Lớp: C304
- Link repo bài làm: https://github.com/phuchoangpath/K5-L2A-Day02-PhanLeHoangPhuc-2A202603180-ObjectDetection
- Link Colab đã chạy: https://colab.research.google.com/drive/1dloe0NXuckXeAbSUx9RitoGvZL46HtWs?hl=vi#scrollTo=3e0508d8

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md). Tóm tắt ba ca mơ hồ đã quyết định, cách áp dụng schema và phần cần giảng viên làm rõ.

## 3. Annotation và self-QC

- Số file nhãn train: 50 ảnh
- Kết quả checker và lỗi đã xử lý: 4
- Danh sách ít nhất 10 ảnh đã rà bằng mắt: drive_002, drive_003, drive_005, drive_007, drive_010, drive_012, drive_014, drive_015, drive_019, drive_020
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: gán thêm nhãn car và đổi nhãn 
- Commit khóa nhãn ban đầu:

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP | |457 |
| FP | |292 |
| FN | |196 |
| Precision | |0.6101 |
| Recall | |0.6998 |
| F1 | |0.6519 |
| mean_iou_of_matches | |0.8351 |
| passed |false |false |

Dẫn tới `outputs/annotation_evaluation.json` trong repo. Nếu rework, ghi ảnh, lỗi đã kiểm, quyết định sửa/giữ và lý do. Không suy nguyên nhân chỉ từ FP/FN. Không có rework thì ghi rõ.

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch: Runtimes 1m22s, GPU/CPU: GPU T4, Ultralytics 8.4.208, python-3.13.16, torch-2.14.1+cu130, CUDA:0
- Các tham số thay đổi so với notebook nếu có và lý do:
- Đường dẫn best checkpoint trong phiên chạy: best checkpoint: /content/Day2-Lab/outputs/yolo26_runs/vehicle_annotation/weights/best.pt

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision |0.4090642760207564 |
| Recall |0.23393606659813174 |
| mAP50 |0.2706670034721526 |
| mAP50–95 |0.1995504032766255 |

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể. ***DO MAIL KHÔNG KẾT NỐI ĐƯỢC GPU T4 NÊN MÌNH CÓ LẤY MAIL KHÁC CHẠY TRAIN MODEL***
Trả lời bốn câu hỏi cuối notebook:

1. Lớp nào recall thấp nhất? Ảnh nào minh họa?
2. Nếu mAP50 cao nhưng mAP50–95 thấp, cần kiểm điều gì trên box?
3. Lỗi class nào có thể liên quan guideline? Dữ kiện nào hỗ trợ nhận xét?
4. Vì sao không dùng 10 ảnh eval để train? Vai trò validation của chúng trong notebook là gì?

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
|Gán nhãn |Mơ hồ car và van |Hỏi |Gán nhãn car |
|Gán nhãn |Xe mờ quá nhỏ, không thể phân biệt bằng mắt |Hỏi |Không dán nhãn |
|Gán nhãn |Xe bị khuất nhiều |Đọc guideline |Không dán nhãn |

## 7. Tự đánh giá theo rubric
| Tiêu chí | Kết quả bài làm | Điểm |
| --- | --- | ---: |
| Hoàn thành và định dạng YOLO | 50 file cùng basename, 5 cột, normalized, bốn class ID đúng | 10 |
| Đầy đủ vật thể | gán đủ xe thuộc schema, kể cả xe che/cắt khung có thể nhận diện | 20 |
| Độ bám sát và hình học box | box sát phần vật thể nhìn thấy, không lấn nền/gộp vật thể | 20 |
| Phân lớp nhất quán | phân biệt `car/truck/bus/van`, không gán vật thể ngoài scope | 15 |
| Mini guideline và quyết định mơ hồ | định nghĩa lớp, quy tắc box, ít nhất ba case có lý do | 10 |
| Gold-set annotation QC | F1 = 0.6519 và mean IoU = 0.8351 | 15 |
| Pipeline YOLO và phân tích | Colab chạy được, không dùng eval để train, có metrics/ảnh eval và nhận xét lỗi | 10 |
Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.

## 8. Công cụ AI và tài liệu tham khảo

Yolo v11x dùng để gán nhãn sau đó check kiễm tra thêm, xóa, sửa. AI agent dùng để tải và tích hợp model vào CVAT.
