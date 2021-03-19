---
title: Adaptives Formular automatisch speichern
seo-title: Adaptives Formular automatisch speichern
description: Sie können ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird.
seo-description: Sie können ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird.
uuid: 0fe9a389-269b-438a-9489-d9d1d09558a1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: d519ac4e-6d29-4a69-874e-792acabe87ff
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 88%

---


# Adaptives Formular automatisch speichern {#auto-save-an-adaptive-form}

Sie können ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird. Standardmäßig werden Inhalte eines adaptiven Formulars bei einer Benutzeraktion wie Drücken der Schaltfläche „Speichern“ gespeichert. Die Option „Automatisches Speichern“ ist bei folgenden Aufgaben hilfreich:

* Automatisches Speichern der Inhalte für anonym und angemeldete Benutzer
* Speichern der Inhalte eines Formulars ohne oder mit minimalem Benutzereingriff
* Speichern von Inhalten eines Formulars basierend auf einem Ereignis starten
* Wiederholtes Speichern von Formularinhalten nach einem angegebenen Zeitintervall

## Automatisches Speichern für adaptives Formular ermöglichen {#enable-autosave-for-an-adaptive-form}

Für ein adaptives Formular ist die Option „Automatisches Speichern“ nicht standardmäßig aktiviert. Sie können die Option „Automatisches Speichern“ über den Abschnitt **Automatisches Speichern** eines adaptiven Formulars aktivieren. Der Abschnitt **Automatisches Speichern** bietet mehrere weitere Konfigurationsoptionen. Führen Sie zum Aktivieren und Konfigurieren der Option „Automatisches Speichern“ für ein adaptives Formular folgende Schritte durch: 

1. Um auf den Abschnitt zum automatischen Speichern in den Eigenschaften zuzugreifen, wählen Sie eine Komponente aus, tippen Sie dann auf ![Feldebene](assets/field-level.png) > **[!UICONTROL Container des adaptiven Formulars]** und dann auf ![cmppr](assets/cmppr.png).
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

   1. Geben Sie im Feld **Nach diesem Ereignis automatisch speichern** ein [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html)-Ereignis ein. Das Formular wird immer dann gespeichert, wenn der Ausdruck „TRUE“ ergibt.

1. (Optional) Um den Inhalt automatisch für anonyme Benutzer zu speichern, wählen Sie die Option **Automatisches Speichern für anonyme Benutzer aktivieren** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Damit die Option zum automatischen Speichern für anonyme Benutzer funktioniert, stellen Sie sicher, dass Sie den allgemeinen Forms-Konfigurationsdienst so konfiguriert ist, dass alle Benutzer Formulare in der Vorschau anzeigen, überprüfen und zu signieren können.
   >
   >Um den Dienst zu konfigurieren, wechseln Sie zu AEM Web-Konsolenkonfiguration unter `https://server:port/system/console/configMgr` und bearbeiten Sie **[!UICONTROL Forms Common Configuration Service]**, um die Option **[!UICONTROL All Users]** im Feld **[!UICONTROL Allow]** auszuwählen und speichern Sie die Konfiguration.

## Implementieren einer benutzerdefinierten Strategie, um automatisches Speichern für adaptive Formulare zu aktivieren {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

Sie können ein benutzerdefiniertes Ereignis implementieren, um die Funktion für automatisches Speichern auszulösen. Führen Sie die folgenden Schritte aus, um das benutzerdefinierte Ereignis zu implementieren.

1. Erstellen Sie die Clientbibliothek und Clientbibliotheksordner. Ausführliche Anweisungen finden Sie unter  in [ Verwenden clientseitiger Bibliotheksdokumente](/help/sites-developing/clientlibs.md). 

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

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, tippen Sie dann auf ![Feldebene](assets/field-level.png) > **[!UICONTROL Container für adaptive Formulare]** und dann auf ![cmppr](assets/cmppr.png).
1. In den Eigenschaften öffnen Sie den Abschnitt **[!UICONTROL Einfach]**. Geben Sie im Feld **[!UICONTROL Client-Bibliothekskategorie]** den Wert der Kategorieeigenschaft ein, der beim Erstellen der Clientbibliotheksordner definiert wurde.
1. Öffnen Sie den Abschnitt „Automatisches Speichern“. Geben Sie im Feld **[!UICONTROL Nach diesem Ereignis automatisch speichern]** ein benutzerdefiniertes Ereignis an, das in der Clientbibliothek bereits definiert ist. Klicken Sie auf **[!UICONTROL OK]**.

