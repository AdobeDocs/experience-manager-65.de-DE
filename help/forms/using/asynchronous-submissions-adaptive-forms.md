---
title: Asynchrone Übermittlung von adaptiven Formularen
seo-title: Asynchrone Übermittlung von adaptiven Formularen
description: In diesem Abschnitt wird die Konfiguration der asynchronen Übermittlung adaptiver Formulare beschrieben.
seo-description: In diesem Abschnitt wird die Konfiguration der asynchronen Übermittlung adaptiver Formulare beschrieben.
uuid: 6555ac63-4d99-4b39-a2d0-a7e61909106b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 0a0d2109-ee1f-43f6-88e5-1108cd215da6
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 67%

---


# Asynchrone Übermittlung von adaptiven Formularen{#asynchronous-submission-of-adaptive-forms}

Webformulare werden herkömmlicherweise für die synchrone Übermittlung konfiguriert. Wenn Benutzer ein Formular synchron senden, werden sie zu einer Bestätigungsseite, zu einer Danksagungsseite oder bei fehlgeschlagener Übermittlung zu einer Fehlerseite umgeleitet. Allerdings sind moderne Webabläufe wie Einzelseitenanwendungen zunehmend beliebt. Dabei bleibt die Webseite unverändert, während die Client-Server-Interaktion im Hintergrund abläuft. Sie können diese Erfahrung jetzt in adaptiven Formularen bieten, indem Sie die asynchrone Übermittlung konfigurieren.

Bei asynchroner Übermittlung fügt der Formularentwickler ein separates Erlebnis ein, z. B. beim Weiterleiten zu einem anderen Formular oder einem separaten Abschnitt der Website. Der Autor kann auch separate Dienste wie das Senden von Daten an einen anderen Datenspeicher oder eine benutzerdefinierte Analytics-Engine hinzufügen. Bei asynchroner Übermittlung verhält sich ein adaptives Formular wie eine Einzelseitenanwendung, da das Formular nicht erneut geladen wird oder sich seine URL nicht ändert, wenn die gesendeten Formulardaten auf dem Server validiert werden.

Im Folgenden finden Sie Details zu asynchronen Übermittlung in adaptiven Formularen.

## Asynchrone Übermittlung konfigurieren {#configure}

So konfigurieren Sie die asynchrone Übermittlung für eine adaptives Formular:

1. Wählen Sie im Authoring-Modus für adaptive Formulare das Objekt &quot;Form Container&quot;aus und tippen Sie auf ![cmppr1](assets/cmppr1.png), um die Eigenschaften zu öffnen.
1. Aktivieren Sie im Abschnitt **[!UICONTROL Submission]** properties **[!UICONTROL Asynchronous submission]**.
1. Wählen Sie im Abschnitt **[!UICONTROL Beim Absenden]** eine der folgenden Optionen aus, die bei der erfolgreichen Übermittlung des Formulars ausgeführt werden soll.

   * **[!UICONTROL Zu URL umleiten]**: Leitet bei Übermittlung des Formulars an die angegebene URL bzw. auf die angegebene Seite um. Sie können eine URL angeben oder im Feld **[!UICONTROL Umleitungs-URL/Pfad]** den Pfad zu einer Seite auswählen.
   * **[!UICONTROL Nachricht anzeigen]**: Zeigt eine Meldung beim Senden des Formulars an. Sie können eine Nachricht in das Textfeld unter der Option Nachricht anzeigen schreiben. Das Textfeld unterstützt Rich Text-Formatierung.

1. Tippen Sie auf ![check-button1](assets/check-button1.png), um die Eigenschaften zu speichern.

## Funktionsweise der asynchronen Übermittlung {#how-asynchronous-submission-works}

AEM Forms bietet standardmäßig Handler zur Verarbeitung von erfolgreichen und fehlgeschlagenen Formularübermittlungen an. Handler sind clientseitige Funktionen, die anhand der Serverantwort ausgeführt werden. Wenn ein Formular übermittelt wird, werden die Daten zur Validierung an den Server gesendet, der eine Antwort mit Informationen über den Erfolg oder das Fehlschlagen der Übermittlung an den Client zurücksendet. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen.

Darüber hinaus können Formularverfasser und -entwickler Regeln auf Formularebene schreiben, um Standard-Handler zu überschreiben. Weitere Informationen finden Sie unter [Standard-Handler mithilfe von Regeln außer Kraft setzen](#custom).

Im Folgenden wird zunächst die Serverantwort für Erfolgs- und Fehlerereignisse beschrieben.

### Serverantwort für Erfolgsereignis bei Übermittlung {#server-response-for-submission-success-event}

Die Serverantwort für Erfolgsereignis bei Übermittlung weist folgende Struktur auf:

```json
{
  contentType : "<xmlschema or jsonschema>",
  data : "<dataXML or dataJson>" ,
  thankYouOption : <page/message>,
  thankYouContent : "<thank you page url/thank you message>"
}
```

Die Antwort des Servers für die erfolgreiche Übermittlung eines Formulars enthält:

* Formattyp der Formulardaten: XML oder JSON
* Formulardaten im XML- oder JSON-Format
* Ausgewählte Option zum Umleiten auf eine Seite oder zum Anzeigen einer Meldung wie im Formular konfiguriert
* Seiten-URL oder Meldungsinhalt wie in dem Formular konfiguriert

Der Erfolgs-Handler liest die Serverantwort und leitet dementsprechend zur konfigurierten Seiten-URL weiter oder zeigt eine Meldung an.

### Serverantwort für Fehlerereignis bei Übermittlung  {#server-response-for-submission-error-event}

Die Serverantwort für Fehlerereignis bei Übermittlung weist folgende Struktur auf:

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

Die Antwort des Servers für eine fehlgeschlagene Übermittlung eines Formulars enthält:

* Grund für den Fehler, falsche Antwort in CAPTCHA oder fehlgeschlagene serverseitige Validierung
* Liste der Fehlerobjekte einschließlich SOM-Ausdruck des Felds mit der fehlgeschlagenen Validierung und zugehörige Fehlermeldung

Der Fehler-Handler liest die Serverantwort und zeigt die entsprechende Fehlermeldung im Formular an.

## Standard-Handler mithilfe von Regeln außer Kraft setzen  {#custom}

Formularautoren und -entwickler können im Codeeditor formularspezifische Regeln schreiben, die die Standard-Handler außer Kraft setzen. Die Serverantwort auf Erfolgs- und Fehlermeldungen wird auf Formularebene bereitgestellt, auf die Entwickler mithilfe von `$event.data` in Ereignissen zugreifen können.

Führen Sie die folgenden Schritte aus, um im Codeeditor Regeln zu schreiben, um die Erfolgs- und Fehlerereignisse zu verarbeiten.

1. Öffnen Sie das adaptive Formular im Bearbeitungsmodus, wählen Sie ein beliebiges Formularobjekt aus und tippen Sie auf ![edit-rules1](assets/edit-rules1.png), um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Formular]** in der Struktur „Formularobjekte“ und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Wählen Sie **[!UICONTROL Codeeditor]** aus der Dropdownliste zur Auswahl des Modus.
1. Tippen Sie im Codeeditor auf **[!UICONTROL Code bearbeiten]**. Tippen Sie im Bestätigungsdialogfeld auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie **[!UICONTROL Übermittlung erfolgreich]** oder **[!UICONTROL Fehler beim Einreichen]** aus der Dropdownliste **[!UICONTROL Ereignis]**.
1. Schreiben Sie eine Regel für das ausgewählte Ereignis und tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern.

