---
title: Externalisieren von URLs
seo-title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
seo-description: Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
uuid: 65bcc352-fc8c-4aa0-82fb-1321a035602d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 938469ad-f466-42f4-8b6f-bfc060ae2785
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Externalisieren von URLs{#externalizing-urls}

In AEM, the **Externalizer** is an OSGI service that allows you to programmatically transform a resource path (e.g. `/path/to/my/page`) into an external and absolute URL (for example, `https://www.mycompany.com/path/to/my/page`) by prefixing the path with a pre-configured DNS.

Da eine Instanz ihre extern sichtbare URL nicht erkennen kann, wenn sie hinter einer Webebene ausgeführt wird, und weil manchmal ein Link außerhalb des Anforderungsbereichs erstellt werden muss, stellt dieser Dienst eine zentrale Stelle zum Konfigurieren dieser externen URLs und zum Erstellen dieser URLs bereit.

Auf dieser Seite wird beschrieben, wie Sie den **Externalizer**-Dienst konfigurieren und verwenden. Weitere Informationen finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Konfigurieren des Externalizer-Diensts {#configuring-the-externalizer-service}

The **Externalizer** service allows you to centrally define multiple domains that can be used to programmatically prefix resource paths. Alle Domänen werden anhand eines eindeutigen Namens zum programmgesteuerten Verweisen auf die Domäne identifiziert.

Definieren Sie eine Domänenzuordnung für den **Externalizer**-Service wie folgt:

1. Navigate to the configuration manager via **Tools**, then **Web Console**, or enter:

   `https://<host>:<port>/system/console/configMgr`

1. Click **Day CQ Link Externalizer** to open the configuration dialog box.

   >[!NOTE]
   >
   >The direct link to the configuration is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![aem-externalizer-01](assets/aem-externalizer-01.png)

1. Define a **Domains** mapping: a mapping consists of a unique name that can be used in the code to reference the domain, a space and the domain:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   wobei:

   * **-Schema** ist normalerweise http oder https, kann aber auch ftp usw. sein.

      * HTTPS verwenden, um HTTPS-Links bei Bedarf zu erzwingen
      * wird verwendet, wenn der Client-Code das Schema nicht außer Kraft setzt, wenn eine externe URL angefordert wird.
   * **server** ist der Hostname (kann ein Domänenname oder eine IP-Adresse sein).
   * **port** (optional) ist die Anschlussnummer.
   * **contextpath** (optional) wird nur festgelegt, wenn AEM als Webapp unter einem anderen Kontextpfad installiert wird.
   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer eingestellt werden, wenn AEM auf sie angewiesen ist:

   * `local` - die örtliche Instanz
   * `author` - das Authoring-System DNS
   * `publish` - die öffentlich zugängliche Website DNS
   >[!NOTE]
   >
   >Mit einer benutzerdefinierten Konfiguration können Sie eine neue Kategorie hinzufügen, z. B. `production``staging` oder sogar externe Nicht-AEM-Systeme wie `my-internal-webservice`. Es ist nützlich, die Hartkodierung solcher URLs an verschiedenen Stellen in der Codebasis eines Projekts zu vermeiden.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

>[!NOTE]
>
>Adobe recommends that you [add the configuration to the repository](/help/sites-deploying/configuring.md#addinganewconfigurationtotherepository).

### Verwenden des Externalizer-Diensts {#using-the-externalizer-service}

Dieser Abschnitt zeigt einige Beispiele dafür, wie der **Externalizer**-Dienst verwendet werden kann:

1. **Den Externalizer-Dienst rufen Sie in JSP wie folgt ab:**

   ```java
   Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);
   ```

1. **Einen Pfad mit der publish-Domäne externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domänenzuordnung:

   * `publish https://www.website.com`
   `myExternalizedUrl` endet mit dem Wert:

   * `https://www.website.com/contextpath/my/page.html`


1. **Einen Pfad mit der author-Domäne externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domänenzuordnung:

   * `author https://author.website.com`
   `myExternalizedUrl` endet mit dem Wert:

   * `https://author.website.com/contextpath/my/page.html`


1. **Einen Pfad mit der local-Domäne externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Angenommen, die Domänenzuordnung:

   * `local https://publish-3.internal`
   `myExternalizedUrl` endet mit dem Wert:

   * `https://publish-3.internal/contextpath/my/page.html`


1. Weitere Beispiele finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
