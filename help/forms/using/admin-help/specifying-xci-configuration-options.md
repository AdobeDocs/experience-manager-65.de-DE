---
title: Angeben der XCI-Konfigurationsoptionen
description: Erfahren Sie, wie Sie die XCI-Konfigurationsoptionen festlegen. Sie können benutzerdefinierte XCI-Dateiwerte für das adaptive Formular angeben, damit sie beim Rendern von Formularen verwendet werden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7cd10389-63e6-41f2-a132-92fd9e40a9b7
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
source-wordcount: '161'
ht-degree: 90%
---
# Angeben der XCI-Konfigurationsoptionen {#specifying-xci-configuration-options}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Mit Forms können Sie eine benutzerdefinierte XCI-Datei angeben, die für das Rendern verwendet werden kann. (Siehe [Konfigurieren von Speicherorten für Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Standardmäßig überschreibt Forms einige der in der XCI-Datei angegebenen Optionen, einschließlich der folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die die Überschreibung für die oben aufgeführten Optionen abbrechen. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administrationskonsole auf **Dienste** > **Forms**.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option aktiviert ist, verwendet Forms seine Standardwerte für die Einstellungen „packets“, „creator“, „producer“ und „compressObjectStream“. Wenn diese Option deaktiviert ist, verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf **Speichern**.
