---
title: Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank
description: Erfahren Sie mehr über die Konfiguration eines Maximalwerts für geöffnete Cursors in Oracle.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 5be26485-afe5-47ac-918c-e2fff4f394b2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 100%
---
# Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank {#oracle-database-maximum-open-cursors-threshold}

Um einen Maximalwert für geöffnete Cursors in Oracle zu konfigurieren, müssen Sie diesen Wert möglicherweise auf eine Zahl einstellen, die für Ihre Anwendung geeignet ist. Es ist offensichtlich, dass die durchschnittliche Anzahl geöffneter Cursors bei mittlerer Auslastung 2700 betrug. Es wird empfohlen, mit einem oberen Grenzwert von 3000 zu beginnen. Weitere Informationen finden Sie unter [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
