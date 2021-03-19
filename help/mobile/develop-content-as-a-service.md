---
title: Inhaltsbereitstellung
seo-title: Inhaltsbereitstellung
description: Inhaltsbereitstellung
seo-description: 'null'
uuid: 1e7bea34-ca50-41ed-8295-fa182c27fa69
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 3d65cc6b-5721-472f-a805-588d50f3571b
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 4%

---


# Inhaltsbereitstellung{#content-delivery}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mobile Apps sollten nach Bedarf alle Inhalte in AEM verwenden können, um das Targeting-App-Erlebnis bereitzustellen.

Dazu gehören die Verwendung von Assets, Site-Inhalten, CaaS-Inhalten (über die Luft) und benutzerspezifischen Inhalten, die möglicherweise eine eigene Struktur haben.

>[!NOTE]
>
>**Over-the-Air** Content kann über ContentSync Handler aus einem der oben genannten stammen. Es kann zum Batch-Paket und Versand über Zips verwendet werden, sowie zum Verwalten von Updates oder solchen Paketen.

Content Services bietet drei Hauptmaterialtypen:

1. **Assets**
1. **Verpackte HTML-Inhalte (HTML/CSS/JS)**
1. **Unabhängiger Kanal**

![chlimage_1-154](assets/chlimage_1-154.png)

## Assets {#assets}

Asset-Sammlungen sind AEM Konstrukte, die Verweise auf andere Sammlungen enthalten.

Eine Asset-Sammlung kann über Content Services bereitgestellt werden. Beim Aufrufen einer Asset-Sammlung in einer Anforderung wird ein Objekt zurückgegeben, das eine Liste der Assets einschließlich ihrer URLs darstellt. Assets werden über eine URL aufgerufen. Die URL wird in einem Objekt bereitgestellt. Beispiel:

* Eine Seitenentität gibt JSON (Seitenobjekt) zurück, das einen Bildverweis enthält. Die Bildreferenz ist eine URL, mit der die Asset-Binärdatei für das Bild abgerufen wird.
* Eine Anforderung einer Liste von Assets in einem Ordner gibt JSON mit Details zu allen Entitäten in diesem Ordner zurück. Diese Liste ist ein Objekt. Die JSON-Datei enthält URL-Verweise, die verwendet werden, um die Asset-Binärdatei für jedes Asset in diesem Ordner abzurufen.

### Asset-Optimierung {#asset-optimization}

Ein wichtiger Wert von Content Services ist die Möglichkeit, Assets zurückzugeben, die für das Gerät optimiert sind. Dadurch werden die Anforderungen an die Datenspeicherung lokaler Geräte verringert und die App-Performance verbessert.

Die Asset-Optimierung ist eine serverseitige Funktion, die auf den in der API-Anforderung bereitgestellten Informationen basiert. Wo immer möglich, sollten die Asset-Darstellungen zwischengespeichert werden, damit ähnliche Anforderungen keine erneute Generierung der Asset-Darstellung erfordern.

### Asset-Workflow {#assets-workflow}

Der Asset-Arbeitsablauf lautet wie folgt:

1. Asset-Referenz im Lieferumfang AEM
1. Asset-Referenzentität nach ihrem Modell erstellen
1. Entität bearbeiten

   1. Asset oder Asset-Sammlung auswählen
   1. JSON-Rendering anpassen

Das folgende Diagramm zeigt den **Asset Reference Workflow**:

![chlimage_1-155](assets/chlimage_1-155.png)

### Verwalten von Assets {#managing-assets}

Content Services bieten Zugriff auf AEM verwalteten Assets, auf die möglicherweise nicht über andere AEM verwiesen wird.

#### Vorhandene verwaltete Assets {#existing-managed-assets}

Ein bestehender AEM Sites- und Assets-Benutzer verwendet AEM Assets, um alle digitalen Inhalte für alle Kanal zu verwalten. Sie entwickeln eine native mobile App und müssen mehrere Assets verwenden, die von AEM Assets verwaltet werden. Zum Beispiel Logos, Hintergrundbilder, Schaltflächensymbole usw.

Derzeit befinden sich diese im Assets-Repository. Die Dateien, auf die die App verweisen muss, befinden sich in:

* /content/dam/geometrixx-outdoors/brand/logo_light.png
* /content/dam/geometrixx-outdoors/brand/logo_dark.png
* /content/dam/geometrixx-outdoors/styles/backgrounds/gray_blue.jpg
* /content/dam/geometrixx-outdoors/brand/icons/app/cart.png
* /content/dam/geometrixx-outdoors/brand/icons/app/home.png

#### Zugriff auf CS Asset Entities {#accessing-cs-asset-entities}

Lassen wir die Schritte beiseite, wie die Seite jetzt über die API zur Verfügung gestellt wird (sie wird durch die Beschreibung der AEM Benutzeroberfläche abgedeckt), und gehen davon aus, dass sie bereits erfolgt ist. Asset-Entitäten wurden erstellt und dem Bereich &quot;appImages&quot;hinzugefügt. Weitere Ordner wurden aus organisatorischen Gründen unter dem Raum erstellt. Die Asset-Entitäten werden also in der AEM JCR wie folgt gespeichert:

* /content/entity/appImages/logos/logo_light
* /content/entity/appImages/logos/logo_dark
* /content/entity/appImages/bkgnd/gray_blue
* /content/entity/appImages/icons/cart
* /content/entity/appImages/icons/home

#### Liste der verfügbaren Asset-Entitäten abrufen {#getting-a-list-of-available-asset-entities}

Ein App-Entwickler kann eine Liste der verfügbaren Assets abrufen, indem er die Asset-Entitäten abruft. Der Leerzeichen-Endpunkt von Content Services kann diese Informationen über das Webdienst-API-SDK bereitstellen.

Das Ergebnis wäre ein Objekt im JSON-Format, das eine Liste der Assets im Ordner &quot;icons&quot;bereitstellt.

![chlimage_1-156](assets/chlimage_1-156.png)

#### Abrufen eines Bildes {#getting-an-image}

Das JSON stellt für jedes Bild eine URL bereit, die von Content Services für das Bild generiert wird.

Um die Binärdatei für das Bild &quot;Einkaufswagen&quot;zu erhalten, wird die Client-Bibliothek erneut verwendet.

## HTML-Inhalt im Paket {#packaged-html-content}

HTML-Inhalte werden für Kunden benötigt, die das Layout der Inhalte beibehalten müssen. Dies ist nützlich für native Anwendungen, die einen Web-Container (z. B. eine Cordova-Webansicht) verwenden, um den Inhalt anzuzeigen.

AEM Content Services kann HTML-Inhalte über die API für die mobile App bereitstellen. Kunden, die AEM Inhalte als HTML bereitstellen möchten, erstellen eine HTML-Seitenentität, die auf die AEM Inhaltsquelle verweist.

Die folgenden Optionen werden in Betracht gezogen:

* **Zip-Datei:** Damit alle referenzierten Elemente der Seite am besten auf dem Gerät korrekt angezeigt werden können - CSS, JavaScript, Assets usw. - wird in einer einzelnen komprimierten Datei mit der Antwort enthalten. Die Verweise auf der HTML-Seite werden angepasst, um einen relativen Pfad zu diesen Dateien zu verwenden.
* **Streaming:** Abrufen eines Manifests der erforderlichen Dateien aus AEM. Verwenden Sie dieses Manifest dann, um alle Dateien (HTML, CSS, JS usw.) anzufordern. mit nachfolgenden Anforderungen.

![chlimage_1-157](assets/chlimage_1-157.png)

## Unabhängiger Kanal {#channel-independent-content}

Kanal-unabhängige Inhalte sind eine Möglichkeit, AEM Inhaltskonstrukte - wie z. B. Seiten - offen zu legen, ohne sich um Layout-, Komponenten- oder andere Kanal-spezifische Informationen zu sorgen.

Diese Inhaltsentitäten werden mithilfe eines Inhaltsmodells generiert, um die AEM Strukturen in ein JSON-Format zu übersetzen. Die resultierenden JSON-Daten enthalten Informationen über die Daten des Inhalts, die vom AEM-Repository entkoppelt werden. Dazu gehören die Rückgabe von Metadaten und AEM Referenz-Links zu Assets sowie die Beziehungen zwischen Inhaltsstrukturen - einschließlich der Entitätshierarchie.

### Verwalten unabhängiger Kanal {#managing-channel-independent-content}

Inhalte können auf verschiedene Weise zur App gelangen.

1. GET content ZIPS über AEM Over-the-Air

   * Content Sync-Handler können das ZIP-Paket direkt oder durch Aufruf vorhandener Inhalts-Renderer aktualisieren

      * Plattformhandler
      * AEMM-Handler
      * Benutzerdefinierte Handler

1. GET direkt über Content Renderer

   * Vordefinierte Standard-Sling-Renderer
   * AEM Mobile/Content Services Content Renderer
   * Benutzerdefinierte Wiedergabe

