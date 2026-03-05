# Voice-Command-Recognition-Correlation 🎙️

## 🇬🇧 English

A Python-based Digital Signal Processing project that recognizes Vietnamese
voice commands ("tắt" / "mở") using cross-correlation and autocorrelation
techniques, developed as a Digital Signal Processing course project at
Ho Chi Minh City University of Science.

### Overview

The system records a live voice command via microphone, normalizes the audio
signal, then computes cross-correlation against two pre-recorded reference
signals. The command with the highest correlation peak is identified as the
recognized voice command. Demonstrated successfully recognizing the command
"tắt" (off) vs "mở" (on).

### Signal Processing Pipeline
| Step | Description |
|---|---|
| 1 | Load reference audio files: `1.wav` ("tắt") and `2.wav` ("mở") via librosa |
| 2 | Record live test command (5 seconds, 44100 Hz) via sounddevice |
| 3 | Normalize all signals to [−1.0, 1.0] (divide by max absolute value) |
| 4 | Compute cross-correlation between test signal and each reference |
| 5 | Find peak of absolute cross-correlation for each reference |
| 6 | Identify command as whichever reference yields the highest peak |
| 7 | Plot waveforms of all three signals (reference × 2 + test) |

### Key Theory
| Concept | Description |
|---|---|
| Autocorrelation | Measures self-similarity of a signal across time lags — detects periodic patterns |
| Cross-Correlation | Measures similarity between two signals as a function of time lag — used for command matching |
| Normalization | Eliminates amplitude/volume differences between recordings |
| Peak Detection | Highest correlation peak determines the best-matching reference command |

### Example Result
- Test input: spoken command "tắt"
- Cross-correlation peak for "tắt" > peak for "mở"
- Recognized command: **"tắt" (off)** ✅

### Improvements over Original MATLAB Code
- Ported from MATLAB to **Python** (NumPy, librosa, sounddevice, Matplotlib)
- Replaced MATLAB's `xcorr` with **`np.correlate`** for cross-correlation
- Added **signal normalization** before correlation, improving accuracy
  regardless of recording volume differences
- Live microphone recording via **sounddevice** instead of MATLAB's built-in recorder
- Added **waveform visualization** with matplotlib subplots

### Technologies
- Python — NumPy, librosa, sounddevice, wavio, Matplotlib
- Concepts: Autocorrelation, Cross-Correlation, Audio Normalization,
  Peak Detection, Voice Command Recognition

### How to Run
```bash
pip install numpy librosa sounddevice wavio matplotlib
python project1.py
```
> Make sure a microphone is connected. Reference files `1.wav` (tắt)
> and `2.wav` (mở) must be in the same directory.

---

## 🇻🇳 Tiếng Việt

Đồ án Xử lý Tín hiệu Số sử dụng Python để nhận diện lệnh giọng nói tiếng
Việt ("tắt" / "mở") bằng kỹ thuật tương quan chéo và tự tương quan, thực
hiện trong khuôn khổ môn Xử lý Tín hiệu Số tại Trường Đại học Khoa học
Tự nhiên TP.HCM.

### Tổng quan

Hệ thống ghi âm lệnh giọng nói trực tiếp qua microphone, chuẩn hóa tín
hiệu, sau đó tính tương quan chéo với hai tín hiệu tham chiếu đã ghi
sẵn. Lệnh có đỉnh tương quan chéo cao nhất được xác định là lệnh được
nhận diện. Kết quả thử nghiệm nhận diện thành công lệnh "tắt" và "mở".

### Chuỗi xử lý tín hiệu
| Bước | Mô tả |
|---|---|
| 1 | Tải file tham chiếu: `1.wav` ("tắt") và `2.wav` ("mở") bằng librosa |
| 2 | Ghi âm lệnh thử nghiệm (5 giây, 44100 Hz) bằng sounddevice |
| 3 | Chuẩn hóa tất cả tín hiệu về khoảng [−1.0, 1.0] |
| 4 | Tính tương quan chéo giữa tín hiệu thử và từng tín hiệu tham chiếu |
| 5 | Tìm đỉnh của tương quan chéo tuyệt đối cho từng tham chiếu |
| 6 | Lệnh được nhận diện là tham chiếu có đỉnh tương quan cao nhất |
| 7 | Vẽ dạng sóng của cả ba tín hiệu (2 tham chiếu + 1 thử nghiệm) |

### Lý thuyết chính
| Khái niệm | Mô tả |
|---|---|
| Tự tương quan | Đo mức tương quan của tín hiệu với chính nó theo độ trễ thời gian — phát hiện tính chu kỳ |
| Tương quan chéo | Đo mức tương đồng giữa hai tín hiệu theo độ trễ thời gian — dùng để so khớp lệnh |
| Chuẩn hóa | Loại bỏ sự khác biệt biên độ/âm lượng giữa các lần ghi âm |
| Phát hiện đỉnh | Đỉnh tương quan cao nhất xác định lệnh tham chiếu phù hợp nhất |

### Kết quả ví dụ
- Đầu vào: giọng nói lệnh "tắt"
- Đỉnh tương quan chéo của "tắt" > đỉnh của "mở"
- Lệnh nhận diện: **"tắt"** ✅

### Cải tiến so với code MATLAB gốc
- Chuyển từ MATLAB sang **Python** (NumPy, librosa, sounddevice, Matplotlib)
- Thay hàm `xcorr` của MATLAB bằng **`np.correlate`** của NumPy
- Thêm **chuẩn hóa tín hiệu** trước khi tính tương quan, cải thiện độ chính xác
  khi âm lượng ghi âm khác nhau
- Ghi âm trực tiếp qua microphone bằng **sounddevice**
- Thêm **trực quan hóa dạng sóng** bằng matplotlib

### Công nghệ
- Python — NumPy, librosa, sounddevice, wavio, Matplotlib
- Khái niệm: Tự tương quan, Tương quan chéo, Chuẩn hóa âm thanh,
  Phát hiện đỉnh, Nhận diện lệnh giọng nói

### Cách chạy
```bash
pip install numpy librosa sounddevice wavio matplotlib
python project1.py
```
> Cần kết nối microphone. File tham chiếu `1.wav` (tắt) và `2.wav` (mở)
> phải nằm cùng thư mục với file code.
