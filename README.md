# 📡 Adaptive Filtering Project — NLMS Algorithm

![NLMS 示意圖](./nlms.png)

> 圖：Normalized Least Mean Squares（NLMS）演算法流程

---

## 🧠 Project Overview

本專案展示 **Normalized LMS（NLMS）自適應濾波演算法**，常用於：

* 雜訊消除（Noise Cancellation）
* 回聲消除（Echo Cancellation）
* 系統識別（System Identification）

---

## ✨ Features

* 📈 快速收斂
* ⚖️ 自動正規化（Normalization）
* 🔧 適用於即時訊號處理

---

## 🧮 Mathematical Formulation

### 🔰 Initialization

$$
\hat{h}(0) = \mathbf{0}
$$

---

### 🔁 Iterative Update

#### 📌 Input Vector

$$
x(n) = [x(n), x(n-1), \dots, x(n-p+1)]^T
$$

#### 📌 Error Signal

$$
e(n) = d(n) - \hat{h}^H(n)x(n)
$$

#### 📌 Weight Update Rule

$$
\hat{h}(n+1) = \hat{h}(n) + \frac{\mu e^*(n)x(n)}{x^H(n)x(n)}
$$

---

## 🔄 Algorithm Flow

```mermaid
flowchart TD
    A[Start] --> B[Initialize h(0)=0]
    B --> C[Receive input x(n)]
    C --> D[Compute y(n)]
    D --> E[Calculate error e(n)]
    E --> F[Update h(n)]
    F --> C
```

---

## 📊 Parameter Table

| 參數           | 說明             |
| ------------ | -------------- |
| $\mu$        | 學習率（Step Size） |
| $x(n)$       | 輸入訊號向量         |
| $d(n)$       | 期望訊號           |
| $e(n)$       | 誤差訊號           |
| $\hat{h}(n)$ | 濾波器權重          |

---

## 🖼️ Illustration (附圖文字)

![Adaptive Filter Diagram](./nlms.png)

> 圖：自適應濾波器架構與誤差回饋機制

---

## 💻 Example Code (Python)

```python
import numpy as np

def nlms(x, d, mu=0.1, p=4):
    h = np.zeros(p)
    N = len(x)

    for n in range(p, N):
        x_vec = x[n:n-p:-1]
        y = np.dot(h, x_vec)
        e = d[n] - y
        norm = np.dot(x_vec, x_vec) + 1e-8
        h = h + (mu * e * x_vec) / norm

    return h
```

---

## 📌 Key Concepts

* **Normalization**：避免輸入訊號能量影響收斂
* **Adaptive Learning**：即時更新權重
* **Stability**：比 LMS 更穩定

---

## 🚀 How to Use

1. Clone repository

```bash
git clone https://github.com/your-username/your-repo.git
```

2. 執行程式

```bash
python nlms.py
```

---

## 🔗 References

* Adaptive Signal Processing
* Digital Signal Processing (DSP)

---

## 👨‍💻 Author

Your Name

---

## 📌 License

MIT License
