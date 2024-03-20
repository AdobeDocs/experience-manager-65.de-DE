---
title: Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank
description: Erfahren Sie, wie Sie einen Maximalwert für geöffnete Cursor in Oracle konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 5be26485-afe5-47ac-918c-e2fff4f394b2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 23%

---

# Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank {#oracle-database-maximum-open-cursors-threshold}

Um einen Maximalwert für geöffnete Cursor in Oracle zu konfigurieren, müssen Sie diesen Wert möglicherweise auf eine Zahl einstellen, die für Ihre Anwendung geeignet ist. Es ist offensichtlich, dass unter moderater Belastung die durchschnittlich geöffneten Cursor 2700 waren. Es wird empfohlen, mit einer Obergrenze von 3000 zu beginnen. Weitere Informationen finden Sie unter [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
