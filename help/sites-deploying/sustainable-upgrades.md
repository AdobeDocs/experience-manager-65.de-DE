---
title: Nachhaltige Aktualisierungen
description: Erfahren Sie mehr über nachhaltige Aktualisierungen in Adobe Experience Manager 6.4.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: b777fdca-e7a5-427a-9e86-688dd7cac636
source-git-commit: 26c0411d6cc16f4361cfa9e6b563eba0bfafab1e
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 18%

---

# Nachhaltige Aktualisierungen{#sustainable-upgrades}

## Anpassungsframework {#customization-framework}

### Architektur (funktional/infrastruktur/content/application)  {#architecture-functional-infrastructure-content-application}

Die Funktion des Anpassungs-Frameworks soll dazu beitragen, Verstöße in nicht erweiterbaren Bereichen des Codes (wie APIS) oder von Inhalten (wie Überlagerungen) zu reduzieren, die nicht aktualisierungsfreundlich sind.

Es gibt zwei Komponenten des Anpassungs-Frameworks: die **API-Oberfläche** und **Inhaltsklassifizierung**.

#### API-Oberfläche {#api-surface}

In früheren Versionen von Adobe Experience Manager (AEM) wurden viele APIs über das Uber Jar verfügbar gemacht. Einige dieser APIs waren nicht für die Verwendung durch Kunden vorgesehen, wurden aber für die Unterstützung AEM Funktionen in mehreren Bundles bereitgestellt. Künftig werden die Java™-APIs als öffentlich oder privat gekennzeichnet, um Kunden anzuzeigen, welche APIs im Zusammenhang mit Upgrades sicher verwendet werden können. Weitere Besonderheiten sind:

* Java™-APIs, die als `Public` kann von benutzerdefinierten Implementierungspaketen verwendet und referenziert werden.

* Die öffentlichen APIs sind abwärtskompatibel mit der Installation eines Kompatibilitätspakets.
* Das Kompatibilitätspaket enthält eine Kompatibilitäts-Uber JAR, um Abwärtskompatibilität sicherzustellen
* Java™-APIs, die als `Private` sind nur für die Verwendung AEM internen Bundles vorgesehen und sollten nicht von benutzerdefinierten Bundles verwendet werden.

>[!NOTE]
>
>Der Begriff `Private` und `Public` in diesem Zusammenhang nicht mit Java™-Vorstellungen öffentlicher und privater Klassen verwechselt werden.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### Inhaltsklassifizierungen {#content-classifications}

AEM verwendet seit langem den Prinzipal von Überlagerungen und Sling Resource Merger, um Kunden zu ermöglichen, AEM Funktionalität zu erweitern und anzupassen. Vordefinierte Funktionen, die die AEM Konsolen und die Benutzeroberfläche bedienen, werden in **/libs**. Kunden können nie etwas ändern unter **/libs** kann jedoch zusätzlichen Inhalt hinzufügen unter **/apps** , um die in **/libs** (Weitere Informationen finden Sie unter Entwickeln mit Überlagerungen .) Dies führte bei der Aktualisierung von AEM als Inhalt in **/libs** kann sich ändern, wodurch die Überlagerungsfunktion auf unerwartete Weise beschädigt wird. Kunden können AEM Komponenten auch durch Vererbung über `sling:resourceSuperType`oder einfach auf eine Komponente in verweisen **/libs** direkt über sling:resourceType. Ähnliche Aktualisierungsprobleme können bei Referenz- und Außerkraftsetzungsfällen auftreten.

So können Kunden leichter nachvollziehen, welche Bereiche von **/libs** sicher sind, den Inhalt in zu verwenden und zu überlagern **/libs** wurde mit den folgenden Mixins klassifiziert:

* **Öffentlich (granite:PublicArea)** - Definiert einen Knoten als &quot;public&quot;, damit er überlagert und vererbt werden kann ( `sling:resourceSuperType`) oder direkt verwendet ( `sling:resourceType`). Knoten unter /libs, die als öffentlich markiert sind, können mit einem Kompatibilitätspaket sicher aktualisiert werden. Im Allgemeinen sollten Kunden nur Knoten verwenden, die als &quot;Öffentlich&quot;gekennzeichnet sind.

* **Abstrakt (granite:AbstractArea)** – Definiert einen Knoten als „Abstrakt“. Knoten können überlagert oder vererbt werden ( `sling:resourceSupertype`), jedoch nicht direkt verwendet ( `sling:resourceType`).

* **Endgültig (granite:FinalArea)** – Definiert einen Knoten als „Endgültig“. Als endgültig eingestufte Knoten sollten idealerweise nicht überlagert oder vererbt werden. Endgültige Knoten können direkt über `sling:resourceType`. Unterknoten der endgültigen Knoten werden standardmäßig als intern eingestuft

* ***Intern (granite:InternalArea)*** – Definiert einen Knoten als „Intern“. Als „intern“ klassifizierte Knoten sollten idealerweise nicht überlagert, vererbt oder direkt verwendet werden. Diese Knoten sind nur für die interne Funktionalität von AEM vorgesehen.

* **Keine Anmerkung** - Knoten übernehmen die Klassifizierung basierend auf der Baumstruktur. Der /root-Wert ist standardmäßig Öffentlich. **Knoten mit einem übergeordneten Element, das als &quot;Intern&quot;oder &quot;Endgültig&quot;klassifiziert ist, sind ebenfalls als &quot;Intern&quot;zu behandeln.**

>[!NOTE]
>
Diese Richtlinien werden nur bei pfadbasierten Sling-Suchmechanismen durchgesetzt. Andere Bereiche von **/libs**, z. B. eine Client-seitige Bibliothek, die als `Internal` gekennzeichnet sind, können jedoch weiterhin mit einem standardmäßigen clientlib-Einschluss verwendet werden. Es ist wichtig, dass ein Kunde in diesen Fällen weiterhin die interne Klassifizierung berücksichtigt.

#### CRXDE Lite Content Type Indicators {#crxde-lite-content-type-indicators}

In CRXDE Lite angewendete Mixins zeigen Inhaltsknoten und -bäume an, die als `INTERNAL` abgeblendet (ausgegraut). Für `FINAL`, wird nur das Symbol abgeblendet angezeigt. Die untergeordneten Elemente dieser Knoten erscheinen ebenfalls abgeblendet. In beiden Fällen ist die Funktion Überlagerungsknoten deaktiviert.

**Öffentlich**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**Endgültig** 

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**Intern**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**Konsistenzprüfung des Inhalts**

>[!NOTE]
>
Ab AEM 6.5 empfiehlt Adobe die Verwendung der Mustererkennung, um Inhaltszugriffsverletzungen zu erkennen. Musterdetektorberichte sind detaillierter, erkennen mehr Probleme und reduzieren die Wahrscheinlichkeit falsch-positiver Ergebnisse.
>
Weitere Informationen finden Sie unter [Bewerten der Aktualisierungskomplexität mit der Mustererkennung](/help/sites-deploying/pattern-detector.md).

AEM Version 6.5 enthält eine Konsistenzprüfung, um Kunden darauf hinzuweisen, dass überlagerte oder referenzierte Inhalte auf eine Weise verwendet werden, die nicht mit der Inhaltsklassifizierung übereinstimmt.

Die Prüfung des **Sling/Granite-Inhaltszugriffs** ist eine neue Konsistenzprüfung, die das Repository überwacht, um festzustellen, ob der Kunden-Code unzulässig auf geschützte Knoten in AEM zugreift.

Das scannt **/apps** und dauert normalerweise mehrere Sekunden.

Gehen Sie wie folgt vor, um auf diese neue Konsistenzprüfung zuzugreifen:

1. Navigieren Sie auf der AEM-Startseite zu **Tools > Vorgänge > Statusberichte**
1. Klicken **Prüfung des Inhaltszugriffs auf Sling/Granite**.

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

Nachdem die Prüfung abgeschlossen ist, wird eine Liste mit Warnungen angezeigt, die einen Endbenutzer des geschützten Knotens informieren, auf den nicht ordnungsgemäß verwiesen wird:

![screen-shot-2018-2-5healthreports](assets/screenshot-2018-2-5healthreports.png)

Nach Beheben der Verstöße wird der Status &quot;grün&quot;angezeigt:

![screenshot-2018-2-5healthreports-violations](assets/screenshot-2018-2-5healthreports-violations.png)

Die Konsistenzprüfung zeigt Informationen an, die von einem Hintergrunddienst erfasst wurden, der asynchron prüft, wann immer eine Überlagerung oder ein Ressourcentyp für alle Sling-Suchpfade verwendet wird. Wenn Inhalts-Mixins falsch verwendet werden, wird ein Verstoß gemeldet.
