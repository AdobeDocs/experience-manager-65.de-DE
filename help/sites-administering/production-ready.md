---
title: Ausführen von AEM im produktionsbereiten Modus
description: Erfahren Sie, wie Sie AEM im produktionsbereiten Modus ausführen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 3c342014-f8ec-4404-afe5-514bdb651aae
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
subfeature_v2:
  - id: c191041a-8b54-4bde-9e43-bc8d8f8cea74
    internal-label: Deploying
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 100%
---
# Ausführen von AEM im produktionsbereiten Modus{#running-aem-in-production-ready-mode}

Mit AEM 6.1 hat Adobe den neuen `"nosamplecontent"`-Ausführungsmodus eingeführt, der der Automatisierung der für die Vorbereitung einer AEM-Instanz zur Bereitstellung einer Produktionsumgebung erforderlichen Schritte dient.

Der neue Ausführungsmodus konfiguriert nicht nur automatisch die Instanz, um die in der Sicherheitsprüfliste beschriebenen Best Practices für die Sicherheit einzuhalten, sondern entfernt darüber hinaus alle Geometrixx-Beispielsanwendungen und -konfigurationen innerhalb des Prozesses.

>[!NOTE]
>
>Da der produktionsbereite Modus von AEM aus praktischen Gründen nur einen Großteil der für die Sicherung einer Instanz erforderlichen Aufgaben abdeckt, empfehlen wir Ihnen dringend, vor dem tatsächlichen Einsatz der Produktionsumgebung die [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) durchzugehen.
>
>Beachten Sie außerdem, dass die Ausführung von AEM im produktionsbereiten Modus den Zugriff auf CRXDE Lite effektiv deaktiviert. Wenn Sie es zum Debuggen benötigen, finden Sie unter [Aktivieren von CRXDE Lite in AEM](/help/sites-administering/enabling-crxde-lite.md) weitere Informationen.

![chlimage_1-83](assets/chlimage_1-83a.png)

Für die Ausführung von AEM im produktionsbereiten Modus müssen Sie nur `nosamplecontent` über den Ausführungsmodus-Schalter `-r` zu Ihren vorhandenen Startargumenten hinzufügen:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

Beispielsweise können Sie den produktionsbereiten Modus zum Starten einer Autoreninstanz mit MongoDB-Persistenz verwenden:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Ändern eines Teils des produktionsbereiten Modus {#changes-part-of-the-production-ready-mode}

Genauer gesagt werden die folgenden Konfigurationsveränderungen durchgeführt, wenn AEM im produktionsbereiten Modus ausgeführt wird:

1. Das **CRXDE-Support-Paket** (`com.adobe.granite.crxde-support`) ist im produktionsbereiten Modus standardmäßig deaktiviert. Es kann jederzeit über das öffentliche Maven-Repository von Adobe installiert werden. Version 3.0.0 ist für AEM 6.1 erforderlich.

1. Das Paket **Apache Sling Simple WebDAV Access to repositories** (`org.apache.sling.jcr.webdav`) ist nur für **Autoreninstanzen** verfügbar.

1. Neu erstellte Benutzende müssen das Passwort bei der ersten Anmeldung ändern. Dies gilt nicht für Admin-Benutzende.
1. **Debug-Informationen erzeugen** ist für den **Apache Sling JavaScript Handler** deaktiviert.

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
