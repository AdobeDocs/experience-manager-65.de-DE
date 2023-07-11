---
title: Datenmodellierung – Modell von David Nuescheler
description: Empfehlungen zur Inhaltsmodellierung von David Nuescheler
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 6ce6a204-db59-4ed2-8383-00c6afba82b4
source-git-commit: b9c164321baa3ed82ae87a97a325fcf0ad2f6ca0
workflow-type: tm+mt
source-wordcount: '1795'
ht-degree: 16%

---

# Datenmodellierung – Modell von David Nuescheler{#data-modeling-david-nuescheler-s-model}

## Quelle {#source}

Im Folgenden werden Ideen und Kommentare von David Nuescheler vorgestellt.

David war Mitgründer und CTO der Day Software AG, eines der führenden Anbieter von Software für globales Content Management und Content-Infrastruktur, die 2010 von Adobe übernommen wurde. Er ist jetzt Mitglied und VP von Enterprise Technology bei der Adobe und leitet auch die Entwicklung von JSR-170, der Java™ Content Repository (JCR) Application Programming Interface (API), dem Technologiestandard für Content Management.

Weitere Updates sind auch unter [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel) zu finden.

## Einführung von David {#introduction-from-david}

In verschiedenen Diskussionen stellte ich fest, dass Entwickler mit den Funktionen und Funktionen von JCR bei der Inhaltsmodellierung etwas unsicher sind. Es gibt noch keine Anleitung und wenig Erfahrung dazu, wie Inhalte in einem Repository modelliert werden und warum ein Inhaltsmodell besser ist als das andere.

In der relationalen Welt verfügt die Software-Industrie zwar über eine große Erfahrung in der Modellierung von Daten, aber wir befinden uns noch in den frühen Phasen des Inhalts-Repository-Raums.

Ich möchte damit beginnen, diese Lücke zu füllen, indem ich meine Meinungen darüber zum Thema der Gestaltung von Inhalten zum Ausdruck bringe, in der Hoffnung, dass dies eines Tages zu etwas Bedeutsamerem für die Entwickler-Community werden könnte, was nicht nur &quot;meine Meinung&quot; ist, sondern etwas, das allgemein anwendbar ist. Betrachten Sie das als einen schnellen ersten Versuch.

>[!NOTE]
>
>Haftungsausschluss: Diese Leitlinien drücken meine persönlichen und mitunter kontroversen Ansichten aus. Ich freue mich darauf, diese Leitlinien zu erörtern und zu verfeinern.

## Sieben einfache Regeln {#seven-simple-rules}

### 1. Regel: Erst die Daten, dann die Struktur. Zumindest gegebenenfalls. {#rule-data-first-structure-later-maybe}

#### Erklärung {#explanation-1}

Es wird empfohlen, sich keine Gedanken über eine deklarierte Datenstruktur im ERD-Sinne zu machen. Zunächst.

Lernen Sie, nt:unstructured (&amp; Freunde) in der Entwicklung zu lieben.

Ich glaube, Stefano fasst diesen ziemlich zusammen.

Meine unterste Zeile: Struktur ist teuer und oft ist es völlig unnötig, die Struktur explizit für den zugrunde liegenden Speicher zu deklarieren.

Es gibt einen impliziten Vertrag über die Struktur, die Ihre Anwendung von sich aus verwendet. Angenommen, ich speichere das Änderungsdatum eines Blog-Posts in einer lastModified -Eigenschaft. Meine App weiß automatisch, dass sie das Änderungsdatum von derselben Eigenschaft erneut lesen kann. Es ist wirklich nicht erforderlich, dies explizit zu deklarieren.

Weitere Dateneinschränkungen wie obligatorische oder Typ- und Wertbegrenzungen sollten nur angewendet werden, wenn dies aus Gründen der Datenintegrität erforderlich ist.

#### Beispiel {#example-1}

Dass im obigen Beispiel eine `lastModified`-Datumseigenschaft beispielsweise für den „blog post“-Knoten verwendet wird, bedeutet noch lange nicht, dass ein spezieller Knotentyp benötigt wird. Ich würde zumindest anfänglich auf jeden Fall `nt:unstructured` für meine „blog post“-Knoten verwenden. Da ich in meiner Blogging-Anwendung ohnehin nur das lastModified-Datum anzeigen möchte (und darauf möglicherweise die Funktion „Sortieren nach“ anwende), kümmert es mich nicht, ob dies überhaupt ein Datum ist. Da ich fest davon ausgehe, dass es in meiner Blogging-Anwendung sowieso ein Datum gibt, ist es nicht nötig, das Vorhandensein eines `lastModified`-Datums in Form eines Knotentyps zu deklarieren.

### 2. Regel: Steuern Sie die Content-Hierarchie, anstatt sie dem Zufall zu überlassen. {#rule-drive-the-content-hierarchy-don-t-let-it-happen}

#### Erklärung {#explanation-2}

Die Inhaltshierarchie ist ein wertvolles Asset. Also lassen Sie es nicht einfach passieren, entwerfen Sie es. Wenn Sie keinen „guten“, für Menschen lesbaren Namen für einen Knoten haben, sollten Sie vermutlich genau da ansetzen. Beliebige Zahlen sind kaum ein &quot;guter Name&quot;.

Es mag zwar einfach sein, ein vorhandenes relationales Modell schnell in ein hierarchisches Modell zu versetzen, doch sollte man in diesem Prozess einen Gedanken machen.

Wenn man sich in meiner Erfahrung mit Zugriffskontrolle und -einschließung befasst, sind normalerweise gute Treiber für die Inhaltshierarchie. Stellen Sie sich vor, es wäre Ihr Dateisystem. Vielleicht verwenden Sie sogar Dateien und Ordner, um es auf Ihrer lokalen Festplatte zu modellieren.

Ich persönlich ziehe in vielen Fällen zuerst Hierarchiekonventionen vor dem Knotentyping-System und führe die Typisierung später ein.

>[!CAUTION]
>
>Die Art und Weise, wie ein Content-Repository strukturiert ist, kann sich auch auf die Leistung auswirken. Für eine optimale Leistung sollte die Anzahl der untergeordneten Knoten, die an einzelne Knoten in einem Inhalts-Repository angehängt werden, 1&#39;000 nicht überschreiten.
>
>Weitere Informationen finden Sie unter [Wie viele Daten kann CRX verarbeiten?](https://helpx.adobe.com/de/experience-manager/kb/CrxLimitation.html).

#### Beispiel {#example-2}

Ich würde ein einfaches Blogging-System wie folgt modellieren. Beachten Sie, dass ich mir anfangs nicht einmal um die entsprechenden Knotentypen kümmere, die ich an dieser Stelle verwende.

```xml
/content/myblog
/content/myblog/posts
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping

/content/myblog/comments/iphone_shipping/i_like_it_too
/content/myblog/comments/iphone_shipping/i_like_it_too/i_hate_it
```

Ich denke, dass sich die Struktur des Inhalts anhand des Beispiels ohne weitere Erklärungen verstehen lässt.

Was am Anfang unerwartet sein kann, ist, warum ich die &quot;Kommentare&quot; nicht mit dem &quot;Post&quot; speichern würde, was auf die Zugriffskontrolle zurückzuführen ist, die ich gerne in einer einigermaßen hierarchischen Weise anwenden möchte.

Mithilfe des obigen Inhaltsmodells kann ich dem &quot;anonymen&quot;Benutzer einfach erlauben, Kommentare zu &quot;erstellen&quot;, aber den anonymen Benutzer für den Rest des Arbeitsbereichs schreibgeschützt halten.

### Regel 3: Workspaces sind für clone(), merge() und update() vorgesehen. {#rule-workspaces-are-for-clone-merge-and-update}

#### Erklärung {#explanation-3}

Wenn Sie in Ihrer Anwendung nicht die Methoden `clone()`, `merge()` oder `update()` verwenden, sollten Sie sich für einen einzigen Workspace entscheiden.

&quot;Entsprechende Knoten&quot;ist ein Konzept, das in der JCR-Spezifikation definiert ist. Grundsätzlich läuft er auf Knoten zurück, die denselben Inhalt in verschiedenen so genannten Arbeitsbereichen darstellen.

JCR führt das abstrakte Konzept von Workspaces ein, wodurch viele Entwickler unklar sind, was sie damit anfangen sollen. Ich möchte vorschlagen, Ihre Nutzung von Arbeitsbereichen zu testen.

Wenn Sie eine erhebliche Überschneidung von &quot;entsprechenden&quot;Knoten (im Wesentlichen die Knoten mit derselben UUID) in mehreren Arbeitsbereichen haben, sollten Sie Arbeitsbereiche wahrscheinlich gut nutzen.

Wenn es keine Überschneidung von Knoten mit derselben UUID gibt, missbrauchen Sie wahrscheinlich Arbeitsbereiche.

Verwenden Sie keine Arbeitsbereiche für die Zugriffskontrolle. Die Sichtbarkeit von Inhalten für eine bestimmte Benutzergruppe ist kein gutes Argument, um Dinge in verschiedene Arbeitsbereiche zu unterteilen. JCR bietet &quot;Zugriffskontrolle&quot;im Content-Repository, um dies bereitzustellen.

Arbeitsbereiche sind die Grenze für Verweise und Abfragen.

#### Beispiel {#example-3}

Verwenden Sie Arbeitsbereiche für Dinge wie:

* v1.2 Ihres Projekts im Vergleich zu v1.3 Ihres Projekts
* einen Status von &quot;Entwicklung&quot;, &quot;Qualitätssicherung&quot;und &quot;Veröffentlicht&quot;

Verwenden Sie keine Arbeitsbereiche für Dinge wie:

* Benutzerstartverzeichnisse
* unterschiedliche Inhalte für verschiedene Zielgruppen wie öffentlich, privat, lokal, ...
* Posteingänge für verschiedene Benutzer

### Regel 4: Vorsicht vor gleichnamigen Geschwistern. {#rule-beware-of-same-name-siblings}

#### Erklärung {#explanation-4}

Während gleichnamige Namensgleichungen (SNS) in die Spezifikation eingeführt wurden, um die Kompatibilität mit Datenstrukturen zu ermöglichen, die für XML entwickelt und ausgedrückt werden und daher für JCR nützlich sind, bringt SNS erhebliche Mehrkosten und Komplexität für das Repository mit sich.

Jeder Pfad in das Inhalts-Repository, der ein SNS in einem seiner Pfadsegmente enthält, wird viel weniger stabil. Wenn ein SNS entfernt oder neu angeordnet wird, wirkt sich dies auf die Pfade aller anderen SNS und ihrer untergeordneten Elemente aus.

Für den Import von XML oder die Interaktion mit vorhandenen XML SNS vielleicht notwendig und nützlich, aber ich habe noch nie SNS verwendet und werde es nie in meinen &quot;grünen Feld&quot;-Datenmodellen.

#### Beispiel {#example-4}

Verwenden Sie

```xml
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping
```

anstelle von

```xml
/content/blog[1]/post[1]
/content/blog[1]/post[2]
```

### Regel 5: Verweise werden als schädlich betrachtet. {#rule-references-considered-harmful}

#### Erklärung {#explanation-5}

Verweise implizieren referenzielle Integrität. Ich halte es für wichtig zu verstehen, dass Verweise nicht nur zusätzliche Kosten für das Repository verursachen, das die referenzielle Integrität verwaltet, sondern auch aus der Sicht der Inhaltsflexibilität kostspielig sind.

Ich persönlich stelle sicher, dass ich nur Verweise verwende, wenn ich wirklich nicht mit einer gefährlichen Referenz umgehen kann und andernfalls einen Pfad, einen Namen oder eine String-UUID verwendet, um auf einen anderen Knoten zu verweisen.

#### Beispiel {#example-5}

Nehmen wir an, ich lasse &quot;Verweise&quot;von einem Dokument (a) auf ein anderes Dokument (b) zu. Wenn ich diese Beziehung mithilfe von Referenzeigenschaften modelliere, bedeutet dies, dass die beiden Dokumente auf Repository-Ebene verknüpft sind. Ich kann Dokument (a) nicht einzeln exportieren/importieren, da das Ziel der Referenzeigenschaft möglicherweise nicht vorhanden ist. Andere Vorgänge wie Zusammenführen, Aktualisieren, Wiederherstellen oder Klonen sind ebenfalls betroffen.

Also würde ich diese Verweise entweder als &quot;schwache Verweise&quot;modellieren (in JCR v1.0 läuft dies im Wesentlichen auf Zeichenfolgeneigenschaften ab, die die UUID des Zielknotens enthalten) oder einfach einen Pfad verwenden. Manchmal ist der Pfad aussagekräftiger.

Ich glaube, es gibt Anwendungsfälle, in denen ein System wirklich nicht funktionieren kann, wenn eine Referenz in Gefahr ist, aber ich kann einfach kein gutes &quot;reales&quot;, aber einfaches Beispiel aus meiner direkten Erfahrung entwickeln.

### 6. Regel: Dateien sind Dateien. {#rule-files-are-files}

#### Erklärung {#explanation-6}

Wenn ein Inhaltsmodell etwas offenbart, das auch remote wie eine Datei oder einen Ordner riecht, versuche ich, zu verwenden (oder zu erweitern) `nt:file`, `nt:folder`und `nt:resource`.

Meiner Erfahrung nach ermöglichen viele generische Anwendungen die implizite Interaktion mit nt:folder und nt:files und wissen, wie diese Ereignisse verarbeitet und angezeigt werden, wenn sie mit zusätzlichen Metainformationen angereichert werden. Beispielsweise wird eine direkte Interaktion mit Dateiserverimplementierungen wie CIFS oder WebDAV, die auf JCR sitzen, implizit.

Als Faustregel kann man meines Erachtens Folgendes verwenden: Wenn Sie den Dateinamen und den MIME-Typ speichern müssen, dann `nt:file`/ `nt:resource` ist eine gute Übereinstimmung. Wenn Sie möglicherweise mehrere „files“ haben, bietet sich „nt:folder“ für ihre Speicherung an.

Wenn Sie Metainformationen für Ihre Ressource hinzufügen müssen, beispielsweise eine Eigenschaft &quot;author&quot;oder &quot;description&quot;, erweitern Sie `nt:resource` nicht `nt:file`. „nt:file“ erweitere ich eher selten, `nt:resource` dagegen häufig.

#### Beispiel {#example-6}

Nehmen wir an, jemand möchte ein Bild in einen Blogeintrag unter:

```xml
/content/myblog/posts/iphone_shipping
```

Und vielleicht wäre die anfängliche Darmreaktion, eine binäre Eigenschaft hinzuzufügen, die das Bild enthält.

Obwohl es sicherlich gute Anwendungsfälle gibt, nur eine binäre Eigenschaft zu verwenden (sagen wir, der Name ist irrelevant und der MIME-Typ ist implizit), in diesem Fall empfehle ich die folgende Struktur für mein Blog-Beispiel.

```xml
/content/myblog/posts/iphone_shipping/attachments [nt:folder]
/content/myblog/posts/iphone_shipping/attachments/front.jpg [nt:file]
/content/myblog/posts/iphone_shipping/attachments/front.jpg/jcr:content [nt:resource]
```

### Regel 7: IDs sind böse. {#rule-ids-are-evil}

#### Erklärung {#explanation-7}

In relationalen Datenbanken sind IDs ein notwendiges Mittel, um Beziehungen auszudrücken, sodass Menschen dazu neigen, sie auch in Inhaltsmodellen zu verwenden. Meistens aus falschen Gründen.

Wenn Ihr Inhaltsmodell voll mit Eigenschaften ist, die auf &quot;ID&quot;enden, verwenden Sie die Hierarchie wahrscheinlich nicht ordnungsgemäß.

Es stimmt, dass einige Knoten während ihres gesamten Lebenszyklus eine stabile Identifizierung benötigen. Viel weniger, als du vielleicht denkst. mix:referenceable bietet einen solchen Mechanismus, der in das Repository integriert ist, sodass es wirklich nicht notwendig ist, ein zusätzliches Mittel zu finden, um einen Knoten stabil zu identifizieren.

Beachten Sie auch, dass Elemente anhand von Pfaden identifiziert werden können. Und so sehr &quot;symlinks&quot; für die meisten Benutzer viel sinnvoller sind als harte Links in einem UNIX®-Dateisystem, ist ein Pfad für die meisten Anwendungen sinnvoll, auf einen Zielknoten zu verweisen.

Wichtiger noch: **mix**:referenceable bedeutet, dass sie zu einem Zeitpunkt auf einen Knoten angewendet werden kann, zu dem Sie ihn tatsächlich referenzieren müssen.

Angenommen, Sie möchten potenziell auf einen Knoten des Typs &quot;Dokument&quot;verweisen, bedeutet nicht, dass Ihr &quot;Dokument&quot;-Knotentyp statisch von mix:referenceable erweitert werden muss, da er dynamisch zu jeder Instanz des &quot;Dokuments&quot;hinzugefügt werden kann.

#### Beispiel {#example-7}

Verwenden Sie:

```xml
/content/myblog/posts/iphone_shipping/attachments/front.jpg
```

Statt:

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
