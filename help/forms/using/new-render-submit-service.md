---
title: Neuer Wiedergabe- und Sendedienst
description: Definieren Sie Wiedergabe- und Sendedienste in Workbench, um XDP-Formulare je nach Gerät, von dem aus auf sie zugegriffen wird, als HTML oder PDF wiederzugeben.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 46de0101-9607-4429-84c3-7c1f34d2da27
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 48%

---

# Neuer Wiedergabe- und Sendedienst{#new-render-and-submit-service}

## Einführung {#introduction}

Wenn Sie in Workbench einen `AssignTask`-Vorgang definieren, geben Sie ein bestimmtes Formular (XDP- oder PDF-Formular) an. Geben Sie außerdem über das Aktionsprofil einen Satz von Wiedergabe- und Sendediensten an.

Eine XDP kann als PDF- oder HTML-Formular wiedergegeben werden. Zu den neuen Funktionen gehören:

* Rendern und Senden eines XDP-Formulars als HTML
* Rendern und Senden eines XDP-Formulars als PDF auf dem Desktop und als HTML auf Mobilgeräten (z. B. einem iPad)

### Neuer HTML Forms-Dienst {#new-html-forms-service}

Der neue HTML Forms-Dienst verwendet die neue Funktion in Forms, um die Wiedergabe von XDP-Formularen als HTML zu unterstützen. Der neue HTML Forms-Dienst stellt die folgenden Methoden bereit:

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

Weitere Informationen zu Profilen in Mobile Forms finden Sie unter [Benutzerdefiniertes Profil erstellen](/help/forms/using/custom-profile.md).

## Neue HTML Form Render &amp; Submit-Prozesse {#new-html-form-render-amp-submit-processes}

Geben Sie für jeden &quot;AssignTask&quot;-Vorgang einen Wiedergabe- und einen Sendeprozess mit dem Formular an. Diese Prozesse werden von den TaskManager-APIs `renderForm` und `submitForm` aufgerufen, um benutzerdefinierte Behandlung zu ermöglichen. Semantik dieser Prozesse für das neue HTML-Formular:

### Neues HTML-Formular rendern {#render-a-new-html-form}

Der neue Prozess zum Rendern von HTML weist wie jeder Renderprozess die folgenden I/O-Parameter auf:

Eingabe - `taskContext`

Ausgabe - `runtimeMap`

Ausgabe - `outFormDoc`

Diese Methode simuliert das genaue Verhalten der `renderHTMLForm`-API des neuen HTML-Forms-Dienstes. Sie ruft die `generateFormURL`-API auf, um die URL für die HTML-Darstellung des Formulars zu erhalten. Anschließend füllt sie die runtimeMap mit den folgenden Schlüsseln oder Werten:

new html form = true

newHTMLFormURL = die URL, die nach dem Aufruf der `generateFormURL`-API zurückgegeben wurde.

### Neues HTML-Formular senden {#submit-a-new-html-form}

Dieser Prozess zum Senden eines neuen HTML-Formulars funktioniert mit den folgenden I/O-Parametern -

Eingabe - `taskContext`

Ausgabe - `runtimeMap`

Ausgabe - `outputDocument`

Der Prozess legt das `outputDocument` auf das `inputDocument` fest, das von `taskContext` abgerufen wird.

## Standardmäßige Wiedergabe- oder Sendeprozesse und Aktionsprofile {#default-render-or-submit-processes-and-action-profiles}

Die standardmäßigen Wiedergabe- und Sendedienste ermöglichen es, PDF auf einem Desktop und HTML auf Mobilgeräten (iPad) zu rendern.

### Standard-Renderformular {#default-render-form}

Dieser Prozess rendert ein XDP-Formular nahtlos auf mehreren Plattformen. Der Prozess ruft den Benutzer-Agenten von `taskContext` ab und verwendet die Daten, um den Prozess zur Wiedergabe von entweder HTML oder PDF aufzurufen.

![default-render-form](assets/default-render-form.png)

### Standardformular für die Übermittlung {#default-submit-form}

Durch diesen Prozess wird ein XDP-Formular nahtlos auf mehreren Plattformen gesendet. Er ruft den Benutzer-Agenten von `taskContext` ab und verwendet die Daten, um den Prozess zum Senden von HTML oder PDF aufzurufen.

![default-submit-form](assets/default-submit-form.png)

## Wechsel der Wiedergabe mobiler Formulare von PDF auf HTML {#switch-the-rendering-of-mobile-forms-from-pdf-to-html}

Browser nehmen allmählich die Unterstützung für NPAPI-basierte Plug-ins zurück. Das betrifft auch Zusatzmodule für Adobe Acrobat und Adobe Reader. Sie können das Rendering mobiler Formulare mithilfe der folgenden Schritte von PDF auf HTML ändern:

1. Melden Sie sich bei Workbench als gültiger Benutzer an.
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

Das standardmäßige Aktionsprofil hat das XDP-Formular als PDF wiedergegeben. Dieses Verhalten wurde geändert und verwendet nun die Prozesse &quot;Default Render Form&quot;und &quot;Default Submit Form&quot;.

Einige häufig gestellte Fragen zu Aktionsprofilen lauten wie folgt:

![gen_question_b_20](assets/gen_question_b_20.png) **Welche Render/Einreichungsprozesse werden standardmäßig verfügbar sein?**

* Render Guide (Guides werden nicht mehr unterstützt)
* Render Form Guide
* PDF-Formular rendern
* HTML-Formular rendern
* Neues HTML-Formular rendern (neu)
* Default Render Form (neu)

Und entsprechende Sendeprozesse.

![gen_question_b_20](assets/gen_question_b_20.png) **Welche Aktionsprofile werden standardmäßig verfügbar sein?**

Für XDP Forms:

* Standard (Wiedergabe/Senden mithilfe der neuen „Default Render/Submit“-Prozesse)

![gen_question_b_20](assets/gen_question_b_20.png) **Was muss der Prozessentwickler tun, damit ein Formular auf einem Gerät in HTML und auf einem Desktop in PDF gerendert werden kann?**

Nichts. Das Standard-Aktionsprofil wird automatisch ausgewählt und auch der Rendermodus wird automatisch berücksichtigt.

![gen_question_b_20](assets/gen_question_b_20.png) **Was muss getan werden, damit das Formular auf einem Desktop in HTML gerendert werden kann?**

Der Benutzer muss das HTML-Optionsfeld für das Standardprofil auswählen.

![gen_question_b_20](assets/gen_question_b_20.png) **Wirkt sich das Upgrade auf das Ändern des Verhaltens des Standardaktionsprofils aus?**

Ja, da die vorherigen dem Standardaktionsprofil zugeordneten Wiedergabe- und Sendedienste unterschiedlich waren, werden sie als Anpassung der vorhandenen Formulare behandelt. Wenn Sie auf **Standardeinstellungen wiederherstellen** klicken, werden stattdessen die Standard-Render- und Einreichungsdienste eingestellt.

Wenn Sie die vorhandenen Wiedergabe- oder Submit-PDF-Formulardienste geändert oder benutzerdefinierte Dienste (z. B. custom1) erstellt haben und jetzt dieselbe Funktion für die HTML-Wiedergabe verwenden möchten. Sie müssen den neuen Wiedergabe- oder Sendedienst replizieren (z. B. custom2) und ähnliche Anpassungen auf diese anwenden. Ändern Sie jetzt das Aktionsprofil für Ihre XDP, um mit der Verwendung von custom2-Diensten statt der benutzerdefinierten1 zum Rendern oder Senden zu beginnen.

Was muss der Prozessentwickler tun, damit ein Formular auf einem Gerät in HTML und auf einem Desktop in PDF gerendert werden kann?
Was muss der Prozessentwickler tun, damit ein Formular auf einem Gerät in HTML und auf einem Desktop in PDF gerendert werden kann?
