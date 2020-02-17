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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Tipps zum Programmieren{#coding-tips}

## So oft wie möglich TagLibs oder HTL verwenden {#use-taglibs-or-htl-as-much-as-possible}

Das Einschließen von Scriptlets in JSPs erschwert das Debugging von Fehlern im Code. Außerdem ist es durch die Einbeziehung von Skripten in JSPs schwierig, Geschäftslogik von der Ansichtsebene zu trennen, was eine Verletzung des Prinzips &quot;Einfache Verantwortung&quot;und des MVC-Designmusters darstellt.

### Lesbaren Code schreiben {#write-readable-code}

Code wird einmal geschrieben, aber viele Male gelesen. Wenn wir etwas Zeit vorn für die Bereinigung des Codes aufwenden, den wir schreiben, werden Dividenden auf der Straße ausgezahlt, wie wir und andere Entwickler es später lesen müssen.

### Namen wählen, die den Zweck beschreiben {#choose-intention-revealing-names}

Idealerweise sollte ein anderer Programmierer kein Modul öffnen müssen, um zu verstehen, was es tut. Ebenso sollten sie in der Lage sein, zu erkennen, was eine Methode tut, ohne sie zu lesen. Je besser wir diese Ideen abonnieren können, desto leichter wird es sein, unseren Code zu lesen und desto schneller können wir unseren Code schreiben und ändern.

Für AEM-Codes gelten die folgenden Konventionen:


* A single implementation of an interface is named `<Interface>Impl`, i.e. `ReaderImpl`.
* Multiple implementations of an interface are named `<Variant><Interface>`, i.e. `JcrReader` and `FileSystemReader`.
* Abstrakte Basisklassen werden benannt `Abstract<Interface>` oder `Abstract<Variant><Interface>`.
* Packages are named `com.adobe.product.module`.  Jedes Maven Artefakt- oder OSGi-Bundle muss ein eigenes Paket haben.
* Java-Implementierungen werden in einem impl-Paket unter ihrer API platziert.


Beachten Sie, dass diese Konventionen nicht notwendigerweise für Kundenimplementierungen gelten müssen. Es ist jedoch wichtig, dass Konventionen definiert und eingehalten werden, sodass der Code verwaltbar bleibt.

Idealerweise sollten Namen den Zweck beschreiben. Ein üblicher Code-Test für den Fall, dass Namen nicht so eindeutig sind, wie sie sein sollten, besteht darin, dass Kommentare vorhanden sind, die erklären, wofür die Variable oder Methode verwendet wird:

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

### Wiederholungen vermeiden  {#don-t-repeat-yourself}

Dieses Prinzip sieht vor, dass derselbe Codesatz niemals dupliziert werden sollte. Dies gilt auch für Dinge wie Zeichenfolgenliterale. Codeduplizierung öffnet die Tür für Defekte, wenn etwas geändert werden muss und sollte gesucht und beseitigt werden.

### Blanke CSS-Regeln vermeiden {#avoid-naked-css-rules}

CSS-Regeln sollten speziell auf das Zielelement im Kontext Ihrer Anwendung ausgerichtet sein. For example, a CSS rule applied to *.content .center* would be overly broad and could potentially end up impacting lots of content across your system, requiring others to override this style in the future. *.myapp-centerText* wäre eine spezifischere Regel, da es zentrierten *Text* im Kontext Ihrer Anwendung angibt.

### Verwendung veralteter APIs vermeiden {#eliminate-usage-of-deprecated-apis}

Wenn eine API veraltet ist, ist es besser, den neuen empfohlenen Ansatz zu suchen anstatt die veraltete API zu verwenden. Dadurch werden in Zukunft reibungslosere Upgrades sichergestellt.

### Lokalisierbaren Code schreiben {#write-localizable-code}

Alle Strings, die nicht von einem Autor bereitgestellt werden, sollten in einem Aufruf des i18n-Wörterbuchs von AEM über *I18n.get()* in JSP/Java und *CQ.I18n.get()* in JavaScript zusammengefasst werden. Bei dieser Implementierung wird die Zeichenfolge zurückgegeben, die an sie übergeben wurde, wenn keine Implementierung gefunden wurde. Auf diese Weise erhalten Sie die Flexibilität bei der Implementierung der Lokalisierung nach der Implementierung der Funktionen in der Hauptsprache.

### Ressourcenpfade zur Sicherheit maskieren {#escape-resource-paths-for-safety}

Zwar sollten Pfade im JCR keine Leerzeichen enthalten, aber der Code sollte nicht fehlschlagen, wenn Leerzeichen vorhanden sind. Jackrabbit stellt eine Text-Hilfsklasse mit den Methoden *escape()* und *escapePath()* bereit. For JSPs, Granite UI exposes a *granite:encodeURIPath() EL* function.

### Zur Absicherung vor Cross-Site-Scripting-Angriffen die XSS-API und/oder HTL nutzen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM stellt eine XSS-API bereit, mit der Sie Parameter einfach bereinigen und die Absicherung vor Cross-Site-Scripting-Angriffen gewährleisten können. Zusätzlich hat HTL diese Schutzmechanismen direkt in die Vorlagensprache integriert. An API cheat sheet is available for download at [Development - Guidelines and Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md).

### Angemessene Protokollierung implementieren {#implement-appropriate-logging}

Für Java-Code unterstützt AEM slf4j als Standard-API für die Protokollierung von Meldungen. Für eine konsistente Administration sollte die API in Verbindung mit den Konfigurationen genutzt werden, die über die OSGi-Konsole verfügbar sind. Slf4j umfasst fünf verschiedene Protokollierungsebenen. Wir empfehlen, bei der Auswahl der Ebene, auf der eine Meldung protokolliert werden soll, die folgenden Richtlinien anzuwenden:

* ERROR: Wenn etwas im Code nicht funktioniert und die Verarbeitung nicht fortgesetzt werden kann. Dies geschieht oft aufgrund einer unerwarteten Ausnahme. In der Regel ist es hilfreich, Stapelspuren in diese Szenarien einzubeziehen.
* WARN: Wenn etwas nicht richtig funktioniert hat, aber die Verarbeitung fortgesetzt werden kann. This will often be the result of an exception that we expected, such as a *PathNotFoundException*.
* INFO: Informationen, die bei der Überwachung eines Systems hilfreich sein dürften. Denken Sie daran, dass dies der Standard ist und dass die meisten Kunden dies in ihren Umgebungen beibehalten. Verwenden Sie diese Ebene daher nicht zu häufig.
* DEBUG: Informationen der unteren Ebene zur Verarbeitung. Hilfreich, wenn ein Problem zusammen mit dem Support behoben wird.
* TRACE: Die niedrigste Ebene von Informationen, z. B. das Aufrufen/Beenden von Methoden. Dies wird in der Regel nur von Entwicklern verwendet.

Bei JavaScript sollte *console.log* nur während der Entwicklung genutzt werden und alle Protokollaussagen sollten vor der Veröffentlichung entfernt werden.

### Nicht durchdachte Programmierung vermeiden {#avoid-cargo-cult-programming}

Vermeiden Sie es, Code zu kopieren, ohne zu wissen, was er tut. Im Zweifelsfall ist es immer am besten, jemanden zu fragen, der über mehr Erfahrung mit dem Modul oder der API verfügt, auf dem Sie nicht klar sind.
