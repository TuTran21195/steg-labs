# Hướng dẫn thực hành các bài lab
## Hướng dẫn làm bài steg-fhss-embed

> Note update 22/04/25: T vừa update lại checkwork mse, nếu trước đó ae đã imodule thì giờ ae cần imodule lại để update lại bài lab. (Nội dung bài lab vẫn vậy, chỉ cần mn dùng 6 file step*.py như hướng dẫn là checkwork thành công)
>
> File đáp án: https://ptiteduvn-my.sharepoint.com/:w:/g/personal/mydtt_b21at134_stu_ptit_edu_vn/EYJut07wNqNPhBebSCrMITIBytpmh9vNw-KbuqKB-mpMKw?e=JphlBp

### tải lab

Vào `/home/student/labtainer/labtainer-student` và gõ lệnh sau trên terminal:
``` bash
imodule https://github.com/TuTran21195/steg-labs/raw/refs/heads/main/steg-fhss-embed/imodule.tar
```
> Các lỗi mn báo lại cho t qua ib zalo nhé. Một số lỗi có thể có như: lỗi ngay từ bước imodule, đã imodule và chạy labtainer -r xong nhưng bị treo máy,...

### khởi tạo lab trên labtainer:
```
labtainer -r steg-fhss-embed
```

### Các bước thực hiện bài lab

```
python3 step1_text_to_bits.py message.txt

-----------python3 step2_generate_hopping_pattern.py <chiều_dài_dãy_nhảy_tần>------------
python3 step2_generate_hopping_pattern.py 96

----python3 step3_modulate_fsk.py <file_bits> <file_hopping_pattern>----
python3 step3_modulate_fsk.py bits.txt hopping_pattern.txt

python3 step4_embed_message.py original_audio.wav modulated_signal.wav

python3 step5_extract_message.py stego_audio.wav hopping_pattern.txt

python3 step6_evaluate.py original_audio.wav stego_audio.wav
```
ở trong file code của bước 3 có phần: `modulated_signal *= 0.0005  # giảm mức ảnh hưởng lên âm thanh`
Xin chú ý: hệ số này nhỏ thế nào là đủ?
các bạn cần thử với nhiều hệ số khác nhau (0.1 0.01 0.001 0.0005 0.0001 ...)
nếu như các bạn vẫn giải được ra tin nhắn ở bước 5, đồng thời hệ số MSE cần phải đủ nhỏ, với thang đo MSE sẽ có ý nghĩa như sau:

- **MSE: 0 – 10**: rất tốt, gần như không nghe ra sự khác biệt (pass checkwork mse)
    
- **MSE: 10 – 100**: vẫn ổn, tai thường không phân biệt được (pass checkwork mse)
    
- **MSE > 100**: có thể nghe thấy sự khác biệt tùy mức độ
    
- **MSE > 1000**: có thể nghe rõ ràng tiếng méo

## Hướng dẫn làm bài steg-fhss-extract
### tải lab
Vào `/home/student/labtainer/labtainer-student` và gõ lệnh sau trên terminal:
```sh
imodule https://github.com/TuTran21195/steg-labs/raw/refs/heads/main/steg-fhss-extract/imodule.tar
```
> Các lỗi mn báo lại cho t qua ib zalo nhé. Một số lỗi có thể có như: lỗi ngay từ bước imodule, đã imodule và chạy labtainer -r xong nhưng bị treo máy,...

### khởi tạo lab trên labtainer:
```
labtainer -r steg-fhss-extract
```

### Các bước thực hiện bài lab
Toàn bộ câu lệnh cần thực hiện như sau:

```sh
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

Mở rộng: Ở trong file `step0_add_noise.py` có phần như sau:
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
Các bạn cần lần lượt thử nghiệm với các loại nhiễu khác nhau nhé, đầu tiên là chỉ có ` 00_Thêm nhiễu trắng` sau đó các bạn bỏ comment câu lệnh dưới dòng `01_nhiễu trắng + thêm nhiễu xung nhẹ ` đi.

Với thí nghiệm tiếp theo thì các bạn comment lại dòng lệnh dưới dòng `01_nhiễu trắng + thêm nhiễu xung nhẹ ` vừa rồi để đổi sang uncomment loại nhiễu tiếp theo `02_nhiễu trắng + thêm nhiễu xung trung bình`.  Tương tự với dòng còn lại.

Việc này sẽ giúp các bạn hiểu được nhiễu sẽ tác động thế nào đến phương pháp giấu tin này (Sau khi thử nghiệm bạn sẽ thấy phương pháp này chống chịu với nhiễu khá tốt, nếu như kết hợp thêm với các loại ECC thì sẽ giảm được BER)

