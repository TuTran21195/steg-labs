# Kỹ thuật giấu và tách tin trong âm thanh - Bài thực hành (Audio Steganography Techniques - Lab Exercises)

![Audio Steganography Banner](https://img.shields.io/badge/Steganography-Audio-C5BAFF)
![License](https://img.shields.io/badge/License-MIT-B0DB9C)
![Python](https://img.shields.io/badge/Python-3\.x-C4D9FF?logo=python)
[![Docs](https://img.shields.io/badge/Documents-tutran21195\.github\.io-FF8282)](https://tutran21195.github.io/steg-labs/)
[![README-en](https://img.shields.io/badge/README-en-FFE99A)](./docs-en/)


## Tổng quan

Kho lưu trữ (repository) này chứa các **bài thực hành (labs) về các kỹ thuật giấu và tách tin trong môi trường âm thanh**. Các bài tập được xây dựng dựa trên nội dung lý thuyết chi tiết từ giáo trình **["Các kỹ thuật giấu tin" - Đỗ Xuân Chợ, Học Viện Công Nghệ Bưu Chính Viễn Thông](https://github.com/TuTran21195/steg-labs/blob/main/docs/Ch%E1%BB%A3%20%C4%90X%20gi%C3%A1o%20tr%C3%ACnh%20c%C3%A1c%20k%E1%BB%B9%20thu%E1%BA%ADt%20gi%E1%BA%A5u%20tin.pdf)**.

Mục tiêu của repository này là cung cấp một môi trường thực hành thiết thực để sinh viên và những người quan tâm có thể trực tiếp áp dụng các kiến thức lý thuyết về giấu tin trong âm thanh vào việc cài đặt, kiểm tra và đánh giá các phương pháp khác nhau.

## Nội dung lý thuyết tham khảo

Các bài thực hành trong repository này tập trung chủ yếu vào **Chương 3: Giấu tin trong âm thanh** của giáo trình "Các kỹ thuật giấu tin". Chương này cung cấp các kiến thức nền tảng và chuyên sâu về:

*   **Đặc điểm của kỹ thuật giấu tin trong âm thanh**: Mô tả cách các tín hiệu âm thanh được sử dụng làm vật chứa và các thách thức đi kèm.
*   **Một số định dạng file âm thanh và công cụ xử lý âm thanh**: Giới thiệu các định dạng phổ biến như WAV, AIFF, AU, RealAudio, MIDI, QuickTime và các công cụ hỗ trợ.
*   **Phân loại phương pháp giấu tin trong âm thanh**: Tổng quan về các hướng tiếp cận chính.
*   **Các phương pháp giấu và tách tin cụ thể**: Đi sâu vào các kỹ thuật như LSB, mã hóa pha, tự đánh dấu, trải phổ (DSSS, FHSS) và tiếng vang (Echo Hiding).

## Các kỹ thuật giấu và tách tin trong âm thanh đã thực hành

Các bài lab trong repository này bao gồm việc cài đặt và kiểm thử các kỹ thuật sau:

1.  **Phương pháp LSB (Least Significant Bit) & LSB matching**:
    *   **Giấu tin**: Cài đặt quy trình giấu tin bằng cách thay thế các bit ít quan trọng nhất của các mẫu âm thanh bằng các bit của thông điệp bí mật.
    *   **Tách tin**: Thực hiện quy trình ngược lại để trích xuất thông điệp đã giấu.
    

2.  **Phương pháp mã hóa pha (Phase Encoding)**:
    *   **Giấu tin**: Cài đặt quy trình giấu tin bằng cách điều chỉnh pha của tín hiệu âm thanh sau khi biến đổi Fourier rời rạc (DFT) trên các đoạn âm thanh.
    *   **Tách tin**: Trích xuất đoạn phase đầu tiên và tái tạo thông điệp.

3.  **Phương pháp trải phổ (Spread Spectrum)**:
    *   **Giấu tin**: Cài đặt kỹ thuật giấu tin bằng cách điều chế sóng mang.
    *   **Tách tin**: Thực hiện giải trải phổ và giải điều chế để khôi phục thông tin.
    *   **Biểu diễn**: Biểu diễn các bit của tin giấu, mã giả ngẫu nhiên, mã sau điều chế.
    *   **Thử nghiệm tấn công**: Đánh giá tính bền vững của phương pháp trước các tấn công như cộng nhiễu.

4. **Phương pháp tự đánh dấu với kỹ thuật STSM**:
   *   **Giấu tin**: Cài đặt kỹ thuật giấu tin bằng cách chỉnh sửa tổng của lần lượt bộ 3 sample liên tiếp để giấu các bit của thông điệp kết hợp sử dụng mã Hamming cho chuỗi thông điệp được giấu.
   *   **Tách tin**: Tính toán tổng của lần lượt 3 sample liên tiếp và dùng mã Hamming và khôi phục thông điệp giấu.
   *   **Thử nghiệm tấn công**: Đánh giá tính bền vững của phương pháp trước các tấn công như nén âm thanh.

5.  **Phương pháp Echo (Tiếng vang)**:
    *   **Giấu tin**: Cài đặt phương pháp giấu tin bằng cách thêm tiếng vang vào tín hiệu âm thanh gốc với các độ trễ khác nhau cho bit 0 và bit 1.
    *   **Tách tin**: Tính toán giá trị Cepstrum và Autocorrelation Cepstrum để phát hiện độ trễ của tiếng vang và trích xuất thông tin giấu.

## Cấu trúc thư mục

Cấu trúc thư mục được tổ chức theo từng kỹ thuật giấu tin để dễ dàng quản lý và thực hành:

```
.
├── README.md
├── <labs-code>/
│   ├── imodule.rar/        # File imolude của bài lab
│   └── README.md/          # Một số mô tả code của bài lab
└── docs/
    └── <Các nguồn tài liệu lý thuyết>/
```

## Hướng dẫn sử dụng

> [!note]
> Toàn bộ các hướng dẫn của các bài labs đều nằm trong:  [https://tutran21195.github.io/steg-labs/](https://tutran21195.github.io/steg-labs/)
>
> Các ghi chép về lý thuyết (lecture notes) của người thực hiện lab: [TuTran Digital notes - Audio Steganography Series](https://tutran-garden.vercel.app/2025/stego/lecture_notes_colection/)

## Đóng góp

Mọi đóng góp để cải thiện các bài lab, thêm các kỹ thuật mới, hoặc tối ưu hóa mã nguồn đều được hoan nghênh! Vui lòng tạo một issue hoặc gửi pull request.

## Tác giả

[![TuTran21195](https://img.shields.io/badge/TuTran21195%20GitHub-096B68?logo=github&logoColor=fff&style=flat)](https://github.com/TuTran21195/)
