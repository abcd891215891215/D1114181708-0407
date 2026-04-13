# 📘 Adaptive Filter Formula

---

## 📌 Initialization

> 初始設定：

$$
\hat{h}(0) = zeros(p)
$$

---

## 🔄 Computation

對於：

- $n = 0$
- $n = 1$
- $n = 2$
- ...

---

### 1️⃣ Input Vector

$$
x(n) = [x(n), x(n-1), ..., x(n-p+1)]^T
$$

- 向量形式
- 包含歷史資料

---

### 2️⃣ Error Function

$$
e(n) = d(n) - \hat{h}^H(n)x(n)
$$

> 誤差為期望值與估計值的差

---

### 3️⃣ Update Rule

$$
\hat{h}(n+1) = \hat{h}(n) + \frac{\mu e^*(n)x(n)}{x^H(n)x(n)}
$$

---

## 📊 Summary Table

| 項目 | 公式 |
|------|------|
| 初始化 | $\hat{h}(0) = zeros(p)$ |
| 輸入向量 | $x(n)$ |
| 誤差 | $e(n)$ |
| 更新 | $\hat{h}(n+1)$ |

---

## 💡 Notes

- 使用 **共軛轉置（Hermitian）**
- 使用 *誤差修正*
- 使用 `learning rate (μ)`

---

## 🧾 Code Block（公式集合）

```text
ĥ(0) = zeros(p)

x(n) = [x(n), x(n-1), ..., x(n-p+1)]^T

e(n) = d(n) - ĥ^H(n)x(n)

ĥ(n+1) = ĥ(n) + (μ e*(n)x(n)) / (x^H(n)x(n))
