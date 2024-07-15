---
title: Erste Schritte mit AEM Forms Workspace
description: Erfahren Sie mehr zu den ersten Schritten, die erforderlich sind, um LiveCycle AEM Forms Workspace zum Verwalten geschäftlicher Automatisierungsprozesse zu verwenden.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: d2a962b6-16be-4866-a856-5064f81c9610
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 100%

---

# Erste Schritte mit AEM Forms Workspace {#getting-started-with-aem-forms-workspace}

Mit AEM Forms Workspace können Sie die folgenden Aufgaben durchführen:

* Starten eines Geschäftsprozesses
* Anzeigen und Ausführen von Aufgaben, die Ihnen oder anderen Aufgabenlisten, auf die Sie Zugriff haben, zugewiesen sind
* Verfolgen von Aufgaben, die Teil der Prozesse sind, die von Ihnen gestartet wurden bzw. an denen Sie beteiligt waren

## Navigieren in AEM Forms Workspace {#navigating-html-workspace}

Welche Elemente in der Benutzeroberfläche von AEM Forms Workspace angezeigt werden, ist je nach dem Prozess oder der Aufgabe, den bzw. die Sie gerade durchführen, unterschiedlich. Möglicherweise werden die Registerkarten „Zusammenfassung“, „Formulare“, „Details“, „Verlauf“, „Anlagen“ oder „Notizen“ nicht alle jederzeit angezeigt oder Sie sehen nicht alle in dieser Hilfe erwähnten Schaltflächen.

Mit den folgenden Methoden können Sie in der Hauptbenutzeroberfläche von AEM Forms Workspace navigieren:

* Klicken Sie auf die Elemente in der oberen Navigationsleiste, um auf die Option für den Prozessstart, die Aufgabenliste, Voreinstellungen, Verfolgung, Hilfe und Abmeldung zuzugreifen.
* Klicken Sie auf die Registerkarte „Prozess starten“, „Aufgaben“ oder „Tracking“, um auf die drei Hauptarbeitsbereiche zuzugreifen.
* Klicken Sie auf den Registerkarten „Prozess starten“, „Aufgaben“ und „Tracking“ auf die Elemente in den Tabellen im linken Bedienfeld, um auf Favoriten, Prozesskategorien, Suchvorlagen, Entwürfe oder zugewiesene Aufgaben zuzugreifen. Verwenden Sie die Bildlaufleiste, um weitere Elemente in der Liste anzuzeigen.
* Alle Aktionsschaltflächen („Genehmigen“, „Ablehnen“, „Weiterleiten“, „Besprechen“, „Sperren“ und „Freigeben“) werden im Dokument und in der Eigentümerschaft angezeigt.
* Klicken Sie in der Navigationsleiste am unteren Seitenrand auf das Symbol „Alle Optionen“, um die Aufgabe an eine andere Person weiterzuleiten, für eine andere Person freizugeben, sich mit einer anderen Person zu besprechen oder die Aufgabe zu sperren.
* Wählen Sie auf der Registerkarte „Verlauf“ eine Aufgabe aus, um die Registerkarten „Anlagen“ und „Zuweisungen“ für die Aufgabe anzuzeigen.
* Verwenden Sie die Tabulatortaste, die Pfeiltasten und die Leertaste, um in AEM Forms Workspace zu navigieren, ohne eine Maus zu verwenden.

## Verwenden von AEM Forms Workspace mit einer Bildschirmlesehilfe {#using-html-workspace-with-screen-readers}

AEM Forms Workspace ist eine webbasierte HTML-Anwendung und mit Sprachausgabeprogrammen kompatibel. Sie können mit der Tastatur in der Benutzeroberfläche von AEM Forms Workspace navigieren.

Beachten Sie bei der Verwendung von AEM Forms Workspace mit einem Sprachausgabeprogramm folgende Punkte:

* AEM Forms Workspace ist eine Standard-HTML-Anwendung, die mit jedem standardmäßigen Sprachausgabeprogramm kompatibel ist. Sie benötigen kein bestimmtes Skript, um ein Bildschirmlesehilfe-Werkzeug auszuführen.
* Die gesamte Navigation in AEM Forms Workspace erfolgt durch Anker-Tags, auf die leicht über Registerkarten zugegriffen werden kann.
* Das Laden von Formularen kann einige Sekunden dauern. Die Bildschirmlesehilfe zeigt nicht akustisch an, dass das Formular geladen wird und Sie warten müssen.

## Navigieren in AEM Forms Workspace über die Tastatur {#navigating-html-workspace-using-a-keyboard}

Bei der Navigation in AEM Forms Workspace mit der Tastatur gelten die Konventionen für HTML-Ein-/Ausgabehilfen. Unter bestimmten Umständen entspricht die Aktivierreihenfolge von Schaltflächen nicht den herkömmlichen Konventionen. Die folgenden Tipps helfen Ihnen bei der Navigation in der Benutzeroberfläche:

* Wenn Sie Probleme haben, die Symbolleisten oben im Browser durch Drücken der Tabulatortaste zu verlassen, drücken Sie Strg+Tab, um in den Inhalt des Browser-Fensters zu gelangen.
* Die AEM Forms Workspace-Hilfe wird in einem separaten Browser-Fenster geöffnet. Verschieben Sie nach dem Anzeigen der Hilfe den Fokus wieder in das Browser-Fenster, das AEM Forms Workspace enthält. Das Hilfemenü behält den Fokus, wenn der Fokus zurückgegeben wird.
* Wenn Sie ein Formular öffnen, um einen Prozess zu starten oder eine Aufgabe abzuschließen, bleibt der Fokus beim vorhandenen Element und wechselt nicht zum Formular. Verwenden Sie die Tabulatortaste, um den Fokus auf das Formular zu verschieben und es zu durchsuchen. Die Aktivierreihenfolge innerhalb des Formulars hängt vom Formulartyp und -entwurf ab.

  Wenn Sie bei PDF-Formularen durch Drücken der Tabulatortaste bis zum Formularende springen oder das Formular absenden, wechselt der Fokus des Cursors in die Adressleiste des Browsers. Um zu den Schaltflächen für Formularaktionen wie „Als Entwurf speichern“ oder „Abschließen“ zu gelangen, durchlaufen Sie die Menüs erneut durch Drücken der Tabulatortaste (nicht jedoch das gesamte Formular). Wenn das Formular noch geöffnet ist, können Sie die Schaltflächen auch überspringen und ins Formular zurückwechseln.

## Verwalten von Voreinstellungen {#managing-preferences}

Sie können die verschiedenen AEM Forms Workspace-Voreinstellungen in den folgenden Kategorien festlegen:

**Abwesenheit:** Mit den verfügbaren Voreinstellungen steuern Sie, wie Aufgaben während Ihrer Abwesenheit anderen Personen zugewiesen werden. Siehe [Festlegen von Abwesenheitseinstellungen](todo-lists.md#setting-out-of-office-preferences).

**Warteschlangen:** Legen Sie die Voreinstellungen zum Freigeben Ihrer Aufgabenliste für andere Benutzende oder zum Anfordern des Zugriffs auf die Liste einer anderen Person fest. Siehe [Arbeiten mit Aufgaben aus Gruppen- und freigegebenen Warteschlangen](todo-lists.md#working-with-tasks-from-group-and-shared-queues)

**Benutzeroberflächeneinstellungen:** Legen Sie Voreinstellungen für die Arbeit mit AEM Forms Workspace fest. Siehe [Festlegen von Benutzeroberflächeneinstellungen](#set-user-interface-preferences).

### Festlegen von Benutzeroberflächeneinstellungen {#set-user-interface-preferences}

Legen Sie die Benutzeroberflächeneinstellungen auf der Registerkarte „Voreinstellungen“ > „Benutzeroberflächeneinstellungen“ fest. Die folgenden Voreinstellungen sind verfügbar.

* **Startposition:** Gibt die Seite an, die beim Anmelden bei AEM Forms Workspace angezeigt wird. Die vier verfügbaren Optionen sind: „Prozess starten“, „Aufgaben“, „Verfolgung“ und „Favoriten“.
* **Abmeldeaufforderung:** Gibt an, ob Sie nach dem Klicken auf „Abmelden“ aufgefordert werden, den Abmeldevorgang zu bestätigen.
* **Datumsformat:** Gibt das Anzeigeformat für das Datum an, das in AEM Forms Workspace verwendet wird.
* **Zeitformat:** Gibt das Anzeigeformat für die Zeit an, das in AEM Forms Workspace verwendet wird.
* **Über Aufgabenereignisse per E-Mail benachrichtigen:** Gibt an, ob Sie E-Mail-Benachrichtigungen für Aufgabenereignisse erhalten, einschließlich Aufgabenzuweisungen, Erinnerungen und Terminen in Ihrer persönlichen Aufgabenliste oder in Gruppenaufgabenlisten, denen Sie zugewiesen sind.
* **Formulare in E-Mail anfügen:** Gibt an, ob eine Kopie des Formulars in E-Mail-Benachrichtigungen angefügt wird. Anlagen werden nur für PDF- und XDP-Formulare unterstützt.
* **Entwurf regelmäßig speichern:** Gibt an, ob Ihre Formularentwürfe regelmäßig automatisch gespeichert werden. Aktivieren Sie diese Option, damit Ihre Entwürfe in regelmäßigen Abständen gespeichert werden, und legen Sie die Frequenz der automatischen Speicherung von 1 bis 30 Minuten fest.  Wenn die automatische Speicherung aktiviert ist und Sie an einem Entwurf arbeiten, wird der Entwurf regelmäßig nach der angegebenen Anzahl von Minuten gespeichert.  Der Entwurf wird nur dann automatisch gespeichert, wenn sich seit der letzten manuellen oder automatischen Speicherung etwas geändert hat.  Wenn der Entwurf gespeichert wurde, erscheint eine Warnmeldung auf dem Bildschirm.
