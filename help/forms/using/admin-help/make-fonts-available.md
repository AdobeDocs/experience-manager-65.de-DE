---
title: Bereitstellen von Schriften
description: Stellen Sie sicher, dass die in einem Formular verwendeten Schriftarten für die Verwendung auf dem J2EE-Anwendungsserver verfügbar sind, auf dem AEM Formulare gehostet werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e9eae896-b1e4-4caa-b466-ac8c9e7416a4
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 16%

---

# Bereitstellen von Schriften {#make-fonts-available}

Stellen Sie sicher, dass die in einem Formular verwendeten Schriftarten für die Verwendung auf dem J2EE-Anwendungsserver verfügbar sind, auf dem AEM Formulare gehostet werden. Betrachten Sie beispielsweise das folgende Szenario. Ein Formularentwickler fügt dem Schriftartenordner, den Designer verwendet, eine Schrift hinzu und erstellt ein Formular, das diese Schrift verwendet, auf einem separaten Computer. Damit der Output-Dienst die Schrift verwenden kann, legen Sie sie im Verzeichnis &quot;Kundenschriftarten&quot;ab. Wenn der Ordner für Kundenschriftarten nicht vorhanden ist, erstellen Sie einen Ordner auf dem J2EE-Anwendungsserver, der AEM Formulare hostet.

Weitere Informationen zu Schrifteinstellungen finden Sie unter [Allgemeine Einstellungen AEM Formulare konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Speicherort des Ordners für Kundenschriftarten angeben**

1. Klicken Sie in Administration Console auf Einstellungen > Core-Systemeinstellungen > Konfigurationen.
1. Geben Sie in das Feld Speicherort des Ordners für Systemschriftarten den Pfad zum Verzeichnis für Kundenschriftarten ein. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.
1. Klicken Sie auf OK.
1. Starten Sie das System neu, auf dem AEM Formulare installiert sind.

>[!NOTE]
>
>Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.
