---
filename: halftones-binarization.md
title: Бинаризация изображений
Summary: >
  Процесс бинаризации – это перевод цветного (или в градациях серого) изображения в двухцветное черно-белое.
  Главным параметром такого преобразования является порог t – значение, с которым сравнивается яркость каждого пикселя.
date: 2022-01-07T11:32:14+03:00
билеты: ["Билет 3", ]
draft: false
weight: 6
cover:
  image: https://images.deepai.org/glossary-terms/4103891acc534977b2872112ce21fef7/binarization.jpg
author: "Ilya Kochankov"
---

## Что такое бинаризация?

Процесс **бинаризации** – это перевод цветного (или в градациях серого) изображения в двухцветное черно-белое. 
Главным параметром такого преобразования является порог t – значение, с которым сравнивается яркость каждого пикселя.

По результатам сравнения, пикселю присваивается значение 0 или 1. Существуют различные методы бинаризации, 
которые можно условно разделить на две группы – глобальные и локальные. 
В первом случае величина порога остается неизменной в течение всего процесса бинаризации. 
Во втором изображение разбивается на области, в каждой из которых вычисляется локальный порог.

> Главная цель бинаризации, это радикальное уменьшение количества информации, с которой приходится работать. 
Просто говоря, удачная бинаризация сильно упрощает последующую работу с изображением. 

> С другой стороны, неудачи в процессе бинаризации могут привести к искажениям, таким, как разрывы в линиях, потеря 
значащих деталей, нарушение целостности объектов, появление шума и непредсказуемое искажение символов из-за 
неоднородностей фона. Различные методы бинаризации имеют свои слабые места: так, например, метод Оцу может 
приводить к утрате мелких деталей и „слипанию“ близлежащих символов, а метод Ниблэка грешит появлением ложных 
объектов в случае неоднородностей фона с низкой контрастностью. Отсюда следует, что каждый метод должен быть 
применен в своей области.

---

## Методы бинаризации
### Глобальный фиксированный порог

Глобальный фиксированный порог легко понять. Всё изображение преобразуется в двоичную форму с единым порогом.

{{< figure src="/images/uploads/global-threshold.png"
class="figure__image" >}}

> Но каким образом подобрать оптимальное пороговое значение? Для этого необходимо анализировать гистограмму изображения.

### Локальный адаптивный порог

**Локальный адаптивный порог** предназначен для определения порога бинаризации в местоположении пикселя в соответствии с
распределением значений пикселя в блоке соседства пикселя. 

Преимущество этого заключается в том, что порог бинаризации 
в каждом местоположении пикселя не фиксируется, а определяется распределением соседних пикселей вокруг него. 

Порог бинаризации области изображения с более высокой яркостью обычно выше, и порог бинаризации области изображения с более 
низкой яркостью будет соответственно меньше.

{{< figure src="/images/uploads/binarization-methods.png"
class="figure__image" >}}

Обычно используемые локальные адаптивные пороги: 
1. среднее значение блока локальной окрестности 
2. взвешенная по Гауссу сумма блока локальной окрестности

### Метод Отсу

**Метод Оцу** использует гистограмму изображения для расчета порога. Напомню, что гистограмма — это набор бинов, 
каждый из которых характеризует количество попаданий в него элементов выборки. В нашем случае выборка — это пиксели 
различной яркости, которая может принимать целые значения от 0 до 255.

{{< figure src="https://habrastorage.org/r/w1560/storage/habraeffect/68/db/68db25aea01ce0142d24b7ea8a57f1e9.jpg"
class="figure__image" >}}

Гистограмма изображения:

{{< figure src="https://habrastorage.org/r/w1560/storage/habraeffect/65/f2/65f283989118f93550841238a085de58.png"
class="figure__image" >}}

Из гистограммы человек легко видит, что имеется два четко разделяющихся класса. Суть метода Оцу заключается в том, 
чтобы выставить порог между классами таким образом, чтобы каждый их них был как можно более «плотным». 
Если выражаться математическим языком, то это сводится к минимизации внутриклассовой дисперсии, которая определяется 
как взвешенная сумма дисперсий двух классов:

{{< figure src="https://habrastorage.org/r/w1560/storage/habraeffect/4d/c1/4dc1d46d299a331ab04ef28d9712c500.png"
class="figure__image" >}}

Здесь w1 и w2 — вероятности первого и второго классов соответственно.

В своей работе Оцу показывает, что минимизация внутриклассовой дисперсии эквивалента максимизации межклассовой 
дисперсии, которая равна:

{{< figure src="https://habrastorage.org/r/w1560/storage/habraeffect/e6/f6/e6f6cad7bd13b5f3396742b5d809993a.png"
class="figure__image" >}}

В этой формуле \\( a_1 \\) и \\( a_2 \\) — средние арифметические значения для каждого из классов.

Особенность этой формулы заключается в том, что 

\\(  w_1(t + 1), w_2(t + 1), a_1(t + 1), a_2(t + 1)  \\)

легко выражаются через предыдущие значения 

\\( w_1(t), w_2(t), a_1(t), a_2(t) \\), где \\( t \\) — текущий порог

Эта особенность позволила разработать быстрый алгоритм:

1. Вычисляем гистограмму (один проход через массив пикселей). Дальше нужна только гистограмма; 
проходов по всему изображению больше не требуется.
2. Начиная с порога t = 1, проходим через всю гистограмму, на каждом шаге пересчитывая дисперсию \\( σ_b(t) \\). 
Если на каком-то из шагов дисперсия оказалась больше максимума, то обновляем дисперсию и T = t.
3. Искомый порог равен T.
