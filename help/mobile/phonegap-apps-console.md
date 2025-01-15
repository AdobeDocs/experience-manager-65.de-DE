---
title: Erstellen und Bearbeiten von Apps mit der Apps-Konsole
description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Bearbeiten von Apps mithilfe der Apps-Konsole.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 49e0b3f6-7ac7-4417-9c31-cc3d3c2305f3
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '2654'
ht-degree: 1%

---

# Erstellen und Bearbeiten von Apps mit der Apps-Konsole{#creating-and-editing-apps-using-the-apps-console}

{{ue-over-mobile}}

Im Entwicklungsprozess für AEM-Mobile-Apps wird anerkannt, dass Nutzer mit unterschiedlichen Fachkenntnissen zur Entwicklung von Mobile Apps beitragen. Die folgende Prozesskarte veranschaulicht die allgemeine Reihenfolge, in der Inhaltsautoren und Anwendungsentwickler Aufgaben ausführen.

![chlimage_1-10](assets/chlimage_1-10.gif)

Informationen zum Ausführen der Aufgaben für Marketing-Fachleute werden auf dieser Seite angezeigt. Weitere Informationen zu den Entwickleraufgaben finden Sie unter Erstellen von PhoneGap-Anwendungen.

## Die Struktur mobiler Anwendungen {#the-structure-of-mobile-applications}

AEM Mobile stellt die Phonegap-App-Blueprint zum Erstellen von Mobile Apps bereit. Der Blueprint definiert die Struktur der von Ihnen erstellten Programme. Die Anträge bestehen aus folgenden Elementen:

* Die Stammseite.
* Die Sprachvarianten der Anwendung.
* Die Startseite der Sprachvariante.

### Das Stammverzeichnis einer PhoneGap-App {#the-root-of-a-phonegap-app}

Die Stammseite der Mobile Apps, die Sie in AEM erstellen, wird in der Apps-Konsole angezeigt.

Die Stammseite wird unter der Eigenschaft Zielpfad der Anwendung gespeichert, die beim Erstellen der Anwendung angegeben wurde (der Standardpfad ist /content/phonegap/apps). Der Seitenname ist die Name-Eigenschaft der Anwendung. Beispielsweise lautet die Standard-URL der Stammseite der Website mit dem Namen `myphonegapapp` `http://localhost:4502/content/phonegap/apps/myphonegapapp.html`.

![chlimage_1-146](assets/chlimage_1-146.png)

### Die Sprachvariante einer PhoneGap-App {#the-language-variation-of-a-phonegap-app}

Die ersten untergeordneten Seiten der Stammseite sind die Sprachvarianten des Programms. Der Name jeder Seite ist die Sprache, für die das Programm erstellt wird. Englisch ist beispielsweise der Name der englischen Variante des Programms.

**Hinweis:** Der standardmäßige PhoneGap-Blueprint erstellt nur eine englische Anwendung. Ihr Entwickler kann die Blueprint ändern, sodass mehr Sprachvarianten erstellt werden können.

![chlimage_1-147](assets/chlimage_1-147.png)

Die Sprachseite dient zwei Zwecken:

* Der Seiteninhalt ist die Splash-Seite für die Sprachvariante des Programms.
* Die Seiteneigenschaften steuern mehrere Design-Aspekte des Programms, z. B. die URL, die zum Anfordern von Inhaltsaktualisierungen verwendet werden soll, und Informationen zur Verbindung mit dem Cloud-Build und der Adobe Analytics Services-Integration.

![chlimage_1-148](assets/chlimage_1-148.png)

### Die Startseite {#the-home-page}

Die Startseite oder index.html-Seite einer Sprachvariante eines Programms wird angezeigt, wenn das Programm geöffnet wird. Die -Startseite bietet Benutzenden ein Menü mit Links zu verschiedenen Seiten in der Anwendung. Mit dem Absatzsystem können Sie der Seite Komponenten zum Erstellen von Inhalten hinzufügen.

## Erstellen einer Mobile App {#creating-a-mobile-application}

Mobile Apps basieren auf einem Blueprint, der eine Seitenstruktur und Eigenschaften definiert. Sie können die folgenden Anwendungseigenschaften konfigurieren:

* **Titel:** Der Titel der Anwendung.
* **Zielpfad:** Der Speicherort im Repository, in dem die Anwendung gespeichert ist. Behalten Sie die Standardeinstellung bei, um einen Pfad basierend auf dem App-Namen zu erstellen.

* **Name:** Der Standardwert ist der Wert der Eigenschaft „Title“, wobei Leerzeichen entfernt werden. Der Name wird in CQ verwendet, um auf das Programm zu verweisen, z. B. für den Repository-Knoten, der das Programm darstellt.
* **Beschreibung:** Eine Beschreibung der Anwendung.
* **Server-URL:** Die URL, die OTA-Inhaltsaktualisierungen (Over-the-Air) für die Anwendung bereitstellt. Der Standardwert ist die Veröffentlichungs-Server-URL der -Instanz, die zum Erstellen einer Anwendung verwendet wird (entnommen aus dem Externalizer-Service). Beachten Sie, dass es sich hierbei um eine Veröffentlichungs-Server-Instanz und nicht um einen Autor handeln muss, wofür eine Authentifizierung erforderlich ist.

Sie können auch eine Bilddatei bereitstellen, die als Miniaturansicht der Anwendung verwendet werden soll, die zu verwendende PhoneGap Build-Konfiguration auswählen und die zu verwendende Mobile-App-Analysekonfiguration auswählen. Dieses Bild wird nur als Miniaturansicht verwendet, um Ihre Mobile App in der Mobile-Apps-Konsole im Experience Manager darzustellen.

Es gibt zusätzliche (und optionale) Registerkarten für Build Cloud Service und die Integration des Adobe Mobile Services SDK-Plug-ins in Ihre App.

* Build: Klicken Sie auf Konfigurationen verwalten und richten Sie Ihren build.phonegap.com Build-Dienst hier ein. Dann können Sie aus der Dropdown-Liste den neu erstellten PhoneGap-Build-Cloud-Service auswählen.
* Analytics: Klicken Sie auf „Konfigurationen verwalten“ und richten Sie Ihren [Adobe Mobile Services SDK](https://experienceleague.adobe.com/docs/mobile-services/using/home.html)-Cloud-Service ein. Anschließend können Sie aus der Dropdown-Liste den neu erstellten Mobile Service auswählen, der in Ihre Mobile App integriert werden soll.

>[!NOTE]
>
>Entwickler können das AEM PhoneGap Starter Kit verwenden, um Apps zu erstellen und sie zur Konsole hinzuzufügen.

Beim folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche verwendet, um eine Mobile App zu erstellen.

1. Klicken Sie in der Leiste auf Apps .
1. Klicken Sie auf das Symbol Erstellen .

   ![Das Symbol „Erstellen“ wird durch ein Pluszeichen innerhalb eines Quadrats angezeigt.](do-not-localize/chlimage_1-7.png)

1. (Optional) Geben Sie auf der Registerkarte „Erweitert“ eine Beschreibung für das Programm ein und ändern Sie bei Bedarf die Server-URL.
1. (Optional) Wenn Sie PhoneGap Build zum Kompilieren des Programms verwenden, wählen Sie auf der Registerkarte Erstellen die zu verwendende Konfiguration aus.

   Um eine PhoneGap-Build-Konfiguration zu erstellen, klicken Sie auf Konfigurationen verwalten .

1. (Optional) Wenn Sie SiteCatalyst zur Verfolgung der Anwendungsaktivität verwenden, wählen Sie auf der Registerkarte „Analytics“ die zu verwendende Konfiguration aus.

   Um eine Mobile-App-Konfiguration zu erstellen, klicken Sie auf Konfigurationen verwalten.

1. (Optional) Um ein Anwendungssymbol bereitzustellen, klicken Sie auf die Schaltfläche Durchsuchen, wählen Sie die Bilddatei aus Ihrem Dateisystem aus und klicken Sie auf Öffnen .
1. Klicken Sie auf „Erstellen“.

### Ändern der Eigenschaften einer Mobile App {#changing-the-properties-of-a-mobile-application}

Nachdem Sie eine Mobile App erstellt haben, können Sie die Eigenschaften ändern.

#### Ändern von Titel, Beschreibung und Symbol {#change-the-title-description-and-icon}

1. Klicken Sie in der Leiste auf Apps .
1. Wählen Sie die zu konfigurierende Anwendung aus und klicken Sie auf das Symbol Seiteneigenschaften anzeigen .

   ![Das Symbol „Seiteneigenschaften anzeigen“, das durch den Buchstaben „I“ in einem Kreis angezeigt wird.](do-not-localize/chlimage_1-8.png)

1. Um die Eigenschaftswerte zu ändern, klicken Sie auf das Symbol Bearbeiten .

   ![Das Bearbeitungssymbol, das durch einen Bleistift angezeigt wird.](do-not-localize/chlimage_1-9.png)

1. Konfigurieren Sie die Eigenschaften „Standard“ und „Erweitert“, und klicken Sie dann auf das Symbol „Fertig“.

   ![Das Symbol „Fertig“, das durch ein Häkchen gekennzeichnet wird.](do-not-localize/chlimage_1-10.png)

#### Konfigurieren einer Sprachvariante der Anwendung {#configure-a-language-variation-of-the-application}

1. Klicken Sie in der Leiste auf Apps .
1. Klicken Sie hier, um einen Drill-in für die Mobile App durchzuführen, die Sie in der Apps-Admin Console bearbeiten möchten. Wählen Sie die Sprachversion des zu konfigurierenden Programms aus und klicken Sie auf das Symbol Anwendungseigenschaften anzeigen .

   ![Das Symbol „Anwendungseigenschaften anzeigen“, angezeigt durch den Buchstaben I innerhalb eines Kreises.](do-not-localize/chlimage_1-11.png)

1. Um die Eigenschaftswerte zu ändern, klicken Sie auf das Symbol Bearbeiten .

   ![Das Bearbeitungssymbol, das durch einen Bleistift angezeigt wird.](do-not-localize/chlimage_1-12.png)

1. Konfigurieren Sie die Eigenschaften auf den Registerkarten „Allgemein“, „Erweitert“, „Erstellen“ und „Analytics“ und klicken Sie dann auf das Symbol „Fertig“.

   ![Das Symbol „Fertig“, das durch ein Häkchen gekennzeichnet wird.](do-not-localize/chlimage_1-13.png)

### Verfassen des Inhalts einer Mobile App {#authoring-the-content-of-a-mobile-application}

Fügen Sie nach dem Erstellen der Mobile App Inhalte hinzu, die als Anwendungs-Benutzeroberfläche verwendet werden.

1. Klicken Sie in der Leiste auf Apps .
1. Klicken Sie auf die Anwendung und dann auf Englisch.
1. Bearbeiten Sie die Startseite oder fügen Sie untergeordnete Seiten hinzu.

### Verschieben von Inhalten zu Mobile Apps {#moving-content-to-mobile-applications}

Der Inhaltssynchronisierungs-Cache auf der AEM-Veröffentlichungsinstanz wird als Content-Repository für Mobile Apps verwendet:

* Inhalte im Inhaltssynchronisierungs-Cache werden in die Anwendung aufgenommen, wenn Entwickler die Anwendung kompilieren.
* Der Inhalt im Cache steht installierten Mobile Apps zur Aktualisierung des Inhalts der Mobile App zur Verfügung.

Mobile Apps enthalten den Befehl Updates , mit dem aktualisierte Programminhalte heruntergeladen und installiert werden. Wenn eine Anwendungsinstanz eine Aktualisierungsanfrage sendet, bestimmt die Inhaltssynchronisierung, welcher Inhalt sich seit der letzten Aktualisierung oder Installation der Anwendung geändert hat, und stellt den neuen Inhalt bereit.

![chlimage_1-149](assets/chlimage_1-149.png)

Um aktualisierte Inhalte für Programme verfügbar zu machen, aktualisieren Sie den Inhaltssynchronisierungs-Cache. Wenn Sie den Cache zum ersten Mal aktualisieren, werden alle veröffentlichten Inhalte hinzugefügt. Nachfolgende Aktualisierungen fügen nur die veröffentlichten Inhalte hinzu, die sich seit der vorherigen Aktualisierung geändert haben.

Die Inhaltssynchronisierung verfolgt auch, wann die Aktualisierungen erfolgen. Mit diesen Informationen kann die Inhaltssynchronisierung bestimmen, welche Cache-Aktualisierung an eine Mobile App gesendet werden soll.

Führen Sie das folgende Verfahren auf der Instanz durch, auf der Sie den Cache aktualisieren möchten. Wenn Ihre Anwendung beispielsweise Aktualisierungen von der Veröffentlichungsinstanz anfordert, führen Sie das Verfahren auf der Veröffentlichungsinstanz durch.

1. Klicken Sie in der Leiste auf Programme und dann auf Ihr Programm.
1. Wählen Sie die Splash-Seite aus und klicken Sie dann auf das Symbol Cache aktualisieren .

   ![Das Symbol Cache aktualisieren , angezeigt durch einen gestreiften Lauf mit einem Papierkorbsymbol darüber.](do-not-localize/chlimage_1-14.png)

### Verwenden von App-Vorlagen {#using-app-templates}

Dies ist eine Funktion, die mit Apps 6.1 Feature Pack 2 verfügbar ist und eine einfache Möglichkeit bietet, vorhandene App-Vorlagen für die Erstellung neuer Apps in AEM zu verwenden.

Was ist eine App-Vorlage? Stellen Sie sich dies als eine Sammlung von Seitenvorlagen und Komponenten vor, die eine Grundlinie oder die Grundlage einer App darstellen.
Wenn Sie eine App basierend auf der Vorlage einer anderen App erstellen, erhalten Sie eine App, deren Startpunkt repräsentativ für die App ist, aus der sie erstellt wurde.

Sie müssen über eine vorhandene Mobile-App-Vorlage (oder eine installierte App mit einer App-Vorlage) verfügen, um diese Funktion verwenden zu können.

Das neueste Beispielpaket für AEM Apps 6.1 enthält eine aktualisierte Version der Geometrixx-App mit einer App-Vorlage. Alternativ können Sie das StarterKit installieren, das auch eine Vorlage bereitstellt.

Schritte zum Erstellen einer App basierend auf einer App-Vorlage:

1. Stellen Sie sicher, dass Sie das neueste Feature Pack und die neuesten Referenzbeispielpakete für AEM Apps 6.1 installiert haben
1. Klicken Sie in der linken Leiste auf Apps .

![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Klicken Sie oben auf die Schaltfläche + Erstellen und wählen Sie App erstellen aus.
1. Sobald Ihnen die Liste der App-Vorlagen angezeigt wird, wählen Sie eine aus:

![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Klicken Sie auf Weiter.
1. Geben Sie eine App-ID und einen Titel an. Sie können aber auch einen Namen und eine Beschreibung hinzufügen.

   1. Sie können auch ein PNG (unterstütztes PhoneGap-Symbolformat) als Symbol bereitstellen, indem Sie AEM-Assets durchsuchen.
   1. Denken Sie daran, dass Sie alle diese Felder bearbeiten können, nachdem die App in der Kachel „Programm verwalten“ erstellt wurde. Mit Ausnahme der App-ID können Sie die App-ID nicht mehr ändern, sobald die App-ID festgelegt wurde.

![chlimage_1-150](assets/chlimage_1-150.png)

1. Klicken Sie auf die Schaltfläche „Erstellen“. Ihnen werden zwei Optionen angezeigt: „Fertig“ (zurück zur App-Katalogansicht) oder „App verwalten“ (öffnet das App-Dashboard).
1. Nach der Erstellung sollte die neue App im App-Katalog aufgelistet sein:

![chlimage_1-3](assets/chlimage_1-3.jpeg)

1. Klicken Sie auf die App, um sie zu öffnen. Sie haben erfolgreich eine neue App basierend auf der Vorlage einer vorhandenen App erstellt.

>[!NOTE]
>
>Wenn Sie das Geometrixx Outdoors-Referenz-App-Paket von AEM deinstallieren und eine App basierend auf der Vorlage erstellen lassen, ist diese App nicht mehr funktionsfähig. Die Geometrixx Outdoors-App kann entfernt werden. Die App-Vorlage muss jedoch erhalten bleiben, wenn sie von anderen Mobile Apps verwendet wird.

## Erkunden der Beispiel-Geometrixx Outdoors-App {#exploring-the-sample-geometrixx-outdoors-app}

Die Geometrixx Outdoors-App ist eine Beispiel-PhoneGap-Anwendung, die die Funktionen des Standard-Blueprints für PhoneGap-Anwendungen und die Beispiel-Komponenten für Mobilgeräte veranschaulicht.

Klicken Sie zum Öffnen der Anwendung in der Leiste auf Mobile Apps und wählen Sie Geometrixx Outdoors-App aus.

### Allgemeine Seitenfunktionen - Geometrixx Mobile App {#common-page-features-geometrixx-mobile-app}

Jede Seite der Mobile App umfasst die folgenden Funktionen:

* Eine Schaltfläche „Zurück“ zum Zurückkehren zur übergeordneten Seite. Die Schaltfläche Zurück wird nicht auf der Startseite angezeigt.
* Eine überflüssige Leiste mit einer Liste von Befehlen und Links:

   * Öffnen Sie die Seite Standorte .
   * Öffnen Sie den Warenkorb.
   * Anmelden.
   * Aktualisieren Sie die Anwendung.

* Das Absatzsystem zum Hinzufügen von Komponenten und Erstellen von Inhalten.

### Die Startseite - Geometrixx Mobile App {#the-home-page-geometrixx-mobile-app}

Der Inhalt der Startseite besteht aus den folgenden Navigations-Tools:

* Eine Menülistenkomponente, die Links zu den untergeordneten Seiten von Gear, Reviews, News und About Us bereitstellt.
* Eine Karussellkomponente zum Wischen, die die untergeordneten Seiten anzeigt.

### Die Zahnradseite - Geometrixx Mobile App {#the-gear-page-geometrixx-mobile-app}

Die Zahnradseite bietet Benutzenden Zugriff auf Produktseiten. Eine Menülistenkomponente bietet Zugriff auf die untergeordneten Seiten der Zahnradseite. Die untergeordneten Seiten sind Produktkategorien, die von der Website unterstützt werden.

* Staffel
* Bekleidung
* Geschlecht
* Aktivität

Jede Kategorieseite verwendet dieselbe Inhaltsstruktur wie die Zahnradseite. Das Karussell bietet Zugriff auf untergeordnete Seiten, die Unterkategorien von Produkten sind. Die Unterkategorieseiten enthalten Produktlisten mit Links zu Produktseiten.

### Die Produktseite - Geometrixx Mobile App {#the-products-page-geometrixx-mobile-app}

Die Produktseite und ihre Hierarchie untergeordneter Seiten implementieren ein Klassifizierungssystem für Produktseiten. Die untersten Seiten in jeder Verzweigung der Hierarchie sind Produktseiten, die eine beliebige Produktkomponente enthalten.

Die Seite Produkte ist für Programmbenutzer nicht verfügbar. Die Zahnradseite bietet Zugriff auf jede Produktseite.

### Die Überprüfungsseite - Geometrixx Mobile App {#the-reviews-page-geometrixx-mobile-app}

Enthält eine Schaltfläche Zurück . Mit dem Absatzsystem können Sie Komponenten hinzufügen.

Wenn Sie das Programm verwenden, ist die Seite „Überprüfungen“ über das Karussell auf der englischen Seite verfügbar.

### Die News-Seite - Geometrixx Mobile App {#the-news-page-geometrixx-mobile-app}

Enthält eine Schaltfläche Zurück . Mit dem Absatzsystem können Sie Komponenten hinzufügen.

Wenn Sie die Anwendung verwenden, ist die Seite Nachrichten über das Karussell auf der englischen Seite verfügbar.

### Die Seite „Über uns“ - Geometrixx Mobile App {#the-about-us-page-geometrixx-mobile-app}

Die Seite „Über uns“ enthält mehrere Komponenten mit zwei Spaltenzeilen. Jede Spalte enthält entweder eine Bild- oder eine Textkomponente. Die Komponenten können bearbeitet werden, und mit dem Absatzsystem können Sie Komponenten hinzufügen.

Wenn Sie das Programm verwenden, ist die Seite „Über uns“ über das Karussell auf der englischen Seite verfügbar.

### Die Seite „Standorte“ - Geometrixx Mobile App {#the-locations-page-geometrixx-mobile-app}

Die Seite Standorte enthält eine Standort -Komponente.

Wenn Sie die Anwendung verwenden, ist die Seite Standorte über die Menüliste auf der englischen Seite verfügbar.

## Beispiele für Mobile-Komponenten {#sample-mobile-components}

Beim Bearbeiten von Seiten einer Mobile App sind mehrere Komponenten sofort im Sidekick verfügbar. Die Komponenten gehören zur Komponentengruppe PhoneGap.

### Karussell-Galerie {#swipe-carousel}

Die Komponente Karussell wischen ist ein Tool zum Anzeigen von und Navigieren auf Seiten einer Site. Die Komponente enthält ein Karussell, das Bilder für die Seiten durchsucht, die sich über einer Liste von Seitenlinks befinden. Bearbeiten Sie die Komponente, um die Seiten und das Verhalten des Karussells anzugeben.

Beachten Sie, dass Bilder im Karussell für Seiten angezeigt werden, die mit einem Bild auf eine bestimmte Weise verknüpft sind. Wenn Seiten nicht mit Bildern verknüpft sind, wird nur die Liste der Links angezeigt.

![chlimage_1-151](assets/chlimage_1-151.png)

**Registerkarte „Karusselleigenschaften“**

Konfigurieren Sie das Verhalten des Karussells:

* Abspielgeschwindigkeit : Die Zeit in Millisekunden, während der jedes Bild angezeigt wird, bevor das nächste Bild angezeigt wird.
* Übergangszeit: Die Dauer in Millisekunden der Animation für Bildübergänge.
* Stil der Steuerelemente: Der Typ der Steuerelemente, die für das Wechseln zwischen Bildern bereitgestellt werden.

**Registerkarte „Listeneigenschaften“**

Geben Sie an, wie die Seitenliste generiert wird:

* Liste erstellen mit: Die Methode, die zum Angeben der im Karussell einzuschließenden Seiten verwendet wird. Siehe Erstellen der Seitenliste.
* Sortieren nach: Wählen Sie eine Seiteneigenschaft aus, die zum Sortieren der Seitenliste verwendet werden soll. Wählen Sie beispielsweise jcr:title aus, um Seiten alphabetisch nach Titel zu sortieren.
* Limit: Die maximale Anzahl der einzuschließenden Seiten. Diese Eigenschaft ist für suchbasierte Methoden zum Erstellen der Seitenliste geeignet.

#### Erstellen der Seitenliste {#building-the-page-list}

Die Komponente Karussell wischen stellt die folgenden Werte für die Eigenschaft Liste mithilfe von erstellen bereit. Das Dialogfeld „Bearbeiten“ ändert sich entsprechend dem ausgewählten Wert:

**Untergeordnete Seiten**

Die Komponente listet alle untergeordneten Seiten einer bestimmten Seite auf. Nachdem Sie diesen Wert ausgewählt haben, wählen Sie die Seite auf der Registerkarte Untergeordnete Seiten aus, oder geben Sie keinen Wert an, um die untergeordneten Elemente der aktuellen Seite aufzulisten.

**Liste fester**

Geben Sie eine Liste mit eingeschlossenen Seiten an. Nachdem Sie diesen Wert ausgewählt haben, konfigurieren Sie die Liste auf der Registerkarte Feste Liste , die angezeigt wird, wenn Sie Feste Liste auswählen:

* Um eine Seite hinzuzufügen, klicken Sie auf Element hinzufügen und suchen Sie nach der Seite.
* Verschieben Sie die Seite innerhalb der Liste mithilfe der Pfeilsymbole nach oben und unten.
* Klicken Sie auf die Schaltfläche Entfernen , um eine Seite aus der Liste zu entfernen.

Die Order By -Eigenschaft hat keinen Einfluss auf die Reihenfolge fester Listen.

**Suchen**

Füllen Sie die Liste mithilfe der Ergebnisse einer Keyword-Suche. Die Suche wird in den untergeordneten Elementen einer von Ihnen angegebenen Seite durchgeführt:

1. Um die Stammseite der Suche anzugeben, wählen Sie mit der Start In -Eigenschaft den Seitenpfad aus. Geben Sie unter der aktuellen Seite keinen zu suchenden Pfad an.
1. Geben Sie in der Eigenschaft Suchanfrage die Suchbegriffe ein.

**Erweiterte Suche**

Füllen Sie die Liste mithilfe einer [QueryBuilder](/help/sites-developing/querybuilder-api.md)-Abfrage.

### Bild {#image}

Fügen Sie ein Bild zu Ihrem Anwendungsinhalt hinzu.

### Text {#text}

Fügen Sie Rich-Text zu Ihren Anwendungsinhalten hinzu.

### Filialen {#store-locations}

Die Komponente „Store-Standorte“ bietet Benutzenden Tools zum Suchen von Geschäftsstellen:

* Suchen
* Listen von Orten, die sich in der Nähe oder in der Entfernung zu den GPS-Koordinaten des Geräts befinden.

Für die Komponente muss das Repository Standortinformationen für jeden Speicher enthalten. Beispielspeicherorte werden im Knoten /etc/commerce/places/adobe installiert. ![chlimage_1-152](assets/chlimage_1-152.png)

### Zeile mit zwei Spalten {#two-column-row}

Ermöglicht das Hinzufügen von nebeneinander angezeigten Komponenten zu einer Seite.

![chlimage_1-153](assets/chlimage_1-153.png)
