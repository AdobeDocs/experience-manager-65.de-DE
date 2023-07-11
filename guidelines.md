---
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 66%

---
# Richtlinien für Beiträge zur Adobe Experience Manager-Dokumentation

## Dokumentationsphilosophie

Adobe weiß, dass Adobe Experience Manager-Benutzer in extrem wettbewerbsorientierten Umgebungen arbeiten, um digitale Erlebnisse zu erstellen, die sie von ihren Wettbewerbern abheben. Daher ist es wichtig, dass bei der Bereitstellung erweiterter neuer Tools durch Adobe in AEM diese Tools durch genaue und klare Dokumentation ergänzt werden, damit der Kunde sofort seine AEM investieren und den ROI maximieren kann.

Das Ziel der AEM-Dokumentation besteht darin, AEM-Benutzer schnellstmöglich mit der Dokumentation vertraut zu machen. Daher priorisiert Adobe genaue und nutzbare Dokumentation und bemüht sich kontinuierlich um deren Aktualisierung und Verbesserung.

## Beiträge zur Dokumentation

Zur stetigen Verbesserung der AEM-Dokumentation ist die gesamte Community von AEM-Benutzern herzlich eingeladen, zur Dokumentation beizutragen. Sei es durch Pull-Anfragen oder Probleme, bei den Verbesserungen der Dokumentation kann es sich um Korrekturen, Klarstellungen, Erweiterungen und weitere Beispiele handeln.

## Dokumentationsstandards

Während Adobe Beiträge zu unserer Dokumentation begrüßt, sollte jeder Beitrag zur AEM Dokumentation in Form einer Pull-Anforderung oder eines Problems mit unseren Beitrags- und Dokumentationsstandards übereinstimmen.

Beiträge, die diesen Standards nicht entsprechen, können abgelehnt werden.

### Anwendungsfälle für Document Standard.

Die AEM-Dokumentation umfasst Standard-Anwendungsfälle. Anwendungsfälle, die über den Umfang der standardmäßigen Installation und Nutzung des Produkts hinausgehen, sind nicht Teil der AEM-Dokumentation.

### Die Dokumentation dokumentiert im Allgemeinen keine Fehler oder ihre Umgehungslösungen.

Die AEM-Dokumentation umfasst Standard-Anwendungsfälle. Aus diesem Grund werden Fehler, durch Fehler verursachte Effekte und Problemumgehungen für Fehler in der Regel nicht dokumentiert.

Ausnahmen gelten für die Versionshinweise, in denen bekannte Probleme mit möglichen Lösungen aufgelistet werden können, die vom AEM Product Management genehmigt wurden.

### Dokumentationsbeiträge sind nicht zur Beantwortung technischer Fragen geeignet.

Alle Ideen, die Sie möglicherweise zur Verbesserung der AEM-Dokumentation haben, sind als Beiträge willkommen. Kommentare, Probleme und Pull-Anfragen sind jedoch nur für *Beiträge* vorgesehen. Sie sind nicht zur Beantwortung Ihrer Fragen über die Verwendung von AEM, Implementierung Ihres AEM-Projekts oder zur Lösung technischer Probleme gedacht.

Fragen zur Verwendung von AEM oder zu technischen Fehlern, die möglicherweise bei Ihnen auftreten, sollten entsprechend dem herkömmlichen Support-Prozess über das [Support-Portal für Experience Manager](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#support) gemeldet oder in der [Experience Manager-Community](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?lang=de) diskutiert werden.

***AEM-Dokumentationsbeiträge sind kein Ersatz für den Adobe-Support*** und Beiträge, die Antworten auf Support-Fragen suchen, werden abgelehnt.

### Die Beiträge müssen sich eindeutig auf die betroffenen Dokumentationsseiten beziehen.

Wenn Sie ein Problem erstellen, um Verbesserungen an der Dokumentation vorzuschlagen, müssen Sie Links zu den betroffenen Seiten angeben. Wenn Sie ein Problem mit der **Diese Seite bearbeiten** auf einer Dokumentationsseite erstellen, wird das Problem automatisch mit einem Link zur Seite erstellt.

Dies gilt nicht für Pull-Anforderungen, da Pull-Anforderungen standardmäßig auf die betroffenen Seiten verweisen.

## Dokumentationsrichtlinien

Wir bitten darum, dass alle Beiträge zu unserer Dokumentation bestimmten Stilrichtlinien folgen.

Durch das Befolgen dieser Richtlinien erleichtern Sie die Überprüfung Ihres Beitrags und beschleunigen somit dessen Aufnahme in unsere Dokumentation.

### Sprache und Stil

#### Sprache

* Die AEM-Dokumentation wird in englischer Sprache verfasst und verwaltet.
* Ausdrücke sollten so einfach wie möglich sein.
* Drücken Sie sich klar und bündig aus.

Denken Sie daran, dass die Leser AEM Dokumentation weltweit sind und nicht erwartet werden können, dass sie fließend Englisch beherrschen oder Muttersprachler sind. Vermeiden Sie umgangssprachliche Wendungen und verwenden Sie eine klare und einfache Sprache wie möglich.

#### Befolgen Sie das Microsoft® Manual of Style

[Das Microsoft® Stilhandbuch](https://learn.microsoft.com/en-us/style-guide/welcome/) ist ein kostenloses Stilhandbuch für Dokumentationen, das sich auf die Softwaredokumentation konzentriert und AEM Dokumentation nach Möglichkeit diesem Handbuch folgt.

### Formatierung

| Element | Stil |
|---|---|
| Element oder Option der Benutzeroberfläche | **fett** |
| Dateiname, Pfad, Benutzereingabe, Parameterwerte | `monospaced` |
| Code, Befehlszeile | ```Code Block``` |

### Screenshots

Screenshots sollten mit Bedacht und nur dann verwendet werden, wenn eine Textbeschreibung nicht ausreicht.

Markierungen oder andere Anmerkungen in Screenshots (wie rote Rahmen, Pfeile oder Text) sollten nicht verwendet werden. Auf diese Weise können die Screenshots in lokalisierten Versionen der Dokumentation einfacher wiederverwendet oder repliziert werden.

### Versionsspezifische Verweise

Versuchen Sie nach Möglichkeit direkte Verweise auf eine bestimmte Version im gesamten Dokumentationsinhalt zu vermeiden. Dadurch wird die Dokumentation für künftige Versionen flexibler und erweiterbarer.

### Verwendung von Day, AEM, CQ, CRX

Das Produkt sollte in einem Artikel zum ersten Mal immer mit dem vollständigen Namen **Adobe Experience Manager** genannt und anschließend als **AEM** bezeichnet werden.

Day, Day-Software, CQ und CRX sollten nur verwendet werden, wenn dies unvermeidlich ist, z. B. in Klassennamen oder bei Verweisen auf die AEM-Historie.