---
title: Automatisches Speichern eines adaptiven Formulars
description: Sie können ein adaptives Formular so konfigurieren, dass der Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: ff9bf466-228d-40e6-9389-15c1f2ed1d2e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '736'
ht-degree: 100%

---

# Adaptives Formular automatisch speichern {#auto-save-an-adaptive-form}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

Sie können ein adaptives Formular so konfigurieren, dass der Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird.  Standardmäßig werden Inhalte eines adaptiven Formulars bei einer Benutzeraktion wie Drücken der Schaltfläche „Speichern“ gespeichert.  Die Option „Automatische Speicherung“ ist bei folgenden Aufgaben hilfreich:

* Automatisches Speichern der Inhalte für anonyme und angemeldete Benutzende
* Speichern der Inhalte eines Formulars ohne oder mit minimalem Benutzereingriff
* Speichern der Inhalte eines Formulars basierend auf einem Benutzerereignis
* Wiederholtes Speichern der Formularinhalte nach einem angegebenen Zeitintervall

## Aktivieren des automatischen Speicherns für adaptive Formulare {#enable-autosave-for-an-adaptive-form}

Die Option „Automatisches Speichern“ ist für ein adaptives Formular nicht standardmäßig aktiviert.  Sie können die Option „Automatisches Speichern“ über den Abschnitt **Automatisches Speichern** eines adaptiven Formulars aktivieren. Der Abschnitt **Automatisches Speichern** bietet mehrere weitere Konfigurationsoptionen. Führen Sie zum Aktivieren und Konfigurieren der Option „Automatisches Speichern“ für ein adaptives Formular folgende Schritte durch: 

1. Um auf den Abschnitt für das automatische Speichern in den Eigenschaften zuzugreifen, wählen Sie eine Komponente und dann ![field-level](assets/field-level.png) > **[!UICONTROL Container für adaptive Formulare]** und anschließend ![cmppr](assets/cmppr.png).
1. **[!UICONTROL Aktivieren]** Sie im Abschnitt **[!UICONTROL Automatische Speicherung]** die Option zum automatischen Speichern.
1. Geben Sie im Feld **[!UICONTROL Ereignis für adaptives Formular]** den Wert „1“ oder „TRUE“ ein, um das Formular automatisch speichern zu lassen, wenn das Formular im Browser geladen wird. Sie können außerdem einen bedingten Ausdruck für ein Ereignis angeben, bei dem, wenn es ausgelöst wird, der Status „true“ zurückgegeben und der Inhalt des Formulars gespeichert wird.
1. Geben Sie den Auslöser an. Die automatische Speicherung wird gemäß Ihrer Konfiguration ausgelöst. Ihre Optionen sind:

   * **[!UICONTROL Zeitbasiert:]** Wählen Sie diese Option, um den Inhalt anhand eines bestimmtes Zeitintervalls zu speichern.
   * **[!UICONTROL Ereignisbasiert:]** Wählen Sie diese Option, um den Inhalt beim Auslösen eines Ereignisses zu speichern.

   Wenn Sie einen Auslöser auswählen, wird das Feld „Strategiekonfiguration“ aktiviert. Mithilfe des Felds „Strategiekonfiguration“ können Sie:

   * ein Zeitintervall angeben, wenn Sie **[!UICONTROL Zeitbasiert]** für den Auslöser wählen.
   * Den Namen des Ereignisses angeben, wenn Sie **[!UICONTROL Ereignisbasiert]** für den Auslöser wählen.

   Darüber hinaus haben Sie die Möglichkeit, eine eigene benutzerdefinierte Strategie zu erstellen und diese der Liste hinzuzufügen. Weitere Informationen finden Sie unter [Implementieren einer benutzerdefinierten Strategie zum automatischen Speichern von Formularen](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Nur zeitbasierte automatische Speicherung) Führen Sie die folgenden Schritte aus, um Optionen für die zeitbasierte automatische Speicherung zu konfigurieren.

   1. Geben Sie im Feld **[!UICONTROL Automatisches Speichern für das Intervall]** das Zeitintervall in Sekunden an. Das Formular wird wiederholt gespeichert, nachdem die im Intervallfeld angegebene Anzahl an Sekunden überschritten wird.

1. (Nur ereignisbasierte automatische Speicherung) Führen Sie die folgenden Schritte aus, um Optionen für die ereignisbasierte automatische Speicherung zu konfigurieren.

   1. Geben Sie im Feld **Automatisch nach diesem Ereignis speichern** ein [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html)-Ereignis an. Das Formular wird immer dann gespeichert, wenn der Ausdruck „TRUE“ ergibt.

1. (Optional) Um den Inhalt automatisch für anonyme Benutzer zu speichern, wählen Sie die Option **Automatisches Speichern für anonyme Benutzer aktivieren** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Damit die Option zum automatischen Speichern für anonyme Benutzer funktioniert, stellen Sie sicher, dass Sie den allgemeinen Forms-Konfigurationsdienst so konfiguriert ist, dass alle Benutzer Formulare in der Vorschau anzeigen, überprüfen und zu signieren können.
   >
   >Um den Service zu konfigurieren, wechseln Sie zur Konfiguration der AEM-Web-Konsole unter `https://server:port/system/console/configMgr` und bearbeiten Sie den **[!UICONTROL allgemeinen Konfigurations-Service von Forms]** so, dass die Option **[!UICONTROL Alle Benutzer]** im Feld **[!UICONTROL Zulassen]** ausgewählt wird, und speichern Sie dann die Konfiguration.

## Implementieren einer benutzerdefinierten Strategie zum Aktivieren des automatischen Speicherns für adaptive Formulare {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

Sie können ein benutzerdefiniertes Ereignis implementieren, um die Funktion für automatisches Speichern auszulösen. Führen Sie die folgenden Schritte aus, um das benutzerdefinierte Ereignis zu erstellen und zu implementieren:

1. Erstellen Sie eine Client-Bibliothek und Client-Bibliotheksordner. Ausführliche Anweisungen finden Sie unter in [Verwenden clientseitiger Bibliotheksdokumente](/help/sites-developing/clientlibs.md). 

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

1. Wählen Sie im Bearbeitungsmodus eine Komponente, ![field-level](assets/field-level.png) > **[!UICONTROL Container für adaptive Formulare]** und dann ![cmppr](assets/cmppr.png) aus.
1. Öffnen Sie in den Eigenschaften den Abschnitt **[!UICONTROL Allgemein]**. Geben Sie im Feld **[!UICONTROL Client-Bibliothekskategorie]** den Wert der Kategorieeigenschaft ein, der beim Erstellen der Client-Bibliotheksordner definiert wurde.
1. Öffnen Sie den Abschnitt „Automatisches Speichern“. Geben Sie im Feld **[!UICONTROL Automatisch nach diesem Ereignis speichern]** ein benutzerdefiniertes Ereignis an, das in der Client-Bibliothek bereits definiert ist. Klicken Sie auf **[!UICONTROL OK]**.
