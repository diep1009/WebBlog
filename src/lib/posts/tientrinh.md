---
title: "Tiến trình & Luồng"
date: "2025-04-29"
categories:
  - "Hệ thống phân tán"
  - "Đa luồng & đa tiến trình"
coverImage: "/images/2.jpg"
excerpt: Phân tích hiệu năng máy tính cá nhân, nghiên cứu bài toán sử dụng đa luồng, tiến trình và hệ thống phân tán.
---

## 1. Kiểm tra CPU, GPU, RAM – Hiệu năng máy tính
## CPU (Bộ vi xử lí)
![alt text](</images/Ảnh chụp Màn hình 2025-05-06 lúc 17.50.32.png>)

---

### ⚙️ Hiệu năng máy bạn:

* **CPU sử dụng:** \~12% → máy hoạt động nhẹ, còn rất nhiều tài nguyên trống.
* **Số tiến trình:** 418
* **Số luồng:** 4.027
* **Ứng dụng nặng:**  `WindowServer`, `Messenger`, `Google Chrome`, `Zalo`.

### 💡 Ý nghĩa:

* **Messenger** và **Chrome** dùng rất nhiều **luồng** → xử lý nhiều tác vụ song song như tin nhắn, hình ảnh, giao diện.
* **Chrome, Zalo, Messenger** sử dụng cả **đa tiến trình** (Helper, Renderer, GPU) → giúp ổn định và tách biệt khi có lỗi.
* Máy bạn có khả năng xử lý đa luồng rất tốt, phù hợp học và làm về **đa luồng/đa tiến trình**.

## GPU (Card đồ hoạ)
![alt text](</images/Ảnh chụp Màn hình 2025-05-06 lúc 18.14.24.png>)
* **GPU:** Apple M1 (tích hợp)
* **Tổng số lõi:** 7
* **Loại:** GPU tích hợp (không phải card rời)
* **Độ phân giải màn hình:** 2560 x 1600 Retina
* **Hỗ trợ Metal GPUFamily Apple 7:** cho phép tăng tốc đồ hoạ tốt hơn trong game, đồ hoạ 3D, AI, video.

---

💡 **Ý nghĩa:**
GPU M1 tuy là tích hợp nhưng rất mạnh, đủ sức xử lý đồ họa 2D/3D nhẹ, làm video, học lập trình, chạy AI cơ bản. Nếu làm đồ hoạ hoặc AI nâng cao thì cần GPU rời (ví dụ NVIDIA).



---
## RAM (Bộ nhớ)
![alt text](</images/Ảnh chụp Màn hình 2025-05-06 lúc 18.12.58.png>)
* **RAM vật lý:** 8 GB
* **Đã sử dụng:** \~7.16 GB
* **Tệp hoán đổi (swap):** 794 MB (khi RAM đầy, macOS dùng ổ cứng làm bộ nhớ tạm)
* **Ứng dụng nặng RAM nhất:** Messenger (1.24 GB, 417 luồng), Microsoft Word (\~1.7 GB), Google Chrome (nhiều tab)

---

💡 **Ý nghĩa:**

* Máy bạn đang **gần đầy RAM**, dẫn đến **swap tăng**, có thể làm máy chậm nếu mở thêm ứng dụng nặng.
* Messenger và Chrome đang chiếm nhiều luồng và RAM => bạn có thể **đóng bớt tab hoặc app nền** để tối ưu hiệu năng.
---

## 2. 12 bài toán phổ biến sử dụng đa luồng/đa tiến trình

| STT | Bài toán                              | Sử dụng đa luồng/tiến trình                         |
|-----|----------------------------------------|----------------------------------------------------|
| 1   | Web server (Nginx, Apache)            | Mỗi request = 1 thread/process                     |
| 2   | Trình duyệt (Chrome, Firefox)         | Tab = process, render = thread                    |
| 3   | Trình biên dịch (Compiler)            | Biên dịch file song song                          |
| 4   | Game                                  | Thread riêng cho hình ảnh, âm thanh, input        |
| 5   | Chat app real-time                    | Thread riêng gửi/nhận tin nhắn                    |
| 6   | Xử lý ảnh                              | Chia ảnh thành block, xử lý song song             |
| 7   | Web scraping                          | Mỗi website = 1 thread/process                    |
| 8   | Hệ điều hành                          | Process quản lý app, thread xử lý I/O             |
| 9   | Huấn luyện AI                         | Đa tiến trình xử lý dữ liệu song song             |
| 10  | Giả lập (VM, emulator)                | VM = process, có nhiều thread phụ                 |
| 11  | Cơ sở dữ liệu                         | Connection pool = thread                          |
| 12  | Streaming video                       | Thread decode, buffer, render riêng               |

---

## 3. Khi nào dùng Thread? Khi nào dùng Process?

![text](/images/tientrinh.jpg)

---

## 4. ChatGPT và hệ thống phân tán khi huấn luyện

### Mô hình ChatGPT sử dụng hệ thống phân tán:
- **Data Parallelism:** chia batch dữ liệu cho nhiều GPU cùng xử lý
- **Model Parallelism:** chia tầng của mạng neural ra nhiều GPU
- **Pipeline Parallelism:** phân tầng thành các giai đoạn để xử lý nối tiếp

### Công nghệ sử dụng:
- GPU cluster tốc độ cao (NVIDIA A100, TPU)
- Kết nối InfiniBand
- Framework: PyTorch Distributed, DeepSpeed, Megatron-LM

### Tài liệu tham khảo:
- [EleutherAI GPT-3 Training Blog](https://blog.eleuther.ai/gpt3-model-training/)
- [NVIDIA - Scaling Deep Learning](https://developer.nvidia.com/blog/large-language-model-training-gpu-clusters/)
- [Microsoft DeepSpeed](https://www.microsoft.com/en-us/research/project/deepspeed/)

---

✅ **Kết luận:** Hiểu rõ luồng, tiến trình và kiến trúc hệ thống phân tán giúp chúng ta thiết kế các ứng dụng hiệu quả hơn, tận dụng tối đa tài nguyên máy tính.

 