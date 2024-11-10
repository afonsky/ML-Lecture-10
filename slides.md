---
theme: seriph
addons:
  - "@twitwi/slidev-addon-ultracharger"
addonsConfig:
  ultracharger:
    inlineSvg:
      markersWorkaround: false
    disable:
      - metaFooter
      - tocFooter
NObackground: >-
  https://images.unsplash.com/photo-1511149755252-35875b273fd6?ixlib=rb-4.0.3&dl=leon-contreras-qpdfU6vehgs-unsplash.jpg&w=1920&q=80&fm=jpg&crop=entropy&cs=tinysrgb
background: /logo/ship2.jpg
highlighter: shiki
routerMode: hash
lineNumbers: false

css: unocss
title: Machine Learning
subtitle: Support Vector Machines
date: 11/11/2024
venue: HSE
author: Alexey Boldyrev
ghPrefix: https://github.com/twitwi/slidev-addon-ultracharger/blob/main/
ghSelf: https://github.com/twitwi/slidev-addon-ultracharger-demo/blob/main/
---

# <span style="font-size:28.0pt" v-html="$slidev.configs.title?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:32.0pt" v-html="$slidev.configs.subtitle?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:18.0pt" v-html="$slidev.configs.author?.replaceAll(' ', '<br/>')"></span>

<span style="font-size:18.0pt" v-html="$slidev.configs.date?.replaceAll(' ', '<br/>')"></span>

<div class="abs-tl mx-5 my-10">
  <img src="/logo/FCS_logo_full_L.svg" class="h-18">
</div>

<div class="abs-tl mx-5 my-30">
  <img src="/logo/DSBA_logo.png" class="h-28">
</div>

<div class="abs-tr mx-5 my-5">
  <img src="/logo/ICEF_logo.png" class="h-28">
</div>

<style>
  :deep(footer) { padding-bottom: 3em !important; }
</style>


---
src: ./slides/0_attendance.md
---

---
src: ./slides/1_overview.md
---

---
src: ./slides/2_hyperplane.md
---

---
src: ./slides/3_MMC.md
---

---
src: ./slides/4_perceptron.md
---

---
src: ./slides/5_SVC.md
---

---
src: ./slides/6_SVM.md
---

---
src: ./slides/0_end.md
---