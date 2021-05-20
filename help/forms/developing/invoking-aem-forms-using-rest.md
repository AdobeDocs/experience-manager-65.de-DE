---
title: Aufrufen von AEM Forms mithilfe von REST-Anforderungen
seo-title: Aufrufen von AEM Forms mithilfe von REST-Anforderungen
description: Rufen Sie Prozesse auf, die in Workbench mit REST-Anforderungen erstellt wurden.
seo-description: Rufen Sie Prozesse auf, die in Workbench mit REST-Anforderungen erstellt wurden.
uuid: 3a19a296-f3fe-4e50-9143-b68aed37f9ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: df7b60bb-4897-479e-a05e-1b1e9429ed87
role: Developer
exl-id: 991fbc56-f144-4ae6-b010-8d02f780d347
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2520'
ht-degree: 4%

---

# Aufrufen von AEM Forms mithilfe von REST-Anforderungen {#invoking-aem-forms-using-rest-requests}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

In Workbench erstellte Prozesse können so konfiguriert werden, dass Sie sie mithilfe von Representational State Transfer (REST)-Anforderungen aufrufen können. REST-Anforderungen werden von HTML-Seiten aus gesendet. Das heißt, Sie können einen Forms-Prozess direkt über eine Webseite mit einer REST-Anfrage aufrufen. Sie können beispielsweise eine neue Instanz einer Webseite öffnen. Anschließend können Sie einen Forms-Prozess aufrufen und ein gerendertes PDF-Dokument mit Daten laden, die in einer HTTP-POST-Anfrage gesendet wurden.

Es gibt zwei Arten von HTML-Clients. Der erste HTML-Client ist ein AJAX Client, der in JavaScript geschrieben ist. Der zweite Client ist ein HTML-Formular mit einer Senden-Schaltfläche. Eine HTML-basierte Client-Anwendung ist nicht der einzige mögliche REST-Client. Jede Client-Anwendung, die HTTP-Anforderungen unterstützt, kann einen Dienst mithilfe eines REST-Aufrufs aufrufen. Beispielsweise können Sie einen Dienst aufrufen, indem Sie einen REST-Aufruf aus einem PDF-Formular verwenden. (Siehe [Aufrufen des Prozesses MyApplication/EncryptDocument von Acrobat](#rest-invocation-examples).)

Bei der Verwendung von REST-Anfragen wird empfohlen, Forms-Dienste nicht direkt aufzurufen. Rufen Sie stattdessen Prozesse auf, die in Workbench erstellt wurden. Verwenden Sie beim Erstellen eines Prozesses, der für den REST-Aufruf vorgesehen ist, einen programmatischen Startpunkt. In diesem Fall wird der REST-Endpunkt automatisch hinzugefügt. Informationen zum Erstellen von Prozessen in Workbench finden Sie unter [Workbench verwenden](https://www.adobe.com/go/learn_aemforms_workbench_63).

Wenn Sie einen Dienst mithilfe von REST aufrufen, werden Sie nach einem Benutzernamen und Kennwort für AEM Formulare aufgefordert. Wenn Sie jedoch keinen Benutzernamen und kein Kennwort angeben möchten, können Sie die Dienstsicherheit deaktivieren.

Um einen Forms-Dienst (ein Prozess wird zu einem Dienst, wenn der Prozess aktiviert wird) mithilfe von REST aufzurufen, konfigurieren Sie einen REST-Endpunkt. (Siehe &quot;Verwalten von Endpunkten&quot;in [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).)

Nachdem ein REST-Endpunkt konfiguriert wurde, können Sie einen Forms-Dienst mithilfe einer HTTP-GET oder einer POST-Methode aufrufen.

```java
 action="https://hiro-xp:8080/rest/services/[ServiceName]/[OperationName]:[ServiceVersion]" method="post" enctype="multipart/form-data"
```

Der obligatorische Wert `ServiceName` ist der Name des aufzurufenden Forms-Dienstes. Der optionale Wert `OperationName` ist der Name des Dienstvorgangs. Wenn dieser Wert nicht angegeben ist, wird für diesen Namen standardmäßig `invoke` verwendet, der der Vorgangsname ist, der den Prozess startet. Der optionale Wert `ServiceVersion` ist die Version, die im X.Y-Format kodiert ist. Wenn dieser Wert nicht angegeben ist, wird die neueste Version verwendet. Der Wert `enctype` kann auch `application/x-www-form-urlencoded` sein.

## Unterstützte Datentypen {#supported-data-types}

Beim Aufrufen von AEM Forms-Diensten mithilfe von REST-Anfragen werden die folgenden Datentypen unterstützt:

* Primitive Java-Datentypen, z. B. Zeichenfolgen und Ganzzahlen
* `com.adobe.idp.Document` Datentyp
* XML-Datentypen wie `org.w3c.Document` und `org.w3c.Element`
* Sammlungsobjekte wie `java.util.List` und `java.util.Map`

   Diese Datentypen werden häufig als Eingabewerte für in Workbench erstellte Prozesse akzeptiert.

   Wenn ein Forms-Dienst mit der HTTP-POST-Methode aufgerufen wird, werden die Argumente innerhalb des HTTP-Anfrageinhalts übergeben. Wenn die Signatur des AEM Forms-Dienstes über einen Zeichenfolgeneingabeparameter verfügt, kann der Anfragetext den Textwert des Eingabeparameters enthalten. Wenn die Signatur des Dienstes mehrere Zeichenfolgenparameter definiert, kann die Anfrage der HTTP-Notation `application/x-www-form-urlencoded` folgen, wobei die Namen des Parameters als Feldnamen des Formulars verwendet werden.

   Wenn ein Forms-Dienst einen Zeichenfolgenparameter zurückgibt, ist das Ergebnis eine Textdarstellung des Ausgabeparameters. Wenn ein Dienst mehrere Zeichenfolgenparameter zurückgibt, ist das Ergebnis ein XML-Dokument, das die Ausgabeparameter im folgenden Format kodiert:
   ` <result> <output-paramater1>output-parameter-value-as-string</output-paramater1> . . . <output-paramaterN>output-parameter-value-as-string</output-paramaterN> </result>`

   >[!NOTE]
   >
   >Der Wert `output-paramater1` stellt den Namen des Ausgabeparameters dar.

   Wenn ein Forms-Dienst einen `com.adobe.idp.Document`-Parameter erfordert, kann der Dienst nur mit der HTTP-POST-Methode aufgerufen werden. Wenn der Dienst einen `com.adobe.idp.Document` -Parameter benötigt, wird der HTTP-Anforderungstext zum Inhalt des Eingabedokumenobjekts.

   Wenn für einen AEM Forms-Dienst mehrere Eingabeparameter erforderlich sind, muss der HTTP-Anforderungstext eine mehrteilige MIME-Nachricht gemäß RFC 1867 sein. (RFC 1867 ist ein Standard, der von Webbrowsern zum Hochladen von Dateien auf Websites verwendet wird.) Jeder Eingabeparameter muss als separater Teil der mehrteiligen Nachricht gesendet und im `multipart/form-data`-Format kodiert werden. Der Name jedes Teils muss mit dem Namen des Parameters übereinstimmen.

   Listen und Karten werden auch als Eingabewerte für in Workbench erstellte AEM Forms-Prozesse verwendet. Daher können Sie diese Datentypen bei Verwendung einer REST-Anfrage verwenden. Java-Arrays werden nicht unterstützt, da sie nicht als Eingabewert für einen AEM Forms-Prozess verwendet werden.

   Wenn ein Eingabeparameter eine Liste ist, kann ein REST-Client ihn senden, indem er den Parameter mehrmals angibt (einmal für jedes Element in der Liste). Wenn beispielsweise A eine Liste von Dokumenten ist, muss die Eingabe eine mehrteilige Nachricht sein, die aus mehreren Teilen namens A besteht. In diesem Fall wird jeder Teil mit dem Namen A zu einem Element in der Eingabeliste. Wenn B eine Liste von Zeichenfolgen ist, kann die Eingabe eine `application/x-www-form-urlencoded`-Nachricht sein, die aus mehreren Feldern namens B besteht. In diesem Fall wird jedes Formularfeld mit dem Namen B zu einem Element in der Eingabeliste.

   Wenn ein Eingabeparameter eine Zuordnung ist und es sich um den einzigen Eingabeparameter der Dienste handelt, wird jeder Teil/Feld der Eingabemeldung zu einem Schlüssel/Wert-Datensatz in der Zuordnung. Der Name jedes Teils/Felds wird zum Schlüssel des Datensatzes. Der Inhalt jedes Teils/Felds wird zum Wert des Datensatzes.

   Wenn eine Eingabezuordnung nicht der einzige Eingabeparameter für Dienste ist, kann jeder Schlüssel/Wert-Datensatz, der zur Zuordnung gehört, mit einem Parameter gesendet werden, der als Verkettung des Parameternamens und des Datensatzschlüssels bezeichnet wird. Beispielsweise kann eine Eingabezuordnung mit dem Namen `attributes` mit einer Liste der folgenden Schlüssel/Werte-Paare gesendet werden:

   `attributesColor=red`

   `attributesShape=box`

   `attributesWidth=5`

   Dies ergibt eine Zuordnung von drei Datensätzen: `Color=red`, `Shape=box` und `Width=5`.

   Die Ausgabeparameter der Listen- und Zuordnungstypen werden Teil der resultierenden XML-Nachricht. Die Ausgabeliste wird in XML als eine Reihe von XML-Elementen dargestellt, wobei für jedes Element in der Liste ein Element vorhanden ist. Jedes Element erhält denselben Namen wie der Ausgabelistenparameter. Der Wert jedes XML-Elements umfasst zwei Elemente:

* Eine Textdarstellung des Elements in der Liste (wenn die Liste aus Zeichenfolgentypen besteht)
* Eine URL, die auf den Inhalt des Dokuments verweist (wenn die Liste aus `com.adobe.idp.Document` -Objekten besteht)

   Das folgende Beispiel zeigt eine XML-Nachricht, die von einem Dienst mit einem einzigen Ausgabeparameter namens *list* zurückgegeben wird, der eine Liste von Ganzzahlen ist.
   ` <result>   <list>12345</list>   . . .   <list>67890</list>  </result>`Ein Ausgabezuordnungsparameter wird in der resultierenden XML-Nachricht als eine Reihe von XML-Elementen mit einem Element für jeden Datensatz in der Zuordnung dargestellt. Jedes Element erhält denselben Namen wie der Schlüssel des Zuordnungsdatensatzes. Der Wert jedes Elements ist entweder eine Textdarstellung des Datensatzwerts der Zuordnung (wenn die Zuordnung aus Datensätzen mit einem Zeichenfolgenwert besteht) oder eine URL, die auf den Inhalt des Dokuments verweist (wenn die Zuordnung aus Datensätzen mit dem Wert `com.adobe.idp.Document` besteht). Nachfolgend finden Sie ein Beispiel einer XML-Nachricht, die von einem Dienst mit einem einzigen Ausgabeparameter namens `map` zurückgegeben wird. Dieser Parameterwert ist eine Zuordnung aus Datensätzen, die Buchstaben mit `com.adobe.idp.Document`-Objekten verknüpfen.
   ` <result>   http://localhost:8080/DocumentManager/docm123/4567   . . .   <Z>http://localhost:8080/DocumentManager/docm987/6543</Z>  </result>  `

## Asynchrone Aufrufe {#asynchronous-invocations}

Einige AEM Forms-Dienste, z. B. am Menschen orientierte langlebige Prozesse, benötigen lange Zeit, um abgeschlossen zu werden. Diese Dienste können asynchron ohne Blockierung aufgerufen werden. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Ein AEM Forms-Dienst kann asynchron aufgerufen werden, indem `services` in der Aufruf-URL durch `async_invoke` ersetzt wird, wie im folgenden Beispiel gezeigt.

```java
 http://localhost:8080/rest/async_invoke/SomeService. SomeOperation?integer_input_variable=123&string_input_variable=abc
```

Diese URL gibt den Kennungswert (im Format &quot;text/plain&quot;) des für diesen Aufruf verantwortlichen Auftrags zurück.

Der Status des asynchronen Aufrufs kann mithilfe einer Aufruf-URL abgerufen werden, wobei `services` durch `async_status` ersetzt wird. Die URL muss einen Parameter `job_id` enthalten, der den Kennungswert des diesem Aufruf zugeordneten Auftrags angibt. Beispiel:

```java
 http://localhost:8080/rest/async_status/SomeService.SomeOperation?job_id=2345353443366564
```

Diese URL gibt einen ganzzahligen Wert (im Format &quot;text/plain&quot;) zurück, der den Auftragsstatus gemäß der Spezifikation von Job Manager kodiert (z. B. 2 bedeutet &quot;Ausführen&quot;, 3 bedeutet &quot;Abgeschlossen&quot;, 4 bedeutet &quot;Fehlgeschlagen&quot; usw.).

Wenn der Auftrag abgeschlossen ist, gibt die URL dasselbe Ergebnis zurück, als ob der Dienst synchron aufgerufen wurde.

Sobald der Auftrag abgeschlossen und das Ergebnis abgerufen wurde, kann der Auftrag mithilfe einer Aufruf-URL verworfen werden, wobei `services` durch `async_dispose` ersetzt wird. Die URL sollte auch einen Parameter `job_id` enthalten, der den Bezeichnerwert des Auftrags angibt. Beispiel:

```java
 http://localhost:8080/rest/async_dispose/SomeService.SomeOperation?job_id=2345353443366564
```

Wenn der Auftrag erfolgreich verworfen wurde, gibt diese URL eine leere Meldung zurück.

## Fehlerberichte {#error-reporting}

Wenn eine synchrone oder asynchrone Aufrufanforderung aufgrund einer auf dem Server ausgelösten Ausnahme nicht abgeschlossen werden kann, wird die Ausnahme als Teil der HTTP-Antwortmeldung gemeldet. Wenn die Aufruf-URL (oder die URL `async_result` im Fall eines asynchronen Aufrufs) kein .xml-Suffix aufweist, gibt der REST-Provider den HTTP-Code `500 Internal Server Error` zurück, gefolgt von einer Ausnahmemeldung.

Wenn die Aufruf-URL (oder die URL `async_result` bei einem asynchronen Aufruf) das Suffix .xml aufweist, gibt der REST-Provider den HTTP-Code `200 OK`zurück, gefolgt von einem XML-Dokument, das die Ausnahme im folgenden Format beschreibt.

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

Das Element `DSCError` ist optional und nur vorhanden, wenn die Ausnahme eine Instanz von `com.adobe.idp.dsc.DSCException` ist.

## Sicherheit und Authentifizierung {#security-and-authentication}

Um REST-Aufrufe mit einem sicheren Transport bereitzustellen, kann ein AEM Forms-Administrator das HTTPS-Protokoll auf dem J2EE-Anwendungsserver aktivieren, der als Host für AEM Forms dient. Diese Konfiguration ist spezifisch für den J2EE-Anwendungsserver. Es ist nicht Teil der Formularserverkonfiguration.

>[!NOTE]
>
>Beachten Sie als Workbench-Entwickler, der Ihre Prozesse über einen REST-Endpunkt verfügbar machen möchte, das XSS-Schwachstellenproblem. XSS-Schwachstellen können zum Stehlen oder Bearbeiten von Cookies, zum Ändern der Darstellung von Inhalten und zum Kompromittieren vertraulicher Informationen verwendet werden. Es wird empfohlen, die Prozesslogik mit den zusätzlichen Validierungsregeln für Eingabe- und Ausgabedaten zu erweitern, wenn die XSS-Schwachstelle ein Problem darstellt.

## AEM Forms-Dienste, die REST-Aufruf unterstützen {#aem-forms-services-that-support-rest-invocation}

Es wird zwar empfohlen, Prozesse aufzurufen, die mit Workbench anstatt direkt mit Diensten erstellt wurden, es gibt jedoch einige AEM Forms-Dienste, die REST-Aufrufe unterstützen. Es wird empfohlen, einen Prozess im Gegensatz zu einem Dienst direkt aufzurufen, da es effizienter ist, einen Prozess aufzurufen. Betrachten Sie das folgende Szenario. Angenommen, Sie möchten eine Richtlinie aus einem REST-Client erstellen. Das heißt, Sie möchten, dass der REST-Client Werte wie den Richtliniennamen und die Offline-Nutzungsdauer definiert.

Um eine Richtlinie zu erstellen, müssen Sie komplexe Datentypen definieren, z. B. ein `PolicyEntry` -Objekt. Ein `PolicyEntry` -Objekt definiert Attribute wie Berechtigungen, die mit der Richtlinie verknüpft sind. (Siehe [Erstellen von Richtlinien](/help/forms/developing/protecting-documents-policies.md#creating-policies).)

Anstatt eine REST-Anfrage zum Erstellen einer Richtlinie zu senden (dazu gehört auch das Definieren komplexer Datentypen wie ein `PolicyEntry` -Objekt), erstellen Sie einen Prozess, der mithilfe von Workbench eine Richtlinie erstellt. Definieren Sie den Prozess, um primitive Eingabevariablen zu akzeptieren, z. B. einen Zeichenfolgenwert, der den Prozessnamen definiert, oder eine Ganzzahl, die die Offline-Nutzungsdauer definiert.

Auf diese Weise müssen Sie keine REST-Aufrufanforderung erstellen, die komplexe Datentypen enthält, die für den Vorgang erforderlich sind. Der Prozess definiert die komplexen Datentypen und alles, was Sie vom REST-Client aus tun, ist, den Prozess aufzurufen und primitive Datentypen zu übergeben. Informationen zum Aufrufen eines Prozesses mit REST finden Sie unter [Aufrufen des Prozesses MyApplication/EncryptDocument mit REST](#rest-invocation-examples).

In der folgenden Liste sind die AEM Forms-Dienste aufgeführt, die einen direkten REST-Aufruf unterstützen.

* Distiller-Dienst
* Rights Management-Dienst
* GeneratePDF-Dienst
* Generate3dPDF-Dienst
* FormDataIntegration

## Beispiele für REST-Aufrufe {#rest-invocation-examples}

Die folgenden REST-Aufrufbeispiele werden bereitgestellt:

* Übergeben boolescher Werte an einen AEM Forms-Prozess
* Übergeben von Datumswerten an einen AEM Forms-Prozess
* Übergeben von Dokumenten an einen AEM Forms-Prozess
* Übergeben von Dokument- und Textwerten an einen AEM Forms-Prozess
* Übergeben von Auflistungswerten an einen AEM Forms-Prozess
* Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST
* Aufrufen des MyApplication/EncryptDocument-Prozesses aus Acrobat

   Jedes Beispiel zeigt die Übergabe verschiedener Datentypen an einen AEM Forms-Prozess

**Übergeben boolescher Werte an einen Prozess**

Im folgenden HTML-Beispiel werden zwei `Boolean`-Werte an einen AEM Forms-Prozess mit dem Namen `RestTest2` übergeben. Der Name der Aufrufmethode ist `invoke` und die Version ist 1.0. Beachten Sie, dass die HTML Post-Methode verwendet wird.

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

Im folgenden HTML-Beispiel wird ein Datumswert an einen AEM Forms-Prozess mit dem Namen `SOAPEchoService` übergeben. Der Name der Aufrufmethode ist `echoCalendar`. Beachten Sie, dass die HTML-Methode `Post` verwendet wird.

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

Das folgende HTML-Beispiel ruft einen AEM Forms-Prozess mit dem Namen `MyApplication/EncryptDocument` auf, für den ein PDF-Dokument erforderlich ist. Weitere Informationen zu diesem Prozess finden Sie unter [AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) aufrufen.

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

Das folgende HTML-Beispiel ruft einen AEM Forms-Prozess mit dem Namen `RestTest3` auf, für den ein Dokument und zwei Textwerte erforderlich sind. Beachten Sie, dass die HTML Post-Methode verwendet wird.

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

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess mit dem Namen `SOAPEchoService` aufgerufen, für den ein Auflistungswert erforderlich ist. Beachten Sie, dass die HTML Post-Methode verwendet wird.

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

Sie können einen kurzlebigen AEM Forms-Prozess mit dem Namen *MyApplication/EncryptDocument* mithilfe von REST aufrufen.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` mithilfe von Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

   Wenn dieser Prozess mithilfe einer REST-Anfrage aufgerufen wird, wird das verschlüsselte PDF-Dokument im Webbrowser angezeigt. Geben Sie vor dem Anzeigen des PDF-Dokuments das Kennwort an (es sei denn, die Sicherheit ist deaktiviert). Der folgende HTML-Code stellt eine REST-Aufrufanforderung für den `MyApplication/EncryptDocument`-Prozess dar.

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

**Aufrufen des MyApplication/EncryptDocument-Prozesses aus Acrobat** {#invoke-process-acrobat}

Sie können einen Forms-Prozess über Acrobat mithilfe einer REST-Anfrage aufrufen. Sie können beispielsweise den Prozess *MyApplication/EncryptDocument* aufrufen. Um einen Forms-Prozess aus Acrobat aufzurufen, platzieren Sie eine Senden-Schaltfläche in einer XDP-Datei in Designer. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63).)

Geben Sie die URL zum Aufrufen des Prozesses im Feld *Senden an URL* der Schaltfläche an, wie in der folgenden Abbildung dargestellt.

Die vollständige URL zum Aufrufen des Prozesses lautet https://hiro-xp:8080/rest/services/MyApplication/EncryptDocument.

Wenn für den Prozess ein PDF-Dokument als Eingabewert erforderlich ist, stellen Sie sicher, dass Sie das Formular als PDF senden, wie in der vorherigen Abbildung gezeigt. Um einen Prozess erfolgreich aufzurufen, muss der Prozess außerdem ein PDF-Dokument zurückgeben. Andernfalls kann Acrobat den Rückgabewert nicht verarbeiten und es tritt ein Fehler auf. Sie müssen den Namen der Eingabeprozessvariablen nicht angeben. Beispielsweise verfügt der Prozess *MyApplication/EncryptDocument* über eine Eingabevariable mit dem Namen `inDoc`. Sie müssen inDoc nicht angeben, solange das Formular als PDF gesendet wird.

Sie können Formulardaten auch als XML an einen Forms-Prozess senden. Um XML-Daten zu senden, stellen Sie sicher, dass in der Dropdown-Liste `Submit As` XML angegeben ist. Da der Rückgabewert des Prozesses ein PDF-Dokument sein muss, wird das PDF-Dokument in Acrobat angezeigt.
