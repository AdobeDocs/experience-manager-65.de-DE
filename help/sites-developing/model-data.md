---
title: Datenmodellierung – Modell von David Nuescheler
seo-title: Datenmodellierung – Modell von David Nuescheler
description: Empfehlungen von David Nuescheler zur Content-Modellierung
seo-description: Empfehlungen von David Nuescheler zur Content-Modellierung
uuid: acb27e81-9143-4e0d-a37a-ba26491a841f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 39546c0a-b72f-42df-859b-98428ee0d5fb
exl-id: 6ce6a204-db59-4ed2-8383-00c6afba82b4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 89%

---

# Datenmodellierung – Modell von David Nuescheler{#data-modeling-david-nuescheler-s-model}

## Quelle {#source}

Bei den folgenden Informationen handelt es sich um Anregungen und Kommentare von David Nuescheler.

David Nuescheler war Mitbegründer und CTO von Day Software AG, einem führenden Anbieter von Content-Management- und Content-Infrastruktur-Software, der im Jahr 2010 von Adobe übernommen wurde. Nuescheler ist nun Fellow und VP des Bereichs Enterprise Technology bei Adobe und leitet die Entwicklung von JSR-170, der Java Content Repository-API (JCR), die den Technologiestandard für Content-Management bildet.

Weitere Aktualisierungen finden Sie auch unter [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

## Einführung von David Nuescheler {#introduction-from-david}

Bei Gesprächen mit Entwicklern habe ich festgestellt, dass diese Bedenken haben, was die Features und Funktionen von JCR im Hinblick auf die Content-Modellierung angeht. Es gibt noch keine Anleitungen und kaum Erfahrungen bezüglich der Fragen, wie Content in Repositorys modelliert werden sollte und warum ein Content-Modell besser ist als das andere.

Während die Softwarebranche in Bezug auf relationale Daten über umfangreiche Erfahrungen mit der Modellierung von Daten verfügt, stehen wir für den Content-Repository-Bereich noch am Anfang.

Ich möchte diese Erfahrungslücken schließen, indem ich meine eigenen Ideen zur Content-Modellierung vorstelle, in der Hoffnung, dass diese der Entwickler-Community als Basis für einen sinnvolleren Ansatz dienen können, der eher allgemein anwendbar ist. Betrachten Sie dies also als einen ersten Versuch, der sich schnell weiterentwickeln wird.

>[!NOTE]
>
>Haftungsausschluss: Diese Leitlinien drücken meine persönlichen und mitunter kontroversen Ansichten aus. Ich freue mich darauf, diese Empfehlungen zu diskutieren und zu verbessern.

## Sieben einfache Regeln {#seven-simple-rules}

### Regel 1: Daten zuerst, Struktur später. Zumindest gegebenenfalls. {#rule-data-first-structure-later-maybe}

#### Erklärung {#explanation-1}

Ich empfehle Ihnen, sich erst einmal keine Gedanken über eine deklarierte Datenstruktur im Rahmen eines ERD zu machen.

Setzen Sie bei der Entwicklung auf „nt:unstructured“ (und Konsorten).

Stefano hat das meiner Meinung nach gut zusammengefasst.

Ich bin zu dem Schluss gekommen, dass Strukturen zu aufwendig sind und es in vielen Fällen gar nicht nötig ist, eine Struktur explizit für den zugrunde liegenden Speicher zu deklarieren.

Es gibt sozusagen eine stillschweigende Vereinbarung über die Struktur, an die sich Ihre Anwendung grundsätzlich hält. Nehmen wir an, ich speichere das Änderungsdatum eines Blogposts in einer lastModified-Eigenschaft. Meine Applikation weiß automatisch, dass das Änderungsdatum wieder von derselben Eigenschaft abzurufen ist. Es ist also nicht nötig, dies explizit zu deklarieren.

Weitere Datenbeschränkungen wie erforderliche oder Typ- und Wertebeschränkungen sollten nur dann angewendet werden, wenn es aus Gründen der Datenintegrität erforderlich ist.

#### Beispiel {#example-1}

Dass im obigen Beispiel eine `lastModified`-Datumseigenschaft beispielsweise für den „blog post“-Knoten verwendet wird, bedeutet noch lange nicht, dass ein spezieller Knotentyp benötigt wird. Ich würde zumindest anfänglich auf jeden Fall `nt:unstructured` für meine „blog post“-Knoten verwenden. Da ich in meiner Blogging-Anwendung ohnehin nur das lastModified-Datum anzeigen möchte (und darauf möglicherweise die Funktion „Sortieren nach“ anwende), kümmert es mich nicht, ob dies überhaupt ein Datum ist. Da ich fest davon ausgehe, dass es in meiner Blogging-Anwendung sowieso ein Datum gibt, ist es nicht nötig, das Vorhandensein eines `lastModified`-Datums in Form eines Knotentyps zu deklarieren.

### 2. Regel: Steuern Sie die Content-Hierarchie, anstatt sie dem Zufall zu überlassen. {#rule-drive-the-content-hierarchy-don-t-let-it-happen}

#### Erklärung {#explanation-2}

Die Content-Hierarchie ist äußerst nützlich. Anstatt sie sich selbst zu überlassen, sollten Sie sie also gezielt gestalten. Wenn Sie keinen &quot;guten&quot;, für Menschen lesbaren Namen für einen Knoten haben, sollten Sie das wahrscheinlich überdenken. Zufällig ausgewählte Zahlen stellen wohl eher keinen „guten Namen“ dar.

Es mag zwar einfach sein, ein vorhandenes relationales Modell schnell in ein hierarchisches Modell zu überführen, aber Sie sollten sich bei diesem Verfahren mit einigen Aspekten intensiver auseinandersetzen.

Meiner Erfahrung nach sollten der Content-Hierarchie Zugriffskontrolle und Kapselung zugrunde liegen. Stellen Sie sich das so wie Ihr Dateisystem vor. Verwenden Sie ggf. sogar Dateien und Ordner, um es auf Ihrer lokalen Festplatte zu modellieren.

Ich persönlich ziehe es vor, in vielen Fällen zunächst Hierarchiekonventionen anstelle des Knotentypsystems anzuwenden, und führe die Typisierung erst später ein.

>[!CAUTION]
>
>Die Struktur des Content-Repositorys kann sich ebenfalls auf die Leistung auswirken. Die beste Leistung wird erzielt, wenn ein Content-Repository nicht mehr als 1.000 untergeordnete Knoten aufweist.
>
>Siehe [Wie viele Daten kann CRX verarbeiten?](https://helpx.adobe.com/experience-manager/kb/CrxLimitation.html) für weitere Informationen.

#### Beispiel {#example-2}

Ich würde ein einfaches Blogging-System wie folgt modellieren. Dabei mache ich mir zunächst keine Gedanken um die jeweiligen an dieser Stelle verwendeten Knotentypen.

```xml
/content/myblog
/content/myblog/posts
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping

/content/myblog/comments/iphone_shipping/i_like_it_too
/content/myblog/comments/iphone_shipping/i_like_it_too/i_hate_it
```

Ich denke, dass eines der Dinge, die sichtbar werden, ist, dass wir alle die Struktur des Inhalts verstehen, basierend auf dem Beispiel ohne weitere Erklärungen.

Überraschend ist möglicherweise zunächst, dass ich die „comments“ nicht mit dem „post“ speichere, was auf die Zugriffskontrolle zurückzuführen ist, die ich auf angemessen hierarchische Weise anwenden möchte.

Mit dem obigen Content-Modell kann ich es einem anonymen Benutzer ohne Weiteres gestatten, Kommentare zu erstellen, ohne dabei den Schreibschutz für den Rest des Workspace für diesen Benutzer aufzuheben.

### 3. Regel: Workspaces sind für „clone()“, „merge()“ und „update()“ vorgesehen.  {#rule-workspaces-are-for-clone-merge-and-update}

#### Erklärung {#explanation-3}

Wenn Sie die Methoden `clone()`, `merge()` oder `update()` in Ihrer Anwendung nicht verwenden, ist wahrscheinlich ein einziger Arbeitsbereich der richtige Weg.

„Korrespondierende Knoten“ sind ein in den JCR-Spezifikationen definiertes Konzept. Im Wesentlichen handelt es sich dabei um Knoten, die denselben Inhalt in verschiedenen sogenannten Workspaces repräsentieren.

JCR führt das sehr abstrakte Konzept der Workspaces ein, das viele Entwickler im Unklaren darüber lässt, was sie damit machen sollen. Ich würde Ihnen empfehlen, Ihren Einsatz von Workspaces der folgenden Überprüfung zu unterziehen.

Wenn es weitgehend zu Überschneidungen von „korrespondierenden“ Knoten (im Wesentlichen die Knoten mit derselben UUID) in mehreren Workspaces kommt, spricht das für einen sinnvollen Einsatz von Workspaces.

Wenn es keine Überschneidung von Knoten mit derselben UUID gibt, nutzen Sie Workspaces wahrscheinlich nicht richtig.

Workspaces sollten nicht für die Zugriffssteuerung verwendet werden. Dass Inhalte nur für eine bestimmte Gruppe von Benutzern sichtbar sein sollen, ist kein plausibler Grund für eine Aufteilung in verschiedene Workspaces. Für diesen Zweck bietet JCR die Zugriffssteuerung im Content-Repository.

Workspaces sind als Abgrenzung für Verweise und Abfragen vorgesehen.

#### Beispiel {#example-3}

Workspaces eignen sich für die folgenden Zwecke:

* zur Abgrenzung von v1.2 Ihres Projekts von v1.3 Ihres Projekts
* zur Abgrenzung von Inhalten mit dem Status „development„, „QA“ und „published“

Für Folgendes sollten Workspaces nicht verwendet werden:

* für Basisverzeichnisse von Benutzern
* zur Unterscheidung von Inhalten für verschiedene Zielgruppen (öffentliche, private, lokale usw.)
* für Postfächer für verschiedene Benutzer

### 4. Regel: Bei gleichgeordneten Elementen mit identischen Namen ist Vorsicht geboten.  {#rule-beware-of-same-name-siblings}

#### Erklärung {#explanation-4}

Gleichgeordnete Elemente mit identischen Namen wurden zwar in die Spezifikation aufgenommen, um die Kompatibilität mit Datenstrukturen zu ermöglichen, die für XML entwickelt und ausgedrückt werden und daher für JCR sehr nützlich sind, aber ihre Verwendung ist auch mit einem erheblichem Aufwand und einer hohen Komplexität für das Repository verbunden.

Jeder Pfad zum Content-Repository, der ein SNS in einem seiner Pfadsegmente enthält, wird deutlich instabiler, wenn ein SNS entfernt oder neu angeordnet wird. Dies hat Auswirkungen auf die Pfade aller anderen SNS und ihrer untergeordneten Elemente.

Für den Import von XML oder die Interaktion mit bestehendem XML sind SNS möglicherweise notwendig und nützlich, aber ich habe noch nie SNS verwendet und werde sie auch nicht in meinen Green Field-Datenmodellen verwenden.

#### Beispiel {#example-4}

Verwenden Sie

```xml
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping
```

anstelle von:

```xml
/content/blog[1]/post[1]
/content/blog[1]/post[2]
```

### 5. Regel: Verweise richten mehr Schaden an, als sie nutzen.  {#rule-references-considered-harmful}

#### Erklärung {#explanation-5}

Verweise implizieren referenzielle Integrität. Meiner Ansicht nach ist es wichtig zu verstehen, dass Verweise nicht nur zusätzlichen Aufwand für das Repository beim Verwalten der referenziellen Integrität verursachen, sondern auch zu Lasten der inhaltlichen Flexibilität gehen.

Ich persönlich verwende nur dann Verweise, wenn sich keine andere Möglichkeit findet, mit einem nicht zugeordneten Verweis umzugehen. Andernfalls verwende ich einen Pfad, einen Namen oder eine Zeichenfolgen-UUID, um auf einen anderen Knoten zu verweisen.

#### Beispiel {#example-5}

Angenommen, ich lasse Verweise von einem Dokument (a) zu einem anderen Dokument (b) zu. Wenn ich diese Beziehung mithilfe von Verweiseigenschaften modelliere, bedeutet dies, dass die beiden Dokumente auf einer Repository-Ebene verknüpft sind. Ich kann das Dokument (a) nicht einzeln exportieren/importieren, da das Ziel der Verweiseigenschaft möglicherweise nicht existiert. Dies betrifft auch andere Vorgänge wie das Zusammenführen, Aktualisieren, Wiederherstellen oder Klonen.

Also würde ich diese Verweise entweder über schwache Referenzen modellieren (in JCR v1.0 läuft das im Wesentlichen auf Zeichenfolgeneigenschaften hinaus, die die UUID des Zielknotens enthalten) oder einfach einen Pfad verwenden. Mitunter ist ein Pfad zunächst sinnvoller.

Möglicherweise gibt es Nutzungsszenarien, in denen ein System wirklich nicht funktionieren kann, solange ein Verweis nicht zugeordnet wird, aber ein praktisches Beispiel fällt mir dazu nicht ein.

### Regel 6: Dateien sind Dateien. {#rule-files-are-files}

#### Erklärung {#explanation-6}

Wenn ein Inhaltsmodell etwas offenbart, das *sogar remote* wie eine Datei oder einen Ordner riecht, versuche ich `nt:file`, `nt:folder` und `nt:resource` zu verwenden (oder zu erweitern).

Meiner Erfahrung nach lassen viele generische Anwendungen implizit die Interaktion mit „nt:folder“ und „nt:files“ zu und wissen, wie sie diese Ereignisse verarbeiten und anzeigen müssen, wenn sie zusätzliche Meta-Informationen aufweisen. Beispielsweise wird eine direkte Interaktion mit Dateiserverimplementierungen wie CIFS oder WebDAV, die auf JCR aufsetzen, implizit.

Als Faustregel kann man meines Erachtens Folgendes verwenden: Wenn Sie den Dateinamen und den MIME-Typ speichern müssen, ist `nt:file`/ `nt:resource` eine sehr gute Übereinstimmung. Wenn Sie möglicherweise mehrere „files“ haben, bietet sich „nt:folder“ für ihre Speicherung an.

Wenn Sie Meta-Informationen für Ihre Ressource hinzufügen müssen, beispielsweise die Eigenschaft „author“ oder „description“, erweitern Sie `nt:resource` und nicht `nt:file`. Ich erweitere selten nt:file und erweitere häufig `nt:resource`.

#### Beispiel {#example-6}

Nehmen wir an, jemand möchte an der folgenden Stelle ein Bild in einen Blogeintrag hochladen:

```xml
/content/myblog/posts/iphone_shipping
```

Unser erster Impuls wäre vermutlich, eine Binärdaten-Eigenschaft hinzufügen zu wollen, die das Bild enthält.

Es mag zwar Nutzungsszenarien geben, in denen es sich empfiehlt, nur eine Binärdaten-Eigenschaft zu verwenden (etwa wenn der Name irrelevant und der Mime-Typ implizit ist), in diesem Fall würde ich jedoch die folgende Struktur für mein Blogbeispiel verwenden:

```xml
/content/myblog/posts/iphone_shipping/attachments [nt:folder]
/content/myblog/posts/iphone_shipping/attachments/front.jpg [nt:file]
/content/myblog/posts/iphone_shipping/attachments/front.jpg/jcr:content [nt:resource]
```

### 7. Regel: IDs sind schlecht.  {#rule-ids-are-evil}

#### Erklärung {#explanation-7}

In relationalen Datenbanken sind IDs ein notwendiges Mittel, um Beziehungen auszudrücken, sodass man dazu neigen könnte, sie auch in Content-Modellen zu verwenden. Allerdings meist aus den falschen Gründen.

Wenn Ihr Content-Modell lauter Eigenschaften umfasst, die mit „Id“ enden, nutzen Sie die Hierarchie wahrscheinlich nicht richtig.

Es ist zwar richtig, dass einige Knoten während ihres gesamten Lebenszyklus eine zuverlässige Identifizierung erfordern. Doch das betrifft weitaus weniger Knoten, als Sie vielleicht annehmen. „mix:referenceable“ stellt einen entsprechenden ins Repository integrierten Mechanismus bereit, sodass es nicht nötig ist, nach einer zusätzlichen Möglichkeit zur zuverlässigen Identifizierung eines Knotens zu suchen.

Beachten Sie außerdem, dass Elemente durch einen Pfad identifiziert werden können. Und auch wenn in einem Unix-Dateisystem Symlinks für die meisten Benutzer sinnvoller als Hardlinks sind, bietet sich für die meisten Anwendungen ein Pfad zum Verweisen auf einen Zielknoten an.

Wichtiger noch: Es ist **mix**:referenceable, was bedeutet, dass es zu einem Zeitpunkt auf einen Knoten angewendet werden kann, zu dem Sie tatsächlich darauf verweisen müssen.

Wenn Sie also beispielsweise auf einen Knoten vom Typ „Document“ verweisen können möchten, bedeutet das nicht, dass Ihr Knotentyp „Document“ statisch von „mix:referenceable“ erweitert werden muss, da er dynamisch zu jeder Instanz von „Document“ hinzugefügt werden kann.

#### Beispiel {#example-7}

Verwenden Sie:

```xml
/content/myblog/posts/iphone_shipping/attachments/front.jpg
```

anstelle von:

```xml
[Blog]
-- blogId
-- author
[Post]
-- postId
-- blogId
-- title
-- text
-- date
[Attachment]
-- attachmentId
-- postId
-- filename
+ resource (nt:resource)
```
