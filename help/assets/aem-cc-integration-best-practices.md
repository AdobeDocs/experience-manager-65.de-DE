---
title: Best Practices für Adobe Creative Cloud [!DNL Adobe Experience Manager] und Integration.
description: Best Practices zur [!DNL Adobe Experience Manager] with [!DNL Adobe Creative Cloud] Integration, um Asset-Transfer-Workflows zu optimieren und eine hohe Inhaltsgeschwindigkeit zu erzielen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 99ce6e0572797b7bccf755aede93623be6bd5698
workflow-type: tm+mt
source-wordcount: '3253'
ht-degree: 57%

---


# [!DNL Adobe Experience Manager] und Best Practices für die [!DNL Creative Cloud] Integration {#aem-and-creative-cloud-integration-best-practices}

[!DNL Adobe Experience Manager Assets] ist eine DAM-Lösung (Digital Asset Management), die DAM-Benutzer bei der Zusammenarbeit mit Kreativteams unterstützen und so die Zusammenarbeit bei der Inhaltserstellung optimieren kann. [!DNL Adobe Creative Cloud]

[!DNL Adobe Creative Cloud] bietet Kreativteams ein System von Lösungen und Services, um digitale Assets zu erstellen. It includes desktop and mobile applications, cloud services like storage with desktop sync or web experience, as well as marketplaces such as [!DNL Adobe Stock].

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>[!DNL Experience Manager] zum [!DNL Creative Cloud] Freigeben von Ordnern wird nicht mehr unterstützt und in diesem Handbuch nicht mehr behandelt. Adobe empfiehlt die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [Experience Manager Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html) , um kreativen Benutzern Zugriff auf Assets zu gewähren, die in verwaltet werden [!DNL Experience Manager].

## Collaboration needs of creatives, marketers, and DAM users {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Anwendungsfall | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Streamline access to asset from a DAM ([!DNL Experience Manager Assets]) for creative professionals, or more broadly, users on desktop working in native asset creation applications. They need an easy and straightforward way to discover, use (open), edit and save changes to [!DNL Experience Manager], as well as upload new files. | Win- oder Mac-Desktop; [!DNL Creative Cloud] Apps |
| Provide high-quality, ready-to-use assets from [!DNL Adobe Stock] | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | [!DNL Experience Manager Assets]; [!DNL Adobe Stock] Marktplatz; Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation freigegeben wurden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | Brand Portal, Asset Share Commons |

## Adobe-Angebote zur Unterstützung von Kooperationsbedarf {#adobe-offerings-to-support-the-collaboration-need}

| Wertangebot für die betroffenen Benutzer | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Creative users discover assets from [!DNL Experience Manager], open and use them, edit and upload changes to [!DNL Experience Manager], as well as upload new files into [!DNL Experience Manager], without leaving [!DNL Creative Cloud] apps. | [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator und InDesign |
| Business users simplify opening and using assets, editing and uploading changes to [!DNL Experience Manager], and uploading new files into [!DNL Experience Manager] from the desktop environment. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Applikationen, auch Adobe-fremden, zu öffnen. | [Experience Manager Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] Desktop App auf Windows- und Mac-Desktop |
| Marketers and business users discover, preview, license and save, and manage the [!DNL Adobe Stock] assets from within [!DNL Experience Manager]. Licensed and saved assets provide select [!DNL Adobe Stock] metadata for better governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] Weboberfläche |

Dieser Artikel konzentriert sich in erster Linie auf die ersten beiden Aspekte der Zusammenarbeit. Die Verteilung und Beschaffung von Vermögenswerten im entsprechende Maß wird kurz als Verwendungsfall genannt. Für solche Lösungen sollten Sie Adobe Brand Portal oder Asset Share Commons beachten. Alternate solutions such as [Brand Portal](https://helpx.adobe.com/de/experience-manager/brand-portal/user-guide.html), solutions that can be built based on [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) components, [Link Share](/help/assets/link-sharing.md), using [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) should be reviewed based on specific requirement.

![Creative Cloud-Verbindungen für Experience Manager, entscheiden Sie, welche Funktion verwendet werden soll](assets/creative-connections-aem.png)

### Zuordnen von Nutzungsszenarien und Adobe-Lösungen   {#mapping-of-use-cases-and-adobe-solutions}

| Nutzungsszenario   | [!DNL Adobe Asset Link] | [!DNL Experience Manager] Desktop-App | Anmerkungen/sonstige Lösungen |
|---|---|---|---|
| Discover - DAM-Ordner durchsuchen | Ja | [!DNL Experience Manager] Web-Oberfläche und Desktop-Aktionen |  |
| Discover - Zugriff auf DAM-Sammlungen | Ja | [!DNL Experience Manager] Web-Oberfläche und Desktop-Aktionen |  |
| Discover - Suche nach Assets aus DAM | Ja | [!DNL Experience Manager] Web-Oberfläche und Desktop-Aktionen |  |
| Verwenden – Öffnen von Assets | Ja | Ja | [Öffnen über die Web-Benutzeroberfläche](managing-assets-touch-ui.md#previewing-assets) oder den Finder |
| Verwenden - Platzieren Sie Assets aus DAM in ein Dokument | Ja – Einbetten | Ja – Verknüpfen oder Einbetten | [!DNL Experience Manager] Desktop App ermöglicht den Zugriff auf Assets als Dateien im lokalen Dateisystem. Diese Links in den nativen Applikationen werden durch lokale Pfade dargestellt. |
| Bearbeiten – Öffnen zur Bearbeitung | Ja – Checkout-Aktion | Ja – Öffnen-Aktion (über die Netzwerkfreigabe) | Beim [Checkout in AAL](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) wird standardmäßig das Asset für das Creative Cloud-Speicherkonto des Benutzers (synchronisiert durch die Creative Cloud-Applikation) gespeichert. |
| Bearbeiten - Arbeiten, die außerhalb von DAM ausgeführt werden | Ja – Asset im mit dem Desktop synchronisierten Creative Cloud-Speicherkonto des Benutzers verfügbar. | Ja |  |
| Bearbeiten – Hochladen von Änderungen | Ja – [Checkin-Aktion](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) mit optionalem Kommentar | Ja |  |
| Hochladen – einzelne Datei | Ja – Hochladen des aktuellen aktiven Dokuments | Ja | [Hochladen über die Web-Oberfläche](managing-assets-touch-ui.md#uploading-assets) |
| Hochladen – mehrere Dateien/hierarchische Ordnerstrukturen | Nein | Ja | [Hochladen über die Web-Oberfläche](managing-assets-touch-ui.md#uploading-assets) oder über benutzerdefinierte Skripten oder Tools. |
| Sonstiges – Benutzer und Anmeldung | Erkennung des Creative Cloud-Benutzers, der bei der Creative Cloud-Desktop-Applikation angemeldet ist (SSO) | [!DNL Experience Manager] Benutzer und Berechtigungen | Users of both solutions count towards the [!DNL Experience Manager] user quota. |
| Sonstiges – Netzwerk und Zugriff | Requires access from user&#39;s desktop to [!DNL Experience Manager] deployment over network | Requires access from user&#39;s desktop to [!DNL Experience Manager] deployment over network | [!DNL Adobe Asset Link] hat keine Netzwerk-Proxy-Umgebung. |
| Sonstiges – Migrieren einer großen Anzahl von Assets | Nein | Nein | [Handbuch zur Asset-Migration](assets-migration-guide.md) |

Um Nutzungsszenarien zum Verteilen von Assets zu unterstützen, sollten andere Lösungen in Betracht gezogen werden:

* [Markenportal](https://helpx.adobe.com/de/experience-manager/brand-portal/user-guide.html) für ein konfigurierbares SaaS-Add-on zum Veröffentlichen von Assets [!DNL Experience Manager Assets] .
* Benutzerdefinierte Lösungen, erstellt auf Grundlage der [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Codebasis
* [!DNL Experience Manager][-Linkfreigabe](/help/assets/link-sharing.md), um Assets ad hoc mithilfe von Links freizugeben
* [Die Experience Manager Assets-Weboberfläche](/help/assets/managing-assets-touch-ui.md) mit durch die Einrichtung der [!DNL Experience Manager] Zugriffskontrolle abgesicherten Bereichen und mit notwendigen IT-/Netzwerkkonfigurationsanpassungen, auf die diese externen Benutzer Zugriff haben, [!DNL Experience Manager].

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **Fertige Kreativ-Assets:**[!DNL Assets] , die für ein breiteres Team freigegeben werden können oder die vom Kreativ-Team für die Freigabe mit Marketing- oder LOB-Teams ausgewählt/genehmigt wurden.
* **Asset-Genehmigungen:** Der Genehmigungsprozess, der für Assets ausgeführt wird, die bereits auf DAM hochgeladen wurden. Dazu gehören in der Regel Markengenehmigungen, Genehmigungen usw.
* **Abgeschlossenes Asset:** Ein Asset, für das alle     Genehmigungen/Metadaten-Tagging durchgeführt wurden und das bereit für die Verwendung durch das breitere Team ist. Ein solches Asset wird in DAM gespeichert und allen (bzw. allen interessierten) Benutzern zur Verfügung gestellt. Es kann in Marketingkanälen oder von Kreativteams verwendet werden, um Designs zu erstellen.
* **Kleinere Asset-Aktualisierung/-Änderung:** Schnelle, kleine Änderung an einem digitalen Asset. Diese wird häufig aufgrund einer Retuschieranforderung oder einer kleineren Bearbeitungsanforderung, einer Asset-Überprüfung oder einer Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung der Sättigung/Helligkeit, Farbe usw.) durchgeführt.
* **Größere Asset-Aktualisierung/-Änderung:** Änderung eines digitalen Assets, die viel Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Diese umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrmals gespeichert werden. Bei umfangreichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase versetzt.
* **DAM:** Digital Asset Management. In diesem Dokument ist es gleichbedeutend mit [!DNL Experience Manager Assets], sofern nicht ausdrücklich etwas Anderes erwähnt wird.
* **Kreativer Benutzer:** Kreativprofi, der digitale Assets mit Creative Cloud-Apps und -Diensten erstellt. In einigen Fällen kann ein kreativer Benutzer Mitglied eines Kreativteams sein, das möglicherweise Creative Cloud verwendet, aber keine digitalen Assets erstellt (z. B. Creative Director oder Creative Team Manager).
* **DAM-Benutzer:** Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder Nicht-Marketing-Benutzer sein, z. B. Branchenbenutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Considerations when using [!DNL Experience Manager] and [!DNL Creative Cloud] integration {#considerations-when-using-aem-and-creative-cloud-integration}

* See [desktop app best practices](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Siehe [Adobe Stock-Integration](aem-assets-adobe-stock.md)
* See [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)

This is a brief summary of best practices for [!DNL Experience Manager] and [!DNL Creative Cloud] integration. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für kreative Benutzer, die in Fotoshop, InDesign oder Illustrator arbeiten:** Adobe Asset Link bietet die beste Benutzererfahrung, einschließlich einer sauberen Handhabung der laufenden Bearbeitung von Assets, von denen aus [!DNL Experience Manager]ausgecheckt wurde.
* **So vereinfachen Sie den Zugriff auf Assets vom Desktop aus für beliebige allgemeine Dateiformate oder Anwendungen:** Verwenden Sie die [!DNL Experience Manager] Desktop-App.
* **Erläutern Sie, warum und wann Assets in DAM gespeichert werden:** Aktualisierungen, die dem breiteren Team in Ihrer Organisation zur Verfügung gestellt werden.
* **Beachten des Volumens freigegebener Assets:** Wenn Ihr Anwendungsfall die Asset-Verteilung ist, könnten Governance und Sicherheit die wichtigsten Aspekte sein. Erwägen Sie die Verwendung von Tools, die für eine skalierte Vorgehensweise entwickelt wurden, wie z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams genutzt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Applikationen keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugriff auf [!DNL Adobe Stock] Assets von [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[Die Integration](/help/assets/aem-assets-adobe-stock.md) von Experience Manager und Adobe Stock bietet [!DNL Experience Manager] Benutzern die Möglichkeit, Assets von [!DNL Adobe Stock] in zu suchen, zu Vorschau, zu lizenzieren und zu speichern [!DNL Experience Manager]. Licensed and saved [!DNL Stock] assets have selected [!DNL Stock] metadata, which can be used to search for them with extra filters.

Einige wichtige Punkte zu dieser Integration:

* When assets from Adobe stock are saved to [!DNL Experience Manager], they become a regular [!DNL Assets], with binary saved to the [!DNL Experience Manager] repository. Some metadata related to [!DNL Adobe Stock] are saved for the asset in [!DNL Experience Manager], otherwise the ingestion process looks the same as for any other file. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* The asset saved to [!DNL Experience Manager] is a copy, not a link back into [!DNL Adobe Stock].

**Arbeiten mit Assets, die von[!DNL Adobe Stock]in[!DNL Experience Manager]gespeichert wurden[!DNL Creative Cloud]**. This integration is independent of[!DNL Adobe Asset Link], but[!DNL Adobe Asset Link]recognizes these assets saved from[!DNL Stock]that way, and displays additional metadata and[!DNL Stock]icon on these assets in[!DNL Adobe Asset Link]extension UI in[!DNL Photoshop],[!DNL Illustrator], or[!DNL InDesign]. The files are available for browsing, opening, and so on - because they are regular assets when saved to[!DNL Experience Manager].
Creative users working in[!DNL Creative Cloud]apps with[!DNL Adobe Asset Link]extension present, in addition to having access to already-licensed assets from[!DNL Adobe Stock]into[!DNL Experience Manager], can also use[!DNL Creative Cloud]Libraries panel to search, preview, and license[!DNL Adobe Stock]assets.[!DNL Assets]von[!DNL Adobe Stock]lizenzierten und gespeicherten Daten[!DNL Experience Manager]zur Verfügung gestellt werden für die breiteren Teams, die auf die[!DNL Experience Manager Assets]Bereitstellung zugreifen, während kreative Elemente, die über das Bedienfeld &quot;[!DNL Adobe Stock]Bibliotheken&quot;lizenziert werden, sie für sich selbst nur standardmäßig in ihrem[!DNL Creative Cloud][!DNL Creative Cloud]Konto verfügbar machen.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Informationen zum Speichern von Assets in DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativteams und Marketing-/Branchenteams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden   {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Es wird sichergestellt, dass die Assets von verschiedenen Benutzern in der gesamten Organisation oder im gesamten System genutzt werden, z. B. von Kunden, Partnern usw.

Most organizations choose to only store assets that are relevant to the downstream marketing/LOB processes (publishing to channels like web channel via [!DNL Experience Manager Sites] or other channels served by Adobe Experience Cloud - Marketing Cloud, Advertising Cloud, and measured by Analytics Cloud, providing to users/partners, and so on). Außerdem speichern Organisationen Assets, für die möglicherweise ein Prüfungs-/Genehmigungsprozess in DAM erfolgt. Auf diese Weise werden hauptsächlich Assets in DAM gespeichert, die mit hoher Wahrscheinlichkeiten genutzt werden, und das Speichern von Assets im Leerlauf wird vermieden.

Die Speicherung von Assets hängt außerdem von Überlegungen zu technischen Aspekten und zur Ressourcennutzung ab. DAM bietet zusätzliche Dienste rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Dienste erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist das Speichern aller Assets und Aktualisierungen nicht empfehlenswert. Beispiel: Wenn Aktualisierungen von schlechter Qualität sind und einen unverhältnismäßigen Ressourcenverbrauch aufweisen, sollten die Assets nicht in DAM gespeichert werden.

#### Wann Assets in DAM gespeichert werden   {#when-assets-are-stored-in-dam}

Kreativteams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Beispielsweise vermeiden sie das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind, oder zum Experimentieren verwendet werden.
* Assets, die den Prüfungszyklus des Kreativteams/internen Teams nicht bestehen.
* Verglichen mit dem fraglichen Asset verfügt das Team über bessere Kandidaten, um seine Arbeit für externe Teams zu repräsentieren.

In der Regel werden Assets der folgenden Klassen in DAM gespeichert:

* Assets, die einen bestimmten Reifegrad erreicht haben und als bereit zur Freigabe für andere Benutzer gelten.
* Assets, die vorab vom Kreativteam ausgewählt wurden.
* Bestimmte Asset-Formate, die vom Marketingteam verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien).

#### Wann Aktualisierungen von Assets in DAM gespeichert werden   {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzer relevant sind. Dadurch wird sichergestellt, dass Benutzern (Marketing- und ähnliche Funktionen) in der DAM-Asset-Zeitleiste nur relevante Versionen angezeigt werden.

Normalerweise handelt es sich dabei um Änderungen in Bezug auf die wichtigsten Meilensteine im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Marketing-Asset oder eine offizielle Aktualisierung basierend auf Anforderungen/Überprüfungen durch das Kreativteam in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativteams zur Überprüfung durch das Marketingteam nach einer Änderungsanforderung für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Diese sollte als Referenzmaterial oder zum Zurücksetzen auf die letzte Version in DAM gespeichert und versioniert werden.

Es folgen Beispiele für Updates, die normalerweise nicht relevant sind:

* Frühe Versionen von Assets, die hochgeladen wurden, bevor sie für die Marketingüberprüfung bereit waren
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor die Kreativ- und Marketingteams das Asset für fertig erklären

### Benutzerzugriff auf DAM {#user-access-to-dam}

[!DNL Assets] unterstützt zwei Benutzertypen je nach Zugriff auf die [!DNL Assets] Bereitstellung. Normalerweise haben Benutzer innerhalb des Unternehmensnetzwerks (Firewall) direkten Zugriff auf DAM. Andere Benutzer außerhalb des Unternehmensnetzwerks haben dagegen keinen direkten Zugriff. Der Benutzertyp bestimmt, welche Integrationen aus technischer Sicht verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM   {#creative-users-with-direct-access-to-dam}

Typically, in-house creative teams or agencies/creative professionals  onboarded  to the internal network have access to the DAM instance, including [!DNL Experience Manager] login. [!DNL Experience Manager] und die Netzinfrastruktur so eingerichtet werden können, dass sie direkten Zugang zu externen Akteuren - meist vertrauenswürdigen Organisationen wie Agenturen, die für einen Kunden arbeiten - ermöglicht, z. B. über VPN oder IP-Whitelist auf [!DNL Experience Manager] das Netzwerk zuzugreifen.

In such cases, Adobe Asset Link or [!DNL Experience Manager] desktop app helps provide easy access to final/approved assets and lets you save creative-ready assets to DAM.

#### Kreative Benutzer ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen oder Freiberufler ohne direkten Zugriff auf die DAM-Instanz benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs in DAM hinzufügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* Verwenden des Desktop-Programms, wenn Asset Link nicht funktioniert.
* Use [Experience Manager Assets Brand Portal](https://helpx.adobe.com/de/experience-manager/brand-portal/user-guide.html) for distributing assets securely to external partners
* Verwenden einer benutzerdefinierten Implementierung eines Verteilungs- und Quellportals basierend auf [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* Use Access Control set up in [!DNL Experience Manager] and necessary network infrastructure (for example, VPN and IP whitelisting) to give external parties access to a dedicated area of content in your DAM. They can use [!DNL Experience Manager] Web UI to get assets and upload new content into your DAM.

#### Laufende Arbeiten an Assets über [!DNL Experience Manager] {#work-in-progress-on-assets-from-aem}

As discussed in this document, it is recommended to carry out major updates on assets, sometimes called work in progress, without having all the edits saved to the local file also uploaded to [!DNL Experience Manager] as changes. Dies beschleunigt die Arbeit von Desktop-Benutzern, schränkt die verwendete Netzwerkbandbreite ein und sorgt dafür, dass die Assets-Timeline „sauber“ bleibt und auf kontrollierte, größere Aktualisierungen ausgerichtet ist.

Adobe Asset Link bietet eine gute Unterstützung für dieses Nutzungsszenario:

* Wenn Benutzer in Photoshop, InDesign oder Illustrator eine Datei bearbeiten möchten, checken sie das jeweilige Asset aus.
* The asset is downloaded in background, put into users Creative Cloud account synchronized to disk by Creative Cloud desktop app, and the check-out flag is toggled in [!DNL Experience Manager] on the asset to minimize editing conflicts
* Von diesem Zeitpunkt an arbeiten die Benutzer in einer Datei, die lokal am synchronisierten Speicherort abgelegt ist. Sie können weiterarbeiten und die erforderlichen Änderungen so oft wie gewünscht speichern.
* Da sich das Asset im Creative Cloud-Konto befindet, ist es auch auf etwaigen anderen Benutzergeräten verfügbar (z. B. zum Öffnen oder Bearbeiten in einer dedizierten mobilen Creative Cloud-Applikation). Außerdem kann es für andere Creative Cloud-Benutzer zwecks Zusammenarbeit freigegeben werden.
* Wenn kreative Benutzer keine weiteren Änderungen vornehmen möchten, können sie diese Datei in ihrer Creative Cloud-Applikation mit einem optionalen Kommentar einchecken. The corresponding asset in [!DNL Experience Manager] are versioned and updated to with the new binary. [!DNL Experience Manager] Benutzer wie Marketingexperten oder LOB-Benutzer haben Zugriff auf wichtige Asset-Änderungen oder Meilensteine über die Benutzeroberfläche der [!DNL Experience Manager] Asset-Zeitschiene.

[!DNL Experience Manager] Desktop App bietet eine Netzwerkfreigabe für in der nativen App geöffnete Assets. By default, all the changes done locally are uploaded to [!DNL Experience Manager] automatically after a brief while. With such a configuration, frequent saves during the work-in-progress phase would all be uploaded into [!DNL Experience Manager] and versioned, creating a lot of network traffic and potential scalability challenges - not to mention unnecessary versions in [!DNL Experience Manager].

The recommended approach here is to use an option in [!DNL Experience Manager] desktop app to turn off automated updates, and upload changes to assets to [!DNL Experience Manager] manually, leveraging the upload changes action in the app&#39;s Asset Status UI.

#### Massen-Upload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von   Fotoschuhe oder größere Projekte
* Hochladen von Assets von Kreativagenturen
* Hochladen von Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Die Beschreibung bezieht sich auf das operationelle Hochladen von Dateien (z. B. jede Woche oder bei jedem Fotoshot) als normalen Teil des Arbeitsablaufs des Desktop-Benutzers. Das Migrieren großer Assets wird hier nicht behandelt.

Sie können die folgenden Upload-Funktionen nutzen:

* To upload large/hierarchical folders in bulk, use [!DNL Experience Manager] desktop app that provides [folder upload](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) functionality. Sie können auch hierarchische Ordnerstrukturen hochladen. [!DNL Assets]Das Hochladen von erfolgt im Hintergrund und ist daher nicht an eine Webbrowsersitzung gebunden.
* To upload a few files from a single folder, drag the files directly to the web interface or use the Create option in the [!DNL Assets] web interface.
* Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Upload-Programme verwenden.

#### Manage digital assets directly from desktop {#managing-digital-assets-directly-from-desktop}

If you use Network File Shares to manage digital assets, just using the network share mapped by [!DNL Experience Manager] desktop app could be seen as a convenient substitute. When transitioning from network file shares, [!DNL Experience Manager] web interface provides a rich set of Digital Asset Management capabilities that go well beyond what is possible on a network share (search, collections, metadata, collaboration, previews, and so on), and [!DNL Experience Manager] desktop app provides a handy link to connect the server-side DAM repository with the work on desktop.

Avoid using [!DNL Experience Manager] desktop app to manage assets directly in the network share of [!DNL Assets]. For example, avoid using [!DNL Experience Manager] desktop app to move/copy multiple files. Instead, use the [!DNL Assets] interface to drag folders from Finder/Explorer to the network share or use the [!DNL Assets] Folder Upload feature.

#### Asset-Migration {#asset-migration}

Informationen zum Planen und Ausführen von Asset-Migrationen von vorhandenen Systemen in ein neues System oder Migrieren großer Mengen von auf Servern gespeicherten Assets finden Sie im [Migrationshandbuch](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] Desktop-App und [!DNL Experience Manager] zu [!DNL Creative Cloud] -Integrationen unterstützen solche Migrationen nicht. Aufgrund der großen Menge an aufzunehmenden Assets und der zusätzlichen Anforderungen rund um Metadatenzuordnungen, Transformationen und Aufnahmen sollten Migrationen mithilfe anderer Tools und Ansätze erfolgen.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [Best Practices für Experience Manager Desktop-Apps](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [Experience Manager-Markenportal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md)

