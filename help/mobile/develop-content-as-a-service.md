---
title: Inhaltsbereitstellung
description: Erfahren Sie, wie Sie alle Inhalte in Adobe Experience Manager verwenden, um das zielgerichtete App-Erlebnis bereitzustellen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 85e73679-684e-402f-8186-8b56d8bd9372
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 1%

---

# Inhaltsbereitstellung{#content-delivery}

{{ue-over-mobile}}

Mobile Apps sollten in der Lage sein, alle Inhalte in AEM nach Bedarf zu verwenden, um ein zielgerichtetes App-Erlebnis bereitzustellen.

Dazu gehören die Verwendung von Assets, Site-Inhalten, CAS-Inhalten (Over-the-Air) und benutzerdefinierten Inhalten, die eine eigene Struktur aufweisen können.

>[!NOTE]
>
>**Over-the-Air** Inhalte können aus jedem der oben genannten Gründe über ContentSync-Handler stammen. Es kann verwendet werden, um Pakete per Batch zu verpacken und per ZIP zu versenden und Aktualisierungen für diese Pakete zu verwalten.

Es gibt drei Haupttypen von Material, das von Content Services bereitgestellt wird:

1. **Assets**
1. **Gepackter HTML-Inhalt (HTML/CSS/JS)**
1. **Kanalunabhängiger Inhalt**

![chlimage_1-154](assets/chlimage_1-154.png)

## Assets {#assets}

Asset-Sammlungen sind AEM-Konstrukte, die Verweise auf andere Sammlungen enthalten.

Eine Asset-Sammlung kann über Content Services verfügbar gemacht werden. Der Aufruf einer Asset-Sammlung in einer Anfrage gibt ein -Objekt zurück, das eine Liste der Assets ist - einschließlich ihrer URLs. Der Zugriff auf Assets erfolgt über eine URL. Die URL wird in einem -Objekt bereitgestellt. Zum Beispiel:

* Eine Seitenentität gibt die JSON-Datei (Seitenobjekt) zurück, die einen Bildverweis enthält. Der Bildverweis ist eine URL, mit der die Asset-Binärdatei für das Bild abgerufen wird.
* Bei einer Anfrage nach einer Liste von Assets in einem Ordner wird die JSON mit Details zu allen Entitäten in diesem Ordner zurückgegeben. Diese Liste ist ein Objekt. Die JSON-Datei enthält URL-Referenzen, mit denen die Binärdaten der Assets für jedes Asset in diesem Ordner abgerufen werden.

### Asset-Optimierung {#asset-optimization}

Ein wichtiger Wert von Content Services ist die Möglichkeit, für das Gerät optimierte Assets zurückzugeben. Dadurch werden die Anforderungen an den lokalen Gerätespeicher reduziert und die App-Leistung verbessert.

Die Asset-Optimierung ist eine Server-seitige Funktion, die auf den in der API-Anfrage bereitgestellten Informationen basiert. Die Asset-Ausgabedarstellungen sollten nach Möglichkeit zwischengespeichert werden, sodass ähnliche Anfragen keine erneute Generierung der Asset-Ausgabedarstellung erfordern.

### Assets-Workflow {#assets-workflow}

Der Asset-Workflow sieht wie folgt aus:

1. Die Asset-Referenz ist vorkonfiguriert in der AEM verfügbar
1. Erstellen einer Asset-Referenzentität für ihr Modell
1. Entität bearbeiten

   1. Asset oder Asset-Sammlung auswählen
   1. JSON-Rendering anpassen

Das folgende Diagramm zeigt den Referenzworkflow für **Assets**:

![chlimage_1-155](assets/chlimage_1-155.png)

### Verwalten von Assets {#managing-assets}

Content Services bieten Zugriff auf AEM-verwaltete Assets, die nicht durch andere AEM-Inhalte referenziert werden können.

#### Managed Assets {#existing-managed-assets}

Ein Anwender von AEM Sites und Assets verwendet AEM Assets, um sein gesamtes digitales Material für alle Kanäle zu verwalten. Sie entwickeln eine native Mobile App und müssen mehrere Assets verwenden, die von AEM Assets verwaltet werden. Zum Beispiel Logos, Hintergrundbilder und Schaltflächensymbole.

Derzeit sind diese über das Assets-Repository verteilt. Die Dateien, auf die die App verweisen muss, befinden sich in den folgenden Dateien:

* /content/dam/geometrixx-outdoors/brand/logo_light.png
* /content/dam/geometrixx-outdoors/brand/logo_dark.png
* /content/dam/geometrixx-outdoors/styles/backgrounds/grey_blue.jpg
* /content/dam/geometrixx-outdoors/brand/icons/app/cart.png
* /content/dam/geometrixx-outdoors/brand/icons/app/home.png

#### Zugreifen auf CSS-Asset-Entitäten {#accessing-cs-asset-entities}

Lassen wir vorerst die Schritte beiseite, in denen beschrieben wird, wie die Seite über die API verfügbar gemacht wird (sie wird von der Beschreibung der AEM-Benutzeroberfläche abgedeckt), und nehmen wir an, dass dies bereits geschehen ist. Asset-Entitäten wurden erstellt und dem Bereich „appImages“ hinzugefügt. Zu Organisationszwecken wurden unter dem Bereich zusätzliche Ordner erstellt. Die Asset-Entitäten werden also im AEM-JCR wie folgt gespeichert:

* /content/entities/appImages/logos/logo_light
* /content/entities/appImages/logos/logo_dark
* /content/entities/appImages/bkgnd/gray_blue
* /content/entities/appImages/icons/cart
* /content/entities/appImages/icons/home

#### Abrufen einer Liste der verfügbaren Asset-Entitäten {#getting-a-list-of-available-asset-entities}

Ein App-Entwickler kann eine Liste der verfügbaren Assets erhalten, indem er die Asset-Entitäten abruft. Der Space-Endpunkt von Content Services kann diese Informationen über die Webservice-API SDK bereitstellen.

Das Ergebnis wäre ein Objekt im JSON-Format, das eine Liste der Assets im Ordner „Symbole“ bereitstellt.

![chlimage_1-156](assets/chlimage_1-156.png)

#### Abrufen eines Bildes {#getting-an-image}

Die JSON-Datei stellt eine URL für jedes Bild bereit, das von Content Services für das Bild generiert wurde.

Um die Binärdatei für das Bild „Warenkorb“ abzurufen, wird die Client-Bibliothek erneut verwendet.

## Inhalt der gepackten HTML {#packaged-html-content}

HTML-Inhalte werden für Kunden benötigt, die das Layout der Inhalte beibehalten müssen. Dies ist für native Programme nützlich, die einen Web-Container - wie eine Cordova-Webansicht - zum Anzeigen des Inhalts verwenden.

AEM Content Services stellt der mobilen App über die API HTML-Inhalte bereit. Kunden, die AEM-Inhalte als HTML bereitstellen möchten, können eine HTML-Seitenentität erstellen, die auf die AEM-Inhaltsquelle verweist.

Die folgenden Optionen werden berücksichtigt:

* **ZIP-Datei:** Damit auf dem Gerät die beste Chance zur ordnungsgemäßen Anzeige besteht, werden das referenzierte Material-css, JavaScript, Assets usw. der Seite in einer einzigen komprimierten Datei mit der Antwort enthalten. Die Verweise auf der HTML-Seite können so angepasst werden, dass sie einen relativen Pfad zu diesen Dateien verwenden.
* **Streaming** Abrufen eines Manifests der erforderlichen Dateien von AEM. Verwenden Sie dieses Manifest dann, um alle Dateien (HTML, CSS, JS usw.) mit nachfolgenden Anfragen anzufordern.

![chlimage_1-157](assets/chlimage_1-157.png)

## Kanalunabhängiger Inhalt {#channel-independent-content}

Kanalunabhängiger Inhalt ist eine Möglichkeit, AEM-Inhaltskonstrukte - wie Seiten - bereitzustellen, ohne sich Gedanken über Layout, Komponenten oder andere kanalspezifische Informationen machen zu müssen.

Diese Inhaltsentitäten werden mithilfe eines Inhaltsmodells generiert, um die AEM-Strukturen in ein JSON-Format zu übersetzen. Die resultierenden JSON-Daten enthalten Informationen zu den Daten des Inhalts, die vom AEM-Repository entkoppelt sind. Dazu gehören die Rückgabe von Metadaten und AEM-Referenzlinks zu Assets und die Beziehungen zwischen Inhaltsstrukturen - einschließlich der Entitätshierarchie.

### Kanalunabhängige Inhalte verwalten {#managing-channel-independent-content}

Inhalte können auf verschiedene Weise zur App gelangen.

1. GET-Content-ZIPs über AEM Over-the-Air

   * Inhaltssynchronisierungs-Handler können das ZIP-Paket direkt aktualisieren oder indem sie vorhandene Inhaltssenderer aufrufen

      * Plattform-Handler
      * AEM-Handler
      * Benutzerdefinierte Handler

1. GET-Inhalte direkt über Content Renderer

   * Vorkonfigurierte Standard-Sling-Renderer
   * Inhalts-Renderer für AEM Mobile/Content Services
   * Benutzerdefinierte Renderings
