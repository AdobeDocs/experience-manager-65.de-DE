---
title: Best Practices zur Integration von AEM und Creative Cloud
description: Best Practices zur Integration von AEM in Adobe Creative Cloud, um Asset-Transfer-Arbeitsabläufe zu optimieren und eine maximale Effizienz zu erzielen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# AEM and Creative Cloud integration best practices {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.4 article that's behind this article in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets ist eine DAM-Lösung (Digital Asset Management), die in die Adobe Creative Cloud integriert werden kann, um DAM-Benutzern die Zusammenarbeit mit Kreativteams zu erleichtern und so die Zusammenarbeit beim Erstellen von Inhalten zu optimieren.

Adobe Creative Cloud bietet Kreativteams ein System von Lösungen und Services, um digitale Assets zu erstellen. Dieses Angebot enthält Desktop- und Mobil-Applikationen, Cloud-Services wie Speicher mit Desktop-Synchronisierung oder Web-Erlebnis sowie Marktplätze wie Adobe Stock.

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>Die gemeinsame Nutzung von AEM in Creative Cloud-Ordnern wird nicht mehr unterstützt und wird in diesem Handbuch nicht mehr behandelt. Adobe recommends using newer capabilities such as [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) or [AEM desktop app](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html) to provide creative user with access to assets managed in AEM.

## Collaboration needs of creatives, marketers, and DAM users {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Anwendungsfall  | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Für Kreativprofis oder, ganz allgemein, für Desktop-Benutzer, die mit nativen Applikationen zur Asset-Erstellung arbeiten, soll der Zugriff auf Assets von einem DAM-System (AEM Assets) optimiert werden. Sie benötigen eine einfache und unkomplizierte Möglichkeit zum Entdecken, Verwenden (Öffnen), Bearbeiten und Speichern von Änderungen in AEM sowie zum Hochladen neuer Dateien. | Windows- oder Mac-Desktop, Creative Cloud-Applikationen |
| Bereitstellen von hochwertigen, gebrauchsfertigen Assets aus Adobe Stock | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | AEM Assets, Adobe Stock Marketplace, Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation freigegeben wurden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | Brand Portal, Asset Share Commons |

## Adobe-Angebote zur Unterstützung von Kooperationsanforderungen {#adobe-offerings-to-support-the-collaboration-need}

| Wertangebot für die betroffenen Benutzer | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Kreativbenutzer entdecken Assets aus AEM, öffnen und verwenden diese, führen Bearbeitungen durch und laden AEM-Änderungen sowie neue Dateien in AEM hoch, ohne Creative Cloud-Applikationen verlassen zu müssen. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator und InDesign |
| Geschäftsbenutzer vereinfachen das Öffnen und Verwenden von Assets, das Bearbeiten und Hochladen von Änderungen in AEM und das Hochladen neuer Dateien in AEM von der Desktop-Umgebung aus. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Applikationen, auch Adobe-fremden, zu öffnen. | [AEM Desktop App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) | AEM Desktop App auf Windows- und Mac-Desktop |
| Marketer und Geschäftsbenutzer können Adobe Stock-Assets in AEM entdecken, in einer Vorschau anzeigen, lizenzieren sowie speichern und verwalten. Lizenzierte und gespeicherte Assets liefern ausgewählte Adobe Stock-Metadaten für eine bessere Governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | AEM-Web-Oberfläche |

Dieser Artikel konzentriert sich hauptsächlich auf die ersten beiden Aspekte der Kooperationsanforderungen. Die Verteilung und Beschaffung skalierter Assets wird kurz als Nutzungsszenario erwähnt. Als Lösungen für diese Anforderungen sollten Sie Adobe Brand Portal oder Asset Share Commons in Betracht ziehen. Alternate solutions such as [Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html), solutions that can be built based on [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) components, [Link Share](/help/assets/link-sharing.md), using [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) should be reviewed based on specific requirement.

![Creative Cloud-Verbindungen für AEM: Festlegen der zu verwendenden Funktion](assets/creative-connections-aem.png)

### Zuordnen von Nutzungsszenarien und Adobe-Lösungen {#mapping-of-use-cases-and-adobe-solutions}

| Nutzungsszenario | Adobe Asset Link | AEM-Desktop-Programm | Anmerkungen/sonstige Lösungen |
|---|---|---|---|
| Entdecken – Durchsuchen von AEM-Ordnern | Ja | AEM-Web-Benutzeroberfläche und Desktop-Aktionen | Deaktivieren Sie beim Durchsuchen der Netzwerkfreigabe die Miniaturansichten, um das Herunterladen binärer Asset-Dateien zu vermeiden. |
| Entdecken – Zugreifen auf AEM-Sammlungen | Ja | AEM-Web-Benutzeroberfläche und Desktop-Aktionen |  |
| Entdecken – Suchen nach Assets aus AEM | Ja | AEM-Web-Benutzeroberfläche und Desktop-Aktionen |  |
| Verwenden – Öffnen von Assets | Ja | Ja – für jede App | [Öffnen über die Weboberfläche](managing-assets-touch-ui.md#previewing-assets) oder den Finder |
| Verwenden – Platzieren von Assets aus AEM in ein Dokument | Ja – Einbetten | Ja – Verknüpfen oder Einbetten | AEM Desktop App ermöglicht den Zugriff auf Assets als Dateien im lokalen Dateisystem. Diese Links in den nativen Applikationen werden durch lokale Pfade dargestellt. |
| Bearbeiten – Öffnen zur Bearbeitung | Ja – Checkout-Aktion | Ja – Öffnen-Aktion (über die Netzwerkfreigabe) | [Beim Auschecken in AAL](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) wird das Asset standardmäßig im Creative Cloud-Speicherkonto des Benutzers (durch Creative Cloud-App synchronisiert) gespeichert. |
| Bearbeiten – laufende Arbeiten außerhalb von AEM | Ja - Asset verfügbar im Creative Cloud-Speicherkonto des Benutzers, das mit dem Desktop synchronisiert wird. | Ja |  |
| Bearbeiten – Hochladen von Änderungen | Ja – [Checkin-Aktion](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) mit optionalem Kommentar | Ja |  |
| Hochladen – einzelne Datei | Ja – Hochladen des aktuellen aktiven Dokuments | Ja | [Hochladen über die Weboberfläche](managing-assets-touch-ui.md#uploading-assets) |
| Hochladen – mehrere Dateien/hierarchische Ordnerstrukturen | Nein | Ja | [Hochladen über die Weboberfläche](managing-assets-touch-ui.md#uploading-assets);<br>Benutzerdefiniertes Skript oder Tool |
| Sonstiges – Benutzer und Anmeldung | Erkennung des Creative Cloud-Benutzers, der bei der Creative Cloud-Desktop-Applikation angemeldet ist (SSO) | AEM-Benutzer/-Anmeldung | Benutzer beider Lösungen werden mit dem AEM-Benutzerkontingent verrechnet. |
| Sonstiges – Netzwerk und Zugriff | Zugriff vom Desktop des Benutzers auf AEM-Bereitstellungen über das Netzwerk erforderlich | Zugriff vom Desktop des Benutzers auf AEM-Bereitstellungen über das Netzwerk erforderlich | Adobe Asset Link gibt keine Netzwerkproxy-Umgebung frei. |
| Sonstiges – Migrieren einer großen Anzahl von Assets | Nein | Nein | [Migrationshandbuch](assets-migration-guide.md) |

Um Nutzungsszenarien zum Verteilen von Assets zu unterstützen, sollten andere Lösungen in Betracht gezogen werden:

* [Markenportal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) für ein konfigurierbares SaaS-Add-on zu AEM Assets, um Assets zu veröffentlichen.
* Benutzerdefinierte Lösungen, erstellt auf Grundlage der [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Codebasis
* AEM-[Linkfreigabe](/help/assets/link-sharing.md), um Assets ad hoc mithilfe von Links freizugeben
* [AEM Assets-Web-Oberfläche](/help/assets/managing-assets-touch-ui.md) mit Bereichen für externe Parteien, die durch Einrichtung einer AEM-Zugriffssteuerung abgesichert sind, und mit notwendigem IT-/Netzwerkkonfigurationsanpassungen, wodurch diese externen Benutzer Zugriff auf AEM erhalten

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **** Kreative Elemente: Assets, die für ein breiteres Team freigegeben werden können oder die vom Kreativteam für die Freigabe mit Marketing- oder LOB-Teams ausgewählt/genehmigt wurden.
* **Asset-Genehmigungen:** Der Genehmigungsprozess für bereits in DAM hochgeladene Assets, welcher in der Regel Markengenehmigungen, rechtliche Genehmigungen usw. umfasst.
* **Abgeschlossenes Asset:** Ein Asset, für das alle  Tagging von Genehmigungen/Metadaten und kann vom breiteren Team verwendet werden. Ein solches Asset wird in DAM gespeichert und für alle (interessierten) Benutzer bereitgestellt. Es kann in Marketingkanälen oder von Kreativteams zur Designgestaltung verwendet werden.
* **Geringfügige Asset-**  update/change: Eine schnelle und kleine Änderung an einem digitalen Asset. Sie erfolgt häufig als Reaktion auf Anforderung einer Retusche oder geringfügigen Bearbeitung oder auf eine Asset-Überprüfung bzw. -Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung von Sättigung/Helligkeit, Farbe usw.).
* **Wesentliche Asset-**  update/change: Eine Veränderung eines digitalen Assets, die erhebliche Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Sie umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrere Male gespeichert werden. Bei wesentlichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase verschoben.
* **DAM:** Digital Asset Management. Sofern nicht ausdrücklich anders angegeben ist „DAM“ in diesem Dokument ein Synonym für AEM (Adobe Experience Manager)-Assets.
* **Kreativer Benutzer:** Ein Kreativprofi, der mit Creative Cloud-Applikationen und -Diensten digitale Assets erstellt. In einigen Fällen kann ein kreativer Benutzer ein Mitglied eines Kreativteams sein, das Creative Cloud verwendet, jedoch keine digitalen Assets erstellt (z. B. ein Creative Director oder Leiter des Kreativteams).
* **** DAM-Benutzer: Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder Nicht-Marketingbenutzer sein, z. B. Branchenbenutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Überlegungen zur Verwendung der AEM- und Creative Cloud-Integration {#considerations-when-using-aem-and-creative-cloud-integration}

* See [desktop app best practices](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Siehe [Adobe Stock-Integration](aem-assets-adobe-stock.md)
* See [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Dies ist eine kurze Zusammenfassung der Best Practices für die Integration von Experience Manager und Creative Cloud. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für kreative Benutzer, die in Photoshop, InDesign oder Illustrator arbeiten:** Adobe Asset Link bietet ein optimales Benutzererlebnis, einschließlich der ordnungsgemäßen Abwicklung laufender Arbeiten von aus AEM ausgecheckten Assets.
* **Für einen vereinfachten Desktop-Zugriff auf Assets bei beliebigen allgemeinen Dateiformaten oder Applikationen:** Verwenden Sie AEM Desktop App.
* **Gründe und Zeitpunkt zum Speichern von Assets in DAM:** Aktualisierungen, die für das breiter gefasste Team in Ihrer Organisation verfügbar gemacht werden sollen.
* **Berücksichtigung der Menge der freigegebenen Assets:** Wenn Ihr Nutzungsszenario eine Asset-Verteilung vorsieht, sind Governance und Sicherheit möglicherweise die wichtigsten Aspekte. Erwägen Sie die Verwendung von Werkzeugen, die dafür entwickelt wurden, z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams gehandhabt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Applikationen keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugreifen auf Adobe Stock Assets über AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[Die AEM- und Adobe Stock-Integration](/help/assets/aem-assets-adobe-stock.md) bietet AEM-Benutzern die Möglichkeit, Assets von Adobe Stock in AEM zu suchen, in der Vorschau anzuzeigen, zu lizenzieren und zu speichern. Lizenzierte und gespeicherte Adobe Stock-Assets verfügen über ausgewählte Stock-Metadaten, mit denen sie mit zusätzlichen Filtern gesucht werden können.

Einige wichtige Punkte zu dieser Integration:

* Wenn Assets aus Adobe Stock in AEM gespeichert werden, werden sie zu regulären AEM-Assets. Die Binärdateien werden dabei im AEM-Repository gespeichert. Einige zu Adobe Stock gehörige Metadaten werden für das Asset in AEM gespeichert. Ansonsten verläuft die Erfassung wie bei jeder anderen Datei. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* Das in AEM gespeicherte Asset ist eine Kopie, kein Link zurück zu Adobe Stock.

**Arbeiten mit Assets in Creative Cloud, die aus Adobe Stock in AEM gespeichert wurden.** Diese Integration ist zwar unabhängig von Adobe Asset Link, aber Adobe Asset Link erkennt diese so aus Adobe Stock gespeicherten Assets und zeigt zusätzliche Metadaten sowie ein Adobe Stock-Symbol auf diesen Assets in der Adobe Asset Link-Erweiterungsoberfläche in Photoshop, Illustrator bzw. InDesign an. Die Dateien sind zum Durchsuchen, Öffnen usw. verfügbar, da sie durch Speichern in AEM zu regulären AEM-Assets werden.
Kreative Benutzer, die in Creative Cloud-Applikationen mit vorhandener Adobe Asset Link-Erweiterung arbeiten, haben zusätzlich zum Zugriff auf bereits lizenzierte Assets von Adobe Stock in AEM auch Zugriff auf das Creative Cloud Libraries-Bedienfeld, um Adobe Stock-Assets zu suchen, in einer Vorschau anzuzeigen und zu lizenzieren.
Lizenzierte und in AEM gespeicherte Assets aus Adobe Stock werden breiter gefassten Teams zur Verfügung gestellt, die auf die AEM Assets-Bereitstellung zugreifen. Kreative hingegen, die Assets aus Adobe Stock über das Creative Cloud Libraries-Bedienfeld lizenzieren, können sich die Assets selbst lediglich standardmäßig in ihrem Creative-Cloud-Konto zur Verfügung stellen.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Informationen zum Speichern von Assets in einem DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativteams und Marketing-/Branchenteams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Es wird sichergestellt, dass die Assets von verschiedenen Benutzern in der gesamten Organisation oder im gesamten System genutzt werden, z. B. von Kunden, Partnern usw.

Die meisten Organisationen entscheiden sich dafür, nur Assets zu speichern, die für nachgelagerte Marketing-/Branchenprozesse (Veröffentlichen in Kanälen wie dem Internet über AEM Sites oder anderen Kanälen wie Marketing Cloud oder Advertising Cloud, die von Adobe Experience Cloud bereitgestellt und von Analytics Cloud bewertet werden, Bereitstellung für Benutzer/Partner usw.) relevant sind. Außerdem speichern Organisationen Assets, für die möglicherweise ein Prüfungs-/Genehmigungsprozess in DAM erfolgt. Auf diese Weise werden hauptsächlich Assets in DAM gespeichert, die mit hoher Wahrscheinlichkeiten genutzt werden, und das Speichern von Assets im Leerlauf wird vermieden.

Die Speicherung von Assets hängt außerdem von Überlegungen zu technischen Aspekten und zur Ressourcennutzung ab. DAM bietet zusätzliche Dienste rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Dienste erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist das Speichern aller Assets und Aktualisierungen nicht empfehlenswert. Beispiel: Wenn Aktualisierungen von schlechter Qualität sind und einen unverhältnismäßigen Ressourcenverbrauch aufweisen, sollten die Assets nicht in DAM gespeichert werden.

#### Wann Assets in DAM gespeichert werden {#when-assets-are-stored-in-dam}

Kreativteams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Beispielsweise vermeiden sie das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind, oder zum Experimentieren verwendet werden
* Assets, die den Prüfungszyklus des Kreativteams/internen Teams nicht bestehen
* Verglichen mit dem betreffenden Asset verfügt das Team über bessere Beispiele für seine Arbeit, um sie externen Teams vorzustellen.

In der Regel werden Assets der folgenden Klassen in DAM gespeichert:

* Assets, die einen bestimmten Reifegrad erreicht haben und als bereit zur Freigabe für andere Benutzer gelten
* Assets, die vorab vom Kreativteam ausgewählt wurden
* Bestimmte Asset-Formate, die vom Marketingteam verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien)

#### Wann Aktualisierungen von Assets in DAM gespeichert werden {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzer relevant sind. Dadurch wird sichergestellt, dass Benutzern (Marketing- und ähnliche Funktionen) in der DAM-Asset-Zeitleiste nur relevante Versionen angezeigt werden.

Normalerweise handelt es sich dabei um Änderungen in Bezug auf die wichtigsten Meilensteine im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Marketing-Asset oder eine offizielle Aktualisierung basierend auf Anforderungen/Überprüfungen durch das Kreativteam in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativteams zur Überprüfung durch das Marketingteam nach einer Änderungsanforderung für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Diese sollte als Referenzmaterial oder zum Zurücksetzen auf die letzte Version in DAM gespeichert und versioniert werden.

Es folgen Beispiele für Updates, die normalerweise nicht relevant sind:

* Frühe Versionen von Assets, die hochgeladen wurden, bevor sie für die Marketingüberprüfung bereit waren
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor die Kreativ- und Marketingteams das Asset für fertig erklären

### Benutzerzugriff auf DAM {#user-access-to-dam}

AEM Assets unterstützt zwei Arten von Benutzern, die auf deren Zugriff auf die AEM Assets-Bereitstellung basieren. Normalerweise haben Benutzer innerhalb des Unternehmensnetzwerks (Firewall) direkten Zugriff auf DAM. Andere Benutzer außerhalb des Unternehmensnetzwerks haben dagegen keinen direkten Zugriff. Der Benutzertyp bestimmt, welche Integrationen aus technischer Sicht verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM {#creative-users-with-direct-access-to-dam}

In der Regel haben interne Kreativteams oder Agenturen/Kreativprofis, die an das interne Netzwerk angeschlossen sind, Zugriff auf die DAM-Instanz, einschließlich AEM-Anmeldung. Die AEM- und Netzwerkinfrastruktur kann eingerichtet werden, um externen Parteien – normalerweise vertrauenswürdige Organisationen wie Agenturen, die für einen Kunden arbeiten – direkten Zugriff zu ermöglichen, damit diese über das Netzwerk (z. B. über VPN oder IP-Whitelisting) auf AEM zugreifen können

In solchen Fällen bietet Adobe Asset Link oder AEM Desktop App einfachen Zugriff auf abgeschlossene/genehmigte Assets und ermöglicht das Speichern fertiger Kreativ-Assets in DAM.

#### Kreative Benutzer ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen oder Freiberufler ohne direkten Zugriff auf die DAM-Instanz benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs in DAM hinzufügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* Verwenden der Desktop-App, wenn Asset Link nicht funktioniert.
* Use [AEM Assets Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) for distributing assets securely to external partners
* Verwenden einer benutzerdefinierten Implementierung eines Verteilungs- und Quellportals basierend auf [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* Verwenden der in AEM eingerichteten Zugriffssteuerung und der erforderlichen Netzwerkinfrastruktur (z. B. VPN und IP-Whitelisting), um externen Parteien Zugriff auf einen speziellen Inhaltsbereich in Ihrem DAM-System zu gewähren. Sie können über die AEM-Web-Benutzeroberfläche Assets abrufen und neue Inhalte in Ihr DAM-System hochladen.

#### Laufende Arbeiten an Assets über AEM {#work-in-progress-on-assets-from-aem}

Wie in diesem Dokument erläutert, wird empfohlen, umfangreiche Aktualisierungen für Assets, auch als laufende Arbeiten bezeichnet, durchzuführen, ohne dass alle in der lokalen Datei gespeicherten Bearbeitungen ebenfalls als Änderungen in AEM hochgeladen wurden. Dies beschleunigt die Arbeit von Desktop-Benutzern, schränkt die verwendete Netzwerkbandbreite ein und sorgt dafür, dass die Assets-Timeline „sauber“ bleibt und auf kontrollierte, größere Aktualisierungen ausgerichtet ist.

Adobe Asset Link bietet eine gute Unterstützung für dieses Nutzungsszenario:

* Wenn Benutzer in Photoshop, InDesign oder Illustrator eine Datei bearbeiten möchten, checken sie das jeweilige Asset aus.
* Das Asset wird im Hintergrund heruntergeladen, in die von der Creative Cloud-Desktop-Applikation mit der Festplatte synchronisierten Creative Cloud-Konten der Benutzer platziert und das Checkout-Flag wird in AEM auf dem Asset umgeschaltet, um Bearbeitungskonflikte zu minimieren.
* Von diesem Zeitpunkt an arbeiten die Benutzer in einer Datei, die lokal am synchronisierten Speicherort abgelegt ist. Sie können weiterarbeiten und die erforderlichen Änderungen so oft wie gewünscht speichern.
* Da sich das Asset im Creative Cloud-Konto befindet, ist es auch auf etwaigen anderen Benutzergeräten verfügbar (z. B. zum Öffnen oder Bearbeiten in einer dedizierten mobilen Creative Cloud-Applikation). Außerdem kann es für andere Creative Cloud-Benutzer zwecks Zusammenarbeit freigegeben werden.
* Wenn kreative Benutzer keine weiteren Änderungen vornehmen möchten, können sie diese Datei in ihrer Creative Cloud-Applikation mit einem optionalen Kommentar einchecken. Das entsprechende Asset in AEM wird versioniert und mit der neuen Binärdatei aktualisiert. AEM-Benutzer wie Marketer oder Branchenbenutzer haben über die Timeline-Benutzeroberfläche von AEM Assets Zugriff auf wichtige Asset-Änderungen oder Meilensteine.

AEM Desktop App bietet eine Netzwerkfreigabe für in der nativen App geöffnete Assets. Standardmäßig werden alle lokalen Änderungen nach kurzer Zeit automatisch in AEM hochgeladen. Mit einer solchen Konfiguration werden häufig gespeicherte Inhalte während der laufenden Arbeit in AEM hochgeladen und versioniert, sodass beträchtlicher Netzwerkverkehr und potenzielle skalierbarkeitsbezogene Herausforderungen entstehen – ganz zu schweigen von den unnötigen Versionen in AEM.

In diesem Fall wird empfohlen, die AEM Desktop App-Option zum Deaktivieren automatischer Aktualisierungen zu verwenden und Asset-Änderungen manuell in AEM hochzuladen. Dabei wird die Aktion zum Hochladen von Assets in der Asset-Status-Benutzeroberfläche der App genutzt.

#### Massenupload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von Fotoschuhe oder größere Projekte
* Hochladen von Assets von Kreativagenturen
* Hochladen von Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Die Beschreibung bezieht sich auf das operationelle Hochladen von Dateien (z. B. jede Woche oder bei jedem Fotoshot) als normalen Teil des Arbeitsablaufs des Desktop-Benutzers. Das Migrieren großer Assets wird hier nicht behandelt.

Sie können die folgenden Upload-Funktionen nutzen:

* Um große/hierarchische Ordner stapelweise hochzuladen, verwenden Sie AEM Desktop App mit Funktionen zum [Hochladen von Ordnern](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload). Sie können auch hierarchische Ordnerstrukturen hochladen. Das Hochladen von Assets erfolgt im Hintergrund und ist daher nicht an eine Webbrowsersitzung gebunden.
* Um einige Dateien aus einem einzelnen Ordner hochzuladen, ziehen Sie die Dateien direkt in die Weboberfläche oder verwenden Sie die Option „Erstellen“ in der Web-Benutzeroberfläche von AEM Assets.
* Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Uploader verwenden.

#### Manage digital assets directly from desktop {#managing-digital-assets-directly-from-desktop}

Wenn Sie digitale Assets in Netzwerk-Dateifreigaben verwalten, kann stattdessen einfach die von AEM Desktop App zugeordnete Netzwerkfreigabe verwendet werden. Beim Übergang von Netzwerk-Dateifreigaben stellt die Web-Benutzeroberfläche von AEM einen umfangreichen Satz von Digital-Asset-Management-Funktionen bereit, die weit über die Möglichkeiten einer Netzwerkfreigabe hinausgehen (Suche, Sammlungen, Metadaten, Zusammenarbeit, Vorschauen usw.). Außerdem bietet AEM Desktop App einen praktischen Link zur Verbindung des serverseitigen DAM-Repositorys mit Arbeiten auf dem Desktop.

Vermeiden Sie die Verwendung der AEM-Desktop-App zum Verwalten von Assets direkt im Netzwerk von AEM Assets. Vermeiden Sie beispielsweise die Verwendung der AEM-Desktop-App zum Verschieben/Kopieren mehrerer Dateien. Verwenden Sie stattdessen die Web-Benutzeroberfläche von AEM Assets, um Ordner aus dem Finder/Explorer in die Netzwerkfreigabe zu ziehen, oder verwenden Sie die Funktion „Ordner hochladen“ von AEM Assets.

#### Asset-Migration {#asset-migration}

Informationen zum Planen und Ausführen von Asset-Migrationen von vorhandenen Systemen in ein neues System oder Migrieren großer Mengen von auf Servern gespeicherten Assets finden Sie im [Migrationshandbuch](/help/assets/assets-migration-guide.md). AEM Desktop App und Integrationen aus AEM in Creative Cloud unterstützen keine derartigen Migrationen. Aufgrund der großen Menge an aufzunehmenden Assets und der zusätzlichen Anforderungen rund um Metadatenzuordnungen, Transformationen und Aufnahmen sollten Migrationen mithilfe anderer Tools und Ansätze erfolgen.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [Optimale Vorgehensweise für AEM Desktop App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [Integration von AEM und Adobe Stock](aem-assets-adobe-stock.md)

