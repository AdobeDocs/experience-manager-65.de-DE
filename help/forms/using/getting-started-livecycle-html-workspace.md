---
title: Erste Schritte mit AEM Forms Workspace
seo-title: Getting started with AEM Forms workspace
description: Erste Schritte mit der Verwendung des LiveCycle AEM Forms Workspace zur Verwaltung Ihrer Automatisierungsprozesse.
seo-description: How to get started with using the LiveCycle AEM Forms workspace to manage your business automation processes.
uuid: 35ca1a51-92c3-40d8-8de3-604be8704752
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: fa6e0246-6bd2-4ffb-b54c-15eda605f213
exl-id: d2a962b6-16be-4866-a856-5064f81c9610
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 30%

---

# Erste Schritte mit AEM Forms Workspace {#getting-started-with-aem-forms-workspace}

Sie können AEM Forms Workspace verwenden, um die folgenden Aufgaben auszuführen:

* Geschäftsprozess starten
* Anzeigen und Bearbeiten von Aufgaben, die Ihnen oder anderen Aufgabenlisten zugewiesen sind, auf die Sie Zugriff haben
* Verfolgen von Aufgaben, die Teil der Prozesse sind, die Sie gestartet haben oder an denen Sie beteiligt waren

## Navigieren in AEM Forms Workspace {#navigating-html-workspace}

Welche Elemente in der Benutzeroberfläche von AEM Forms Workspace angezeigt werden, ist je nach dem Prozess oder der Aufgabe, den bzw. die Sie gerade durchführen, unterschiedlich. Möglicherweise werden die Registerkarten „Zusammenfassung“, „Formulare“, „Details“, „Verlauf“, „Anlagen“ oder „Notizen“ nicht alle jederzeit angezeigt oder Sie sehen nicht alle in dieser Hilfe erwähnten Schaltflächen.

Mit den folgenden Methoden können Sie in der Hauptbenutzeroberfläche von AEM Forms Workspace navigieren:

* Klicken Sie auf die Elemente in der oberen Navigationsleiste, um auf die Option &quot;Prozess starten&quot;, &quot;Aufgabenliste&quot;, &quot;Voreinstellungen&quot;, &quot;Tracking&quot;, &quot;Hilfe&quot;und &quot;Abmelden&quot;zuzugreifen.
* Klicken Sie auf die Registerkarte &quot;Prozess starten&quot;, &quot;Aufgaben&quot;oder &quot;Verfolgung&quot;, um auf die drei Hauptarbeitsbereiche zuzugreifen.
* Klicken Sie auf den Registerkarten Prozess starten, Aufgaben und Verfolgung auf die Elemente in der Liste im linken Bereich, um auf Favoriten, Prozesskategorien, Suchvorlagen, Entwürfe oder zugewiesene Aufgaben zuzugreifen. Verwenden Sie die Bildlaufleiste, um zusätzliche Elemente in der Liste anzuzeigen.
* Alle Aktionsschaltflächen - Genehmigen, Ablehnen, Weiterleiten, Besprechen, Sperren und Freigeben - werden sowohl im Dokument als auch im Eigentum angezeigt.
* Klicken Sie in der Navigationsleiste unten auf der Seite auf das Symbol Alle Optionen , um die Aufgabe an einen anderen Benutzer weiterzuleiten, sie für einen anderen Benutzer freizugeben, die Aufgabe mit einem anderen Benutzer zu besprechen oder die Aufgabe zu sperren.
* Wählen Sie auf der Registerkarte Verlauf eine Aufgabe aus, um die Registerkarten Anhänge und Zuweisungen für diese Aufgabe anzuzeigen.
* Verwenden Sie die Tabulatortaste, die Pfeiltasten und die Leertaste, um in AEM Forms Workspace zu navigieren, ohne eine Maus zu verwenden.

## Verwenden von AEM Forms Workspace mit einer Bildschirmlesehilfe {#using-html-workspace-with-screen-readers}

AEM Forms Workspace ist eine webbasierte HTML-Anwendung und mit Sprachausgabeprogrammen kompatibel. Sie können mit der Tastatur in der Benutzeroberfläche von AEM Forms Workspace navigieren.

Beachten Sie bei der Verwendung von AEM Forms Workspace mit einem Sprachausgabeprogramm folgende Punkte:

* AEM Forms Workspace ist eine Standard-HTML-Anwendung, die mit jedem standardmäßigen Sprachausgabeprogramm kompatibel ist. Sie benötigen kein bestimmtes Skript, um ein Bildschirmlesehilfe-Werkzeug auszuführen.
* Die gesamte Navigation in AEM Forms Workspace erfolgt durch Anker-Tags, auf die leicht über Registerkarten zugegriffen werden kann.
* Das Laden von Forms kann einige Sekunden dauern. Die Bildschirmlesehilfe informiert Sie nicht hörbar darüber, dass das Formular geladen wird und Sie warten müssen.

## Navigieren in AEM Forms Workspace über eine Tastatur {#navigating-html-workspace-using-a-keyboard}

Bei der Navigation in AEM Forms Workspace mit der Tastatur gelten die Konventionen für HTML-Ein-/Ausgabehilfen. In bestimmten Situationen entspricht die Tab-Reihenfolge nicht der üblichen herkömmlichen Reihenfolge. Die folgenden Tipps helfen Ihnen beim Navigieren in der Benutzeroberfläche:

* Wenn Sie Probleme haben, die Symbolleisten am oberen Rand des Browsers mit dem Tabulator zu verlassen, drücken Sie Strg+Tab, um den Inhalt des Browser-Fensters zu öffnen.
* Die AEM Forms Workspace-Hilfe wird in einem separaten Browser-Fenster geöffnet. Nachdem Sie die Hilfe angezeigt haben, kehrt der Fokus zum Browserfenster zurück, das AEM Forms Workspace enthält. Das Hilfemenü bleibt konzentriert, wenn der Fokus zurückgegeben wird.
* Wenn Sie ein Formular öffnen, um einen Prozess zu starten oder eine Aufgabe abzuschließen, bleibt der Fokus beim vorhandenen Element und ändert sich nicht in das Formular. Verwenden Sie die Registerkarte , um den Fokus auf das Formular zu verschieben und es zu durchsuchen. Die Tab-Reihenfolge im Formular hängt vom Typ und Design des Formulars ab.

  Bei PDF forms springt der Cursorfokus beim Drücken der Tabulatortaste bis zum Formularende oder beim Senden des Formulars zur Adressleiste des Browsers. Navigieren Sie erneut durch die Menüs (aber nicht durch das gesamte Formular), um zu den Formularaktionsschaltflächen wie &quot;Als Entwurf speichern&quot;und &quot;Fertig stellen&quot;zu wechseln. Wenn das Formular noch geöffnet ist, können Sie auch die Schaltflächen überspringen und in das Formular zurückwechseln.

## Verwalten von Voreinstellungen {#managing-preferences}

Sie können die verschiedenen AEM Forms Workspace-Voreinstellungen in den folgenden Kategorien festlegen:

**Abwesenheit:** Legen Sie Voreinstellungen fest, um zu steuern, wie Aufgaben während Ihrer Abwesenheit anderen Personen zugewiesen werden. Siehe [Abwesenheitseinstellungen festlegen](todo-lists.md#setting-out-of-office-preferences).

**Warteschlangen:** Legen Sie Voreinstellungen für die Freigabe Ihrer Aufgabenliste für andere Benutzer oder für die Anforderung des Zugriffs auf die Liste eines anderen Benutzers fest. Siehe [Arbeiten mit Aufgaben aus Gruppen- und freigegebenen Warteschlangen](todo-lists.md#working-with-tasks-from-group-and-shared-queues).

**Benutzeroberflächeneinstellungen:** Legen Sie Voreinstellungen für die Arbeit mit AEM Forms Workspace fest. Siehe [Festlegen von Benutzeroberflächen-Voreinstellungen](#set-user-interface-preferences).

### Festlegen von Benutzeroberflächen-Voreinstellungen {#set-user-interface-preferences}

Legen Sie die Benutzeroberflächenvoreinstellungen auf der Registerkarte Voreinstellungen > Benutzeroberflächeneinstellungen fest. Die folgenden Voreinstellungen sind verfügbar.

* **Startposition:** Gibt die Seite an, die beim Anmelden bei AEM Forms Workspace angezeigt wird. Die vier verfügbaren Optionen sind: „Prozess starten“, „Aufgaben“, „Verfolgung“ und „Favoriten“.
* **Abmeldeaufforderung:** Gibt an, ob Sie nach dem Klicken auf „Abmelden“ aufgefordert werden, den Abmeldevorgang zu bestätigen.
* **Datumsformat:** Gibt das Anzeigeformat des Datums an, das in AEM Forms Workspace verwendet wird.
* **Zeitformat**: Gibt das Anzeigeformat der Zeit an, das in AEM Forms Workspace verwendet wird.
* **Benachrichtigung über Aufgabenereignisse per E-Mail:** Gibt an, ob Sie E-Mail-Benachrichtigungen für Aufgabenereignisse erhalten, einschließlich Aufgabenzuweisungen, Erinnerungen und Terminen für Aufgaben in Ihrer Aufgabenliste und in Gruppenaufgabenlisten, zu denen Sie gehören.
* **Forms in E-Mail anhängen:** Gibt an, ob eine Kopie des Formulars an E-Mail-Benachrichtigungen angehängt wird. Anhänge werden nur für PDF- und XDP-Formulare unterstützt.
* **Entwurf regelmäßig speichern:** Gibt an, ob Ihre Formularentwürfe regelmäßig automatisch gespeichert werden. Um Ihre Entwürfe regelmäßig zu speichern, aktivieren Sie diese Option und legen Sie die Dauer für das automatische Speichern von 1 bis 30 Minuten fest. Wenn die automatische Speicherung aktiviert ist und ein Benutzer an einem Entwurf arbeitet, wird der Entwurf regelmäßig nach der angegebenen Anzahl von Minuten gespeichert. Der Entwurf wird nur dann automatisch gespeichert, wenn der Entwurf seit dem letzten Speichern oder automatischen Speichern geändert wurde. Wenn der Entwurf gespeichert wurde, erscheint eine Warnmeldung auf dem Bildschirm.
