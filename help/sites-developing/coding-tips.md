---
title: Tipps zum Programmieren
description: Hier finden Sie Tipps für Best Practices beim Programmieren in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 85ca35e5-6e2b-447a-9711-b12601beacdd
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 96%

---

# Tipps zum Programmieren{#coding-tips}

## So oft wie möglich Taglibs oder HTL verwenden {#use-taglibs-or-htl-as-much-as-possible}

Das Einschließen von Scriptlets in JSPs erschwert das Debugging von Fehlern im Code. Auch wird es dadurch schwierig, die Business-Logik von der Ansichtsebene zu trennen, was gegen das Single-Responsibility-Prinzip und das MVC-Design-Muster verstößt.

### Schreiben von lesbarem Code {#write-readable-code}

Code wird einmal geschrieben, aber viele Male gelesen. Es zahlt sich aus, von Anfang an darauf zu achten, übersichtlichen Code zu schreiben, da Sie und andere Entwicklerinnen und Entwickler ihn später lesen werden und nachvollziehen können müssen.

### Auswählen von Namen, die den Zweck beschreiben {#choose-intention-revealing-names}

Idealerweise sollten andere Programmierer kein Modul öffnen müssen, um zu verstehen, was es tut. Ebenso sollten sie sagen können, was eine Methode macht, ohne sie zu lesen. Je besser Sie diesen Ansatz verinnerlichen, desto einfacher lesbar wird der Code und desto schneller können Sie den Code schreiben und verändern.

Für AEM-Codes gelten die folgenden Konventionen:


* Eine einzige Implementierung einer Schnittstelle wird `<Interface>Impl` genannt, d. h. `ReaderImpl`.
* Mehrere Implementierungen einer Schnittstelle werden `<Variant><Interface>` genannt, d. h. `JcrReader` und `FileSystemReader`.
* Abstrakte Basisklassen werden `Abstract<Interface>` oder `Abstract<Variant><Interface>` genannt.
* Pakete werden `com.adobe.product.module` genannt. Jedes Maven-Artefakt oder OSGi-Bundle muss ein eigenes Paket aufweisen.
* Java™-Implementierungen werden in einem impl-Paket unter ihrer API platziert.


Diese Konventionen gelten nicht notwendigerweise für Kundenimplementierungen, aber es ist wichtig, Konventionen zu definieren und einzuhalten, damit der Code aufrechterhalten werden kann.

Idealerweise sollten Namen den Zweck beschreiben. Ein guter Hinweis darauf, dass Namen nicht so deutlich sind wie gewünscht, ist das Vorhandensein von Kommentaren, die erklären, wozu die Variable oder die Methode dient:

<table>
 <tbody>
  <tr>
   <td><p><strong>Unklar</strong></p> </td>
   <td><p><strong>Klar</strong></p> </td>
  </tr>
  <tr>
   <td><p>int d; //elapsed time in days</p> </td>
   <td><p>int elapsedTimeInDays;</p> </td>
  </tr>
  <tr>
   <td><p>//get tagged images<br /> public List getItems() {}</p> </td>
   <td><p>public List getTaggedImages() {}</p> </td>
  </tr>
 </tbody>
</table>

### Wiederholen Sie sich nicht  {#don-t-repeat-yourself}

Dieses Prinzip sieht vor, dass derselbe Codesatz niemals dupliziert werden sollte. Dies gilt auch für Elemente wie Zeichenfolgentexte. Code-Duplikate erhöhen die Fehleranfälligkeit, wenn etwas geändert werden muss, und sollten gesucht und entfernt werden.

### Blanke CSS-Regeln vermeiden {#avoid-naked-css-rules}

CSS-Regeln sollten speziell auf das Zielelement im Kontext Ihrer Anwendung ausgerichtet sein. Eine CSS-Regel, die auf *.content .center* angewendet wird, wäre beispielsweise zu breit angelegt und könnte sich auf viele Inhalte in Ihrem System auswirken, weshalb andere diesen Stil zukünftig überschreiben müssten. Dagegen wäre *.myapp-centertext* eine spezifischere Regel, da sie zentrierten *Text* im Kontext Ihrer Anwendung festlegt.

### Verwendung veralteter APIs vermeiden {#eliminate-usage-of-deprecated-apis}

Wenn eine API veraltet ist, ist es besser, den neuen empfohlenen Ansatz zu suchen anstatt die veraltete API zu verwenden. Diese Vorgehensweise vereinfacht zukünftige Upgrades.

### Lokalisierbaren Code schreiben {#write-localizable-code}

Alle Zeichenfolgen, die nicht autorenseitig bereitgestellt werden, sollten in einem Aufruf des i18n-Wörterbuchs von AEM über *I18n.get()* in JSP/Java und *CQ.I18n.get()* in JavaScript zusammengefasst werden. Diese Implementierung gibt die Zeichenfolge zurück, die an sie übergeben wurde, wenn keine Implementierung gefunden wird. Dies bietet die Flexibilität, die Lokalisierung zu implementieren, nachdem die Funktionen in der primären Sprache implementiert wurden.

### Ressourcenpfade zur Sicherheit maskieren {#escape-resource-paths-for-safety}

Zwar sollten Pfade im JCR keine Leerzeichen enthalten, aber der Code sollte nicht fehlschlagen, wenn Leerzeichen vorhanden sind. Jackrabbit stellt eine Text-Hilfsklasse mit den Methoden *escape()* und *escapePath()* bereit. Für JSPs stellt die Granite-Benutzeroberfläche die Funktion *granite:encodeURIPath() EL* bereit.

### Zur Absicherung vor Cross-Site-Scripting-Angriffen die XSS-API und/oder HTL nutzen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM stellt eine XSS-API bereit, mit der Sie Parameter einfach bereinigen und die Absicherung vor Cross-Site-Scripting-Angriffen gewährleisten können. Außerdem sind diese Schutzmechanismen bei HTL direkt in der Vorlagensprache integriert. Ein API-Cheat-Sheet können Sie unter [Entwicklung – Richtlinien und Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md) herunterladen.

### Angemessene Protokollierung implementieren {#implement-appropriate-logging}

Für Java™-Code unterstützt AEM slf4j als Standard-API für die Protokollierung von Meldungen. Für eine konsistente Administration sollte die API mit den Konfigurationen genutzt werden, die über die OSGi-Konsole verfügbar sind. Slf4j umfasst fünf verschiedene Protokollierungsebenen. Adobe empfiehlt, bei der Auswahl der Ebene, auf der eine Meldung protokolliert werden soll, die folgenden Richtlinien anzuwenden:

* ERROR: Wenn etwas im Code nicht funktioniert und die Verarbeitung nicht fortgesetzt werden kann. Dies geschieht häufig in Folge eines unerwarteten Ausnahmefehlers. Es ist hilfreich, bei solchen Szenarien Stapelüberwachungen einzuschließen.
* WARN: Wenn etwas nicht richtig funktioniert hat, aber die Verarbeitung fortgesetzt werden kann. Dies geschieht oft in Folge eines Ausnahmefehlers, mit dem gerechnet wurde, z. B. *PathNotFoundException*.
* INFO: Informationen, die bei der Überwachung eines Systems hilfreich sein dürften. Denken Sie daran, dass dies der Standard ist und die meisten Kunden ihn in ihren Umgebungen beibehalten. Verwenden Sie diese Ebene daher nicht zu häufig.
* DEBUG: Informationen der unteren Ebene zur Verarbeitung. Dies ist hilfreich, wenn ein Problem zusammen mit dem Support behoben wird.
* TRACE: Informationen der untersten Ebene, z. B. das Aufrufen/Beenden von Methoden. Dies wird normalerweise nur von Entwicklerinnen und Entwicklern verwendet.

Wenn JavaScript vorhanden ist, sollte *console.log* nur während der Entwicklung genutzt werden und alle Protokollanweisungen sollten vor der Veröffentlichung entfernt werden.

### Nicht durchdachte Programmierung vermeiden {#avoid-cargo-cult-programming}

Vermeiden Sie es, Code zu kopieren, ohne zu wissen, was er tut. Im Zweifelsfall ist es ratsam, jemanden zu fragen, der über größere Erfahrung mit dem Modul oder der API verfügt, bei dem/der Sie sich nicht sicher sind.
