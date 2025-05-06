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

**Thiết bị:** MacBook sử dụng chip **Apple M1**

- **CPU:** Apple M1 – 8 lõi (4 hiệu năng cao + 4 tiết kiệm điện)
- **GPU:** Apple 7 lõi GPU tích hợp
- **RAM:** 8GB Unified Memory

**Đánh giá hiệu năng:**

- CPU kiến trúc ARM mạnh mẽ, tiết kiệm điện, hiệu quả cao cho cả đơn luồng và đa luồng.
- GPU tích hợp phù hợp đồ họa cơ bản, xử lý AI nhẹ, lập trình, chỉnh sửa ảnh/video cơ bản.
- RAM 8GB đáp ứng tốt cho nhu cầu học tập, lập trình, xử lý tài liệu, nhưng không lý tưởng cho các tác vụ nặng như xử lý video 4K hay chạy nhiều máy ảo.

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

[text](../../../static/images/IMG_7722.HEIC)

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

 