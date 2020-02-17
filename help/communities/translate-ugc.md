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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Übersetzen benutzergenerierter Inhalte {#translating-user-generated-content}

Die Übersetzungsfunktion für AEM Communities erweitert das Konzept der [Übersetzung von Seiteninhalten](../../help/sites-administering/translation.md) auf die benutzergenerierten Inhalte (UGC), die mithilfe von SCF-Komponenten ( [Social Component Framework) auf Community-Sites veröffentlicht werden](scf.md).

Die Übersetzung von UGC ermöglicht es Site-Besuchern und -Mitgliedern, eine globale Gemeinschaft zu erleben, indem Sprachbarrieren beseitigt werden.

Beispiel:

* Ein französisches Mitglied stellt ein französisches Rezept in das Gemeinschaftsforum einer multinationalen Kochwebsite ein
* Ein anderes japanisches Mitglied verwendet die Übersetzungsfunktion, um die Übersetzung des Rezeptes vom Französischen ins Japanische auszulösen
* Nachdem das Rezept auf Japanisch gelesen wurde, postet das japanische Mitglied einen Kommentar auf Japanisch
* Das Mitglied aus Frankreich verwendet die Übersetzungsfunktion, um den japanischen Kommentar ins Französische zu übersetzen
* Globale Kommunikation!

## Überblick {#overview}

In diesem Abschnitt der Dokumentation wird insbesondere erläutert, wie der Übersetzungsdienst mit UGC funktioniert. Dabei wird erläutert, wie AEM mit einem [Übersetzungsdienstleister](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) verbunden und dieser Dienst in eine Website integriert werden kann, indem ein [Übersetzungsintegrationsframework](../../help/sites-administering/tc-tic.md)konfiguriert wird.

Wenn ein Übersetzungsdienstleister mit der Site verknüpft ist, unterhält jede Sprachkopie der Site eigene Threads von UGC, die über SCF-Komponenten wie Kommentare veröffentlicht werden.

Wenn ein Framework für die Integration von Übersetzungen zusätzlich zum Übersetzungsdienstleister konfiguriert wird, kann für jede Sprachkopie der Site ein einziger Thread von UGC verwendet werden, um eine globale Kommunikation über Sprachkopien zu ermöglichen. Anstelle eines nach Sprache getrennten Diskussionsthread ermöglicht der konfigurierte [globale gemeinsame Speicher](#global-translation-of-ugc) , dass der gesamte Thread sichtbar ist, unabhängig davon, von welcher Sprachkopie er angezeigt wird. Darüber hinaus können mehrere Konfigurationen für die Integration von Übersetzungen konfiguriert werden, um verschiedene globale freigegebene Stores für eine logische Gruppierung globaler Teilnehmer anzugeben, z. B. nach Regionen.

## Standardübersetzungsdienst {#the-default-translation-service}

AEM Communities bietet eine [Testlizenz](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) für einen [Standard-Übersetzungsdienst](../../help/sites-administering/tc-msconf.md) , der für mehrere Sprachen aktiviert ist.

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
* Cloud- **[!UICONTROL Dienste auswählen]**
* Bildlauf nach unten zur **[!UICONTROL Übersetzungsintegration]**

![chlimage_1-65](assets/chlimage_1-65.png)

* Konfigurationen **[!UICONTROL anzeigen auswählen]**

![chlimage_1-66](assets/chlimage_1-66.png)

* Klicken Sie auf `[+]` das Symbol neben **[!UICONTROL Verfügbare Konfigurationen]** , um eine neue Konfiguration zu erstellen.

#### Dialogfeld &quot;Konfiguration erstellen&quot; {#create-configuration-dialog}

![chlimage_1-67](assets/chlimage_1-67.png)

* **[!UICONTROL Übergeordnete Konfiguration]**(Erforderlich) In der Regel als Standard beibehalten. Der Standardwert ist `/etc/cloudservices/translation`.

* **[!UICONTROL Titel]**(Erforderlich) Geben Sie einen Anzeigentitel Ihrer Wahl ein. Kein Standardwert.

* **[!UICONTROL Name]**(Optional) Geben Sie einen Namen für die Konfiguration ein. Standard ist ein Knotenname, der auf dem Titel basiert.

* Wählen Sie **[!UICONTROL Erstellen]**

#### Dialogfeld &quot;Konvertierungskonfiguration&quot; {#translation-config-dialog}

![chlimage_1-68](assets/chlimage_1-68.png)

Ausführliche Anweisungen finden Sie unter [Erstellen einer Konfiguration für die Integration von Übersetzungen](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration)

* **[!UICONTROL Registerkarte &quot;Sites]** &quot;: kann als Standard
* **[!UICONTROL Registerkarte &quot;Communities]** &quot;:
   * **[!UICONTROL Übersetzungsanbieter]** Wählen Sie den Übersetzungsanbieter aus der Dropdownliste aus. Der Standard ist `microsoft`der Testdienst.

   * **[!UICONTROL Inhaltskategorie]** Wählen Sie eine Kategorie, die den zu übersetzenden Inhalt beschreibt. Der Standardwert ist `General.`

   * ****Gebietsschema auswählen...
(Optional) Durch Auswahl eines Gebietsschemas zum Speichern von UGC werden Beiträge aus allen Sprachkopien in einer globalen Konversation angezeigt. Wählen Sie standardmäßig das Gebietsschema für die [Basissprache](sites-console.md#translation) der Website. Die Auswahl `No Common Store` deaktiviert die globale Übersetzung. Standardmäßig ist die globale Übersetzung deaktiviert.

* **[!UICONTROL Registerkarte &quot;Assets]** &quot;: kann als Standard
* Wählen Sie **[!UICONTROL OK]** aus

#### Aktivierung {#activation}

Der neue Dienst für die Integration von Übersetzungen muss in der Veröffentlichungsumgebung aktiviert werden. Wenn die Verbindung zu einer Website noch nicht aktiviert ist, wird der Aktivierungsarbeitsablauf aufgefordert, diese Cloud-Dienstkonfiguration zu veröffentlichen, sobald die Seite, mit der sie verknüpft ist, veröffentlicht wird.

## Verwalten von Übersetzungseinstellungen {#managing-translation-settings}

>[!NOTE]
>
>**Bevorzugte Sprache**
>
>Um festzustellen, ob der Beitrag in einer anderen Sprache als der bevorzugten Sprache verfasst ist, muss die bevorzugte Sprache des Besuchers der Site festgelegt werden.
>
>Die bevorzugte Sprache ist die Spracheinstellung, die in einem Benutzerprofil festgelegt wird, wenn der Site-Besucher angemeldet ist und eine Spracheinstellung angegeben hat.
>
>Wenn der Site-Besucher anonym ist oder keine Spracheinstellung in seinem Profil angegeben hat, ist die bevorzugte Sprache die Basissprache der Seitenvorlage.

### Benutzereinstellungen {#user-preference}

#### Benutzerprofil {#user-profile}

Alle Communities-Sites bieten ein Benutzerprofil, das von Mitgliedern bearbeitet werden kann, um sich selbst für die Community zu identifizieren und ihre Voreinstellungen festzulegen.

Eine dieser Einstellungen ist, ob Community-Inhalte immer in ihrer bevorzugten Sprache angezeigt werden sollen. Standardmäßig ist diese Einstellung nicht festgelegt und wird standardmäßig auf die Systemeinstellung angewendet. Der Benutzer kann die Einstellung entweder auf Ein oder Aus ändern und dadurch die Systemeinstellung überschreiben.

Wenn Seiten automatisch in die vom Benutzer bevorzugte Sprache übersetzt werden, wird die Benutzeroberfläche zum Anzeigen des Originaltextes und Verbessern der Übersetzung weiterhin zur Verfügung gestellt.

![chlimage_1-69](assets/chlimage_1-69.png)

### Community-Site-Einstellung {#community-site-setting}

Wenn eine Community-Site erstellt wird, kann die Übersetzungsoption aktiviert und konfiguriert werden. Die Übersetzungseinstellung ist für Inhalte, die anonyme Site-Besucher anzeigen können, in Kraft, wird jedoch durch die Profileinstellung des Benutzers außer Kraft gesetzt.
