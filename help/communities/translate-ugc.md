---
title: Übersetzen von benutzergenerierten Inhalten
description: Erfahren Sie, wie die Übersetzung von benutzergenerierten Inhalten es Besuchenden und Mitgliedern einer Website ermöglicht, eine globale Community zu erleben, indem sie Sprachbarrieren beseitigen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: ac54f06e-1545-44bb-9f8f-970f161ebb72
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 3%

---

# Übersetzen von benutzergenerierten Inhalten {#translating-user-generated-content}

Die Übersetzungsfunktion für Adobe Experience Manager (AEM) Communities erweitert das Konzept [Übersetzen von Seiteninhalten](../../help/sites-administering/translation.md) auf die benutzergenerierten Inhalte (User-Generated Content, UGC), die mithilfe von Social Component Framework[Komponenten (SCF) auf Community](scf.md)Sites veröffentlicht werden.

Die Übersetzung von UGC ermöglicht es Besuchenden und Mitgliedern von Websites, eine globale Community zu erleben, indem sie Sprachbarrieren beseitigen.

Nehmen wir als Beispiel an:

* Ein französisches Mitglied veröffentlicht ein Rezept auf Französisch im Community Forum einer multinationalen Kochwebsite.
* Ein anderes japanisches Mitglied verwendet die Übersetzungsfunktion, um die Übersetzung des Rezepts aus dem Französischen ins Japanische in Trigger zu bringen.
* Nachdem sie das Rezept auf Japanisch gelesen hat, postet das Mitglied aus Japan dann einen Kommentar auf Japanisch.
* Das französische Mitglied übersetzt den japanischen Kommentar mithilfe der Übersetzungsfunktion ins Französische.
* Globale Kommunikation.

## Überblick {#overview}

In diesem Abschnitt wird erläutert, wie der Übersetzungs-Service mit benutzergenerierten Inhalten zusammenarbeitet. Es wird auch davon ausgegangen, dass Sie wissen, wie Sie AEM mit einem [Übersetzungsdienstleister](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) verbinden und diesen Dienst in eine Website integrieren können, indem Sie ein [Framework für die Übersetzungsintegration](../../help/sites-administering/tc-tic.md) konfigurieren.

Wenn ein Übersetzungsdienstleister mit der Website verknüpft ist, verwaltet jede Sprachkopie der Website ihre eigenen Threads von UGC, die über SCF-Komponenten wie Kommentare veröffentlicht werden.

Wenn zusätzlich zum Übersetzungsdienstleister eine Übersetzungsintegration konfiguriert ist, kann jede Sprachkopie der Website einen einzigen Thread von benutzergenerierten Inhalten gemeinsam nutzen und so eine globale Kommunikation über Sprachkopien hinweg sicherstellen. Anstelle eines nach Sprache getrennten Diskussions-Threads ermöglicht der konfigurierte [globale freigegebene ](#global-translation-of-ugc)) die Anzeige des gesamten Threads, unabhängig davon, von welcher Sprachkopie er angezeigt wird. Darüber hinaus können mehrere Übersetzungsintegrationskonfigurationen konfiguriert werden, die unterschiedliche globale Shared Stores für eine logische Gruppierung globaler Teilnehmer angeben, z.B. nach Regionen.

## Der standardmäßige Übersetzungs-Service {#the-default-translation-service}

AEM Communities enthält eine [Testlizenz](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) für einen [Standard-Übersetzungs-Service](../../help/sites-administering/tc-msconf.md) der für mehrere Sprachen aktiviert ist.

Beim [Erstellen einer Community](sites-console.md)Site wird der standardmäßige Übersetzungs-Service aktiviert, wenn `Allow Machine Translation` im Unterbedienfeld [ÜBERSETZUNG](sites-console.md#translation) aktiviert wird.

>[!CAUTION]
>
>Der standardmäßige Übersetzungs-Service dient nur zur Demonstration.
>
>Für ein Produktionssystem ist ein lizenzierter Übersetzungs-Service erforderlich. Wenn er nicht lizenziert ist, sollte der standardmäßige Übersetzungs-Service [deaktiviert) ](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license-geometrixx-outdoors).

## Globale Übersetzung von UGC {#global-translation-of-ugc}

Wenn eine Website über mehrere [Sprachkopien](../../help/sites-administering/tc-prep.md) verfügt, erkennt der standardmäßige Übersetzungsdienst nicht, dass benutzergenerierte Inhalte, die auf einer Website eingegeben wurden, mit benutzergenerierten Inhalten in Verbindung stehen können, die auf einer anderen Website eingegeben wurden. Dies gilt, wenn der benutzergenerierte Inhalt von derselben Komponente (der Sprachkopie der Seite, die die Komponente enthält) generiert wird.

Es ist ähnlich wie Gruppen von Menschen, die ein Thema diskutieren. Sie sind sich der Kommentare, die in anderen Gruppen als ihrer eigenen gemacht werden, nicht bewusst, im Vergleich zu allen in einer großen Gruppe, die an einem Gespräch teilnehmen.

Wenn „eine Gruppenkonversation“ gewünscht wird, ist es möglich, die globale Übersetzung auf einer Website mit mehreren Sprachkopien zu aktivieren, sodass der gesamte Thread unabhängig davon sichtbar ist, von welcher Sprachkopie er angezeigt wird.

Wenn beispielsweise ein Forum auf der Basis-Website eingerichtet, Sprachkopien erstellt und die globale Übersetzung aktiviert wurde, würde ein in einer Sprachkopie erstelltes Thema in allen Sprachkopien angezeigt. Dies gilt für alle Antworten, unabhängig davon, von welcher Sprachkopie die Antwort eingegeben wurde. Das Ergebnis wäre, dass das Thema und sein gesamter Thread von Antworten unabhängig davon sichtbar wären, von welcher Sprachkopie das Thema angezeigt wird.

>[!CAUTION]
>
>Alle benutzergenerierten Inhalte, die vor der globalen Übersetzung existierten, sind nicht mehr sichtbar.
>
>Während sich der benutzergenerierte Inhalt noch im [Common Store](working-with-srp.md) befindet, befindet er sich unter dem sprachspezifischen Speicherort des benutzergenerierten Inhalts, während neue Inhalte, die nach der Konfiguration der globalen Übersetzung hinzugefügt wurden, aus dem globalen freigegebenen Speicherort abgerufen werden.
>
>Es gibt kein Migrations-Tool zum Verschieben oder Zusammenführen sprachspezifischer Inhalte in den globalen freigegebenen Speicher.

### Konfiguration für Übersetzungsintegration {#translation-integration-configuration}

So erstellen Sie eine Übersetzungsintegration, die einen Connector für den Übersetzungsdienst mit der Website in der Autoreninstanz integriert:

* Als Administrator anmelden
* Vom [Hauptmenü](http://localhost:4502/)
* Wählen Sie **[!UICONTROL Tools]**
* Wählen Sie **[!UICONTROL Vorgänge]**
* Wählen Sie **[!UICONTROL Cloud]**
* **[!UICONTROL Cloud Service auswählen]**
* Scrollen Sie nach unten **[!UICONTROL Übersetzungsintegration]**

  ![translation-integration](assets/translation-integration.png)

* Wählen Sie **[!UICONTROL Konfigurationen anzeigen]**

  ![show-configuration](assets/translation-integration1.png)

* Wählen Sie `[+]` Symbol neben **[!UICONTROL Verfügbare Konfigurationen]** aus, um eine Konfiguration zu erstellen.

#### Dialogfeld „Konfiguration erstellen“ {#create-configuration-dialog}

![create-configuration](assets/translation-integration2.png)

* **[!UICONTROL Übergeordnete Konfiguration]**

  (Erforderlich) Lassen Sie normalerweise als Standard. Der Standardwert ist `/etc/cloudservices/translation`.

* **[!UICONTROL Titel]**

  (Erforderlich) Geben Sie einen Anzeigetitel Ihrer Wahl ein. Kein Standardwert.

* **[!UICONTROL Name]**

  (Optional) Geben Sie einen Namen für die Konfiguration ein. Standard ist ein Knotenname, der auf dem Titel basiert.

* Wählen Sie **[!UICONTROL Erstellen]** aus

#### Dialogfeld „Übersetzungskonfiguration“ {#translation-config-dialog}

![configuration-dialog](assets/translation-integration3.png)

Detaillierte Anweisungen finden Sie unter [Erstellen einer Konfiguration für die Übersetzungsintegration](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration).

* Registerkarte **[!UICONTROL Sites]**: kann als Standard beibehalten.

* Registerkarte **[!UICONTROL Communities]**:
   * **[!UICONTROL Übersetzungsanbieter]**
Wählen Sie den Übersetzungsanbieter aus der Dropdown-Liste aus. Die Standardeinstellung ist `microsoft`, der Testdienst.

   * **[!UICONTROL Inhaltskategorie]**
Wählen Sie eine Kategorie aus, die den zu übersetzenden Inhalt beschreibt. Der Standardwert ist `General.`

   * **[!UICONTROL Wählen Sie ein Gebietsschema…]**
(Optional) Wenn Sie ein Gebietsschema zum Speichern von benutzergenerierten Inhalten auswählen, werden Beiträge aus allen Sprachkopien in einer globalen Konversation angezeigt. Standardmäßig wählen Sie das Gebietsschema für die [Basissprache](sites-console.md#translation) für die Website. Durch Auswahl von `No Common Store` wird die globale Übersetzung deaktiviert. Standardmäßig ist die globale Übersetzung deaktiviert.

* Registerkarte **[!UICONTROL Assets]**: kann als Standard beibehalten werden.
* Wählen Sie **[!UICONTROL OK]** aus.

#### Aktivierung {#activation}

Der neue Cloud-Service für die Übersetzungsintegration muss für die Publish-Umgebung aktiviert werden. Wenn der Aktivierungs-Workflow mit einer Website verknüpft ist (sofern noch nicht aktiviert), wird er aufgefordert, diese Cloud Service-Konfiguration zu veröffentlichen, wenn die Seite, mit der sie verknüpft ist, veröffentlicht wird.

## Verwalten von Übersetzungseinstellungen {#managing-translation-settings}

>[!NOTE]
>
>**Bevorzugte Sprache**
>
>Wenn festgestellt wird, ob der Beitrag in einer anderen Sprache als der bevorzugten Sprache verfasst ist, muss die bevorzugte Sprache des Site-Besuchers festgelegt werden.
>
>Die bevorzugte Sprache ist die Spracheinstellung, die im Profil eines Benutzers festgelegt wird, wenn der Site-Besucher angemeldet ist und eine Spracheinstellung angegeben hat.
>
>Wenn der Site-Besucher anonym ist oder keine Sprachvoreinstellung in seinem Profil angegeben hat, ist die bevorzugte Sprache die Basissprache der Seitenvorlage.

### Benutzerpräferenz {#user-preference}

#### Benutzerprofil {#user-profile}

Alle Communities-Sites bieten ein Benutzerprofil, das angemeldete Mitglieder bearbeiten können, um sich gegenüber der Community zu identifizieren und ihre Voreinstellungen festzulegen.

Eine dieser Einstellungen ist, ob Community-Inhalte immer in der bevorzugten Sprache angezeigt werden sollen. Standardmäßig ist die Einstellung nicht festgelegt und standardmäßig auf die Systemeinstellung festgelegt. Der Benutzer kann die Einstellung entweder auf Ein oder auf Aus ändern, um die Systemeinstellung zu überschreiben.

Wenn Seiten automatisch in die bevorzugte Sprache des Benutzers übersetzt werden, steht die Benutzeroberfläche zum Anzeigen des Originaltextes und zum Verbessern der Übersetzung weiterhin zur Verfügung.

![user-profile](assets/translation-integration4.png)

### Community-Site-Einstellungen {#community-site-setting}

Wenn eine Community-Site erstellt wird, kann die Übersetzungsoption aktiviert und konfiguriert werden. Die Übersetzungseinstellung ist für Inhalte aktiv, die anonyme Site-Besucher anzeigen können, wird jedoch durch die Profileinstellung des Benutzers überschrieben.
