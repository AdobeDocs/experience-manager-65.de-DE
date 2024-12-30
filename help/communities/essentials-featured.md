---
title: Grundlagen zu vorgestellten Inhalten
description: Erfahren Sie mehr über die Grundlagen der Arbeit mit vorgestellten Inhalten, die an einer beliebigen Stelle auf der Community-Site hervorgehoben werden sollen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 70b0ad6a-c891-4588-8515-449aed206805
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 5%

---

# Grundlagen zu vorgestellten Inhalten  {#featured-content-essentials}

Auf dieser Seite finden Sie die wichtigsten Informationen zum Arbeiten mit vorgestellten Inhalten.

Im Gegensatz zum Anheften eines Posts an den Anfang eines Forums ermöglicht diese Funktion das Hervorheben von Inhalten an jeder Stelle innerhalb der Community-Site.


## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/commons/components/hbs/featuresContent</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td>
   <td> <i>default</i></td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td> /libs/social/commons/components/hbs/featuredcontent/featuredcontent.hbs<br /> /libs/social/commons/components/hbs/featuredtopic/featuredtopic.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/commons/components/hbs/featuredcontent/clientlibs/featuredcontent.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="featured.md">Vorgestellte Inhalte</a></td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

### Dateibibliotheksfunktion {#file-library-function}

Eine Community-Site-Struktur, die die [Funktion für vorgestellte Inhalte](functions.md#featured-content-function) enthält, enthält eine konfigurierte `featured content`.
