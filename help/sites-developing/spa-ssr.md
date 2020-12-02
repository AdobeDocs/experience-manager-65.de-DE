---
title: SPA und serverseitiges Rendering
seo-title: SPA und serverseitiges Rendering
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
source-git-commit: 590dc4464182d4baf8293e7bb0774ce92971c0af
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 2%

---


# SPA und serverseitiges Rendering{#spa-and-server-side-rendering}

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, bei denen SPA Framework-basiertes clientseitiges Rendering (z.B. React oder Angular) erforderlich ist.

>[!NOTE]
>
>AEM Version 6.5.1.0 oder höher ist erforderlich, um die Renderingfunktionen auf SPA Server zu verwenden, wie in diesem Dokument beschrieben.

## Überblick{#overview}

Einzelseitenanwendungen (SPA) können dem Anwender ein umfangreiches, dynamisches Angebot bieten, das auf vertraute Weise reagiert und sich verhält, oft genau wie eine native Anwendung. [Dies wird erreicht, indem der Client den Inhalt vorab laden und dann die aufwändige ](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) Interaktion mit dem Benutzer aufheben und so die erforderliche Kommunikation zwischen dem Client und dem Server minimieren muss, wodurch die App reaktiver wird.

Dies kann jedoch zu längeren anfänglichen Ladezeiten führen, insbesondere wenn die SPA groß und reich an Inhalt ist. Um die Ladezeit zu optimieren, können einige Inhalte serverseitig wiedergegeben werden. Die Verwendung des serverseitigen Renderings (SSR) kann das anfängliche Laden der Seite beschleunigen und dann das Rendering an den Client weiterleiten.

## Verwenden von SSR {#when-to-use-ssr}

SSR ist nicht für alle Projekte erforderlich. Obwohl AEM JS SSR für SPA vollständig unterstützt, empfiehlt Adobe nicht, es systematisch für jedes Projekt zu implementieren.

Bei der Entscheidung, SSR zu implementieren, müssen Sie zunächst abschätzen, welche zusätzliche Komplexität, Aufwand und Kostenaufstockung SSR realistisch für das Projekt, einschließlich der langfristigen Wartung, darstellen. Eine SSR-Architektur sollte nur gewählt werden, wenn der Mehrwert die geschätzten Kosten deutlich übersteigt.

SSR bietet in der Regel einen Wert, wenn eine der folgenden Fragen mit einem klaren Ja beantwortet wird:

* **SEO:** Ist SSR noch immer erforderlich, damit Ihre Site von den Suchmaschinen, die Traffic bringen, korrekt indiziert wird? Denken Sie daran, dass die wichtigsten Suchmaschinen-Crawler jetzt JS bewerten.
* **Seitengeschwindigkeit:** Stellt SSR eine messbare Geschwindigkeitsverbesserung in realen Umgebung dar und steigert die Benutzererfahrung insgesamt?

Nur wenn mindestens eine dieser beiden Fragen mit einem klaren &quot;Ja&quot;für Ihr Projekt beantwortet wird, empfiehlt Adobe die Implementierung von SSR. In den folgenden Abschnitten wird beschrieben, wie Sie dies mit Adobe I/O Runtime tun.

## Adobe I/O Runtime {#adobe-i-o-runtime}

Wenn Sie [sicher sind, dass Ihr Projekt die Implementierung von SSR](/help/sites-developing/spa-ssr.md#when-to-use-ssr) erfordert, empfiehlt die Adobe die Verwendung von Adobe I/O Runtime.

Weitere Informationen zu Adobe I/O Runtime finden Sie unter

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html)  - Überblick über den Dienst
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - für eine ausführliche Dokumentation auf der Plattform

In den folgenden Abschnitten wird erläutert, wie Adobe I/O Runtime zur Implementierung von SSR für Ihre SPA in zwei verschiedenen Modellen verwendet werden kann:

* [AEM-gesteuerter Kommunikationsfluss](/help/sites-developing/spa-ssr.md#aem-driven-communication-flow)
* [Adobe I/O Runtime-orientierter Kommunikationsfluss](/help/sites-developing/spa-ssr.md#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe empfiehlt für jede AEM Umgebung eine separate Adobe I/O Runtime-Instanz (Autor, Veröffentlichung, Stage usw.).

## Remote Renderer-Konfiguration {#remote-renderer-configuration}

AEM müssen wissen, wo der remote gerenderte Inhalt abgerufen werden kann. Unabhängig davon, welches Modell Sie für SSR implementieren, müssen Sie [ angeben, AEM wie Sie auf diesen Remote-Rendering-Dienst zugreifen können.](#adobe-i-o-runtime)

Dies erfolgt über den Dienst **RemoteContentRenderer - Configuration Factory OSGi**. Suchen Sie in der Web-Konsolenkonfiguration unter `http://<host>:<port>/system/console/configMgr` nach der Zeichenfolge &quot;RemoteContentRenderer&quot;.

![Renderer-Konfiguration](assets/rendererconfig.png)

Die folgenden Felder stehen für die Konfiguration zur Verfügung:

* **Content path pattern**  - Regulärer Ausdruck, um ggf. einen Inhaltsbereich zuzuordnen
* **Remote-Endpunkt-URL**  - URL des Endpunkts, der für die Erstellung des Inhalts verantwortlich ist
   * Verwenden Sie das gesicherte HTTPS-Protokoll, wenn nicht im lokalen Netzwerk.
* **Zusätzliche Anforderungs-Header** : Zusätzliche Header, die der an den Remote-Endpunkt gesendeten Anforderung hinzugefügt werden
   * Muster: `key=value`
* **Anfrage-Timeout**  - Zeitlimit für Remote-Host-Anfrage in Millisekunden

>[!NOTE]
>
>Unabhängig davon, ob Sie den [AEM-basierten Kommunikationsfluss](#aem-driven-communication-flow) oder den [Adobe I/O Runtime-basierten Fluss implementieren, müssen Sie eine Remote-Konfiguration des Inhalts-Renderers definieren.](#adobe-i-o-runtime-driven-communication-flow)
>
>Diese Konfiguration muss auch definiert werden, wenn Sie [einen benutzerdefinierten Node.js-Server verwenden.](#using-node-js)

>[!NOTE]
>
>Diese Konfiguration nutzt den [Remote Content Renderer,](#remote-content-renderer), der über zusätzliche Erweiterungs- und Anpassungsoptionen verfügt.

## AEM-gesteuerter Kommunikationsfluss {#aem-driven-communication-flow}

Bei Verwendung von SSR umfasst der [Arbeitsablauf für Komponenteninteraktion](/help/sites-developing/spa-overview.md#workflow) von SPA in AEM eine Phase, in der der anfängliche Inhalt der App auf Adobe I/O Runtime generiert wird.

1. Der Browser fordert den SSR-Inhalt von AEM an.

1. AEM sendet das Modell an Adobe I/O Runtime.

1. Adobe I/O Runtime gibt den generierten Inhalt zurück.

1. AEM gibt den von Adobe I/O Runtime über die HTML-Vorlage der Backend-Seitenkomponente zurückgegebenen HTML-Code aus.

![server-side-rendering-cms-drivenaemnode-adobeio](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime-orientierter Kommunikationsfluss {#adobe-i-o-runtime-driven-communication-flow}

Im vorherigen Abschnitt wird die standardmäßige und empfohlene Implementierung des serverseitigen Renderings in Bezug auf SPA in AEM beschrieben, bei dem AEM das Bootstrapping und Bereitstellen von Inhalten durchführt.

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
   <th><strong>aem</strong><br /> </th>
   <td>
    <ul>
     <li>AEM verwaltet die Injektion von Bibliotheken bei Bedarf</li>
     <li>Ressourcen müssen nur auf AEM<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Möglicherweise unbekannt für SPA Entwickler<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>über Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Weitere Kenntnisse SPA Entwicklern<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-Ressourcen, die für die Anwendung erforderlich sind, wie CSS und JavaScript, müssen vom AEM-Entwickler über die <code><a href="/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet">allowProxy</a></code>-Eigenschaft<br /> verfügbar gemacht werden </li>
     <li>Ressourcen müssen zwischen AEM und Adobe I/O Runtime<br /> synchronisiert werden </li>
     <li>Um das Authoring der SPA zu aktivieren, ist unter Umständen ein Proxyserver für Adobe I/O Runtime erforderlich</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planung für SSR {#planning-for-ssr}

Im Allgemeinen muss nur ein Teil einer Anwendung serverseitig gerendert werden. Das allgemeine Beispiel ist der Inhalt, der über der Kante beim ersten Laden der Seite angezeigt wird, wird serverseitig gerendert. Dies spart Zeit, indem bereits gerenderte Inhalte an den Client gesendet werden. Wenn der Benutzer mit dem SPA interagiert, wird der zusätzliche Inhalt vom Client gerendert.

Wenn Sie erwägen, das serverseitige Rendering für Ihre SPA zu implementieren, müssen Sie überprüfen, welche Teile der App erforderlich sind.

## Entwickeln eines SPA mit SSR {#developing-an-spa-using-ssr}

SPA Komponenten können vom Client (im Browser) oder vom Server gerendert werden. Beim Rendern auf Serverseite sind keine Browsereigenschaften wie Fenstergröße und -position vorhanden. Daher sollten SPA Komponenten isomorphisch sein, ohne dass davon ausgegangen wird, wo sie gerendert werden.

Zur Nutzung von SSR müssen Sie Ihren Code sowohl in AEM als auch auf Adobe I/O Runtime bereitstellen, das für das serverseitige Rendering zuständig ist. Der Großteil des Codes ist gleich, jedoch unterscheiden sich serverspezifische Aufgaben.

## SSR für SPA in AEM {#ssr-for-spas-in-aem}

SSR für SPA in AEM erfordern Adobe I/O Runtime, das für die Wiedergabe der App Content Server-Seite aufgerufen wird. Innerhalb der HTL der App wird eine Ressource auf Adobe I/O Runtime aufgerufen, um den Inhalt zu rendern.

Ebenso wie AEM standardmäßig die Frameworks Angular und React SPA unterstützt, wird auch das serverseitige Rendering für Angular- und React-Apps unterstützt. Weitere Informationen finden Sie in der NPM-Dokumentation für beide Frameworks.

* Reaktion: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Ein einfaches Beispiel finden Sie in der [We.Retail-Protokoll-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Es rendert die gesamte Anwendungsserverseite. Obwohl dies kein echtes Beispiel ist, zeigt es doch, was zur Umsetzung der Reform des Sicherheitssektors erforderlich ist.

>[!CAUTION]
>
>Die [We.Retail-Protokoll-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) dient nur zu Demonstrationszwecken und verwendet daher Node.js als einfaches Beispiel anstelle des empfohlenen Adobe I/O Runtime. Dieses Beispiel sollte für keine Projektarbeit verwendet werden.

>[!NOTE]
>
>Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA SDK verwendet.

## Verwenden von Node.js {#using-node-js}

Adobe I/O Runtime ist die empfohlene Lösung für die Implementierung von SSR für SPA in AEM.

Bei Instanzen, die auf einer AEM ausgeführt werden, ist es auch möglich, SSR mit einer benutzerdefinierten Node.js-Instanz zu implementieren, wie oben beschrieben. Obwohl dies von Adobe unterstützt wird, wird es nicht empfohlen.

>[!NOTE]
>
>Node.js wird für Instanzen, die von Adoben gehostet AEM, nicht unterstützt.

>[!NOTE]
>
>Wenn SSR über Node.js implementiert werden muss, empfiehlt Adobe eine separate Node.js-Instanz für jede AEM Umgebung (Autor, Veröffentlichung, Stage usw.).

## Remote Content Renderer {#remote-content-renderer}

Die [Remote Content Renderer-Konfiguration](#remote-content-renderer-configuration), die erforderlich ist, um SSR mit Ihren SPA in AEM zu verwenden, tippt auf einen allgemeineren Rendering-Dienst, der erweitert und an Ihre Anforderungen angepasst werden kann.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` ist ein OSGi-Dienst zum Abrufen von Inhalten, die auf einem Remote-Server wiedergegeben werden, z. B. von Adobe I/O. Der an den Remote-Server gesendete Inhalt basiert auf dem weitergeleiteten Anforderungsparameter.

`RemoteContentRenderingService` kann durch Abhängigkeitsinversion in ein benutzerdefiniertes Sling-Modell oder Servlet eingefügt werden, wenn zusätzliche Inhaltsbearbeitung erforderlich ist.

Dieser Dienst wird intern von [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet) verwendet.

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

Das `RemoteContentRendererRequestHandlerServlet` kann verwendet werden, um die Anforderungskonfiguration programmgesteuert festzulegen. `DefaultRemoteContentRendererRequestHandlerImpl`, der bereitgestellten standardmäßigen Implementierung des Anforderungs-Handlers, ermöglicht Ihnen, mehrere OSGi-Konfigurationen zu erstellen, um einen Speicherort in der Inhaltsstruktur einem Remote-Endpunkt zuzuordnen.

Um einen benutzerdefinierten Anforderungs-Handler hinzuzufügen, implementieren Sie die `RemoteContentRendererRequestHandler`-Schnittstelle. Stellen Sie sicher, dass die Komponenteneigenschaft `Constants.SERVICE_RANKING` auf eine Ganzzahl größer als 100 eingestellt ist. Dies ist die Rangfolge von `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### OSGi-Konfiguration des Standardhandlers {#configure-default-handler} konfigurieren

Die Konfiguration des Standard-Handlers muss wie im Abschnitt [Konfiguration des Remote Content Renderers](#remote-content-renderer-configuration) beschrieben konfiguriert werden.

### Remote Content Renderer-Nutzung {#usage}

So rufen Sie ein Servlet ab und geben Inhalte zurück, die in die Seite eingefügt werden können:

1. Stellen Sie sicher, dass auf den Remote-Server zugegriffen werden kann.
1. hinzufügen eines der folgenden Snippets zur HTML-Vorlage einer AEM Komponente.
1. Optional können Sie die OSGi-Konfigurationen erstellen oder ändern.
1. Durchsuchen des Inhalts Ihrer Site

In der Regel ist die HTL-Vorlage einer Seitenkomponente der wichtigste Empfänger einer solchen Funktion.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Voraussetzungen {#requirements}

Die Servlets verwenden den Sling Model Exporter, um die Komponentendaten zu serialisieren. Standardmäßig werden sowohl `com.adobe.cq.export.json.ContainerExporter` als auch `com.adobe.cq.export.json.ComponentExporter` als Sling-Modelladapter unterstützt. Bei Bedarf können Sie Klassen hinzufügen, die die Anforderung an die Verwendung von `RemoteContentRendererServlet` und die Implementierung von `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses` anpassen sollen. Die zusätzlichen Klassen müssen das `ComponentExporter` erweitern.
