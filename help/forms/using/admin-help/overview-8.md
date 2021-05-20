---
title: Überblick über den Ausgabedienst
seo-title: Überblick über den Ausgabedienst
description: 'Mit Output können Sie XML-Daten mit einem in Designer erstellten Formularentwurf zusammenführen und einen Dokumentausgabestream in einer Vielzahl von Formaten erstellen: '
seo-description: 'Mit Output können Sie XML-Daten mit einem in Designer erstellten Formularentwurf zusammenführen und einen Dokumentausgabestream in einer Vielzahl von Formaten erstellen: '
uuid: 7890b0a6-bae5-4ad5-ae41-503b988ba3da
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5a96f5ea-6fe3-44b1-b314-14097b9e9c01
exl-id: e99b72d0-fbd5-4150-a225-1a91ad4c5867
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 97%

---

# Überblick über den Ausgabedienst {#overview-of-output-service}

Mit Output können Sie XML-Daten mit einem in Designer erstellten Formularentwurf zusammenführen und einen Dokumentausgabestream in einer Vielzahl von Formaten erstellen: Der Ausgabestream kann an einen Netzwerkdrucker, einen lokalen Drucker oder in eine Datei auf einem Datenträger gesendet werden

Sie können die Output-Seite in Administration Console verwenden, um den Output-Dienst zu verwalten. Die von Ihnen konfigurierten Einstellungen werden zur Laufzeit verwendet, wenn die entsprechenden Einstellungen nicht über die API von AEM Forms festgelegt wurden. Die über das AEM Forms SDK vorgenommene Konfiguration setzt die mit Administration Console konfigurierten Einstellungen außer Kraft.

Weitere Informationen zum Ausgabedienst finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_61).

Sie können auf den Output-Seiten in Administration Console mehrere Aufgaben durchführen:

* Zeichensätze für die Internationalisierung angeben. (Siehe [Den Zeichensatz ändern](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).)
* Absolute und relative Pfade für URLs, URIs, XCIs und Dateispeicherorte angeben. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)
* Cachegrößen und -richtlinien konfigurieren (Siehe [Cachemodus angeben](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) und [Cache-Einstellungen konfigurieren](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).)
* Schriften auf dem Anwendungsserver bereitstellen. (Siehe [Schriftarten zur Verfügung stellen](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).)
* Einzubettende Schriften angeben. (Siehe [Einzubettende Schriften angeben](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).)
* XCI-Konfigurationsoptionen angeben. (Siehe [XCI-Konfigurationsoptionen angeben](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).)
* Sicherheitseinstellungen angeben. (Siehe [Sicherheitseinstellungen angeben](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).)

Klicken Sie nach dem Ändern der Einstellungen auf „Speichern“, um sie auf Output anzuwenden. Der Server muss nicht neu gestartet werden, um die Änderungen zu übernehmen. Sie müssen jedoch ggf. den Output-Dienst neu starten, wenn Sie Cacheeinstellungen konfigurieren.
