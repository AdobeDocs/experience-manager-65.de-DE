---
title: Übersetzen benutzergenerierter Inhalte
seo-title: Übersetzen benutzergenerierter Inhalte
description: Funktionsweise der Übersetzungsfunktion
seo-description: Funktionsweise der Übersetzungsfunktion
uuid: 7ee3242c-2aca-4787-a60d-b807161401ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: bfaf80c5-448b-47fb-9f22-57ee0eb169b2
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 2%

---


# Übersetzen benutzergenerierter Inhalte {#translating-user-generated-content}

Die Übersetzungsfunktion für AEM Communities erweitert das Konzept der [Übersetzung von Seiteninhalten](../../help/sites-administering/translation.md) auf die benutzergenerierten Inhalte (UGC), die mithilfe von SCF-Komponenten [(](scf.md)Social Component Framework) an Community-Sites veröffentlicht werden.

Die Übersetzung von UGC ermöglicht es Site-Besuchern und -Mitgliedern, eine globale Community zu erleben, indem sie Sprachbarrieren beseitigen.

Beispiel:

* Ein französisches Mitglied postet ein französisches Rezept im Gemeinschaftsforum einer multinationalen Kochwebsite.
* Ein anderes japanisches Mitglied verwendet die Übersetzungsfunktion, um die Übersetzung des Rezepts vom Französischen ins Japanische auszulösen.
* Nach dem Lesen des Rezepts auf Japanisch, das Mitglied aus Japan dann einen Kommentar auf Japanisch.
* Das Mitglied aus Frankreich verwendet die Übersetzungsfunktion, um den japanischen Kommentar ins Französische zu übersetzen.
* Globale Kommunikation.

## Überblick {#overview}

In diesem Abschnitt der Dokumentation wird insbesondere erläutert, wie der Übersetzungsdienst mit UGC funktioniert. Dabei wird erläutert, wie AEM mit einem [Übersetzungsdienst](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) verbunden und dieser Dienst in eine Website integriert werden kann, indem ein [Übersetzungsintegrationsframework](../../help/sites-administering/tc-tic.md)konfiguriert wird.

Wenn ein Übersetzungs-Dienstleister mit der Site verknüpft ist, unterhält jede Sprachkopie der Site eigene Threads von UGC, die über SCF-Komponenten wie Kommentare veröffentlicht werden.

Wenn ein Framework für die Integration von Übersetzungen zusätzlich zu dem Dienstleister für Übersetzungen konfiguriert wird, kann für jede Sprachkopie der Site ein einziger Thread von UGC verwendet werden, um eine globale Kommunikation über Sprachkopien zu ermöglichen. Anstelle eines nach Sprache getrennten Diskussionsthread ermöglicht der konfigurierte [globale gemeinsame Speicher](#global-translation-of-ugc) , dass der gesamte Thread sichtbar ist, unabhängig davon, von welcher Sprachkopie er angezeigt wird. Darüber hinaus können mehrere Konfigurationen für die Integration von Übersetzungen konfiguriert werden, um verschiedene globale freigegebene Stores für eine logische Gruppierung globaler Teilnehmer anzugeben, z. B. nach Regionen.

## Der Standard-Übersetzungsdienst {#the-default-translation-service}

AEM Communities verfügt über eine [Testlizenz](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) für einen [Standard-Übersetzungsdienst](../../help/sites-administering/tc-msconf.md) , der für mehrere Sprachen aktiviert ist.

Beim [Erstellen einer Community-Site](sites-console.md)ist der Standard-Übersetzungsdienst aktiviert, wenn `Allow Machine Translation` er im Unterfeld [TRANSLATION](sites-console.md#translation) überprüft wird.

>[!CAUTION]
>
>Der Standard-Übersetzungsdienst dient nur zur Veranschaulichung.
>
>Für ein Produktionssystem ist ein lizenzierter Übersetzungsdienst erforderlich. Ist keine Lizenz vorhanden, sollte der Standard-Übersetzungsdienst [deaktiviert](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license-geometrixx-outdoors)werden.

## Globale Übersetzung von UGC {#global-translation-of-ugc}

Wenn eine Website mehrere [Sprachkopien](../../help/sites-administering/tc-prep.md)hat, erkennt der Standard-Übersetzungsdienst nicht, dass auf einer Site eingegebener UGC mit einem in einer anderen Site eingegebenen UGC in Beziehung stehen kann, als ob der UGC im Wesentlichen von derselben Komponente (der Sprachkopie der Seite, die die Komponente enthält) generiert wird.

Es ähnelt Gruppen von Menschen, die ein Thema diskutieren, die sich nicht bewusst sind, dass Kommentare in anderen Gruppen als ihren eigenen abgegeben werden, im Vergleich zu allen in einer großen Gruppe, die an einem Gespräch teilnimmt.

Wenn &quot;eine Gruppenunterhaltung&quot;gewünscht wird, ist es möglich, globale Übersetzungen über eine Website mit mehreren Sprachkopien zu aktivieren, sodass der gesamte Thread sichtbar ist, unabhängig davon, von welcher Sprachkopie er angezeigt wird.

Wenn z. B. ein Forum auf der Basis-Site eingerichtet wurde, Sprachkopien erstellt wurden und globale Übersetzung aktiviert wurde, wird ein Thema, das im Forum veröffentlicht wurde, in einer Sprachkopie in allen Sprachkopien angezeigt. Dasselbe gilt für alle Antworten, unabhängig davon, aus welcher Sprache die Antwort eingegeben wurde. Das Ergebnis wäre, dass das Thema und sein gesamter Thread mit Antworten sichtbar wären, unabhängig davon, aus welcher Sprache das Thema angezeigt wird.

>[!CAUTION]
>
>Alle UGC, die vor der globalen Übersetzung existierten, sind nicht mehr sichtbar.
>
>Während sich das UGC noch im [gemeinsamen Speicher](working-with-srp.md)befindet, befindet es sich unter dem sprachspezifischen UGC-Speicherort, während neue Inhalte, die nach der Konfiguration der globalen Übersetzung hinzugefügt wurden, vom globalen freigegebenen Speicherort abgerufen werden.
>
>Es gibt kein Migrationswerkzeug zum Verschieben oder Zusammenführen sprachspezifischer Inhalte in den globalen gemeinsamen Speicher.

### Konfiguration für Übersetzungsintegration {#translation-integration-configuration}

So erstellen Sie eine neue Translation Integration, die einen Translation Service-Connector mit der Website in der Autoreninstanz integriert:

* Anmelden als Administrator
* Über das [Hauptmenü](http://localhost:4502/)
* Wählen Sie **[!UICONTROL Tools]**
* Vorgänge **[!UICONTROL auswählen]**
* **[!UICONTROL Cloud auswählen]**
* **[!UICONTROL Cloud Services auswählen]**
* Bildlauf nach unten zur **[!UICONTROL Übersetzungsintegration]**

   ![translation-integration](assets/translation-integration.png)

* Konfigurationen **[!UICONTROL anzeigen auswählen]**

   ![show-configuration](assets/translation-integration1.png)

* Klicken Sie auf `[+]` das Symbol neben **[!UICONTROL Verfügbare Konfigurationen]** , um eine neue Konfiguration zu erstellen.

#### Dialogfeld &quot;Konfiguration erstellen&quot; {#create-configuration-dialog}

![create-configuration](assets/translation-integration2.png)

* **[!UICONTROL Übergeordnete Konfiguration]**

   (Erforderlich) Lassen Sie in der Regel als Standard. Der Standardwert ist `/etc/cloudservices/translation`.

* **[!UICONTROL Titel]**

   (Erforderlich) Geben Sie einen Anzeigentitel Ihrer Wahl ein. Kein Standardwert.

* **[!UICONTROL Name]**

   (Optional) Geben Sie einen Namen für die Konfiguration ein. Standard ist ein Knotenname, der auf dem Titel basiert.

* Wählen Sie **[!UICONTROL Erstellen]**

#### Dialogfeld &quot;Konvertierungskonfiguration&quot; {#translation-config-dialog}

![configuration-dialog](assets/translation-integration3.png)

Ausführliche Anweisungen finden Sie unter [Erstellen einer Konfiguration für die Integration von Übersetzungen](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration)

* **[!UICONTROL Registerkarte &quot;Sites]** &quot;: kann als Standard beibehalten werden.

* **[!UICONTROL Registerkarte &quot;Communities]** &quot;:
   * **[!UICONTROL Übersetzungsanbieter]** Wählen Sie den Übersetzungsanbieter aus der Dropdown-Liste. Der Standardwert ist 
`microsoft`, den Testdienst.

   * **[!UICONTROL Content Kategorie]** Wählen Sie eine Kategorie, die die zu übersetzenden Inhalte beschreibt. Der Standardwert ist 
`General.`

   * **[!UICONTROL Gebietsschema auswählen...]**
(Optional) Durch Auswahl eines Gebietsschemas zum Speichern von UGC werden Beiträge aus allen Sprachkopien in einer globalen Konversation angezeigt. Wählen Sie standardmäßig das Gebietsschema für die [Basissprache](sites-console.md#translation) der Website aus. Durch Auswahl dieser Option `No Common Store` wird die globale Übersetzung deaktiviert. Standardmäßig ist die globale Übersetzung deaktiviert.

* **[!UICONTROL Registerkarte &quot;Assets]** &quot;: kann als Standard beibehalten werden.
* Wählen Sie **[!UICONTROL OK]** aus

#### Aktivierung {#activation}

Der neue Cloud-Dienst für die Integration von Übersetzungen muss in der Umgebung zur Veröffentlichung aktiviert werden. Wenn eine Verbindung zu einer Website hergestellt wird und diese noch nicht aktiviert ist, wird der Arbeitsablauf der Aktivierung aufgefordert, diese Cloud-Dienstkonfiguration zu veröffentlichen, sobald die zugehörige Seite veröffentlicht wird.

## Verwalten von Übersetzungseinstellungen {#managing-translation-settings}

>[!NOTE]
>
>**Bevorzugte Sprache**
>
>Um festzustellen, ob der Beitrag in einer anderen Sprache als der bevorzugten Sprache verfasst ist, muss die bevorzugte Sprache des Site-Besuchers festgelegt werden.
>
>Die bevorzugte Sprache ist die Spracheinstellung, die im Profil des Benutzers festgelegt wird, wenn der Site-Besucher angemeldet ist und eine Spracheinstellung festgelegt hat.
>
>Wenn der Site-Besucher anonym ist oder keine Spracheinstellung in seinem Profil angegeben hat, ist die bevorzugte Sprache die Basissprache der Seitenvorlage.

### Benutzereinstellungen {#user-preference}

#### Benutzerprofil {#user-profile}

Alle Communities-Sites bieten ein Profil, das von den angemeldeten Mitgliedern bearbeitet werden kann, um sich in der Community zu identifizieren und ihre Voreinstellungen festzulegen.

Eine dieser Einstellungen ist, ob Community-Inhalte immer in ihrer bevorzugten Sprache angezeigt werden sollen. Standardmäßig ist diese Einstellung nicht festgelegt und wird standardmäßig auf die Systemeinstellung angewendet. Der Benutzer kann die Einstellung entweder auf Ein oder Aus ändern und dadurch die Systemeinstellung überschreiben.

Wenn Seiten automatisch in die vom Benutzer bevorzugte Sprache übersetzt werden, wird die Benutzeroberfläche zum Anzeigen des Originaltextes und Verbessern der Übersetzung weiterhin zur Verfügung gestellt.

![user-Profil](assets/translation-integration4.png)

### Community-Site-Einstellung {#community-site-setting}

Wenn eine Community-Site erstellt wird, kann die Übersetzungsoption aktiviert und konfiguriert werden. Die Übersetzungseinstellung ist in Kraft, wenn anonyme Site-Besucher Ansicht haben können, wird jedoch durch die Benutzereinstellung &quot;Profil&quot;außer Kraft gesetzt.
