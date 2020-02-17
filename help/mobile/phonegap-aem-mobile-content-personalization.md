---
title: Personalisierung von AEM Mobile-Inhalten
seo-title: Personalisierung von AEM Mobile-Inhalten
description: Auf dieser Seite erfahren Sie mehr zur Personalisierungsfunktion von AEM Mobile-Inhalten, mit der AEM-Autoren Inhalte für mobile Apps personalisieren können, indem sie Adobe Target nutzen.
seo-description: Auf dieser Seite erfahren Sie mehr zur Personalisierungsfunktion von AEM Mobile-Inhalten, mit der AEM-Autoren Inhalte für mobile Apps personalisieren können, indem sie Adobe Target nutzen.
uuid: 9078edd1-8399-485f-8a63-a07e766f7ef9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: c9c818dc-c5c4-4a96-94fe-9dc9fe75705b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Personalisierung von AEM Mobile-Inhalten{#aem-mobile-content-personalization}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>This document is part of the [Getting Started with AEM Mobile](/help/mobile/getting-started-aem-mobile.md) Guide, a recommended starting point for AEM Mobile reference.

Mit der Personalisierungsfunktion für AEM Mobile-Inhalte können [AEM-Autoren](#author) Inhalte für mobile Apps mithilfe von [Adobe Target](https://www.adobe.com/ca/marketing-cloud/testing-targeting.html)personalisieren. Dies ermöglicht die Bereitstellung gezielter Angebote an Benutzer mobiler Anwendungen. Adobe Experience Manager Mobile bietet die Möglichkeit, Inhalte zu erstellen, als Ziel festzulegen und bereitzustellen, die dem Benutzer Inhalte bereitstellen, die für seine individuellen Vorlieben spezifisch sind.

Wie es in AEM oft der Fall ist, müssen Administratoren und Entwickler zunächst die Umgebung vorbereiten, damit Autoren mit der Erstellung dieser Inhalte beginnen können.

[AEM-Administratoren](#administrator) müssen eine Verbindung zwischen AEM Mobile und dem Adobe Target Cloud-Dienst herstellen.

In der Zwischenzeit müssen AEM Mobile- [Entwickler](#developer) ihre vorhandenen Skripte ändern, um das Erstellen zielgerichteter Inhalte zu erleichtern.

## Für Administratoren {#for-administrators}

Es müssen eine Reihe von Schritten durchgeführt werden, bevor Autoren von Inhalten beginnen können, zielgerichtete Inhalte für mobile Apps zu erstellen: Sie erhalten die richtigen Berechtigungen für Benutzer und Gruppen, erstellen Cloud-Dienste, konfigurieren die Anwendung für die Aktivität und generieren den Inhalt schließlich.

Dieser Artikel führt Sie durch den Prozess zum Konfigurieren der [AEM Mobile-Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) für Targeting.

Es wird davon ausgegangen, dass die AEM Mobile Hybrid-Referenzanwendung erfolgreich bereitgestellt wurde und über das AEM Mobile Dashboard zugänglich ist.

Bevor Autoren zielgerichteten Inhalt in einer Anwendung generieren können, muss Ihre AEM-Instanz mit dem Adobe Target Cloud-Dienst [konfiguriert werden.](/help/mobile/aem-mobile-configuring-cloud-service.md)

### Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen Teil der `target-activity-authors` Gruppe sein.

Es wird empfohlen, dass die target-activity-Gruppe im Rahmen der Benutzer- und Gruppeneinrichtung der Gruppe apps-admins hinzugefügt wird. Wenn Sie die Gruppe target-activity-authors hinzufügen, können Benutzer den Eintrag im Navigationsmenü &quot;Personalisierung&quot;sehen.

>[!NOTE]
>
>Wenn Sie vergessen haben, der Gruppe target-activity-authors Benutzer oder Gruppen hinzuzufügen, die Zugriff auf die Personalisierungskonsole haben möchten, wird verhindert, dass Benutzer die Personalisierungskonsole sehen.

### Cloud-Services {#cloud-services}

Damit zielgerichtete Inhalte für mobile Anwendungen verwendet werden können, müssen zwei Dienste konfiguriert werden: Der Adobe Target-Dienst und der Adobe Mobile Services-Dienst. Der Adobe Target-Dienst stellt die Engine für die Verarbeitung von Clientanforderungen und die Rückgabe personalisierter Inhalte bereit. Der Adobe Mobile Services-Dienst stellt die Verbindung zwischen den Adobe-Diensten und der mobilen Anwendung über die Datei ADBMobileConfig.json bereit, die vom AMS-Cordova-Zusatzmodul genutzt wird. Über das AEM Mobile Dashboard können Sie Ihre Anwendung konfigurieren, indem Sie die beiden Dienste hinzufügen.

Suchen Sie im AEM Mobile Dashboard die Option Cloud-Dienste verwalten und klicken Sie auf die Schaltfläche +.

![chlimage_1-38](assets/chlimage_1-38.png)

Wählen Sie im Assistenten zum Hinzufügen von Cloud-Diensten die Cloud-Dienstkarte &quot;Adobe Target&quot;und klicken Sie auf Weiter.

![chlimage_1-39](assets/chlimage_1-39.png)

Im Dropdownmenü Konfiguration auswählen können Sie entweder eine neue Konfiguration erstellen oder aus einer vorhandenen auswählen. Um eine neue Konfiguration zu erstellen, wählen Sie &quot;Konfiguration erstellen&quot; aus der Dropdownliste. Geben Sie einen Titel für die Target-Konfiguration ein. Geben Sie Ihren Clientcode, Ihre E-Mail-Adresse und Ihr Kennwort ein, die mit Ihrem Target-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target-Support. Klicken Sie auf die Schaltfläche &quot;Überprüfen&quot;, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche &quot;Senden&quot;, um den Cloud-Dienst zu erstellen.

>[!NOTE]
>
>Der Cloud-Dienst, der erstellt wird, wird über den Assistenten automatisch mit der mobilen Anwendung verknüpft. Der Wert der Eigenschaft cq:cloudserviceConfigs wird auf dem Knoten jcr:content des Knoten apps group festgelegt. Für das Hybrid-App-Beispiel wird es unter &quot;/content/mobileapps/hybrid-reference-app/jcr:content&quot;festgelegt. Der Wert verweist auf den automatisch generierten Framework-Knoten unter &quot;/etc/cloudservices/testandtarget/adobe-target—aem-apps/framework&quot;. Der Framework-Knoten verfügt über zwei Eigenschaften, die standardmäßig festgelegt sind: Geschlecht und Alter. Das Framework wird nur von der AEM-Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel &quot;Cloud-Dienst verwalten&quot;den Target-Cloud-Dienst, enthält jedoch eine Warnung über ein fehlendes Adobe Mobile Service-Konto.

![chlimage_1-40](assets/chlimage_1-40.png)

### Adobe Mobile Services {#adobe-mobile-services}

Es ist erforderlich, ein Adobe Mobile Services (AMS)-Konto auch mit der Anwendung zu verknüpfen. Der AMS-Dienst stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Target-Clientcodeinformationen enthält. Vor dem Erstellen einer Verbindung mit dem AMS-Konto muss das AMS-Konto von einem Benutzer geändert werden, der über die Berechtigung für AMS verfügt.

### Client-Code {#client-code}

Um sich bei den AMS-Diensten anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die mobile Anwendung aus und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK-Target-Optionen, platzieren Sie den Clientcode in das Feld und klicken Sie auf Speichern.

![chlimage_1-41](assets/chlimage_1-41.png)

Nachdem der Clientcode mit der mobilen Anwendung verknüpft wurde, werden die Einstellungen für die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Dienst über das Adobe Mobile Dashboard konfiguriert wird.

### Adobe Mobile Service Cloud Service {#adobe-mobile-service-cloud-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die mobile Anwendung im Adobe Mobile Dashboard zu verknüpfen. Suchen Sie im AEM Mobile Dashboard die Option Cloud-Dienste verwalten und klicken Sie auf die Schaltfläche +.

![chlimage_1-42](assets/chlimage_1-42.png)

Wählen Sie die Adobe Mobile Services-Karte und klicken Sie auf Weiter.

![chlimage_1-43](assets/chlimage_1-43.png)

Wählen Sie im Schritt Erstellen oder Auswählen des Assistenten das Dropdown-Menü Mobile Service und wählen Sie den Eintrag Konfiguration erstellen. Geben Sie einen Titel, ein Unternehmen, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Adobe Mobile Service-Administrator, um sie zu erhalten. Klicken Sie nach dem Ausfüllen aller Felder auf die Schaltfläche Überprüfen. Der Überprüfungsprozess wird an AMS gesendet und überprüft die Anmeldeinformationen für das Konto. Bei erfolgreicher Überprüfung wird eine Liste mit Mobilanwendungen gefüllt, in der Sie die zugehörige Mobilanwendung aus der Dropdownliste auswählen. Klicken Sie auf die Schaltfläche &quot;Senden&quot;, um den Assistenten abzuschließen. Der Prozess kann einige Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle damit verbundenen Analysen der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs im Modal auf die Schaltfläche Fertig, um zum Adobe Mobile Dashboard zurückzukehren.

Bei Rückkehr zum Mobile Dashboard enthält die Kachel &quot;Cloud-Dienste verwalten&quot;den AMS-Cloud-Dienst. Sie werden außerdem feststellen, dass die Kachel &quot;Analytics-Metriken&quot;mit Lebenszyklusberichten gefüllt wird.

![chlimage_1-44](assets/chlimage_1-44.png)

## Für Autoren {#for-authors}

**** Voraussetzung: Wie oben erwähnt, müssen Administratoren die Verbindung zum Adobe Target-Dienst konfigurieren, bevor Autoren neue zielgerichtete Inhalte erstellen können.

Nachdem der Administrator die beiden Cloud-Dienste konfiguriert und der Entwickler den Handler mobileappoffers konfiguriert hat, können Inhaltsersteller jetzt mit der Generierung zielgerichteter Erlebnisse beginnen.

Beim Erstellen zielgerichteter Inhalte in einer AEM Mobile-App wird eine ähnliche Vorgehensweise wie beim Erstellen von AEM-Sites angewendet:

Eine vollständige Übersicht zum [Authoring zielgerichteter Inhalte in AEM finden Sie hier](/help/sites-authoring/personalization.md)

## Für Entwickler {#for-developers}

AEM-Entwickler, die mobile Anwendungen erstellen, sollten weiterhin den in AEM üblichen Mustern bei der Entwicklung von Komponenten folgen. Hier führen wir Sie durch die erforderlichen Schritte, damit Autoren von Inhalten zielgerichtete Inhalte erstellen können:

### Adobe Target ContentSync-Handler {#adobe-target-contentsync-handlers}

Die Bereitstellung von Inhalten für den Geräteinhalt des Benutzers wird durch die Wiedergabe der von AEM-Inhaltserstellern erstellten Angebote generiert. Zur Verarbeitung der Wiedergabe von Zielangeboten gibt es einen neuen Content-Synchronisierungs-Handler, der die Angebote verarbeitet. Mit der Hybrid-Referenzanwendung als Beispiel enthält das en-Inhaltspaket (Englisch) ContentSyncConfig mit einem [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml) -Handler. Der nächste Schritt ist entscheidend für die Wiedergabe von Angeboten an das Gerät. Der Handler mobileappoffers verfügt über eine Pfadeigenschaft, die den Pfad zur Personalisierungsaktivität angibt, die für die Anwendung verwendet werden soll.

Wenn sich beispielsweise eine Aktivität unter */content/campaigns/hybridref* befindet, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in die *path* -Eigenschaft des Handlers mobileappoffers ein.

>[!NOTE]
>
>Für die Hybrid-Referenzanwendung gibt es zwei Handler für mobileappoffers: einen für den dev und einen für Produktionen.

Nachdem der Aktivitätspfad in der pfadeigenschaft des Handlers mobileappoffers festgelegt wurde, speichern Sie den Handler. Der Handler ist nun bereit, Angebote für unsere Mobilgeräte zu rendern.

### Rendermodus {#render-mode}

Der Handler mobileappoffers wird für Veröffentlichungs- und Entwicklungs-Setups anders konfiguriert. Für Veröffentlichungseinstellungen gibt es die Eigenschaft *renderMode* mit dem Wert *publish* , der auf dem Knoten cq:ContentSyncConfig festgelegt ist. Der Handler mobileappoffers verweist auf den renderMode und ändert, wenn er auf &quot;publish&quot;eingestellt ist, die erstellte mbox-ID. Standardmäßig wird an die mbox-ID ein —author-Wert angehängt, der von AEM erstellt wird. Dadurch wird festgestellt, dass die Aktivität noch nicht veröffentlicht wurde, und die unveröffentlichte Kampagne sollte für Angebotsauflösungen verwendet werden.

Wenn Inhalte über das Adobe Mobile Dashboard gestaffelt werden, werden gestaffelte Inhalte als produktionsfertige Inhalte betrachtet und über die Content Sync-Konfiguration ohne Entwicklungsabgleich wiedergegeben. Bei einer solchen Wiedergabe wird —author aus allen mbox-IDs entfernt und erwartet, dass eine veröffentlichte Aktivität auf dem Target-Server verfügbar ist. Bevor Sie gestaffelte Inhalte testen, stellen Sie sicher, dass die Aktivität veröffentlicht wurde.

### Entwicklung von Personalisierungs-Apps {#personalization-app-development}

#### Komponenten {#components}

Die Grundlage für alle Inhalte ist normalerweise eine Seitenkomponente, die eine der AEM-Basisseitenkomponenten wcm/foundation/components/page oder foundation/components/page erweitert, je nachdem, ob Sie HTML oder JSPs verwenden. Die Dauer dieser Schritte konzentriert sich auf die Verwendung der Komponente &quot;wcm/foundation/components/page&quot;. Die Grundstruktur der Seitenkomponente wird in mehrere Skripten unterteilt, wobei jedes Skript den Entwicklern die Möglichkeit gibt, ihren Code bei Bedarf zu organisieren und zu überschreiben. Die beiden Skripten, die für Personalisierung von Interesse sind, sind head.html und body.html. Diese beiden Skripten bieten einen Bereich, in dem Code zur Unterstützung des Context Hub-, Cloud Services- und Mobile-Authoring eingefügt werden kann.

Im Folgenden finden Sie eine Übersicht über die beiden primären Skripten, die zum Aktivieren des Content-Targeting verwendet werden.

#### head.html {#head-html}

Um dem Autor die Möglichkeit zu geben, seinen Inhalt zielgerichtet zu gestalten, muss das Zielmenü der Seite hinzugefügt werden, damit der Autor den Kontext vom Bearbeitungsmodus zum Targeting-Modus wechseln kann. Um diese Funktion zu aktivieren, sollte der Entwickler das Skript head.html so ändern, dass es den folgenden Codeausschnitt am Anfang der head.html-Datei oder möglichst nahe am &lt;title>&lt;/title>-Element enthält.

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

Damit Autoren die Möglichkeit erhalten, eine Vorschau des zielgerichteten Inhalts anzuzeigen, muss der Editor die Konfiguration des Adobe Target-Cloud-Dienstes finden können. Im folgenden Codeblock werden zwei wichtige Skripten hinzugefügt. Das erste Hinzufügen der Fähigkeit der Seite, den zugehörigen Target-Cloud-Dienst zu finden und die Aufrufe an Adobe Target abzugeben. Der zweite ist der Zusatz der Kategorie &quot;cq.apps.targeting&quot;.

Die **Kategorie &quot;cq.apps.targeting** &quot;überschreibt die Standardkomponente &quot;cq/personalization/component/target&quot;und verwendet die Komponente &quot;mobileapps/components/target&quot;, die Angebote speziell für den Mobilanwendungskonsum rendert. Weitere Informationen dazu finden Sie im Abschnitt Target-Komponente.

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

### Referenz-Anwendung {#reference-application}

Beispiele für head.html und body.html finden Sie in der [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) , die dem Entwickler zeigt, wo die Skriptblöcke in den beiden Skripten platziert werden sollen.

### Content Sync-Handler {#content-sync-handlers}

Wenn der Autor des Inhalts die Erstellung von Inhalten für die mobile Anwendung abgeschlossen hat, müssen Sie als Nächstes die Quelle herunterladen und die Anwendung erstellen oder die zu veröffentlichenden Inhalte bereitstellen. Es gibt eine Reihe von Schritten, die der Entwickler durchführen muss, um dies zu erreichen. Um die Wiedergabe des Inhalts zu unterstützen, verwendet AEM Mobile Content Sync-Handler, um den Inhalt zu rendern und zu verpacken. Für den Anwendungsfall &quot;Personalisierung&quot;wurde ein neuer Content-Synchronisierungs-Handler eingeführt, um zielgerichtete Inhalte wiederzugeben. Der Handler &quot;mobileappoffers&quot;weiß, wie die verknüpften Zielangebote wiedergegeben werden, die vom Autor des Inhalts erstellt wurden. Der Handler mobileappoffers erweitert den Updatehandler für abstrakte Seiten, daher sind viele Eigenschaften ähnlich. Die Details des Handlers mobileappoffers haben die folgenden Eigenschaften.

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
   <td>Die rewrite-Eigenschaft gibt an, wie Pfade im Inhalt umgeschrieben werden sollen.</td>
  </tr>
  <tr>
   <td>includePageTypes</td>
   <td><p>"cq/personalization/components/teaserpage",</p> <p>"cq/personalization/components/offerproxy"</p> </td>
   <td>Die Eigenschaft includePageTypes ist optional. Standardmäßig werden Seiten mit den Ressourcentypen cq/personalization/components/teaserpage und cq/personalization/components/offerproxy verwendet. Diese beiden Ressourcentypen sind die Standard-Ressourcentypen, die beim Targeting von Inhalten verwendet werden. Wenn zusätzliche Ressourcentypen unterstützt werden müssen, sollten sie der Liste der includePageTypes hinzugefügt werden.</td>
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
   <td>true| false</td>
   <td>Wenn "true", werden alle im Angebot enthaltenen Bilder gerendert. Wenn FALSE-Bilder übersprungen werden.</td>
  </tr>
  <tr>
   <td>includeVideos</td>
   <td>true| false</td>
   <td>Wenn "true", werden alle im Angebot enthaltenen Videos gerendert. Wenn "false", werden Videos übersprungen.</td>
  </tr>
  <tr>
   <td>path</td>
   <td>/content/campaigns/&lt;brand&gt;</td>
   <td>Verweist auf die Marke der Kampagne, an der die Angebote teilnehmen. Derzeit müssen alle Angebote aus derselben Kampagne stammen.</td>
  </tr>
  <tr>
   <td>tief</td>
   <td>true| false</td>
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
>Die [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) verfügt über die Standardkonfiguration des Handlers mobileappoffer. Die Pfadeigenschaft im Beispiel ist leer, da sie vom Kampagnenort abhängt. Nachdem ein Kampagnenautor eine Kampagne erstellt hat, sollte der Apps-Administrator die Kampagne mit dem Handler verknüpfen, indem er die Pfadeigenschaft angibt, die auf die Kampagne verweist.

### Zielkomponente {#target-component}

Um Inhalte speziell für mobile Anwendungen wiederzugeben, verwendet AEM Mobile die Komponente mobileapps/components/target. Die mobile Zielkomponente erweitert die Komponente cq/personalization/components/target und überschreibt das Skript engine_tnt.jsp. Durch Überschreiben der Datei &quot;engine_tnt.jsp&quot;kann AEM Mobile den generierten HTML-Code für die Anwendungsfälle mobiler Apps steuern. Für jede Komponente, die auf einen Inhaltsersteller ausgerichtet ist, wird eine verknüpfte mbox von der Datei engine_tnt.jsp erstellt.

Für jede mbox wird ein Attribut des **cq-targeting** hinzugefügt, das Anwendungsentwicklern die Möglichkeit gibt, benutzerspezifischen Code zu schreiben, um ihn zu nutzen und zu verwenden, wie es ihnen gefällt. Die [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) enthält ein Beispiel für eine Angular-Direktive, die das Attribut cq-targeting verwendet. Das Konzept des Ersatzes von Inhalten, wann und wie er durchgeführt wird, liegt sehr am Entwickler von mobilen Anwendungen. Es gibt ein mobiles SDK, das über AEM /etc/clientlibs/mobileapps/js/mobileapps.js bereitgestellt wird und eine API zum Aufrufen des Adobe Targeting-Dienstes bereitstellt. Es ist Sache des Anwendungsentwicklers, anzugeben, wann dieser Aufruf gemäß dem Design ihrer Anwendung erfolgen soll.

## Wie geht es weiter? {#what-s-next}

1. [Mein AEM Mobile App-Erlebnis](/help/mobile/starting-aem-phonegap-app.md) 
1. [Verwalten des App-Inhalts](/help/mobile/phonegap-manage-app-content.md) 
1. [Erstellen meiner Anwendung](/help/mobile/building-app-mobile-phonegap.md) 
1. [Messen der Leistung meiner App mit Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md) 
1. [Ein personalisiertes App-Erlebnis mit Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md) 
1. [Senden wichtiger Nachrichten an meine Benutzer](/help/mobile/phonegap-push-notifications.md) 
