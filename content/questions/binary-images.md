---
filename: binary-images.md
title: Бинарные изображения
Summary: >
    Бинарное изображение -  это изображение, состоящее из пикселей, которые могут иметь один из двух цветов, 
    обычно черный и белый. Каждый пиксель хранится в виде одного бита, то есть 0 или 1
date: 2022-01-06T16:35:06+03:00
билеты: ["Билет 2", ]
draft: false
weight: 2
cover:
    image: https://www.researchgate.net/publication/330363296/figure/fig3/AS:714957767331840@1547470623287/Image-thresholding-a-a-sample-image-with-road-signs-b-binary-image-after-the-colour.ppm
author: "Ilya Kochankov"
---

## Виды изображений
### Бинарное изображение
**Бинарное изображение** - это изображение, которое состоит из пикселей ровно двух цветов, обычно чёрный и белый. 
Каждый пиксель хранится в виде одного бита, то есть 0 или 1. 

Названия черно-белый, B & W, монохромный или монохроматический часто используются для 
этой концепции, но могут также обозначать любые изображения, которые имеют только один образец на пиксель, 
такие как изображения в градациях тяжести.

{{< figure src="https://media.geeksforgeeks.org/wp-content/uploads/20201203201048/Screenshot18.png"
class="figure__image" >}}

### Полутоновое изображение

**Полутоновое (серое, монохромное, Ч/Б) изображение** – это цифровое изображение, у которого
каждому пикселю соответствует одно значение интенсивности (яркости).

{{< figure src="https://p1.pxfuel.com/preview/998/558/460/female-beauty-fresh-clean.jpg"
class="figure__image" >}}

### Мультиспектральное изображение

Мультиспектральное изображение – это цифровое изображение, у которого каждому пикселю соответствует вектор значений.
(у цветных изображений размерность вектора = 3).

{{< figure src="https://ko.com.ua/files/u5101/b3woalsl.jpg"
class="figure__image" >}}

## Где применяются бинарные изображения?
Некоторые устройства ввода/вывода, такие как лазерные принтеры, fax-машины и дисплеи bile computer, 
могут обрабатывать только бинарные изображения.

Бинарные изображения в смысле подмножеств пикселов («масок») часто используются в цифровой обработке изображений. 
Для исследования формы и структуры некоторых множеств однотипных объектов бинарные растры используются в 
математической [морфологии](/questions/morphology-operations/).

Значительное практическое применение бинарные растровые изображения находят в цифровой картографии и геоинформационных системах, пространственном анализе.



## Как хранятся бинарные изображения?
Бинарное изображение может храниться в памяти как растровое изображение, упакованный луч битов. 
Изображение 640 × 480 требует 37,5 КиБ хранилища. Из-за небольшого размера файлов изображений 
fax-машина и решения по управлению документами обычно используют этот формат. Большинство бинарных изображений 
также хорошо сжимаются с помощью простых схем сжатия длины прогона.

## 
