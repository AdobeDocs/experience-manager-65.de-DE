---
title: Externalisieren von URLs
seo-title: Externalizing URLs
description: Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: 65bcc352-fc8c-4aa0-82fb-1321a035602d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 938469ad-f466-42f4-8b6f-bfc060ae2785
docset: aem65
exl-id: 971d6c25-1fbe-4c07-944e-be6b97a59922
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '500'
ht-degree: 100%

---

# Externalisieren von URLs{#externalizing-urls}

In AEM ist der **Externalizer** ein OSGI-Service, der es Ihnen ermöglicht, einen Ressourcenpfad (z. B. `/path/to/my/page`) programmgesteuert in eine externe und absolute URL umzuwandeln (z. B. `https://www.mycompany.com/path/to/my/page`), indem der Pfad mit einem vorangestellten vorkonfigurieren DNS versehen wird.

Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs, weil eine Instanz ihre extern sichtbare URL nicht kennen kann, wenn sie hinter einer Web-Layer läuft, und weil manchmal ein Link außerhalb des Anfrageumfangs erstellt werden muss.

Auf dieser Seite wird beschrieben, wie Sie den **Externalizer**-Dienst konfigurieren und verwenden. Weitere Informationen finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Konfigurieren des Externalizer-Diensts {#configuring-the-externalizer-service}

Der **Externalizer**-Dienst ermöglicht es Ihnen, zentral mehrere Domains zu definieren, die für das programmgesteuerte Voranstellen von Präfixen für Ressourcenpfade verwendet werden können. Alle Domains werden anhand eines eindeutigen Namens zum programmgesteuerten Verweisen auf die Domain identifiziert.

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
      * Es wird verwendet, wenn der Client-Code das Schema nicht überschreibt, wenn er die Externalisierung einer URL anfordert.
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


1. Weitere Beispiele finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
