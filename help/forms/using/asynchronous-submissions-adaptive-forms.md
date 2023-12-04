---
title: Asynchrone Übermittlung von adaptiven Formularen
description: Erfahren Sie, wie Sie die asynchrone Übermittlung für adaptive Formulare konfigurieren.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms
exl-id: bd0589e2-b15a-4f0e-869c-2da4760b1ff4
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 70%

---

# Asynchrone Übermittlung von adaptiven Formularen{#asynchronous-submission-of-adaptive-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/asynchronous-submissions-adaptive-forms.html) |
| AEM 6.5 | Dieser Artikel |

Web-Formulare werden herkömmlicherweise für die synchrone Übermittlung konfiguriert. Wenn Benutzer bei der synchronen Übermittlung ein Formular übermitteln, werden sie auf eine Bestätigungsseite, eine Dankeseite oder, falls ein Sendefehler vorliegt, eine Fehlerseite umgeleitet. Allerdings sind moderne Web-Abläufe wie Einzelseitenanwendungen zunehmend beliebt. Dabei bleibt die Web-Seite unverändert, während die Client-Server-Interaktion im Hintergrund abläuft. Sie können diese Erfahrung jetzt in adaptiven Formularen bieten, indem Sie die asynchrone Übermittlung konfigurieren.

Bei der asynchronen Übermittlung fügt der Formularentwickler beim Absenden des Formulars durch den Benutzer ein separates Erlebnis ein, wie etwa die Weiterleitung zu einem anderen Formular oder einem separaten Bereich der Website. Der Autor kann auch separate Services wie das Senden von Daten an einen anderen Speicherort oder das Hinzufügen einer benutzerdefinierten Analytics-Engine einbinden. Bei asynchroner Übermittlung verhält sich ein adaptives Formular wie eine Einzelseitenanwendung, da das Formular nicht neu geladen wird oder sich die URL nicht ändert, wenn die gesendeten Formulardaten auf dem Server validiert werden.

Weitere Informationen zur asynchronen Übermittlung in adaptiven Formularen finden Sie im Abschnitt .

## Asynchrone Übermittlung konfigurieren {#configure}

Konfigurieren der asynchronen Übermittlung für ein adaptives Formular:

1. Wählen Sie im Authoring-Modus für adaptive Formulare das Objekt Formular-Container aus und wählen Sie ![cmppr1](assets/cmppr1.png) , um seine Eigenschaften zu öffnen.
1. Aktivieren Sie im Eigenschaftenbereich **[!UICONTROL Übermittlung]** die Option **[!UICONTROL Asynchrone Übermittlung verwenden]**.
1. Wählen Sie im Abschnitt **[!UICONTROL Beim Absenden]** eine der folgenden Optionen aus, die bei der erfolgreichen Übermittlung des Formulars ausgeführt werden soll.

   * **[!UICONTROL Zu URL umleiten]**: Leitet beim Senden des Formulars zur angegebenen URL oder Seite um. Sie können eine URL angeben oder mit der Funktion zum Durchsuchen den Pfad zu einer Seite im Feld **[!UICONTROL Umleitungs-URL/Pfad]** wählen.
   * **[!UICONTROL Nachricht anzeigen]**: Zeigt eine Meldung beim Senden des Formulars an. Sie können eine Nachricht in das Textfeld unterhalb der Option Nachricht anzeigen eingeben. Das Textfeld unterstützt Rich-Text-Formatierung.

1. Auswählen ![check-button1](assets/check-button1.png) , um die Eigenschaften zu speichern.

## Funktionsweise der asynchronen Übermittlung {#how-asynchronous-submission-works}

AEM Forms bietet standardmäßig Handler zur Verarbeitung von erfolgreichen und fehlgeschlagenen Formularübermittlungen an. Handler sind Client-seitige Funktionen, die basierend auf der Server-Antwort ausgeführt werden. Wenn ein Formular gesendet wird, werden die Daten zur Validierung an den Server übermittelt, der eine Antwort mit Informationen zum Erfolgs- oder Fehlerereignis für die Übermittlung an den Client zurückgibt. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen.

Darüber hinaus können Formularautoren und -entwickler formularspezifische Regeln schreiben, die die Standard-Handler überschreiben. Weitere Informationen finden Sie unter [Standard-Handler mithilfe von Regeln außer Kraft setzen](#custom).

Im Folgenden wird zunächst die Server-Antwort auf Erfolgs- und Fehlerereignisse beschrieben.

### Server-Antwort für Erfolgsereignis bei Übermittlung {#server-response-for-submission-success-event}

Die Server-Antwort für Erfolgsereignis bei Übermittlung weist folgende Struktur auf:

```json
{
  contentType : "<xmlschema or jsonschema>",
  data : "<dataXML or dataJson>" ,
  thankYouOption : <page/message>,
  thankYouContent : "<thank you page url/thank you message>"
}
```

Die Serverantwort bei erfolgreicher Formularübermittlung umfasst:

* Formattyp der Formulardaten: XML oder JSON
* Formulardaten im XML- oder JSON-Format
* Ausgewählte Option zum Umleiten auf eine Seite oder zum Anzeigen einer Nachricht wie im Formular konfiguriert
* Seiten-URL oder Nachrichteninhalt wie im Formular konfiguriert

Der Erfolgs-Handler liest die Server-Antwort und leitet entsprechend zur konfigurierten Seiten-URL weiter oder zeigt eine Nachricht an.

### Serverantwort für Fehlerereignis bei Übermittlung {#server-response-for-submission-error-event}

Die Server-Antwort für ein Fehlerereignis bei Übermittlung weist folgende Struktur auf:

```json
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

Die Serverantwort, wenn bei der Formularübermittlung ein Fehler auftritt, umfasst:

* Grund für den Fehler, falsche Antwort in CAPTCHA oder fehlgeschlagene Server-seitige Validierung
* Liste der Fehlerobjekte einschließlich SOM-Ausdruck des Felds mit der fehlgeschlagenen Validierung und zugehörige Fehlermeldung

Der Fehler-Handler liest die Antwort des Servers und zeigt die entsprechende Fehlermeldung im Formular an.

## Standard-Handler mithilfe von Regeln außer Kraft setzen {#custom}

Formularentwickler und -autoren können im Code-Editor auf Formularebene Regeln schreiben, um Standard-Handler zu überschreiben. Die Antwort des Servers bei Erfolgs- und Fehlerereignissen wird auf Formularebene bereitgestellt, auf die Entwickler mithilfe von `$event.data` in Regeln zugreifen können.

Führen Sie die folgenden Schritte aus, um im Codeeditor Regeln zu schreiben, um die Erfolgs- und Fehlerereignisse zu verarbeiten.

1. Öffnen Sie das adaptive Formular im Authoring-Modus, wählen Sie ein beliebiges Formularobjekt aus und wählen Sie ![edit-rules1](assets/edit-rules1.png) , um den Regeleditor zu öffnen.
1. Auswählen **[!UICONTROL Formular]** Wählen Sie in der Formularobjektstruktur die Option **[!UICONTROL Erstellen]**.
1. Auswählen **[!UICONTROL Code-Editor]** aus der Dropdown-Liste der Modusauswahl.
1. Wählen Sie im Code-Editor **[!UICONTROL Code bearbeiten]**. Auswählen **[!UICONTROL Bearbeiten]** im Bestätigungsdialogfeld angezeigt.
1. Auswählen **[!UICONTROL Erfolgreiche Übermittlung]** oder **[!UICONTROL Fehler bei Übermittlung]** aus dem **[!UICONTROL Ereignis]** angezeigt.
1. Eine Regel für das ausgewählte Ereignis schreiben und auswählen **[!UICONTROL Fertig]** , um die Regel zu speichern.
