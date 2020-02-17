---
title: Aufrufen von AEM Forms mithilfe von REST-Anforderungen
seo-title: Aufrufen von AEM Forms mithilfe von REST-Anforderungen
description: 'null'
seo-description: 'null'
uuid: 3a19a296-f3fe-4e50-9143-b68aed37f9ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: df7b60bb-4897-479e-a05e-1b1e9429ed87
translation-type: tm+mt
source-git-commit: 7cbe3e94eddb81925072f68388649befbb027e6d

---


# Aufrufen von AEM Forms mithilfe von REST-Anforderungen {#invoking-aem-forms-using-rest-requests}

In Workbench erstellte Prozesse können so konfiguriert werden, dass Sie sie mithilfe von Representational State Transfer (REST)-Anforderungen aufrufen können. REST-Anforderungen werden von HTML-Seiten aus gesendet. Das heißt, Sie können einen Forms-Prozess direkt von einer Webseite aufrufen, indem Sie eine REST-Anforderung verwenden. Sie können beispielsweise eine neue Instanz einer Webseite öffnen. Anschließend können Sie einen Formularprozess aufrufen und ein gerendertes PDF-Dokument mit Daten laden, die in einer HTTP POST-Anforderung gesendet wurden.

Es gibt zwei Arten von HTML-Clients. Der erste HTML-Client ist ein AJAX-Client, der in JavaScript geschrieben wurde. Der zweite Client ist ein HTML-Formular mit einer Senden-Schaltfläche. Eine HTML-basierte Client-Anwendung ist nicht der einzige mögliche REST-Client. Jede Clientanwendung, die HTTP-Anforderungen unterstützt, kann einen Dienst mit einem REST-Aufruf aufrufen. Beispielsweise können Sie einen Dienst über einen REST-Aufruf aus einem PDF-Formular aufrufen. (Siehe [Aufrufen des MyApplication/EncryptDocument-Prozesses aus Acrobat](#rest-invocation-examples).)

Bei REST-Anforderungen wird empfohlen, Forms-Dienste nicht direkt aufzurufen. Rufen Sie stattdessen Prozesse auf, die in Workbench erstellt wurden. Verwenden Sie beim Erstellen eines Prozesses, der für den REST-Aufruf vorgesehen ist, einen programmatischen Startpunkt. In diesem Fall wird der REST-Endpunkt automatisch hinzugefügt. Informationen zum Erstellen von Prozessen in Workbench finden Sie unter [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

Wenn Sie einen Dienst mit REST aufrufen, werden Sie zur Eingabe eines AEM Forms-Benutzernamens und -Kennworts aufgefordert. Wenn Sie jedoch keinen Benutzernamen und kein Kennwort angeben möchten, können Sie die Dienstsicherheit deaktivieren.

Um einen Forms-Dienst aufzurufen (ein Prozess wird bei Aktivierung des Prozesses zu einem Dienst), konfigurieren Sie einen REST-Endpunkt. (Siehe &quot;Verwalten von Endpunkten&quot;in der [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).)

Nachdem ein REST-Endpunkt konfiguriert wurde, können Sie einen Forms-Dienst mit einer HTTP GET-Methode oder einer POST-Methode aufrufen.

```as3
 action="https://hiro-xp:8080/rest/services/[ServiceName]/[OperationName]:[ServiceVersion]" method="post" enctype="multipart/form-data"
```

Der obligatorische `ServiceName` Wert ist der Name des aufzurufenden Forms-Dienstes. Der optionale `OperationName` Wert ist der Name des Dienstvorgangs. Wenn dieser Wert nicht angegeben ist, wird dieser Name standardmäßig verwendet `invoke`(d. h. der Vorgangsname, der den Prozess startet). Der optionale `ServiceVersion` Wert ist die im X.Y-Format kodierte Version. Wenn dieser Wert nicht angegeben ist, wird die neueste Version verwendet. Der `enctype` Wert kann auch `application/x-www-form-urlencoded`sein.

## Unterstützte Datentypen {#supported-data-types}

Die folgenden Datentypen werden beim Aufrufen von AEM Forms-Diensten mit REST-Anforderungen unterstützt:

* Java-Primitive-Datentypen wie Strings und Ganzzahlen
* `com.adobe.idp.Document` Datentyp
* XML-Datentypen wie `org.w3c.Document` und `org.w3c.Element`
* Sammlungsobjekte wie `java.util.List` und `java.util.Map`

   Diese Datentypen werden normalerweise als Eingabewerte für Prozesse akzeptiert, die in Workbench erstellt wurden.

   Wenn ein Forms-Dienst mit der HTTP POST-Methode aufgerufen wird, werden die Argumente im HTTP-Anforderungstext übergeben. Wenn die Signatur des AEM Forms-Dienstes einen Zeichenfolgeneingabeparameter hat, kann der Anforderungstext den Textwert des Eingabeparameters enthalten. Wenn die Unterschrift des Dienstes mehrere Zeichenfolgenparameter definiert, kann die Anforderung der `application/x-www-form-urlencoded` Schreibweise des HTTP-Dienstes folgen, wobei die Namen des Parameters als Feldnamen des Formulars verwendet werden.

   Wenn ein Forms-Dienst einen Zeichenfolgenparameter zurückgibt, ist das Ergebnis eine Textdarstellung des Ausgabeparameters. Wenn ein Dienst mehrere Zeichenfolgenparameter zurückgibt, ist das Ergebnis ein XML-Dokument, das die Ausgabeparameter im folgenden Format kodiert:
   ` <result> <output-paramater1>output-parameter-value-as-string</output-paramater1> . . . <output-paramaterN>output-parameter-value-as-string</output-paramaterN> </result>`**Hinweis **: Der`output-paramater1`Wert stellt den Namen des Ausgabeparameters dar.

   Wenn ein Forms-Dienst einen `com.adobe.idp.Document` Parameter erfordert, kann der Dienst nur mit der HTTP POST-Methode aufgerufen werden. Wenn der Dienst einen `com.adobe.idp.Document` Parameter erfordert, wird der Hauptteil der HTTP-Anforderung zum Inhalt des Eingabedokuments.

   Wenn ein AEM Forms-Dienst mehrere Eingabeparameter erfordert, muss der HTTP-Anforderungstext eine mehrteilige MIME-Meldung gemäß RFC 1867 sein. (RFC 1867 ist ein Standard, der von Webbrowsern zum Hochladen von Dateien auf Websites verwendet wird.) Jeder Eingabeparameter muss als separater Teil der mehrteiligen Meldung gesendet und im `multipart/form-data` Format kodiert werden. Der Name jedes Teils muss mit dem Namen des Parameters übereinstimmen.

   Listen und Maps werden auch als Eingabewerte für in Workbench erstellte AEM Forms-Prozesse verwendet. Daher können Sie diese Datentypen bei der Verwendung einer REST-Anforderung verwenden. Java-Arrays werden nicht unterstützt, da sie nicht als Eingabewert für einen AEM Forms-Prozess verwendet werden.

   Wenn ein Eingabeparameter eine Liste ist, kann ein REST-Client ihn senden, indem er den Parameter mehrmals angibt (einmal für jedes Element in der Liste). Wenn A beispielsweise eine Liste von Dokumenten ist, muss die Eingabe eine mehrteilige Meldung sein, die aus mehreren Teilen mit dem Namen A besteht. In diesem Fall wird jedes Teil mit dem Namen A zu einem Element in der Eingabeliste. Wenn B eine Liste von Zeichenfolgen ist, kann die Eingabe eine `application/x-www-form-urlencoded` Meldung sein, die aus mehreren Feldern mit dem Namen B besteht. In diesem Fall wird jedes Formularfeld mit dem Namen B zu einem Element in der Eingabeliste.

   Wenn ein Eingabeparameter eine Zuordnung ist und es sich um den reinen Eingabeparameter für Dienste handelt, wird jeder Teil/Feld der Eingabemeldung zu einem Schlüssel/Wert-Datensatz in der Zuordnung. Der Name jedes Teils/Felds wird zum Schlüssel des Datensatzes. Der Inhalt der einzelnen Teile/Felder wird zum Datensatzwert.

   Wenn eine Eingabemap nicht der einzige Eingabeparameter für Dienste ist, kann jeder Schlüssel/Wert-Datensatz, der zur Map gehört, mit einem Parameter gesendet werden, der als Verkettung des Parameternamens und des Datensatzschlüssels benannt ist. Beispielsweise kann eine Eingabemap mit dem Namen `attributes` mit einer Liste der folgenden Schlüssel/Werte-Paare gesendet werden:

   `attributesColor=red`

   `attributesShape=box`

   `attributesWidth=5`

   Dies ergibt eine Karte mit drei Datensätzen: `Color=red`, `Shape=box`und `Width=5`.

   Die Ausgabeparameter der Listen- und Zuordnungstypen werden Teil der XML-Meldung. Die Ausgabeliste wird in XML als eine Reihe von XML-Elementen mit einem Element für jedes Element in der Liste dargestellt. Jedem Element wird der gleiche Name wie dem Ausgabelistenparameter gegeben. Der Wert jedes XML-Elements besteht aus zwei Elementen:

* Eine Textdarstellung des Elements in der Liste (wenn die Liste aus Zeichenfolgen-Typen besteht)
* Eine URL, die auf den Inhalt des Dokuments verweist (wenn die Liste aus `com.adobe.idp.Document` Objekten besteht)

   Das folgende Beispiel ist eine XML-Meldung, die von einem Dienst zurückgegeben wird, der über einen einzigen Ausgabeparameter namens *list*verfügt, bei dem es sich um eine Liste von Ganzzahlen handelt.
   ` <result>   <list>12345</list>   . . .   <list>67890</list>  </result>`Ein Ausgabezuordnungsparameter wird in der resultierenden XML-Meldung als eine Reihe von XML-Elementen mit einem Element für jeden Datensatz in der Zuordnung dargestellt. Jedes Element erhält denselben Namen wie der Schlüssel des Kartendatensatzes. Der Wert jedes Elements ist entweder eine Textdarstellung des Wertes des Map-Datensatzes (wenn die Zuordnung aus Datensätzen mit einem Zeichenfolgenwert besteht) oder eine URL, die auf den Inhalt des Dokuments verweist (wenn die Zuordnung aus Datensätzen mit dem `com.adobe.idp.Document` Wert besteht). Nachstehend finden Sie ein Beispiel für eine XML-Meldung, die von einem Dienst mit einem einzigen Ausgabeparameter namens `map`zurückgegeben wird. Dieser Parameterwert ist eine Zuordnung, die aus Datensätzen besteht, die Briefe mit `com.adobe.idp.Document` Objekten verbinden.
   ` <result>   http://localhost:8080/DocumentManager/docm123/4567   . . .   <Z>http://localhost:8080/DocumentManager/docm987/6543</Z>  </result>  `

## Asynchrone Aufrufe {#asynchronous-invocations}

Einige AEM Forms-Dienste, z. B. menschenorientierte Prozesse mit langer Lebensdauer, benötigen eine lange Zeit, um abgeschlossen zu werden. Diese Dienste können asynchron ohne Blockierung aufgerufen werden. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Ein AEM Forms-Dienst kann asynchron aufgerufen werden, indem er `services` durch `async_invoke` die Aufruf-URL ersetzt wird, wie im folgenden Beispiel gezeigt.

```as3
 http://localhost:8080/rest/async_invoke/SomeService. SomeOperation?integer_input_variable=123&string_input_variable=abc
```

Diese URL gibt den Bezeichnerwert (im Format &quot;text/plain&quot;) des Auftrags zurück, der für diesen Aufruf verantwortlich ist.

Der Status des asynchronen Aufrufs kann mithilfe einer URL abgerufen werden, die durch eine `services` ersetzte URL ersetzt wird `async_status`. Die URL muss einen `job_id` Parameter enthalten, der den Bezeichnerwert des mit diesem Aufruf verknüpften Auftrags angibt. Beispiel:

```as3
 http://localhost:8080/rest/async_status/SomeService.SomeOperation?job_id=2345353443366564
```

Diese URL gibt einen ganzzahligen Wert (im Format &quot;text/plain&quot;) zurück, der den Auftragsstatus gemäß der Spezifikation des Job Managers kodiert (z. B. 2 bedeutet Ausführen, 3 bedeutet abgeschlossen, 4 bedeutet fehlgeschlagen usw.).

Wenn der Auftrag abgeschlossen ist, gibt die URL dasselbe Ergebnis zurück, als ob der Dienst synchron aufgerufen wurde.

Nachdem der Auftrag abgeschlossen und das Ergebnis abgerufen wurde, kann der Auftrag mithilfe einer Aufruf-URL entsorgt werden, die durch ersetzt `services` wird `async_dispose`. Die URL sollte auch einen `job_id` Parameter enthalten, der den Bezeichnerwert des Auftrags angibt. Beispiel:

```as3
 http://localhost:8080/rest/async_dispose/SomeService.SomeOperation?job_id=2345353443366564
```

Wenn der Auftrag erfolgreich gelöscht wurde, gibt diese URL eine leere Meldung zurück.

## Fehler-Berichterstellung {#error-reporting}

Wenn eine synchrone oder asynchrone Aufrufanforderung aufgrund einer auf dem Server ausgelösten Ausnahme nicht abgeschlossen werden kann, wird die Ausnahme als Teil der HTTP-Antwortmeldung gemeldet. Wenn die Aufrufungs-URL (bzw. die `async_result` -URL bei einem asynchronen Aufruf) kein .xml-Suffix hat, gibt der REST-Provider den HTTP-Code zurück, `500 Internal Server Error` gefolgt von einer Ausnahmemeldung.

Wenn die Aufrufungs-URL (oder die `async_result` -URL bei einem asynchronen Aufruf) das Suffix .xml enthält, gibt der REST-Provider den HTTP-Code zurück, `200 OK`gefolgt von einem XML-Dokument, das die Ausnahme im folgenden Format beschreibt.

```as3
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

Das `DSCError` Element ist optional und nur vorhanden, wenn die Ausnahme eine Instanz von `com.adobe.idp.dsc.DSCException`ist.

## Sicherheit und Authentifizierung {#security-and-authentication}

Um REST-Aufrufe mit einem sicheren Transport bereitzustellen, kann ein AEM Forms-Administrator das HTTPS-Protokoll auf dem J2EE-Anwendungsserver aktivieren, auf dem AEM Forms gehostet wird. Diese Konfiguration ist spezifisch für den J2EE-Anwendungsserver. Es ist nicht Teil der Formularserverkonfiguration.

>[!NOTE]
>
>Als Workbench-Entwickler, der Ihre Prozesse über einen REST-Endpunkt verfügbar machen möchte, sollten Sie das XSS-Schwachstellenproblem beachten. XSS-Schwachstellen können zum Stehlen oder Manipulieren von Cookies, zum Ändern der Darstellung von Inhalten und zum Kompromittieren vertraulicher Informationen verwendet werden. Es wird empfohlen, die Prozesslogik mit den zusätzlichen Validierungsregeln für Eingabe- und Ausgabedaten zu erweitern, wenn die XSS-Verwundbarkeit ein Problem darstellt.

## AEM Forms-Dienste, die REST-Aufrufe unterstützen {#aem-forms-services-that-support-rest-invocation}

Es wird empfohlen, Prozesse, die mit Workbench erstellt wurden, im Gegensatz zu Diensten direkt aufzurufen. Es gibt jedoch einige AEM Forms-Dienste, die REST-Aufrufe unterstützen. Es wird empfohlen, einen Prozess im Gegensatz zu einem Dienst direkt aufzurufen, weil es effizienter ist, einen Prozess aufzurufen. Betrachten Sie das folgende Szenario. Angenommen, Sie möchten eine Richtlinie aus einem REST-Client erstellen. Das heißt, der REST-Client soll Werte wie den Richtliniennamen und die Offline-Nutzungsdauer definieren.

Um eine Richtlinie zu erstellen, müssen Sie komplexe Datentypen wie z. B. ein `PolicyEntry` Objekt definieren. Ein `PolicyEntry` Objekt definiert Attribute wie Berechtigungen, die der Richtlinie zugeordnet sind. (Siehe [Richtlinien](/help/forms/developing/protecting-documents-policies.md#creating-policies)erstellen.)

Anstatt eine REST-Anforderung zum Erstellen einer Richtlinie zu senden (wozu auch das Definieren komplexer Datentypen wie eines `PolicyEntry` Objekts gehören würde), erstellen Sie einen Prozess, der eine Richtlinie mithilfe von Workbench erstellt. Definieren Sie den Prozess zum Akzeptieren von primitiven Eingabevariablen, z. B. einem Zeichenfolgenwert, der den Prozessnamen oder eine Ganzzahl definiert, die die Offline-Nutzungsdauer definiert.

Auf diese Weise müssen Sie keine REST-Aufrufanforderung erstellen, die komplexe Datentypen enthält, die für den Vorgang erforderlich sind. Der Prozess definiert die komplexen Datentypen und alles, was Sie vom REST-Client aus tun, wird der Prozess aufgerufen und primitive Datentypen übergeben. Informationen zum Aufrufen eines Prozesses mit REST finden Sie unter [Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST](#rest-invocation-examples).

In der folgenden Liste werden die AEM Forms-Dienste aufgeführt, die direkte REST-Aufrufe unterstützen.

* Distiller-Dienst
* Rights Management-Dienst
* GeneratePDF-Dienst
* Generate3dPDF-Dienst
* FormDataIntegration

## Beispiele für REST-Aufrufe {#rest-invocation-examples}

Die folgenden REST-Aufrufbeispiele sind verfügbar:

* Übergeben boolescher Werte an einen AEM Forms-Prozess
* Übergeben von Datumswerten an einen AEM Forms-Prozess
* Übergeben von Dokumenten an einen AEM Forms-Prozess
* Übergeben von Dokument- und Textwerten an einen AEM Forms-Prozess
* Übergeben von Aufzählungswerten an einen AEM Forms-Prozess
* Aufrufen des MyApplication/EncryptDocument-Prozesses mithilfe von REST
* MyApplication/EncryptDocument-Prozess aus Acrobat aufrufen

   Jedes Beispiel zeigt die Übergabe verschiedener Datentypen an einen AEM Forms-Prozess

**Übergeben boolescher Werte an einen Prozess**

Im folgenden HTML-Beispiel werden zwei `Boolean` Werte an einen AEM Forms-Prozess mit dem Namen `RestTest2`übergeben. Der Name der Aufrufmethode lautet `invoke` und die Version 1.0.Beachten Sie, dass die HTML Post-Methode verwendet wird.

```as3
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

Im folgenden HTML-Beispiel wird ein Datumswert an einen AEM Forms-Prozess namens `SOAPEchoService`. Der Name der Aufrufmethode lautet `echoCalendar`. Beachten Sie, dass die HTML- `Post` Methode verwendet wird.

```as3
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

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess mit dem Namen `MyApplication/EncryptDocument` aufgerufen, für den ein PDF-Dokument erforderlich ist. Weitere Informationen zu diesem Vorgang finden Sie unter [Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).

```as3
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

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess mit dem Namen `RestTest3` aufgerufen, für den ein Dokument und zwei Textwerte erforderlich sind. Beachten Sie, dass die HTML Post-Methode verwendet wird.

```as3
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

**Übergeben von Aufzählungswerten an einen Prozess**

Im folgenden HTML-Beispiel wird ein AEM Forms-Prozess mit dem Namen `SOAPEchoService` aufgerufen, für den ein Aufzählungswert erforderlich ist. Beachten Sie, dass die HTML Post-Methode verwendet wird.

```as3
 <html>
 <body>
 
 <form name="input" action="https://hiro-xp:8080/rest/services/SOAPEchoService/echoEnum" method="post">
 
 Color Enum Value: <input type="text" name="value-to-echo" value="green">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Aufrufen des MyApplication/EncryptDocument-Prozesses mithilfe von REST**

Sie können einen kurzlebigen AEM Forms-Prozess mit dem Namen *MyApplication/EncryptDocument* mithilfe von REST aufrufen.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. To follow along with the code example, create a process named `MyApplication/EncryptDocument` using workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

   Wenn dieser Prozess mithilfe einer REST-Anforderung aufgerufen wird, wird das verschlüsselte PDF-Dokument im Webbrowser angezeigt. Bevor Sie das PDF-Dokument anzeigen, geben Sie das Kennwort an (es sei denn, die Sicherheit ist deaktiviert). Der folgende HTML-Code stellt eine REST-Aufrufanforderung für den `MyApplication/EncryptDocument` Prozess dar.

   ```as3
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

**MyApplication/EncryptDocument-Prozess aus Acrobat** aufrufen {#invoke-process-acrobat}

Sie können einen Formularprozess in Acrobat über eine REST-Anforderung aufrufen. Sie können beispielsweise den *MyApplication/EncryptDocument* -Prozess aufrufen. Um einen Formularprozess aus Acrobat aufzurufen, platzieren Sie eine Senden-Schaltfläche in einer XDP-Datei in Designer. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63).)

Geben Sie die URL an, um den Prozess im Feld &quot; *Senden an URL* &quot;der Schaltfläche aufzurufen, wie in der folgenden Abbildung dargestellt.

Die vollständige URL zum Aufrufen des Prozesses ist https://hiro-xp:8080/rest/services/MyApplication/EncryptDocument.

Wenn für den Prozess ein PDF-Dokument als Eingabewert erforderlich ist, stellen Sie sicher, dass Sie das Formular als PDF übermitteln, wie in der vorherigen Abbildung gezeigt. Um einen Prozess erfolgreich aufzurufen, muss der Prozess auch ein PDF-Dokument zurückgeben. Andernfalls kann Acrobat den Rückgabewert nicht verarbeiten und es tritt ein Fehler auf. Sie müssen nicht den Namen der Eingabeprozessvariablen angeben. Beispielsweise enthält der *MyApplication/EncryptDocument* -Prozess eine Eingabevariable mit dem Namen `inDoc`. Sie müssen nicht inDoc angeben, solange das Formular als PDF gesendet wird.

Sie können auch Formulardaten als XML an einen Formularprozess senden. Wenn Sie XML-Daten senden möchten, stellen Sie sicher, dass in der `Submit As` Dropdown-Liste &quot;XML&quot;angegeben ist. Da der Rückgabewert des Prozesses ein PDF-Dokument sein muss, wird das PDF-Dokument in Acrobat angezeigt.
