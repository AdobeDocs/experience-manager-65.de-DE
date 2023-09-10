---
title: Angeben der XCI-Konfigurationsoptionen
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7cd10389-63e6-41f2-a132-92fd9e40a9b7
source-git-commit: f0dd1ac3ab9c17a8b331f5048d84ec97dd23924f
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 21%

---

# Angeben der XCI-Konfigurationsoptionen {#specifying-xci-configuration-options}

Mit Forms können Sie eine benutzerdefinierte XCI-Datei angeben, die für die Wiedergabe verwendet werden kann. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms). Standardmäßig überschreibt Forms einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die das Außerkraftsetzen der oben aufgeführten Optionen verhindern. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in Administration Console auf **Dienste** > **Forms**.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option aktiviert ist, verwendet Forms seine Standardwerte für die Einstellungen &quot;packet&quot;, &quot;creator&quot;, &quot;manufacturer&quot;und &quot;compressObjectStream&quot;. Wenn diese Option deaktiviert ist, verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf **Speichern**.
