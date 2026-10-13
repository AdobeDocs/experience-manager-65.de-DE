---
title: Konfigurieren der Formularausgabe
description: Erfahren Sie, wie Sie die Formularausgabe konfigurieren. Um die Formularausgabe zu konfigurieren und die Funktion zu aktivieren, verwenden Sie die benutzerdefinierten Skripte vor der Formularübermittlung.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d739806c-ce72-40fd-b304-3262a0988d96
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
source-wordcount: '257'
ht-degree: 100%
---
# Konfigurieren der Formularausgabe{#configuring-form-output}

## Geben Sie den Typ der HTML-Ausgabe an, der an den Webbrowser zurückgegeben wird {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms“.
1. Wählen Sie unter „Formularausgabe“ in der Liste „Ausgabetyp“ eine der folgenden Optionen aus:

   **Voll-HTML**: Zum Rendern des Formulars mit vollständigen HTML-Tags (eine vollständige HTML-Seite). Dies ist der Standardwert.

   **Formularhauptteil:** Um das Formular zwischen `<BODY>`-Tags wiederzugeben (keine vollständige HTML-Seite).

1. Klicken Sie auf Speichern.

## Geben Sie den Ort an, an dem PDF-Inhalte gerendert werden. {#specify-the-location-where-pdf-content-is-rendered}

1. Wählen Sie unter „Formularausgabe“ in der Liste „Rendern auf“ eine der folgenden Optionen aus:

   **Client:** Rendern von PDF-Formularen in Adobe Acrobat oder Adobe Reader Das Client-seitige Rendern verbessert die Leistung von AEM-Formularen und findet nur bei der PDFForm-Transformation Anwendung.

   **Server:** Rendern von PDF-Formularen auf dem Anwendungs-Server

   **Autom.**, um das PDF-Formular an dem Ort wiederzugeben, der über den Konfigurationswert `dynamicRender` der XDP-Datei angegeben ist. Dies ist der Standardwert.

1. Klicken Sie auf Speichern.

## Konfigurieren von Aufrufen benutzerdefinierter Skripte, bevor das Formular abgesendet wird {#configuring-invocation-of-custom-scripts-before-form-submit}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Führen Sie zum Aktivieren der Funktion folgende Schritte durch:

1. Melden Sie sich bei der Administrationskonsole an.
1. Gehen Sie zu **Dienste** > **Formulare**.
1. Geben Sie den Ausgabetyp als Form Body an.
1. Speichern Sie die Einstellungen.
1. Deklarieren Sie eine JavaScript-Variable, __CUSTOM_SCRIPTS_VERSION, im Kopfteil des HTML-Codes und stellen Sie den Wert auf 1 ein.

   >[!NOTE]
   >
   >*Um die Funktion zu deaktivieren, können Sie die JavaScript-Variable entfernen oder ihren Wert auf 0 einstellen.*
