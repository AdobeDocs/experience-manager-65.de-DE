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
role: Admin
exl-id: ac54f06e-1545-44bb-9f8f-970f161ebb72
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 2%

---

# Übersetzen benutzergenerierter Inhalte {#translating-user-generated-content}

Die Übersetzungsfunktion für AEM Communities erweitert das Konzept der [Übersetzung von Seiteninhalten](../../help/sites-administering/translation.md) auf die benutzergenerierten Inhalte (UGC), die über die Komponenten [Social Component Framework (SCF) auf Community-Sites veröffentlicht werden](scf.md).

Die Übersetzung von UGC ermöglicht es Site-Besuchern und Mitgliedern, durch die Beseitigung von Sprachbarrieren eine globale Community zu erleben.

Beispiel:

* Ein Mitglied aus Frankreich postet ein Rezept in französischer Sprache in das Community-Forum einer multinationalen Kochwebsite.
* Ein anderes japanisches Mitglied verwendet die Übersetzungsfunktion, um die Übersetzung des Rezepts aus dem Französischen ins Japanische Trigger.
* Nach dem Lesen des Rezepts auf Japanisch, das Mitglied aus Japan dann einen Kommentar auf Japanisch.
* Das Mitglied aus Frankreich verwendet die Übersetzungsfunktion, um den japanischen Kommentar ins Französische zu übersetzen.
* Globale Kommunikation.

## Übersicht {#overview}

In diesem Abschnitt der Dokumentation wird insbesondere erläutert, wie der Übersetzungsdienst mit UGC arbeitet, während er eine Vorstellung davon erhält, wie er AEM mit einem [Übersetzungsdienstleister](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) verbindet und diesen Dienst in eine Website integriert, indem ein [Framework für die Übersetzungsintegration](../../help/sites-administering/tc-tic.md) konfiguriert wird.

Wenn ein Übersetzungsdienstleister mit der Site verknüpft ist, verwaltet jede Sprachkopie der Site eigene Threads von UGC, die über SCF-Komponenten wie Kommentare veröffentlicht werden.

Wenn ein Framework für die Übersetzungsintegration zusätzlich zum Übersetzungsdienstleister konfiguriert ist, ist es möglich, dass jede Sprachkopie der Site einen einzigen Thread von UGC gemeinsam nutzt, um so eine globale Kommunikation über Sprachkopien hinweg zu ermöglichen. Anstelle eines Diskussionsthreads, der nach Sprache getrennt ist, ermöglicht der konfigurierte [globale gemeinsame Speicher](#global-translation-of-ugc), dass der gesamte Thread sichtbar ist, unabhängig davon, von welcher Sprachkopie er angezeigt wird. Außerdem können mehrere Konfigurationen für die Integration von Übersetzungen konfiguriert werden, die verschiedene globale gemeinsame Stores für eine logische Gruppierung globaler Teilnehmer angeben, z. B. nach Regionen.

## Standardübersetzungsdienst {#the-default-translation-service}

AEM Communities enthält eine [Testlizenz](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) für einen [standardmäßigen Übersetzungsdienst](../../help/sites-administering/tc-msconf.md), der für mehrere Sprachen aktiviert ist.

Beim Erstellen einer Community-Site](sites-console.md) wird der standardmäßige Übersetzungsdienst aktiviert, wenn `Allow Machine Translation` im Unterbereich [ÜBERSETZUNG](sites-console.md#translation) aktiviert wird.[

>[!CAUTION]
>
>Der standardmäßige Übersetzungsdienst dient nur zur Veranschaulichung.
>
>Für ein Produktionssystem ist ein lizenzierter Übersetzungsdienst erforderlich. Wenn keine Lizenz erteilt wurde, sollte der standardmäßige Übersetzungsdienst [disabled](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license-geometrixx-outdoors) sein.

## Globale Übersetzung von UGC {#global-translation-of-ugc}

Wenn eine Website über mehrere [Sprachkopien](../../help/sites-administering/tc-prep.md) verfügt, erkennt der standardmäßige Übersetzungsdienst nicht, dass auf einer Site eingegebene benutzergenerierte Inhalte sich auf in einer anderen Site eingegebene benutzergenerierte Inhalte beziehen können, da der benutzergenerierte Inhalt im Wesentlichen von derselben Komponente generiert wird (die Sprachkopie der Seite, die die Komponente enthält).

Es ist ähnlich wie Gruppen von Menschen, die ein Thema diskutieren, die nicht wissen, dass Kommentare in anderen Gruppen als ihren eigenen gemacht werden, im Vergleich zu jedem in einer großen Gruppe, die an einem Gespräch teilnimmt.

Wenn &quot;eine Gruppenkonversation&quot;gewünscht wird, ist es möglich, eine globale Übersetzung auf einer Website mit mehreren Sprachkopien zu aktivieren, sodass der gesamte Thread unabhängig davon sichtbar ist, von welcher Sprachkopie er angezeigt wird.

Wenn beispielsweise ein Forum auf der Basis-Site eingerichtet wurde, Sprachkopien erstellt wurden und die globale Übersetzung aktiviert wurde, wird ein Thema, das im Forum veröffentlicht wurde und in einer Sprachkopie erstellt wurde, in allen Sprachkopien angezeigt. Dasselbe gilt für alle Antworten, unabhängig davon, von welcher Sprachkopie die Antwort eingegeben wurde. Das Ergebnis wäre, dass das Thema und der gesamte Thread mit Antworten sichtbar wären, unabhängig davon, von welcher Sprachkopie das Thema angezeigt wird.

>[!CAUTION]
>
>Alle UGC, die vor der globalen Übersetzung existierten, sind nicht mehr sichtbar.
>
>Während sich das UGC noch im [gemeinsamen Speicher](working-with-srp.md) befindet, befindet es sich unter dem sprachspezifischen UGC-Speicherort, während neue Inhalte, die nach der Konfiguration der globalen Übersetzung hinzugefügt wurden, vom globalen freigegebenen Speicherort abgerufen werden.
>
>Es gibt kein Migrationstool zum Verschieben oder Zusammenführen sprachspezifischer Inhalte in den globalen freigegebenen Speicher.

### Konfiguration für Übersetzungsintegration {#translation-integration-configuration}

So erstellen Sie eine neue Übersetzungsintegration, die einen Connector für Übersetzungsdienst mit der Website in der Autoreninstanz integriert:

* Als Administrator anmelden
* Von [Hauptmenü](http://localhost:4502/)
* Wählen Sie **[!UICONTROL Tools]**
* Wählen Sie **[!UICONTROL Vorgänge]** aus.
* Wählen Sie **[!UICONTROL Cloud]**
* Wählen Sie **[!UICONTROL Cloud Services]** aus.
* Scrollen Sie nach unten zu **[!UICONTROL Übersetzungsintegration]**

   ![Translation-Integration](assets/translation-integration.png)

* Wählen Sie **[!UICONTROL Konfigurationen anzeigen]** aus.

   ![show-configuration](assets/translation-integration1.png)

* Klicken Sie auf das Symbol `[+]` neben **[!UICONTROL Verfügbare Konfigurationen]**, um eine neue Konfiguration zu erstellen.

#### Dialogfeld &quot;Konfiguration erstellen&quot; {#create-configuration-dialog}

![create-configuration](assets/translation-integration2.png)

* **[!UICONTROL Übergeordnete Konfiguration]**

   (Erforderlich) Lassen Sie in der Regel als Standard. Der Standardwert ist `/etc/cloudservices/translation`.

* **[!UICONTROL Titel]**

   (Erforderlich) Geben Sie einen Anzeigetitel Ihrer Wahl ein. Kein Standardwert.

* **[!UICONTROL Name]**

   (Optional) Geben Sie einen Namen für die Konfiguration ein. Der Standardwert ist ein Knotenname, der auf dem Titel basiert.

* Wählen Sie **[!UICONTROL Erstellen]**

#### Dialogfeld &quot;Übersetzungskonfiguration&quot; {#translation-config-dialog}

![configuration-dialog](assets/translation-integration3.png)

Ausführliche Anweisungen finden Sie unter [Erstellen einer Konfiguration für die Übersetzungsintegration](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration)

* **** Sitestab: kann als Standard festgelegt werden.

* **** Communitiestab:
   * **[!UICONTROL Übersetzungsanbieter]**
Wählen Sie den Übersetzungsanbieter aus der Dropdown-Liste aus. Der Standardwert ist 
`microsoft`, den Testdienst.

   * **[!UICONTROL Inhaltskategorie]**
Wählen Sie eine Kategorie, die den zu übersetzenden Inhalt beschreibt. Der Standardwert ist 
`General.`

   * **[!UICONTROL Gebietsschema auswählen...]**
(Optional) Wenn Sie ein Gebietsschema zum Speichern von benutzergenerierten Inhalten auswählen, werden Beiträge aus allen Sprachkopien in einer globalen Konversation angezeigt. Standardmäßig wählen Sie das Gebietsschema für die [Basissprache](sites-console.md#translation) der Website. Wenn Sie `No Common Store` auswählen, wird die globale Übersetzung deaktiviert. Standardmäßig ist die globale Übersetzung deaktiviert.

* **** Assetstab: kann als Standard festgelegt werden.
* Wählen Sie **[!UICONTROL OK]** aus

#### Aktivierung {#activation}

Der neue Cloud-Service für die Übersetzungsintegration muss für die Veröffentlichungsumgebung aktiviert werden. Wenn eine Verbindung zu einer Website hergestellt wird und diese noch nicht aktiviert ist, wird der Aktivierungs-Workflow aufgefordert, diese Cloud Service-Konfiguration zu veröffentlichen, wenn die Seite, mit der sie verknüpft ist, veröffentlicht wird.

## Verwalten von Übersetzungseinstellungen {#managing-translation-settings}

>[!NOTE]
>
>**Bevorzugte Sprache**
>
>Um festzustellen, ob der Beitrag in einer anderen Sprache als der bevorzugten Sprache verfasst ist, muss die bevorzugte Sprache des Site-Besuchers festgelegt werden.
>
>Die bevorzugte Sprache ist die Sprachvoreinstellung, die in einem Benutzerprofil festgelegt wird, wenn der Site-Besucher angemeldet ist und eine Spracheinstellung festgelegt hat.
>
>Wenn der Besucher der Site anonym ist oder keine Spracheinstellung in seinem Profil angegeben hat, ist die bevorzugte Sprache die Basissprache der Seitenvorlage.

### Benutzerpräferenz {#user-preference}

#### Benutzerprofil {#user-profile}

Alle Communities-Sites bieten ein Benutzerprofil, das angemeldete Mitglieder bearbeiten können, um sich für die Community zu identifizieren und ihre Voreinstellungen festzulegen.

Eine dieser Einstellungen ist, ob Community-Inhalte immer in ihrer bevorzugten Sprache angezeigt werden sollen. Standardmäßig ist die Einstellung nicht festgelegt und standardmäßig auf die Systemeinstellung festgelegt. Der Benutzer kann die Einstellung entweder auf Ein oder Aus ändern und dadurch die Systemeinstellung überschreiben.

Wenn Seiten automatisch in die bevorzugte Sprache des Benutzers übersetzt werden, wird die Benutzeroberfläche für die Anzeige des Originaltextes und die Verbesserung der Übersetzung weiterhin zur Verfügung gestellt.

![user-profile](assets/translation-integration4.png)

### Community-Site-Einstellung {#community-site-setting}

Wenn eine Community-Site erstellt wird, kann die Übersetzungsoption aktiviert und konfiguriert werden. Die Übersetzungseinstellung gilt für Inhalte, die anonyme Site-Besucher anzeigen können, wird jedoch durch die Profileinstellung des Benutzers überschrieben.
