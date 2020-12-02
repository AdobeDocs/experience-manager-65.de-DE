---
title: XCI-Konfigurationsoptionen angeben
seo-title: XCI-Konfigurationsoptionen angeben
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
seo-description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---


# XCI-Konfigurationsoptionen angeben {#specifying-xci-configuration-options}

Forms ermöglicht Ihnen, eine benutzerdefinierte XCI-Datei anzugeben, die für die Wiedergabe verwendet werden soll. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Standardmäßig setzt Forms einige der in der XCI-Datei festgelegten Optionen außer Kraft:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die das Außerkraftsetzen der oben angegebenen Optionen verhindern. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option ausgewählt ist, verwendet Forms seine Standardwerte für die packets-, creator-, producer- und compressObjectStream-Einstellungen. Bei deaktivierter Option verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf Speichern.

