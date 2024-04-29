---
title: Angeben der XCI-Konfigurationsoptionen
description: Erfahren Sie, wie Sie die XCI-Konfigurationsoptionen festlegen. Sie können benutzerdefinierte XCI-Dateiwerte für das adaptive Formular angeben, damit sie beim Rendern von Formularen verwendet werden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7cd10389-63e6-41f2-a132-92fd9e40a9b7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '149'
ht-degree: 100%

---

# Angeben der XCI-Konfigurationsoptionen {#specifying-xci-configuration-options}

Mit Forms können Sie eine benutzerdefinierte XCI-Datei angeben, die für das Rendern verwendet werden kann. (Siehe [Konfigurieren von Speicherorten für Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Standardmäßig überschreibt Forms einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die die Überschreibung für die oben aufgeführten Optionen abbrechen. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administrationskonsole auf **Dienste** > **Forms**.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option aktiviert ist, verwendet Forms seine Standardwerte für die Einstellungen „packets“, „creator“, „producer“ und „compressObjectStream“. Wenn diese Option deaktiviert ist, verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf **Speichern**.
