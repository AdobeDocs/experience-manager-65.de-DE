---
title: Integration mit Best Practices für Adobe Creative Cloud
description: Best Practices zur Integration [!DNL Adobe Experience Manager] mit [!DNL Adobe Creative Cloud] Optimierung der Workflows für die Asset-Übertragung und Erzielung einer hohen Content-Geschwindigkeit.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin
feature: Collaboration,Adobe Asset Link,Desktop App
exl-id: c7d589a3-1c5f-4ff0-879e-15e1c556f6dc
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '3280'
ht-degree: 57%

---

# [!DNL Adobe Experience Manager] und [!DNL Creative Cloud] Best Practices für die Integration {#aem-and-creative-cloud-integration-best-practices}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/aem-cc-integration-best-practices.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-integration-best-practices.html?lang=en) |

[!DNL Adobe Experience Manager Assets] ist eine Digital Asset Management (DAM)-Lösung, die in integriert werden kann. [!DNL Adobe Creative Cloud] , um DAM-Benutzer bei der Zusammenarbeit mit Kreativteams zu unterstützen und so die Zusammenarbeit bei der Inhaltserstellung zu optimieren.

[!DNL Adobe Creative Cloud] bietet Kreativ-Teams ein System von Lösungen und Services, um digitale Assets zu erstellen. Dazu gehören Desktop- und Mobilanwendungen, Cloud-Services wie Speicher mit Desktop-Synchronisierung oder Web-Erlebnis sowie Marktplätze wie [!DNL Adobe Stock].

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>[!DNL Experience Manager] nach [!DNL Creative Cloud] Die Ordnerfreigabe wird nicht mehr unterstützt und in diesem Handbuch nicht mehr behandelt. Adobe empfiehlt die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html) , um kreativen Benutzern Zugriff auf Assets zu gewähren, die in verwaltet werden. [!DNL Experience Manager].

## Kooperationsanforderungen von Kreativen, Marketing-Experten und DAM-Benutzern {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Nutzungsszenario | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Für Kreativprofis oder allgemein für Desktop-Benutzer, die mit nativen Anwendungen zur Asset-Erstellung arbeiten, soll der Zugriff auf Assets von einem DAM-System ([!DNL Experience Manager Assets]) optimiert werden. Sie benötigen eine einfache und einfache Möglichkeit, Änderungen zu finden, zu verwenden (zu öffnen), zu bearbeiten und zu speichern. [!DNL Experience Manager]und laden Sie neue Dateien hoch. | Windows- oder Mac-Desktop; [!DNL Creative Cloud] apps |
| Bereitstellen von hochwertigen, gebrauchsfertigen Assets aus [!DNL Adobe Stock] | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | [!DNL Experience Manager Assets]; Marktplatz [!DNL Adobe Stock]; Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation freigegeben wurden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | Brand Portal, Asset Share Commons |

## Adobe-Angebote zur Unterstützung von Kooperationsbedarf {#adobe-offerings-to-support-the-collaboration-need}

| Wertangebot für die betroffenen Benutzer | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Kreative Benutzer können Assets aus [!DNL Experience Manager], öffnen und verwenden Sie sie, bearbeiten und laden Sie Änderungen in hoch. [!DNL Experience Manager], und laden Sie neue Dateien in hoch. [!DNL Experience Manager], ohne [!DNL Creative Cloud] Apps. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign]. |
| Business-Anwender vereinfachen das Öffnen und Verwenden von Assets, das Bearbeiten und Hochladen von Änderungen in [!DNL Experience Manager] sowie das Hochladen neuer Dateien aus der Desktop-Umgebung in [!DNL Experience Manager]. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Programmen zu öffnen, auch von anderen Anbietern als Adobe. | [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] Desktop App auf Windows- und Mac-Desktop |
| Marketingexperten und Geschäftsbenutzer können die [!DNL Adobe Stock] Assets aus [!DNL Experience Manager]. Lizenzierte und gespeicherte Assets bieten Auswahl [!DNL Adobe Stock] Metadaten für bessere Governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager]-Web-Oberfläche |

Dieser Artikel konzentriert sich in erster Linie auf die ersten beiden Aspekte der Zusammenarbeit. Die Verteilung und Beschaffung von Vermögenswerten im entsprechende Maß wird kurz als Verwendungsfall genannt. Für solche Lösungen sollten Sie Adobe Brand Portal oder Asset Share Commons beachten. Alternative Lösungen wie [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de), Lösungen, die basierend auf [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) Komponenten, [Linkfreigabe](/help/assets/link-sharing.md)verwendet [Experience Manager Assets](/help/assets/manage-assets.md) auf der Grundlage einer spezifischen Anforderung überprüft werden.

![Creative Cloud-Verbindungen für Experience Manager entscheiden, welche Funktion verwendet werden soll](assets/creative-connections-aem.png)

### Zuordnen von Nutzungsszenarien und Adobe-Lösungen {#mapping-of-use-cases-and-adobe-solutions}

<!-- TBD: Add some info about XD integration and possibly info about DA v2.0.
-->

| Nutzungsszenario | [!DNL Adobe Asset Link] | [!DNL Experience Manager]-Desktop-Programm | Anmerkungen/sonstige Lösungen |
|---|---|---|---|
| Discover - DAM-Ordner durchsuchen | Ja | [!DNL Experience Manager] Web-Oberfläche und Desktop-Aktionen |  |
| Discover - Zugriff auf DAM-Sammlungen | Ja | [!DNL Experience Manager] Web-Oberfläche und Desktop-Aktionen |  |
| Discover - Suchen nach Assets aus DAM | Ja | [!DNL Experience Manager] Web-Oberfläche und Desktop-Aktionen |  |
| Verwenden – Öffnen von Assets | Ja | Ja | [Öffnen über die Web-Benutzeroberfläche](manage-assets.md#previewing-assets) oder den Finder |
| Verwenden - Platzieren von Assets aus DAM in einem Dokument | Ja – Einbetten | Ja – Verknüpfen oder Einbetten | [!DNL Experience Manager] Desktop App ermöglicht den Zugriff auf Assets als Dateien im lokalen Dateisystem. Diese Links in den nativen Programmen werden durch lokale Pfade dargestellt. |
| Bearbeiten – Öffnen zur Bearbeitung | Ja – Checkout-Aktion | Ja – Öffnen-Aktion (über die Netzwerkfreigabe) | Beim [Checkout in AAL](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) wird standardmäßig das Asset für das Creative Cloud-Speicherkonto des Benutzers (synchronisiert durch das Creative Cloud-Programm) gespeichert. |
| Bearbeiten - laufende Arbeiten außerhalb von DAM | Ja – Asset im mit dem Desktop synchronisierten Creative Cloud-Speicherkonto des Benutzers verfügbar. | Ja |  |
| Bearbeiten – Hochladen von Änderungen | Ja – [Checkin-Aktion](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) mit optionalem Kommentar | Ja |  |
| Hochladen – einzelne Datei | Ja – Hochladen des aktuellen aktiven Dokuments | Ja | [Hochladen über die Web-Oberfläche](manage-assets.md#uploading-assets) |
| Hochladen – mehrere Dateien/hierarchische Ordnerstrukturen | Nein | Ja | [Hochladen über die Web-Oberfläche](manage-assets.md#uploading-assets) oder über ein benutzerdefiniertes Skript oder Tool. |
| Sonstiges – Benutzer und Anmeldung | Erkennung des Creative Cloud-Benutzers, der beim Creative Cloud-Desktop-Programm angemeldet ist (SSO) | [!DNL Experience Manager] Benutzer und Berechtigungen | Die Benutzer beider Lösungen zählen auf die [!DNL Experience Manager] Benutzerkontingent. |
| Sonstiges – Netzwerk und Zugriff | Erfordert Zugriff vom Desktop des Benutzers auf [!DNL Experience Manager] Netzwerkbereitstellung | Erfordert Zugriff vom Desktop des Benutzers auf [!DNL Experience Manager] Netzwerkbereitstellung | [!DNL Adobe Asset Link] gibt keine Netzwerk-Proxy-Umgebung frei. |
| Sonstiges – Migrieren einer großen Anzahl von Assets | Nein | Nein | [Handbuch zur Asset-Migration](assets-migration-guide.md) |

Um Nutzungsszenarien zum Verteilen von Assets zu unterstützen, sollten andere Lösungen in Betracht gezogen werden:

* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) für ein konfigurierbares SaaS-Add-on auf [!DNL Experience Manager Assets] , um Assets zu veröffentlichen.
* Benutzerdefinierte Lösungen auf Grundlage der [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Code-Basis.
* [!DNL Experience Manager][-Linkfreigabe](/help/assets/link-sharing.md), um Assets ad hoc mithilfe von Links freizugeben.
* [Experience Manager Assets-Webschnittstelle](/help/assets/manage-assets.md) mit Gebieten für externe Parteien, die durch [!DNL Experience Manager] Einrichtung der Zugriffskontrolle und mit den erforderlichen IT-/Netzwerkkonfigurationsanpassungen, die diesen externen Benutzern Zugriff auf [!DNL Experience Manager].

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **Kreativ fertige Assets:** [!DNL Assets] die für ein breiteres Team freigegeben werden können oder vom Kreativteam für die Freigabe mit Marketing- oder LOB-Teams ausgewählt oder genehmigt wurden.
* **Asset-Genehmigungen:** Der Genehmigungsprozess, der für Assets ausgeführt wird, die bereits auf DAM hochgeladen wurden. Dazu gehören in der Regel Markengenehmigungen, Genehmigungen usw.
* **Abgeschlossenes Asset:** Ein Asset, für das alle Genehmigungen/Metadaten-Tagging durchgeführt wurden und das bereit für die Verwendung durch das breitere Team ist. Ein solches Asset wird in DAM gespeichert und allen (bzw. allen interessierten) Benutzern zur Verfügung gestellt. Es kann in Marketing-Kanälen oder von Kreativ-Teams verwendet werden, um Designs zu erstellen.
* **Kleinere Asset-Aktualisierung/-Änderung:** Schnelle, kleine Änderung an einem digitalen Asset. Diese wird häufig aufgrund einer Retuschieranfrage oder einer kleineren Bearbeitungsanfrage, einer Asset-Überprüfung oder einer Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung der Sättigung/Helligkeit, Farbe usw.) durchgeführt.
* **Größere Asset-Aktualisierung/-Änderung:** Änderung eines digitalen Assets, die viel Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Diese umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrmals gespeichert werden. Bei umfangreichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase versetzt.
* **DAM:** Digital Asset Management. In diesem Dokument ist es gleichbedeutend mit [!DNL Experience Manager Assets], sofern nicht ausdrücklich anders angegeben.
* **Kreativer Benutzer:** Kreativprofi, der digitale Assets mit Creative Cloud-Programmen und -Services erstellt. In einigen Fällen kann ein kreativer Benutzer Mitglied eines Kreativ-Teams sein, das möglicherweise Creative Cloud verwendet, aber keine digitalen Assets erstellt (z. B. Creative Director oder Creative Team Manager).
* **DAM-Benutzer:** Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder Nicht-Marketing-Benutzer sein, z. B. Branchenbenutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Überlegungen zur Verwendung von [!DNL Experience Manager] und [!DNL Creative Cloud] Integration {#considerations-when-using-aem-and-creative-cloud-integration}

* Siehe [Best Practices für das Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Siehe [Adobe Stock-Integration](aem-assets-adobe-stock.md)
* Weitere Informationen finden Sie unter [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Dies ist eine kurze Zusammenfassung der Best Practices für [!DNL Experience Manager] und [!DNL Creative Cloud] Integration. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für kreative Benutzer, die in Photoshop, InDesign oder Illustrator arbeiten:** Adobe Asset Link bietet das beste Benutzererlebnis, einschließlich der ordnungsgemäßen Handhabung der laufenden Arbeiten an Assets, die aus ausgecheckt wurden [!DNL Experience Manager].
* **So vereinfachen Sie den Zugriff auf Assets vom Desktop aus für beliebige allgemeine Dateiformate oder Anwendungen:** use [!DNL Experience Manager] Desktop-Programm.
* **Verstehen Sie, warum und wann Assets in DAM gespeichert werden:** Aktualisierungen, die dem breiteren Team in Ihrer Organisation zur Verfügung gestellt werden.
* **Beachten des Volumens freigegebener Assets:** Wenn Ihr Anwendungsfall die Asset-Verteilung ist, könnten Governance und Sicherheit die wichtigsten Aspekte sein. Erwägen Sie die Verwendung von Tools, die für eine skalierte Vorgehensweise entwickelt wurden, wie z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams genutzt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Programme keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugriff auf [!DNL Adobe Stock] Assets aus [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[Integration von Experience Manager und Adobe Stock](/help/assets/aem-assets-adobe-stock.md) stellt [!DNL Experience Manager] Benutzer mit der Möglichkeit, Assets aus zu suchen, eine Vorschau anzuzeigen, zu lizenzieren und zu speichern [!DNL Adobe Stock] in [!DNL Experience Manager]. Lizenziert und gespeichert [!DNL Stock] Assets wurden ausgewählt [!DNL Stock] Metadaten, die verwendet werden können, um mit zusätzlichen Filtern nach ihnen zu suchen.

Einige wichtige Punkte zu dieser Integration:

* Wenn Assets aus dem Adobe-Bestand in gespeichert werden [!DNL Experience Manager], werden sie zu regulären [!DNL Assets], wobei die Binärdatei im [!DNL Experience Manager] Repository. Einige Metadaten für [!DNL Adobe Stock] für das Asset in gespeichert werden. [!DNL Experience Manager], andernfalls sieht der Aufnahmevorgang genauso aus wie bei jeder anderen Datei. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* Das Asset, das in gespeichert wurde [!DNL Experience Manager] ist eine Kopie, kein Link zurück in [!DNL Adobe Stock].

**Arbeiten mit Assets, die aus gespeichert wurden [!DNL Adobe Stock] in [!DNL Experience Manager] in[!DNL Creative Cloud]**. Diese Integration ist unabhängig von [!DNL Adobe Asset Link], aber [!DNL Adobe Asset Link] erkennt diese Assets, die in gespeichert wurden [!DNL Stock] Auf diese Weise werden zusätzliche Metadaten und ein [!DNL Adobe Stock] Logo auf diesen Assets in [!DNL Adobe Asset Link] Erweiterungs-Benutzeroberfläche in [!DNL Photoshop], [!DNL Illustrator]oder [!DNL InDesign]. Die Dateien stehen zum Durchsuchen, Öffnen usw. zur Verfügung, da es sich bei ihnen um normale Assets handelt, wenn sie in gespeichert werden [!DNL Experience Manager].
Kreative Benutzer, die in [!DNL Creative Cloud] Apps mit [!DNL Adobe Asset Link] Erweiterung vorhanden, zusätzlich zum Zugriff auf bereits lizenzierte Assets von [!DNL Adobe Stock] in [!DNL Experience Manager]kann auch [!DNL Creative Cloud] Bibliotheksbedienfeld zum Suchen, Anzeigen einer Vorschau und Lizenzieren [!DNL Adobe Stock] Assets.
[!DNL Assets] von [!DNL Adobe Stock] lizenziert und gespeichert in [!DNL Experience Manager] für breitere Teams verfügbar sein, die auf [!DNL Experience Manager Assets] Bereitstellung, während Kreative Assets von lizenzieren [!DNL Adobe Stock] via [!DNL Creative Cloud] Das Bibliotheksbedienfeld stellt sie nur standardmäßig für sich selbst zur Verfügung [!DNL Creative Cloud] -Konto.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM introduction article.
-->

## Informationen zum Speichern von Assets in DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativ-Teams und Marketing-/Branchen-Teams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Es wird sichergestellt, dass die Assets von verschiedenen Benutzern in der gesamten Organisation oder im gesamten System genutzt werden, z. B. von Kunden, Partnern usw.

Die meisten Unternehmen speichern nur Assets, die für nachgelagerte Marketing-/LOB-Prozesse relevant sind (Veröffentlichen in Kanälen wie Webkanälen über [!DNL Experience Manager Sites] oder anderen Kanälen, die von Adobe Experience Cloud bereitgestellt werden - Marketing Cloud, Advertising Cloud, gemessen von Analytics Cloud, bereitgestellt für Benutzer/Partner usw.). Außerdem speichern Organisationen Assets, für die möglicherweise ein Prüfungs-/Genehmigungsprozess in DAM erfolgt. Auf diese Weise werden hauptsächlich Assets in DAM gespeichert, die mit hoher Wahrscheinlichkeiten genutzt werden, und das Speichern von Assets im Leerlauf wird vermieden.

Die Speicherung von Assets hängt außerdem von Überlegungen zu technischen Aspekten und zur Ressourcennutzung ab. DAM bietet zusätzliche Services rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Services erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist das Speichern aller Assets und Aktualisierungen nicht empfehlenswert. Beispiel: Wenn Aktualisierungen von schlechter Qualität sind und einen unverhältnismäßigen Ressourcenverbrauch aufweisen, sollten die Assets nicht in DAM gespeichert werden.

#### Wann Assets in DAM gespeichert werden {#when-assets-are-stored-in-dam}

Kreativ-Teams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Beispielsweise vermeiden sie das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind, oder zum Experimentieren verwendet werden.
* Assets, die den Prüfungszyklus des Kreativ-Teams/internen Teams nicht bestehen.
* Verglichen mit dem betreffenden Asset verfügt das Team über bessere Kandidaten, um seine Arbeit externen Teams vorzustellen.

In der Regel werden Assets der folgenden Klassen in DAM gespeichert:

* Assets, die einen bestimmten Reifegrad erreicht haben und als bereit zur Freigabe für andere Benutzer gelten.
* Assets, die vorab vom Kreativ-Team ausgewählt wurden.
* Bestimmte Asset-Formate, die vom Marketing-Team verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien).

#### Wann Aktualisierungen von Assets in DAM gespeichert werden {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzer relevant sind. Dadurch wird sichergestellt, dass Benutzern (Marketing- und ähnliche Funktionen) in der DAM-Asset-Zeitleiste nur relevante Versionen angezeigt werden.

Normalerweise handelt es sich dabei um Änderungen in Bezug auf die wichtigsten Meilensteine im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Marketing-Asset oder eine offizielle Aktualisierung basierend auf Anfragen/Überprüfungen durch das Kreativ-Team in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativ-Teams zur Überprüfung durch das Marketing-Team nach einer Änderungsanfrage für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Diese sollte als Referenzmaterial oder zum Zurücksetzen auf die letzte Version in DAM gespeichert und versioniert werden.

Es folgen Beispiele für Updates, die normalerweise nicht relevant sind:

* Frühe Versionen von Assets, die hochgeladen wurden, bevor sie für die Marketingüberprüfung bereit waren
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor die Kreativ- und Marketing-Teams das Asset für fertig erklären

### Benutzerzugriff auf DAM {#user-access-to-dam}

[!DNL Assets] unterstützt zwei Arten von Benutzern basierend auf ihrem Zugriff auf die [!DNL Assets] Implementierung. Normalerweise haben Benutzer innerhalb des Unternehmensnetzwerks (Firewall) direkten Zugriff auf DAM. Andere Benutzer außerhalb des Unternehmensnetzwerks haben dagegen keinen direkten Zugriff. Der Benutzertyp bestimmt, welche Integrationen aus technischer Sicht verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM {#creative-users-with-direct-access-to-dam}

Normalerweise haben interne Kreativ-Teams oder Agenturen/Kreativprofis, die in das interne Netzwerk im internen Netzwerk integriert sind, haben Zugriff auf die DAM-Bereitstellung, einschließlich [!DNL Experience Manager] anmelden. [!DNL Experience Manager] und die Netzwerkinfrastruktur eingerichtet werden, um externen Parteien - normalerweise vertrauenswürdige Organisationen wie Agenturen, die für einen Kunden arbeiten - direkten Zugriff zu ermöglichen, damit sie Zugriff auf [!DNL Experience Manager] über das Netzwerk, z. B. über VPN oder IP-Zulassungsliste.

In solchen Fällen ist die Adobe Asset Link oder [!DNL Experience Manager] Das -Desktop-Programm bietet einfachen Zugriff auf endgültige/genehmigte Assets und ermöglicht das Speichern von fertigen Kreativ-Assets in DAM.

#### Kreative Benutzer ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen und Freiberufler ohne direkten Zugriff auf die DAM-Bereitstellung benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs zum DAM hinzufügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* Verwenden des Desktop-Programms, wenn Asset Link nicht funktioniert.
* Verwenden von [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), um Assets sicher an externe Partner zu verteilen.
* Verwenden einer benutzerdefinierten Implementierung eines Verteilungs- und Quellportals auf Basis von [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* Einrichten der Zugriffssteuerung in [!DNL Experience Manager] und der erforderlichen Netzwerkinfrastruktur (z. B. VPN und IP-Zulassungsliste), um externen Parteien Zugriff auf einen speziellen Inhaltsbereich in Ihrem DAM zu gewähren. Sie können [!DNL Experience Manager] Web-Benutzeroberfläche , um Assets abzurufen und neue Inhalte in Ihr DAM hochzuladen.

#### Laufende Arbeiten an Assets über [!DNL Experience Manager] {#work-in-progress-on-assets-from-aem}

Wie in diesem Dokument erläutert, wird empfohlen, umfangreiche Aktualisierungen für Assets durchzuführen, die manchmal als laufende Arbeit bezeichnet werden, ohne dass alle Änderungen in der lokalen Datei ebenfalls in hochgeladen werden [!DNL Experience Manager] geändert. Dies beschleunigt die Arbeit von Desktop-Benutzern, schränkt die verwendete Netzwerkbandbreite ein und sorgt dafür, dass die Assets-Zeitleiste „sauber“ bleibt und auf kontrollierte, größere Aktualisierungen ausgerichtet ist.

Adobe Asset Link bietet eine gute Unterstützung für dieses Nutzungsszenario:

* Wenn Benutzer [!DNL Photoshop], [!DNL InDesign]oder [!DNL Illustrator] Um eine Datei zu bearbeiten, führen sie einen Checkout-Vorgang für das angegebene Asset aus
* Das Asset wird im Hintergrund heruntergeladen, in das Benutzerkonto übertragen, das mit dem Creative Cloud-Desktop-Programm auf dem Datenträger synchronisiert wurde, und das Checkout-Flag wird aktiviert [!DNL Experience Manager] auf dem Asset, um Bearbeitungskonflikte zu minimieren
* Von diesem Zeitpunkt an arbeiten die Benutzer in einer Datei, die lokal am synchronisierten Speicherort abgelegt ist. Sie können weiterarbeiten und die erforderlichen Änderungen so oft wie gewünscht speichern.
* Da sich das Asset im Creative Cloud-Konto befindet, ist es auch auf etwaigen anderen Benutzergeräten verfügbar (z. B. zum Öffnen oder Bearbeiten in einer dedizierten Creative Cloud-Mobile-App). Außerdem kann es für andere Creative Cloud-Benutzer zwecks Zusammenarbeit freigegeben werden.
* Wenn kreative Benutzer keine weiteren Änderungen vornehmen möchten, können sie diese Datei in ihrem Creative Cloud-Programm mit einem optionalen Kommentar einchecken. Das entsprechende Asset in [!DNL Experience Manager] werden versioniert und mit der neuen Binärdatei aktualisiert. [!DNL Experience Manager] Benutzer wie Marketingexperten oder LOB-Benutzer haben Zugriff auf wichtige Asset-Änderungen oder Meilensteine über [!DNL Experience Manager] Benutzeroberfläche der Asset-Timeline.

[!DNL Experience Manager] Desktop App bietet eine Netzwerkfreigabe für in der nativen App geöffnete Assets. Standardmäßig werden alle lokal vorgenommenen Änderungen in [!DNL Experience Manager] automatisch nach einer kurzen Zeit. Mit einer solchen Konfiguration würden häufige Speichervorgänge während der laufenden Phase in [!DNL Experience Manager] und versioniert sind, was zu einer Menge Netzwerk-Traffic und potenziellen Skalierbarkeitsproblemen führt - ganz zu schweigen von unnötigen Versionen in [!DNL Experience Manager].

Es wird empfohlen, hier eine Option in [!DNL Experience Manager] Desktop-Programm zum Deaktivieren automatisierter Aktualisierungen und zum Hochladen von Änderungen in Assets in [!DNL Experience Manager] manuell verwenden und die Aktion zum Hochladen von Änderungen in der Asset Status-Benutzeroberfläche des Programms nutzen.

#### Massen-Upload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von Fotoshootings oder größere Projekte
* Hochladen von Assets von Kreativagenturen
* Hochladen von Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Die Beschreibung bezieht sich auf das betriebsbedingte Hochladen von Dateien (z. B. jede Woche oder bei jedem Foto-Shooting) als normaler Teil des Workflows des Desktop-Benutzers. Das Migrieren großer Assets wird hier nicht behandelt.

Sie können die folgenden Upload-Funktionen nutzen:

* Um große/hierarchische Ordner stapelweise hochzuladen, verwenden Sie [!DNL Experience Manager] -Desktop-Programm, das [Ordner-Upload](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#upload-and-add-new-assets-to-aem) Funktionalität. Sie können auch hierarchische Ordnerstrukturen hochladen. [!DNL Assets]Das Hochladen von erfolgt im Hintergrund und ist daher nicht an eine Webbrowser-Sitzung gebunden.
* Um einige Dateien aus einem einzelnen Ordner hochzuladen, ziehen Sie die Dateien direkt auf die Web-Oberfläche oder verwenden Sie die Option Erstellen im [!DNL Assets] Web-Schnittstelle.
* Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Upload-Programme verwenden.

#### Verwalten digitaler Assets direkt auf dem Desktop {#managing-digital-assets-directly-from-desktop}

Wenn Sie digitale Assets mithilfe von Netzwerkdateifreigaben verwalten, verwenden Sie einfach die Netzwerkfreigabe, die von [!DNL Experience Manager] Das -Desktop-Programm könnte als bequemer Ersatz angesehen werden. Beim Übergang von Netzwerkdateifreigaben [!DNL Experience Manager] Die Web-Oberfläche bietet eine Vielzahl von Digital Asset Management-Funktionen, die weit über das hinausgehen, was in einer Netzwerkfreigabe möglich ist (Suche, Sammlungen, Metadaten, Zusammenarbeit, Vorschau usw.), und [!DNL Experience Manager] Das -Desktop-Programm bietet einen praktischen Link, um das serverseitige DAM-Repository mit der Arbeit auf dem Desktop zu verbinden.

Vermeiden Sie die Verwendung von [!DNL Experience Manager] -Desktop-Programm zum Verwalten von Assets direkt in der Netzwerkfreigabe von [!DNL Assets]. Vermeiden Sie beispielsweise die Verwendung von [!DNL Experience Manager] Desktop-Programm zum Verschieben/Kopieren mehrerer Dateien. Verwenden Sie stattdessen die [!DNL Assets] -Benutzeroberfläche zum Ziehen von Ordnern aus Finder/Explorer in die Netzwerkfreigabe oder zur Verwendung der [!DNL Assets] Funktion &quot;Ordner hochladen&quot;.

#### Asset-Migration {#asset-migration}

Informationen zum Planen und Ausführen von Asset-Migrationen von vorhandenen Systemen in ein neues System oder Migrieren großer Mengen von auf Servern gespeicherten Assets finden Sie im [Migrationshandbuch](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] Desktop-Programm und [!DNL Experience Manager] nach [!DNL Creative Cloud] -Integrationen unterstützen solche Migrationen nicht. Aufgrund der großen Menge an aufzunehmenden Assets und der zusätzlichen Anforderungen rund um Metadatenzuordnungen, Transformationen und Aufnahmen sollten Migrationen mithilfe anderer Tools und Ansätze erfolgen.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Best Practices für das Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [Experience Manager Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=de)
>* [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md)

