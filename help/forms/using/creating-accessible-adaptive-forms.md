---
title: Zugreifbare adaptive Formulare erstellen
seo-title: Zugreifbare adaptive Formulare erstellen
description: AEM Forms bietet Werkzeuge zum Erstellen barrierefreier adaptiver Formulare und vereinfacht die Einhaltung von Barrierefreiheitsstandards.
seo-description: AEM Forms bietet Werkzeuge zum Erstellen barrierefreier adaptiver Formulare und vereinfacht die Einhaltung von Barrierefreiheitsstandards.
uuid: 6472bc2d-47ca-4883-88b7-5de0b758fd00
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 1e95c66b-d132-4c44-a1dc-31fd09af8113
docset: aem65
feature: Adaptive Formulare
exl-id: e755159f-374f-42b8-b28b-e8864df44f9d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 37%

---

# Zugreifbare adaptive Formulare erstellen{#creating-accessible-adaptive-forms}

## Einführung {#introduction}

Ein barrierefreies Formular ist ein Formular, das jeder verwenden kann, einschließlich Benutzer mit Behinderungen. Adaptive Forms umfasst eine Reihe von Funktionen, die die Benutzerfreundlichkeit für Benutzer mit unterschiedlichen Fähigkeiten verbessern. Die Integration von Barrierefreiheit in adaptive Formulare ermöglicht nicht nur die größte potenzielle Zielgruppe für den Inhalt, sie ist auch eine Anforderung beim Bereitstellen von Dokumenten in Regionen, in denen die Einhaltung von Barrierefreiheitsstandards obligatorisch ist. Mit AEM Forms können Formularentwickler die Barrierefreiheitsstandards einhalten.

Beim Verfassen eines adaptiven Formulars muss der Autor die folgenden Punkte berücksichtigen, um barrierefreie adaptive Formulare zu erstellen:

* Überprüfen Sie das Formular mit dem Test-Tool für barrierefreie Namen und Beschreibungsinspektoren (ANDI).
* Angabe von angemessenen Beschriftungen für Formularsteuerelemente
* Angabe von Textäquivalenten für Bilder
* Bereitstellung von ausreichendem Farbkontrast
* Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können

## Voraussetzung

Sie benötigen ein Barrierefreiheitswerkzeug wie **Accessible Name and Description Inspector (ANDI)** und ein **Adaptives Formulardesign, das zur Behebung von Problemen mit Barrierefreiheit** entwickelt wurde, um ein barrierefreies adaptives Formular zu erstellen.

### Tool zum Testen der Barrierefreiheit herunterladen und installieren

Das Tool &quot;Accessible Name and Description Inspector (ANDI)&quot;hilft Ihnen bei der Identifizierung und Behebung von Problemen mit der Barrierefreiheit in Webinhalten. Es ist das empfohlene Tool nach den Richtlinien des Ministeriums für Innere Sicherheit von Trusted Tester v5. Es wird von der Abteilung Social Security Administration &#x200B; USA entwickelt, um die Einhaltung von Abschnitt 508 des Webinhalts zu überprüfen. Das Tool:

* Hilft bei der Erkennung von Zugänglichkeitsproblemen &#x200B; einer Webseite
* Bietet Vorschläge zur Verbesserung der Barrierefreiheit &#x200B;
* Ermittelt Probleme mit der Barrierefreiheit der Tastatur und dem Farbkontrast
* Gibt den Inhalt der Bildschirmlesehilfe eindeutig gemäß den Standards an

ANDI arbeitet mit allen gängigen Internet-Browsern. Detaillierte Anweisungen zum Konfigurieren und Verwenden des Tools finden Sie in der [ANDI-Dokumentation](https://www.ssa.gov/accessibility/andi/help/install.html) .

### Laden Sie das Thema Ultramarine-Accessible herunter und installieren Sie es.

Das Thema Ultramarine-Accessible ist ein Referenzthema. Sie hilft zu demonstrieren, wie Sie Farbkontrast und andere Probleme mit Barrierefreiheit in einem adaptiven Formular beheben können. Adobe empfiehlt, ein benutzerdefiniertes Design für die Produktionsumgebung basierend auf den von Ihrem Unternehmen genehmigten Stilen zu erstellen. Führen Sie die folgenden Schritte aus, um das Design in Ihre AEM-Instanz hochzuladen:

1. Laden Sie das Designpaket herunter.
1. Navigieren Sie zu **[!UICONTROL Experience Manager]** > **[!UICONTROL Navigation]** ![Navigation](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Forms]** in Ihrer AEM Instanz.
1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**. Wählen Sie die Datei &quot;x Ultramarine-Accessible-Theme.zip&quot;aus und laden Sie sie hoch. Das Design wird in Ihre AEM-Instanz hochgeladen.

## Barrierefreies Gestalten eines adaptiven Formulars

Sie sollten sich auf vier Schlüsselaspekte konzentrieren: Tastaturnavigation, Farbkontrast, aussagekräftiger Alternativtext für Bilder und geeignete Beschriftungen für Formularsteuerelemente, um ein adaptives Formular barrierefrei zu machen. Führen Sie die folgenden Schritte aus, um die vorhandenen adaptiven Formulare barrierefrei zu machen:

### 1. Wenden Sie ein barrierefreies Design an und führen Sie zusätzliche Korrekturen durch

Wenden Sie das Thema Ultramarine-Accessible auf Ihr vorhandenes adaptives Formular an. So wenden Sie das Design an:

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten.
1. Wählen Sie eine Komponente aus und tippen Sie auf das übergeordnete Symbol. Tippen Sie im Kontextmenü auf **[!UICONTROL Container für adaptive Formulare]** und tippen Sie dann auf das Konfigurationssymbol.
1. Wählen Sie im Eigenschaftenbrowser das Thema Ultramarine-Accessible aus und tippen Sie auf das Symbol **[!UICONTROL Speichern]**.
1. Aktualisieren Sie das Browser-Fenster. Das Design wird auf das adaptive Formular angewendet.

Nachdem Sie ein barrierefreies Design angewendet haben, führen Sie die folgenden zusätzlichen Korrekturen durch. Die Fehlerbehebungen sind zusätzlich zu den Fehlerbehebungen verfügbar, die im barrierefreien Design behandelt werden:

1. Fügen Sie im adaptiven Formular einen aussagekräftigen alternativen Text für das Logo-Bild hinzu.

   Geben Sie einen aussagekräftigen alternativen Text für Bilder in den Kopf- und Fußzeilenkomponenten der adaptiven Formularvorlage an. Wenn Sie die Vorlage korrigieren und sie zum Erstellen eines adaptiven Formulars verwenden, übernehmen die adaptiven Formulare alle auf die Barrierefreiheit bezogenen Fehlerbehebungen, die auf die Kopf- und Fußzeile der Vorlage angewendet werden.  Nehmen Sie für ein vorhandenes adaptives Formular Änderungen auf der Ebene des adaptiven Formulars vor. Änderungen an einer adaptiven Formularvorlage fließen nicht automatisch in ein vorhandenes adaptives Formular.

1. Fügen Sie dem adaptiven Formular eine Überschriftenkomponente hinzu, die den Formularnamen enthält. Wenn Ihr Formularentwurf einen Unternehmensnamen angibt, fügen Sie auch eine separate Überschriftenkomponente für den Unternehmensnamen hinzu.

   Die meisten Barrierefreiheitstools informieren Benutzer über die Hierarchie des Inhalts, damit sie die Struktur der Webseite besser verstehen können. Legen Sie unterschiedliche Überschriftenebenen für den Organisationsnamen und den Formularnamentext im adaptiven Formular fest, um eine hierarchische Struktur für diesen Text bereitzustellen. Verwenden Sie außerdem eine Textkomponente vor jedem Bedienfeld und Abschnitt mit einer entsprechenden Überschriftenebene, um eine Hierarchie zu erstellen.

   ![Anwenden eines Header-Stils](assets/apply-style.gif)

1. Ändern Sie die Hintergrundfarbe der Fußzeile, sodass entsprechend den Barrierefreiheitsstandards ein angemessener Kontrast verwendet wird, um die Sichtbarkeit und Lesbarkeit des Textes zu verbessern. Sie können ANDI verwenden, um Farbkontrastprobleme in Ihrem Formular zu finden. Verwenden Sie auch keine sehr kleine Schrift. Kleine Schriftarten sind schwer zu lesen.

1. Ersetzen Sie die Switch- und Bildauswahlkomponenten in Ihrem vorhandenen adaptiven Formular durch die Auswahlkomponente (Optionsfeld).

1. Ersetzen Sie die Komponente &quot;Numerische Schritte&quot;im vorhandenen adaptiven Formular durch die Komponente &quot;Numerisches Feld&quot;.

1. Ersetzen Sie das Datumseingabefeld durch das Datumsauswahlfeld.

1. Legen Sie Anzeige-, Validierungs- und Bearbeitungsmuster für die Datumsauswahlkomponente fest. Legen Sie außerdem eine benutzerdefinierte Validierungsfehlermeldung fest. Sie haben beispielsweise ein ungültiges Datum angegeben. Das korrekte Format des Datums ist JJJ-MM-TT.

1. Legen Sie benutzerdefinierten Barrierefreiheitstext für die Datumsauswahlkomponente fest. Geben Sie beispielsweise Ihr Geburtsdatum ein. Sprachausgaben lesen diese benutzerdefinierten Barrierefreiheitstexte.

1. Verwenden Sie für adaptive Formularkomponenten eine kurze Beschreibung anstelle einer langen Beschreibung. Eine lange Beschreibung fügt die Schaltfläche &quot;Hilfe&quot;hinzu. Stellen Sie sicher, dass das adaptive Formular über keine Hilfesymbolleiste verfügt.

1. Fügen Sie allen schreibgeschützten Zellen von Tabellen benutzerdefinierten Barrierefreiheitstext hinzu. Deaktivieren Sie außerdem alle schreibgeschützten Zellen von Tabellen.

1. Entfernen Sie Scribble-Signaturfelder, falls im adaptiven Formular vorhanden. Konfigurieren Sie das adaptive Formular für die Verwendung von Adobe Sign für ein nahtloses digitales Signieren.

### 2. Stellen Sie geeignete Beschriftungen für Formularsteuerelemente bereit {#provide-proper-labels-for-form-controls}

Die Beschriftung oder der Titel einer Komponente gibt an, was die Formularkomponente darstellt. Beispiel: Der Text „Vorname“ weist darauf hin, dass der Benutzer seinen Vornamen in ein Textfeld eingeben muss. Damit die Beschriftung von Bildschirmlesegeräten erkannt werden kann, wird sie programmgesteuert mit einer Formularkomponente verknüpft. Alternativ dazu kann das Formularsteuerelement mit zusätzlichen Barrierefreiheitsinformationen konfiguriert werden.

Die Beschriftung, die von Bildschirmlesegeräten erkannt wird, muss nicht unbedingt mit der visuellen Beschriftung identisch sein. In einigen Fällen möchten Sie den Zweck des Steuerelements möglicherweise genauer angeben. Für jedes Feldobjekt in einem Formular können die Barrierefreiheitsoptionen verwendet werden, um anzugeben, wie das Bildschirmlesegerät das entsprechende Formularfeld identifiziert.

Gehen Sie wie folgt vor, um die Barrierefreiheitsoptionen zu verwenden:

1. Wählen Sie eine Komponente aus und tippen Sie auf ![cmppr](assets/cmppr.png).
1. Klicken Sie in der Randleiste auf **[!UICONTROL Ein-/Ausgabehilfe]**, um die gewünschte Barrierefreiheitsoption auszuwählen.

### Barrierefreiheitsoptionen in Formularkomponenten {#accessibility-options-in-form-components}

![Barrierefreiheitsoptionen in Formularkomponenten](assets/accessibility-options.png)

**Benutzerdefinierte** TextForm-Autoren stellen den Inhalt im Feld für die Barrierefreiheitsoption Benutzerdefinierter Text bereit. Die Hilfstechnologie, wie Bildschirmlesehilfen, verwendet diesen benutzerdefinierten Text. In den meisten Szenarien ist die Verwendung der Einstellung „Titel“ die beste Option. Sie sollten nur dann benutzerdefinierten Text für Bildschirmlesegeräte erstellen, wenn die Option „Titel“ oder eine Kurzbeschreibung nicht möglich ist.

**Kurze** Beschreibung: Für die meisten Komponenten wird die kurze Beschreibung zur Laufzeit angezeigt, wenn der Benutzer den Mauszeiger über die Komponente bewegt. Sie können diese Option im Feld „Kurzbeschreibung“ unter der Option für den Hilfeinhalt festlegen.

**** TitelVerwenden Sie diese Option, damit AEM Forms die visuelle Bezeichnung, die dem Formularfeld zugeordnet ist, als Text für die Bildschirmlesehilfe verwenden kann.

**** NameSie können auf der Registerkarte &quot;Bindung&quot;im Feld &quot;Name&quot;einen Wert angeben. Der Name darf keine Leerzeichen enthalten.

**** Keine Auswahl Keine bewirkt, dass das Formularobjekt keinen Namen im veröffentlichten Formular hat. &quot;Keine&quot;ist keine empfohlene Einstellung für Formularsteuerelemente.

>[!NOTE]
>
>* Optionsfelder und Kontrollkästchen können nur zwei Optionen für die Barrierefreiheit aufweisen, nämlich „Benutzerdefinierter Text“ und „Titel“.
>* Bei XFA-basierten adaptiven Formularen wird die Barrierefreiheitsoption von den in der XDP festgelegten Barrierefreiheitsoptionen übernommen. QuickInfo von XDP werden der Kurzbeschreibung zugeordnet, und die Beschriftung wird dem Titel zugeordnet. Die anderen Optionen bleiben gleich.


### 3. Stellen Sie Textäquivalente für Bilder bereit {#provide-text-equivalents-for-images}

Durch Bilder können einigen Benutzern Aspekte veranschaulicht werden. Für Benutzer, die Bildschirmlesegeräte verwenden, verringern Bilder allerdings die Barrierefreiheit Ihres Formulars. Wenn Sie Bilder verwenden möchten, sollten Sie Textbeschreibungen für alle Bilder angeben.

Stellen Sie sicher, dass der Text das Objekt und seinen Zweck im Formular beschreibt. Ein Bildschirmlesegerät liest den alternativen Text, wenn ein Bild auftritt. Für jedes Bild muss ein alternativer Text angegeben sein.

Wählen Sie eine Bildkomponente aus und tippen Sie auf ![cmppr](assets/cmppr.png). Geben Sie in der Randleiste unter „Eigenschaften“ alternativen Text für ein Bild ein.

![Alternativtext für ein Bild](assets/image-properties.png)

### 4. Bereitstellung eines ausreichenden Farbkontrasts {#provide-sufficient-color-contrast}

Bei Barrierefreiheitsdesigns müssen zusätzliche Richtlinien zur Farbverwendung beachtet werden. Formularautoren können Farben verwenden, um das Erscheinungsbild von Formularen zu verbessern, indem sie verschiedene Formularkomponenten hervorheben. Bei einer falschen Farbnutzung kann ein Formular allerdings für Personen mit unterschiedlichen Fähigkeiten schwieriger oder gar nicht lesbar werden.

Sehbehinderte Benutzer sind auf einen hohen Kontrast zwischen Text und Hintergrund angewiesen, um digitale Inhalte lesen zu können. Ohne ausreichend Kontrast kann ein Formular für einige Benutzern schwieriger oder überhaupt nicht zu lesen sein.

Es wird empfohlen, dass Sie die Standardschrift und -hintergrundfarben verwenden: Inhalt in schwarzer Farbe auf einem weißen Hintergrund. Wenn Sie die Standardfarben ändern, wählen Sie entweder eine dunkle Vordergrundfarbe auf einer hellen Hintergrundfarbe oder umgekehrt.

Weitere Informationen zum Ändern des Farbkontrasts und des Themas für adaptive Formulare finden Sie unter [Erstellen benutzerdefinierter Themen für adaptive Formulare](/help/forms/using/creating-custom-adaptive-form-themes.md).

### 5. Stellen Sie sicher, dass Formularsteuerelemente über die Tastatur zugänglich sind. {#ensure-that-form-controls-are-keyboard-accessible}

Ein barrierefreies Formular kann vollständig mit nur der Tastatur oder einem ähnlichen Eingabegerät ausgefüllt werden. Benutzer mit eingeschränkter Mobilität bzw. Sehfähigkeit haben möglicherweise keine andere Wahl, als die Tastatur zu nutzen, und viele Benutzer, die eine Maus verwenden könnten, ziehen es vor, Eingaben per Tastatur vorzunehmen. Indem Sie mehrere Eingabeverfahren ermöglichen, erstellen Sie Formulare, die nicht nur barrierefrei sind, sondern auch den Vorlieben aller Benutzer entgegenkommen.

Die folgenden Tastaturbefehle sind in AEM Forms verfügbar.

| Aktion | Tastaturbefehl |
|---|---|
| Den Cursor in einem Formular vorwärts bewegen | Registerkarte |
| Den Cursor in einem Formular rückwärts bewegen | Umschalt+Tab |
| Zum nächsten Bereich wechseln | Alt+Nach-rechts-Taste |
| Zum vorherigen Bereich wechseln | Alt+Nach-links-Taste |
| Die ausgefüllten Daten in einem Formular zurücksetzen | Alt+R |
| Formular senden | Alt+S |

Darüber hinaus stehen für die Komponente **[!UICONTROL Datumsauswahl]** in Adaptive Forms verschiedene Tastaturbefehle zur Verfügung. Um die Tastaturbefehle zu aktivieren, tippen Sie auf die Komponente **[!UICONTROL Datumsauswahl]** und dann auf ![Konfigurieren](assets/configure-icon.svg) , um die Eigenschaften zu öffnen. Wählen Sie im Abschnitt **[!UICONTROL Muster]** ein Anzeigemuster mithilfe der Dropdown-Listen **[!UICONTROL Typ]** und **[!UICONTROL Muster]** aus. Speichern Sie die Eigenschaften, um die Verwendung der Tastaturbefehle für die Komponente **[!UICONTROL Datumsauswahl]** zu aktivieren.

Die folgenden Tastaturbefehle sind für die Datumsauswahlkomponente in Adaptive Forms verfügbar:

| Aktion | Tastaturbefehl |
|---|---|
| <ul><li>Zeigen Sie die Komponentenoptionen für die Datumsauswahl an, wenn der Tab-Fokus das Kalendersymbol markiert</li><li>Führen Sie das Klickereignis aus, wenn im Registerfokus eine Option hervorgehoben wird</li> | Leerzeichen oder Eingabetaste |
| Ausblenden der Optionen der Datumsauswahl-Komponente | Esc |
| <ul><li>Bewegen Sie den Cursor nach vorne durch die Optionen, die in der Komponente Datumsauswahl verfügbar sind.</li><li>Festlegen des Tabulatorfokus auf das Kalendersymbol, wenn das Eingabefeld für das Datum aktiv ist</li> | Registerkarte |
| Den Cursor durch die in der Datumsauswahl-Komponente verfügbaren Optionen nach hinten bewegen | Umschalt+Tab |
| <ul><li>Zeigen Sie die Komponentenoptionen für die Datumsauswahl an, wenn der Tab-Fokus das Eingabefeld für das Datum markiert</li><li>Bewegen Sie den Cursor im Kalender nach unten, der in der Datumsauswahlkomponente verfügbar ist.</li> | Nach-unten-Pfeil |
| Bewegen Sie den Cursor im Kalender nach oben, der in der Datumsauswahlkomponente verfügbar ist. | Nach-oben-Taste |
| Den Cursor im Kalender in der Datumsauswahl-Komponente nach hinten verschieben | Nach-links-Taste |
| Bewegen Sie den Cursor im Kalender, der in der Datumsauswahl-Komponente verfügbar ist, nach vorne. | Rechtspfeil |
| Führen Sie die Aktion für die Beschriftung durch, die zwischen den Navigationspfeilen rechts und links im Kalender verfügbar ist. | Umschalt+Aufwärtspfeil |
| Führen Sie die Aktion für das im Kalender verfügbare Pfeilsymbol für die rechte Navigation ![Rechtspfeil](assets/right-navigation-icon.svg) aus. | Umschalt+Linkspfeil |
| Führen Sie die Aktion für das linke Navigationspfeilsymbol ![Linkspfeil](assets/left-navigation-icon.svg) aus, das im Kalender verfügbar ist. | Umschalt+Rechtspfeil |

## Verwenden Sie das Barrierefreiheitswerkzeug, um die verbleibenden Probleme mit der Barrierefreiheit zu finden.

Der Accessible Name and Description Inspector (ANDI) unterstützt Sie beim Identifizieren und Beheben von Problemen mit der Barrierefreiheit in einem adaptiven Formular. So suchen Sie mit dem ANDI-Tool nach Zugänglichkeitsproblemen in einem adaptiven Formular:

1. Öffnen Sie das adaptive Formular im Vorschaumodus.
1. Klicken Sie auf das mit Lesezeichen versehene ANDI-Tool-Symbol. Das ANDI-Tool analysiert das adaptive Formular und zeigt Probleme mit der Barrierefreiheit an. Weitere Informationen zur Verwendung des Tools finden Sie in der [ANDI-Dokumentation](https://www.ssa.gov/accessibility/andi/help/howtouse.html).
1. Überprüfen und beheben Sie die von ANDI gemeldeten Probleme.
