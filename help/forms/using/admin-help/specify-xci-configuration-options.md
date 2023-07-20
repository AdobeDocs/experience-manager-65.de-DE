---
title: Angeben von XCI-Konfigurationsoptionen
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen angeben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 8fbff12a-4923-4151-a758-c1e44dee9160
source-git-commit: 3885cc51f7e821cdb352737336a29f9c4f0c2f41
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 7%

---

# Angeben von XCI-Konfigurationsoptionen {#specify-xci-configuration-options}

Mit Output können Sie eine benutzerdefinierte XCI-Datei angeben, die für die Wiedergabe verwendet wird. Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

Standardmäßig überschreibt Output einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die die Überschreibung für die oben aufgeführten Optionen abbrechen. In diesem Fall verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in Administration Console auf **Dienste** > Ausgabe.
1. Aktivieren oder deaktivieren Sie das Kontrollkästchen &quot;XCI-Systemstandardoptionen verwenden&quot;. Wenn diese Option aktiviert ist, verwendet Output seine Standardwerte für die Einstellungen &quot;packet&quot;, &quot;creator&quot;, &quot;manufacturer&quot;und &quot;compressObjectStream&quot;. Wenn diese Option deaktiviert ist, verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf **Speichern**.
