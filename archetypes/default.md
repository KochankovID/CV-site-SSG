---
filename: {{ .Name }}.md
title: {{ replace .Name "-" " " | title }}
Summary:
date: {{ .Date }}
билеты: ["Билет {{ add (len .Site.Sections) 1}}", ]
draft: false
weight: 1
cover:
  image:
author: "Ilya Kochankov"
---

