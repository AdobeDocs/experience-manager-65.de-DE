---
title: Best Practices zur Integration mit Adobe Creative Cloud
description: Best Practices für die Integration von [!DNL Adobe Experience Manager] und [!DNL Adobe Creative Cloud] zur Optimierung der Workflows für die Asset-Übertragung und Erzielung einer hohen Content-Geschwindigkeit.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin
feature: Collaboration,Adobe Asset Link,Desktop App
exl-id: c7d589a3-1c5f-4ff0-879e-15e1c556f6dc
hide: true
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '3263'
ht-degree: 94%

---

# Best Practices für die Integration von [!DNL Adobe Experience Manager] und [!DNL Creative Cloud] {#aem-and-creative-cloud-integration-best-practices}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/aem-cc-integration-best-practices.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

[!DNL Adobe Experience Manager Assets] ist eine DAM-Lösung (Digital Asset Management), die mit [!DNL Adobe Creative Cloud] integriert werden kann, um DAM-Benutzende bei der Zusammenarbeit mit Kreativ-Teams zu unterstützen und so die Kooperation beim Erstellen von Inhalten zu optimieren.

[!DNL Adobe Creative Cloud] bietet Kreativ-Teams ein System von Lösungen und Services, um digitale Assets zu erstellen. Dazu gehören Desktop- und Mobilanwendungen, Cloud-Services wie Speicher mit Desktop-Synchronisierung oder Web-Erlebnis sowie Marktplätze wie [!DNL Adobe Stock].

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>Die Freigabe von Ordnern aus [!DNL Experience Manager] in [!DNL Creative Cloud] ist veraltet und wird in diesem Handbuch nicht mehr behandelt. Adobe empfiehlt die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=de), um Kreativprofis Zugriff auf Assets zu gewähren, die in [!DNL Experience Manager] verwaltet werden.

## Kooperationsanforderungen von Kreativen, Marketern und DAM-Benutzenden {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Nutzungsszenario | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Für Kreativprofis oder allgemein für Desktop-Benutzer, die mit nativen Anwendungen zur Asset-Erstellung arbeiten, soll der Zugriff auf Assets von einem DAM-System ([!DNL Experience Manager Assets]) optimiert werden. Sie benötigen eine einfache und einfache Möglichkeit, Änderungen zu finden, zu verwenden (zu öffnen), zu bearbeiten und zu speichern. [!DNL Experience Manager]und laden Sie neue Dateien hoch. | Windows- oder Mac-Desktop; [!DNL Creative Cloud]-Programme |
| Bereitstellen von hochwertigen, gebrauchsfertigen Assets aus [!DNL Adobe Stock] | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | [!DNL Experience Manager Assets]; Marktplatz [!DNL Adobe Stock]; Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/lokale Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation gemeinsam genutzt werden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | Brand Portal, Asset Share Commons |

## Adobe-Angebote zur Unterstützung von Kooperationsbedarf {#adobe-offerings-to-support-the-collaboration-need}

| Wertvorschlag für die beteiligten Rollen | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Kreative Benutzer können Assets aus [!DNL Experience Manager], öffnen und verwenden Sie sie, bearbeiten und laden Sie Änderungen in hoch. [!DNL Experience Manager], und laden Sie neue Dateien in hoch. [!DNL Experience Manager], ohne [!DNL Creative Cloud] Apps. | [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) | [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign]. |
| Business-Anwender vereinfachen das Öffnen und Verwenden von Assets, das Bearbeiten und Hochladen von Änderungen in [!DNL Experience Manager] sowie das Hochladen neuer Dateien aus der Desktop-Umgebung in [!DNL Experience Manager]. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Programmen zu öffnen, auch von anderen Anbietern als Adobe. | [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de) | [!DNL Experience Manager] Desktop App auf Windows- und Mac-Desktop |
| Marketer und Business-User können [!DNL Adobe Stock]-Assets in [!DNL Experience Manager] identifizieren, in einer Vorschau anzeigen, lizenzieren sowie speichern und verwalten. Lizenzierte und gespeicherte Assets liefern ausgewählte [!DNL Adobe Stock]-Metadaten für eine bessere Governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager]-Web-Oberfläche |

Dieser Artikel konzentriert sich in erster Linie auf die ersten beiden Aspekte der Zusammenarbeit. Die Verteilung und Beschaffung von Vermögenswerten im entsprechende Maß wird kurz als Verwendungsfall genannt. Für solche Lösungen sollten Sie Adobe Brand Portal oder Asset Share Commons beachten. Alternative Lösungen wie [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de), Lösungen, die auf Basis von [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Komponenten oder [Link-Freigabe](/help/assets/link-sharing.md) mithilfe von [Experience Manager Assets](/help/assets/manage-assets.md) erstellt werden können, sind auf Grundlage der spezifischen Anforderungen zu prüfen.

![Creative Cloud-Verbindungen für Experience Manager, Festlegen der zu verwendenden Funktion](assets/creative-connections-aem.png)

### Zuordnen von Nutzungsszenarien und Adobe-Lösungen {#mapping-of-use-cases-and-adobe-solutions}

<!-- TBD: Add some info about XD integration and possibly info about DA v2.0.
-->

| Nutzungsszenario | [!DNL Adobe Asset Link] | [!DNL Experience Manager]-Desktop-Programm | Anmerkungen/sonstige Lösungen |
|---|---|---|---|
| Entdecken – Durchsuchen von DAM-Ordnern | Ja | [!DNL Experience Manager]-Web-Oberfläche und Desktop-Aktionen | |
| Entdecken – Zugreifen auf DAM-Sammlungen | Ja | [!DNL Experience Manager]-Web-Oberfläche und Desktop-Aktionen | |
| Entdecken – Suchen nach Assets aus DAM | Ja | [!DNL Experience Manager]-Web-Oberfläche und Desktop-Aktionen | |
| Verwenden – Asset öffnen | Ja | Ja | [Öffnen über die Web-Benutzeroberfläche](manage-assets.md#previewing-assets) oder den Finder |
| Verwenden – Platzieren von Assets aus DAM in ein Dokument | Ja – Einbetten | Ja – Verknüpfen oder Einbetten | [!DNL Experience Manager] Desktop App ermöglicht den Zugriff auf Assets als Dateien im lokalen Dateisystem. Diese Links in den nativen Programmen werden durch lokale Pfade dargestellt. |
| Bearbeiten – zur Bearbeitung öffnen | Ja – Aktion zum Auschecken | Ja – Aktion zum Öffnen (über die Netzwerkfreigabe) | Beim [Checkout in AAL](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) wird standardmäßig das Asset für das Creative Cloud-Speicherkonto des Benutzers (synchronisiert durch das Creative Cloud-Programm) gespeichert. |
| Bearbeiten – laufende Arbeiten außerhalb von DAM | Ja – Asset im mit dem Desktop synchronisierten Creative Cloud-Speicherkonto des Benutzers verfügbar. | Ja | |
| Bearbeiten – Änderungen hochladen | Ja – [Aktion zum Einchecken](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) mit optionalem Kommentar | Ja | |
| Hochladen – einzelne Datei | Ja – lädt das aktuelle aktive Dokument hoch | Ja | [Hochladen über die Web-Oberfläche](manage-assets.md#uploading-assets) |
| Hochladen – mehrere Dateien / hierarchische Ordnerstrukturen | Nein | Ja | [Hochladen über die Web-Oberfläche](manage-assets.md#uploading-assets) oder über ein benutzerdefiniertes Skript oder Tool. |
| Sonstiges – Benutzende und Anmeldung | Erkennung des Creative Cloud-Benutzers, der beim Creative Cloud-Desktop-Programm angemeldet ist (SSO) | [!DNL Experience Manager]-Benutzende und Anmeldedaten | Benutzende beider Lösungen werden auf das [!DNL Experience Manager]-Benutzerkontingent angerechnet. |
| Sonstiges – Netzwerk und Zugriff | Zugriff vom Desktop der Benutzenden auf die [!DNL Experience Manager]-Bereitstellung über das Netzwerk erforderlich | Zugriff vom Desktop der Benutzenden auf die [!DNL Experience Manager]-Bereitstellung über das Netzwerk erforderlich | [!DNL Adobe Asset Link] gibt keine Netzwerk-Proxy-Umgebung frei. |
| Sonstiges – Migrieren einer großen Anzahl von Assets | Nein | Nein | [Handbuch zur Assets-Migration](assets-migration-guide.md) |

Um Nutzungsszenarien zum Verteilen von Assets zu unterstützen, sollten andere Lösungen in Betracht gezogen werden:

* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de) für ein konfigurierbares SaaS-Add-on für [!DNL Experience Manager Assets] zum Veröffentlichen von Assets.
* Benutzerdefinierte Lösungen auf Grundlage der [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Code-Basis.
* [!DNL Experience Manager] [Linkfreigabe](/help/assets/link-sharing.md) , um Assets bei Bedarf über Links freizugeben.
* [Experience Manager Assets-Web-Oberfläche](/help/assets/manage-assets.md) mit Bereichen für externe Parteien, die über die [!DNL Experience Manager]-Zugriffssteuerung und mit notwendigen IT-/Netzwerkkonfigurationsanpassungen abgesichert sind, sodass diese externen Benutzenden Zugriff auf [!DNL Experience Manager] erhalten.

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **Fertige Kreativ-Assets:** [!DNL Assets], die für ein größeres Team freigegeben werden können oder die vom Kreativ-Team für die Freigabe mit Marketing- oder LOB-Teams ausgewählt oder genehmigt wurden.
* **Asset-Genehmigungen:** Der Genehmigungsprozess, der für Assets ausgeführt wird, die bereits auf DAM hochgeladen wurden. Dazu gehören in der Regel Markengenehmigungen, Genehmigungen usw.
* **Abgeschlossenes Asset:** Ein Asset, für das alle Genehmigungen/Metadaten-Tagging durchgeführt wurden und das bereit für die Verwendung durch das breitere Team ist. Ein solches Asset wird in DAM gespeichert und allen (bzw. allen interessierten) Benutzern zur Verfügung gestellt. Es kann in Marketing-Kanälen oder von Kreativ-Teams verwendet werden, um Designs zu erstellen.
* **Kleinere Asset-Aktualisierung/-Änderung:** Schnelle, kleine Änderung an einem digitalen Asset. Diese wird häufig aufgrund einer Retuschieranfrage oder einer kleineren Bearbeitungsanfrage, einer Asset-Überprüfung oder einer Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung der Sättigung/Helligkeit, Farbe usw.) durchgeführt.
* **Größere Asset-Aktualisierung/-Änderung:** Änderung eines digitalen Assets, die viel Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Diese umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrmals gespeichert werden. Bei umfangreichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase versetzt.
* **DAM:** Digital Asset Management. In diesem Dokument wird der Begriff synonym mit [!DNL Experience Manager Assets] verwendet, sofern nicht ausdrücklich anders angegeben.
* **Kreativer Benutzer:** Kreativprofi, der digitale Assets mit Creative Cloud-Programmen und -Services erstellt. In einigen Fällen kann ein kreativer Benutzer Mitglied eines Kreativ-Teams sein, das möglicherweise Creative Cloud verwendet, aber keine digitalen Assets erstellt (z. B. Creative Director oder Creative Team Manager).
* **DAM-Benutzer:** Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder ein Nicht-Marketing-Benutzer sein, z. B. ein &quot;Line-of-Business&quot;(LOB)-Benutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Überlegungen zur Integration von [!DNL Experience Manager] und [!DNL Creative Cloud]○ {#considerations-when-using-aem-and-creative-cloud-integration}

* Siehe [Best Practices für das Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=de#best-practices-to-prevent-troubles)
* Siehe [Adobe Stock-Integration](aem-assets-adobe-stock.md)
* Siehe [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)

Dies ist eine kurze Zusammenfassung von Best Practices für die Integration von [!DNL Experience Manager] und [!DNL Creative Cloud]. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für Kreativprofis, die in Photoshop, InDesign oder Illustrator arbeiten:** Adobe Asset Link bietet ein optimales Benutzererlebnis, einschließlich der ordnungsgemäßen Abwicklung laufender Arbeiten an aus [!DNL Experience Manager] ausgecheckten Assets. 
* **Für einen vereinfachten Desktop-Zugriff auf Assets in beliebigen allgemeinen Dateiformaten oder Applikationen:** Verwenden Sie das [!DNL Experience Manager]-Desktop-Programm.
* **Verstehen, warum und wann Assets in DAM gespeichert werden:** Aktualisierungen, die dem größeren Team in Ihrer Organisation zur Verfügung zu stellen sind.
* **Beachten des Volumens freigegebener Assets:** Wenn Ihr Anwendungsfall die Asset-Verteilung ist, könnten Governance und Sicherheit die wichtigsten Aspekte sein. Erwägen Sie die Verwendung von Tools, die für eine skalierte Vorgehensweise entwickelt wurden, wie z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams genutzt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Programme keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugriff auf [!DNL Adobe Stock]-Assets aus [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[Die Integration von Experience Manager und Adobe Stock](/help/assets/aem-assets-adobe-stock.md) ermöglicht [!DNL Experience Manager]-Benutzenden die Suche, Vorschau, Lizenzierung und Speicherung von Assets aus [!DNL Adobe Stock] in [!DNL Experience Manager]. Lizenzierte und gespeicherte [!DNL Stock]-Assets verfügen über ausgewählte [!DNL Stock]-Metadaten, mit denen Suchvorgänge über zusätzliche Filter durchgeführt werden können.

Einige wichtige Punkte zu dieser Integration:

* Wenn Assets aus Adobe Stock in [!DNL Experience Manager] gespeichert werden, werden sie zu regulären [!DNL Assets]. Die Binärdateien werden im [!DNL Experience Manager]-Repository gespeichert. Einige zu [!DNL Adobe Stock] gehörige Metadaten werden für das Asset in [!DNL Experience Manager] gespeichert. Ansonsten verläuft die Erfassung wie bei jeder anderen Datei. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* Das in [!DNL Experience Manager] gespeicherte Asset ist eine Kopie, kein Link zurück zu [!DNL Adobe Stock].

**Arbeiten mit Assets, die aus [!DNL Adobe Stock] in [!DNL Experience Manager] in[!DNL Creative Cloud]** gespeichert wurden. Diese Integration ist unabhängig von [!DNL Adobe Asset Link], aber [!DNL Adobe Asset Link] erkennt diese Assets, die aus [!DNL Stock] gespeichert wurden, und zeigt zusätzliche Metadaten und ein [!DNL Adobe Stock]-Logo auf diesen Assets in der [!DNL Adobe Asset Link]-Erweiterungs-Benutzeroberfläche in [!DNL Photoshop], [!DNL Illustrator] oder [!DNL InDesign] an. Die Dateien sind zum Durchsuchen, Öffnen usw. verfügbar, da sie durch das Speichern in [!DNL Experience Manager] zu regulären Assets werden.
Kreativprofis, die in [!DNL Creative Cloud]-Programmen mit vorhandener[!DNL Adobe Asset Link]-Erweiterung arbeiten, haben zusätzlich zum Zugriff auf bereits lizenzierte Assets aus [!DNL Adobe Stock] in [!DNL Experience Manager] auch Zugriff auf das [!DNL Creative Cloud]-Libraries-Bedienfeld, um [!DNL Adobe Stock]-Assets zu suchen, in einer Vorschau anzuzeigen und zu lizenzieren.
[!DNL Assets] aus [!DNL Adobe Stock], die lizenziert und in [!DNL Experience Manager] gespeichert wurden, stehen umfangreicheren Teams zur Verfügung, die auf die [!DNL Experience Manager Assets]-Bereitstellung zugreifen. Kreativprofis hingegen, die Assets aus [!DNL Adobe Stock] über das [!DNL Creative Cloud]-Libraries-Bedienfeld lizenzieren, stehen die Assets standardmäßig lediglich in ihrem eigenen [!DNL Creative Cloud]-Konto zur Verfügung.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM introduction article.
-->

## Informationen zum Speichern von Assets in DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativ-Teams und Marketing-/Branchen-Teams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Dadurch wird sichergestellt, dass die Assets von zahlreichen Benutzenden im gesamten Unternehmen oder Ökosystem genutzt werden können, wozu Partnerinnen bzw. Partner, Kundinnen bzw. Kunden usw. gehören.

Die meisten Unternehmen entscheiden sich dafür, nur Assets zu speichern, die für nachgelagerte Marketing-/Branchenprozesse (Veröffentlichen in Kanälen wie dem Internet über [!DNL Experience Manager Sites] oder in anderen Kanälen wie Marketing Cloud oder Advertising Cloud, die von Adobe Experience Cloud bereitgestellt und von Analytics Cloud bewertet werden, Bereitstellung für Benutzende/Partnerinnen und Partner usw.) relevant sind. Darüber hinaus speichern Unternehmen in DAM Assets, die einem Überprüfungs-/Genehmigungsprozess unterzogen werden können. Auf diese Weise speichert DAM hauptsächlich Assets, die mit hoher Wahrscheinlichkeit genutzt werden, und vermeidet das Speichern inaktiver Assets.

Das Speichern von Assets unterliegt auch technischen Überlegungen und Überlegungen zur Ressourcenauslastung. DAM bietet zusätzliche Services rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Services erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist es nicht wünschenswert, alle Assets und Updates zu speichern. Wenn beispielsweise Aktualisierungen an bestimmten Assets von schlechter Qualität sind und übermäßige Ressourcen verbrauchen, werden die Assets möglicherweise nicht in DAM gespeichert.

#### Wann Assets in DAM gespeichert werden {#when-assets-are-stored-in-dam}

Kreativ-Teams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Sie vermeiden beispielsweise das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind oder getestet werden müssen.
* Assets, die den Prüfungszyklus des Kreativ-Teams/internen Teams nicht bestehen.
* Verglichen mit dem betreffenden Asset verfügt das Team über bessere Beispiele für seine Arbeit, um sie externen Teams vorzustellen.

Normalerweise werden die folgenden Klassen-Assets in DAM gespeichert:

* Assets, die eine bestimmte Laufzeit erreicht haben und als zur Freigabe bereit gelten.
* Assets, die vorab vom Kreativ-Team ausgewählt wurden.
* Bestimmte Asset-Formate, die vom Marketing-Team verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien).

#### Wann Aktualisierungen von Assets in DAM gespeichert werden {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzenden relevant sind. Dadurch wird sichergestellt, dass Benutzende (Marketing- und ähnliche Funktionen) nur relevante Versionen in der DAM-Asset-Timeline sehen.

Normalerweise handelt es sich um Änderungen im Zusammenhang mit wichtigen Meilensteinen im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Marketing-Asset oder eine offizielle Aktualisierung basierend auf Anfragen/Überprüfungen durch das Kreativ-Team in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativ-Teams zur Überprüfung durch das Marketing-Team nach einer Änderungsanfrage für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Sie sollte in DAM gespeichert und versioniert werden, um weitere Informationen zu erhalten oder zur vorherigen Version zurückzukehren.

Im Folgenden finden Sie Beispiele für Aktualisierungen, die normalerweise nicht relevant sind:

* Frühzeitige Versionen von Assets, die hochgeladen wurden, bevor sie zur Marketing-Überprüfung bereit sind
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor die Kreativ- und Marketing-Teams das Asset für fertig erklären

### Benutzerzugriff auf DAM {#user-access-to-dam}

[!DNL Assets] unterstützt zwei Arten von Benutzenden, basierend auf deren Zugriff auf die [!DNL Assets]-Bereitstellung. Normalerweise haben Benutzende im Unternehmensnetzwerk (Firewall) direkten Zugriff auf DAM. Andere Benutzende außerhalb des Unternehmensnetzwerks hätten keinen direkten Zugriff. Der Benutzertyp bestimmt aus technischer Sicht, welche Integrationen verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM {#creative-users-with-direct-access-to-dam}

Normalerweise haben interne Kreativ-Teams oder Agenturen/Kreativprofis, die in das interne Netzwerk eingegliedert sind, Zugriff auf die DAM-Bereitstellung, einschließlich [!DNL Experience Manager]-Anmeldung. [!DNL Experience Manager] und die Netzwerkinfrastruktur eingerichtet werden, um externen Parteien - normalerweise vertrauenswürdige Organisationen wie Agenturen, die für einen Kunden arbeiten - direkten Zugriff zu ermöglichen, damit sie Zugriff auf [!DNL Experience Manager] über das Netzwerk, beispielsweise über VPN oder IP-Zulassungsliste.

In solchen Fällen bietet Adobe Asset Link oder das [!DNL Experience Manager]-Desktop-Programm einfachen Zugriff auf abgeschlossene/genehmigte Assets und ermöglicht das Speichern fertiger Kreativ-Assets in DAM.

#### Kreativprofis ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen oder Freiberufler ohne direkten Zugriff auf die DAM-Bereitstellung benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs in DAM hinzufügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* Verwenden des Desktop-Programms, wenn Asset Link nicht funktioniert.
* Verwenden von [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de), um Assets sicher an externe Partner zu verteilen.
* Verwenden einer benutzerdefinierten Implementierung eines Verteilungs- und Quellportals auf Basis von [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* Verwenden der in [!DNL Experience Manager] eingerichteten Zugriffssteuerung und der erforderlichen Netzwerkinfrastruktur (z. B. VPN und IP-Zulassungsliste), um externen Parteien Zugriff auf einen speziellen Inhaltsbereich in Ihrem DAM-System zu gewähren. Sie können über die [!DNL Experience Manager]-Web-Benutzeroberfläche Assets abrufen und neue Inhalte in Ihr DAM-System hochladen.

#### Laufende Arbeiten an Assets über [!DNL Experience Manager] {#work-in-progress-on-assets-from-aem}

Wie in diesem Dokument erläutert, wird empfohlen, umfangreiche Aktualisierungen für Assets, auch als laufende Arbeiten bezeichnet, durchzuführen, ohne dass alle in der lokalen Datei gespeicherten Bearbeitungen ebenfalls als Änderungen in [!DNL Experience Manager] hochgeladen werden. Dies beschleunigt die Arbeit von Desktop-Benutzern, schränkt die verwendete Netzwerkbandbreite ein und sorgt dafür, dass die Assets-Zeitleiste „sauber“ bleibt und auf kontrollierte, größere Aktualisierungen ausgerichtet ist.

Adobe Asset Link bietet eine gute Unterstützung für diesen Anwendungsfall:

* Wenn Benutzende in [!DNL Photoshop], [!DNL InDesign] oder [!DNL Illustrator] eine Datei bearbeiten möchten, checken sie das jeweilige Asset aus.
* Das Asset wird im Hintergrund heruntergeladen und in die vom Creative Cloud-Desktop-Programm mit der Festplatte synchronisierten Creative Cloud-Konten der Benutzenden platziert. In [!DNL Experience Manager] wird die Checkout-Markierung auf dem Asset umgeschaltet, um Bearbeitungskonflikte zu minimieren.
* Von dort aus arbeiten die Benutzenden in einer Datei, die lokal am synchronisierten Speicherort gespeichert ist, und können in beliebiger Häufigkeit weiterarbeiten und notwendige Änderungen speichern
* Da sich das Asset im Creative Cloud-Konto befindet, ist es auch auf etwaigen anderen Benutzergeräten verfügbar (z. B. zum Öffnen oder Bearbeiten in einer dedizierten Creative Cloud-Mobile-App). Außerdem kann es für andere Creative Cloud-Benutzer zwecks Zusammenarbeit freigegeben werden.
* Wenn kreative Benutzer keine weiteren Änderungen vornehmen möchten, können sie diese Datei in ihrem Creative Cloud-Programm mit einem optionalen Kommentar einchecken. Das entsprechende Asset in [!DNL Experience Manager] wird versioniert und mit der neuen Binärdatei aktualisiert. [!DNL Experience Manager]-Benutzende wie Marketer oder Branchenbenutzende haben über die Zeitleisten-Benutzeroberfläche von [!DNL Experience Manager] Assets Zugriff auf wichtige Asset-Änderungen oder Meilensteine.

[!DNL Experience Manager] Desktop App bietet eine Netzwerkfreigabe für in der nativen App geöffnete Assets. Standardmäßig werden alle lokalen Änderungen nach kurzer Zeit automatisch in [!DNL Experience Manager] hochgeladen. Mit einer solchen Konfiguration werden häufig gespeicherte Inhalte während der laufenden Arbeit in [!DNL Experience Manager] hochgeladen und versioniert, sodass beträchtlicher Netzwerk-Traffic und potenzielle Herausforderungen mit der Skalierbarkeit entstehen – ganz zu schweigen von den unnötigen Versionen in [!DNL Experience Manager].

Es wird empfohlen, hier eine Option in [!DNL Experience Manager] Desktop-Programm zum Deaktivieren automatisierter Aktualisierungen und zum Hochladen von Änderungen in Assets in [!DNL Experience Manager] manuell mithilfe der Aktion zum Hochladen von Änderungen in der Asset Status-Benutzeroberfläche des Programms.

#### Massen-Upload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von Foto-Shootings oder größeren Projekten
* Hochladen von Assets von Kreativagenturen
* Hochladen ausgewählter Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Die Beschreibung bezieht sich auf das betriebsbedingte Hochladen von Dateien (z. B. jede Woche oder bei jedem Foto-Shooting) als normaler Teil des Workflows von Desktop-Benutzenden. Große Asset-Migrationen werden hier nicht behandelt.

Sie können die folgenden Upload-Funktionen nutzen:

* Um große/hierarchische Ordner stapelweise hochzuladen, verwenden Sie das [!DNL Experience Manager]-Desktop-Programm mit Funktionen zum [Hochladen von Ordnern](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#upload-and-add-new-assets-to-aem). Sie können auch hierarchische Ordnerstrukturen hochladen. Das Hochladen von [!DNL Assets] erfolgt im Hintergrund und ist daher nicht an eine Webbrowser-Sitzung gebunden.
* Wenn Sie mehrere Dateien aus einem einzelnen Ordner hochladen möchten, ziehen Sie die Dateien direkt in die Web-Oberfläche oder verwenden Sie die Option „Erstellen“ in der Web-Benutzeroberfläche von [!DNL Assets].
* Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Upload-Programme verwenden.

#### Verwalten digitaler Assets direkt auf dem Desktop {#managing-digital-assets-directly-from-desktop}

Wenn Sie digitale Assets mithilfe von Netzwerk-Dateifreigaben verwalten, kann stattdessen einfach die über das [!DNL Experience Manager]-Desktop-Programm zugeordnete Netzwerkfreigabe verwendet werden. Beim Übergang von Netzwerk-Dateifreigaben stellt die Web-Benutzeroberfläche von [!DNL Experience Manager] einen umfangreichen Satz von Digital-Asset-Management-Funktionen bereit, die weit über die Möglichkeiten einer Netzwerkfreigabe hinausgehen (Suche, Sammlungen, Metadaten, Zusammenarbeit, Vorschauen usw.). Außerdem bietet das [!DNL Experience Manager]-Desktop-Programm einen praktischen Link zur Verbindung des Server-seitigen DAM-Repositorys mit Arbeiten auf dem Desktop.

Verwenden Sie das [!DNL Experience Manager]-Desktop-Programm nicht für die direkte Verwaltung von Assets in der Netzwerkfreigabe von [!DNL Assets]. Vermeiden Sie beispielsweise die Verwendung des [!DNL Experience Manager]-Desktop-Programms zum Verschieben/Kopieren mehrerer Dateien. Verwenden Sie stattdessen die Web-Benutzeroberfläche von [!DNL Assets], um Ordner aus dem Finder/Explorer in die Netzwerkfreigabe zu ziehen, oder verwenden Sie die Funktion „Ordner hochladen“ von [!DNL Assets].

#### Asset-Migration {#asset-migration}

Informationen zum Planen und Ausführen von Asset-Migrationen von einem vorhandenen System auf ein neues System oder zum Migrieren einer großen Menge von auf Servern gespeicherten Assets finden Sie unter [Migrationshandbuch](/help/assets/assets-migration-guide.md). [!DNL Experience Manager]-Desktop-Programm und Integrationen aus [!DNL Experience Manager] in [!DNL Creative Cloud] unterstützen keine derartigen Migrationen. Aufgrund der großen Menge an aufzunehmenden Assets und der zusätzlichen Anforderungen rund um Metadatenzuordnungen, Transformationen und Aufnahmen sollten Migrationen mithilfe anderer Tools und Ansätze erfolgen.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)
>* [Best Practices für das Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html?lang=de)
>* [Experience Manager Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=de)
>* [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md)
