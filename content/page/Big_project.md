---
title: "Semestrálny projekt"
date: 2025-09-22T12:00:00+05:30
menu:
  main:
    identifier: big_project
    name: "Semestrálny projekt"
    weight: 3
---

# Vyvažovač rotačných súčastí
<iframe
  src="https://vutbr1486.autodesk360.com/g/shares/SH28cd1QT2badd0ea72bff1d9acf0b8a7380?mode=embed"
  width="100%"
  height="300"
  allowfullscreen
  style="display:inline-block; border:none;"
  frameborder="0">
</iframe>
Dynamický stolný vyvažovač rotačných súčastí, určený najmä pre vrtule alebo kolesá RC modelov. Na základe vybrácii pri rotácii vyhodnotí miesto kde a koľko materiálu odobrať, resp. aké závažie pridať.
{{< myimg src="/267859_ZPC_2025/images/sem_schema.png" width="500" alt="" >}}
Celý systém bude fungovať tak, že hriadeľ, uložený na kĺbe a pružine, spolu s nevyváženým dielom, sa budú otáčať dostatoňe vysokýmy otáčkami, aby akcelerometer dokázal zachytiť vybrácie. Dáta z akcelerometra budú po meraní vyhodnotené Arduinom na základe budeného kmitania s jedným stupňom voľnosti.
{{< myimg src="/267859_ZPC_2025/images/sem_remen.png" width="500" alt="" >}}
Prevod točivého mementu bude zaisťovať ozubený remeň podľa shémy. Napnutie bude zaistené napinákom na pružine.