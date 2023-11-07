---
title: Inhaltsbereitstellung
description: Erfahren Sie, wie Sie alle Inhalte in Adobe Experience Manager verwenden können, um das Targeting-App-Erlebnis bereitzustellen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 85e73679-684e-402f-8186-8b56d8bd9372
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---

# Inhaltsbereitstellung{#content-delivery}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mobile Apps sollten alle Inhalte in AEM nach Bedarf verwenden können, um das zielgerichtete App-Erlebnis bereitzustellen.

Dazu gehören die Verwendung von Assets, Site-Inhalten, CAAs-Inhalten (Over-the-Air) und benutzerdefinierten Inhalten, die möglicherweise eine eigene Struktur aufweisen.

>[!NOTE]
>
>**Over-the-Air-Inhalt** kann über ContentSync-Handler von einem der oben genannten stammen. Sie können sie verwenden, um ein Batch-Paket zu erstellen und mithilfe von ZIP-Dateien bereitzustellen und Aktualisierungen für diese Pakete zu verwalten.

Es gibt drei Hauptmaterialtypen, die Content Services bereitstellt:

1. **Assets**
1. **HTML-Inhalt verpackt (HTML/CSS/JS)**
1. **Kanalunabhängiger Inhalt**

![chlimage_1-154](assets/chlimage_1-154.png)

## Assets {#assets}

Asset-Sammlungen sind AEM Konstrukte, die Verweise auf andere Sammlungen enthalten.

Eine Asset-Sammlung kann über Content Services verfügbar gemacht werden. Der Aufruf einer Asset-Sammlung in einer Anfrage gibt ein Objekt zurück, das eine Liste der Assets einschließlich ihrer URLs ist. Der Zugriff auf Assets erfolgt über eine URL. Die URL wird in einem Objekt bereitgestellt. Beispiel:

* Eine Seitenentität gibt die JSON (Seitenobjekt) zurück, die eine Bildreferenz enthält. Die Bildreferenz ist eine URL, mit der die Asset-Binärdatei für das Bild abgerufen wird.
* Bei einer Anforderung einer Liste von Assets in einem Ordner wird die JSON-Datei mit Details zu allen Entitäten in diesem Ordner zurückgegeben. Diese Liste ist ein Objekt. Die JSON-Datei enthält URL-Verweise, mit denen die Asset-Binärdatei für jedes Asset in diesem Ordner abgerufen wird.

### Asset-Optimierung {#asset-optimization}

Ein Schlüsselwert von Content Services ist die Möglichkeit, Assets zurückzugeben, die für das Gerät optimiert sind. Dadurch werden die Anforderungen an die lokale Gerätespeicherung reduziert und die App-Leistung verbessert.

Die Asset-Optimierung ist eine serverseitige Funktion, die auf den in der API-Anfrage bereitgestellten Informationen basiert. Wo immer möglich, sollten die Asset-Ausgabedarstellungen zwischengespeichert werden, sodass ähnliche Anforderungen keine Neuerstellung der Asset-Ausgabedarstellung erfordern.

### Assets-Workflow {#assets-workflow}

Der Asset-Workflow sieht wie folgt aus:

1. Asset-Referenz verfügbar in AEM nativen
1. Erstellen einer Asset-Referenzentität anhand ihres Modells
1. Entität bearbeiten

   1. Auswählen eines Assets oder einer Asset-Sammlung
   1. JSON-Rendering anpassen

Das folgende Diagramm zeigt die **Asset-Referenz-Workflow**:

![chlimage_1-155](assets/chlimage_1-155.png)

### Verwalten von Assets {#managing-assets}

Content Services bieten Zugriff auf AEM verwaltete Assets, auf die möglicherweise nicht über andere AEM verwiesen wird.

#### Vorhandene verwaltete Assets {#existing-managed-assets}

Ein Benutzer von AEM Sites und Assets verwendet AEM Assets, um alle digitalen Inhalte für alle Kanäle zu verwalten. Sie entwickeln eine native mobile App und müssen mehrere Assets verwenden, die von AEM Assets verwaltet werden. Zum Beispiel Logos, Hintergrundbilder und Schaltflächensymbole.

Derzeit sind diese auf das Assets-Repository verteilt. Die Dateien, auf die die App verweisen muss, lauten wie folgt:

* /content/dam/geometrixx-outdoors/brand/logo_light.png
* /content/dam/geometrixx-outdoors/brand/logo_dark.png
* /content/dam/geometrixx-outdoors/styles/backgrounds/gray_blue.jpg
* /content/dam/geometrixx-outdoors/brand/icons/app/cart.png
* /content/dam/geometrixx-outdoors/brand/icons/app/home.png

#### Zugreifen auf CS Asset-Entitäten {#accessing-cs-asset-entities}

Lassen wir die Schritte beiseite, die zeigen, wie die Seite zunächst über die API zur Verfügung gestellt wird (sie wird durch die Beschreibung der AEM UI abgedeckt), und gehen Sie davon aus, dass sie abgeschlossen ist. Asset-Entitäten wurden erstellt und zum Bereich &quot;appImages&quot;hinzugefügt. Zusätzliche Ordner wurden aus organisatorischen Gründen unter dem Bereich erstellt. Daher werden die Asset-Entitäten im AEM JCR wie folgt gespeichert:

* /content/entity/appImages/logos/logo_light
* /content/entity/appImages/logos/logo_dark
* /content/entity/appImages/bkgnd/gray_blue
* /content/entity/appImages/icons/cart
* /content/entity/appImages/icons/home

#### Abrufen einer Liste der verfügbaren Asset-Entitäten {#getting-a-list-of-available-asset-entities}

Ein App-Entwickler kann eine Liste der verfügbaren Assets abrufen, indem er die Asset-Entitäten abruft. Der Leerzeichen-Endpunkt von Content Services kann diese Informationen über das Web Service API SDK bereitstellen.

Das Ergebnis wäre ein Objekt im JSON-Format, das eine Liste der Assets im Ordner &quot;Symbole&quot;bereitstellt.

![chlimage_1-156](assets/chlimage_1-156.png)

#### Abrufen eines Bildes {#getting-an-image}

Die JSON stellt für jedes von Content Services generierte Bild eine URL für das Bild bereit.

Um die Binärdatei für das &quot;Warenkorb&quot;-Bild zu erhalten, wird die Client-Bibliothek erneut verwendet.

## Paketmäßiger HTML-Inhalt {#packaged-html-content}

HTML-Inhalte sind für Kunden erforderlich, die das Layout des Inhalts beibehalten müssen. Dies ist nützlich für native Anwendungen, die einen Webcontainer verwenden (z. B. eine Cordova-Webansicht), um den Inhalt anzuzeigen.

AEM Content Services stellt der mobilen App über die API HTML-Inhalte zur Verfügung. Kunden, die AEM Inhalt als HTML verfügbar machen möchten, können eine HTML-Seitenentität erstellen, die auf die AEM Inhaltsquelle verweist.

Die folgenden Optionen werden berücksichtigt:

* **Zip-Datei:** Damit die beste Möglichkeit besteht, auf dem Gerät richtig anzuzeigen, werden die referenzierten Materialien (CSS, JavaScript, Assets usw. der Seite) in einer einzelnen komprimierten Datei mit der Antwort enthalten. Die Verweise auf der HTML-Seite können angepasst werden, um einen relativen Pfad zu diesen Dateien zu verwenden.
* **Streaming:** Abrufen eines Manifests der erforderlichen Dateien von AEM. Verwenden Sie dann dieses Manifest, um alle Dateien (HTML, CSS, JS usw.) mit nachfolgenden Anfragen anzufordern.

![chlimage_1-157](assets/chlimage_1-157.png)

## Kanalunabhängige Inhalte {#channel-independent-content}

Kanalunabhängiger Inhalt ist eine Möglichkeit, AEM Inhaltskonstrukte - wie z. B. Seiten - verfügbar zu machen, ohne sich um Layout, Komponenten oder andere kanalspezifische Informationen zu sorgen.

Diese Inhaltsentitäten werden mithilfe eines Inhaltsmodells generiert, um die AEM Strukturen in ein JSON-Format zu übersetzen. Die resultierenden JSON-Daten enthalten Informationen zu den Daten des Inhalts, die vom AEM Repository entkoppelt sind. Dazu gehören die Rückgabe von Metadaten und AEM Referenzlinks zu Assets sowie die Beziehungen zwischen Inhaltsstrukturen - einschließlich der Entitätshierarchie.

### Verwalten von kanalunabhängigen Inhalten {#managing-channel-independent-content}

Inhalte können auf verschiedene Arten in die App gelangen.

1. GET-ZIPS über AEM Übersee

   * Content Sync-Handler können das ZIP-Paket direkt aktualisieren oder vorhandene Content-Renderer aufrufen

      * Platform-Handler
      * AEM Handler
      * Benutzerdefinierte Handler

1. GET direkt über Content Renderer

   * Vordefinierte Standard-Sling-Renderer
   * AEM Mobile/Content Services Content Renderer
   * Benutzerdefinierte Renderer
