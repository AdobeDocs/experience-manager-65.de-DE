---
title: Aufrufen von AEM Forms mithilfe von REST-Anforderungen
description: Rufen Sie Prozesse auf, die in Workbench mithilfe von REST-Anforderungen erstellt wurden.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
role: Developer
exl-id: 991fbc56-f144-4ae6-b010-8d02f780d347
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '2503'
ht-degree: 83%

---

# Aufrufen von AEM Forms mithilfe von REST-Anforderungen {#invoking-aem-forms-using-rest-requests}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

In Workbench erstellte Prozesse können so konfiguriert werden, dass sie über Representational State Transfer-Anforderungen (REST) aufgerufen werden können. REST-Anfragen werden von HTML-Seiten gesendet. Das heißt, Sie können mithilfe einer REST-Anforderung einen Forms-Prozess direkt von einer Web-Seite aufrufen. Sie können beispielsweise eine neue Instanz einer Web-Seite öffnen. Anschließend können Sie einen Forms-Prozess aufrufen und ein gerendertes PDF-Dokument mit Daten laden, die in einer HTTP-POST-Anfrage gesendet wurden.

Es gibt zwei Arten von HTML-Clients. Der erste HTML-Client ist ein AJAX Client, der in JavaScript geschrieben ist. Der zweite Client ist ein HTML-Formular mit einer Senden-Schaltfläche. Ein HTML-basiertes Client-Programm ist nicht der einzige mögliche REST-Client. Jedes Client-Programm, das HTTP-Anforderungen unterstützt, kann einen Service mithilfe eines REST-Aufrufs aufrufen. Beispielsweise können Sie einen Service aufrufen, indem Sie einen REST-Aufruf aus einem PDF-Formular verwenden. (Siehe [Aufrufen des Prozesses MyApplication/EncryptDocument aus Acrobat](#rest-invocation-examples).)

Bei der Verwendung von REST-Anfragen wird empfohlen, Forms-Services nicht direkt aufzurufen. Rufen Sie stattdessen Prozesse auf, die in Workbench erstellt wurden. Verwenden Sie beim Erstellen eines Prozesses, der für den REST-Aufruf vorgesehen ist, einen programmgesteuerten Startpunkt. In diesem Fall wird der REST-Endpunkt automatisch hinzugefügt. Informationen zum Erstellen von Prozessen in Workbench finden Sie unter [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).

Wenn Sie einen Dienst mithilfe von REST aufrufen, werden Sie nach einem Benutzernamen und einem Kennwort für AEM Formulare aufgefordert. Wenn Sie jedoch keinen Benutzernamen und kein Kennwort angeben möchten, können Sie für den Service die Sicherheit deaktivieren.

Um einen Forms-Service (ein Prozess wird zu einem Service, wenn der Prozess aktiviert wird) mithilfe von REST aufzurufen, konfigurieren Sie einen REST-Endpunkt. (Siehe „Verwalten von Endpunkten“ in der [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63_de).)

Nachdem ein REST-Endpunkt konfiguriert wurde, können Sie einen Forms-Service mithilfe einer HTTP-GET-Methode oder einer POST-Methode aufrufen.

```java
 action="https://hiro-xp:8080/rest/services/[ServiceName]/[OperationName]:[ServiceVersion]" method="post" enctype="multipart/form-data"
```

Der obligatorische Wert für `ServiceName` ist der Name des aufzurufenden Forms-Services. Das optionale `OperationName` value ist der Name des Dienstvorgangs. Wenn dieser Wert nicht angegeben ist, wird für diesen Namen standardmäßig `invoke` verwendet, der Name des Vorgangs, der den Prozess startet. Der optionale Wert von `ServiceVersion` ist die Version im Format „X.Y“. Wenn dieser Wert nicht angegeben ist, wird die neueste Version verwendet. Die Wert von `enctype` kann auch `application/x-www-form-urlencoded` sein.

## Unterstützte Datentypen {#supported-data-types}

Beim Aufrufen von AEM Forms-Services mithilfe von REST-Anfragen werden die folgenden Datentypen unterstützt:

* Primitive Java-Datentypen, z. B. Zeichenfolgen und Ganzzahlen
* Datentyp `com.adobe.idp.Document`
* XML-Datentypen wie `org.w3c.Document` und `org.w3c.Element`
* Sammlungsobjekte wie `java.util.List` und `java.util.Map`

  Diese Datentypen werden gemeinhin als Eingabewerte für in Workbench erstellte Prozesse akzeptiert.

  Wenn ein Forms-Service mithilfe der HTTP-POST-Methode aufgerufen wird, werden die Argumente innerhalb des Inhalts der HTTP-Anfrage übergeben. Wenn die Signatur des AEM Forms-Dienstes über einen Zeichenfolgeneingabeparameter verfügt, kann der Anfragetext den Textwert des Eingabeparameters enthalten. Wenn die Signatur des Dienstes mehrere Zeichenfolgenparameter definiert, kann die Anfrage dem HTTP-Code folgen `application/x-www-form-urlencoded` -Notation mit den Namen des Parameters, die als Feldnamen des Formulars verwendet werden.

  Wenn ein Forms-Service einen Zeichenfolgenparameter zurückgibt, ist das Ergebnis eine textuelle Darstellung des Ausgabeparameters. Wenn ein Service mehrere Zeichenfolgenparameter zurückgibt, ist das Ergebnis ein XML-Dokument, das die Ausgabeparameter im folgenden Format codiert:
  ` <result> <output-paramater1>output-parameter-value-as-string</output-paramater1> . . . <output-paramaterN>output-parameter-value-as-string</output-paramaterN> </result>`

  >[!NOTE]
  >
  >Der Wert `output-paramater1` steht für den Namen des Ausgabeparameters.

  Wenn ein Forms-Service einen Parameter `com.adobe.idp.Document` benötigt, kann der Service nur mithilfe der HTTP-POST-Methode aufgerufen werden. Wenn der Service einen Parameter `com.adobe.idp.Document` erfordert, wird der Textkörper der HTTP-Anfrage zum Inhalt des Eingabedokumenobjekts.

  Wenn für einen AEM Forms-Service mehrere Eingabeparameter erforderlich sind, muss der Textkörper der HTTP-Anfrage eine mehrteilige MIME-Nachricht gemäß RFC 1867 sein. (RFC 1867 ist ein Standard, der von Webbrowsern zum Hochladen von Dateien auf Websites verwendet wird.) Jeder Eingabeparameter muss als separater Teil der mehrteiligen Nachricht gesendet werden und im Format `multipart/form-data` codiert sein. Der Name jedes Teils muss mit dem Namen des Parameters übereinstimmen.

  Listen und Zuordnungen werden auch als Eingabewerte für AEM Forms-Prozesse verwendet, die in Workbench erstellt wurden. Daher können Sie diese Datentypen bei Verwendung einer REST-Anfrage verwenden. Java-Arrays werden nicht unterstützt, da sie nicht als Eingabewert für einen AEM Forms-Prozess dienen.

  Wenn eine Liste als Eingabeparameter dient, kann ein REST-Client diese senden, indem er den Parameter mehrmals (für jedes Element der Liste einmal) angibt. Wenn beispielsweise A eine Liste von Dokumenten ist, muss die Eingabe eine mehrteilige Nachricht sein, die aus mehreren Teilen namens A besteht. In diesem Fall wird jeder Teil mit dem Namen A zu einem Element der Eingabeliste. Wenn B eine Liste von Zeichenfolgen ist, kann die Eingabe eine `application/x-www-form-urlencoded`-Nachricht sein, die aus mehreren Feldern namens B besteht. In diesem Fall wird jedes Formularfeld mit dem Namen B zu einem Element der Eingabeliste.

  Wenn eine Zuordnung als Eingabeparameter dient und es sich dabei um den einzigen Eingabeparameter der Services handelt, wird jeder Teil/jedes Feld der Eingabemeldung zu einem Schlüssel/Wert-Datensatz der Zuordnung. Der Name jedes Teils/Felds wird zum Schlüssel des Datensatzes. Der Inhalt jedes Teils/Felds wird zum Wert des Datensatzes.

  Wenn eine Eingabezuordnung nicht der einzige Eingabeparameter für Dienste ist, kann jeder Schlüssel/Wert-Datensatz, der zur Zuordnung gehört, mit einem Parameter gesendet werden, der als Verkettung des Parameternamens und des Datensatzschlüssels bezeichnet wird. Beispielsweise kann eine Eingabezuordnung namens `attributes` mit einer Liste der folgenden Schlüssel/Werte-Paare gesendet werden:

  `attributesColor=red`

  `attributesShape=box`

  `attributesWidth=5`

  Dies ergibt eine Zuordnung von drei Datensätzen: `Color=red`, `Shape=box` und `Width=5`.

  Die Ausgabeparameter der Listen- und Zuordnungstypen werden Teil der resultierenden XML-Nachricht. Die Ausgabeliste wird in XML als eine Serie von XML-Elementen dargestellt, wobei für jedes Element der Liste genau ein XML-Element vorhanden ist. Jedes Element erhält den gleichen Namen wie der Ausgabelistenparameter. Der Wert jedes XML-Elements repräsentiert eine von zwei verschiedenen Möglichkeiten:

* eine Textdarstellung des Elements der Liste (wenn die Liste aus Zeichenfolgentypen besteht)
* eine URL, die auf den Inhalt des Dokuments verweist (wenn die Liste aus `com.adobe.idp.Document`-Objekten besteht)

  Im folgenden Beispiel wird eine XML-Nachricht von einem Service zurückgegeben, der einen einzigen Ausgabeparameter namens *Liste*, hier eine Liste von Ganzzahlen, aufweist.
  ` <result>   <list>12345</list>   . . .   <list>67890</list>  </result>`Ein ausgegebener Zuordnungsparameter wird in der resultierenden XML-Nachricht als Serie von XML-Elementen mit genau einem Element für jeden Datensatz in der Zuordnung dargestellt. Jedes Element erhält denselben Namen wie der Schlüssel des Zuordnungsdatensatzes. Der Wert jedes Elements ist entweder eine Textdarstellung des Datensatzwerts der Zuordnung (wenn die Zuordnung aus Datensätzen mit einem Zeichenfolgenwert besteht) oder eine URL, die auf den Inhalt des Dokuments verweist (wenn die Zuordnung aus Datensätzen mit der `com.adobe.idp.Document` -Wert). Nachfolgend finden Sie ein Beispiel für eine XML-Nachricht, die von einem Service zurückgegeben wird, der einen einzigen Ausgabeparameter namens `map` aufweist. Dieser Parameterwert ist eine Zuordnung, die aus Datensätzen besteht, die Briefe mit `com.adobe.idp.Document`-Objekten verknüpfen.
  ` <result>   http://localhost:8080/DocumentManager/docm123/4567   . . .   <Z>http://localhost:8080/DocumentManager/docm987/6543</Z>  </result>  `

## Asynchrone Aufrufe {#asynchronous-invocations}

Einige AEM Forms-Services, z. B. am Menschen orientierte langlebige Prozesse, benötigen viel Zeit, bis sie abgeschlossen sind. Diese Services können asynchron, auf nicht blockierende Weise aufgerufen werden. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Ein AEM Forms-Service kann auf asynchrone Weise aufgerufen werden, indem in der Aufruf-URL `services` durch `async_invoke` ersetzt wird, wie im folgenden Beispiel gezeigt.

```java
 http://localhost:8080/rest/async_invoke/SomeService. SomeOperation?integer_input_variable=123&string_input_variable=abc
```

Diese URL gibt den Bezeichnerwert (im Format „text/plain“) des für diesen Aufruf verantwortlichen Auftrags zurück.

Mithilfe einer Aufruf-URL, bei der `services` durch `async_status` ersetzt ist, kann der Status des asynchronen Aufrufs abgerufen werden. Die URL muss einen `job_id`-Parameter enthalten, der den Kennungswert des mit diesem Aufruf verknüpften Auftrags angibt. Beispiel:

```java
 http://localhost:8080/rest/async_status/SomeService.SomeOperation?job_id=2345353443366564
```

Diese URL gibt einen ganzzahligen Wert (im Format &quot;text/plain&quot;) zurück, der den Auftragsstatus gemäß der Spezifikation von Job Manager kodiert (z. B. 2 bedeutet &quot;Ausführen&quot;, 3 bedeutet &quot;Abgeschlossen&quot;, 4 bedeutet &quot;Fehlgeschlagen&quot; usw.).

Wenn der Auftrag abgeschlossen ist, gibt die URL das gleiche Ergebnis zurück, wie wenn der Service synchron aufgerufen worden wäre.

Sobald der Auftrag abgeschlossen ist und das Ergebnis abgerufen wurde, kann der Auftrag mithilfe einer Aufruf-URL, bei der `services` durch `async_dispose` ersetzt wurde, verworfen werden. Die URL sollte auch einen `job_id`-Parameter enthalten, der den Kennungswert des Auftrags angibt. Beispiel:

```java
 http://localhost:8080/rest/async_dispose/SomeService.SomeOperation?job_id=2345353443366564
```

Wenn das Verwerfen des Auftrags gelungen ist, gibt diese URL eine leere Nachricht zurück.

## Fehlerberichterstattung {#error-reporting}

Wenn eine synchrone oder asynchrone Aufrufanforderung aufgrund einer auf dem Server ausgelösten Ausnahme nicht abgeschlossen werden kann, wird die Ausnahme als Teil der HTTP-Antwortnachricht gemeldet. Wenn die Aufruf-URL (oder die `async_result` URL, wenn ein asynchroner Aufruf vorhanden ist) kein .xml-Suffix aufweist, gibt der REST-Provider den HTTP-Code zurück `500 Internal Server Error` gefolgt von einer Ausnahmemeldung.

Wenn die Aufruf-URL (oder die `async_result` URL, wenn ein asynchroner Aufruf vorhanden ist) das Suffix .xml aufweist, gibt der REST-Provider den HTTP-Code zurück `200 OK`gefolgt von einem XML-Dokument, das die Ausnahme im folgenden Format beschreibt.

```xml
 <exception>
       <exception_class_name>[
       <DSCError>
          <componentUID>component_UUD</componentUID>
         <errorCode>error_code</errorCode>
         <minorCode>minor_code</minorCode>
         <message>error_message</message>
       </DSCError>
 ]
       <message>exception_message</message>
     <stackTrace>exception_stack_trace</stackTrace>
       </exception_class_name>
     <exception>
       </exception>
 </exception>
```

Die `DSCError`-Element ist optional und nur vorhanden, wenn die Ausnahme eine Instanz von `com.adobe.idp.dsc.DSCException` ist.

## Sicherheit und Authentifizierung {#security-and-authentication}

Um REST-Aufrufe mit einem sicheren Transport bereitzustellen, kann ein AEM Forms-Administrator das HTTPS-Protokoll auf dem J2EE-Anwendungsserver aktivieren, der als Host für AEM Forms dient. Diese Konfiguration ist spezifisch für den J2EE-Anwendungsserver. Sie ist nicht Teil der Forms Server-Konfiguration.

>[!NOTE]
>
>Als Workbench-Entwickler, der Prozesse über einen REST-Endpunkt verfügbar machen möchte, sollten Sie die XSS-Schwachstelle im Auge behalten. XSS-Schwachstellen können ausgenutzt werden, um Cookies zu stehlen oder zu manipulieren, die Darstellung von Inhalten zu verändern und vertrauliche Informationen zu kompromittieren. Es wird empfohlen, die Prozesslogik um zusätzliche Validierungsregeln für Eingabe- und Ausgabedaten zu erweitern, wenn die XSS-Schwachstelle ein Problem darstellt.

## AEM Forms-Services, die REST-Aufrufe unterstützen {#aem-forms-services-that-support-rest-invocation}

Es wird zwar empfohlen, Prozesse, die mit Workbench erstellt wurden, und nicht direkt Services aufzurufen, dennoch gibt es einige AEM Forms-Services, die REST-Aufrufe unterstützen. Es wird empfohlen, einen Prozess im Gegensatz zu einem Service direkt aufzurufen, da es effizienter ist, einen Prozess aufzurufen. Betrachten Sie das folgende Szenario. Angenommen, Sie möchten aus einem REST-Client eine Richtlinie erstellen. Das heißt, Sie möchten, dass der REST-Client Werte wie den Richtliniennamen und die Offline-Nutzungsdauer definiert.

Um eine Richtlinie zu erstellen, müssen Sie komplexe Datentypen definieren, z. B. ein `PolicyEntry`-Objekt. Ein `PolicyEntry`-Objekt definiert Attribute wie Berechtigungen, die mit der Richtlinie verknüpft sind. (Siehe [Erstellen von Richtlinien](/help/forms/developing/protecting-documents-policies.md#creating-policies).)

Anstatt eine REST-Anfrage zu senden, um eine Richtlinie zu erstellen (was das Definieren komplexer Datentypen wie eines `PolicyEntry`-Objekts beinhalten würde), erstellen Sie einen Prozess, der eine Richtlinie mithilfe von Workbench erstellt. Definieren Sie den Prozess so, dass er primitive Eingabevariablen akzeptiert, z. B. einen Zeichenfolgenwert, der den Prozessnamen definiert, oder eine Ganzzahl, die die Offline-Nutzungsdauer definiert.

Auf diese Weise müssen Sie keine REST-Aufrufanforderung erstellen, die komplexe Datentypen enthält, die für den Vorgang erforderlich sind. Der Prozess definiert die komplexen Datentypen und alles, was Sie vom REST-Client aus tun müssen, ist, den Prozess aufzurufen und primitive Datentypen zu übergeben. Informationen zum Aufrufen eines Prozesses mithilfe von REST finden Sie unter [Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST](#rest-invocation-examples).

In der folgenden Liste sind die AEM Forms-Services aufgeführt, die einen direkten REST-Aufruf unterstützen.

* Distiller-Dienst
* Rights Management-Dienst
* GeneratePDF-Service
* Generate3dPDF-Service
* FormDataIntegration

## Beispiele für REST-Aufrufe {#rest-invocation-examples}

Die folgenden Beispiele für REST-Aufrufe werden bereitgestellt:

* Übergeben von booleschen Werten an einen AEM Forms-Prozess
* Übergeben von Datumswerten an einen AEM Forms-Prozess
* Übergeben von Dokumenten an einen AEM Forms-Prozess
* Übergeben von Dokument- und Textwerten an einen AEM Forms-Prozess
* Übergeben von Auflistungswerten an einen AEM Forms-Prozess
* Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST
* Aufrufen des Prozesses MyApplication/EncryptDocument aus Acrobat

  Jedes Beispiel zeigt die Übergabe verschiedener Datentypen an einen AEM Forms-Prozess

**Übergeben von booleschen Werten an einen Prozess**

Im folgenden HTML-Beispiel werden zwei `Boolean`-Werte an einen AEM Forms-Prozess namens `RestTest2` übergeben. Der Name der Aufrufmethode lautet `invoke`, und die Version ist 1.0. Beachten Sie, dass die HTML-Post-Methode verwendet wird.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/RestTest2/invoke/1.0" method="post">
 
 Boolean 1: <input type="text" name="inBooleanList" value="true">
 Boolean 2: <input type="text" name="inBooleanList" value="false">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Übergeben von Datumswerten an einen Prozess**

Im folgenden HTML-Beispiel wird ein Datumswert an einen AEM Forms-Prozess namens `SOAPEchoService` übergeben. Der Name der Aufrufmethode lautet `echoCalendar`. Beachten Sie, dass die HTML-`Post`-Methode verwendet wird.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/SOAPEchoService/echoCalendar" method="post">
 
 Date: <input type="text" name="value-to-echo" value="2009-01-02T12:15:30Z">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Übergeben von Dokumenten an einen Prozess**

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess namens `MyApplication/EncryptDocument` aufgerufen, für den ein PDF-Dokument erforderlich ist. Weitere Informationen zu diesem Prozess finden Sie unter [Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/MyApplication/EncryptDocument/invoke" method="post"
          enctype="multipart/form-data">
 
 File: <input type="file" name="value-to-echo">
 <input type="submit" value="Submit"/>
 
 </form>
 
 </body>
 </html>
```

**Übergeben von Dokument- und Textwerten an einen Prozess**

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess namens `RestTest3` aufgerufen, für den ein Dokument und zwei Textwerte erforderlich sind. Beachten Sie, dass die HTML-Post-Methode verwendet wird.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/RestTest3" method="post"
          enctype="multipart/form-data">
 
 Doc: <input type="file" name="inDoc">
 String 1: <input type="text" name="inListOfStrings" value="hello">
 String 2: <input type="text" name="inListOfStrings" value="privet">
 <input type="submit" value="Submit"/>
 
 </form>
 
 </body>
 </html>
```

**Übergeben von Auflistungswerten an einen Prozess**

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess mit dem Namen `SOAPEchoService` aufgerufen, für den ein Auflistungswert erforderlich ist. Beachten Sie, dass die HTML-Post-Methode verwendet wird.

```html
 <html>
 <body>
 
 <form name="input" action="https://hiro-xp:8080/rest/services/SOAPEchoService/echoEnum" method="post">
 
 Color Enum Value: <input type="text" name="value-to-echo" value="green">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST**

Sie können einen kurzlebigen AEM Forms-Prozess namens *MyApplication/EncryptDocument* mithilfe von REST aufrufen.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Code-Beispiel zu folgen, erstellen Sie mithilfe von Workbench einen Prozess mit dem Namen `MyApplication/EncryptDocument`. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

   Wenn dieser Vorgang mithilfe einer REST-Anfrage aufgerufen wird, wird das verschlüsselte PDF-Dokument im Webbrowser angezeigt. Bevor Sie das PDF-Dokument anzeigen, geben Sie das Kennwort an (es sei denn, die Sicherheit ist deaktiviert). Der folgende HTML-Code stellt eine REST-Aufrufanforderung für den Prozess `MyApplication/EncryptDocument` dar.

   ```html
    <html>
    <body>
    <form action="https://hiro-xp:8080/rest/services/MyApplication/EncryptDocument" method="post" enctype="multipart/form-data">
         <p>Chose a PDF file (.pdf) to send to the EncryptDocument process.</p>
         <p>file:
           <input type="file" name="inDoc" />
         </p>
         <p>
           <input type="submit"/>
         </p>
    </form>
    </body>
   ```

**Aufrufen des Prozesses MyApplication/EncryptDocument aus Acrobat** {#invoke-process-acrobat}

Sie können einen Forms-Prozess über Acrobat mithilfe einer REST-Anfrage aufrufen. Sie können beispielsweise den Prozess *MyApplication/EncryptDocument* aufrufen. Um einen Forms-Prozess aus Acrobat aufzurufen, platzieren Sie in Designer eine Senden-Schaltfläche auf einer XDP-Datei. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63_de).)

Geben Sie die URL an, um den Prozess innerhalb der *Senden an URL* -Feld, wie in der folgenden Abbildung dargestellt.

Die vollständige URL zum Aufrufen des Prozesses lautet https://hiro-xp:8080/rest/services/MyApplication/EncryptDocument.

Wenn für den Vorgang ein PDF-Dokument als Eingabewert erforderlich ist, stellen Sie sicher, dass Sie das Formular als PDF übermitteln, wie in der vorherigen Abbildung dargestellt. Um einen Prozess erfolgreich aufzurufen, muss der Prozess außerdem ein PDF-Dokument zurückgeben. Andernfalls kann Acrobat den Rückgabewert nicht verarbeiten und es tritt ein Fehler auf. Sie brauchen den Namen der Eingabeprozessvariablen nicht anzugeben. Der Prozess *MyApplication/EncryptDocument* hat beispielsweise eine Eingabevariable mit dem Namen `inDoc`. Sie brauchen inDoc nicht anzugeben, solange das Formular als PDF übermittelt wird.

Sie können auch Formulardaten als XML an einen Forms-Prozess senden. Stellen Sie sicher, dass die Variable `Submit As` -Dropdown-Liste gibt XML an. Da der Rückgabewert des Prozesses ein PDF-Dokument sein muss, wird das PDF-Dokument in Acrobat angezeigt.
