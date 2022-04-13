---
title: Beheben von Problemen mit MSM und häufig gestellte Fragen
description: Hier erfahren Sie, wie Sie die häufigsten Probleme mit MSM beheben, und erhalten Antworten auf häufig gestellte Fragen zu MSM.
feature: Multi Site Manager
role: Admin
source-git-commit: d4fa331ad048e1d8bd57e0944c8bc5b67be1d203
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 100%

---

# Beheben von Problemen mit MSM und häufig gestellte Fragen {#troubleshooting-msm}

## Fehlerbehebung: erste Schritte {#first-steps}

Wenn Sie ein Ihrer Ansicht nach falsches Verhalten oder einen Fehler in MSM feststellen, sollten Sie vor der detaillierten Fehlerbehebung Folgendes sicherstellen:

* Lesen Sie die [häufig gestellten Fragen zu MSM](#faq) durch, da Ihre Probleme oder Fragen dort möglicherweise bereits angesprochen werden.
* Lesen Sie den Artikel [Best Practices für MSM](msm-best-practices.md), da er eine Reihe von Tipps enthält und Missverständnisse ausräumt.

## Erweiterte Informationen zum Status Ihres Blueprints und Ihrer Live Copy {#advanced-info}

MSM enthält mehrere Servlets, die mit Selektoren in den Ressourcen-URLs angefordert werden. Diese werden auf der Benutzeroberfläche verwendet, können aber auch direkt angefordert werden, um zusätzliche erweiterte und berechnete MSM-Statusinformationen für Ihre Seiten direkt anzuzeigen:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Verwenden Sie diesen Code auf einer Blueprint-Seite, um die Liste aller mit ihr verknüpften Live Copies mit zusätzlichen Live Copy-Statusinformationen abzurufen.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Verwenden Sie diesen Code auf Live Copy-Seiten, um erweiterte Informationen über die Verbindung mit den Blueprint-Seiten abzurufen. Wenn es sich bei der Seite nicht um eine Live Copy handelt, erhalten Sie kein Ergebnis.

Diese Servlets generieren DEBUG-Protokollmeldungen über den `com.day.cq.wcm.msm`-Logger, die ebenfalls hilfreich sein können.

## Abrufen MSM-spezifischer Informationen im Repository {#checking-repo}

Die Servlets haben berechnete Informationen auf Grundlage MSM-spezifischer Knoten und Mixins zurückgegeben. Diese Informationen werden folgendermaßen im Repository gespeichert.

* `cq:LiveSync`-Mixin-Typ
   * Dieser wird auf `jcr:content`-Knoten festgelegt und definiert Live Copy-Stammseiten.
   * Diese Seiten haben einen untergeordneten `cq:LiveSyncConfig`-Knoten des Typs `cq:LiveCopy`, der grundlegende und obligatorische Informationen über die Live Copy in den folgenden Eigenschaften enthält:
      * `cq:master` verweist auf die Blueprint-Seite der Live Copy.
      * `cq:rolloutConfigs` zeigt aktive Rollout-Konfigurationen an, die auf die Live Copy angewendet werden.
      * `cq:isDeep` ist „true“, wenn die untergeordneten Seiten dieses Live Copy-Stamms in der Live Copy enthalten sind.
* `cq:LiveRelationship`-Mixin-Typ
   * Jede Live Copy-Seite verfügt über einen solchen Mixin-Typ auf ihrem `jcr:content`-Knoten.
   * Ist dies nicht der Fall, wurde die Seite zu einem bestimmten Zeitpunkt getrennt oder außerhalb einer Live Copy-Aktion manuell über die Authoring-Oberfläche (Erstellen oder Rollout) erstellt.
* `cq:LiveSyncCancelled`-Mixin-Typ
   * Wurde zu `jcr:content`-Knoten der Live Copy-Seiten hinzugefügt, die ausgesetzt wurden.
   * Wenn die Aussetzung auch für untergeordnete Seiten gilt, wird eine `cq:isCancelledForChildren`-Eigenschaft auf demselben Knoten auf „true“ festgelegt.

Die in diesen Eigenschaften enthaltenen Informationen sollten auf der Benutzeroberfläche angezeigt werden. Bei der Fehlerbehebung ist es jedoch hilfreich, das MSM-Verhalten direkt im Repository zu beobachten, wenn MSM-Aktionen auftreten.

Die Kenntnis dieser Eigenschaften ist auch nützlich, um Abfragen an Ihr Repository zu senden und Sets von Seiten zu finden, die einen bestimmten Status aufweisen. Beispiel:

* `select * from cq:LiveSync` gibt als Ergebnis alle Live Copy-Stammseiten zurück.

## Häufig gestellte Fragen (FAQ) {#faq}

Im Folgenden finden Sie einige häufig gestellte Fragen zu MSM und Live Copy.

### Warum werden einige Eigenschaften (z. B. Titel, Anmerkungen) während eines MSM-Rollouts nicht aktualisiert? {#missing-properties}

MSM-Synchronisierungsaktionen sind hochgradig konfigurierbar. Welche Eigenschaften oder Komponenten während der Rollouts geändert werden, hängt unmittelbar von den Eigenschaften dieser Konfigurationen ab.

Weitere Informationen zu diesem Thema finden Sie in [diesem Artikel](msm-best-practices.md).

### Wie kann ich Rollout-Berechtigungen für eine Gruppe von Autoren entfernen? {#remove-rollout-permissions}

Es gibt keine **Rollout**-Berechtigung, die für AEM-Prinzipale (Benutzer oder Gruppen) festgelegt oder entfernt werden kann.

Stattdessen können Sie Folgendes tun:

* Passen Sie die Benutzeroberfläche des Produkts an, um die Rollout-Aktionen für einen bestimmten Prinzipal auszublenden.
* Entfernen Sie Schreibberechtigungen aus der Live Copy-Struktur für Autoren, die keine Rollout durchführen dürfen.

### Warum sehe ich Live Copy-Seiten mit dem Suffix „_msm_move“? {#moved-pages}

Bei einem Rollout einer Blueprint-Seite wird entweder die entsprechende Live Copy-Seite aktualisiert oder eine neue Live Copy-Seite erstellt, falls diese noch nicht vorhanden ist (z. B. wenn sie zum ersten Mal ausgerollt wird oder die Live Copy-Seite manuell gelöscht wurde).

Wenn in letzterem Fall jedoch eine Seite ohne `cq:LiveRelationship`-Eigenschaft mit demselben Namen vorhanden ist, wird diese Seite entsprechend umbenannt, bevor die Live Copy-Seite erstellt wird.

Standardmäßig wird bei einem Rollout entweder eine verknüpfte Live Copy-Seite erwartet, auf die die Updates der Blueprints ausgerollt werden, oder überhaupt keine Seite.

Wenn eine eigenständige Seite gefunden wird, benennt MSM diese Seite um und erstellt eine separate, verknüpfte Live Copy-Seite.

Eine solche eigenständige Seite in einer Live Copy-Unterstruktur ist normalerweise das Ergebnis einer **Trennung** oder die vorherige Live Copy-Seite wurde von einem Autor manuell gelöscht und dann mit demselben Namen neu erstellt.

Um dies zu vermeiden, verwenden Sie die Funktion **Aussetzen** für die Live Copy anstelle von **Trennen**. Weitere Informationen zur Aktion **Trennen** finden Sie in [diesem Artikel.](msm-livecopy.md)
