---
title: Auditprotokollwartung in AEM 6
seo-title: Audit Log Maintenance in AEM 6
description: Erfahren Sie mehr über die Auditprotokollwartung in Adobe Experience Manager (AEM).
seo-description: Learn about Audit Log Maintenance in Adobe Experience Manager (AEM).
uuid: 212de4df-6bf4-434c-94e1-74186d21945a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 565d89de-b3ca-41a5-8e1c-d10905c25fb5
exl-id: 1e05faf5-619a-4ea3-acbf-2fd37c71e6d2
feature: Operations
source-git-commit: c7c32130a3257c14c98b52f9db31d80587d7993a
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 54%

---

# Auditprotokollwartung in AEM 6{#audit-log-maintenance-in-aem}

AEM Ereignisse, die für die Prüfprotokollierung qualifiziert sind, generieren viele archivierte Daten. Diese Datenmenge kann aufgrund von Replikationen, Asset-Uploads und anderen Systemaktivitäten schnell anwachsen.

Die Wartung des Auditprotokolls umfasst verschiedene Funktionsbereiche, mit denen die Wartung von Auditprotokollen unter bestimmten Richtlinien automatisiert werden kann.

Es wird als konfigurierbare wöchentliche Wartungsaufgabe implementiert und kann über die Überwachungskonsole des Vorgangs-Dashboards aufgerufen werden.

Weitere Informationen finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

Es gibt drei Arten von Optionen zur Auditprotokolllöschung:

1. [Seiten-Auditprotokolllöschung](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM-Auditprotokolllöschung](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [Replikations-Auditprotokolllöschung](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

Jede der Optionen kann durch Erstellen von Regeln in der Web-Konsole von AEM konfiguriert werden. Nachdem sie konfiguriert wurden, können Sie sie auslösen, indem Sie zu **Tools > Vorgänge > Wartung > Wöchentliches Wartungsfenster** wechseln und die **AuditLog-Wartungsaufgabe** ausführen.

## Konfigurieren der Seiten-Auditprotokolllöschung {#configure-page-audit-log-purging}

Führen Sie zum Konfigurieren der Auditprotokolllöschung die folgenden Schritte aus:

1. Gehen Sie zum Admin der Web-Konsole, indem Sie über den Browser `http://localhost:4502/system/console/configMgr/` aufrufen.

1. Suchen Sie nach einem Element namens **Pages audit Log Purge rule** und klicken Sie darauf.

   ![chlimage_1-365](assets/chlimage_1-365.png)

1. Konfigurieren Sie anschließend den Bereinigungs-Scheduler entsprechend Ihren Anforderungen. Folgende Optionen sind verfügbar:

   * **Regelname:** den Namen der Prüfrichtlinienregel;
   * **Content path:** der Inhalts-Pfad, auf den die Regel angewandt wird;
   * **Mindestalter:** die Zeit in Tagen, in der die Auditprotokolle aufbewahrt werden müssen;
   * **Auditprotokolltyp:** der Typ des Auditprotokolls, das bereinigt werden soll.

   >[!NOTE]
   >
   >Der Inhalts-Pfad gilt nur für untergeordnete Elemente des Knotens `/var/audit/com.day.cq.wcm.core.page` im Repository.

1. Speichern Sie die Regel.
1. Die soeben erstellte Regel muss im Vorgangs-Dashboard verfügbar gemacht werden, damit sie ausgeführt werden kann. Gehen Sie hierzu über den AEM-Begrüßungsbildschirm zu **Tools > Vorgänge > Wartung**.

1. Klicken Sie auf die Karte **Wöchentliches Wartungsfenster**.

1. Die Wartungsaufgabe ist bereits auf der Karte **AuditLog-Wartungsaufgabe** vorhanden.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Sie können entweder das Datum der nächsten Ausführung ermitteln, es konfigurieren oder es durch das Drücken der Wiedergabetaste manuell ausführen.

Wenn das Fenster zur geplanten Wartung in AEM 6.3 geschlossen wird, bevor die Aufgabe zur Auditprotokolllöschung abgeschlossen werden konnte, wird die Aufgabe automatisch angehalten. Sie wird fortgesetzt, wenn das nächste Wartungsfenster beginnt.

**Mit AEM 6.5** können Sie eine aktuell ausgeführte Aufgabe zur Auditprotokolllöschung manuell anhalten, indem Sie auf das **Stopp**-Symbol klicken. Bei der nächsten Ausführung wird die Aufgabe sicher fortgesetzt.

>[!NOTE]
>
>Die Wartungsaufgabe anzuhalten bedeutet, die Ausführung auszusetzen, ohne den bereits ausgeführten Auftrag zu verlieren.

## DAM-Auditprotokolllöschung konfigurieren {#configure-dam-audit-log-purging}

1. Navigieren Sie unter *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr* zur Systemkonsole.
1. Suchen Sie nach **Bereinigung des DAM-Auditprotokolls** und klicken Sie auf das Ergebnis.
1. Konfigurieren Sie im nächsten Fenster Ihre Regel entsprechend: Die Optionen sind:

   * **Regelname:** den Namen der Prüfrichtlinienregel;
   * **Content path:** der Inhalts-Pfad, auf den die Regel angewandt wird
   * **Mindestalter:** die Zeit in Tagen, in der die Auditprotokolle aufbewahrt werden müssen
   * **Auditprotokoll-DAM-Ereignistypen:** die Typen der DAM-Prüfereignisse, die bereinigt werden sollen.

1. Klicks **Speichern** , um Ihre Konfiguration zu speichern

## Konfigurieren der Replikations-Auditprotokolllöschung  {#configure-replication-audit-log-purging}

1. Navigieren Sie unter *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr* zur Systemkonsole.
1. Suchen Sie nach **Replikations-Auditprotokoll-Bereinigungs-Planung** und klicken Sie auf das Ergebnis
1. Konfigurieren Sie im nächsten Fenster Ihre Regel entsprechend: Die Optionen sind:

   * **Regelname:** den Namen der Prüfrichtlinienregel
   * **Content path:** der Inhalts-Pfad, auf den die Regel angewandt wird
   * **Mindestalter:** die Zeit in Tagen, in der die Auditprotokolle aufbewahrt werden müssen
   * **Audit log Replication event types:** die Typen von Replikations-Audit-Ereignissen, die gelöscht werden sollen

1. Klicks **Speichern** , um Ihre Konfiguration zu speichern.
