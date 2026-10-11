---
title: Überblick über den Ausgabe-Service
description: Mit der Ausgabe können Sie XML-Daten mit einem in Designer erstellten Formularentwurf zusammenführen und einen Dokumentausgabe-Stream in einer Vielzahl von Formaten erstellen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e99b72d0-fbd5-4150-a225-1a91ad4c5867
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
source-wordcount: '263'
ht-degree: 100%
---
# Überblick über den Ausgabe-Service {#overview-of-output-service}

Mit der Ausgabe können Sie XML-Daten mit einem in Designer erstellten Formularentwurf zusammenführen und einen Dokumentausgabe-Stream in einer Vielzahl von Formaten erstellen. Der Ausgabe-Stream kann an einen Netzwerkdrucker, einen lokalen Drucker oder in eine Datei auf einem Datenträger gesendet werden.

Sie können die Ausgabe-Seite in der Administrationskonsole verwenden, um den Ausgabe-Dienst zu verwalten. Die von Ihnen konfigurierten Einstellungen werden zur Laufzeit verwendet, wenn die entsprechenden Einstellungen nicht über die API von AEM Forms festgelegt wurden. Die über das AEM Forms-SDK vorgenommene Konfiguration setzt die mit der Administrationskonsole konfigurierten Einstellungen außer Kraft.

Weitere Informationen zum Ausgabe-Service finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_61_de).

Sie können auf den Ausgabe-Seiten in der Administrationskonsole mehrere Aufgaben durchführen:

* Geben Sie Zeichensätze für die Internationalisierung an. (Siehe [Ändern des Zeichensatzes](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).)
* Geben Sie absolute und relative Pfade für URLs, URIs, XCIs und Dateispeicherorte an. (Siehe [Angeben der Dateispeicherorte für die Ausgabe](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)
* Konfigurieren Sie Cache-Größen und -Richtlinien. (Siehe [Angeben des Cache-Modus](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) und [Konfigurieren der Cache-Einstellungen](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).)
* Stellen Sie Schriften auf dem Anwendungs-Server bereit. (Siehe [Bereitstellen von Schriften](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).)
* Geben Sie die einzubettenden Schriften an. (Siehe [Angeben der einzubettenden Schriftarten](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).)
* Geben Sie die XCI-Konfigurationsoptionen an. (Siehe [Angeben von XCI-Konfigurationsoptionen](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).)
* Geben Sie die Sicherheitseinstellungen an. (Siehe [Angeben der Sicherheitseinstellungen](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).)

Klicken Sie nach dem Ändern der Einstellungen auf „Speichern“, um sie auf die Ausgabe anzuwenden. Der Server muss nicht neu gestartet werden, um die Änderungen zu übernehmen. Sie müssen jedoch ggf. den Ausgabe-Service neu starten, wenn Sie Cache-Einstellungen konfigurieren.
