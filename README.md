# ✦ Adaptive Filter ✦

---

> ### $$\hat{h}(0) = zeros(p)$$

---

> - $n = 0$
> - $n = 1$
> - $n = 2$
> - $\dots$

---

## ◆

$$x(n) = [x(n), x(n-1), ..., x(n-p+1)]^T$$

---

## ◇

$$e(n) = d(n) - \hat{h}^H(n)x(n)$$

---

## ◆◇

$$\hat{h}(n+1) = \hat{h}(n) + \frac{\mu e^*(n)x(n)}{x^H(n)x(n)}$$

---

### ▣ Matrix View

| $\hat{h}(0)$ | $zeros(p)$ |
|:-----------:|:----------:|
| $x(n)$ | $[x(n), x(n-1), ..., x(n-p+1)]^T$ |
| $e(n)$ | $d(n) - \hat{h}^H(n)x(n)$ |
| $\hat{h}(n+1)$ | $\hat{h}(n) + \frac{\mu e^*(n)x(n)}{x^H(n)x(n)}$ |

---

### ▣ Code Form

```text
ĥ(0) = zeros(p)

x(n) = [x(n), x(n-1), ..., x(n-p+1)]^T

e(n) = d(n) - ĥ^H(n)x(n)

ĥ(n+1) = ĥ(n) + (μ e*(n)x(n)) / (x^H(n)x(n))
