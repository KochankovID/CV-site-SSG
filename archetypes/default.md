---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
билеты: ["Билет {{ add (len .Site.Sections) 1}}", ]
draft: false
author: "Ilya Kochankov"
---

