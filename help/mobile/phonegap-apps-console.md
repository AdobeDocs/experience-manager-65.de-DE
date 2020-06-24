---
title: Erstellen und Bearbeiten von Apps mit der Apps-Konsole
seo-title: Erstellen und Bearbeiten von Apps mit der Apps-Konsole
description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Bearbeiten von Apps mit der Apps-Konsole.
seo-description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Bearbeiten von Apps mit der Apps-Konsole.
uuid: 4f7db978-ae2b-4ca6-89f1-26e091d9140a
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 9890d045-cead-4d70-b797-95319284e0d8
translation-type: tm+mt
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '2638'
ht-degree: 2%

---


# Erstellen und Bearbeiten von Apps mit der Apps-Konsole{#creating-and-editing-apps-using-the-apps-console}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Der Entwicklungsprozess für mobile Anwendungen in AEM erkennt, dass Benutzer unterschiedlicher Expertise zur Entwicklung von mobilen Anwendungen beitragen. Die folgende Prozesszuordnung veranschaulicht die allgemeine Reihenfolge, in der Inhaltsersteller und Anwendungsentwickler Aufgaben durchführen.

![chlimage_1-10](assets/chlimage_1-10.gif)

Informationen zur Durchführung der Aufgaben von Marketer werden auf dieser Seite angezeigt. Weitere Informationen zu den Developer-Aufgaben finden Sie unter Erstellen von PhoneGap-Anwendungen.

## Die Struktur von Mobilanwendungen {#the-structure-of-mobile-applications}

AEM Mobile bietet den Phonegap-App-Entwurf zum Erstellen von Mobilanwendungen. Der Entwurf definiert die Struktur der von Ihnen erstellten Anwendungen. Anträge umfassen die folgenden Elemente:

* Die Stammseite.
* Die Sprachvarianten der Anwendung.
* Die Startseite der Sprachvariante.

### Der Stamm einer PhoneGap-App {#the-root-of-a-phonegap-app}

Die Stammseite der mobilen Anwendungen, die Sie in AEM erstellen, wird in der Apps-Konsole angezeigt.

Die Stammeseite wird unter der Eigenschaft Zielpfad der Anwendung gespeichert, die beim Erstellen der Anwendung angegeben wurde (der Standardpfad lautet /content/phonegap/apps). Der Seitenname ist die Name-Eigenschaft der Anwendung. Die Standard-URL der Stammseite der Site `myphonegapapp` lautet beispielsweise `http://localhost:4502/content/phonegap/apps/myphonegapapp.html`.

![chlimage_1-146](assets/chlimage_1-146.png)

### Die Sprachvariation einer PhoneGap-App {#the-language-variation-of-a-phonegap-app}

Die ersten untergeordneten Seiten der Stammseite sind die Sprachvarianten der Anwendung. Der Name jeder Seite ist die Sprache, für die die Anwendung erstellt wird. Beispielsweise ist Englisch der Name der englischen Variante des Antrags.

**Hinweis:** Der standardmäßige PhoneGap-Blueprint erstellt nur eine englische Anwendung. Ihr Entwickler kann den Entwurf so ändern, dass er weitere Sprachvarianten erstellen kann.

![chlimage_1-147](assets/chlimage_1-147.png)

Die Sprachseite dient zwei Zwecken:

* Der Seiteninhalt ist die Seite, auf der die Sprachvariation der Anwendung angezeigt wird.
* Die Seiteneigenschaften steuern verschiedene Designaspekte der Anwendung, z. B. die URL zum Anfordern von Inhaltsaktualisierungen und Informationen zum Herstellen einer Verbindung mit dem Cloud-Build und der Adobe Analytics Services-Integration.

![chlimage_1-148](assets/chlimage_1-148.png)

### Die Startseite {#the-home-page}

Die Startseite oder die Seite &quot;index.html&quot;einer Sprachvariante einer Anwendung wird beim Öffnen der Anwendung angezeigt. Die Startseite bietet den Benutzern ein Menü mit Links zu verschiedenen Seiten der Anwendung. Mit dem Absatzsystem können Sie Komponenten zur Seite hinzufügen, um Inhalte zu erstellen.

## Erstellen einer Mobilanwendung {#creating-a-mobile-application}

Mobile Anwendungen basieren auf einem Entwurf, der eine Seitenstruktur und Eigenschaften definiert. Sie können die folgenden Anwendungseigenschaften konfigurieren:

* **Titel:** Der Titel der Anwendung.
* **Zielpfad:** Der Speicherort im Repository, in dem die Anwendung gespeichert wird. Lassen Sie die Standardeinstellung, um einen Pfad basierend auf dem App-Namen zu erstellen.

* **Name:** Der Standardwert ist der Wert der Title-Eigenschaft, bei der Leerzeichen entfernt werden. Der Name wird in CQ verwendet, um auf die Anwendung zu verweisen, z. B. auf den Repository-Knoten, der die Anwendung darstellt.
* **Beschreibung:** Eine Beschreibung des Antrags.
* **Server-URL:** Die URL, die OTA-Inhalte (Over-the-Air) bereitstellt, wird der Anwendung aktualisiert. Der Standardwert ist die Veröffentlichungsserver-URL der Instanz, die zum Erstellen einer Anwendung verwendet wird (vom Externalisierungs-Dienst genommen). Beachten Sie, dass es sich hierbei nicht um einen Autor, sondern um eine Instanz im Veröffentlichungsserver handeln muss. Hierfür ist eine Authentifizierung erforderlich.

Sie können auch eine Bilddatei zur Verwendung als Anwendungsminiaturansicht angeben, die PhoneGap Build-Konfiguration auswählen und die zu verwendende Mobile App-Analysekonfiguration auswählen. Dieses Bild wird nur als Miniaturansicht für Ihre Mobilanwendung in der App-Konsole in Experience Manager verwendet.

Zusätzliche (und optionale) Registerkarten sind vorhanden, um den Cloud-Dienst zu erstellen und das Adobe Mobile Services SDK-Plug-In in Ihre App zu integrieren.

* Erstellen: Klicken Sie auf Konfigurationen verwalten und richten Sie hier Ihren Build-Dienst build.phonegap.com ein. Dann können Sie aus der Dropdownliste den neu erstellten PhoneGap Build Cloud-Dienst auswählen.
* Analytics: Klicken Sie auf Konfigurationen verwalten und richten Sie Ihren [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/using/home.html) -Cloud-Dienst ein. Anschließend können Sie aus der Dropdownliste den neu erstellten Mobile Service auswählen, der in Ihre mobile App integriert werden soll.

>[!NOTE]
>
>Entwickler können das AEM PhoneGap Starter Kit verwenden, um Apps zu erstellen und sie der Konsole hinzuzufügen.

Im folgenden Verfahren wird die Touch-Benutzeroberfläche zum Erstellen einer mobilen Anwendung verwendet.

1. Klicken Sie in der Leiste auf Apps.
1. Klicken oder tippen Sie auf das Symbol Erstellen.

   ![](do-not-localize/chlimage_1-7.png)

1. (Optional) Geben Sie auf der Registerkarte &quot;Erweitert&quot;eine Beschreibung für die Anwendung ein und ändern Sie bei Bedarf die Server-URL.
1. (Optional) Wenn Sie die Anwendung mit PhoneGap Build kompilieren, wählen Sie auf der Registerkarte &quot;Erstellen&quot;die zu verwendende Konfiguration aus.

   Um eine PhoneGap-Buildkonfiguration zu erstellen, klicken Sie auf Konfigurationen verwalten.

1. (Optional) Wenn Sie SiteCatalyst zur Verfolgung der Aktivität von Anwendungen verwenden, wählen Sie auf der Registerkarte &quot;Analytics&quot;die zu verwendende Konfiguration aus.

   Um eine Mobile App-Konfiguration zu erstellen, klicken Sie auf Konfigurationen verwalten.

1. (Optional) Um ein Anwendungssymbol bereitzustellen, klicken Sie auf die Schaltfläche &quot;Durchsuchen&quot;, wählen Sie die Bilddatei im Dateisystem aus und klicken Sie auf &quot;Öffnen&quot;.
1. Klicken Sie auf Erstellen.

### Eigenschaften einer Mobilanwendung ändern {#changing-the-properties-of-a-mobile-application}

Nachdem Sie eine Mobilanwendung erstellt haben, können Sie die Eigenschaften ändern.

#### Titel, Beschreibung und Symbol ändern {#change-the-title-description-and-icon}

1. Klicken Sie in der Leiste auf oder tippen Sie auf Apps.
1. Wählen Sie die zu konfigurierende Ansicht aus und klicken Sie auf das Symbol Seiteneigenschaften.

   ![](do-not-localize/chlimage_1-8.png)

1. Um die Eigenschaftswerte zu ändern, klicken Sie auf das Symbol Bearbeiten oder tippen Sie darauf.

   ![](do-not-localize/chlimage_1-9.png)

1. Konfigurieren Sie die Eigenschaften &quot;Einfach&quot;und &quot;Erweitert&quot;und klicken Sie dann auf das Symbol &quot;Fertig&quot;.

   ![](do-not-localize/chlimage_1-10.png)

#### Konfigurieren einer Sprachvariation der Anwendung {#configure-a-language-variation-of-the-application}

1. Klicken Sie in der Leiste auf oder tippen Sie auf Apps.
1. Klicken Sie auf , um einen Drilldown für die mobile Anwendung durchzuführen, die Sie in der Admin-Konsole von Apps bearbeiten möchten. Wählen Sie die zu konfigurierende Sprachversion der Ansicht aus und klicken Sie auf das Symbol Anwendungseigenschaften.

   ![](do-not-localize/chlimage_1-11.png)

1. Um die Eigenschaftswerte zu ändern, klicken Sie auf das Symbol Bearbeiten oder tippen Sie darauf.

   ![](do-not-localize/chlimage_1-12.png)

1. Konfigurieren Sie die Eigenschaften auf den Registerkarten &quot;Einfach&quot;, &quot;Erweitert&quot;, &quot;Erstellen&quot;und &quot;Analytics&quot;und klicken Sie dann auf das Symbol &quot;Fertig&quot;.

   ![](do-not-localize/chlimage_1-13.png)

### Erstellen des Inhalts einer mobilen Anwendung {#authoring-the-content-of-a-mobile-application}

Nachdem Sie die Mobilanwendung erstellt haben, fügen Sie Inhalte hinzu, die als Benutzeroberfläche der Anwendung verwendet werden.

1. Klicken Sie in der Leiste auf oder tippen Sie auf Apps.
1. Klicken Sie auf oder tippen Sie auf die Anwendung und klicken Sie dann auf oder tippen Sie auf Englisch.
1. Bearbeiten Sie die Startseite oder fügen Sie nach Bedarf untergeordnete Seiten hinzu.

### Verschieben von Inhalten in mobile Anwendungen {#moving-content-to-mobile-applications}

Der Inhaltssynchronisierungscache in der AEM-Veröffentlichungsinstanz wird als Repository für Inhalte für mobile Anwendungen verwendet:

* Inhalte im Inhaltssynchronisierungs-Cache werden in der Anwendung enthalten, wenn Entwickler die Anwendung kompilieren.
* Inhalte im Cache stehen für installierte Mobilanwendungen zur Aktualisierung des Anwendungsinhalts zur Verfügung.

Mobile Anwendungen enthalten einen Befehl &quot;Updates&quot;, mit dem aktualisierte Anwendungsinhalte heruntergeladen und installiert werden. Wenn eine Anwendungsinstanz eine Aktualisierungsanforderung sendet, bestimmt die Inhaltssynchronisierung, welche Inhalte sich seit der letzten Aktualisierung oder Installation der Anwendung geändert haben, und stellt den neuen Inhalt bereit.

![chlimage_1-149](assets/chlimage_1-149.png)

Um aktualisierte Inhalte für Anwendungen verfügbar zu machen, aktualisieren Sie den Content Sync-Cache. Wenn Sie den Cache zum ersten Mal aktualisieren, werden alle veröffentlichten Inhalte hinzugefügt. Bei nachfolgenden Aktualisierungen werden nur die veröffentlichten Inhalte hinzugefügt, die sich seit der letzten Aktualisierung geändert haben.

Bei der Inhaltssynchronisierung wird auch verfolgt, wann die Aktualisierungen stattfinden. Anhand dieser Informationen kann die Inhaltssynchronisierung bestimmen, welches Cache-Update an eine Mobilanwendung gesendet werden soll.

Führen Sie das folgende Verfahren für die Instanz durch, auf der Sie den Cache aktualisieren möchten. Wenn Ihre Anwendung beispielsweise Updates von der Veröffentlichungsinstanz anfordert, führen Sie das Verfahren für die Veröffentlichungsinstanz aus.

1. Klicken Sie in der Leiste auf oder tippen Sie auf Apps und dann auf Ihre Anwendung.
1. Wählen Sie die Begrüßungsseite aus und klicken Sie dann auf das Symbol &quot;Cache aktualisieren&quot;oder tippen Sie darauf.

   ![](do-not-localize/chlimage_1-14.png)

### Verwenden von App-Vorlagen {#using-app-templates}

Diese Funktion ist mit Apps 6.1 Feature Pack 2 verfügbar und bietet eine einfache Möglichkeit, vorhandene App-Vorlagen für die Erstellung neuer Apps in AEM zu nutzen.

Was ist eine App-Vorlage? Stellen Sie sich dies als eine Sammlung von Seitenvorlagen und Komponenten vor, die eine Grundlage oder Grundlage einer App darstellen.
Wenn Sie eine neue App erstellen, die auf der Vorlage einer anderen App basiert, erhalten Sie eine App mit einem Startpunkt, der der App entspricht, aus der sie erstellt wurde.

Sie müssen über eine vorhandene mobile App-Vorlage verfügen (oder eine App mit einer App-Vorlage installiert haben), um diese Funktion nutzen zu können.

Das neueste AEM Apps 6.1-Musterpaket enthält eine aktualisierte Version der Geometrixx-App mit einer App-Vorlage. Alternativ können Sie das StarterKit installieren, das auch eine Vorlage bereitstellt.

Schritte zum Erstellen einer neuen App basierend auf einer App-Vorlage:

1. Vergewissern Sie sich, dass das neueste AEM Apps 6.1 Feature Pack und Referenzbeispiele installiert sind
1. Klicken Sie in der linken Leiste auf Apps.

![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Klicken Sie oben auf die Schaltfläche + Erstellen und wählen Sie App erstellen.
1. Nachdem Sie die Liste der App-Vorlagen angezeigt haben, wählen Sie eine aus:

![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Klicken Sie auf Weiter.
1. Geben Sie eine App-ID und einen Titel ein, Sie sollten jedoch auch einen Namen und eine Beschreibung angeben.

   1. Darüber hinaus können Sie ein PNG-Format (unterstütztes PhoneGap-Symbolformat) als Symbol bereitstellen, indem Sie in AEM-Assets navigieren.
   1. Denken Sie daran, dass Sie alle diese Felder bearbeiten können, nachdem die App in der Kachel App verwalten erstellt wurde. Mit Ausnahme der App-ID können Sie die App-ID nach dem Festlegen nicht mehr ändern.

![chlimage_1-150](assets/chlimage_1-150.png)

1. Klicken Sie auf die Schaltfläche &quot;Erstellen&quot;. Es stehen Ihnen zwei Optionen zur Verfügung: &quot;Fertig&quot;(Zurück zur App-Ansicht) oder &quot;App verwalten&quot;(Öffnen des App-Dashboards).
1. Nach der Erstellung sollte die neue App im App-Katalog aufgeführt werden:

![chlimage_1-3](assets/chlimage_1-3.jpeg)

1. Klicken Sie auf die App, um sie zu öffnen. Sie haben erfolgreich eine neue App erstellt, die auf der Vorlage einer vorhandenen App basiert.

>[!NOTE]
>
>Wenn Sie das Geometrixx Outdoors-Referenz-App-Paket aus AEM deinstallieren und eine App basierend auf der Vorlage erstellt haben, funktioniert diese App nicht mehr. Die Geometrixx Outdoors-App kann entfernt werden. Die App-Vorlage muss jedoch erhalten bleiben, wenn sie von anderen mobilen Anwendungen verwendet wird.

## Die Beispielanwendung Geometrixx Outdoors {#exploring-the-sample-geometrixx-outdoors-app}

Die Geometrixx Outdoors-App ist eine Beispielanwendung für PhoneGap, die die Funktionen des standardmäßigen PhoneGap-Anwendungsblueprints und der mobilen Musterkomponenten demonstriert.

Um die Anwendung zu öffnen, klicken Sie in der Leiste auf Mobile Applications und wählen Sie dann Geometrixx Outdoors-App.

### Allgemeine Seitenfunktionen - Geometrixx Mobile-App {#common-page-features-geometrixx-mobile-app}

Jede Seite der mobilen App umfasst die folgenden Funktionen:

* Eine Zurück-Schaltfläche zum Zurückkehren zur übergeordneten Seite. Beachten Sie, dass die Schaltfläche &quot;Zurück&quot;nicht auf der Startseite angezeigt wird.
* Eine erweiterte Leiste, die ein Menü mit Befehlen und Links Angebot:

   * Öffnen Sie die Seite &quot;Speicherorte&quot;.
   * Öffnen Sie den Warenkorb.
   * Melden Sie sich an.
   * Aktualisieren Sie die Anwendung.

* Das Absatzsystem zum Hinzufügen von Komponenten und Erstellen von Inhalten.

### Startseite - Geometrixx-Mobil-App {#the-home-page-geometrixx-mobile-app}

Der Inhalt der Startseite besteht aus den folgenden Navigationswerkzeugen:

* Eine Menükomponente, die Links zu den Unterseiten &quot;Gear&quot;, &quot;Reviews&quot;, &quot;News&quot;und &quot;Über uns&quot;enthält.
* Eine Swipe Carousel-Komponente, die die untergeordneten Seiten darstellt.

### Zahnradseite - Geometrixx-Mobil-App {#the-gear-page-geometrixx-mobile-app}

Die Seite &quot;Gear&quot;bietet Benutzern Zugriff auf Produktseiten. Eine Komponente der Menu-Liste bietet Zugriff auf die untergeordneten Seiten der Zahnradseite. Die untergeordneten Seiten sind Kategorien von Produkten, die die Website enthält.

* Saison
* Bekleidung
* Geschlecht
* Aktivität

Jede Seite der Kategorie verwendet dieselbe Inhaltsstruktur wie die Seite &quot;Gear&quot;. Das Karussell bietet Zugriff auf untergeordnete Seiten, die Unterkategorien von Produkten sind. Die Seiten der Unterkategorie enthalten Produktauflistungen, die Links zu Produktseiten enthalten.

### Produktseite - Geometrixx Mobile-App {#the-products-page-geometrixx-mobile-app}

Die Seite &quot;Produkte&quot;und ihre Hierarchie untergeordneter Seiten implementieren ein Klassifizierungssystem für Produktseiten. Die untersten Seiten in jeder Zweigstelle der Hierarchie sind Produktseiten, die eine ng-Produktkomponente enthalten.

Die Seite &quot;Produkte&quot;steht Anwendungsbenutzern nicht zur Verfügung. Die Zahnradseite bietet Zugriff auf jede Produktseite.

### Reviews Page - Geometrixx Mobile App {#the-reviews-page-geometrixx-mobile-app}

Enthält eine Zurück-Schaltfläche. Mit dem Absatzsystem können Sie Komponenten hinzufügen.

Bei Verwendung der Anwendung ist die Seite &quot;Reviews&quot;im Karussell auf der englischen Seite verfügbar.

### News-Seite - Geometrixx-Mobil-App {#the-news-page-geometrixx-mobile-app}

Enthält eine Zurück-Schaltfläche. Mit dem Absatzsystem können Sie Komponenten hinzufügen.

Wenn Sie die Anwendung verwenden, ist die Seite Nachrichten im Karussell auf der englischen Seite verfügbar.

### Die Seite &quot;Info&quot;- Geometrixx-Mobil-App {#the-about-us-page-geometrixx-mobile-app}

Die Seite &quot;Über uns&quot;enthält mehrere Komponenten für zwei Spalten. Jede Spalte enthält entweder eine Bild- oder eine Text-Komponente. Die Komponenten können bearbeitet werden, und das Absatzsystem ermöglicht es Ihnen, Komponenten hinzuzufügen.

Wenn Sie die Anwendung verwenden, ist die Info-Seite im Karussell auf der englischen Seite verfügbar.

### Die Seite &quot;Speicherorte&quot;- Geometrixx-Mobil-App {#the-locations-page-geometrixx-mobile-app}

Die Seite &quot;Speicherorte&quot;enthält eine Komponente &quot;Speicherorte&quot;.

Wenn Sie die Anwendung verwenden, ist die Seite &quot;Speicherorte&quot;in der Menü-Liste auf der englischen Seite verfügbar.

## Beispiele für mobile Komponenten {#sample-mobile-components}

Beim Authoring der Seiten einer mobilen Anwendung stehen in Sidekick sofort mehrere Komponenten zur Verfügung. Die Komponenten gehören zur Gruppe der PhoneGap-Komponenten.

### Swipe-Karussell {#swipe-carousel}

Die Komponente &quot;Karussell blättern&quot;ist ein Werkzeug zum Anzeigen und Navigieren auf Seiten der Site. Die Komponente enthält ein Karussell, das die Bilder für die Seiten über einer Liste von Seitenlinks durchläuft. Bearbeiten Sie die Komponente, um die anzuzeigenden Seiten und das Verhalten des Karussells anzugeben.

Beachten Sie, dass Bilder im Karussell für Seiten angezeigt werden, die auf eine bestimmte Weise mit einem Bild verknüpft sind. Wenn Seiten nicht mit Bildern verknüpft sind, wird nur die Liste der Links angezeigt.

![chlimage_1-151](assets/chlimage_1-151.png)

**Karussell-Eigenschaften, Registerkarte**

Verhalten des Karussels konfigurieren:

* Abspielgeschwindigkeit: Die Zeit in Millisekunden, die jedes Bild angezeigt wird, bevor das nächste Bild angezeigt wird.
* Transition: Die Dauer der Animation in Millisekunden für Transitionen.
* Steuerelementstil: Die Art der Steuerelemente, die zum Wechseln zwischen Bildern bereitgestellt werden.

**Registerkarte &quot;Eigenschaften&quot;**

Geben Sie an, wie die Liste der Seite generiert wird:

* Liste erstellen mit: Die Methode zur Angabe der Seiten, die in das Karussell aufgenommen werden sollen. Siehe Erstellen der Liste &quot;Seite&quot;.
* Reihenfolge nach: Wählen Sie eine Seiteneigenschaft zum Sortieren der Liste aus. Wählen Sie beispielsweise &quot;jcr:title&quot;aus, um die Seiten alphabetisch nach Titel zu sortieren.
* Maximal: Die maximale Anzahl der einzuschließenden Seiten. Diese Eigenschaft eignet sich für suchbasierte Methoden zum Erstellen der Liste der Seite.

#### Erstellen der Liste der Seite {#building-the-page-list}

Die Komponente &quot;Karussell blättern&quot;stellt die folgenden Werte für die Eigenschaft &quot;Liste erstellen mit&quot;bereit. Das Dialogfeld &quot;Bearbeiten&quot;ändert sich je nach ausgewähltem Wert:

**Untergeordnete Seiten**

Die Komponente Liste alle untergeordneten Seiten einer bestimmten Seite. Wählen Sie nach Auswahl dieses Wertes die Seite auf der Registerkarte &quot;Untergeordnete Seiten&quot;aus oder geben Sie keinen Wert für die Liste der untergeordneten Elemente der aktuellen Seite an.

**Liste fester Werte**

Geben Sie eine Liste der Einschlussseiten an. Nachdem Sie diesen Wert ausgewählt haben, konfigurieren Sie die Liste auf der Registerkarte &quot;Feste Liste&quot;, die angezeigt wird, wenn Sie &quot;Feste Liste&quot;auswählen:

* Um eine Seite hinzuzufügen, klicken Sie auf Hinzufügen Element und suchen Sie dann nach der Seite.
* Verwenden Sie die Pfeilsymbole nach oben und unten, um die Liste zu verschieben.
* Klicken Sie auf die Schaltfläche &quot;Entfernen&quot;, um eine Seite aus der Liste zu entfernen.

Die Eigenschaft &quot;Reihenfolge nach&quot;hat keine Auswirkungen auf die Reihenfolge der festen Listen.

**Suchen**

Füllen Sie die Liste mit den Ergebnissen einer Suchbegriffsuche. Die Suche wird in den untergeordneten Elementen einer Seite durchgeführt, die Sie angeben:

1. Um die Stammseite der Suche festzulegen, wählen Sie den Seitenpfad mit der Eigenschaft &quot;Beginn in&quot;aus. Geben Sie keinen Pfad für die Suche unterhalb der aktuellen Seite an.
1. Geben Sie in der Eigenschaft Abfrage suchen die Suchbegriffe ein.

**Erweiterte Suche**

Füllen Sie die Liste mit einer [Querybuilder](/help/sites-developing/querybuilder-api.md) -Abfrage.

### Bild {#image}

Hinzufügen Sie ein Bild in Ihren Anwendungsinhalt.

### Text {#text}

Hinzufügen Rich-Text in Ihren Anwendungsinhalt.

### Filialen {#store-locations}

Die Komponente &quot;Speicherorte&quot;bietet Benutzern Werkzeuge zum Suchen von Geschäftsfeldern:

* Suchen
* Listen von Positionen, die in der Nähe oder in der Entfernung zu den GPS-Koordinaten des Geräts liegen.

Die Komponente erfordert, dass das Repository Informationen zum Speicherort für jeden Store enthält. Beispielspeicherorte werden unter dem Knoten /etc/commerce/locations/adobe installiert. ![chlimage_1-152](assets/chlimage_1-152.png)

### Zeile mit zwei Spalten {#two-column-row}

Ermöglicht das Hinzufügen von Komponenten nebeneinander zu einer Seite.

![chlimage_1-153](assets/chlimage_1-153.png)
