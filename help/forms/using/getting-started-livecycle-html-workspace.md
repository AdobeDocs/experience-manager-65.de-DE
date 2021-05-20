---
title: Erste Schritte mit AEM Forms Workspace
seo-title: Erste Schritte mit AEM Forms Workspace
description: In diesem Artikel werden die ersten Schritte zur Verwaltung der Automatisierung Ihrer Geschäftsprozesse mit LiveCycle AEM Forms Workspace beschrieben.
seo-description: In diesem Artikel werden die ersten Schritte zur Verwaltung der Automatisierung Ihrer Geschäftsprozesse mit LiveCycle AEM Forms Workspace beschrieben.
uuid: 35ca1a51-92c3-40d8-8de3-604be8704752
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: fa6e0246-6bd2-4ffb-b54c-15eda605f213
exl-id: d2a962b6-16be-4866-a856-5064f81c9610
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 82%

---

# Erste Schritte mit AEM Forms Workspace {#getting-started-with-aem-forms-workspace}

Mit AEM Forms Workspace können Sie die folgenden Aufgaben durchführen:

* Geschäftsprozess starten
* Anzeigen und Ausführen von Aufgaben, die Ihnen oder Aufgabenlisten, auf die Sie Zugriff haben, zugewiesen sind
* Verfolgen von Aufgaben, die Teil der Prozesse sind, die von Ihnen gestartet wurden bzw. an denen Sie teilnehmen

## Navigieren in AEM Forms Workspace  {#navigating-html-workspace}

Je nach dem Prozess und der Aufgabe, an der Sie arbeiten, werden in der Benutzeroberfläche von AEM Forms Workspace verschiedene Elemente angezeigt. Möglicherweise werden die Registerkarten „Zusammenfassung“, „Formulare“, „Details“, „Verlauf“, „Anlagen“ oder „Notizen“ nicht alle jederzeit angezeigt oder Sie sehen nicht alle in dieser Hilfe erwähnten Schaltflächen.

Sie können mit einer der folgenden Methoden durch die Hauptbenutzeroberfläche von AEM Forms Workspace navigieren:

* Klicken Sie auf die Elemente in der oberen Navigationsleiste, um auf den Startprozess, die Aufgabenliste, Voreinstellungen, Verfolgung, Hilfe und die Option zum Abmelden zuzugreifen.
* Klicken Sie auf die Registerkarte „Prozess starten“, „Aufgaben“ oder „Verfolgung“, um auf die drei Hauptarbeitsbereiche zuzugreifen.
* Klicken Sie auf den Registerkarten „Prozess starten“, „Aufgaben“ und „Verfolgung“ auf die Elemente in den Tabellen im linken Fensterbereich, um auf Favoriten, Prozesskategorien, Suchvorlagen, Entwürfe oder zugewiesene Aufgaben zuzugreifen. Verwenden Sie die Bildlaufleiste, um weitere Elemente in der Liste anzuzeigen.
* Alle Aktionsschaltflächen--Genehmigen, Ablehnung, Weiterleitung, Besprechen, Sperren und Freigeben--werden im Dokument und in der Eigentümerschaft angezeigt.
* Klicken Sie in der Navigationsleite am unteren Seitenrand auf das Symbol „Alle Optionen“, um die Aufgabe an einen anderen Benutzer weiterzuleiten oder für einen anderen Benutzer freizugeben, sich mit einem anderen Benutzer zu beraten oder die Aufgabe zu sperren.
* Wählen Sie auf der Registerkarte „Verlauf“ eine Aufgabe aus, um die Registerkarten „Anlagen“ und „Zuweisungen“ für die Aufgabe anzuzeigen.
* Verwenden Sie die Tabulatortaste, die Pfeiltasten und die Leertaste, um ohne Maus durch AEM Forms Workspace zu navigieren.

## Verwenden von AEM Forms Workspace mit einer Bildschirmlesehilfe {#using-html-workspace-with-screen-readers}

AEM Forms Workspace ist eine webbasierte HTML-Anwendung und mit Bildschirmlesehilfen kompatibel. Sie können über die Tastatur durch die Benutzeroberfläche von AEM Forms Workspace navigieren.

Beachten Sie die folgenden Punkte, um AEM Forms Workspace mit einer Bildschirmlesehilfe zu verwenden:

* AEM Forms Workspace ist eine standardmäßige HTML-Anwendung, die mit jedem standardmäßigen Bildschirmlesehilfen-Tool kompatibel ist. Sie benötigen kein bestimmtes Skript, um ein Bildschirmlesehilfe-Werkzeug auszuführen.
* Die gesamte Navigation in AEM Forms Workspace erfolgt über Anker-Tags, auf die über Registerkarten einfach zugegriffen werden kann.
* Das Laden von Formularen kann einige Sekunden dauern. Die Bildschirmlesehilfe zeigt nicht akustisch an, dass das Formular lädt und der Benutzer warten muss.

## Navigieren in AEM Forms Workspace über die Tastatur  {#navigating-html-workspace-using-a-keyboard}

Wenn Sie mit einer Tastatur in AEM Forms Workspace navigieren, entspricht die Navigation den HTML-Richtlinien für Barrierefreiheit. Unter bestimmten Umständen entspricht die Aktivierreihenfolge von Schaltflächen nicht den herkömmlichen Konventionen. Die folgenden Tipps erleichtern Ihnen die Navigation in der Benutzeroberfläche:

* Wenn Sie Probleme haben, die Symbolleisten oben im Browser durch Drücken der Tabulatortaste zu verlassen, drücken Sie Strg+Tabulatortaste, um in den Inhalt des Browserfensters zu gelangen.
* Die AEM Forms Workspace-Hilfe wird in einem separaten Browserfenster geöffnet. Verschieben Sie nach dem Anzeigen der Hilfe den Fokus wieder in das Browserfenster, das AEM Forms Workspace enthält. Das Hilfemenü behält den Fokus, wenn der Fokus zurückgegeben wird.
* Wenn Sie ein Formular öffnen, um einen Prozess zu starten oder eine Aufgabe abzuschließen, bleibt der Fokus im vorhandenen Element und wechselt nicht zum Formular. Verwenden Sie die Tabulatortaste, um den Fokus auf das Formular zu verschieben und es zu durchsuchen. Die Aktivierreihenfolge innerhalb des Formulars hängt vom Formulartyp und -design ab.

   Wenn Sie bei PDF-Formularen durch Drücken der Tabulatortaste bis zum Formularende springen oder das Formular übertragen, wird der Cursorfokus in die Adressleiste des Browsers verschoben. Um zu den Schaltflächen für Formularaktionen wie das Speichern als Entwurf oder das Abschließen zu gelangen, müssen Sie die Menüs erneut durch Drücken der Tabulatortaste durchgehen (nicht jedoch das gesamte Formular). Wenn das Formular noch geöffnet ist, können Sie die Schaltflächen auch überspringen und ins Formular zurückwechseln.

## Voreinstellungen verwalten {#managing-preferences}

Sie können die verschiedenen AEM Forms Workspace-Voreinstellungen in den folgenden Kategorien festlegen:

**Abwesenheit:** Mit den verfügbaren Voreinstellungen steuern Sie, wie Aufgaben während Ihrer Abwesenheit anderen Personen zugewiesen werden. Siehe [Festlegen von Abwesenheitseinstellungen](todo-lists.md#setting-out-of-office-preferences).

**Warteschlangen:** Legen Sie die Voreinstellungen zum Freigeben Ihrer Aufgabenliste für andere Benutzer oder zum Anfordern des Zugriffs auf die Liste eines anderen Benutzers fest. Siehe [Arbeiten mit Aufgaben aus Gruppen- und freigegebenen Warteschlangen](todo-lists.md#working-with-tasks-from-group-and-shared-queues).

**Benutzeroberflächeneinstellungen:** Legen Sie Voreinstellungen für die Arbeit mit AEM Forms Workspace fest. Siehe [Festlegen von Benutzeroberflächeneinstellungen](#set-user-interface-preferences).

### Benutzeroberflächen-Voreinstellungen festlegen  {#set-user-interface-preferences}

Legen Sie die Benutzeroberflächenvoreinstellungen auf der Registerkarte „UI-Einstellungen“ fest. Die folgenden Voreinstellungen sind verfügbar.

* **Startposition:** Gibt die Seite an, die beim Anmelden bei AEM Forms Workspace angezeigt wird. Die vier verfügbaren Optionen sind: „Prozess starten“, „Aufgaben“, „Verfolgung“ und „Favoriten“.
* **Abmeldeaufforderung:** Gibt an, ob Sie nach dem Klicken auf „Abmelden“ aufgefordert werden, den Abmeldevorgang zu bestätigen.
* **Datumsformat:** Gibt das Anzeigeformat für das Datum an, das in AEM Forms Workspace verwendet wird.
* **Zeitformat:** Gibt das Anzeigeformat für die Zeit an, das in AEM Forms Workspace verwendet wird.
* **Über Aufgabenereignisse per E-Mail benachrichtigen:** Gibt an, ob Sie E-Mail-Benachrichtigungen für Aufgabenereignisse erhalten, einschließlich Aufgabenzuweisungen, Erinnerungen und Terminen in Ihrer persönlichen Aufgabenliste oder in Gruppenaufgabenlisten, denen Sie zugewiesen sind.
* **Formulare in E-Mail anfügen:** Gibt an, ob eine Kopie des Formulars in E-Mail-Benachrichtigungen angefügt wird. Anlagen werden nur für PDF- und XDP-Formulare unterstützt.
* **Entwurf regelmäßig speichern:** Gibt an, ob Ihre Formularentwürfe regelmäßig automatisch gespeichert werden. Um Ihre Entwürfe in regelmäßigen Abständen zu speichern, aktivieren Sie diese Option und legen Sie die Dauer der automatischen Speicherung von 1 bis 30 Minuten fest. Wenn die automatische Speicherung aktiviert ist und ein Benutzer an einem Entwurf arbeitet, wird der Entwurf regelmäßig nach einer bestimmten Anzahl von Minuten gespeichert. Der Entwurf wird nur automatisch gespeichert, wenn er seit der letzten Speicherung oder automatischen Speicher geändert wurde. Wenn der Entwurf gespeichert wurde, erscheint eine Warnmeldung auf dem Bildschirm.
