---
date: 2025-10-25T18:35:02+02:00
# description: ""
featured_image: "/267859_ZPC_2025/images/tisk_final.jpg"
lastmod: 2025-10-25
showTableOfContents: false
# tags: ["",]
title: "Mini projekt 3 - WHACK-A-MOLE"
type: "post"
---
<!--more-->

Zadaním tretieho projektu bolo vytvoriť jednoduchý 3D tlačený mechanizmus, na ktorý bolo možné použiť maximálne 100 g filamentu. Rozhodol som sa pre vačkový mechanizmus, pretože mi pripomínal hru Whack-A-Mole. Preto som ho navrhol v štýle tejto hry.

Ako vždy som začal tvorbou 3D modelu v softvéri Autodesk Inventor, kde som vytvoril jednoduchú zostavu pozostávajúcu z rámu, trojdielneho hriadeľa s vačkami, kľuky a „krtkov“.

<iframe
  src="https://vutbr1486.autodesk360.com/g/shares/SH28cd1QT2badd0ea72b43c5db9e59588a82?mode=embed"
  width="100%"
  height="300"
  allowfullscreen
  style="display:inline-block; border:none;"
  frameborder="0">
</iframe>
{{< myimg src="/267859_ZPC_2025/images/tisk_slice.png" width="500" alt="" >}}
Následne som model naslicoval v Prusa slicery, nastavil výšku vrstvy 0,2mm, použil organické podpory, potom som na 3D tlačiarni vytlačil prototyp, na ktorom som otestoval jednotlivé uloženia. Prototyp však nespĺňal moje požiadavky, pretože „krtkovia“ vypadávali z vodiacich dier (pozri obrázok).
| ![](/267859_ZPC_2025/images/tisk_prototyp.jpg) | ![](/267859_ZPC_2025/images/tisk_rozpad.jpg) |
|--------------------------------------------------------|------------------------------------------------------------|

{{< myimg src="/267859_ZPC_2025/images/tisk_problem.jpg" width="500" alt="" >}}
Po upravách tolerancií a pridaní dizajnových prvkov, pomocou softweru Blender. Model krtka som stiahol z internetu, upravil pre potreby tlače, bohužial popri tom som ho upravil na nespoznanie. Hŕby na rám som pridal jednoducho pomocou metódy Sculpt. Modely som následne naslicoval ako predtým a vytlačil.
| {{< myimg src="/267859_ZPC_2025/images/tisk_hrba.png" width="300" alt="" >}} | ![](/267859_ZPC_2025/images/tisk_krtek.png) |
|--------------------------------------------------------|------------------------------------------------------------|
Tu je finálny produkt.
{{< myimg src="/267859_ZPC_2025/images/tisk_final.jpg" width="500" alt="" >}}
<video src="/267859_ZPC_2025/images/tisk_vid.mp4" class="table-media" style="border-radius:20px;" width="500" autoplay loop muted playsinline></video>