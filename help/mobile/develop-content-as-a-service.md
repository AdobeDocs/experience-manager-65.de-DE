---
title: Inhaltsbereitstellung
seo-title: Inhaltsbereitstellung
description: 'null'
seo-description: 'null'
uuid: 1e7bea34-ca50-41ed-8295-fa182c27fa69
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 3d65cc6b-5721-472f-a805-588d50f3571b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Inhaltsbereitstellung{#content-delivery}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mobile Apps sollten alle Inhalte in AEM nach Bedarf verwenden können, um das zielgerichtete App-Erlebnis bereitzustellen.

Dazu gehören die Verwendung von Assets, Site-Inhalten, CaaS-Inhalten (über die Luft) und benutzerspezifischen Inhalten, die möglicherweise eine eigene Struktur haben.

>[!NOTE]
>
>**Über ContentSync-Handler können Überstunden** aus den oben genannten Elementen stammen. Es kann für Batch-Pakete und -Auslieferungen über Zips verwendet werden, sowie für die Wartung von Updates oder Paketen.

Content Services bietet drei Hauptmaterialtypen:

1. **Assets**
1. **Verpackte HTML-Inhalte (HTML/CSS/JS)**
1. **Kanalunabhängiger Inhalt**

![chlimage_1-154](assets/chlimage_1-154.png)

## Assets {#assets}

Asset-Sammlungen sind AEM-Konstrukte, die Verweise auf andere Sammlungen enthalten.

Eine Asset-Sammlung kann über Content Services bereitgestellt werden. Beim Aufrufen einer Asset-Sammlung in einer Anforderung wird ein Objekt zurückgegeben, das eine Liste der Assets einschließlich ihrer URLs enthält. Assets werden über eine URL aufgerufen. Die URL wird in einem Objekt bereitgestellt. Beispiel:

* Eine Seitenentität gibt JSON (Seitenobjekt) zurück, das einen Bildverweis enthält. Die Bildreferenz ist eine URL, mit der die Asset-Binärdatei für das Bild abgerufen wird.
* Eine Anforderung einer Liste von Assets in einem Ordner gibt JSON mit Details zu allen Entitäten in diesem Ordner zurück. Diese Liste ist ein Objekt. Die JSON-Datei enthält URL-Verweise, die verwendet werden, um die Asset-Binärdatei für jedes Asset in diesem Ordner abzurufen.

### Asset-Optimierung {#asset-optimization}

Ein wichtiger Wert von Content Services ist die Möglichkeit, Assets zurückzugeben, die für das Gerät optimiert sind. Dadurch werden die Speicheranforderungen für lokale Geräte verringert und die App-Leistung verbessert.

Die Asset-Optimierung ist eine serverseitige Funktion, die auf den in der API-Anforderung bereitgestellten Informationen basiert. Wo immer möglich, sollten die Asset-Darstellungen zwischengespeichert werden, damit ähnliche Anforderungen keine erneute Generierung der Asset-Darstellung erfordern.

### Asset-Workflow {#assets-workflow}

Der Asset-Arbeitsablauf lautet wie folgt:

1. Asset-Referenz in AEM
1. Asset-Referenzentität nach ihrem Modell erstellen
1. Entität bearbeiten

   1. Asset oder Asset-Sammlung auswählen
   1. JSON-Rendering anpassen

Das folgende Diagramm zeigt den **Asset Reference Workflow**:

![chlimage_1-155](assets/chlimage_1-155.png)

### Verwalten von Assets {#managing-assets}

Content Services bieten Zugriff auf von AEM verwaltete Assets, auf die möglicherweise nicht über andere AEM-Inhalte verwiesen wird.

#### Vorhandene verwaltete Assets {#existing-managed-assets}

Ein bestehender AEM-Sites- und -Assets-Benutzer verwendet AEM Assets, um alle digitalen Inhalte für alle Kanäle zu verwalten. Sie entwickeln eine native mobile App und müssen mehrere Assets verwenden, die von AEM Assets verwaltet werden. Zum Beispiel Logos, Hintergrundbilder, Schaltflächensymbole usw.

Derzeit befinden sich diese im Assets-Repository. Die Dateien, auf die die App verweisen muss, befinden sich in:

* /content/dam/geometrixx-outdoors/brand/logo_light.png
* /content/dam/geometrixx-outdoors/brand/logo_dark.png
* /content/dam/geometrixx-outdoors/styles/backgrounds/gray_blue.jpg
* /content/dam/geometrixx-outdoors/brand/icons/app/cart.png
* /content/dam/geometrixx-outdoors/brand/icons/app/home.png

#### Zugriff auf CS Asset Entities {#accessing-cs-asset-entities}

Lassen wir die Schritte beiseite, wie die Seite jetzt über die API zur Verfügung gestellt wird (sie wird durch die Beschreibung der AEM-Benutzeroberfläche abgedeckt), und gehen davon aus, dass sie bereits erfolgt ist. Asset-Entitäten wurden erstellt und dem Bereich &quot;appImages&quot;hinzugefügt. Unter dem Raum wurden zu Organisationszwecken weitere Ordner erstellt. Die Asset-Entitäten werden also wie folgt in AEM JCR gespeichert:

* /content/entity/appImages/logos/logo_light
* /content/entity/appImages/logos/logo_dark
* /content/entity/appImages/bkgnd/gray_blue
* /content/entity/appImages/icons/cart
* /content/entity/appImages/icons/home

#### Abrufen einer Liste der verfügbaren Asset-Entitäten {#getting-a-list-of-available-asset-entities}

Ein App-Entwickler kann eine Liste der verfügbaren Assets abrufen, indem er die Asset-Entitäten abruft. Der Leerzeichen-Endpunkt von Content Services kann diese Informationen über das Webdienst-API-SDK bereitstellen.

Das Ergebnis wäre ein Objekt im JSON-Format, das eine Liste der Assets im Ordner &quot;icons&quot;bereitstellt.

![chlimage_1-156](assets/chlimage_1-156.png)

#### Abrufen eines Bildes {#getting-an-image}

Das JSON stellt für jedes Bild eine URL bereit, die von Content Services für das Bild generiert wird.

Um die Binärdatei für das Bild &quot;Einkaufswagen&quot;zu erhalten, wird die Client-Bibliothek erneut verwendet.

## Verpackter HTML-Inhalt {#packaged-html-content}

HTML-Inhalte werden für Kunden benötigt, die das Layout der Inhalte beibehalten müssen. Dies ist nützlich für native Anwendungen, die einen Webcontainer verwenden - z. B. eine Cordova-Webansicht -, um den Inhalt anzuzeigen.

AEM Content Services kann HTML-Inhalte über die API für die mobile App bereitstellen. Kunden, die AEM-Inhalte als HTML bereitstellen möchten, erstellen eine HTML-Seitenentität, die auf die AEM-Inhaltsquelle verweist.

Die folgenden Optionen werden in Betracht gezogen:

* **** Zip-Datei: Damit das gesamte auf der Seite referenzierte Material - CSS, JavaScript, Assets usw. - am besten auf dem Gerät korrekt angezeigt werden kann. - wird in einer einzelnen komprimierten Datei mit der Antwort enthalten. Die Verweise auf der HTML-Seite werden angepasst, um einen relativen Pfad zu diesen Dateien zu verwenden.
* **** Streaming: Abrufen eines Manifests der erforderlichen Dateien aus AEM. Verwenden Sie dieses Manifest dann, um alle Dateien (HTML, CSS, JS usw.) anzufordern. mit nachfolgenden Anforderungen.

![chlimage_1-157](assets/chlimage_1-157.png)

## Kanalunabhängige Inhalte {#channel-independent-content}

Kanalunabhängiger Inhalt ist eine Möglichkeit, AEM-Inhaltskonstrukte - wie z. B. Seiten - offen zu legen, ohne sich um Layout, Komponenten oder andere kanalspezifische Informationen zu sorgen.

Diese Inhaltsentitäten werden mithilfe eines Inhaltsmodells generiert, um die AEM-Strukturen in ein JSON-Format zu übersetzen. Die resultierenden JSON-Daten enthalten Informationen über die Daten des Inhalts, die vom AEM-Repository entkoppelt werden. Dazu gehören die Rückgabe von Metadaten und AEM-Referenzlinks zu Assets sowie die Beziehungen zwischen Inhaltsstrukturen - einschließlich der Entitätshierarchie.

### Verwalten von kanaltunabhängigen Inhalten {#managing-channel-independent-content}

Inhalte können auf verschiedene Weise zur App gelangen.

1. Abrufen von Inhalt-ZIPS über AEM Over-the-Air

   * Content Sync-Handler können das ZIP-Paket direkt oder durch Aufruf vorhandener Inhalts-Renderer aktualisieren

      * Plattformhandler
      * AEMM-Handler
      * Benutzerdefinierte Handler

1. Inhalte direkt über Content-Renderer abrufen

   * Standardmäßige Sling-Renderer
   * AEM Mobile/Content Services Content Renderer
   * Benutzerdefinierte Wiedergabe

