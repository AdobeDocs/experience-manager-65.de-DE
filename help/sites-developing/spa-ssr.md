---
title: SPA- und serverseitiges Rendering
seo-title: SPA- und serverseitiges Rendering
description: 'null'
seo-description: 'null'
uuid: 27e26e3f-65d4-4069-b570-58b8b9e2a1ae
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 844e5c96-2a18-4869-b4c8-2fb9efe0332a
docset: aem65
translation-type: tm+mt
source-git-commit: 2dad220d6593ed542816f8a97b0d4b44f0d57876

---


# SPA- und serverseitiges Rendering{#spa-and-server-side-rendering}

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen clientseitiges Rendering (z.B. React oder Angular) durch das SPA-Framework erforderlich ist.

>[!NOTE]
>
>AEM 6.5.1.0 oder höher ist erforderlich, um die Funktionen für die serverseitige Wiedergabe von SPA zu verwenden, wie in diesem Dokument beschrieben.

## Überblick {#overview}

Einzelseitenanwendungen (SPAs) bieten dem Benutzer ein vielseitiges, dynamisches Erlebnis, das auf vertraute Weise reagiert und sich verhält, oft genau wie eine native Anwendung. [Dies wird erreicht, indem der Client den Inhalt vorab lädt und dann die Benutzerinteraktion](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) intensiv aufhebt und so die erforderliche Kommunikation zwischen Client und Server minimiert, wodurch die App reaktiver wird.

Dies kann jedoch zu längeren anfänglichen Ladezeiten führen, insbesondere wenn die SPA groß und inhaltlich reich ist. Um die Ladezeit zu optimieren, können einige Inhalte serverseitig wiedergegeben werden. Die Verwendung des serverseitigen Renderings (SSR) kann das anfängliche Laden der Seite beschleunigen und dann das Rendering an den Client weiterleiten.

## Verwendung von SSR {#when-to-use-ssr}

SSR ist nicht für alle Projekte erforderlich. Obwohl AEM JS SSR für SPA vollständig unterstützt, empfiehlt Adobe nicht, es systematisch für jedes Projekt zu implementieren.

Bei der Entscheidung, SSR zu implementieren, müssen Sie zunächst abschätzen, welche zusätzliche Komplexität, Aufwand und Kostenaufstockung SSR realistisch für das Projekt, einschließlich der langfristigen Wartung, darstellen. Eine SSR-Architektur sollte nur gewählt werden, wenn der Mehrwert die geschätzten Kosten deutlich übersteigt.

SSR bietet in der Regel einen Wert, wenn eine der folgenden Fragen mit einem klaren Ja beantwortet wird:

* **** SEO: Ist SSR noch immer erforderlich, damit Ihre Site von den Suchmaschinen, die Traffic bringen, korrekt indiziert wird? Beachten Sie, dass die wichtigsten Suchmaschinen-Crawler jetzt JS bewerten.
* **** Seitengeschwindigkeit: Bietet SSR eine messbare Geschwindigkeitsverbesserung in Echtzeit-Umgebungen und steigert die Benutzererfahrung insgesamt?

Nur wenn mindestens eine dieser beiden Fragen mit einem klaren Ja für Ihr Projekt beantwortet wird, empfiehlt Adobe die Implementierung von SSR. In den folgenden Abschnitten wird beschrieben, wie Sie dies mit der Adobe I/O-Laufzeit tun.

## Adobe I/O-Laufzeit {#adobe-i-o-runtime}

Wenn Sie [sicher sind, dass Ihr Projekt die Implementierung der SSR](/help/sites-developing/spa-ssr.md#when-to-use-ssr)erfordert, empfiehlt Adobe die Verwendung der Adobe I/O-Laufzeit.

Weitere Informationen zur Adobe I/O-Laufzeit finden Sie unter

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - Überblick über den Dienst
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - für eine ausführliche Dokumentation auf der Plattform

In den folgenden Abschnitten wird erläutert, wie Adobe I/O Runtime zum Implementieren von SSR für Ihre SPA in zwei verschiedenen Modellen verwendet werden kann:

* [AEM-gesteuerter Kommunikationsfluss](/help/sites-developing/spa-ssr.md#aem-driven-communication-flow)
* [Adobe I/O-Laufzeitgesteuerter Kommunikationsfluss](/help/sites-developing/spa-ssr.md#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe empfiehlt für jede AEM-Umgebung (Autor, Veröffentlichung, Stage usw.) eine separate Adobe I/O-Laufzeitinstanz.

## AEM-gesteuerter Kommunikationsfluss {#aem-driven-communication-flow}

Bei Verwendung von SSR umfasst der [Komponenteninteraktionsarbeitsablauf](/help/sites-developing/spa-overview.md#workflow) von SPAs in AEM eine Phase, in der der ursprüngliche Inhalt der App in der Adobe I/O-Laufzeit generiert wird.

1. Der Browser fordert den SSR-Inhalt von AEM an.

1. AEM sendet das Modell zur Adobe I/O-Laufzeit.

1. Adobe I/O Runtime gibt den generierten Inhalt zurück.

1. AEM stellt das von Adobe I/O Runtime zurückgegebene HTML über die HTML-Vorlage der Backend-Seitenkomponente bereit.

![server-side-rendering-cms-drivenaemnode-adobeio](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

## Adobe I/O-Laufzeitgesteuerter Kommunikationsfluss {#adobe-i-o-runtime-driven-communication-flow}

Im vorherigen Abschnitt wird die standardmäßige und empfohlene Implementierung des serverseitigen Renderings in Bezug auf SPAs in AEM beschrieben, wobei AEM das Bootstrapping und Bereitstellen von Inhalten ausführt.

Alternativ kann SSR implementiert werden, sodass Adobe I/O Runtime für das Bootstrapping verantwortlich ist und den Kommunikationsfluss effektiv umkehrt.

Beide Modelle sind gültig und werden von AEM unterstützt. Vor der Einführung eines bestimmten Modells sollten jedoch die Vor- und Nachteile jedes einzelnen Modells berücksichtigt werden.

<table>
 <tbody>
  <tr>
   <th><strong>Bootstrapping</strong></th>
   <th><strong>Vorteile</strong></th>
   <th><strong>Nachteile</strong></th>
  </tr>
  <tr>
   <th><strong>über AEM</strong><br /> </th>
   <td>
    <ul>
     <li>AEM verwaltet die Injektion von Bibliotheken bei Bedarf</li>
     <li>Ressourcen müssen nur auf AEM beibehalten werden<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Möglicherweise nicht mit SPA-Entwicklern vertraut<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>über Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Eingehendere Kenntnisse der SPA-Entwickler<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Für die Anwendung erforderliche Clientlib-Ressourcen wie CSS und JavaScript müssen vom AEM-Entwickler über die <code><a href="/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet">allowProxy</a></code> Eigenschaft verfügbar gemacht werden<br /> </li>
     <li>Ressourcen müssen zwischen AEM und Adobe I/O Runtime synchronisiert werden<br /> </li>
     <li>Um das Authoring der SPA zu aktivieren, ist unter Umständen ein Proxyserver für die Adobe I/O Runtime erforderlich.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planung für SSR {#planning-for-ssr}

Im Allgemeinen muss nur ein Teil einer Anwendung serverseitig gerendert werden. Das allgemeine Beispiel ist der Inhalt, der über der Kante beim ersten Laden der Seite angezeigt wird, wird serverseitig gerendert. Dies spart Zeit, indem bereits gerenderte Inhalte an den Client gesendet werden. Wenn der Benutzer mit der SPA interagiert, wird der zusätzliche Inhalt vom Client wiedergegeben.

Wenn Sie erwägen, das serverseitige Rendering für Ihre SPA zu implementieren, müssen Sie überprüfen, welche Teile der App erforderlich sind.

## Entwickeln einer SPA mit SSR {#developing-an-spa-using-ssr}

SPA-Komponenten können vom Client (im Browser) oder vom Server gerendert werden. Beim Rendern auf Serverseite sind keine Browsereigenschaften wie Fenstergröße und -position vorhanden. Daher sollten SPA-Komponenten isomorphisch sein, sodass keine Annahme darüber besteht, wo sie gerendert werden.

Um SSR zu nutzen, müssen Sie Ihren Code in AEM sowie in Adobe I/O Runtime bereitstellen, die für das serverseitige Rendering zuständig ist. Der Großteil des Codes ist identisch, aber serverspezifische Aufgaben unterscheiden sich.

## SSR für SPAs in AEM {#ssr-for-spas-in-aem}

SSR für SPAs in AEM erfordern Adobe I/O Runtime, die für die Wiedergabe der App Content Server-Seite aufgerufen wird. Innerhalb der HTL der App wird eine Ressource auf der Adobe I/O-Laufzeit aufgerufen, um den Inhalt wiederzugeben.

Genau wie AEM die standardmäßigen SPA-Frameworks Angular und React unterstützt, wird auch das serverseitige Rendering für Angular- und React-Apps unterstützt. Weitere Informationen finden Sie in der NPM-Dokumentation für beide Frameworks.

* Reaktion: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Ein einfaches Beispiel finden Sie in der App [We.Retail Journal](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Gibt die gesamte Anwendungsserverseite wieder. Obwohl dies kein echtes Beispiel ist, zeigt es doch, was zur Umsetzung der Reform des Sicherheitssektors erforderlich ist.

>[!CAUTION]
>
>Die [We.Retail Journal-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) dient nur zu Demonstrationszwecken und verwendet daher Node.js als einfaches Beispiel anstelle der empfohlenen Adobe I/O-Laufzeit. Dieses Beispiel sollte für keine Projektarbeit verwendet werden.

>[!NOTE]
>
>Alle SPA-Projekte auf AEM sollten auf dem [Maven Archetype for SPA Starter Kit](https://github.com/adobe/aem-spa-project-archetype)basieren.

## Verwenden von Node.js {#using-node-js}

Adobe I/O Runtime ist die empfohlene Lösung für die Implementierung von SSR für SPAs in AEM.

Bei AEM-Instanzen im Vorfeld ist es auch möglich, SSR mit einer benutzerdefinierten Node.js-Instanz zu implementieren, wie oben beschrieben. Dies wird zwar von Adobe unterstützt, wird jedoch nicht empfohlen.

>[!NOTE]
>
>Node.js wird für von Adobe gehostete AEM-Instanzen nicht unterstützt.

>[!NOTE]
>
>Wenn SSR über Node.js implementiert werden muss, empfiehlt Adobe für jede AEM-Umgebung (Autor, Veröffentlichung, Stage usw.) eine separate Node.js-Instanz.
