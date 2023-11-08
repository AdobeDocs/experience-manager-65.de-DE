---
title: Tipps zum Programmieren
description: Hier finden Sie Tipps zum Kodieren von Best Practices in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 85ca35e5-6e2b-447a-9711-b12601beacdd
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 55%

---

# Tipps zum Programmieren{#coding-tips}

## Verwenden Sie möglichst viele Taglibs oder HTL {#use-taglibs-or-htl-as-much-as-possible}

Das Einschließen von Scriptlets in JSPs erschwert das Debugging von Fehlern im Code. Außerdem ist es schwierig, durch die Einbeziehung von Skripten in JSPs die Geschäftslogik von der Ansichtsebene zu trennen, was einen Verstoß gegen den Grundsatz der Einzelverantwortung und das MVC-Designmuster darstellt.

### Schreiben von lesbarem Code {#write-readable-code}

Code wird einmal geschrieben, aber viele Male gelesen. Wenn Sie etwas Zeit vorwärts verbringen, um den geschriebenen Code zu bereinigen, zahlt sich dies aus, während Sie und andere Entwickler ihn später lesen.

### Auswählen von Namen, die den Zweck beschreiben {#choose-intention-revealing-names}

Idealerweise sollten andere Programmierer kein Modul öffnen müssen, um zu verstehen, was es tut. Ebenso sollten sie sagen können, was eine Methode macht, ohne sie zu lesen. Je besser Sie diese Ideen abonnieren können, desto einfacher ist es, den Code zu lesen und desto schneller können Sie den Code schreiben und ändern.

Für AEM-Codes gelten die folgenden Konventionen:


* Eine einzelne Implementierung einer Schnittstelle heißt `<Interface>Impl`, d. h. `ReaderImpl`.
* Mehrere Implementierungen einer Schnittstelle werden `<Variant><Interface>`, d. h. `JcrReader` und `FileSystemReader`.
* Abstrakte Basisklassen werden `Abstract<Interface>` oder `Abstract<Variant><Interface>` genannt.
* Pakete werden `com.adobe.product.module` genannt.  Jedes Maven-Artefakt oder OSGi-Bundle muss ein eigenes Paket aufweisen.
* Java™-Implementierungen werden in einem impl-Paket unter ihrer API platziert.


Diese Konventionen gelten nicht unbedingt für Kundenimplementierungen, aber es ist wichtig, Konventionen zu definieren und einzuhalten, damit der Code aufrechterhalten werden kann.

Idealerweise sollten Namen den Zweck beschreiben. Ein guter Hinweis darauf, dass Namen nicht so deutlich sind wie gewünscht, ist das Vorhandensein von Kommentaren, die erklären, wozu die Variable oder die Methode dient:

<table>
 <tbody>
  <tr>
   <td><p><strong>Unklar</strong></p> </td>
   <td><p><strong>Klar</strong></p> </td>
  </tr>
  <tr>
   <td><p>int d; //vergangene Zeit in Tagen</p> </td>
   <td><p>int elapsedTimeInDays;</p> </td>
  </tr>
  <tr>
   <td><p>//getaggte Bilder abrufen<br /> public List getItems() {}</p> </td>
   <td><p>public List getTaggedImages() {}</p> </td>
  </tr>
 </tbody>
</table>

### Wiederholen Sie sich nicht  {#don-t-repeat-yourself}

Dieses Prinzip sieht vor, dass derselbe Codesatz niemals dupliziert werden sollte. Dies gilt auch für Elemente wie Zeichenfolgentexte. Code-Duplikate erhöhen die Fehleranfälligkeit, wenn etwas geändert werden muss, und sollten gesucht und entfernt werden.

### Blanke CSS-Regeln vermeiden {#avoid-naked-css-rules}

CSS-Regeln sollten speziell auf das Zielelement im Kontext Ihrer Anwendung ausgerichtet sein. Eine CSS-Regel, die auf *.content .center* angewendet wird, wäre beispielsweise zu breit angelegt und könnte sich auf viele Inhalte in Ihrem System auswirken, weshalb andere diesen Stil zukünftig überschreiben müssten. in Erwägung nachstehender Gründe *.myapp-centertext* wäre eine spezifischere Regel, da sie die Zentrierung angibt. *text* im Kontext Ihrer Anwendung.

### Verwendung veralteter APIs vermeiden {#eliminate-usage-of-deprecated-apis}

Wenn eine API veraltet ist, ist es besser, den neuen empfohlenen Ansatz zu suchen anstatt die veraltete API zu verwenden. Diese Vorgehensweise vereinfacht zukünftige Upgrades.

### Lokalisierbaren Code schreiben {#write-localizable-code}

Alle Zeichenfolgen, die nicht von einem Autor bereitgestellt werden, sollten in einen Aufruf zum AEM i18n-Wörterbuch durch eingeschlossen werden. *I18n.get()* in JSP/Java und *CQ.I18n.get()* in JavaScript. Diese Implementierung gibt die Zeichenfolge zurück, die an sie übergeben wurde, wenn keine Implementierung gefunden wird. Dies bietet die Flexibilität, die Lokalisierung zu implementieren, nachdem die Funktionen in der primären Sprache implementiert wurden.

### Ressourcenpfade für Sicherheit maskieren {#escape-resource-paths-for-safety}

Während Pfade im JCR keine Leerzeichen enthalten sollten, sollte das Vorhandensein von Leerzeichen nicht dazu führen, dass der Code umbrochen wird. Jackrabbit stellt eine Text-Hilfsklasse mit den Methoden *escape()* und *escapePath()* bereit. Für JSPs stellt die Granite-Benutzeroberfläche die Funktion *granite:encodeURIPath() EL* bereit.

### Zur Absicherung vor Cross-Site-Scripting-Angriffen die XSS-API und/oder HTL nutzen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM stellt eine XSS-API bereit, mit der Sie Parameter einfach bereinigen und die Absicherung vor Cross-Site-Scripting-Angriffen gewährleisten können. Darüber hinaus sind diese Schutzmaßnahmen in HTL direkt in die Vorlagensprache integriert. Ein API-Cheat-Sheet können Sie unter [Entwicklung – Richtlinien und Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md) herunterladen.

### Angemessene Protokollierung implementieren {#implement-appropriate-logging}

Für Java™-Code unterstützt AEM slf4j als Standard-API für die Protokollierung von Nachrichten und sollte mit den Konfigurationen verwendet werden, die über die OSGi-Konsole zur Einheitlichkeit der Administration verfügbar gemacht werden. Slf4j umfasst fünf verschiedene Protokollierungsebenen. Adobe empfiehlt die Verwendung der folgenden Richtlinien bei der Auswahl der Ebene, auf der eine Nachricht protokolliert werden soll:

* ERROR: Wenn etwas im Code nicht funktioniert und die Verarbeitung nicht fortgesetzt werden kann. Dies geschieht häufig in Folge eines unerwarteten Ausnahmefehlers. Es ist hilfreich, Stacktraces in diese Szenarien aufzunehmen.
* WARN: Wenn etwas nicht richtig funktioniert hat, aber die Verarbeitung fortgesetzt werden kann. Dies geschieht oft in Folge eines Ausnahmefehlers, mit dem gerechnet wurde, z. B. *PathNotFoundException*.
* INFO: Informationen, die bei der Überwachung eines Systems hilfreich sein dürften. Denken Sie daran, dass dies der Standard ist und die meisten Kunden ihn in ihren Umgebungen beibehalten. Verwenden Sie sie daher nicht übermäßig.
* DEBUG: Informationen der unteren Ebene zur Verarbeitung. Nützlich beim Debugging eines Problems mit Unterstützung.
* TRACE: Die Informationen auf der niedrigsten Ebene, Dinge wie Einstieg/Ausstieg-Methoden. Dies wird normalerweise nur von Entwicklern verwendet.

Wenn JavaScript vorhanden ist, *console.log* sollten nur während der Entwicklung verwendet werden und alle Protokollanweisungen sollten vor der Veröffentlichung entfernt werden.

### Vermeiden von Frachtschnitt-Programmierung {#avoid-cargo-cult-programming}

Vermeiden Sie es, Code zu kopieren, ohne zu wissen, was er tut. Im Zweifelsfall ist es ratsam, jemanden zu fragen, der über größere Erfahrung mit dem Modul oder der API verfügt, bei dem/der Sie sich nicht sicher sind.
