---
title: Ausführen von AEM im produktionsbereiten Modus
description: Erfahren Sie, wie Sie AEM im produktionsbereiten Modus ausführen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 3c342014-f8ec-4404-afe5-514bdb651aae
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 45%

---

# Ausführen von AEM im produktionsbereiten Modus{#running-aem-in-production-ready-mode}

Mit AEM 6.1 führt Adobe die neue `"nosamplecontent"` Ausführungsmodus zur Automatisierung der Schritte, die zur Vorbereitung einer AEM Instanz für die Bereitstellung in einer Produktionsumgebung erforderlich sind.

Der neue Ausführungsmodus konfiguriert die Instanz nicht nur automatisch, um die in der Sicherheitscheckliste beschriebenen Best Practices für die Sicherheit einzuhalten, sondern entfernt auch alle Beispielanwendungen und -konfigurationen im Geometrixx.

>[!NOTE]
>
>Da aus praktischen Gründen der AEM produktionsbereite Modus nur die meisten Aufgaben abdeckt, die zum Schützen einer Instanz erforderlich sind, empfehlen wir dringend, die [Sicherheitscheckliste](/help/sites-administering/security-checklist.md) bevor Sie mit Ihrer Produktionsumgebung live gehen.
>
>Beachten Sie außerdem, dass die Ausführung von AEM im produktionsbereiten Modus den Zugriff auf CRXDE Lite effektiv deaktiviert. Wenn Sie es zum Debuggen benötigen, finden Sie unter [Aktivieren von CRXDE Lite in AEM](/help/sites-administering/enabling-crxde-lite.md) weitere Informationen.

![chlimage_1-83](assets/chlimage_1-83a.png)

Um AEM im produktionsbereiten Modus auszuführen, müssen Sie nur Folgendes hinzufügen: `nosamplecontent` über die `-r` Wechseln Sie zum Ausführungsmodus zu den vorhandenen Startargumenten:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

Beispielsweise können Sie den produktionsbereiten Modus zum Starten einer Autoreninstanz mit MongoDB-Persistenz verwenden:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Ändern eines Teils des produktionsbereiten Modus {#changes-part-of-the-production-ready-mode}

Genauer gesagt werden die folgenden Konfigurationsänderungen ausgeführt, wenn AEM im produktionsbereiten Modus ausgeführt wird:

1. Das **CRXDE-Support-Bundle** (`com.adobe.granite.crxde-support`) ist im produktionsbereiten Modus standardmäßig deaktiviert. Es kann jederzeit über das öffentliche Adobe-Maven-Repository installiert werden. Version 3.0.0 ist für AEM 6.1 erforderlich.

1. Das Bundle **Apache Sling Simple WebDAV Access to repositories** (`org.apache.sling.jcr.webdav`) ist nur für **Autoreninstanzen** verfügbar.

1. Neu erstellte Benutzer müssen das Kennwort bei der ersten Anmeldung ändern. Dies gilt nicht für den Admin-Benutzer.
1. **Debug-Informationen generieren** ist für die **Apache Sling JavaScript Handler**.

1. **Die Funktionen zum zugeordneten Inhalt** und **zum Erzeugen von Debug-Informationen** sind für den **Apache Sling Jsp Script Handler** deaktiviert.

1. Der **Day CQ WCM-Filter** ist auf `edit` bei der **Autoreninstanz** und auf `disabled` bei der **Veröffentlichungsinstanz** eingestellt.

1. Der **Adobe Granite HTML Library Manager** wird mit den folgenden Einstellungen konfiguriert:

   1. **Minify:** `enabled`
   1. **Debug:** `disabled`
   1. **Gzip:** `enabled`
   1. **Timing:** `disabled`

1. Das **Apache Sling Get Servlet** ist so eingestellt, dass es sichere Konfigurationen standardmäßig unterstützt, so zum Beispiel wie folgt:

| **Konfiguration** | **Autor** | **Veröffentlichen** |
|---|---|---|
| TXT-Ausgabedarstellung | disabled | disabled |
| HTML-Ausgabedarstellung | disabled | disabled |
| JSON-Ausgabedarstellung | enabled | enabled |
| XML-Ausgabedarstellung | disabled | disabled |
| json.maximumresults | 1000 | 100 |
| Auto Index | disabled | disabled |
