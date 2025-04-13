# Hướng dẫn làm bài steg-fhss-embed

### tải lab

Vào `/home/student/labtainer/labtainer-student` và gõ lệnh sau trên terminal:
``` bash
imodule https://github.com/TuTran21195/steg-labs/raw/refs/heads/main/steg-fhss-embed.tar
```
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

python3 step5_extract_message.py stego_audio.wav modulated_signal.wav hopping_pattern.txt

python3 step6_evaluate.py original_audio.wav stego_audio.wav
```
ở trong file code của bước 3 có phần: `modulated_signal *= 0.0005  # giảm mức ảnh hưởng lên âm thanh`
Xin chú ý: hệ số này nhỏ thế nào là đủ?
các bạn cần thử với nhiều hệ số khác nhau (0.1 0.01 0.001 0.0005 0.0001 ...)
nếu như các bạn vẫn giải được ra tin nhắn ở bước 5, đồng thời hệ số MSE sẽ có ý nghĩa như sau:

- **MSE: 0 – 10**: rất tốt, gần như không nghe ra sự khác biệt (checkwork mse)
    
- **MSE: 10 – 100**: vẫn ổn, tai thường không phân biệt được (checkwork mse)
    
- **MSE > 100**: có thể nghe thấy sự khác biệt tùy mức độ
    
- **MSE > 1000**: có thể nghe rõ ràng tiếng méo


