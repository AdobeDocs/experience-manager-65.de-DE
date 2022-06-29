---
title: Schriften bereitstellen
seo-title: Make fonts available
description: Stellen Sie sicher, dass Schriften, die in einem Formular verwendet werden, zur Verwendung auf dem J2EE-Anwendungsserver, der als Host für AEM Forms dient, zur Verfügung stehen.
seo-description: Ensure that the fonts used within a form are available for use on the J2EE application server hosting AEM forms.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
exl-id: e9eae896-b1e4-4caa-b466-ac8c9e7416a4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---

# Schriften bereitstellen {#make-fonts-available}

Stellen Sie sicher, dass Schriften, die in einem Formular verwendet werden, zur Verwendung auf dem J2EE-Anwendungsserver, der als Host für AEM Forms dient, zur Verfügung stehen. Betrachten Sie beispielsweise das folgende Szenario. Ein Formularentwickler fügt dem Schriftartenordner, das von Designer verwendet wird, eine Schrift hinzu und erstellt ein Formular, das diese Schrift verwendet, auf einem separaten Computer. Damit der Output-Dienst diese Schrift verwenden kann, legen Sie sie im „Verzeichnis für Kundenschriftarten“ ab. Wenn der Ordner für Kundenschriftarten nicht vorhanden ist, erstellen Sie einen Ordner auf dem J2EE-Anwendungsserver, der als Host für AEM Forms dient.

Weitere Informationen zu Schriftarteinstellungen finden Sie unter [Konfigurieren allgemeiner AEM Forms-Einstellungen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Speicherort des „Verzeichnisses für Kundenschriftarten“ angeben.**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie in das Feld „Speicherort des Verzeichnisses für Systemschriftarten“ den Pfad für den Ordner für Kundenschriftarten an. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.
1. Klicken Sie auf OK.
1. Starten Sie das System neu, auf dem AEM Forms installiert ist.

>[!NOTE]
>
>Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.
