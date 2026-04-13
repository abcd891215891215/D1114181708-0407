# 📘 Adaptive Filter Algorithm

## 📌 Overview
本文件說明一種自適應濾波演算法，其核心為透過誤差修正來更新權重向量。

---

## 🧠 Initialization（初始化）

> 初始權重設定為零向量：

$$
\hat{h}(0) = zeros(p)
$$

- `p`：濾波器階數（filter order）

---

## 🔄 Computation（計算流程）

對於每個時間步：

$$
n = 0, 1, 2, ...
$$

---

### 1️⃣ 輸入向量建構

$$
x(n) = [x(n), x(n-1), ..., x(n-p+1)]^T
$$

- 為一個向量
- 包含目前與過去的輸入資料

---

### 2️⃣ 誤差計算

$$
e(n) = d(n) - \hat{h}^H(n)x(n)
$$

- `d(n)`：期望輸出
- `\hat{h}^H(n)`：共軛轉置

---

### 3️⃣ 權重更新

$$
\hat{h}(n+1) = \hat{h}(n) + \frac{\mu e^*(n)x(n)}{x^H(n)x(n)}
$$

- `\mu`：學習率（learning rate）
- `e^*(n)`：誤差共軛

---

## 📊 特性分析

| 項目 | 說明 |
|------|------|
| 收斂速度 | 快 |
| 穩定性 | 與 μ 有關 |
| 應用 | 訊號處理 |

---

## ⚙️ 參數說明

- **μ**：學習率  
- **p**：濾波器階數  
- **x(n)**：輸入訊號  
- **d(n)**：期望訊號  

---

## 🧾 使用情境

- 噪音消除（Noise Cancellation）
- 回聲消除（Echo Cancellation）
- 通道估測（Channel Estimation）

---

## 💻 範例（Pseudo Code）

```python
h = zeros(p)

for n in range(N):
    x_vec = [x[n], x[n-1], ..., x[n-p+1]]
    y = dot(conj(h), x_vec)
    e = d[n] - y
    h = h + (mu * conj(e) * x_vec) / dot(conj(x_vec), x_vec)
