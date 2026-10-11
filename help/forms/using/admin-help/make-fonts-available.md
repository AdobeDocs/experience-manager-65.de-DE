---
title: Bereitstellen von Schriften
description: Stellen Sie sicher, dass die in einem Formular verwendeten Schriften für den J2EE-Anwendungs-Server zur Verfügung stehen, der als Host für AEM Forms dient.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e9eae896-b1e4-4caa-b466-ac8c9e7416a4
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
source-wordcount: '228'
ht-degree: 100%
---
# Bereitstellen von Schriften {#make-fonts-available}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Stellen Sie sicher, dass die in einem Formular verwendeten Schriften für den J2EE-Anwendungs-Server zur Verfügung stehen, der als Host für AEM Forms dient. Betrachten Sie beispielsweise das folgende Szenario. Eine Formularentwicklerin oder ein Formularentwickler fügt dem Schriftartenverzeichnis, das von Designer verwendet wird, eine Schrift hinzu und erstellt ein Formular, das diese Schrift verwendet, auf einem separaten Computer. Damit der Ausgabe-Service diese Schrift verwenden kann, legen Sie sie im Verzeichnis für Kundenschriftarten ab. Wenn das Verzeichnis für Kundenschriftarten nicht vorhanden ist, erstellen Sie ein entsprechendes Verzeichnis auf dem J2EE-Anwendungs-Server, der als Host für AEM Forms dient.

Weitere Informationen zu Schrifteinstellungen finden Sie unter [Konfigurieren allgemeiner AEM Forms-Einstellungen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Angeben des Speicherorts des Verzeichnisses für Kundenschriftarten**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie im Feld „Speicherort des Verzeichnisses für Systemschriftarten“ den Pfad für das Verzeichnis für Kundenschriftarten an. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.
1. Klicken Sie auf OK.
1. Starten Sie das System neu, auf dem AEM Forms installiert ist.

>[!NOTE]
>
>Schriften werden aus dem Schriftarten-Cache des Windows-Systems ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.
