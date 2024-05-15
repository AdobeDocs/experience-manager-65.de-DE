---
title: Erstellen barrierefreier adaptiver Formulare
description: AEM Forms bietet Tools zum Erstellen barrierefreier adaptiver Formulare und vereinfacht die Einhaltung von Standards zur Barrierefreiheit.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: e755159f-374f-42b8-b28b-e8864df44f9d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2099'
ht-degree: 100%

---

# Zugreifbare adaptive Formulare erstellen{#creating-accessible-adaptive-forms}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/introduction) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird ein älterer Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Einführung {#introduction}

Ein barrierefreies Formular ist ein Formular, das alle verwenden können, einschließlich von Benutzenden mit Behinderungen. Adaptive Formulare verfügen über eine Reihe von Merkmalen und Funktionen, die die Benutzerfreundlichkeit für Benutzende mit unterschiedlichen Fähigkeiten verbessern. Die Integration barrierefreier Ein-/Ausgabehilfen in adaptive Formulare ermöglicht nicht nur eine größtmögliche Zielgruppe für den Inhalt, dies ist auch eine Anforderung beim Bereitstellen von Dokumenten in Regionen, in denen die Einhaltung von Standards zur Barrierefreiheit obligatorisch ist. Mit AEM Forms können Formularentwickler die Barrierefreiheitsstandards einhalten.

Beim Verfassen eines adaptiven Formulars müssen Autorinnen und Autoren die folgenden Punkte berücksichtigen, um barrierefreie adaptive Formulare zu erstellen:

* Überprüfen des Formulars mit dem Barrierefreiheits-Test-Tool ANDI (Accessible Name and Description Inspector)
* Angabe von angemessenen Beschriftungen für Formularsteuerelemente
* Angabe von Textäquivalenten für Bilder
* Sicherstellen von ausreichendem Farbkontrast
* Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können

## Voraussetzung

Sie benötigen ein Tool für Barrierefreiheit wie **ANDI (Accessible Name and Description Inspector)** und ein **adaptives Formular-Design, das entwickelt wurde, um Barrierefreiheitsprobleme zu beheben**, um ein barrierefreies adaptives Formular zu erstellen.

### Herunterladen und Installieren des Test-Tools für Barrierefreiheit

Das Tool ANDI (Accessible Name and Description Inspector) hilft Ihnen bei der Identifizierung und Behebung von Problemen mit der Barrierefreiheit in Web-Inhalten. Es ist das empfohlene Tool gemäß den Trusted Tester-Richtlinien v5 des Ministeriums für Innere Sicherheit. Es wurde von der Abteilung „Social Security Administration“ der USA entwickelt, um Webinhalte auf die Einhaltung von Section 508-Anforderungen hin zu überprüfen. Das Tool:

* Hilft bei der Erkennung von Barrierefreiheitsproblemen auf einer Web-Seite
* Macht Vorschläge zur Verbesserung der Barrierefreiheit
* Erkennt Probleme mit der Barrierefreiheit der Tastaturnutzbarkeit und dem Farbkontrast
* Identifiziert eindeutig den Inhalt von Bildschirmlesehilfen gemäß den Standards

ANDI funktioniert mit allen gängigen Internetbrowsern. Detaillierte Anweisungen zum Konfigurieren und Verwenden des Tools finden Sie in der [ANDI-Dokumentation](https://www.ssa.gov/accessibility/andi/help/install.html).

### Herunterladen und Installieren des „Ultramarine-Accessible“-Designs

Das „Ultramarine-Accessible“-Design („Ultramarinblau – Barrierefreiheit“) ist ein Referenzdesign. Es veranschaulicht, wie Sie Farbkontrast- und andere Probleme mit der Barrierefreiheit in einem adaptiven Formular beheben können. Adobe empfiehlt, ein benutzerdefiniertes Design für die Produktionsumgebung zu erstellen, das auf den von Ihrem Unternehmen genehmigten Stilen basiert. Führen Sie die folgenden Schritte aus, um das Thema in Ihre AEM-Instanz hochzuladen:

1. Laden Sie das Designpaket herunter.
1. Navigieren Sie in Ihrer AEM-Instanz zu **[!UICONTROL Experience Manager]** > **[!UICONTROL Navigation]** ![Navigation](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]**.
1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]** aus. Wählen Sie die Datei x Ultramarine-Accessible-Theme.zip aus und laden Sie sie hoch. Das Design wird in Ihre AEM Instanz hochgeladen.

## Gestalten eines barrierefreien adaptiven Formulars

Sie sollten sich auf vier wichtige Aspekte konzentrieren: Tastaturnavigation, Farbkontrast, aussagekräftige Alternativtexte für Bilder und geeignete Beschriftungen für Formularsteuerelemente, um ein adaptives Formular barrierefrei zu gestalten. Führen Sie die folgenden Schritte aus, um das vorhandene adaptive Forms barrierefrei zu machen:

### 1. Anwenden eines barrierefreien Designs und Vornehmen weiterer Korrekturen

Wenden Sie das Design „Ultramarine-Accessible“ auf Ihr vorhandenes adaptives Formular an. So wenden Sie das Design an:

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten.
1. Wählen Sie eine Komponente und das übergeordnete Symbol aus. Wählen Sie im Kontextmenü die Option **[!UICONTROL Container für adaptive Formulare]** und dann das Symbol „Konfigurieren“ aus.
1. Wählen Sie im Eigenschaften-Browser das Design „Ultramarine-barrierefrei“ und dann das Symbol **[!UICONTROL Speichern]** aus.
1. Aktualisieren Sie das Browser-Fenster. Das Design wird auf das adaptive Formular angewendet.

Nachdem Sie ein barrierefreies Design angewendet haben, führen Sie die folgenden zusätzlichen Korrekturen durch. Die Korrekturen ergänzen die Barrierefreiheitskorrekturen, die anhand des barrierefreien Designs angewandt werden:

1. Fügen Sie einen aussagekräftigen Alternativtext für das Logobild im adaptiven Formular hinzu.

   Geben Sie einen aussagekräftigen Alternativtext für Bilder in den Kopf- und Fußzeilenkomponenten der Vorlage für das adaptive Formular ein. Wenn Sie die Vorlage korrigieren und zum Erstellen eines adaptiven Formulars verwenden, übernimmt das adaptive Formular alle Korrekturen, die im Interesse der Barrierefreiheit an der Kopf- und Fußzeile der Vorlage vorgenommen wurden.  Nehmen Sie Änderungen für ein vorhandenes adaptives Formular auf Ebene des adaptiven Formulars vor. Änderungen, die an einer Vorlage für adaptive Formulare vorgenommen wurden, werden nicht automatisch in schon vorhandene adaptive Formulare eingespielt.

1. Fügen Sie dem adaptiven Formular eine Überschriftenkomponente hinzu, die den Formularnamen enthält. Wenn Ihr Formularentwurf einen Firmennamen angibt, fügen Sie auch für den Firmennamen eine separate Überschriftenkomponente hinzu.

   Die meisten Barrierefreiheits-Tools informieren Benutzer über die Hierarchie der Inhalte, damit sie die Struktur der Web-Seite besser verstehen. Legen Sie im adaptiven Formular unterschiedliche Überschriftenebenen für den Namen des Unternehmens und des Formulars fest, um eine hierarchische Struktur dieser Texte zu erzielen. Verwenden Sie außerdem vor jedem Bereich und Abschnitt eine Textkomponente mit einer entsprechenden Überschriftenebene, um eine Hierarchie zu erstellen.

   ![Anwenden eines Kopfzeilenstils](assets/apply-style.gif)

1. Ändern Sie die Hintergrundfarbe der Fußzeile, um einen gemäß den Barrierefreiheitsstandards angemessenen Kontrast zu erhalten, damit der Text besser sichtbar und lesbar wird. Sie können ANDI verwenden, um Probleme mit dem Farbkontrast in Ihrem Formular zu ermitteln. Verwenden Sie auch keine zu kleinen Schriftarten. Kleine Schriftarten sind schwer zu lesen.

1. Ersetzen Sie die Umschalt- und Bildauswahl-Komponenten in Ihrem vorhandenen adaptiven Formular durch die Auswahlkomponente (Optionsfeld).

1. Ersetzen Sie die Komponente „Numerische Schritte“ in einem vorhandenen adaptiven Formular durch die Komponente „Numerisches Feld“.

1. Ersetzen Sie Datumseingabe-Felder durch Datumsauswahl-Felder.

1. Legen Sie Anzeige-, Prüf- und Bearbeitungsmuster für die Datumsauswahl-Komponente fest. Legen Sie außerdem eine benutzerdefinierte Fehlermeldung für den Fall von Prüffehlern fest. Zum Beispiel: „Sie haben ein ungültiges Datum angegeben. Das korrekte Datumsformat lautet TT.MM.JJJJ.“

1. Legen Sie einen benutzerdefinierten barrierefreien Text für die Datumsauswahl-Komponente fest. Zum Beispiel: „Geben Sie Ihr Geburtsdatum ein.“ Bildschirmlesehilfen lesen diese benutzerdefinierten barrierefreien Texte.

1. Verwenden Sie für Komponenten des adaptiven Formulars kurze statt langer Beschreibungen. Eine lange Beschreibung fügt die Schaltfläche „Hilfe“ hinzu. Vergewissern Sie sich, dass das adaptive Formular über keine Schaltfläche „Hilfe“ verfügt.

1. Fügen Sie allen schreibgeschützten Tabellenzellen einen benutzerdefinierten barrierefreien Text hinzu. Deaktivieren Sie außerdem alle schreibgeschützten Zellen von Tabellen.

1. Entfernen Sie Felder für die Freihandeingabe von Unterschriften aus dem adaptiven Formular, sofern vorhanden. Konfigurieren Sie das adaptive Formular so, dass Adobe Sign für problemloses digitales Signieren verwendet wird.

### 2. Angabe von angemessenen Beschriftungen für Formularsteuerelemente {#provide-proper-labels-for-form-controls}

Die Beschriftung oder der Titel einer Komponente gibt an, was die Formularkomponente darstellt. Der Text „Vorname“ weist Benutzende zum Beispiel darauf hin, dass sie ihren Vornamen in ein Textfeld eingeben müssen. Damit Bildschirmlesehilfen auf die Beschriftung zugreifen können, wird diese programmgesteuert mit einer Formularkomponente verknüpft. Alternativ dazu kann das Steuerelement im Formular mit zusätzlichen Barrierefreiheitsinformationen konfiguriert werden.

Die Beschriftung, die von Bildschirmlesehilfen wahrgenommen wird, muss nicht mit der visuellen Beschriftung übereinstimmen. In einigen Fällen möchten Sie den Zweck des Steuerelements möglicherweise genauer untersuchen. Für jedes Feldobjekt in einem Formular können die Barrierefreiheitsoptionen verwendet werden, um festzulegen, was die Bildschirmlesehilfe anzeigt, um das spezifische Formularfeld zu identifizieren.

Gehen Sie wie folgt vor, um die Barrierefreiheitsoptionen zu verwenden:

1. Wählen Sie eine Komponente und ![cmppr](assets/cmppr.png) aus.
1. Klicken Sie in der Seitenleiste auf **[!UICONTROL Ein-/Ausgabehilfe]**, um die gewünschte Barrierefreiheitsoption auszuwählen.

### Barrierefreiheitsoptionen in Formularkomponenten {#accessibility-options-in-form-components}

![Barrierefreiheitsoptionen in Formularkomponenten](assets/accessibility-options.png)

**Eigener Text** Formularautoren geben den Inhalt im Textfeld „Eigener Text“ der Barrierefreiheitsoptionen an. Die Hilfstechnologie, wie Bildschirmlesegeräte, verwendet diesen benutzerdefinierten Text. In den meisten Szenarien ist die Verwendung der Einstellung „Titel“ die beste Option. Sie sollten nur dann benutzerdefinierten Text für Bildschirmlesehilfen erstellen, wenn die Option „Titel“ oder eine Kurzbeschreibung nicht möglich ist.

**Kurzbeschreibung** Bei den meisten Komponenten wird die Kurzbeschreibung zur Laufzeit angezeigt, wenn der Benutzer den Mauszeiger über die Komponente hält. Sie können diese Option im Feld „Kurzbeschreibung“ unter der Option für den Hilfeinhalt festlegen.

**Titel** Verwenden Sie diese Option, damit AEM Forms die visuelle Beschriftung, die mit dem Formularfeld verknüpft ist, als Text für Bildschirmlesegeräte verwendet.

**Name** Sie können einen Wert im Feld „Name“ auf der Registerkarte „Bindung“ angeben. Der Name darf keine Leerzeichen enthalten.

**Kein** Bei Auswahl von „Kein“ verfügt das Formularobjekt im veröffentlichten Formular über keinen Namen. Die Einstellung „Kein“ empfiehlt sich nicht für Formularsteuerelemente.

>[!NOTE]
>
>* Optionsfelder und Kontrollkästchen können nur zwei Optionen für die Barrierefreiheit aufweisen, nämlich „Eigener Text“ und „Titel“.
>* Bei XFA-basierten adaptiven Formularen wird die Barrierefreiheitsoption von den in der XDP festgelegten Barrierefreiheitsoptionen übernommen. QuickInfos aus der XDP werden der Kurzbeschreibung zugeordnet und die Beschriftung dem Titel. Die anderen Optionen bleiben gleich.

### 3. Angabe von Textäquivalenten für Bilder {#provide-text-equivalents-for-images}

Bilder können bei einigen Benutzenden zu einem besseren Verständnis beitragen. Für diejenigen Benutzenden, die Bildschirmlesehilfen verwenden, verringern Bilder jedoch die Barrierefreiheit Ihres Formulars. Wenn Sie Bilder verwenden möchten, sollten Sie Textbeschreibungen für alle Bilder angeben.

Stellen Sie sicher, dass der Text das Objekt und seinen Zweck im Formular beschreibt. Eine Bildschirmlesehilfe liest diesen alternativen Text vor, wenn sie auf ein Bild stößt. Für jedes Bild muss ein alternativer Text angegeben sein.

Wählen Sie eine Bildkomponente und ![cmppr](assets/cmppr.png) aus. Geben Sie in der Seitenleiste unter „Eigenschaften“ einen Alternativtext für ein Bild ein.

![Alternativtext für ein Bild](assets/image-properties.png)

### 4. Sicherstellen von ausreichendem Farbkontrast {#provide-sufficient-color-contrast}

Bei Barrierefreiheits-Designs müssen zusätzliche Richtlinien zur Farbverwendung beachtet werden. Formularautorinnen und -autoren können Farben verwenden, um das Erscheinungsbild von Formularen zu verbessern, indem sie verschiedene Formularkomponenten hervorheben. Bei falscher Farbnutzung kann ein Formular allerdings für Personen mit unterschiedlichen Fähigkeiten schwieriger oder gar nicht lesbar werden.

Benutzende mit Sehbehinderung benötigen etwa einen hohen Kontrast zwischen Text und Hintergrund, um digitale Inhalte zu lesen. Ohne genügend Kontrast kann ein Formular für einige Benutzende schwieriger oder überhaupt nicht lesbar sein.

Es wird empfohlen, die standardmäßigen Schrift- und Hintergrundfarben zu verwenden: Inhalte in schwarzer Farbe auf weißem Hintergrund. Wenn Sie die Standardfarben ändern, wählen Sie entweder eine dunkle Vordergrundfarbe auf heller Hintergrundfarbe oder umgekehrt.

Weitere Informationen zum Ändern des Farbkontrasts und Designs für adaptive Formulare finden Sie unter [Erstellen benutzerdefinierter Designs für adaptive Formulare](/help/forms/using/creating-custom-adaptive-form-themes.md).

### 5. Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können {#ensure-that-form-controls-are-keyboard-accessible}

Ein barrierefreies Formular kann vollständig mit nur der Tastatur oder einem entsprechenden Eingabegerät ausgefüllt werden. Benutzende mit eingeschränkter Mobilität oder Sehfähigkeit haben möglicherweise keine andere Wahl, als die Tastatur zu verwenden, und auch viele Benutzende, die eine Maus verwenden könnten, bevorzugen die Eingabe über die Tastatur. Indem Sie mehrere Eingabeverfahren ermöglichen, erstellen Sie Formulare, die nicht nur barrierefrei sind, sondern auch den Vorlieben von allen Benutzenden entgegenkommen.

Die folgenden Tastaturbefehle sind in AEM Forms verfügbar.

| Aktion | Tastaturbefehl |
|---|---|
| Cursor in einem Formular vorwärts bewegen | Registerkarte |
| Cursor in einem Formular rückwärts bewegen | Umsch+Tab |
| Zum nächsten Bedienfeld wechseln | Alt+Nach-rechts-Taste |
| Zum vorherigen Bedienfeld wechseln | Alt+Nach-links-Taste |
| Die ausgefüllten Daten in einem Formular zurücksetzen | Alt+R |
| Formular absenden | Alt+S |

Darüber hinaus stehen verschiedene Tastaturbefehle für die Komponente **[!UICONTROL Datumsauswahl]** in adaptiven Formularen zur Verfügung. Wählen Sie zum Aktivieren der Tastenkombinationen die Komponente **[!UICONTROL Datumsauswahl]** und dann ![Konfigurieren](assets/configure-icon.svg) aus, um die Eigenschaften zu öffnen. Wählen Sie im Abschnitt **[!UICONTROL Muster]** ein Anzeigemuster mithilfe der Dropdown-Listen **[!UICONTROL Typ]** und **[!UICONTROL Muster]** aus. Speichern Sie die Eigenschaften, um die Verwendung der Tastenkombinationen für die Komponente **[!UICONTROL Datumsauswahl]** zu aktivieren.

Für die Datumsauswahl-Komponente in adaptiven Formularen stehen die folgenden Tastaturbefehle zur Verfügung:

| Aktion | Tastaturbefehl |
|---|---|
| <ul><li>Anzeigen der Optionen für die Datumsauswahl-Komponente, wenn der Fokus auf dem Kalendersymbol liegt</li><li>Ausführen des Klick-Ereignisses, wenn der Fokus auf einer Option liegt</li> | Leertaste oder Eingabetaste |
| Ausblenden der Optionen für die Datumsauswahl-Komponente | Esc |
| <ul><li>Vorwärtsbewegen des Cursors durch die Optionen, die in der Komponente „Datumsauswahl“ verfügbar sind</li><li>Festlegen des Fokus auf das Kalendersymbol, wenn das Datumseingabefeld aktiv ist</li> | Registerkarte |
| Rückwärtsbewegen des Cursors durch die Optionen, die in der Komponente „Datumsauswahl“ verfügbar sind | Umsch+Tab |
| <ul><li>Anzeigen der Optionen für die Datumsauswahl-Komponente, wenn der Fokus auf dem Eingabefeld für ein Datum liegt</li><li>Abwärtsbewegen des Cursors in dem Kalender, der in der Datumsauswahl-Komponente verfügbar ist</li> | Nach-unten-Taste |
| Aufwärtsbewegen des Cursors in dem Kalender, der in der Datumsauswahl-Komponente verfügbar ist | Nach-oben-Taste |
| Rückwärtsbewegen des Cursors in dem Kalender, der in der Datumsauswahl-Komponente verfügbar ist | Nach-links-Taste |
| Vorwärtsbewegen des Cursors in dem Kalender, der in der Datumsauswahl-Komponente verfügbar ist | Nach-rechts-Taste |
| Durchführen der Aktion für die Beschriftung, die zwischen dem Nach-links- und dem Nach-rechts-Navigationssymbol und im Kalender verfügbar ist | Umsch+Nach-oben-Taste |
| Durchführen der Aktion für das Nach-rechts-Navigationssymbol ![right-arrow](assets/right-navigation-icon.svg), das im Kalender verfügbar ist | Umsch+Nach-links-Taste |
| Durchführen der Aktion für das Nach-links-Navigationssymbol ![left-arrow](assets/left-navigation-icon.svg), das im Kalender verfügbar ist | Umsch+Nach-rechts-Taste |

## Verwenden des Barrierefreiheits-Tools, um noch verbleibende Probleme hinsichtlich der Barrierefreiheit zu ermitteln

ANDI (Accessible Name and Description Inspector) unterstützt Sie beim Identifizieren und Beheben von Problemen mit der Barrierefreiheit in einem adaptiven Formular. So suchen Sie mit dem ANDI-Tool nach Barrierefreiheitsproblemen in einem adaptiven Formular:

1. Öffnen Sie das adaptives Formular im Vorschaumodus.
1. Klicken Sie auf das als Lesezeichen gespeicherte Symbol für das ANDI-Tool. Das ANDI-Tool analysiert das adaptive Formular und zeigt Probleme bezüglich der Barrierefreiheit an. Weitere Informationen zur Verwendung des Tools finden Sie in der [ANDI-Dokumentation](https://www.ssa.gov/accessibility/andi/help/howtouse.html).
1. Überprüfen und beheben Sie die von ANDI gemeldeten Probleme.
