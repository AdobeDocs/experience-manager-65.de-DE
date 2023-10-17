---
title: Auswählen der Benutzeroberfläche in AEM
description: Konfigurieren Sie die Benutzeroberfläche, die Sie für Adobe Experience Manager 6.5 verwenden.
exl-id: 01cab3c3-4c0d-44d9-b47c-034de9a08cb1
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 42%

---

# Auswahl der Benutzeroberfläche{#selecting-your-ui}

Die Touch-optimierte Benutzeroberfläche von Adobe Experience Manager (AEM) ist jetzt die Standardbenutzeroberfläche und die Funktionsparität bei der Verwaltung und Bearbeitung von Sites wurde nahezu erreicht. Es kann jedoch vorkommen, dass der Benutzer zum [klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/classicui.md). Dazu gibt es mehrere Möglichkeiten.

>[!NOTE]
>
>Weitere Informationen zum Status der Funktionsparität mit der klassischen Benutzeroberfläche finden Sie im Dokument [Funktionsparität bei der Touch-optimierten Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md).

Es gibt verschiedene Stellen, an denen Sie definieren können, welche Benutzeroberfläche verwendet werden soll:

* [Konfigurieren der Standard-Benutzeroberfläche für Ihre Instanz](#configuring-the-default-ui-for-your-instance)
Dadurch wird die Standardbenutzeroberfläche festgelegt, die bei der Benutzeranmeldung angezeigt wird. Der Benutzer kann dies überschreiben und eine andere Benutzeroberfläche für sein Konto oder die aktuelle Sitzung auswählen.

* [Einrichten der klassischen Benutzeroberflächen-Bearbeitung für Ihr Konto](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account)
Dadurch wird die Benutzeroberfläche beim Bearbeiten von Seiten als Standard festgelegt, obwohl der Benutzer dies überschreiben und eine andere Benutzeroberfläche für sein Konto oder die aktuelle Sitzung auswählen kann.

* [Wechseln zur klassischen Benutzeroberfläche für die aktuelle Sitzung](#switching-to-classic-ui-for-the-current-session)
Wechselt zur klassischen Benutzeroberfläche für die aktuelle Sitzung.

* Im Falle von [Seitenbearbeitung, überschreibt das System bestimmte Aspekte in Bezug auf die Benutzeroberfläche](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Verschiedene Optionen zum Wechseln zur klassischen Benutzeroberfläche sind nicht sofort standardmäßig verfügbar, sondern müssen für Ihre Instanz konfiguriert werden.
>
>Weitere Informationen finden Sie unter [Aktivieren des Zugriffs auf die klassische Benutzeroberfläche](/help/sites-administering/enable-classic-ui.md).

>[!NOTE]
>
>Von einer früheren Version aktualisierte Instanzen behalten die klassische Benutzeroberfläche für die Seitenbearbeitung bei.
>
>Nach der Aktualisierung wird die Seitenbearbeitung nicht automatisch auf die Touch-optimierte Benutzeroberfläche umgestellt. Sie können dies jedoch mit dem [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** ( `AuthoringUIMode` -Dienst). Weitere Informationen dazu finden Sie unter [Benutzeroberflächenüberschreibung für den Editor](#ui-overrides-for-the-editor).

## Konfigurieren der Standard-Benutzeroberfläche für Ihre Instanz {#configuring-the-default-ui-for-your-instance}

Systemadmins können die Benutzeroberfläche konfigurieren, die beim Start und bei der Anmeldung angezeigt wird, indem sie die [Stammzuordnung](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) verwenden.

Dies kann durch Benutzerstandardeinstellungen oder Sitzungseinstellungen überschrieben werden.

## Einrichten der Seitenerstellung in der klassischen Benutzeroberfläche für Ihr Konto {#setting-classic-ui-authoring-for-your-account}

Jeder Benutzer kann auf seine eigenen [Benutzereinstellungen](/help/sites-authoring/user-properties.md#userpreferences) , um zu definieren, ob sie die klassische Benutzeroberfläche für die Seitenbearbeitung anstelle der standardmäßigen Benutzeroberfläche verwenden möchten.

Dies kann durch Sitzungseinstellungen überschrieben werden.

## Wechseln zur klassischen Benutzeroberfläche für die aktuelle Sitzung {#switching-to-classic-ui-for-the-current-session}

Bei Verwendung der Touch-optimierten Benutzeroberfläche möchten Desktop-Benutzer möglicherweise zur klassischen Benutzeroberfläche (nur Desktop) zurückkehren. Es gibt mehrere Methoden, um für die aktuelle Sitzung zur klassischen Benutzeroberfläche zu wechseln:

* **Navigations-Links**

  >[!CAUTION]
  >
  >Diese Option zum Wechseln zur klassischen Benutzeroberfläche ist nicht sofort standardmäßig verfügbar, sondern muss für Ihre Instanz konfiguriert werden.
  >
  >
  >Weitere Informationen finden Sie unter [Aktivieren des Zugriffs auf die klassische Benutzeroberfläche](/help/sites-administering/enable-classic-ui.md).

  Wenn diese Option aktiviert ist, wird jedes Mal, wenn Sie den Mauszeiger über eine entsprechende Konsole bewegen, ein Symbol (ein Monitorsymbol) angezeigt. Wenn Sie darauf tippen/klicken, wird der entsprechende Speicherort in der klassischen Benutzeroberfläche geöffnet.

  Beispielsweise die Links von **Sites** nach **siteadmin**:

  ![syui-01](assets/syui-01.png)

* **URL**

  Die klassische Benutzeroberfläche kann über die URL für den Begrüßungsbildschirm unter `welcome.html` aufgerufen werden. Beispiel:

  `https://localhost:4502/welcome.html`

  >[!NOTE]
  >
  >Die Touch-optimierte Benutzeroberfläche kann über `sites.html` aufgerufen werden. Beispiel:
  >
  >
  >`https://localhost:4502/sites.html`

### Wechseln zur klassischen Benutzeroberfläche bei der Bearbeitung einer Seite {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Diese Option zum Wechseln zur klassischen Benutzeroberfläche ist nicht sofort standardmäßig verfügbar, sondern muss für Ihre Instanz konfiguriert werden.
>
>Weitere Informationen finden Sie unter [Aktivieren des Zugriffs auf die klassische Benutzeroberfläche](/help/sites-administering/enable-classic-ui.md).

Sofern aktiviert, ist die Option **Klassische Benutzeroberfläche öffnen** im Dialogfeld **Seiteninformationen** verfügbar: 

![syui-02](assets/syui-02.png)

### Benutzeroberflächenüberschreibungen für den Editor {#ui-overrides-for-the-editor}

Die von einem Benutzer oder Systemadministrator festgelegten Einstellungen können vom System überschrieben werden, wenn Seiten bearbeitet werden.

* Beim Bearbeiten von Seiten:

   * Die Verwendung des klassischen Editors wird erzwungen, wenn die Seite über eine URL aufgerufen wird, die `cf#` enthält. Beispiel:
     `https://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Die Verwendung des Touch-optimierten Editors wird erzwungen, wenn `/editor.html` in der URL verwendet oder ein Touch-Gerät genutzt wird. Beispiel:
     `https://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Jede erzwungene Einstellung ist temporär und nur für die aktuelle Browser-Sitzung gültig.

   * Ein festgelegtes Cookie hängt davon ab, ob die Touch-Funktion ( `editor.html`) oder klassisch ( `cf#`) verwendet wird.

* Beim Öffnen von Seiten durch `siteadmin`, werden folgende Fälle geprüft:

   * dem Cookie
   * einer Benutzervoreinstellung
   * Wenn keines von beiden vorhanden ist, wird standardmäßig die im [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** ( `AuthoringUIMode` -Dienst).

>[!NOTE]
>
>Wenn [ein Benutzer bereits eine Voreinstellung für die Seitenbearbeitung definiert hat](#settingthedefaultauthoringuiforyouraccount), das nicht durch Ändern der OSGi-Eigenschaft überschrieben wird.

>[!CAUTION]
>
>Aufgrund der Verwendung von Cookies wird, wie bereits beschrieben, Folgendes nicht empfohlen:
>
>* Manuelles Bearbeiten der URL – Eine nicht-standardmäßige URL könnte zu einer unbekannten Situation und fehlender Funktionalität führen.
>* Verwenden Sie beide Editoren zur selben Zeit, z. B. in separaten Fenstern.
