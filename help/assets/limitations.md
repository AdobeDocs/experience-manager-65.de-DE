---
title: Grenzwerte für Dynamic Media
description: Erfahren Sie mehr über die Best Practices und durchgesetzten Grenzwerte beim Erstellen eines Bildsets oder eines Rotationssets oder beim Hochladen einer PDF. Erfahren Sie auch mehr über nicht unterstützte Webbrowser- und Betriebssystemkombinationen für Dynamic Media.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/Dynamic-Media-Classic
geptopics: SG_SCENESEVENONDEMAND_PK/categories/ecatalogs
feature: Dynamic Media Classic,Asset Management,Image Sets,Spin Sets,eCatalog
role: User
exl-id: e4d4059e-ac0b-42e7-910c-001310796574
source-git-commit: cd4342740a09cb5315c640768bf24af6c7788a48
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 79%

---

# Grenzwerte für Dynamic Media

In den folgenden Abschnitten werden Grenzwerte für Dynamic Media beschrieben.

Dieses Thema enthält die folgenden Abschnitte:

* [Best Practices und durchgesetzte Grenzwerte in Dynamic Media für Asset-Typen](#best-practice-enforced-limits)
* [Nicht unterstützte Webbrowser- und Betriebssystemkombinationen für Dynamic Media](#unsupported-browser-os)

## Best Practices und durchgesetzte Grenzwerte in Dynamic Media für Asset-Typen {#best-practice-enforced-limits}

Wenn Sie ein Rotationsset oder Bildset erstellen oder PDFs zur Seitenextrahierung hochladen, empfiehlt Adobe die folgenden Best Practices und setzt die folgenden Grenzwerte durch:

| Asset – Art des Grenzwerts | Best Practice | Grenzwert | Änderung des Grenzwerts am 31. Dezember 2022 |
| --- | --- | --- | --- |
| **Bild**: Anzahl der smarten Zuschnitte pro Bild | 5 | 100 | Nicht zutreffend |
| **Alle Sets**: Anzahl doppelter Assets pro Set | Keine Duplikate | 20 | Nicht zutreffend |
| **Alle Sets**: Maximale Anzahl von Assets pro Set | 5–10 Bilder pro Set | 1000 | Nicht zutreffend |
| **Rotationsset**: Maximale Anzahl von Zeilen/Spalten pro 2D-Set | 12–18 Bilder pro Set | 1000 | Nicht zutreffend |
| **PDF**: Maximale Seitenzahl für eine PDF, die für die Extraktion berücksichtigt werden sollen |  | 5000 (für neue Uploads) | 100 (für alle PDFs) |

<!-- See also [Dynamic Media limitations](/help/assets/limitations.md). -->

## Nicht unterstützte Webbrowser- und Betriebssystemkombinationen für Dynamic Media {#unsupported-browser-os}

Dynamic Media unterstützt die folgenden Webbrowser- und Betriebssystemkombinationen nicht.

* Internet Explorer 11 + Windows 7
* Internet Explorer 11 + Windows 8.1
* Internet Explorer 11 + Windows Phone 8.1
* Internet Explorer 11 + Windows Phone 8.1 Update
* Safari 6 + iOS 6.0.1
* Safari 7 + iOS 7.1
* Safari 7 + OS X 10.9 Mavericks
* Safari 8 + iOS 8.4
* Safari 8 + OS X 10.10 Yosemite

## Ende der Unterstützung für TLS 1.0 und 1.1 {#tls}

<!-- CQDOC-19433 -->

Ab dem 30. September 2022 stellt Adobe Dynamic Media die Unterstützung für Folgendes ein:

* TLS (Transport Layer Security) 1.0 und 1.1
* Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_RSA_WITH_AES_256_GCM_SHA384`
   * `TLS_RSA_WITH_AES_256_CBC_SHA256`
   * `TLS_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_AES_128_GCM_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
   * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`

