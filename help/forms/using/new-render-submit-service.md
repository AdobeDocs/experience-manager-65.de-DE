---
title: Neuer Wiedergabe- und Sendedienst
description: Definieren Sie Render- und Sendedienste in Workbench, um XDP-Formulare als HTML oder PDF zu rendern, je nach Gerät, von dem der Zugriff erfolgt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 46de0101-9607-4429-84c3-7c1f34d2da27
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 100%

---

# Neuer Wiedergabe- und Sendedienst{#new-render-and-submit-service}

## Einführung {#introduction}

Wenn Sie in Workbench einen `AssignTask`-Vorgang definieren, geben Sie ein bestimmtes Formular (XDP- oder PDF-Formular) an. Geben Sie außerdem über ein Aktionsprofil einen Satz von Render- und Sendediensten an.

XDP kann als PDF- oder HTML-Formular gerendert werden. Die neuen Funktionen bieten u. a. folgende Möglichkeiten:

* Rendern und Senden eines XDP-Formulars als HTML
* Rendern und Senden eines XDP-Formulars als PDF auf dem Desktop und als HTML auf Mobilgeräten (z. B. einem iPad)

### Neuer HTML-Forms-Dienst {#new-html-forms-service}

Der neue HTML-Forms-Dienst nutzt die neue Funktion in Forms, um das Rendern von XDP-Formularen als HTML zu unterstützen. Der neue HTML-Forms-Dienst macht die folgenden Methoden verfügbar:

```java
/*
 * Generates a URL (for the HTML Form) to be passed to client, given a TaskContext.
 * The output of this API is something like this - /lc/content/xfaforms/profiles/default.ws.html?ContentRoot=repository://Applications/MyApplication/MyFolder&template=MyForm.xdp
 * @param taskContext task context
 * @param profileName Forms servlet URL.
 * @return form URL string
 */
public String generateFormURL(TaskContext taskContext, String profileName);

/*
 * Render the XDP Form as HTML. Can be used directly for updating the runtimeMap in render.
 * It adds the following keys to the map -
 * hint:new html form = true
 * newHTMLFormURL = the URL returned after calling 'generateFormURL' API.
 * @param TaskContext taskContext
 * @param profileName Forms servlet URL.
 * @param runtimeMap runtime map<string,object> associated with form rendering.
 * return runtimeMap
 */
public Map<String, Object> renderHTMLForm (TaskContext taskContext, String profileName, Map<String,Object> runtimeMap);
```

Weitere Informationen über Profile mobiler Formulare finden Sie unter [Erstellen eines benutzerdefinierten Profils](/help/forms/using/custom-profile.md).

## Neue Render- und Sendeprozesse für HTML-Formulare {#new-html-form-render-amp-submit-processes}

Geben Sie bei jedem Vorgang „Aufgabe zuweisen“ einen Render- und Sendeprozess für das Formular an. Diese Prozesse werden von den TaskManager-APIs `renderForm` und `submitForm` aufgerufen, um benutzerdefinierte Behandlung zu ermöglichen. Semantik dieser Prozesse für ein neues HTML-Formular:

### Rendern eines neuen HTML-Formulars {#render-a-new-html-form}

Der neue Prozess zum Rendern von HTML hat wie jeder Render-Prozess die folgenden E/A-Parameter:

Eingabe - `taskContext`

Ausgabe - `runtimeMap`

Ausgabe - `outFormDoc`

Diese Methode simuliert das genaue Verhalten der `renderHTMLForm`-API des neuen HTML-Forms-Dienstes. Sie ruft die `generateFormURL`-API auf, um die URL für die HTML-Darstellung des Formulars zu erhalten. Dann wird die runtimeMap mit folgendem Schlüssel bzw. folgenden Werten aufgefüllt:

new html form = true

newHTMLFormURL = die URL, die nach dem Aufruf der `generateFormURL`-API zurückgegeben wurde.

### Senden eines neuen HTML-Formulars {#submit-a-new-html-form}

Dieser Prozess zum Senden eines neuen HTML-Formulars verwendet die folgenden E/A-Parameter:

Eingabe - `taskContext`

Ausgabe - `runtimeMap`

Ausgabe - `outputDocument`

Der Prozess legt das `outputDocument` auf das `inputDocument` fest, das von `taskContext` abgerufen wird.

## Standardmäßige Render- oder Sendeprozesse und Aktionsprofile {#default-render-or-submit-processes-and-action-profiles}

Die standardmäßigen Render- und Sendeprozesse bieten Unterstützung zum Rendern von PDF-Dateien auf einem Desktop und von HTML auf Mobilgeräten (iPad).

### Default Render Form {#default-render-form}

Dieser Prozess rendert ein XDP-Formular nahtlos auf mehreren Plattformen. Der Prozess ruft den Benutzer-Agenten von `taskContext` ab und verwendet die Daten, um den Prozess zur Wiedergabe von entweder HTML oder PDF aufzurufen.

![default-render-form](assets/default-render-form.png)

### Default Submit Form {#default-submit-form}

Dieser Prozess sendet ein XDP-Formular nahtlos auf mehreren Plattformen. Er ruft den Benutzer-Agenten von `taskContext` ab und verwendet die Daten, um den Prozess zum Senden von HTML oder PDF aufzurufen.

![default-submit-form](assets/default-submit-form.png)

## Ändern des Renderns mobiler Formulare von PDF in HTML {#switch-the-rendering-of-mobile-forms-from-pdf-to-html}

Browser nehmen allmählich die Unterstützung für NPAPI-basierte Plug-ins zurück. Das betrifft auch Zusatzmodule für Adobe Acrobat und Adobe Reader. Sie können das Rendern mobiler Formulare von PDF in HTML wie folgt ändern:

1. Melden Sie sich bei Workbench mit gültigen Benutzerdaten an.
1. Wählen Sie **Datei** > **Anwendungen abrufen**.

   Das Dialogfeld „Anwendungen abrufen“ wird angezeigt.

1. Wählen Sie die Anwendungen aus, für die Sie die Wiedergabe der mobilen Formulare ändern möchten, und klicken Sie auf **OK**.
1. Öffnen Sie den Prozess, für den Sie die Wiedergabe ändern möchten.
1. Öffnen Sie den/die zielgerichtete/n Startpunkt/Aufgabe, navigieren Sie zum Abschnitt für Präsentation und Daten und klicken Sie auf **Aktionsprofile verwalten**.

   Das Dialogfeld „Aktionsprofile verwalten“ wird angezeigt. 
1. Ändern Sie die standardmäßige Wiedergabeprofilkonfigurationen von PDF in HTML und klicken Sie auf **OK**.
1. Checken Sie den Prozess ein.
1. Wiederholen Sie diese Schritte, um die Wiedergabe für andere Prozesse zu ändern.
1. Stellen Sie die Anwendung für die geänderten Prozesse bereit.

### Standardaktionsprofil {#default-action-profile}

Mit dem Standardaktionsprofil wurde das XDP-Formular als PDF gerendert. Dieses Verhalten wurde geändert, sodass jetzt die Prozesse „Default Render Form“ und „Default Submit Form“ verwendet werden.

Einige häufig gestellte Fragen zu Aktionsprofilen sind:

![gen_question_b_20](assets/gen_question_b_20.png) **Welche Render/Einreichungsprozesse werden standardmäßig verfügbar sein?**

* Render Guide (Guides werden nicht mehr unterstützt)
* Render Form Guide
* Render PDF form
* Render HTML form
* Render New HTML form (new)
* Default Render form (new)

Sowie entsprechende Sendeprozesse.

![gen_question_b_20](assets/gen_question_b_20.png) **Welche Aktionsprofile werden standardmäßig verfügbar sein?**

Für XDP-Formulare:

* Standard (Wiedergabe/Senden mithilfe der neuen „Default Render/Submit“-Prozesse)

![gen_question_b_20](assets/gen_question_b_20.png) **Was muss der Prozessentwickler tun, damit ein Formular auf einem Gerät in HTML und auf einem Desktop in PDF gerendert werden kann?**

Nichts. Das Standardaktionsprofil wird automatisch ausgewählt und der Render-Modus wird ebenfalls automatisch berücksichtigt.

![gen_question_b_20](assets/gen_question_b_20.png) **Was muss getan werden, damit das Formular auf einem Desktop in HTML gerendert werden kann?**

Der Benutzer muss das HTML-Optionsfeld für das Standardprofil auswählen.

![gen_question_b_20](assets/gen_question_b_20.png) **Wirkt sich das Upgrade auf das Ändern des Verhaltens des Standardaktionsprofils aus?**

Ja, da die vorherigen dem Standardaktionsprofil zugeordneten Wiedergabe- und Sendedienste unterschiedlich waren, werden sie als Anpassung der vorhandenen Formulare behandelt. Wenn Sie auf **Standardeinstellungen wiederherstellen** klicken, werden stattdessen die Standard-Render- und Einreichungsdienste eingestellt.

Angenommen, Sie haben die vorhandenen Render- oder Sendedienste für PDF-Formulare geändert oder benutzerdefinierte Dienste (z. B. custom1) erstellt und möchten nun dieselbe Funktion für die HTML-Wiedergabe verwenden. Sie müssen den neuen Render- oder Sendedienst (z. B. custom2) replizieren und ähnliche Anpassungen anwenden. Ändern Sie nun das Aktionsprofil für Ihre XDP, um custom2-Dienste anstelle von custom1-Diensten zum Rendern oder Senden zu verwenden.

Was muss der Prozessentwickler tun, damit ein Formular auf einem Gerät in HTML und auf einem Desktop in PDF gerendert werden kann?
Was muss der Prozessentwickler tun, damit ein Formular auf einem Gerät in HTML und auf einem Desktop in PDF gerendert werden kann?
