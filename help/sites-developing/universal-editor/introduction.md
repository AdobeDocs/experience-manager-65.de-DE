---
title: Der universelle Editor
description: Erfahren Sie mehr über die Flexibilität des universellen Editors und wie Sie mit AEM 6.5 Ihr Headless-Erlebnis optimieren können.
feature: Developing
role: Developer
exl-id: 7bdf1fcc-02b9-40bc-8605-e6508a84d249
source-git-commit: 6301f0fdba9f7a6fa8fa998759b9ebad6b4fa9a6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 4%

---


# Der universelle Editor {#universal-editor}

Erfahren Sie mehr über die Flexibilität des universellen Editors und wie Sie mit AEM 6.5 Ihr Headless-Erlebnis optimieren können.

## Überblick {#overview}

Der universelle Editor ist ein vielseitiger visueller Editor, der Teil von Adobe Experience Manager Sites ist. Sie ermöglicht es Autoren, die Bearbeitung eines Headless-Erlebnisses (WYSIWYG) zu übernehmen.

* Autoren profitieren von der Flexibilität des universellen Editors, da er dieselbe konsistente visuelle Bearbeitung für alle Formen von Headless-AEM unterstützt.
* Entwickler profitieren von der Vielseitigkeit des universellen Editors, da er auch eine echte Entkopplung der Implementierung unterstützt. Damit können Entwickler praktisch jedes Framework oder jede Architektur ihrer Wahl nutzen, ohne SDK- oder Technologieeinschränkungen vorzuschreiben.

Weitere Informationen finden Sie in der Dokumentation zu [AEM as a Cloud Service im universellen Editor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) .

## Architektur {#architecture}

Der universelle Editor ist ein Dienst, der mit AEM zusammenarbeitet, um Inhalte Headless zu erstellen.

* Der Universal Editor wird unter `https://experience.adobe.com/#/aem/editor/canvas` gehostet und kann Seiten bearbeiten, die von AEM 6.5 gerendert werden.
* Die AEM Seite wird vom universellen Editor über den Dispatcher aus der AEM Autoreninstanz gelesen.
* Der Universal Editor-Dienst, der auf demselben Host wie der Dispatcher ausgeführt wird, schreibt Änderungen zurück in die AEM Autoreninstanz.

![Autorenfluss mit dem universellen Editor](assets/author-flow.png)

## Einrichtung {#setup}

Um den universellen Editor zu testen, müssen Sie:

1. [Aktualisieren und konfigurieren Sie Ihre AEM Authoring-Instanz.](#update-configure-aem)
1. [Richten Sie einen lokalen universellen Editor-Dienst ein.](#set-up-ue)
1. [Passen Sie Ihren Dispatcher so an, dass der Universal Editor-Dienst zugelassen wird.](#update-dispatcher)

Nachdem Sie die Einrichtung abgeschlossen haben, können Sie [Ihre Anwendungen für die Verwendung des universellen Editors instrumentieren.](#instrumentation)

### AEM aktualisieren {#update-aem}

Service Pack 21 oder 22 und ein Feature Pack für AEM sind erforderlich, damit der Universal Editor mit AEM 6.5 verwendet werden kann.

#### Anwenden des neuesten Service Packs {#latest}

Stellen Sie sicher, dass Sie mindestens Service Pack 21 oder 22 für AEM 6.5 ausführen. Sie können das neueste Service Pack von [Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de) herunterladen.

#### Installieren des Feature Packs für den universellen Editor {#feature-pack}

Installieren Sie das Feature Pack **Universal Editor für AEM 6.5** [, das für Softwareverteilung verfügbar ist.](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-6.5.21-universal-editor-1.0.0.zip)

Wenn Sie bereits Service Pack 23 oder höher ausführen, ist das Feature Pack nicht erforderlich.

### Dienste konfigurieren {#configure-services}

Das Feature Pack installiert eine Reihe neuer Pakete, für die eine zusätzliche Konfiguration erforderlich ist.

#### Legen Sie das SameSite-Attribut für das Cookie `login-token` fest. {#samesite-attribute}

1. Öffnen Sie den Configuration Manager. 
   * `http://<host>:<port>/system/console/configMgr`
1. Suchen Sie **Adobe Granite Token Authentication Handler** in der Liste und klicken Sie auf **Konfigurationswerte ändern**.
1. Ändern Sie im Dialogfeld das Attribut **SameSite für den Wert des Anmelde-Token-Cookies** (`token.samesite.cookie.attr`) in `Partitioned`.
1. Klicken Sie auf **Speichern**.

#### Entfernen Sie die Option `SAMEORIGIN` Headers X-Frame . {#sameorigin}

1. Öffnen Sie den Configuration Manager. 
   * `http://<host>:<port>/system/console/configMgr`
1. Suchen Sie **Apache Sling Main Servlet** in der Liste und klicken Sie auf **Konfigurationswerte bearbeiten**.
1. Löschen Sie den Wert `X-Frame-Options=SAMEORIGIN` aus dem Attribut **Zusätzliche Antwortheader** (`sling.additional.response.headers`), sofern vorhanden.
1. Klicken Sie auf **Speichern**.

#### Konfigurieren Sie den Adobe Granite Query Parameter Authentication Handler. {#query-parameter}

1. Öffnen Sie den Configuration Manager. 
   * `http://<host>:<port>/system/console/configMgr`
1. Suchen Sie **Adobe Granite Query Parameter Authentication Handler** in der Liste und klicken Sie auf **Konfigurationswerte bearbeiten**.
1. Fügen Sie im Feld **Pfad** (`path`) den Wert `/` hinzu, um ihn zu aktivieren.
   * Ein leerer Wert deaktiviert den Authentifizierungs-Handler.
1. Klicken Sie auf **Speichern**.

#### Definieren Sie, für welche Inhaltspfade oder `sling:resourceTypes` der universelle Editor geöffnet werden soll. {#paths}

1. Öffnen Sie den Configuration Manager. 
   * `http://<host>:<port>/system/console/configMgr`
1. Suchen Sie **URL-Dienst für den universellen Editor** in der Liste und klicken Sie auf **Konfigurationswerte bearbeiten** .
1. Definieren Sie, für welche Inhaltspfade oder `sling:resourceTypes` der universelle Editor geöffnet werden soll.
   * Geben Sie im Feld **Universal Editor Opening Mapping** die Pfade an, für die der universelle Editor geöffnet wird.
   * Geben Sie im Feld **Sling:resourceTypes , das vom universellen Editor geöffnet werden soll** eine Liste der Ressourcen an, die direkt vom universellen Editor geöffnet werden.
1. Klicken Sie auf **Speichern**.

AEM öffnet den Universal Editor für Seiten, die auf dieser Konfiguration basieren.

1. AEM überprüft die Zuordnungen unter `Universal Editor Opening Mapping`. Wenn sich der Inhalt unter einem dort definierten Pfad befindet, wird der universelle Editor dafür geöffnet.
1. Bei Inhalten, die nicht unter in `Universal Editor Opening Mapping` definierten Pfaden definiert sind, überprüft AEM, ob der `resourceType` des Inhalts mit den in **Sling:resourceTypes definierten übereinstimmt, die vom universellen Editor geöffnet werden sollen**, und ob der Inhalt mit einem dieser Typen übereinstimmt, wird der universelle Editor unter `${author}${path}.html` geöffnet.
1. Andernfalls AEM der Seiteneditor geöffnet.

Die folgenden Variablen sind verfügbar, um Ihre Zuordnungen unter `Universal Editor Opening Mapping` zu definieren.

* `path`: Inhaltspfad der zu öffnenden Ressource
* `localhost`: Externalizer-Eintrag für `localhost` ohne Schema, z. B. `localhost:4502`
* `author`: Externalizer-Eintrag für Autor ohne Schema, z. B. `localhost:4502`
* `publish`: Externalizer-Eintrag für die Veröffentlichung ohne Schema, z. B. `localhost:4503`
* `preview`: Externalizer-Eintrag für die Vorschau ohne Schema, z. B. `localhost:4504`
* `env`: `prod`, `stage`, `dev` basierend auf den definierten Sling-Ausführungsmodi
* `token`: Abfrage-Token erforderlich für den `QueryTokenAuthenticationHandler`

Beispielzuordnungen:

* Öffnen Sie alle Seiten unter &quot;`/content/foo`&quot;in der AEM-Autoreninstanz:
   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Dadurch wird `https://localhost:4502/content/foo/x.html?login-token=<token>` geöffnet
* Öffnen Sie alle Seiten unter &quot;`/content/bar`&quot;auf einem Remote-NextJS-Server und geben Sie alle Variablen als Informationen ein.
   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Dadurch wird `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>` geöffnet

### Einrichten eines universellen Editordienstes {#set-up-ue}

Mit AEM Aktualisierung und Konfiguration können Sie einen lokalen Universal Editor-Dienst für Ihre eigene lokale Entwicklung und Tests einrichten.

1. Installieren Sie Node.js , Version >=20.
1. Laden Sie den neuesten Universal Editor-Dienst von [Softwareverteilung](https://experienceleague.adobe.com/en/docs/experience-cloud/software-distribution/home) herunter und entpacken Sie ihn.
1. Konfigurieren Sie den universellen Editor-Dienst über Umgebungsvariablen oder die Datei `.env` .
   * [Weitere Informationen finden Sie in der Dokumentation zum AEM as a Cloud Service Universal Editor.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service)
   * Beachten Sie, dass Sie möglicherweise die Option `UES_MAPPING` verwenden müssen, wenn eine interne IP-Umschreibung erforderlich ist.
1. Führen Sie `universal-editor-service.cjs` aus.

### Aktualisieren der Dispatcher {#update-dispatcher}

Wenn AEM konfiguriert ist und ein lokaler Universal Editor-Dienst ausgeführt wird, müssen Sie einen Reverse-Proxy für den neuen Dienst [im Dispatcher zulassen.](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher)

1. Passen Sie die Datei vhost der Autoreninstanz an, um einen Reverse-Proxy einzuschließen.

   ```html
   <IfModule mod_proxy.c>
    ProxyPass "/universal-editor" "http://localhost:8080"
    ProxyPassReverse "/universal-editor" "http://localhost:8080"
   </IfModule>
   ```

   >[!NOTE]
   >
   >8080 ist der Standardanschluss. Wenn Sie dies mithilfe des Parameters `UES_PORT` in der Datei [Ihre `.env` Datei](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service) geändert haben, müssen Sie den Anschlusswert hier entsprechend anpassen.

1. Starten Sie Apache neu.

## App Instrumentieren {#instrumentation}

Wenn AEM aktualisiert und ein lokaler Universal Editor-Dienst ausgeführt wird, können Sie mit der Bearbeitung von Headless-Inhalten mit dem universellen Editor beginnen.

Ihre App muss jedoch instrumentiert werden, um den universellen Editor nutzen zu können. Dazu gehört das Einschließen von Meta-Tags, um den Editor anzuweisen, wie und wo der Inhalt beibehalten werden soll. Einzelheiten zu dieser Instrumentierung finden Sie in der Dokumentation zum [universellen Editor für AEM as a Cloud Service.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/getting-started#instrument-page)

Beachten Sie, dass bei der Verwendung der folgenden Dokumentation für den universellen Editor mit AEM as a Cloud Service die folgenden Änderungen bei AEM 6.5 gelten.

* Das Protokoll im Meta-Tag muss `aem65` anstelle von `aem` sein.

  ```html
  <meta name="urn:adobe:aue:system:aemconnection" content={`aem65:${getAuthorHost()}`}/>
  ```

* Der Endpunkt Universal Editor Service muss über ein Meta-Tag angekündigt werden.

  ```html
  <meta name="urn:adobe:aue:config:service" content={`${getAuthorHost()}/universal-editor`}/>
  ```

* Im Abschnitt `plugins` der Komponentendefinition muss `aem65` anstelle von `aem` verwendet werden.

>[!TIP]
>
>Eine umfassende Anleitung für Entwickler zu den ersten Schritten mit dem universellen Editor finden Sie im Dokument [Überblick über den universellen Editor für AEM Entwickler](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/developer-overview) in der AEM as a Cloud Service-Dokumentation. Beachten Sie dabei die erforderlichen Änderungen, die für AEM 6.5-Unterstützung erforderlich sind, wie in diesem Abschnitt beschrieben.
