---
title: ClientContext
description: Erfahren Sie, wie Sie mit ClientContext Informationen zur aktuellen Seite und zum Besucher in Adobe Experience Manager anzeigen können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 69c66c82-fbd6-406e-aefd-b85480a62109
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '1961'
ht-degree: 37%

---


# ClientContext{#client-context}

>[!NOTE]
>
>ClientContext wurde durch ContextHub abgelöst. Weitere Informationen finden Sie in der zugehörigen [Konfiguration](/help/sites-developing/ch-configuring.md) und [Entwickler](/help/sites-developing/contexthub.md) Dokumentation.

ClientContext ist ein Mechanismus, der Ihnen bestimmte Informationen zur aktuellen Seite und zum aktuellen Besucher liefert. Um ClientContext zu öffnen, drücken Sie die Tastenkombination **Strg+Alt+C** (Windows) oder **Ctrl+Wahl+C** (Mac):

![Beispiel für das ClientContext-Fenster](assets/clientcontext_alisonparker.png)

Sowohl in der Veröffentlichungs- als auch in der Autorenumgebung werden Informationen zu folgenden Themen angezeigt:

* Der Besucher; abhängig von Ihrer Instanz werden bestimmte Informationen angefordert oder abgeleitet.
* Seiten-Tags und die Häufigkeit, mit der der aktuelle Besucher auf diese Tags zugegriffen hat (wird angezeigt, wenn Sie den Mauszeiger über ein bestimmtes Tag bewegen) .
* Seiteninformationen.
* Informationen zur technischen Umgebung, wie IP-Adresse, Browser und Bildschirmauflösung.
* Alle Segmente, die derzeit aufgelöst sind.

Mit den Symbolen (nur in der Autorenumgebung verfügbar) können Sie die Details des ClientContext konfigurieren:

![Die Symbole Bearbeiten, Laden und Zurücksetzen des Fensters ClientContext](do-not-localize/clientcontext_icons.png)

* **Bearbeiten**
Eine neue Seite wird geöffnet, auf der Sie [Bearbeiten, Hinzufügen oder Entfernen einer Profileigenschaft](#editingprofiledetails).

* **Laden**
Sie können [aus einer Liste von Profilen auswählen und das Profil laden](#loading-a-new-user-profile), das getestet werden soll.

* **Zurücksetzen**
Sie können [das Profil auf den aktuellen Benutzer zurücksetzen](#resetting-the-profile-to-the-current-user).

## Verfügbare ClientContext-Komponenten {#available-client-context-components}

ClientContext kann die folgenden Eigenschaften anzeigen ([je nachdem, was mit Bearbeiten ausgewählt wurde](#adding-a-property-component)):

**Surfer-Informationen**: Zeigt die folgenden Client-seitigen Informationen an:

* die **IP-Adresse**
* **Schlüsselwörter** als Suchmaschinenreferenz
* die verwendeten **Browser**
* das verwendete **Betriebssystem**
* die **Auflösung** des Bildschirms
* die **X**-Position der Maus
* die **Y**-Position der Maus

**Aktivitäts-Stream** Hier erhalten Sie Informationen zur sozialen Aktivität des Benutzers auf verschiedenen Plattformen, z. B. den AEM, Blogs, Bewertungen usw.

**Kampagne**: Ermöglicht es Autoren, ein bestimmtes Erlebnis für eine Kampagne zu simulieren. Diese Komponente setzt die normale Kampagnenauflösung und Erlebnisauswahl außer Kraft, um verschiedene Permutationen testen zu können.

Die Kampagnenauflösung basiert normalerweise auf der Prioritätseigenschaft der Kampagne. Das Erlebnis wird im Regelfall auf Grundlage der Segmentierung ausgewählt.

**Warenkorb** Zeigt Informationen zum Warenkorb an, einschließlich Produkteinträgen (Titel, Menge, PreisFormatiert usw.), aufgelösten Promotions (Titel, Nachricht usw.) und Gutscheinen (Code, Beschreibung usw.).

Der Sitzungsspeicher des Warenkorbs benachrichtigt den Server auch über aufgelöste Promotion-Änderungen (basierend auf Segmentierungsänderungen) mit dem ClientContextCartServlet.

**Generischer Store**: Eine generische Komponente, die den Inhalt eines Stores angezeigt. Es handelt sich um eine Version der Komponente &quot;Generische Store-Eigenschaften&quot;.

Der generische Store muss mit einem JS-Renderer konfiguriert werden, der die Daten auf benutzerdefinierte Weise anzeigt.

**Generische Store-Eigenschaften**: Eine generische Komponente, die den Inhalt eines Stores angezeigt. Es handelt sich um eine übergeordnete Version der Komponente &quot;Generischer Store&quot;.

Die Komponente &quot;Generische Store-Eigenschaften&quot;enthält einen standardmäßigen Renderer, der die konfigurierten Eigenschaften auflistet (zusammen mit einer Miniaturansicht).

**Geolocation**: Zeigt den Breiten- und Längengrad des Kundenstandorts an. Über die HTML5-Geolocation-API wird der aktuelle Standort vom Browser abgefragt. Dabei wird eine Popup-Meldung angezeigt, über die der Besucher gebeten wird, seine Standortdaten freizugeben.

Bei der Anzeige in der Context Cloud verwendet die Komponente eine Google-API, um eine Zuordnung als Miniaturansicht anzuzeigen. Die Komponente unterliegt der Google-API [Nutzungsbeschränkungen](https://developers.google.com/maps/documentation/staticmaps/intro#Limits).

>[!NOTE]
>
>In AEM 6.1 bietet der Geolocation-Store nicht mehr die Funktion zur umgekehrten Geocodierung. Daher ruft der Geolocation-Store keine Details mehr zum aktuellen Speicherort ab, z. B. den Stadt- oder Ländercode. Segmente, die diese Store-Daten verwenden, funktionieren nicht ordnungsgemäß. Der Geolocation-Store enthält nur den Längen- und Breitengrad eines Standorts.

**JSONP-Store**: Eine Komponente, die Inhalt anzeigt, der abhängig von Ihrer Installation ist.

Der JSON-Standard ist eine JSON-Ergänzung, mit der dieselbe ursprüngliche Richtlinie umgangen werden kann (sodass eine Web-Anwendung mit Servern in einer anderen Domain kommunizieren kann). Er besteht darin, das JSON-Objekt in einen Funktionsaufruf zu verpacken, damit es als `<script>` von der anderen Domäne aus (was eine zulässige Ausnahme von derselben Ursprungsrichtlinie ist).

Der JSONP-Store ist zwar wie jeder andere Store, er lädt allerdings Informationen aus einer anderen Domain, ohne dass für diese Informationen ein Proxy in der aktuellen Domain benötigt wird. Siehe hierzu das Beispiel unter [Speichern von Daten in ClientContext über JSON](/help/sites-administering/client-context.md#storing-data-in-client-context-via-jsonp).

>[!NOTE]
>
>Der JSONP-Store speichert die Informationen nicht im Cookie zwischen, ruft aber die Daten bei jedem Seitenladevorgang ab.

**Profildaten**: Zeigt im Benutzerprofil erfasste Informationen an, Zum Beispiel Geschlecht, Alter, E-Mail-Adresse usw.

**Aufgelöste Segmente**: Gibt an, welche Segmente aktuell aufgelöst werden (häufig von anderen in ClientContext angezeigten Informationen abhängig). Dies ist beim Konfigurieren von Kampagnen von Interesse.

Beispiel: die Frage, ob sich die Maus aktuell im linken oder rechten Fensterbereich befindet. Dieses Segment dient in erster Linie für Tests, da Änderungen sofort zu sehen sind.

**Soziales Diagramm**: Zeigt das soziale Diagramm von Freunden und Followern des Benutzers an.

>[!NOTE]
>
>Derzeit ist dies eine Demofunktion, die auf vorkonfigurierten Datensätzen in den Profilknoten unserer Demonstrationsbenutzer angewiesen ist. Ein Beispiel finden Sie unter:
>
>`/home/users/geometrixx/aparker@geometrixx.info/profile` => Eigenschaft „Freunde“

**Tag-Cloud**: Zeigt die auf der aktuellen Seite gesetzten und beim Navigieren auf der Site gesammelten Tags an. Wenn Sie mit der Maus auf ein Tag zeigen, sehen Sie, wie oft der aktuelle Benutzer auf Seiten mit diesem bestimmten Tag zugegriffen hat.

>[!NOTE]
>
Auf DAM-Assets gesetzte Tags, die auf besuchten Seiten angezeigt werden, werden nicht gezählt.

**Technografie-Store**: Diese Komponente hängt von Ihrer Installation ab.

**ViewedProducts**: Verfolgt die vom Einkäufer angesehenen Produkte. Kann für das zuletzt angezeigte Produkt oder das zuletzt angezeigte Produkt abgerufen werden, das noch nicht im Warenkorb ist.

Dieser Sitzungsspeicher verfügt über keine standardmäßige ClientContext-Komponente.

Weitere Informationen finden Sie unter [ClientContext im Detail](/help/sites-developing/client-context.md).

>[!NOTE]
>
Die Seitendaten sind keine Standardkomponenten in ClientContext mehr. Sie können sie ggf. hinzufügen, indem Sie ClientContext bearbeiten, die Komponente **Generische Store-Eigenschaften** hinzufügen und dann eine entsprechende Konfiguration durchführen, um den **Store** als `pagedata` zu definieren.

## Ändern des ClientContext-Profils {#changing-the-client-context-profile}

Mit ClientContext können Sie Details interaktiv ändern:

* Wenn Sie das in ClientContext verwendete Profil ändern, können Sie die unterschiedlichen Erlebnisse sehen, die den verschiedenen Benutzern für die aktuelle Seite angezeigt werden.
* Abgesehen vom Ändern des Benutzerprofils können Sie auch bestimmte Profildetails ändern, um nachzuvollziehen, wie sich das Seitenerlebnis unter verschiedenen Bedingungen verändert.

### Laden neuer Benutzerprofile {#loading-a-new-user-profile}

Sie können das Profil wie folgt ändern:

* [über das Ladesymbol oder](#loading-a-new-visitor-profile-with-the-load-profile-icon)
* [über den Auswahlregler.](#loadinganewvisitorprofilewiththeselectionslider)

Wenn Sie fertig sind, können Sie [Profil zurücksetzen](#resetting-the-profile-to-the-current-user).

#### Laden eines neuen Besucherprofils mit dem Symbol Profil laden {#loading-a-new-visitor-profile-with-the-load-profile-icon}

1. Klicken Sie auf das Symbol „Profil laden“:

   ![Das Symbol Profil laden in ClientContext](do-not-localize/clientcontext_loadprofile.png)

1. Dadurch wird das Dialogfeld geöffnet. Hier können Sie das zu ladende Profil auswählen:

   ![Das Dialogfeld Profillader mit der Dropdown-Liste zur Auswahl eines Profils](assets/clientcontext_profileloader.png)

1. Klicken Sie auf **OK**, um das Profil zu laden.

#### Laden neuer Benutzerprofile mit dem Auswahlregler {#loading-a-new-user-profile-with-the-selection-slider}

Sie können ein Profil auch mit dem Auswahlregler auswählen:

1. Doppelklicken Sie auf das Symbol für den aktuellen Benutzer. Der Selektor wird geöffnet. Navigieren Sie mit den Pfeilen und sehen Sie sich die verfügbaren Profile an:

   ![Der Benutzerselektor](assets/clientcontext_profileselector.png)

1. Klicken Sie auf das zu ladende Profil. Wenn die Details geladen wurden, klicken Sie auf eine Stelle außerhalb der Auswahl, um diese zu schließen.

#### Zurücksetzen des Profils auf den aktuellen Benutzer {#resetting-the-profile-to-the-current-user}

1. Setzen Sie das Profil in ClientContext mit dem Symbol „Zurücksetzen“ auf den aktuellen Benutzer zurück:

   ![Das Symbol &quot;Zurücksetzen&quot;](do-not-localize/clientcontext_resetprofile.png)

### Ändern der Browser-Plattform {#changing-the-browser-platform}

1. Doppelklicken Sie auf das Symbol, das die Browser-Plattform darstellt. Der Selektor wird geöffnet. Navigieren Sie mit den Pfeilen zu den verfügbaren Plattformen/Browsern und sehen Sie sie an:

   ![Browser-Plattformauswahl](assets/clientcontext_browserplatform.png)

1. Klicken Sie auf den Browser der Plattform, den Sie laden möchten. Wenn die Details geladen wurden, klicken Sie auf eine Stelle außerhalb der Auswahl, um diese zu schließen.

### Geolocation ändern {#changing-the-geolocation}

1. Doppelklicken Sie auf das Geolocation-Symbol. Eine erweiterte Zuordnung wird geöffnet. Hier können Sie die Markierung an eine neue Position ziehen:

   ![Geolocation-Detail](assets/clientcontext_geomocationrelocate.png)

1. Klicken Sie außerhalb der Karte, um zu schließen.

### Ändern der Tag-Auswahl {#changing-the-tag-selection}

1. Doppelklicken Sie auf den Abschnitt Tag Cloud des ClientContext. Das Dialogfeld wird geöffnet. Hier können Sie Tags auswählen:

   ![Tag-Cloud-Dialogfeld](assets/clientcontext_tagselection.png)

1. Klicken Sie auf OK , um in ClientContext zu laden.

## Bearbeiten des ClientContext {#editing-the-client-context}

Die Bearbeitung eines Client-Kontexts kann verwendet werden, um die Werte bestimmter Eigenschaften festzulegen (oder zurückzusetzen), eine neue Eigenschaft hinzuzufügen oder eine Eigenschaft zu entfernen, die nicht mehr benötigt wird.

### Bearbeiten von Eigenschaftendetails {#editing-property-details}

Mittels ClientContext-Bearbeitung können die Werte bestimmter Eigenschaften festgelegt (zurückgesetzt) werden. Damit können Sie bestimmte Szenarien testen (besonders nützlich für [Segmentierung](/help/sites-administering/campaign-segmentation.md) und [Kampagnen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md)).

![Bearbeiten des ClientContext](assets/clientcontext_alisonparker_edit.png)

### Hinzufügen von Eigenschaftskomponenten {#adding-a-property-component}

Nachdem Sie die **ClientContext-Designseite** können Sie auch **Hinzufügen** eine vollständig neue Eigenschaft mit den verfügbaren Komponenten (die Komponenten werden sowohl im Sidekick als auch aus dem **Neue Komponente einfügen** Dialogfeld, das nach einem Doppelklick auf die **Komponenten oder Assets hierher ziehen** -Feld):

![Hinzufügen einer Eigenschaft zum ClientContext-Fenster](assets/clientcontext_alisonparker_new.png)

### Entfernen einer Eigenschaftskomponente {#removing-a-property-component}

Nachdem Sie die **ClientContext-Designseite** können Sie auch **Entfernen** eine Eigenschaft, wenn sie nicht mehr benötigt wird. Dies umfasst standardmäßig bereitgestellte Eigenschaften. **Zurücksetzen** reaktiviert diese, wenn sie entfernt wurden.

## Speichern von Daten in ClientContext über JSONP {#storing-data-in-client-context-via-jsonp}

In diesem Beispiel erfahren Sie, wie Sie mit der Kontextspeicherkomponente &quot;JSONP-Store&quot;externe Daten zu ClientContext hinzufügen. Erstellen Sie dann ein Segment basierend auf den Informationen aus diesen Daten. Das Beispiel verwendet den JSONP-Dienst, den WIPmania.com bereitstellt. Der Dienst gibt Geolocation-Informationen basierend auf der IP-Adresse des Webclients zurück.

In diesem Beispiel wird die Beispiel-Website der Geometrixx Outdoors verwendet, um auf ClientContext zuzugreifen und das erstellte Segment zu testen. Sie können eine andere Website verwenden, solange die Seite ClientContext aktiviert hat. (Siehe [Hinzufügen von ClientContext zu einer Seite](/help/sites-developing/client-context.md#adding-client-context-to-a-page).

### Hinzufügen der JSONP-Store-Komponente {#add-the-jsonp-store-component}

Fügen Sie die JSONP Store-Komponente zu ClientContext hinzu und verwenden Sie sie zum Abrufen und Speichern von Geolocation-Informationen zum Webclient.

1. Öffnen Sie die englische Homepage der Geometrixx Outdoors-Site in der AEM-Autoreninstanz. ([https://localhost:4502/content/geometrixx-outdoors/en.html](https://localhost:4502/content/geometrixx-outdoors/en.html)).
1. Drücken Sie zum Öffnen von ClientContext die Tastenkombination Strg+Alt+C (Windows) oder Ctrl+Wahl+C (Mac).
1. Klicken Sie auf das Bearbeitungssymbol oben in Client Context, um Client Context-Designer zu öffnen.

   ![Link-Symbol](do-not-localize/chlimage_1.png)

1. Ziehen Sie die JSONP Store-Komponente in ClientContext.

   ![Ziehen und Ablegen der JSONP Store-Komponente in ClientContext](assets/chlimage_1-4.jpeg)

1. Doppelklicken Sie auf die Komponente, um das Dialogfeld &quot;Bearbeiten&quot;zu öffnen.
1. Geben Sie in das Feld „JSONP-Service-URL“ die folgende URL ein und klicken Sie dann auf „Store abrufen“:

   `https://api.wipmania.com/jsonp?callback=${callback}`

   Die Komponente ruft den JSONP-Dienst auf und listet alle Eigenschaften auf, die die zurückgegebenen Daten enthalten. Die Eigenschaften in der Liste sind diejenigen, die in ClientContext verfügbar sein werden.

   ![Die Eigenschaften des JSONP-Dienstes](assets/chlimage_1-40.png)

1. Klicken Sie auf OK.
1. Kehren Sie zur Homepage der Geometrixx Outdoors zurück und aktualisieren Sie die Seite. ClientContext enthält jetzt die Informationen aus der JSONP Store-Komponente.

   ![Beispiel einer mit Daten gefüllten JSONP-Komponente](assets/chlimage_1-41.png)

### Segment erstellen {#create-the-segment}

Verwenden Sie die Daten aus dem Sitzungsspeicher, den Sie mit der JSONP-Store-Komponente erstellt haben. Das Segment verwendet den Breitengrad aus dem Sitzungsspeicher und das aktuelle Datum, um zu bestimmen, ob es sich um Winterzeit am Standort des Kunden handelt.

1. Öffnen Sie die Tools-Konsole in Ihrem Webbrowser (`https://localhost:4502/miscadmin#/etc`).
1. Klicken Sie in der Ordnerstruktur auf den Ordner Tools/Segmentierung und klicken Sie dann auf Neu > Neuer Ordner. Geben Sie die folgenden Eigenschaftswerte an und klicken Sie dann auf Erstellen:

   * Name: mysegments
   * Titel: Meine Segmente

1. Wählen Sie den Ordner Meine Segmente aus und klicken Sie auf Neu > Neue Seite:

   1. Geben Sie für den Titel &quot;Winter&quot;ein.
   1. Wählen Sie die Vorlage Segment aus.
   1. Klicken Sie auf „Erstellen“.

1. Klicken Sie mit der rechten Maustaste auf das Segment Winter und klicken Sie auf Öffnen .
1. Ziehen Sie die generische Store-Eigenschaft in den standardmäßigen UND-Container.

   ![Hinzufügen einer Komponente zum Segment-Editor](assets/chlimage_1-5.jpeg)

1. Doppelklicken Sie auf die Komponente, um das Dialogfeld &quot;Bearbeiten&quot;zu öffnen, geben Sie die folgenden Eigenschaftswerte an und klicken Sie dann auf &quot;OK&quot;:

   * Store: wipmania
   * Eigenschaftsname: latitude
   * Operator: größer als
   * Eigenschaftswert: 30

1. Ziehen Sie die Skriptkomponente in denselben UND-Container und öffnen Sie das Bearbeitungsdialogfeld. Fügen Sie das folgende Skript hinzu und klicken Sie dann auf OK :

   `3 < new Date().getMonth() < 12`
