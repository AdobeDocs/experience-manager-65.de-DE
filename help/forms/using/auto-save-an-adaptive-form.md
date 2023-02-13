---
title: Automatisches Speichern eines adaptiven Formulars
seo-title: Auto-save an adaptive form
description: Sie können ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird.
seo-description: You can configure an adaptive form to automatically start saving the content based on an event or a pre-defined time-interval
uuid: 0fe9a389-269b-438a-9489-d9d1d09558a1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: d519ac4e-6d29-4a69-874e-792acabe87ff
feature: Adaptive Forms
exl-id: 948b2c12-895d-49e3-a943-d8fe87174fc4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '688'
ht-degree: 100%

---

# Adaptives Formular automatisch speichern {#auto-save-an-adaptive-form}

Sie können ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird. Standardmäßig werden Inhalte eines adaptiven Formulars bei einer Benutzeraktion wie Drücken der Schaltfläche „Speichern“ gespeichert. Die Option „Automatisches Speichern“ ist bei folgenden Aufgaben hilfreich:

* Automatisches Speichern der Inhalte für anonym und angemeldete Benutzer
* Speichern der Inhalte eines Formulars ohne oder mit minimalem Benutzereingriff
* Speichern von Inhalten eines Formulars basierend auf einem Ereignis starten
* Wiederholtes Speichern von Formularinhalten nach einem angegebenen Zeitintervall

## Automatisches Speichern für adaptives Formular ermöglichen {#enable-autosave-for-an-adaptive-form}

Für ein adaptives Formular ist die Option „Automatisches Speichern“ nicht standardmäßig aktiviert. Sie können die Option „Automatisches Speichern“ über den Abschnitt **Automatisches Speichern** eines adaptiven Formulars aktivieren. Der Abschnitt **Automatisches Speichern** bietet mehrere weitere Konfigurationsoptionen. Führen Sie zum Aktivieren und Konfigurieren der Option „Automatisches Speichern“ für ein adaptives Formular folgende Schritte durch: 

1. Um auf den Abschnitt für das automatische Speichern in den Eigenschaften zuzugreifen, wählen Sie eine Komponente aus und tippen Sie auf ![Feldebene](assets/field-level.png) > **[!UICONTROL Container für ein adaptives Formular]** und anschließend auf ![cmppr](assets/cmppr.png).
1. Im Abschnitt **[!UICONTROL Automatisches Speichern]** **[!UICONTROL aktivieren]** Sie die Option zum automatischen Speichern.
1. Geben Sie im Feld **[!UICONTROL Adaptives Formular-Ereignis]** 1 oder TRUE ein, um das Formular automatisch zu speichern, wenn das Formular im Browser geladen wird. Sie können außerdem einen bedingten Ausdruck für ein Ereignis angeben, das, wenn es ausgelöst wird, den Status „true“ zurückgibt und den Inhalt des Formulars speichert.
1. Geben Sie den Auslöser an. Die automatische Speicherung wird gemäß Ihrer Konfiguration ausgelöst. Ihre Optionen sind:

   * **[!UICONTROL Zeitbasiert:]** Wählen Sie diese Option, um den Inhalt anhand eines bestimmtes Zeitintervalls zu speichern.
   * **[!UICONTROL Ereignisbasiert:]** Wählen Sie diese Option, um den Inhalt beim Auslösen eines Ereignisses zu speichern.

   Wenn Sie einen Auslöser auswählen, wird das Feld „Strategiekonfiguration“ aktiviert. Mithilfe der Strategiekonfiguration können Sie:

   * ein Zeitintervall angeben, wenn Sie **[!UICONTROL Zeitbasiert]** für den Auslöser wählen.
   * Den Namen des Ereignisses angeben, wenn Sie **[!UICONTROL Ereignisbasiert]** für den Auslöser wählen.

   Darüber hinaus haben Sie die Möglichkeit, eine eigene benutzerdefinierte Strategie zu erstellen und diese der Liste hinzuzufügen. Weitere Informationen finden Sie unter [Implementieren einer benutzerdefinierten Strategie](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Nur zeitbasiertes automatisches Speichern) Führen Sie die folgenden Schritte aus, um serverseitige Protokolle zu konfigurieren:

   1. Geben Sie im Feld **[!UICONTROL In diesem Intervall automatisch speichern]** den Zeitintervall in Sekunden an. Das Formular wird wiederholt gespeichert, nachdem die im Intervallfeld angegebene Anzahl an Sekunden überschritten wird.

1. (Nur ereignisbasiertes automatisches Speichern) Führen Sie die folgenden Schritte aus, um Optionen für ereignisbasiertes automatisches Speichern zu konfigurieren.

   1. Geben Sie im Feld **Automatisch nach diesem Ereignis speichern** ein [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html)-Ereignis an. Das Formular wird immer dann gespeichert, wenn der Ausdruck „TRUE“ ergibt.

1. (Optional) Um den Inhalt automatisch für anonyme Benutzer zu speichern, wählen Sie die Option **Automatisches Speichern für anonyme Benutzer aktivieren** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Damit die Option zum automatischen Speichern für anonyme Benutzer funktioniert, stellen Sie sicher, dass Sie den allgemeinen Forms-Konfigurationsdienst so konfiguriert ist, dass alle Benutzer Formulare in der Vorschau anzeigen, überprüfen und zu signieren können.
   >
   >Um den Service zu konfigurieren, wechseln Sie zur Konfiguration der AEM-Web-Konsole unter `https://server:port/system/console/configMgr` und bearbeiten Sie den **[!UICONTROL allgemeinen Konfigurations-Service von Forms]** so, dass die Option **[!UICONTROL Alle Benutzer]** im Feld **[!UICONTROL Zulassen]** ausgewählt wird, und speichern Sie dann die Konfiguration.

## Implementieren einer benutzerdefinierten Strategie, um automatisches Speichern für adaptive Formulare zu aktivieren {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

Sie können ein benutzerdefiniertes Ereignis implementieren, um die Funktion für automatisches Speichern auszulösen. Führen Sie die folgenden Schritte aus, um das benutzerdefinierte Ereignis zu implementieren.

1. Erstellen Sie die Clientbibliothek und Clientbibliotheksordner. Ausführliche Anweisungen finden Sie unter in [Verwenden clientseitiger Bibliotheksdokumente](/help/sites-developing/clientlibs.md). 

   Beispiel: Das folgende Skript verwendet das benutzerdefinierte Ereignis `emailFocusChange`, um die Funktion für automatisches Speichern auszulösen:

   ```javascript
   window.addEventListener("bridgeInitializeStart", function (){
       guideBridge.connect(function () { guideBridge.on("elementFocusChanged", function (event,data) {
           if(data.target.name === 'Email') {
               guideBridge.trigger("emailFocusChange");
           }
       });
      });
   });
   ```

   >[!NOTE]
   >
   >Eine Kategorieeigenschaft wird beim Erstellen von Clientbibliothekordnern definiert. Halten Sie den der Kategorieeigenschaft zugewiesenen Wert bereit.

1. Öffnen Sie das adaptive Formular im Authoring-Modus.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und tippen Sie anschließend auf ![field-level](assets/field-level.png) > **[!UICONTROL Container für ein adaptives Formular]** und dann auf ![cmppr](assets/cmppr.png).
1. In den Eigenschaften öffnen Sie den Abschnitt **[!UICONTROL Einfach]**. Geben Sie im Feld **[!UICONTROL Client-Bibliothekskategorie]** den Wert der Kategorieeigenschaft ein, der beim Erstellen der Clientbibliotheksordner definiert wurde.
1. Öffnen Sie den Abschnitt „Automatisches Speichern“. Geben Sie im Feld **[!UICONTROL Nach diesem Ereignis automatisch speichern]** ein benutzerdefiniertes Ereignis an, das in der Clientbibliothek bereits definiert ist. Klicken Sie auf **[!UICONTROL OK]**.
