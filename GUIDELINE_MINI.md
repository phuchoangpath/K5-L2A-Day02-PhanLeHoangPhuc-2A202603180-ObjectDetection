# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` |Phương tiện cơ giới 4 bánh cỡ nhỏ đến trung bình, chở tối đa từ 4 đến 7 người, chủ yếu dùng cho gia đình hoặc cá nhân |Ví dụ: Sedan, Hatchback, SUV, Crossover, CUV, Minicar,.../ Xe có chiều cao thấp, thấp hơn và ngắn hơn chiều dài xe van và xe |
| `truck` |Phương tiện cơ giới chuyên dụng để chở hàng hóa, vật liệu, có thùng xe tải (thùng kín, thùng lửng, hoặc thùng mui bạt) hoặc đầu kéo tách biệt |Xe tải, xe ben, xe bồn, xe container / Có cabin lái tách rời hoặc nối liền với thùng chở hàng lớn phía sau; thiết kế ưu tiên chở hàng hơn chở người |
| `bus` | Xe chở khách công cộng cỡ lớn, sức chứa từ 16 chỗ ngồi/đứng trở lên|Xe buýt nội đô, xe khách liên tỉnh, xe giường nằm, xe buýt 2 tầng / Kích thước dài, thân xe hình hộp chữ nhật lớn, nhiều hàng cửa kính kéo dài dọc thân, có cửa lên xuống riêng cho hành khách |
| `van` |Xe khoang kín một khối, thân hình hộp, thường có cửa trượt bên hông, dùng để chở hàng nhẹ tối  1 tấn |Ford Transit, Hyundai Solati, Toyota HiAce, các dòng xe tải van chở hàng nội đô / Thấp và ngắn hơn bus, không có thùng hàng hở như truck hoặc bán tải, thân xe liền khối từ đầu tới đuôi (khác với dáng sedan/SUV của car) |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Ôm sát phần thân xe nhìn thấy được, không lấy thêm mặt đường, bầu trời hay xe bên cạnh
- Vật thể bị che khuất: Vẫn gán box bao quanh phần nhìn thấy được nếu nhận diện được lớp; nếu bị che đè lên nhau thì vẽ từng box riêng cho từng xe
- Vật thể bị cắt bởi rìa ảnh: Box chạm đúng rìa ảnh, tuyệt đối không vẽ đoán phần thân xe nằm ngoài khung hình
- Vật thể rất nhỏ/mơ hồ: Không tự đoán; nếu chỉ còn mảnh rất nhỏ không chắc lớp thì bỏ qua/không tự chọn, ghi mã nhận diện (case ID) vào mini guideline để hỏi người phụ trách.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_008` | Tool nhận diện xe 133 là car | Van | thân hình hộp dài, kiểu dáng minivan |
| `drive_016` | Xe màu cam có cabin cao vuông vức, dễ gây mơ hồ giữa van và truck| Truck | xe có cấu trúc to và  cao hơn xe van, thân dài có thùng phía sau, xe chuyên chở hàng hóa |
| `drive_028` |Xe 431 nằm lề đường, tool nhận diện là car | Truck | Xe to, có buồng lái tách rời, phía sau có thùng hàng |
