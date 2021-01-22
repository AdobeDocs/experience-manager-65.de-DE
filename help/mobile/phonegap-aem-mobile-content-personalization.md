---
title: Personalisierung von AEM Mobile-Inhalten
seo-title: Personalisierung von AEM Mobile-Inhalten
description: Auf dieser Seite erfahren Sie mehr über die AEM Mobile-Funktion zur Personalisierung von Inhalten, die es AEM Autoren ermöglicht, Inhalte mobiler Apps mithilfe von Adobe Target zu personalisieren.
seo-description: Auf dieser Seite erfahren Sie mehr über die AEM Mobile-Funktion zur Personalisierung von Inhalten, die es AEM Autoren ermöglicht, Inhalte mobiler Apps mithilfe von Adobe Target zu personalisieren.
uuid: 9078edd1-8399-485f-8a63-a07e766f7ef9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: c9c818dc-c5c4-4a96-94fe-9dc9fe75705b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '2701'
ht-degree: 3%

---


# Personalisierung von AEM Mobile-Inhalten{#aem-mobile-content-personalization}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Dieses Dokument ist Teil des Leitfadens [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md), einem empfohlenen Ausgangspunkt für AEM Mobile-Referenzzwecke.

Mit der AEM Mobile-Funktion zur Personalisierung von Inhalten können [AEM-Autoren](#author) Inhalte mobiler Apps personalisieren, indem [Adobe Target](https://www.adobe.com/ca/marketing-cloud/testing-targeting.html) genutzt wird. Dies ermöglicht den Versand zielgerichteter Angebot an Benutzer mobiler Anwendungen. Adobe Experience Manager Mobile bietet die Möglichkeit, Inhalte zu erstellen, Zielgruppen zu erstellen und bereitzustellen, die dem Benutzer Inhalte bereitstellen, die für seine individuellen Vorlieben spezifisch sind.

Wie es in AEM oft der Fall ist, müssen Administratoren und Entwickler zunächst die Umgebung vorbereiten, damit Autoren mit der Erstellung dieser Inhalte beginnen können.

[AEM ](#administrator) Verwaltungen müssen eine Verbindung zwischen AEM Mobile und dem Adobe Target-Cloud Service herstellen.

AEM Mobile [Entwickler](#developer) müssen ihre vorhandenen Skripte ändern, um das Erstellen zielgerichteter Inhalte zu erleichtern.

## Für Administratoren {#for-administrators}

Es müssen mehrere Schritte durchgeführt werden, bevor Autoren von Inhalten Beginn zur Erstellung zielgerichteter Inhalte für mobile Apps erhalten: Sie erhalten die richtigen Berechtigungen für Benutzer und Gruppen, erstellen Cloud-Dienste, konfigurieren die Anwendung für die Aktivität und generieren den Inhalt schließlich.

Dieser Artikel führt Sie durch den Prozess, der zum Konfigurieren der [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) für das Targeting verwendet wird.

Es wird davon ausgegangen, dass die AEM Mobile Hybrid-Referenzanwendung erfolgreich implementiert wurde und über das AEM Mobile-Dashboard zugänglich ist.

Bevor Autoren zielgerichteten Inhalt in einer Anwendung generieren können, muss Ihre AEM mit dem Adobe Target Cloud Service konfiguriert werden.](/help/mobile/aem-mobile-configuring-cloud-service.md)[

### Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen Teil der `target-activity-authors`-Gruppe sein.

Es wird empfohlen, dass im Rahmen der Benutzer- und Gruppeneinrichtung die Zielgruppe-Aktivität-Gruppe der Gruppe apps-admins hinzugefügt wird. Durch Hinzufügen der Zielgruppe-Aktivität-Autorengruppe können Benutzer den Eintrag im Menü &quot;Personalisierung&quot;sehen.

>[!NOTE]
>
>Wenn Sie vergessen haben, die Benutzer oder Gruppen, die Zugriff auf die Personalisierungskonsole haben sollen, der Zielgruppe-Aktivität-Autoren-Gruppe hinzuzufügen, wird verhindert, dass die Personalisierungskonsole angezeigt wird.

### Cloud Services {#cloud-services}

Damit zielgerichtete Inhalte für mobile Anwendungen verwendet werden können, müssen zwei Dienste konfiguriert werden: Der Adobe Target-Dienst und der Adobe Mobile Services-Dienst. Der Adobe Target-Dienst stellt die Engine für die Verarbeitung von Clientanforderungen und die Rückgabe personalisierter Inhalte bereit. Der Adobe Mobile Services-Dienst stellt über die Datei ADBMobileConfig.json, die vom AMS Cordova-Zusatzmodul genutzt wird, eine Verbindung zwischen den Adoben- und der Mobilanwendung her. Über das AEM Mobile-Dashboard können Sie Ihre Anwendung konfigurieren, indem Sie die beiden Dienste hinzufügen.

Suchen Sie im AEM Mobile-Dashboard die Cloud Services verwalten und klicken Sie auf die Schaltfläche +.

![chlimage_1-38](assets/chlimage_1-38.png)

Wählen Sie im Assistenten für Hinzufügen Cloud Service die Cloud-Dienstkarte &quot;Adobe Target&quot;und klicken Sie auf Weiter.

![chlimage_1-39](assets/chlimage_1-39.png)

Im Dropdownmenü Konfiguration auswählen können Sie entweder eine neue Konfiguration erstellen oder aus einer vorhandenen auswählen. Um eine neue Konfiguration zu erstellen, wählen Sie &quot;Konfiguration erstellen&quot; aus der Dropdownliste. Geben Sie einen Titel für die Zielgruppe-Konfiguration ein. Geben Sie Ihren Clientcode, Ihre E-Mail-Adresse und Ihr Kennwort ein, die mit Ihrem Zielgruppen-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target Support. Klicken Sie auf die Schaltfläche &quot;Überprüfen&quot;, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche &quot;Senden&quot;, um den Cloud-Dienst zu erstellen.

>[!NOTE]
>
>Der Cloud-Dienst, der erstellt wird, wird über den Assistenten automatisch mit der mobilen Anwendung verknüpft. Der Wert der Eigenschaft cq:cloudserviceConfigs wird auf dem Knoten jcr:content des Knoten apps group festgelegt. Für das Hybrid-App-Beispiel wird es unter &quot;/content/mobileapps/hybrid-reference-app/jcr:content&quot;festgelegt. Der Wert verweist auf den automatisch generierten Framework-Knoten unter &quot;/etc/cloudservices/testandtarget/adobe-Zielgruppe—aem-apps/framework&quot;. Der Framework-Knoten verfügt über zwei Eigenschaften, die standardmäßig festgelegt sind: Geschlecht und Alter. Das Framework wird nur von AEM Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel Cloud Service verwalten den Zielgruppe Cloud-Dienst, enthält jedoch eine Warnung über ein fehlendes Adobe Mobile Service-Konto.

![chlimage_1-40](assets/chlimage_1-40.png)

### Adobe Mobile Services {#adobe-mobile-services}

Es ist erforderlich, ein Adobe Mobile Services (AMS)-Konto mit der Anwendung zu verknüpfen. Der AMS-Dienst stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Informationen zum Zielgruppe-Client-Code enthält. Bevor Sie eine Verbindung mit dem AMS-Konto erstellen, muss das AMS-Konto von einem Benutzer geändert werden, der über Berechtigungen für AMS verfügt.

### Clientcode {#client-code}

Um sich bei den AMS-Diensten anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die Mobilanwendung und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK-Zielgruppen-Optionen, platzieren Sie den Clientcode in das Feld und klicken Sie auf Speichern.

![chlimage_1-41](assets/chlimage_1-41.png)

Nachdem der Clientcode mit der Mobilanwendung verknüpft wurde, werden die Einstellungen für die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Dienst über das Adobe Mobile-Dashboard konfiguriert wird.

### Adobe Mobile Service Cloud Service {#adobe-mobile-service-cloud-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die Mobilanwendung mit dem Adobe Mobile-Dashboard zu verknüpfen. Suchen Sie im AEM Mobile-Dashboard die Cloud Services verwalten und klicken Sie auf die Schaltfläche +.

![chlimage_1-42](assets/chlimage_1-42.png)

Wählen Sie die Adobe Mobile Services und klicken Sie auf Next.

![chlimage_1-43](assets/chlimage_1-43.png)

Wählen Sie im Schritt Erstellen oder Auswählen des Assistenten das Dropdown-Menü Mobile Service und wählen Sie den Eintrag Konfiguration erstellen. Geben Sie einen Titel, eine Firma, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Mobile Service-Administrator von Adobe, um sie abzurufen. Klicken Sie nach dem Ausfüllen aller Felder auf die Schaltfläche Überprüfen. Der Überprüfungsprozess wird an AMS gesendet und überprüft die Anmeldeinformationen für das Konto. Bei erfolgreicher Überprüfung wird eine Liste von Mobilanwendungen ausgefüllt, in der Sie die zugehörige Mobilanwendung aus der Dropdownliste auswählen. Klicken Sie auf die Schaltfläche &quot;Senden&quot;, um den Assistenten abzuschließen. Der Prozess kann einige Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle damit verbundenen Analysen der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs im Modal auf die Schaltfläche Fertig, um zum Dashboard Adobe Mobile zurückzukehren.

Bei Rückkehr zum mobilen Dashboard enthält die Kachel Cloud Services verwalten den AMS-Cloud-Dienst. Sie werden außerdem feststellen, dass die Kachel &quot;Analytics-Metriken&quot;mit Lebenszyklusberichten gefüllt wird.

![chlimage_1-44](assets/chlimage_1-44.png)

## Für Autoren {#for-authors}

**Voraussetzung:** Wie oben erwähnt müssen Administratoren die Verbindung zum Adobe Target-Dienst konfigurieren, bevor Autoren neue zielgerichtete Inhalte erstellen können.

Sobald der Administrator die beiden Cloud-Dienste konfiguriert hat und der Entwickler den Handler mobileappoffers konfiguriert hat, können Autoren von Inhalten jetzt Beginn erstellen, die zielgerichtete Erlebnisse generieren.

Beim Authoring zielgerichteter Inhalte in einer AEM Mobile-App wird ein ähnlicher Vorgang wie beim Authoring von AEM Sites durchgeführt:

Eine vollständige Übersicht über [Authoring zielgerichteter Inhalte in AEM](/help/sites-authoring/personalization.md) finden Sie hier

## Für Entwickler {#for-developers}

AEM Entwickler, die mobile Anwendungen erstellen, sollten weiterhin den Mustern folgen, die bei der Entwicklung von Komponenten in allen AEM gebräuchlich sind. Hier führen wir Sie durch die erforderlichen Schritte, damit Autoren von Inhalten zielgerichtete Inhalte erstellen können:

### Adobe Target ContentSync Handlers {#adobe-target-contentsync-handlers}

Die Inhaltsbereitstellung für den Geräteinhalt des Benutzers erfolgt durch Wiedergabe der Angebot, die von AEM Inhaltserstellern erstellt werden. Zur Verarbeitung der Wiedergabe von Zielgruppe-Angeboten gibt es einen neuen Content-Synchronisierungs-Handler, der die Angebot verarbeitet. Unter Verwendung der Hybrid-Referenzanwendung als Beispiel enthält das en-Inhaltspaket (Englisch) den ContentSyncConfig mit dem Handler [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml). Der nächste Schritt ist entscheidend für die Wiedergabe von Angeboten auf dem Gerät. Der Handler &quot;mobileappoffers&quot;verfügt über eine path-Eigenschaft, die den Pfad zur Personalisierungs-Aktivität identifiziert, die für die Anwendung verwendet werden soll.

Wenn sich beispielsweise eine Aktivität unter */content/Kampagnen/hybridref* befindet, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in die Eigenschaft *path* des Handlers mobileappoffers ein.

>[!NOTE]
>
>Für die Hybrid-Referenzanwendung gibt es zwei Handler für mobileappoffers: einen für den dev und einen für Produktionen.

Nachdem der Pfad der Aktivitäten in der Eigenschaft path des Handlers mobileappoffers festgelegt wurde, speichern Sie den Handler. Der Handler ist nun bereit, Angebot für die Wiedergabe auf Beginn für unsere Mobilgeräte zu rendern.

### Rendermodus {#render-mode}

Der Handler mobileappoffers wird für Veröffentlichungs- und Entwicklungs-Setups anders konfiguriert. Bei Veröffentlichungseinstellungen gibt es die Eigenschaft *renderMode* mit dem Wert *publish*, der auf dem Knoten cq:ContentSyncConfig festgelegt ist. Der Handler mobileappoffers verweist auf den renderMode und ändert, wenn er auf &quot;publish&quot;eingestellt ist, die erstellte mbox-ID. Standardmäßig wird bei Mboxes, die von AEM erstellt werden, der Wert —author an die mbox-ID angehängt. Dadurch wird festgestellt, dass die Aktivität nicht veröffentlicht wurde, und die nicht veröffentlichte Kampagne sollte für Angebot-Auflösungen verwendet werden.

Wenn Inhalte über das Adobe Mobile-Dashboard gestaffelt werden, werden gestaffelte Inhalte als produktionsfertige Inhalte betrachtet und über die Content Sync-Konfiguration ohne dev wiedergegeben. Bei einer solchen Wiedergabe wird —author aus allen mbox-IDs entfernt und erwartet, dass eine veröffentlichte Aktivität auf dem Zielgruppe-Server verfügbar ist. Bevor Sie gestaffelte Inhalte testen, stellen Sie sicher, dass die Aktivität veröffentlicht wurde.

### Personalization App Development {#personalization-app-development}

#### Komponenten {#components}

Die Grundlage für alle Inhalte ist normalerweise eine Seitenkomponente, die eine der AEM Seitenkomponenten wcm/foundation/components/page oder foundation/components/page erweitert, je nachdem, ob Sie HTML oder JSPs verwenden. Die Dauer dieser Schritte konzentriert sich auf die Verwendung der Komponente &quot;wcm/foundation/components/page&quot;. Die Grundstruktur der Seitenkomponente wird in mehrere Skripten unterteilt, wobei jedes Skript den Entwicklern die Möglichkeit gibt, ihren Code bei Bedarf zu organisieren und zu überschreiben. Die beiden Skripten, die für Personalisierung von Interesse sind, sind head.html und body.html. Diese beiden Skripten bieten einen Bereich, in dem Code eingefügt werden kann, um den Context Hub, Cloud Services und das Mobile Authoring zu unterstützen.

Im Folgenden finden Sie eine Übersicht über die beiden primären Skripten, die zum Aktivieren des Content-Targeting verwendet werden.

#### head.html {#head-html}

Damit der Autor die Zielgruppe seines Inhalts erhalten kann, muss das Seitenmenü hinzugefügt werden, damit der Autor den Kontext vom Bearbeitungsmodus zum Targeting-Modus wechseln kann. Um diese Funktion zu aktivieren, sollte der Entwickler das Skript head.html so ändern, dass es den folgenden Codeausschnitt am Anfang der head.html-Datei oder möglichst nahe am &lt;title>&lt;/title>-Element enthält.

```xml
<meta data-sly-test="${!wcmmode.disabled}">
    <div data-sly-call="${clientLib.all @ categories='personalization.kernel'}" data-sly-unwrap></div>
    <div data-sly-resource="${'config' @ resourceType='cq/personalization/components/clientcontext_optimized/config'}" data-sly-unwrap></div>
    <div data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}" data-sly-unwrap></div>
</meta>
```

>[!NOTE]
>
>Beachten Sie, dass das Skript nur dann einbezogen werden sollte, wenn der WCM-Modus nicht deaktiviert wurde. Wenn der WCM-Modus deaktiviert ist (weitere Informationen finden Sie im Abschnitt des ContentSync-Handlers), wird das Skript nicht in den endgültigen Anwendungscode aufgenommen.

Um Autoren die Möglichkeit zu geben, die zielgerichteten Inhalte Vorschau, muss der Editor in der Lage sein, die Konfiguration des Adobe Target Cloud-Dienstes zu finden. Der Codeblock unten fügt zwei wichtige Skripten hinzu. Das erste Mal, dass die Seite die Möglichkeit hat, den zugehörigen Zielgruppe Cloud-Dienst zu finden und die Anrufe an Adobe Target abzuwickeln. Die zweite ist die Kategorie cq.apps.targeting.

Die Kategorie **cq.apps.targeting** überschreibt die Standardkomponente cq/personalization/component/Zielgruppe und verwendet die Komponente mobileapps/components/Zielgruppe, die Angebot speziell für den Mobilanwendungskonsum rendert. Weitere Informationen dazu finden Sie im Abschnitt Zielgruppe Component.

Der Code sollte in head.html hinzugefügt und direkt vor dem Ende des &lt;/head>-Elements platziert werden.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-include="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" data-sly-unwrap></div>
    <meta data-sly-call="${clientLib.all @ categories='cq.apps.targeting'}" data-sly-unwrap></meta>
</div>
```

>[!NOTE]
>
>Beachten Sie, dass der Codeblock in einen WCM-Modus eingeschlossen ist, der nicht deaktiviert wird. Daher wird er erst abgespielt, wenn der Autor an der Erstellung von Inhalten arbeitet. Die Cloud-Dienst-Skripten werden dem generierten Mobile Runtime-Code nicht hinzugefügt.

#### body.html {#body-html}

Damit der Autor des Inhalts verschiedene Personen testen kann, muss das Skript body.html den folgenden Codeblock als erstes untergeordnetes Element des Body-Elements einschließen.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-resource="${'clientcontext' @ resourceType='cq/personalization/components/clientcontext_optimized'}" data-sly-unwrap></div>
</div>
```

Das letzte erforderliche Codefragment befindet sich ganz unten in body.html. Dieser Code sucht nach dem zugehörigen Cloud-Dienst und fügt den entsprechenden Targeting-Engine-Code ein.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-resource="${'cloudservices' @ resourceType='cq/cloudserviceconfigs/components/servicecomponents'}" data-sly-unwrap></div>
</div>
```

### Referenzanwendung {#reference-application}

Beispiele für head.html und body.html finden Sie in der [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference), die dem Entwickler zeigt, wo die Skriptblöcke in den beiden Skripten platziert werden sollen.

### Content Sync Handlers {#content-sync-handlers}

Wenn der Autor des Inhalts die Erstellung von Inhalten für die mobile Anwendung abgeschlossen hat, müssen Sie als Nächstes die Quelle herunterladen und die Anwendung erstellen oder die zu veröffentlichenden Inhalte bereitstellen. Es gibt eine Reihe von Schritten, mit denen der Entwickler befasst ist, um dies zu erreichen. Um die Wiedergabe des Inhalts zu unterstützen, verwendet AEM Mobile Content-Synchronisierungs-Handler, um den Inhalt zu rendern und zu verpacken. Für den Anwendungsfall &quot;Personalisierung&quot;wurde ein neuer Content-Synchronisierungs-Handler eingeführt, um zielgerichtete Inhalte wiederzugeben. Der Handler &quot;mobileappoffers&quot;weiß, wie die zugehörigen Zielgruppen-Angebot wiedergegeben werden, die vom Inhaltsautor erstellt wurden. Der Handler mobileappoffers erweitert den Updatehandler für abstrakte Seiten, daher sind viele Eigenschaften ähnlich. Die Details des Handlers mobileappoffers haben die folgenden Eigenschaften.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>rewrite</td>
   <td>+ relativeParentPath<p> - "/"</p> </td>
   <td>Die rewrite-Eigenschaft gibt an, wie Pfade innerhalb des Inhalts umgeschrieben werden sollen.</td>
  </tr>
  <tr>
   <td>includePageTypes</td>
   <td><p>"cq/personalization/components/teaserpage",</p> <p>"cq/personalization/components/offerproxy"</p> </td>
   <td>Die Eigenschaft includePageTypes ist optional. Standardmäßig werden Seiten mit den Ressourcentypen cq/personalization/components/teaserpage und cq/personalization/components/offerproxy verwendet. Diese beiden Ressourcentypen sind die Standard-Ressourcentypen, die beim Targeting von Inhalten verwendet werden. Wenn zusätzliche Ressourcentypen unterstützt werden müssen, sollten sie der Liste von includePageTypes hinzugefügt werden.</td>
  </tr>
  <tr>
   <td>locationRoot</td>
   <td>/content/mobileapps/</td>
   <td>Der Speicherort der App.</td>
  </tr>
  <tr>
   <td>type</td>
   <td>mobileappoffers</td>
   <td>Der Name des Handlers, der mobileappoffers ist.</td>
  </tr>
  <tr>
   <td>selector</td>
   <td>tandt</td>
   <td>Die Standardauswahl wird zum Rendern des zielgerichteten Inhalts verwendet. </td>
  </tr>
  <tr>
   <td>targetRootDirectory</td>
   <td>www</td>
   <td>Der Stammordner, in dem der gerenderte Inhalt beibehalten werden soll.</td>
  </tr>
  <tr>
   <td>includeImages</td>
   <td>true | false</td>
   <td>Wenn "true", werden alle im Angebot enthaltenen Bilder gerendert. Wenn FALSE-Bilder übersprungen werden.</td>
  </tr>
  <tr>
   <td>includeVideos</td>
   <td>true | false</td>
   <td>Wenn "true", werden alle im Angebot enthaltenen Videos gerendert. Wenn "false", werden Videos übersprungen.</td>
  </tr>
  <tr>
   <td>path</td>
   <td>/content/Kampagnen/</td>
   <td>Verweist auf die Marke der Kampagne, an der die Angebote teilnehmen. Derzeit müssen alle Angebot aus derselben Kampagne kommen.</td>
  </tr>
  <tr>
   <td>tief</td>
   <td>true | false</td>
   <td>Wenn "true"rekursiv alle untergeordneten Seiten wiedergibt, werden bei "false"keine Wiederholungen durchgeführt. </td>
  </tr>
  <tr>
   <td>extension</td>
   <td>html</td>
   <td>Legt die Erweiterung für die gerenderte Ressource fest. Auf html eingestellt, sodass die Seiten die Erweiterung .html haben.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die [AEM Mobile Hybrid-Referenz-App](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) verfügt über die Standardkonfiguration des Handlers mobileappoffer. Die Eigenschaft path im Beispiel ist leer, da sie vom Speicherort der Kampagne abhängt. Nachdem ein Verfasser der Kampagne eine Kampagne erstellt hat, sollte der Anwendungsadministrator die Kampagne mit dem Handler verknüpfen, indem die Eigenschaft path angegeben wird, die auf die Kampagne verweist.

### Zielgruppe Component {#target-component}

Um Inhalte speziell für mobile Anwendungen wiederzugeben, verwendet AEM Mobile die Komponente mobileapps/components/Zielgruppe. Die Komponente &quot;mobile Zielgruppe&quot;erweitert die Komponente &quot;cq/personalization/components/Zielgruppe&quot;und überschreibt das Skript &quot;engine_tnt.jsp&quot;. Durch Überschreiben der Datei &quot;engine_tnt.jsp&quot;kann AEM Mobile den generierten HTML-Code für die Anwendungsfälle mobiler Apps steuern. Für jede Komponente, die auf einen Inhaltsersteller ausgerichtet ist, wird eine verknüpfte mbox von der Datei engine_tnt.jsp erstellt.

Für jede mbox wird ein Attribut von **cq-targeting** hinzugefügt, das es Anwendungsentwicklern ermöglicht, benutzerspezifischen Code zu schreiben, der verwendet und verwendet werden kann, wie es gewünscht wird. Die [AEM Mobile Hybrid-Referenz-App](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) enthält ein Beispiel für eine Angular-Direktive, die das Attribut cq-targeting verwendet. Das Konzept des Ersatzes von Inhalten, wann und wie er durchgeführt wird, liegt sehr am Entwickler von mobilen Anwendungen. Es gibt ein mobiles SDK, das über AEM /etc/clientlibs/mobileapps/js/mobileapps.js bereitgestellt wird, das eine API zum Aufrufen des Adobe-Targeting-Dienstes bereitstellt. Es ist Sache des Anwendungsentwicklers, anzugeben, wann dieser Aufruf gemäß dem Design ihrer Anwendung erfolgen soll.

## Wie geht es weiter? {#what-s-next}

1. [Mein AEM Mobile App-Erlebnis](/help/mobile/starting-aem-phonegap-app.md) 
1. [Verwalten des App-Inhalts](/help/mobile/phonegap-manage-app-content.md) 
1. [Erstellen meiner Anwendung](/help/mobile/building-app-mobile-phonegap.md) 
1. [Messen der Leistung meiner App mit Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md) 
1. [Ein personalisiertes App-Erlebnis mit Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md) 
1. [Senden wichtiger Nachrichten an meine Benutzer](/help/mobile/phonegap-push-notifications.md) 
