---
title: Überblick über den Ausgabe-Service
description: Mit der Ausgabe können Sie XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammenführen, um einen Dokumentausgabestream in verschiedenen Formaten zu erstellen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e99b72d0-fbd5-4150-a225-1a91ad4c5867
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 7%

---

# Überblick über den Ausgabe-Service {#overview-of-output-service}

Mit der Ausgabe können Sie XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammenführen, um einen Dokumentausgabestream in verschiedenen Formaten zu erstellen. Der Ausgabestream kann an einen Netzwerkdrucker, einen lokalen Drucker oder eine Festplattendatei gesendet werden

Sie können die Output-Seite in Administration Console verwenden, um den Output-Dienst zu verwalten. Die konfigurierten Einstellungen werden zur Laufzeit verwendet, wenn die entsprechenden Einstellungen nicht über die AEM Forms-API angegeben wurden. Die über das AEM Forms SDK vorgenommene Konfiguration setzt die mithilfe von Administration Console konfigurierten Einstellungen außer Kraft.

Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_61_de).

Auf den Output-Seiten in Administration Console können Sie mehrere Aufgaben ausführen:

* Geben Sie Zeichensätze für die Internationalisierung an. (Siehe [Zeichensatz ändern](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).
* Geben Sie absolute und relative Pfade für URLs, URIs, XCIs und Dateispeicherorte an. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).
* Konfigurieren Sie die Cachegrößen und -richtlinien. (Siehe [Festlegen des Cache-Modus](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) und [Cache-Einstellungen konfigurieren](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).
* Schriftarten auf dem Anwendungsserver verfügbar machen. (Siehe [Schriftarten verfügbar machen](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).
* Geben Sie die einzubettenden Schriften an. (Siehe [Einzubettende Schriften angeben](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).
* Geben Sie die XCI-Konfigurationsoptionen an. (Siehe [XCI-Konfigurationsoptionen angeben](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).
* Geben Sie die Sicherheitseinstellungen an. (Siehe [Sicherheitseinstellungen festlegen](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).

Nachdem Sie die Einstellungen geändert haben, klicken Sie auf Speichern , um sie auf Output anzuwenden. Sie müssen den Server nicht neu starten, damit die Änderungen wirksam werden. Möglicherweise müssen Sie den Output-Dienst jedoch beim Konfigurieren der Cacheeinstellungen neu starten.
