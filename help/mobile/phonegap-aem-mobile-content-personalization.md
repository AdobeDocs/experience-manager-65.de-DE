---
title: Adobe Experience Manager Mobile-Inhaltspersonalisierung
description: Auf dieser Seite erfahren Sie mehr über die Adobe-Personalisierungsfunktion für mobile Inhalte in Experience Manager (AEM), mit der AEM-Autorinnen und -Autoren Inhalte für mobile Apps mithilfe von Adobe Target personalisieren können.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 70d7ee0d-2f6d-4f97-a6e2-b02d84a0ca42
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2571'
ht-degree: 2%

---

# AEM Mobile-Inhaltspersonalisierung{#aem-mobile-content-personalization}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Dieses Dokument ist Teil des Handbuchs [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md), ein empfohlener Ausgangspunkt für die AEM Mobile-Referenz.

Mit der Inhaltspersonalisierungsfunktion von AEM Mobile können [AEM-Autoren](#author) Inhalte von Mobile Apps mithilfe von [Adobe Target personalisieren](https://business.adobe.com/de/products/target/adobe-target.html). Dies ermöglicht die Bereitstellung zielgerichteter Angebote für Benutzende von Mobile Apps. Adobe Experience Manager Mobile bietet die Möglichkeit, Inhalte zu erstellen, anzusprechen und bereitzustellen, die den Benutzenden Inhalte bieten, die für ihren eigenen Geschmack spezifisch sind.

Damit Autorinnen und Autoren mit der Erstellung dieses Inhalts in AEM beginnen können, müssen Administratoren und Entwicklerinnen und Entwickler zunächst die Umgebung vorbereiten.

[AEM-](#administrator): sind erforderlich, um eine Verbindung zwischen AEM Mobile und dem Adobe Target-Cloud Service herzustellen.

In der Zwischenzeit müssen AEM Mobile [Entwickler](#developer) ihre vorhandenen Skripte bearbeiten, um die zielgerichtete Inhaltserstellung zu erleichtern.

## Für Administratoren {#for-administrators}

Es gibt mehrere Schritte, die zusammengeführt werden müssen, bevor Inhaltsautorinnen und -autoren mit der Generierung zielgerichteter Inhalte für mobile Apps beginnen können: Es gibt den richtigen Berechtigungssatz für Benutzende und Gruppen, die Erstellung von Cloud-Services, die Konfiguration der Anwendung für die Aktivität und schließlich die Erstellung des Inhalts.

Dieser Artikel führt Sie durch den Prozess, der zum Konfigurieren der [AEM Mobile Hybrid-Referenzanwendung](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) für das Targeting verwendet wird.

Es wird davon ausgegangen, dass die AEM Mobile Hybrid-Referenzanwendung erfolgreich bereitgestellt wurde und über das AEM Mobile-Dashboard zugänglich ist.

Bevor Autorinnen und Autoren zielgerichtete Inhalte innerhalb eines Programms generieren können, muss Ihre AEM-Instanz [mit dem Adobe Target-Cloud Service konfiguriert“ werden](/help/mobile/aem-mobile-configuring-cloud-service.md)

### Berechtigungen {#permissions}

Benutzer, die Zugriff auf die Personalisierungskonsole benötigen, müssen Teil der `target-activity-authors` sein.

Es wird empfohlen, die target-activity-group im Rahmen der Benutzer- und Gruppeneinrichtung der Gruppe apps-admins hinzuzufügen. Durch Hinzufügen der Gruppe target-activity-authors können Benutzerinnen und Benutzer den Menüeintrag Personalization-Navigation sehen.

>[!NOTE]
>
>Wenn Sie vergessen haben, die Benutzenden oder Gruppen, auf die Sie Zugriff haben möchten, zur Admin Console target-activity-authors hinzuzufügen, wird verhindert, dass Benutzende die Personalisierungskonsole sehen.

### Cloud Services {#cloud-services}

Damit zielgerichtete Inhalte für Mobile Apps funktionieren, müssen zwei Services konfiguriert werden: der Adobe Target-Service und der Adobe Mobile Services-Service. Der Adobe Target-Service stellt die Engine zum Verarbeiten von Client-Anfragen und Zurückgeben der personalisierten Inhalte bereit. Der Service Adobe Mobile Services stellt die Verbindung zwischen den Adobe-Services und der Mobile App über die Datei ADBMobileConfig.json her, die vom AMS Cordova-Plug-in genutzt wird. Über das AEM Mobile-Dashboard können Sie Ihr Programm konfigurieren, indem Sie die beiden Services hinzufügen.

Suchen Sie im AEM Mobile-Dashboard nach der Option Cloud Service verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-38](assets/chlimage_1-38.png)

Wählen Sie im Assistenten &quot;Cloud Service hinzufügen“ die Cloud Service-Karte &quot;Adobe Target&quot; aus und klicken Sie auf Weiter.

![chlimage_1-39](assets/chlimage_1-39.png)

In der Dropdown-Liste Konfiguration auswählen können Sie entweder eine Konfiguration erstellen oder aus einer vorhandenen auswählen. Um eine Konfiguration zu erstellen, wählen Sie aus dem Dropdown-Menü „Konfiguration erstellen“ aus. Geben Sie einen Titel für die Target-Konfiguration ein. Geben Sie den Clientcode, die E-Mail-Adresse und das Kennwort ein, die mit Ihrem Target-Konto verknüpft sind. Wenn Sie die Werte für diese Felder nicht kennen, wenden Sie sich an den Adobe Target-Support. Klicken Sie auf die Schaltfläche „Überprüfen“, um die Anmeldeinformationen zu überprüfen. Klicken Sie nach der Überprüfung auf die Schaltfläche Senden , um den Cloud-Service zu erstellen.

>[!NOTE]
>
>Der erstellte Cloud-Service wird über den Assistenten automatisch mit der Mobile App verknüpft. Der Wert der Eigenschaft cq:cloudserviceconfigs wird auf dem Knoten jcr:content des Gruppenknotens apps festgelegt. Für das Beispiel der Hybrid-App wird sie unter /content/mobileapps/hybrid-reference-app/jcr:content festgelegt, wobei der Wert auf den automatisch generierten Framework-Knoten unter /etc/cloudservices/testandtarget/adobe-target—aem-apps/framework verweist. Für den Framework-Knoten sind standardmäßig zwei Eigenschaften festgelegt: Geschlecht und Alter. Das Framework wird nur von der AEM-Vorschau verwendet und hat keine Auswirkungen auf das Gerät.

Nach Abschluss des Assistenten enthält die Kachel Cloud Service verwalten den Target-Cloud-Service. Sie enthält jedoch eine Warnung zu einem fehlenden Adobe Mobile Service-Konto.

![chlimage_1-40](assets/chlimage_1-40.png)

### Adobe Mobile Services {#adobe-mobile-services}

Es ist auch erforderlich, ein Adobe Mobile Services (AMS)-Konto mit der Anwendung zu verknüpfen. Der AMS-Service stellt die erforderliche Datei ADBMobileConfig.json bereit, die die Target-Client-Code-Informationen enthält. Bevor Sie eine Verknüpfung mit dem AMS-Konto erstellen, muss das AMS-Konto von einem Benutzer geändert werden, der über Berechtigungen für AMS verfügt.

### Client-Code {#client-code}

Um sich bei den AMS-Services anzumelden, besuchen Sie [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), wählen Sie die Mobile App aus und klicken Sie auf die Einstellungen. Suchen Sie das Feld SDK Target-Optionen , platzieren Sie den Client-Code in das Feld und klicken Sie auf Speichern .

![chlimage_1-41](assets/chlimage_1-41.png)

Nachdem der Client-Code mit der Mobile App verknüpft wurde, werden die Einstellungen für die Diensteinstellungen über die Datei ADBMobileConfig.json bereitgestellt, wenn der AMS-Cloud-Service über das Dashboard für mobile Adobe-Geräte konfiguriert ist.

### Adobe Mobile Service-Cloud Service {#adobe-mobile-service-cloud-service}

Nachdem AMS konfiguriert wurde, ist es an der Zeit, die Mobile App im Adobe Mobile Dashboard zu verknüpfen. Suchen Sie im AEM Mobile-Dashboard nach der Option Cloud Service verwalten und klicken Sie auf die Schaltfläche + .

![chlimage_1-42](assets/chlimage_1-42.png)

Wählen Sie die Karte Adobe Mobile Services aus und klicken Sie auf Weiter.

![chlimage_1-43](assets/chlimage_1-43.png)

Wählen Sie im Schritt Erstellen oder Assistenten auswählen die Dropdown-Liste Mobile Service und dann den Eintrag Konfiguration erstellen aus. Geben Sie einen Titel, ein Unternehmen, einen Benutzernamen und ein Kennwort ein und wählen Sie das entsprechende Rechenzentrum aus. Wenn Sie diese Werte nicht kennen, wenden Sie sich an Ihren Adobe Mobile Service-Administrator, um sie zu erhalten. Nachdem alle Felder ausgefüllt wurden, klicken Sie auf **Überprüfen**. Der Verifizierungsprozess wird an AMS gesendet und überprüft die Anmeldeinformationen für das Konto. Nach erfolgreicher Validierung wird eine Liste der Mobile Apps ausgefüllt, in der Sie die zugehörige Mobile App aus der Dropdown-Liste auswählen. Klicken Sie **Senden**, um den Assistenten abzuschließen. Der Vorgang kann einige Zeit in Anspruch nehmen, um die Konfigurationsdaten und alle zugehörigen Analysen der Anwendung abzurufen. Klicken Sie nach Abschluss des Vorgangs auf **Fertig**, um zum Adobe Mobile-Dashboard zurückzukehren.

Zurück zum mobilen Dashboard enthält die Kachel Cloud Service verwalten den AMS-Cloud-Service. Außerdem wird die Kachel Metriken analysieren mit Lebenszyklusberichten gefüllt.

![chlimage_1-44](assets/chlimage_1-44.png)

## Für Autoren {#for-authors}

**Voraussetzung:** oben erwähnt, müssen Admins die Verbindung zum Adobe Target-Service konfigurieren, bevor Autorinnen und Autoren neue zielgerichtete Inhalte generieren können.

Nachdem der Administrator die beiden Cloud-Services konfiguriert hat und der Entwickler den Mobile-App-Angebots-Handler konfiguriert hat, können Inhaltsautoren jetzt mit der Generierung zielgerichteter Erlebnisse beginnen.

Das Verfassen zielgerichteter Inhalte in einer AEM Mobile-App erfolgt auf ähnliche Weise wie das Verfassen von AEM Sites:

Hier finden Sie einen vollständigen Überblick über [Authoring zielgerichteter Inhalte in AEM](/help/sites-authoring/personalization.md)

## Für Entwickler {#for-developers}

AEM-Entwickler, die Mobile Apps erstellen, sollten bei der Entwicklung von Komponenten weiterhin den üblichen AEM-Mustern folgen. Hier führt Sie Adobe durch die erforderlichen Schritte, die es Inhaltsautorinnen und -autoren ermöglichen, zielgerichtete Inhalte zu erstellen:

### Adobe Target ContentSync-Handler {#adobe-target-contentsync-handlers}

Um Inhalte auf dem Gerät des Benutzers bereitzustellen, werden Inhalte durch das Rendern von Angeboten generiert, die von AEM-Inhaltsautoren erstellt wurden. Für das Rendering von Target-Angeboten gibt es einen neuen Inhaltssynchronisierungs-Handler, der die Angebote verarbeitet. Unter Verwendung der Hybrid-Referenzanwendung als Beispiel enthält das Inhaltspaket en (Englisch) den ContentSyncConfig mit einem [mobileAppOffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml)-Handler. Der nächste Schritt ist wichtig, um Angebote auf dem Gerät zu rendern. Der mobileAppOffers-Handler verfügt über eine path-Eigenschaft, die den Pfad zur Personalisierungsaktivität angibt, die für die Anwendung verwendet werden soll.

Wenn beispielsweise eine Aktivität unter */content/campaigns/hybridref* vorhanden ist, kopieren Sie diesen Pfad und fügen Sie ihn als Wert in die Eigenschaft *path* des MobileAppOffers-Handlers ein.

>[!NOTE]
>
>Für die Hybrid-Referenzanwendung gibt es zwei mobile App-Handler, einen für die Entwicklung und einen für Produktionen.

Nachdem der Aktivitätspfad in der Path-Eigenschaft des MobileAppOffers-Handlers festgelegt wurde, speichern Sie den Handler. Der Handler ist jetzt bereit, um mit dem Rendern von Angeboten für Mobilgeräte zu beginnen.

### Render-Modus {#render-mode}

Der MobileAppOffers-Handler ist für Veröffentlichungs- und Entwicklungs-Setups unterschiedlich konfiguriert. Bei Veröffentlichungseinstellungen gibt es eine Eigenschaft mit dem Namen *renderMode* mit dem Wert *publish*, der auf dem Knoten cq:ContentSyncConfig festgelegt ist. Der mobileAppOffers-Handler verweist auf den renderMode und bearbeitet, wenn er auf publish festgelegt ist, die erstellte mbox id. Standardmäßig wird bei Mboxes, die von AEM erstellt werden, ein —author-Wert an die mbox-ID angehängt. Dadurch wird erkannt, dass die Aktivität nicht veröffentlicht wurde und die nicht veröffentlichte Kampagne zur Angebotsauflösung verwenden sollte.

Wenn Inhalte über das Dashboard für mobile Adobe-Geräte bereitgestellt werden, werden bereitgestellte Inhalte als produktionsbereite Inhalte betrachtet und über die Konfiguration der Inhaltssynchronisierung ohne Entwicklung gerendert. Wenn Sie auf diese Weise rendern, wird —author aus allen mbox-IDs entfernt und erwartet, dass eine veröffentlichte Aktivität auf dem Target-Server verfügbar ist. Stellen Sie vor dem Testen von Staging-Inhalten sicher, dass die Aktivität bereits veröffentlicht ist.

### Personalization-App-Entwicklung {#personalization-app-development}

#### Komponenten {#components}

Die Grundlage für jeden Inhalt ist in der Regel eine Seitenkomponente, die entweder die AEM-Basisseitenkomponenten „wcm/foundation/components/page“ oder „foundation/components/page“ erweitert, je nachdem, ob Sie HTL oder JSPs verwenden. Die Dauer dieser Schritte konzentriert sich auf die Verwendung der Komponente wcm/foundation/components/page . Die grundlegende Struktur der Seitenkomponente ist in mehrere Skripte unterteilt, wobei jedes Skript den spezifischen Zweck erfüllt, es dem Entwickler zu ermöglichen, seinen Code bei Bedarf zu organisieren und zu überschreiben. Die beiden Skripte, die für Personalization von Interesse sind, sind head.html und body.html. Diese beiden Skripte bieten einen Bereich, in den Code eingefügt werden kann, um ContextHub, Cloud Service und mobiles Authoring zu unterstützen.

Im Folgenden finden Sie eine Übersicht über die beiden primären Skripte, die zum Aktivieren des Content-Targeting verwendet werden.

#### head.html {#head-html}

Um Autorinnen und Autoren die Möglichkeit zu geben, ihre Inhalte auszuwählen, muss das Zielmenü zur Seite hinzugefügt werden, damit Autorinnen und Autoren den Kontext vom Bearbeitungsmodus in den Targeting-Modus ändern können. Um diese Funktion zu aktivieren, sollte der Entwickler das Skript head.html so ändern, dass das folgende Codefragment am Anfang der Datei head.html oder so nah wie möglich am Element &lt;title>&lt;/title> eingefügt wird.

```xml
<meta data-sly-test="${!wcmmode.disabled}">
    <div data-sly-call="${clientLib.all @ categories='personalization.kernel'}" data-sly-unwrap></div>
    <div data-sly-resource="${'config' @ resourceType='cq/personalization/components/clientcontext_optimized/config'}" data-sly-unwrap></div>
    <div data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}" data-sly-unwrap></div>
</meta>
```

>[!NOTE]
>
>Schließen Sie das Skript nur ein, wenn der WCM-Modus deaktiviert ist. Wenn der WCM-Modus deaktiviert ist (Details finden Sie im Abschnitt zum ContentSync-Handler), wird das Skript nicht in den endgültigen Anwendungs-Code aufgenommen.

Um Autorinnen und Autoren die Möglichkeit zu geben, eine Vorschau der zielgerichteten Inhalte anzuzeigen, muss der Editor in der Lage sein, die Konfiguration des Adobe Target-Cloud-Service zu finden. Der folgende Code-Block fügt zwei wichtige Skripte hinzu. Das erste, das die Möglichkeit hinzufügt, dass die Seite den zugehörigen Target-Cloud-Service findet und die Aufrufe an Adobe Target sendet. Als zweites wird die Kategorie cq.apps.targeting hinzugefügt.

Die Kategorie **CQ.apps.** überschreibt die standardmäßige Komponente CQ/Personalization/Component/Target und verwendet die Komponente MobileApps/Components/Target, die Angebote speziell für die Nutzung durch Mobile Apps rendert. Weitere Informationen hierzu finden Sie im Abschnitt Target-Komponente .

Der Code sollte in der Datei head.html hinzugefügt und direkt vor dem Ende des Elements &lt;/head> platziert werden.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-include="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" data-sly-unwrap></div>
    <meta data-sly-call="${clientLib.all @ categories='cq.apps.targeting'}" data-sly-unwrap></meta>
</div>
```

>[!NOTE]
>
>Der Codeblock wird in einem WCM-Modus umschlossen, der nicht deaktiviert wird. Daher kommt er nur zum Tragen, während der Inhaltsautor an der Erstellung von Inhalten arbeitet. Die Cloud Service-Skripte werden nicht zum generierten mobilen Runtime-Code hinzugefügt.

#### body.html {#body-html}

Damit Inhaltsautorinnen und -autoren verschiedene Rollen testen können, muss das Skript body.html den folgenden Codeblock als erstes untergeordnetes Element des body-Elements enthalten.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-resource="${'clientcontext' @ resourceType='cq/personalization/components/clientcontext_optimized'}" data-sly-unwrap></div>
</div>
```

Das letzte erforderliche Code-Fragment befindet sich am unteren Rand von body.html. Dieser Code sucht nach dem zugehörigen Cloud Service und fügt den entsprechenden Code der Targeting-Engine ein.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-resource="${'cloudservices' @ resourceType='cq/cloudserviceconfigs/components/servicecomponents'}" data-sly-unwrap></div>
</div>
```

### Referenzanwendung {#reference-application}

Beispiele für head.html und body.html finden Sie in der [AEM Mobile Hybrid Reference Application](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) die dem Entwickler zeigt, wo die Skriptblöcke in den beiden Skripten platziert werden sollen.

### Content Sync Handler {#content-sync-handlers}

Wenn der Inhaltsautor die Erstellung des Inhalts für die Mobile App abgeschlossen hat, besteht der nächste Schritt darin, die Quelle herunterzuladen und die App zu erstellen oder den zu veröffentlichenden Inhalt zu inszenieren. Es gibt mehrere Schritte, an denen der Entwickler beteiligt ist, um dies zu ermöglichen. Um das Rendern des Inhalts zu unterstützen, verwendet AEM Mobile Inhaltssynchronisierungs-Handler zum Rendern und Verpacken des Inhalts. Für den Personalization-Anwendungsfall zum Rendern zielgerichteter Inhalte wurde ein neuer Content-Sync-Handler eingeführt. Der Handler &#39;mobileAppOffers&#39; weiß, wie die zugehörigen Zielangebote gerendert werden, die vom Inhaltsautor erstellt wurden. Der MobileAppOffers-Handler erweitert den Aktualisierungs-Handler für abstrakte Seiten. Daher sind viele Eigenschaften ähnlich. Die Details des MobileAppOffers-Handlers haben die folgenden Eigenschaften.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>umschreiben</td>
   <td>+ relativeParentPath<p> - "/"</p> </td>
   <td>Die Eigenschaft rewrite gibt an, wie Pfade innerhalb des Inhalts neu geschrieben werden sollen.</td>
  </tr>
  <tr>
   <td>includedPageTypes</td>
   <td><p>„cq/personalization/components/teaserpage“,</p> <p>„cq/personalization/components/offerProxy“</p> </td>
   <td>Die Eigenschaft includePageTypes ist optional. Standardmäßig werden Seiten verwendet, die die Ressourcentypen „cq/personalization/components/teaserpage“ oder „cq/personalization/components/offerProxy“ aufweisen. Diese beiden Ressourcentypen sind die Standard-Ressourcentypen, die verwendet werden, wenn Inhalte angesprochen werden. Wenn zusätzliche Ressourcentypen unterstützt werden müssen, fügen Sie sie zur Liste der includePageTypes hinzu.</td>
  </tr>
  <tr>
   <td>locationRoot</td>
   <td>/content/mobileapps/&lt;app&gt;</td>
   <td>Der Speicherort der App.</td>
  </tr>
  <tr>
   <td>Typ</td>
   <td>mobileAppOffers</td>
   <td>Der Name des Handlers, der von mobileApps angeboten wird.</td>
  </tr>
  <tr>
   <td>Selektor</td>
   <td>Tandt</td>
   <td>Der Standardselektor wird zum Rendern des zielgerichteten Inhalts verwendet. </td>
  </tr>
  <tr>
   <td>targetRootDirectory</td>
   <td>www</td>
   <td>Das Stammverzeichnis, in dem der gerenderte Inhalt beibehalten werden soll.</td>
  </tr>
  <tr>
   <td>includeImages</td>
   <td>wahr | falsch</td>
   <td>Wenn „true“, werden alle im Angebot enthaltenen Bilder gerendert. Bei „false“ werden Bilder übersprungen.</td>
  </tr>
  <tr>
   <td>Videos einschließen</td>
   <td>wahr | falsch</td>
   <td>Wenn „true“, werden alle im Angebot enthaltenen Videos gerendert. Bei „false“ werden Videos übersprungen.</td>
  </tr>
  <tr>
   <td>path</td>
   <td>/content/campaigns/&lt;Marke&gt;</td>
   <td>verweist auf die Marke der Kampagne, an der die Angebote teilnehmen. Derzeit müssen alle Angebote von derselben Kampagne stammen.</td>
  </tr>
  <tr>
   <td>tief</td>
   <td>wahr | falsch</td>
   <td>Wenn „true“, werden alle untergeordneten Seiten rekursiv gerendert. Wenn „false“, wird das nicht wiederholt. </td>
  </tr>
  <tr>
   <td>Erweiterung</td>
   <td>html</td>
   <td>Legt die Erweiterung für die Ressource fest, die gerendert wird. Legen Sie auf HTML fest, sodass die Seiten eine HTML-Erweiterung aufweisen.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die [AEM Mobile Hybrid Reference App](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) verfügt über die Standardkonfiguration des MobileAppAngebot-Handlers. Die Pfadeigenschaft im Beispiel ist leer, da sie vom Speicherort der Kampagne abhängt. Nachdem ein Kampagnenautor eine Kampagne erstellt hat, sollte der App-Administrator die Kampagne mit dem Handler verknüpfen, indem er die Pfadeigenschaft angibt, die auf die Kampagne verweisen soll.

### Target-Komponente {#target-component}

Um Inhalte speziell für Mobile Apps rendern zu können, verwendet AEM Mobile die Komponente „mobileApps/components/target“. Die mobile Target-Komponente erweitert die Komponente cq/personalization/components/target und überschreibt das Skript „engine_tnt.jsp“. Durch Überschreiben der engine_tnt.jsp kann AEM Mobile die generierte HTML für den Anwendungsfall „Mobile Apps“ steuern. Für jede Komponente, die Ziel eines Inhaltsautors ist, wird von engine_tnt.jsp eine zugehörige Mbox erstellt.

Für jede Mbox wird das Attribut **cq-**) hinzugefügt, sodass Anwendungsentwickler benutzerdefinierten Code schreiben können, der beliebig genutzt und verwendet werden kann. Die [AEM Mobile Hybrid Reference App](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) enthält ein Beispiel für eine Angular-Direktive, die das Attribut cq-targeting verwendet. Das Konzept der Ersetzung von Inhalten, wann und wie sie durchgeführt wird, liegt beim Entwickler der Mobile App. Es gibt eine Mobile SDK, die über die AEM /etc/clientlibs/mobileapps/js/mobileapps.js bereitgestellt wird und eine API zum Aufrufen des Adobe-Targeting-Services bereitstellt. Der Anwendungsentwickler kann festlegen, wann dieser Aufruf gemäß dem Design der Anwendung erfolgen soll.

## Wie geht es weiter? {#what-s-next}

1. [Mein AEM Mobile-App-Erlebnis starten](/help/mobile/starting-aem-phonegap-app.md)
1. [Inhalt meiner App verwalten](/help/mobile/phonegap-manage-app-content.md)
1. [Meine Anwendung erstellen](/help/mobile/building-app-mobile-phonegap.md)
1. [Leistung meiner App mit Adobe Mobile Analytics verfolgen](/help/mobile/phonegap-intro-to-app-analytics.md)
1. [Bereitstellen eines personalisierten App-Erlebnisses mit Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md)
1. [Senden wichtiger Nachrichten an meine Benutzer](/help/mobile/phonegap-push-notifications.md)
