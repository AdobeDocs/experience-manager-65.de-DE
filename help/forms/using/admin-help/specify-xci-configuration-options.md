---
title: XCI-Konfigurationsoptionen angeben
seo-title: XCI-Konfigurationsoptionen angeben
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
seo-description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 8fbff12a-4923-4151-a758-c1e44dee9160
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 100%

---

# XCI-Konfigurationsoptionen angeben {#specify-xci-configuration-options}

Output ermöglicht Ihnen, eine benutzerdefinierte XCI-Datei anzugeben, die für die Wiedergabe verwendet werden soll. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) Standardmäßig setzt Output einige der in der XCI-Datei festgelegten Optionen außer Kraft:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die das Außerkraftsetzen der oben angegebenen Optionen verhindern. In diesem Fall verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option ausgewählt ist, verwendet Output seine Standardwerte für die packets-, creator-, producer- und compressObjectStream-Einstellungen. Bei deaktivierter Option verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf Speichern.
