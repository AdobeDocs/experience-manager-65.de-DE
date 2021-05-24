---
title: Tipps zum Programmieren
seo-title: Tipps zum Programmieren
description: Tipps zum Programmieren für AEM
seo-description: Tipps zum Programmieren für AEM
uuid: 1bb1cc6a-3606-4ef4-a8dd-7c08a7cf5189
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 4adce3b4-f209-4a01-b116-a5e01c4cc123
exl-id: 85ca35e5-6e2b-447a-9711-b12601beacdd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 53%

---

# Tipps zum Programmieren{#coding-tips}

## So oft wie möglich TagLibs oder HTL verwenden {#use-taglibs-or-htl-as-much-as-possible}

Das Einschließen von Scriptlets in JSPs erschwert das Debugging von Fehlern im Code. Darüber hinaus ist es schwierig, durch die Einbeziehung von Skripten in JSPs die Geschäftslogik von der Ansichtsebene zu trennen, was einen Verstoß gegen das Prinzip der Einzelverantwortung und das MVC-Designmuster darstellt.

### Lesbaren Code schreiben {#write-readable-code}

Code wird einmal geschrieben, aber viele Male gelesen. Wenn wir etwas Zeit im Voraus für die Bereinigung des Codes aufwenden, den wir schreiben, werden wir Dividenden auf der Straße auszahlen, da wir und andere Entwickler es später lesen müssen.

### Namen wählen, die den Zweck beschreiben {#choose-intention-revealing-names}

Idealerweise sollte ein anderer Programmierer kein Modul öffnen müssen, um zu verstehen, was es tut. Genauso sollten sie in der Lage sein, zu sagen, was eine Methode tut, ohne sie zu lesen. Je besser wir diese Ideen abonnieren können, desto einfacher wird es sein, unseren Code zu lesen und desto schneller werden wir in der Lage sein, unseren Code zu schreiben und zu ändern.

Für AEM-Codes gelten die folgenden Konventionen:


* Eine einzelne Implementierung einer Schnittstelle heißt `<Interface>Impl`, d. h. `ReaderImpl`.
* Mehrere Implementierungen einer Schnittstelle werden `<Variant><Interface>` genannt, d. h. `JcrReader` und `FileSystemReader`.
* Abstrakte Basisklassen werden `Abstract<Interface>` oder `Abstract<Variant><Interface>` genannt.
* Pakete werden `com.adobe.product.module` genannt.  Jedes Maven-Artefakt oder OSGi-Bundle muss über ein eigenes Paket verfügen.
* Java-Implementierungen werden in einem impl-Paket unter ihrer API platziert.


Beachten Sie, dass diese Konventionen nicht notwendigerweise für Kundenimplementierungen gelten müssen. Es ist jedoch wichtig, dass Konventionen definiert und eingehalten werden, sodass der Code verwaltbar bleibt.

Idealerweise sollten Namen den Zweck beschreiben. Ein gängiger Codetest für den Fall, dass Namen nicht so klar sind, wie sie sein sollten, besteht darin, dass Kommentare vorhanden sind, die erklären, wofür die Variable oder Methode verwendet wird:

<table>
 <tbody>
  <tr>
   <td><p><strong>Unklar</strong></p> </td>
   <td><p><strong>Clear</strong></p> </td>
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

### Wiederholungen vermeiden   {#don-t-repeat-yourself}

Dieses Prinzip sieht vor, dass derselbe Codesatz niemals dupliziert werden sollte. Dies gilt auch für Dinge wie Zeichenfolgenliterale. Code-Duplizierung öffnet die Tür für Fehler, wann immer sich etwas ändern muss und gesucht und beseitigt werden sollte.

### Blanke CSS-Regeln vermeiden {#avoid-naked-css-rules}

CSS-Regeln sollten speziell auf das Zielelement im Kontext Ihrer Anwendung ausgerichtet sein. Eine CSS-Regel, die auf *.content.center* angewendet wird, wäre beispielsweise zu breit angelegt und könnte sich letztendlich auf viele Inhalte in Ihrem System auswirken, sodass andere diesen Stil in Zukunft überschreiben müssen. *.myapp-* centertext wäre eine spezifischere Regel, da sie zentrierte  ** Texte im Kontext Ihrer Anwendung angibt.

### Verwendung veralteter APIs vermeiden {#eliminate-usage-of-deprecated-apis}

Wenn eine API veraltet ist, ist es besser, den neuen empfohlenen Ansatz zu suchen anstatt die veraltete API zu verwenden. Dadurch werden in Zukunft reibungslosere Upgrades gewährleistet.

### Lokalisierbaren Code schreiben {#write-localizable-code}

Alle Strings, die nicht von einem Autor bereitgestellt werden, sollten in einem Aufruf des i18n-Wörterbuchs von AEM über *I18n.get()* in JSP/Java und *CQ.I18n.get()* in JavaScript zusammengefasst werden. Diese Implementierung gibt die Zeichenfolge zurück, die an sie übergeben wurde, wenn keine Implementierung gefunden wird. Dies bietet daher die Flexibilität, die Lokalisierung nach der Implementierung der Funktionen in der Primärsprache zu implementieren.

### Ressourcenpfade zur Sicherheit maskieren {#escape-resource-paths-for-safety}

Zwar sollten Pfade im JCR keine Leerzeichen enthalten, aber der Code sollte nicht fehlschlagen, wenn Leerzeichen vorhanden sind. Jackrabbit stellt eine Text-Hilfsklasse mit den Methoden *escape()* und *escapePath()* bereit. Für JSPs stellt die Granite-Benutzeroberfläche eine *granite:encodeURIPath() EL*-Funktion bereit.

### Zur Absicherung vor Cross-Site-Scripting-Angriffen die XSS-API und/oder HTL nutzen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM stellt eine XSS-API bereit, mit der Sie Parameter einfach bereinigen und die Absicherung vor Cross-Site-Scripting-Angriffen gewährleisten können. Darüber hinaus sind diese Schutzmaßnahmen in HTL direkt in die Vorlagensprache integriert. Ein API-Cheatsheet kann unter [Entwicklung - Richtlinien und Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md) heruntergeladen werden.

### Angemessene Protokollierung implementieren {#implement-appropriate-logging}

Für Java-Code unterstützt AEM slf4j als Standard-API für die Protokollierung von Meldungen. Für eine konsistente Administration sollte die API in Verbindung mit den Konfigurationen genutzt werden, die über die OSGi-Konsole verfügbar sind. Slf4j umfasst fünf verschiedene Protokollierungsebenen. Wir empfehlen, bei der Auswahl der Ebene, auf der eine Meldung protokolliert werden soll, die folgenden Richtlinien anzuwenden:

* ERROR: Wenn etwas im Code nicht funktioniert und die Verarbeitung nicht fortgesetzt werden kann. Dies geschieht oft aufgrund einer unerwarteten Ausnahme. In der Regel ist es hilfreich, Stacktraces in diese Szenarien aufzunehmen.
* WARN: Wenn etwas nicht richtig funktioniert hat, aber die Verarbeitung fortgesetzt werden kann. Dies ist häufig das Ergebnis einer von uns erwarteten Ausnahme, z. B. einer *PathNotFoundException*.
* INFO: Informationen, die bei der Überwachung eines Systems hilfreich sein dürften. Beachten Sie, dass dies die Standardeinstellung ist und die meisten Kunden dies in ihren Umgebungen beibehalten. Verwenden Sie diese Ebene daher nicht zu häufig.
* DEBUG: Informationen der unteren Ebene zur Verarbeitung. Hilfreich, wenn ein Problem zusammen mit dem Support behoben wird.
* TRACE: Die niedrigste Ebene von Informationen, z. B. das Aufrufen/Beenden von Methoden. Dies wird in der Regel nur von Entwicklern verwendet.

Bei JavaScript sollte *console.log* nur während der Entwicklung genutzt werden und alle Protokollaussagen sollten vor der Veröffentlichung entfernt werden.

### Nicht durchdachte Programmierung vermeiden  {#avoid-cargo-cult-programming}

Vermeiden Sie es, Code zu kopieren, ohne zu wissen, was er tut. Im Zweifelsfall ist es immer am besten, jemanden zu fragen, der über mehr Erfahrung mit dem -Modul oder der -API verfügt, über die Sie nicht genau Bescheid wissen.
