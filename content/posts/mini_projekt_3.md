---
date: 2025-10-28T18:35:02+02:00
# description: ""
featured_image: "/267859_ZPC_2025/images/scan_scan.jpg"
lastmod: 2025-10-28
showTableOfContents: false
# tags: ["",]
title: "Mini projekt 4 - Scan 5L PET fľaše"
type: "post"
---
<!--more-->

Štvrtý projekt bol zameraný na technológiu 3D skenovania, konkrétne pomocou laserového optického skenera. Mojou úlohou bolo naskenovať 5-litrovú PET fľašu.
{{< myimg src="/267859_ZPC_2025/images/scan_pred.jpg" width="500" alt="" >}}
Najskôr som pripravil povrch skenovaného objektu – keďže PET fľaša je priehľadná, musel som ju nastriekať matným skenovacím sprejom. Následne som na jej povrch náhodne rozmiestnil nalepovacie body. Takto pripravený objekt som umiestnil na skenovací otočný stolík spolu s kalibračnými kockami s bodmi.
<div style="display:flex; align-items:center; gap:8px;">
  <img src="/267859_ZPC_2025/images/scan_strek.jpg" width="300">
  <img src="/267859_ZPC_2025/images/scan_scan.jpg" width="300">
</div>
Skener som nastavil na režim pre veľké priehľadné objekty (hustota bodov 0,5 mm, expozícia 5 ms) a začal som so skenovaním. Najskôr som nasnímal referenčné body a potom samotnú fľašu z dvoch strán. Po dokončení som tieto dva skeny zlepil a odstránil pozadie.
Naskenovaný model som ďalej spracovával v softvéri GOM Inspect, kde som najprv zredukoval polygónovú sieť, následne ju vyhladil a odstránil diery.
<iframe
  src="https://vutbr1486.autodesk360.com/g/shares/SH28cd1QT2badd0ea72bb1e3bbc364d1223b?mode=embed"
  width="100%"
  height="300"
  allowfullscreen
  style="display:inline-block; border:none;"
  frameborder="0">
</iframe>

Potom som pokračoval meraním maximálnych rozmerov. Meranie som realizoval pomocou Touch pointov a rovín. Začal som od spodnej časti fľaše, kde som si určil prvú referenčnú rovinu, a na základe jej normály som pomocou touch pointu našiel najvzdialenejší bod na vrchnáku fľaše. Podobne som postupoval aj pri stranách fľaše – tam to bolo jednoduchšie, pretože som poznal kolmú rovinu. Nakoniec som zmeral aj obsah povrchu modelu.

| ![](/267859_ZPC_2025/images/scan_vysledky.png) | ![](/267859_ZPC_2025/images/scan_roviny.png) |
|--------------------------------------------------------|------------------------------------------------------------|
<a href="/267859_ZPC_2025/images/ZPC_flasa.ginspect" download>Stiahnuť GOM súbor</a>