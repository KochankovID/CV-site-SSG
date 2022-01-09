---
filename: cv-math.md
title: Математические понятия
Summary: >
  Математические понятия, используемые в методах компьютерного зрения.
date: 2022-01-09T08:32:25+03:00
билеты: ["Математика", ]
draft: false
weight: 12
cover:
  image: https://miro.medium.com/max/1400/1*L76A5gL6176UbMgn7q4Ybg.jpeg
author: "Ilya Kochankov"
---

## Математические понятия, используемые в методах компьютерного зрения

### Математическое ожидание

\\( M(x) = \sum_{i=1}^nx_ip_i \\), где \\( p_i \\) - вероятность

### Дисперсия

\\( D(x) = \frac{\sum_{i=1}^n(x_i-\overline{x})^2}{n-1} \\), где \\( \overline{x} \\) - среднее значение в выборке

\\( D(x) = M(x^2) - M(x)^2 \\)

### Среднеквадратическое отклонение (стандартное отклонение)

\\( S = \sqrt{D} \\), где \\( D \\) - дисперсия

### Ковариация

\\( cov\left(X,\ Y\right)=M\left(\left(X-M\left(X\right)\right)\left(Y-M\left(Y\right)\right)\right) \\)

\\( cov\left(X,\ Y\right)=M\left(XY\right)-M\left(X\right)M\left(Y\right) \\)

### Корреляция

\\( \rho \left(X,\ Y\right)={{cov\left(X,\ Y\right)}\over {\sqrt{D\left(X\right)D\left(Y\right)}}} \\)

### Медиана

{{< figure src="https://statanaliz.info/wp-content/uploads/2015/01/mediana_01.png"
class="figure__image" >}}

### Скалярное произведение

\\( \vec{x}\vec{y} = x_1* y_1 + x_2 * y_2 + ... + x_n * y_n \\)
