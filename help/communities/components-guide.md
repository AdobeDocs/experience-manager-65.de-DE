---
title: Handbuch der Community-Komponenten
seo-title: Handbuch der Community-Komponenten
description: Ein interaktives Entwicklungstool für die ersten Schritte mit dem Framework für soziale Komponenten (SCF)
seo-description: Ein interaktives Entwicklungstool für die ersten Schritte mit dem Framework für soziale Komponenten (SCF)
uuid: 120e56d1-b93c-4f92-bab4-6bb5e40e0ddf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a777a3f1-b39f-4d90-b9b6-02d3e321a86f
translation-type: tm+mt
source-git-commit: 3da113e88784def54e0a94e280bf1a965de015ed
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 3%

---


# Handbuch der Community-Komponenten  {#community-components-guide}

Das Handbuch &quot;Community Components&quot;ist ein interaktives Entwicklungstool für den Rahmen für [soziale Komponenten (SCF)](scf.md). Es bietet eine Liste der verfügbaren AEM Communities-Komponenten oder der komplexeren Funktionen, die aus mehreren Komponenten bestehen.

Neben den grundlegenden Informationen für jede Komponente ermöglicht das Handbuch Experimente darüber, wie die SCF-Komponenten/-Funktionen funktionieren und wie sie konfiguriert oder angepasst werden können.

Weitere Informationen zu Entwicklungserfordernissen für die einzelnen Komponenten finden Sie unter [Feature und Component Essentials](essentials.md).

## Erste Schritte {#getting-started}

Das Handbuch ist für die Verwendung in Entwicklungs-Installationen von Autoreninstanzen (localhost:4502) und Veröffentlichungsinstanzen (localhost:4503) vorgesehen.

Die Website &quot;Community-Komponenten&quot;finden Sie unter

* [https://&lt;server>:&lt;port>/content/community-components/en.html](http://localhost:4502/content/community-components/en.html)

Die Interaktionen mit den Communities-Komponenten variieren je nach:

* Der Server (Autor oder Veröffentlichungsserver).
* Gibt an, ob der Site-Besucher angemeldet ist.
* Wenn Sie sich angemeldet haben, werden die dem Mitglied zugewiesenen Rechte angezeigt.
* Gibt an, ob der Standard-SRP, [JSRP](jsrp.md), verwendet wird.

Wenn Sie beim Autor in den Bearbeitungsmodus wechseln möchten, fügen Sie nach dem Servernamen entweder `editor.html` oder `cf#` als erstes Pfadsegment ein:

* Standard-Benutzeroberfläche:

   [https://&lt;server>:&lt;port>/editor.html/content/community-components/en.html](http://localhost:4502/editor.html/content/community-components/en.html)

* Klassische Benutzeroberfläche:

   [https://&lt;server>:&lt;port>/cf#/content/community-components/en.html](http://localhost:4502/cf#/content/community-components/en.html)

>[!NOTE]
>
>Beim Autor im Bearbeitungsmodus sind die Links auf einer Seite nicht aktiv.
>
>Um zu einer Komponentenseite zu navigieren, wählen Sie zunächst den Vorschau-Modus aus, um die Links zu aktivieren.
>
>Kehren Sie bei angezeigter Komponentenseite zum Bearbeitungsmodus zurück, um das Dialogfeld der Komponente zu öffnen.
>
>For general authoring information, view the [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).
>
>If not familiar with AEM, view the documentation on [basic handling](../../help/sites-authoring/basic-handling.md).


### Startseite {#home-page}

Das Handbuch enthält eine Liste der SCF-Komponenten, die für die Vorschau und das Erstellen von Prototypen auf der linken Seite verfügbar sind.

Komponentenhandbuch, wie auf einer Autoreninstanz im Bearbeitungsmodus angezeigt:

![community-component1](assets/community-component1.png)

## Komponentenseiten {#component-pages}

Wählen Sie eine Komponente aus der Liste links auf der Seite aus.

![community-component-pages](assets/community-component2.png)

Der Hauptteil des Handbuchs wird angezeigt:

1. Titel: Der Name der ausgewählten Komponente
1. [Clientseitige Bibliotheken](#client-side-libraries): Eine Liste einer oder mehrerer erforderlicher Kategorien
1. [Einschließlich](scf.md#add-or-include-a-communities-component): Wenn die Komponente dynamisch eingeschlossen werden kann, kann der Status im Bearbeitungsmodus des Autors umgeschaltet werden:

   * Wenn der Text hinzugefügt wird, wird Folgendes angezeigt: &quot;Diese Komponente wird über ihren par-Knoten eingeschlossen.&quot;
   * Wenn der Text einbezogen wird, wird Folgendes angezeigt: &quot;Diese Komponente wird dynamisch einbezogen.&quot;
   * Ist dies nicht möglich, wird kein Text angezeigt

1. Beispielkomponente oder -funktion: eine aktive Instanz der Komponente oder Funktion. Wenn eine Komponente geändert wird, kann sie durch Änderungen an den Vorlagen, CSS und Daten im Abschnitt &quot;Registerkarte&quot;geändert werden.

>[!NOTE]
>
>Nachdem Sie eine Auswahl auf der linken Seite getroffen haben, wird die Komponente unter und nicht neben der Auflistung der Komponenten angezeigt, wenn das Browserfenster zu schmal ist.

### Autoreninteraktionen {#author-interactions}

Wenn Sie das Handbuch für eine Autoreninstanz verwenden, können Sie die Konfiguration einer Komponente durch Öffnen des Dialogfelds durchführen. Informationen für Entwickler finden Sie im Abschnitt [Komponenten und Funktionen](essentials.md) der Dokumentation, während die Dialogeinstellungen im Abschnitt [Communities Komponenten](author-communities.md) für Autoren beschrieben werden.

Im Handbuch &quot;Community-Komponenten&quot;werden einige Einstellungen für das Komponentendialogfeld mit dem Status &quot; [Einschließen](scf.md#add-or-include-a-communities-component) &quot;überlagert. Um zwischen der vorhandenen Ressource oder einer dynamisch eingeschlossenen Ressource zu wechseln, wählen Sie im Bearbeitungsmodus sowohl die Komponente als auch den inklusiven Text aus und klicken Sie bei gedrückter Dublette, um das Bearbeitungsdialogfeld zu öffnen:

![community-component3](assets/community-component3.png)

Auf der Registerkarte **Vorlagen** :

![community-component4](assets/community-component4.png)

* **Untergeordnete Komponente mit sling:include einschließen**

   Wenn diese Option deaktiviert ist, verwendet das Komponentenleitfaden die vorhandene Ressource im Repository (einen jcr-Knoten, der einem par-Knoten untergeordnet ist).

   * angezeigter Text: &quot;Diese Komponente wird über ihren par-Knoten eingeschlossen.&quot;

   Wenn diese Option aktiviert ist, verwendet das Komponentenleitfaden sling, um dynamisch eine Komponente des resourceType des untergeordneten Knotens (nicht vorhandene Ressource) einzuschließen.

   * angezeigter Text: &quot;Diese Komponente wird dynamisch einbezogen.&quot;

   Diese Option ist standardmäßig deaktiviert.

### Veröffentlichungsinteraktionen {#publish-interactions}

Bei Verwendung des Handbuchs in einer Veröffentlichungsinstanz können die Komponenten und Funktionen als Site-Besucher (nicht angemeldet) und als Mitglieder mit verschiedenen Berechtigungen beim Anmelden angezeigt werden.

>[!NOTE]
>
>Wenn die SRP standardmäßig auf [JSRP](jsrp.md)festgelegt ist, ist UGC, die in der Veröffentlichungsinstanz eingegeben wird, nur bei der Veröffentlichung sichtbar und *nicht* in der [Moderationskonsole](moderate-ugc.md) auf der Autoreninstanz sichtbar.

## Client-seitige Bibliotheken {#client-side-libraries}

Die clientseitigen Bibliotheken (clientlibs), die für jede Komponente aufgelistet sind, sind diejenigen, auf die beim Platzieren der Komponente auf einer Seite verwiesen werden *muss* . Die clientlibs bieten eine Möglichkeit zum Verwalten und Optimieren des Downloads von Javascript und CSS, die zur Wiedergabe der Komponente im Browser verwendet werden.

Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

## Personifikation {#impersonation}

Verwenden Sie für die Autoreninstanz, bei der einer oft als Administrator oder Entwickler angemeldet ist, das Textfeld links neben der Schaltfläche **[!UICONTROL Eigenschaftswechsel]** , um den Benutzernamen einzugeben oder aus der Pulldown-Liste auszuwählen, und klicken Sie dann auf die Schaltfläche. Klicken Sie auf &quot;Zurück&quot;, um den Identitätswechsel zu signalisieren und zu beenden.

Die Instanz im Veröffentlichungsmodus muss nicht imitiert werden. Verwenden Sie einfach den Link Anmelden/Abmelden, um verschiedene Benutzer, wie z.B. die [Demobenutzer](tutorials.md#demo-users), zu imitieren.

## Anpassung {#customization}

Bei Aktivierung steht jede SCF-Komponente für die Prototypisierung möglicher Anpassungen zur Verfügung, indem die Vorlage, das CSS und die Daten der Komponente vorübergehend geändert werden.

### Aktivieren der Anpassung {#enabling-customization}

>[!NOTE]
>
>**Dieses Tool ist schreibgeschützt**. Keine der an Vorlagen, CSS oder Daten vorgenommenen Änderungen werden im Repository gespeichert.

Um schnell mit Anpassungen zu experimentieren, muss die `scg:showIde`Eigenschaft dem content-JCR-Knoten der Komponentenseite hinzugefügt und auf true eingestellt werden.

Verwenden der Kommentarkomponente als Beispiel für die Autor- oder Veröffentlichungsinstanz, die mit Administratorberechtigungen angemeldet ist:

1. Zur [CRXDE Lite navigieren](../../help/sites-developing/developing-with-crxde-lite.md)

   For example, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

1. Wählen Sie den `jcr:content` Knoten der Komponente

   Beispiel: `/content/community-components/en/comments/jcr:content`

1. Eigenschaft hinzufügen

   * **Name** `scg:showIde`
   * **Typ** `String`
   * **Wert** `true`

1. Select **[!UICONTROL Save All]**
1. Laden Sie die Seite &quot;Kommentare&quot;im Handbuch erneut.

   [http://localhost:4503/content/community-components/en/comments.html](http://localhost:4503/content/community-components/en/comments.html)

1. Beachten Sie, dass es jetzt 3 Registerkarten für Vorlagen, CSS und Daten gibt.

![community-component5](assets/community-component5.png)

![community-component6](assets/community-component6.png)

### Registerkarte &quot;Vorlagen&quot; {#templates-tab}

Wählen Sie die Registerkarte &quot;Vorlagen&quot;, um die mit der Komponente verknüpften Vorlagen anzuzeigen.

Mit dem Vorlageneditor können lokale Bearbeitungen kompiliert und auf die Beispielkomponenteninstanz oben auf der Seite angewendet werden, ohne dass die Komponente im Repository betroffen ist.

Wenn Sie die Kompilierung auf lokalen Bearbeitungen ausführen, werden alle Fehler hervorgehoben, indem Sie einen Punkt in die Bundstege setzen und den Text rot markieren.

### CSS-Registerkarte {#css-tab}

Wählen Sie die Registerkarte &quot;CSS&quot;, um die mit der Komponente verknüpfte CSS anzuzeigen.

Wenn eine Komponente aus mehreren Komponenten besteht, kann ein Teil des CSS unter einer der anderen Komponenten aufgeführt werden.

Mit dem CSS-Editor kann das CSS geändert und auf die Beispielkomponenteninstanz oben auf der Seite angewendet werden.

Eine Regel kann ausgewählt werden, um die Teile des DOM mithilfe dieser Regel hervorzuheben, indem Sie neben der Regel im Bundstegen klicken.

### Registerkarte &quot;Daten&quot; {#data-tab}

Wählen Sie die Registerkarte &quot;Daten&quot;, um die Endpunktdaten &quot;.social.json&quot;anzuzeigen. Diese Daten können bearbeitet werden und werden auf die Beispielkomponenteninstanz angewendet.

Syntaxfehler können in der Bundstege markiert und im Editor hervorgehoben werden.
