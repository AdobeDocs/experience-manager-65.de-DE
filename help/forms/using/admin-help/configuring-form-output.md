---
title: Formularausgabe konfigurieren
seo-title: Formularausgabe konfigurieren
description: Erfahren Sie, wie Sie die Formularausgabe konfigurieren.
seo-description: Erfahren Sie, wie Sie die Formularausgabe konfigurieren.
uuid: 70aad14e-c845-4ef3-a751-ad8860d5d505
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 17c9b69a-3c6f-47e3-a828-841bb90eba8b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 94%

---


# Formularausgabe konfigurieren{#configuring-form-output}

## Den Typ der HTML-Ausgabe angeben, der an den Webbrowser zurückgegeben wird.{#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Wählen Sie unter „Formularausgabe“ in der Liste „Ausgabetyp“ eine der folgenden Optionen aus:

   **Voll-HTML**, um das Formular mit vollständigen HTML-Tags wiederzugeben (eine vollständige HTML-Seite). Dies ist der Standardwert.

   **Formularhauptteil:** Zum Wiedergeben des Formulars in  `<BODY>` Tags (keine vollständige HTML-Seite).

1. Klicken Sie auf Speichern.

## Den Ort angeben, an dem PDF-Inhalt wiedergegeben wird. {#specify-the-location-where-pdf-content-is-rendered}

1. Wählen Sie unter „Formularausgabe“ in der Liste „Wiedergeben“ eine der folgenden Optionen aus:

   **Client**, um PDF-Formulare in Adobe Acrobat oder Adobe Reader wiederzugeben. Die clientseitige Wiedergabe verbessert die Leistung von AEM Forms und findet nur bei der PDFForm-Transformation Anwendung.

   **Server**, um PDF-Formulare auf dem Anwendungsserver wiederzugeben.

   **Autom.**, um das PDF-Formular an dem Ort wiederzugeben, der über den Konfigurationswert `dynamicRender` der XDP-Datei angegeben ist. Dies ist der Standardwert.

1. Klicken Sie auf Speichern.

## Aufrufe von benutzerdefinierten Skripten konfigurieren, bevor das Formular eingereicht wird  {#configuring-invocation-of-custom-scripts-before-form-submit}

Führen Sie zum Aktivieren der Funktion folgende Schritte durch:

1. Melden Sie sich bei Administration Console an.
1. Gehen Sie zu **Dienste** > **Forms**.
1. Geben Sie den Ausgabetyp als Form Body an.
1. Speichern Sie die Einstellungen.
1. Deklarieren Sie eine JavaScript-Variable, __CUSTOM_SCRIPTS_VERSION, im Kopfteil des HTML-Codes und stellen Sie den Wert auf 1 ein.

   >[!NOTE]
   >
   >*Um die Funktion zu deaktivieren, können Sie die JavaScript-Variable entfernen oder ihren Wert auf 0 einstellen.*

