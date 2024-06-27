---
title: Verwenden der Scribble-Signatur in HTML5-Formularen
description: HTML5-Formulare werden zunehmend auf Touch-Geräten verwendet. Eine allgemeine Voraussetzung ist dabei die Unterstützung von Signaturen. Das Unterzeichnen von Dokumenten auf Mobilgeräten ist eine immer mehr gängige Form der Unterzeichnung von Formularen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
docset: aem65
feature: Forms Designer,Designer
exl-id: 2025182f-195b-40d0-aee7-67669f55b964
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '655'
ht-degree: 100%

---

# Verwenden der Scribble-Signatur in HTML5-Formularen{#using-scribble-signature-in-html-forms}

HTML5-Formulare werden zunehmend auf Touch-Geräten verwendet. Eine allgemeine Voraussetzung ist dabei die Unterstützung von Signaturen. Die Scribble-Signatur (Schreiben mit dem Eingabestift oder mit dem Finger) ist eine immer mehr gängige Form der Unterzeichnung von Formularen auf Mobilgeräten. HTML5 Forms und Designer bieten jetzt auf dem Formular ein Feld für die Scribble-Signatur. Wenn das Formular im Browser angezeigt wird, können Benutzende mit einem Eingabestift, einer Maus oder einem Finger in diesem Feld unterzeichnen.

## Entwerfen eines Formulars mit einem Feld für Scribble-Signaturen {#how-to-design-a-form-using-scribble-signature-field}

1. Öffnen Sie ein Formular in Forms Designer.
1. Ziehen das Scribble-Signatur-Feld auf die Seite.

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Die Abmessungen des in Forms Designer ausgewählten Feldes werden beim Rendern des Feldes berücksichtigt. Allerdings wird die Größe des angezeigten Unterschriftenfelds basierend auf dem Seitenverhältnis des Felds und nicht anhand der in Forms Designer festgelegten Größe berechnet.

1. Konfigurieren Sie das Freihand-Signatur-Feld.

   Beim Unterschreiben auf einem iPad werden vom Freihand-Signatur-Feld standardmäßig die geografischen Informationen als Pflichtangabe markiert. (Diese Angabe ist auf anderen Geräten optional.) Dieses Standardverhalten kann außer Kraft gesetzt werden, indem der Wert der Eigenschaft `geoLocMandatoryOnIpad` geändert wird. Diese Eigenschaft wird im Freihand-Signatur-Feld als Extra-Option geboten. So nehmen Sie eine Änderung vor:

   1. Wählen Sie im Formular das Freihand-Signatur-Feld aus.
   1. Wählen Sie die Registerkarte **XML-Quelle.**

      >[!NOTE]
      >
      >Um die Registerkarte „XML-Quelle“ zu öffnen, klicken Sie auf **Ansicht** > **XML-Quelle**.

   1. Suchen Sie das Tag `<ui>` im Tag `<field>` und ändern Sie den Quell-Code so, dass er wie folgt aussieht:

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Wählen Sie die Registerkarte **Design-Ansicht** aus. Klicken Sie im Bestätigungsfenster auf **Ja**.
   1. Speichern Sie das Formular.

1. Rendern Sie das Formular in einem unterstützten Geräte-/Desktop-Browser.

## Benutzeroberfläche für Freihand-Signaturen {#interfacing-with-the-scribble-signatures}

### Unterzeichnen {#signing}

Nachdem ein Freihand-Signatur-Feld dem Formular hinzugefügt wurde und gerendert wird, wird beim Klicken oder Tippen auf das Feld ein Dialogfeld geöffnet. Benutzende können mit einer Maus, mit dem Finger oder einem Eingabestift in einem gepunkteten Rechteckrahmen unterschreiben.

![geolocation](assets/geolocation.png)

**A.** Pinsel **B.** Radiergummi **C.** Geolocation **D.** Geografische Informationen

### Geotagging {#geo-tagging}

Wenn Sie beim Erstellen der Freihand-Signatur auf das Geolocation-Symbol klicken, werden geografische Informationen und Zeitangaben in das Feld eingebettet.

>[!NOTE]
>
Das Einbetten der geografischen Informationen ist auf einem iPad obligatorisch.

Auf einem iPad wird das Geolocation-Symbol standardmäßig nicht angezeigt. Die geografischen Informationen werden automatisch eingebettet, wenn Sie auf **OK** klicken.

Diese Einstellung kann auf iPads geändert werden, indem in den init-Parametern des Feldes der Wert des Parameters `geoLocManadatoryOnIpad` auf `0` gesetzt wird.

* Wenn die Angabe geografischer Informationen obligatorisch ist, wird den Benutzenden ein kleinerer Bereich zum Zeichnen angezeigt. Der Text mit den geografischen Informationen wird außerhalb dieses Bereichs hinzugefügt, wenn die Benutzenden auf das Symbol **OK** klicken.
* In anderen Fällen wird ihnen der komplette Bereich, in dem gezeichnet werden kann, angezeigt. Wenn die Person sich dazu entscheidet, geografische Informationen hinzuzufügen, wird die Größe des Bereichs angepasst, um den entsprechenden Text einfügen zu können.

### Löschen einer Signatur {#clearing-a-signature}

Bei dieser Funktion kann ein Benutzer auf das Symbol **Radiergummi** klicken, um den Inhalt des Felds zu löschen und von vorne zu beginnen. Wenn zuvor geografische Informationen hinzugefügt wurden, werden diese ebenfalls gelöscht.

### Speichern einer Signatur {#saving-a-signature}

Durch Klicken auf das Symbol **OK** wird die Freihand-Signatur als Bild im Feld gespeichert. Das Bild und die Werte können zur weiteren Bearbeitung an den Server gesendet werden. Sobald die Person auf **OK** geklickt hat, wird das Freihand-Signatur-Feld gesperrt. Die Unterschrift kann nicht mehr mithilfe des Freihand-Widgets bearbeitet werden.

Durch Tippen oder Klicken auf das Freihand-Feld wird das Dialogfeld im schreibgeschützten Modus geöffnet.

![3](assets/3.png)

### Auswählen der Schriftgröße {#selecting-pen-size}

Klicken Sie auf das Symbol **Pinsel**, um eine Liste der verfügbaren Stiftgrößen anzuzeigen. Klicken Sie auf eine Stiftgröße, um den entsprechenden Stift zu verwenden.

### Löschen von Signaturen aus dem Formular {#delete-signatures-from-the-form}

So löschen Sie die Signaturen aus dem Formular:

* (Mobilgeräte) Drücken Sie lange auf das Signaturfeld und wählen Sie im Bestätigungsdialogfeld die Option **Ja**.
* (Desktop) Bewegen Sie den Mauszeiger über das Signaturfeld und klicken Sie auf das Symbol **Abbrechen** und dann im Bestätigungsdialogfeld auf **Ja**.
