---
title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Dienst, mit dem Sie Ressourcenpfade programmgesteuert in externe, absolute URLs umwandeln können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: 971d6c25-1fbe-4c07-944e-be6b97a59922
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 94%
---
# Externalisieren von URLs{#externalizing-urls}

In Adobe Experience Manager (AEM) ist der **Externalizer** ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad (z. B. `/path/to/my/page`) programmgesteuert in eine externe und absolute URL (z. B. `https://www.mycompany.com/path/to/my/page`) umwandeln können, indem der Pfad mit einem vorkonfigurierten DNS-Präfix versehen wird.

Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs, weil eine Instanz ihre extern sichtbare URL nicht kennen kann, wenn sie hinter einer Web-Layer läuft, und weil manchmal ein Link außerhalb des Anfrageumfangs erstellt werden muss.

Auf dieser Seite wird beschrieben, wie Sie den **Externalizer**-Dienst konfigurieren und verwenden. Weitere Informationen finden Sie unter [Javadocs](https://experienceleague.adobe.com/en/tools/aem-api-documentation/6-5/javadoc/com/day/cq/commons/Externalizer.html).

## Konfigurieren des Externalizer-Diensts {#configuring-the-externalizer-service}

Der **Externalizer**-Dienst ermöglicht es Ihnen, mehrere Domains zentral zu definieren, die für das programmgesteuerte Voranstellen von Präfixen für Ressourcenpfade verwendet werden können. Alle Domains werden anhand eines eindeutigen Namens zum programmgesteuerten Verweisen auf die Domain identifiziert.

Definieren Sie eine Domain-Zuordnung für den **Externalizer**-Service wie folgt:

1. Wechseln Sie zum Konfigurations-Manager über **Tools** > **Web-Konsole** oder geben Sie Folgendes ein:

   `https://<host>:<port>/system/console/configMgr`

1. Klicken Sie auf **Day CQ Link Externalizer**, um das Konfigurationsdialogfeld zu öffnen.

   >[!NOTE]
   >
   >Der Direkt-Link zur Konfiguration lautet `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![aem-externalizer-01](assets/aem-externalizer-01.png)

1. Definieren einer **Domain**-Zuordnung: Eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domain, ein Leerzeichen und die Domain zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Dabei gilt:

   * **Schema** ist normalerweise „http“ oder „https“, kann aber auch z. B. „ftp“ sein.

     * Verwenden Sie bei Bedarf HTTPS, um HTTPS-Links zu erzwingen.
     * Es wird verwendet, wenn der Clientcode das Schema nicht überschreibt, wenn er die Externalisierung einer URL anfordert.

   * **Server** ist der Host-Name (kann ein Domain-Name oder eine IP-Adresse sein).
   * **Port** (optional) ist die Portnummer.
   * **Kontextpfad** (optional) wird nur festgelegt, wenn AEM als Web-App unter einem anderen Kontextpfad installiert wird.

   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer festgelegt werden, da AEM auf sie angewiesen ist:

   * `local` – die lokale Instanz
   * `author` – das DNS des Bearbeitungssystems
   * `publish` – das DNS der öffentlichen Website

   >[!NOTE]
   >
   >Mit einer benutzerdefinierten Konfiguration können Sie eine neue Kategorie hinzufügen, z. B. `production`, `staging` oder sogar externe Nicht-AEM-Systeme wie `my-internal-webservice`. Es ist nützlich, die Hartkodierung solcher URLs an verschiedenen Stellen in der Code-Basis eines Projekts zu vermeiden.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

>[!NOTE]
>
>Adobe empfiehlt, dass Sie [die Konfiguration dem Repository hinzufügen](/help/sites-deploying/configuring.md#addinganewconfigurationtotherepository).

### Verwenden des Externalizer-Diensts {#using-the-externalizer-service}

Dieser Abschnitt zeigt einige Beispiele dafür, wie der **Externalizer**-Dienst verwendet werden kann:

1. **Den Externalizer-Dienst rufen Sie in JSP wie folgt ab:**

   ```java
   Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);
   ```

1. **Einen Pfad mit der publish-Domain externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domain-Zuordnung:

   * `publish https://www.website.com`

   `myExternalizedUrl` endet mit dem Wert:

   * `https://www.website.com/contextpath/my/page.html`

1. **So externalisieren Sie einen Pfad mit der Domain „author“:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domain-Zuordnung:

   * `author https://author.website.com`

   `myExternalizedUrl` endet mit dem Wert:

   * `https://author.website.com/contextpath/my/page.html`

1. **So externalisieren Sie einen Pfad mit der Domain „local“:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Angenommen, die Domain-Zuordnung:

   * `local https://publish-3.internal`

   `myExternalizedUrl` endet mit dem Wert:

   * `https://publish-3.internal/contextpath/my/page.html`

1. Weitere Beispiele finden Sie in den [Javadocs](https://experienceleague.adobe.com/en/tools/aem-api-documentation/6-5/javadoc/com/day/cq/commons/Externalizer.html).
