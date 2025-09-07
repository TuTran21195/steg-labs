---
title: FHSS steg-fhss-extract
layout: default
parent: Labs Trải phổ
nav_order: 2
---
1. TOC
{:toc}

## Introduce
{: .info }
FHSS - Tách tin trong âm thanh sử dụng kỹ thuật trải phổ nhảy tần

## Hướng dẫn làm bài steg-fhss-extract

### tải lab

Vào `/home/student/labtainer/labtainer-student` và gõ lệnh sau trên terminal:

```shell
imodule https://github.com/TuTran21195/steg-labs/raw/refs/heads/main/steg-fhss-extract/imodule.tar
```


### khởi tạo lab trên labtainer:
```bash
labtainer -r steg-fhss-extract
```

### Các bước thực hiện bài lab

Toàn bộ câu lệnh cần thực hiện như sau:

```shell
python3 step0_add_noise.py stego_audio.wav

python3 step1_generate_hopping_pattern.py 96 PTITsecretkey123
python3 step2_extract_bits.py noisy.wav hopping_pattern.txt
python3 step3_bits_to_message.py extracted_bits.txt

python3 step4_calculate_ber.py extracted_bits.txt original_bits.txt

=========Đánh giá file âm thanh dài hơn và chứa nhiều bit bản tin hơn===========
python3 step0_add_noise.py stego_audio2.wav

python3 step1_generate_hopping_pattern.py 96 PTITsecretkey123
python3 step2_extract_bits.py noisy.wav hopping_pattern.txt
python3 step3_bits_to_message.py extracted_bits.txt

python3 step4_calculate_ber.py extracted_bits.txt original_bits2.txt

```

Mở rộng: Ở trong file `step0_add_noise.py` có phần như sau:

```python
	# 00_Thêm nhiễu trắng (giả lập nhiễu kênh truyền)
    data_noisy = add_gaussian_noise(data, snr_db=20)

	# Hãy cố gắng test với nhiều hệ số khác nhau để thấy được khả năng chống chịu của phương pháp fhss này trước tác động của nhiễu thông qua BER tại bước cuối.
    # 01_nhiễu trắng + thêm nhiễu xung nhẹ (Giả lập môi trường nhiễu khá lớn khi có  nhiễu cùng tác động lên bản âm thanh)
    # data_noisy = add_impulse_noise(data_noisy, num_impulses=15, amplitude= 0.5)

    # 02_nhiễu trắng + thêm nhiễu xung trung bình (Giả lập môi trường nhiễu mạnh -> có thể là do bị tấn công chèn nhiễu)
    # data_noisy = add_impulse_noise(data_noisy, num_impulses=30, amplitude= 0.7)

    # 03_Nhiễu trắng + thêm Nhiễu xung cực mạnh (giả lập môi trường nhiễu cực mạnh -> tình huống rất rất tệ, gần như là bản âm thanh đã bị phá hoại)
    # data_noisy = add_impulse_noise(data_noisy, num_impulses=50, amplitude=2.5)
```

Các bạn cần lần lượt thử nghiệm với các loại nhiễu khác nhau nhé, đầu tiên là chỉ có  `00_Thêm nhiễu trắng` sau đó các bạn bỏ comment câu lệnh dưới dòng `01_nhiễu trắng + thêm nhiễu xung nhẹ`  đi.

Với thí nghiệm tiếp theo thì các bạn comment lại dòng lệnh dưới dòng `01_nhiễu trắng + thêm nhiễu xung nhẹ`  vừa rồi để đổi sang uncomment loại nhiễu tiếp theo `02_nhiễu trắng + thêm nhiễu xung trung bình`. Tương tự với dòng còn lại.

Việc này sẽ giúp các bạn hiểu được nhiễu sẽ tác động thế nào đến phương pháp giấu tin này (Sau khi thử nghiệm bạn sẽ thấy phương pháp này chống chịu với nhiễu khá tốt, nếu như kết hợp thêm với các loại ECC thì sẽ giảm được BER)