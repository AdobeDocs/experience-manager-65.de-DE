---
title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad programmgesteuert in eine externe und absolute URL umwandeln können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: 971d6c25-1fbe-4c07-944e-be6b97a59922
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 55%

---

# Externalisieren von URLs{#externalizing-urls}

In Adobe Experience Manager (AEM) wird die **Externalizer** ist ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad programmgesteuert umwandeln können (z. B. `/path/to/my/page`) in eine externe und absolute URL (zum Beispiel `https://www.mycompany.com/path/to/my/page`), indem dem Pfad ein vorkonfiguriertes DNS vorangestellt wird.

Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs, weil eine Instanz ihre extern sichtbare URL nicht kennen kann, wenn sie hinter einer Web-Layer läuft, und weil manchmal ein Link außerhalb des Anfrageumfangs erstellt werden muss.

Auf dieser Seite wird beschrieben, wie Sie die **Externalizer** und wie Sie ihn verwenden. Weitere Informationen finden Sie unter [Javadocs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/Externalizer.html).

## Konfigurieren des Externalizer-Dienstes {#configuring-the-externalizer-service}

Die **Externalizer** Mit dem -Dienst können Sie zentral mehrere Domänen definieren, mit denen Ressourcenpfade programmgesteuert vorangestellt werden können. Alle Domains werden anhand eines eindeutigen Namens zum programmgesteuerten Verweisen auf die Domain identifiziert.

Definieren Sie eine Domain-Zuordnung für den **Externalizer**-Service wie folgt:

1. Wechseln Sie zum Konfigurations-Manager über **Tools** > **Web-Konsole** oder geben Sie Folgendes ein:

   `https://<host>:<port>/system/console/configMgr`

1. Klicken Sie auf **Day CQ Link Externalizer**, um das Konfigurationsdialogfeld zu öffnen.

   >[!NOTE]
   >
   >Der Direkt-Link zur Konfiguration lautet `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![aem-externalizer-01](assets/aem-externalizer-01.png)

1. Definieren Sie eine **Domänen** mapping: Eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domäne, ein Leerzeichen und die Domäne zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Dabei gilt:

   * **schema** ist http oder https, kann aber auch ftp sein usw.

      * Verwenden Sie bei Bedarf HTTPS, um HTTPS-Links zu erzwingen.
      * wird verwendet, wenn der Client-Code das Schema bei der Anforderung der Externalisierung einer URL nicht außer Kraft setzt.

   * **Server** ist der Host-Name (kann ein Domain-Name oder eine IP-Adresse sein).
   * **Port** (optional) ist die Portnummer.
   * **Kontextpfad** (optional) wird nur festgelegt, wenn AEM als Web-App unter einem anderen Kontextpfad installiert wird.

   Zum Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen festgelegt werden, da AEM von ihnen abhängt:

   * `local` – die lokale Instanz
   * `author` – das DNS des Bearbeitungssystems
   * `publish` – das DNS der öffentlichen Website

   >[!NOTE]
   >
   >Mit einer benutzerdefinierten Konfiguration können Sie eine Kategorie hinzufügen, z. B. `production`, `staging`, oder sogar externe AEM, wie z. B. `my-internal-webservice`. Es ist nützlich, die Hartkodierung solcher URLs an verschiedenen Stellen in der Code-Basis eines Projekts zu vermeiden.

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

1. Weitere Beispiele finden Sie in den [Javadocs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/Externalizer.html).
