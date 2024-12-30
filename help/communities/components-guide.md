---
title: Handbuch der Community-Komponenten
description: Ein interaktives Entwicklungstool für die ersten Schritte mit dem Social Component Framework (SCF)
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 12c0eae5-fd76-4480-a012-25d3312f3570
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---

# Handbuch der Community-Komponenten  {#community-components-guide}

Das Community Components Guide ist ein interaktives Entwicklungstool für das [Social Component Framework (SCF)](scf.md). Es enthält eine Liste der verfügbaren Adobe Experience Manager (AEM)-Communities-Komponenten oder der komplexeren Funktionen, die aus mehreren Komponenten erstellt wurden.

Neben grundlegenden Informationen zu den einzelnen Komponenten ermöglicht das Handbuch Experimente mit der Funktionsweise der SCF-Komponenten/-Funktionen und der Möglichkeit, sie zu konfigurieren oder anzupassen.

Informationen zu den Entwicklungsgrundlagen für jede Komponente finden Sie unter [Funktions- und Komponentengrundlagen](essentials.md).

## Erste Schritte {#getting-started}

Das Handbuch ist für die Verwendung in Entwicklungsinstallationen von Autoreninstanzen (localhost:4502) und Veröffentlichungsinstanzen (localhost:4503) vorgesehen.

Die Community-Komponenten-Website finden Sie unter

* [https://&lt;server>:&lt;port>/content/community-components/en.html](http://localhost:4502/content/community-components/en.html)

Die Interaktionen mit den Communitys-Komponenten variieren je nach:

* Server (Autor oder Veröffentlichung).
* Ob der Site-Besucher angemeldet ist oder nicht.
* Wenn angemeldet, die dem Mitglied zugewiesenen Berechtigungen.
* Ob das standardmäßige SRP [JSRP](jsrp.md) verwendet wird.

Um in der Autoreninstanz in den Bearbeitungsmodus zu wechseln, fügen Sie nach dem Servernamen als erstes Pfadsegment entweder `editor.html` oder `cf#` ein:

* Standard-Benutzeroberfläche:

  [https://&lt;server>:&lt;port>/editor.html/content/community-components/en.html](http://localhost:4502/editor.html/content/community-components/en.html)

* Klassische Benutzeroberfläche:

  [https://&lt;server>:&lt;port>/cf#/content/community-components/en.html](http://localhost:4502/cf#/content/community-components/en.html)

>[!NOTE]
>
>Bei der Autoreninstanz im Bearbeitungsmodus sind die Links auf einer Seite nicht aktiv.
>
>Um zu einer Komponentenseite zu navigieren, wählen Sie zunächst den Vorschaumodus aus, um die Links zu aktivieren.
>
>Kehren Sie bei im Browser angezeigter Komponentenseite zum Modus Bearbeiten zurück, um das Dialogfeld Bearbeiten der Komponente zu öffnen.
>
>Allgemeine Informationen zum Authoring finden Sie in der [Kurzanleitung zum Authoring von Seiten](../../help/sites-authoring/qg-page-authoring.md).
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [Grundlegende Handhabung](../../help/sites-authoring/basic-handling.md).

### Startseite {#home-page}

Das Handbuch enthält eine Liste der SCF-Komponenten, die links auf der Seite für Vorschau und Prototyping verfügbar sind.

Komponentenleitfaden, wie in einer Autoreninstanz im Bearbeitungsmodus angezeigt:

![community-component1](assets/community-component1.png)

## Komponentenseiten {#component-pages}

Wählen Sie links auf der Seite in der Liste eine Komponente aus.

![community-component-pages](assets/community-component2.png)

Der Hauptteil des Handbuchs zeigt Folgendes an:

1. Titel: Der Name der ausgewählten Komponente
1. [Client-seitige ](#client-side-libraries): Eine Liste mit einer oder mehreren erforderlichen Kategorien
1. [Einschließbar](scf.md#add-or-include-a-communities-component): Wenn die Komponente dynamisch eingeschlossen werden kann, kann der Status im Bearbeitungsmodus für Autoren umgeschaltet werden:

   * Wenn sie hinzugefügt wird, wird Text angezeigt: „Diese Komponente ist über ihren übergeordneten Knoten enthalten.“
   * Wenn enthalten, wird Text angezeigt: „Diese Komponente ist dynamisch enthalten.“
   * Wenn dies nicht der Fall ist, wird kein Text angezeigt

1. Beispielkomponente oder -funktion: Eine aktive Instanz der Komponente oder Funktion. Wenn es sich um eine Komponente handelt, kann sie durch Änderungen an den Vorlagen, CSS und den Daten geändert werden, die im Abschnitt Registerkarte bereitgestellt werden.

>[!NOTE]
>
>Nachdem Sie eine Auswahl auf der linken Seite getroffen haben, wird die Komponente unter anstelle von neben der Liste der Komponenten angezeigt, wenn das Browser-Fenster zu eng ist.

### Autoreninteraktionen {#author-interactions}

Bei Verwendung des Handbuchs auf einer Autoreninstanz ist es möglich, die Konfiguration einer Komponente durch Öffnen des entsprechenden Dialogfelds zu erleben. Informationen für Entwickler finden Sie im Abschnitt [Komponenten und ](essentials.md)) der Dokumentation, während die Dialogeinstellungen für Autoren im Abschnitt [Communities-Komponenten](author-communities.md) beschrieben werden.

Für das Handbuch der Community-Komponenten werden einige Einstellungen für das Komponentendialogfeld mit dem [Einschließbar](scf.md#add-or-include-a-communities-component)-Umschalter überlagert. Um zwischen der Verwendung der vorhandenen Ressource oder einer dynamisch eingeschlossenen Ressource umzuschalten, wählen Sie im Bearbeitungsmodus sowohl die Komponente als auch den einzuschließenden Text aus und doppelklicken Sie, um das Dialogfeld „Bearbeiten“ zu öffnen:

![community-component3](assets/community-component3.png)

Auf der Registerkarte **Vorlagen**:

![community-component4](assets/community-component4.png)

* **Untergeordnete Komponente mit sling:include einschließen**

  Wenn diese Option deaktiviert ist, verwendet das Komponenten-Handbuch die vorhandene Ressource im Repository (einen jcr-Knoten, der einem para-Knoten untergeordnet ist).

   * Angezeigter Text: „Diese Komponente ist über ihren übergeordneten Knoten enthalten.“

  Wenn diese Option aktiviert ist, verwendet das Komponenten-Handbuch Sling, um eine Komponente des resourceType des untergeordneten Knotens dynamisch einzuschließen (nicht vorhandene Ressource).

   * Angezeigter Text: „Diese Komponente ist dynamisch enthalten.“

  Standard ist deaktiviert.

### Publish Interactions {#publish-interactions}

Bei Verwendung des Handbuchs auf einer Veröffentlichungsinstanz können die Komponenten und Funktionen als Site-Besucher (nicht angemeldet) und als Mitglieder mit verschiedenen Berechtigungen erleben, wenn sie angemeldet sind.

>[!NOTE]
>
>Beachten Sie: Wenn der SRP standardmäßig auf [JSRP](jsrp.md) eingestellt bleibt, ist der in der Veröffentlichungsinstanz eingegebene benutzergenerierte Inhalt nur in der Veröffentlichungsinstanz sichtbar und *nicht* in der [Moderation](moderate-ugc.md)-Konsole in der Autoreninstanz sichtbar.

## Client-seitige Bibliotheken {#client-side-libraries}

Die für jede Komponente aufgelisteten Client-seitigen Bibliotheken (clientlibs) sind die (*),* beim Platzieren der Komponente auf einer Seite referenziert werden müssen. Die Clientlibs bieten eine Möglichkeit zur Verwaltung und Optimierung des Downloads von JavaScript und CSS, die zum Rendern der Komponente im Browser verwendet werden.

Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

## Personifikation {#impersonation}

Verwenden Sie auf der Autoreninstanz, bei der häufig eine Person als Administrator oder Entwickler angemeldet ist, um die als ein anderer Benutzer angemeldete Komponente zu verwenden, das Textfeld links neben der Schaltfläche **[!UICONTROL Identität annehmen]**, um entweder den Benutzernamen einzugeben oder aus der Pulldown-Liste auszuwählen, und klicken Sie dann auf die Schaltfläche. Klicken Sie auf Wiederherstellen , um sich abzumelden und den Identitätswechsel zu beenden.

Für die Veröffentlichungsinstanz ist keine Stellvertretung erforderlich. Verwenden Sie einfach den Anmelde-/Abmelde-Link, um die Identität verschiedener Benutzer anzunehmen, z. B[ Demo-Benutzer](tutorials.md#demo-users).

## Anpassung {#customization}

Wenn diese Option aktiviert ist, ist jede SCF-Komponente für das Prototyping möglicher Anpassungen verfügbar, indem die Vorlage, das CSS und die Daten der Komponente vorübergehend geändert werden.

### Aktivieren der Anpassung {#enabling-customization}

>[!NOTE]
>
>**Dieses Tool ist schreibgeschützt**. Keine der Änderungen an Vorlagen, CSS oder Daten wird im Repository gespeichert.

Um schnell mit Anpassungen zu experimentieren`scg:showIde` muss die Eigenschaft zum Inhalts-JCR-Knoten der Komponentenseite hinzugefügt und auf „true“ gesetzt werden.

Verwenden Sie die Komponente Kommentare als Beispiel für die Autoren- oder Veröffentlichungsinstanz, die mit Administratorrechten angemeldet ist:

1. Zu [CRXDE Lite navigieren](../../help/sites-developing/developing-with-crxde-lite.md)

   Beispiel: [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

1. Wählen Sie den `jcr:content` der Komponente aus

   Zum Beispiel: `/content/community-components/en/comments/jcr:content`

1. Eigenschaft hinzufügen

   * **Name** `scg:showIde`
   * **Typ** `String`
   * **Wert** `true`

1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Laden Sie die Seite Kommentare im Handbuch neu.

   [http://localhost:4503/content/community-components/en/comments.html](http://localhost:4503/content/community-components/en/comments.html)

1. Beachten Sie, dass es jetzt drei Registerkarten für Vorlagen, CSS und Daten gibt.

![community-component5](assets/community-component5.png)

![community-component6](assets/community-component6.png)

### Registerkarte „Vorlagen“ {#templates-tab}

Wählen Sie die Registerkarte Vorlagen aus, um die mit der Komponente verknüpften Vorlagen anzuzeigen.

Mit dem Vorlageneditor können lokale Bearbeitungen kompiliert und auf die Beispielkomponenteninstanz oben auf der Seite angewendet werden, ohne dass die Komponente im Repository betroffen ist.

Wenn Sie den Compiler für lokale Bearbeitungen ausführen, werden alle Fehler hervorgehoben, indem Sie einen Punkt in den Rinnstein platzieren und den Text rot markieren.

### Registerkarte CSS {#css-tab}

Wählen Sie die Registerkarte CSS aus, um das mit der Komponente verknüpfte CSS anzuzeigen.

Wenn eine Komponente aus mehreren Komponenten zusammengesetzt ist, können einige CSS-Elemente unter einer der anderen Komponenten aufgeführt werden.

Der CSS-Editor ermöglicht das Ändern des CSS und dessen Anwendung auf die Beispielkomponenteninstanz oben auf der Seite.

Sie können eine Regel auswählen, um die Teile des DOM mithilfe dieser Regel hervorzuheben, indem Sie neben der Regel im Rinnstein klicken.

### Registerkarte „Daten“ {#data-tab}

Wählen Sie die Registerkarte Daten aus, um die .social.json-Endpunktdaten anzuzeigen. Diese Daten können bearbeitet werden und werden auf die Beispielkomponenteninstanz angewendet.

Syntaxfehler können in der Rinne markiert und im Editor hervorgehoben werden.
