---
title: Aufrufen von AEM Forms mithilfe von Remoting
seo-title: Invoking AEM Forms using Remoting
description: Verwenden Sie Remoting, um einen AEM Forms-Prozess aufzurufen, der in Workbench erstellte Prozesse aufruft. Sie können einen AEM Forms-Prozess aus einem mit Flex erstellten Client-Programm aufrufen.
seo-description: Use Remoting to invoke an AEM Forms process to invoke processes created in Workbench. You can invoke a AEM Forms process from a client application built with Flex.
uuid: 592d1519-c38b-4b33-8cf3-61e2bff81501
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: 3d8bb2d3-b1f8-49e1-a529-b3e7a28da4bb
role: Developer
exl-id: 94a48776-f537-4b4e-8d71-51b08e463cba
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '4628'
ht-degree: 100%

---

# Aufrufen von AEM Forms mithilfe von Remoting {#invoking-aem-forms-using-remoting}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

In Workbench erstellte Prozesse können mit Remoting aufgerufen werden. Das heißt, Sie können einen AEM Forms-Prozess aus einem mit Flex erstellten Client-Programm aufrufen. Diese Funktion basiert auf Data Services.

>[!NOTE]
>
>Bei Verwendung von Remoting wird empfohlen, Prozesse aufzurufen, die in Workbench erstellt wurden, anstatt in AEM Forms-Services. Es ist jedoch möglich, AEM Forms-Services direkt aufzurufen. (Siehe Verschlüsseln von PDF-Dokumenten mit Remoting im AEM Forms Developer Center.)

>[!NOTE]
>
>Wenn ein AEM Forms-Service nicht so konfiguriert ist, dass er anonymen Zugriff zulässt, stellen Anforderungen von einem Flex-Client eine Herausforderung für den Webbrowser dar. Der Benutzer muss seine Anmeldeinformationen mit Benutzernamen und Kennwort eingeben.

Der folgende kurzlebige AEM Forms-Prozess mit dem Namen `MyApplication/EncryptDocument` kann mit Remoting aufgerufen werden. (Weitere Informationen zu diesem Prozess, wie Eingabe- und Ausgabewerte, finden Sie unter [Beispiel für einen kurzlebigen Prozess](/help/forms/developing/aem-forms-processes.md).)

![iu_iu_encryptdocumentprocess2](assets/iu_iu_encryptdocumentprocess2.png)

>[!NOTE]
>
>Um einen AEM Forms-Prozess mit einem Flex-Programm aufzurufen, stellen Sie sicher, dass ein Remoting-Endpunkt aktiviert ist. Standardmäßig ist ein Remoting-Endpunkt aktiviert, wenn Sie einen Prozess bereitstellen.

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das als Eingabewert übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Name des Eingabeparameters lautet `inDoc` und der Datentyp `document`. (Der Datentyp `document` ist ein verfügbarer Datentyp aus Workbench.)
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Der Name des Ausgabewerts für diesen Prozess lautet `outDoc` und stellt das kennwortverschlüsselte PDF-Dokument dar. Der Datentyp von outDoc lautet `document`.
1. Speichert das kennwortverschlüsselte PDF-Dokument als PDF-Datei im lokalen Dateisystem. Diese Aktion basiert auf dem Vorgang `WriteDocument`. 

>[!NOTE]
>
>Der Prozess `MyApplication/EncryptDocument` basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um den Code-Beispielen zu folgen, erstellen Sie mit Workbench einen Prozess mit dem Namen `MyApplication/EncryptDocument`.

>[!NOTE]
>
>Weitere Informationen zur Verwendung von Remoting zum Aufrufen eines langlebigen Prozesses finden Sie unter [Aufrufen von an Menschen orientierten langlebigen Prozessen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

**Siehe auch**

[Einschließen der AEM Forms Flex-Bibliotheksdatei](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Umgang mit Dokumenten mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms)](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Authentifizieren von mit Flex erstellten Client-Anwendungen](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

[Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)

[Aufrufen benutzerdefinierter Komponenten-Services mithilfe von Remoting](invoking-aem-forms-using-remoting.md#invoking-custom-component-services-using-remoting)

[Erstellung eines Client-Programms mit Flex, das einen an Menschen orientierten, langlebigen Prozess aufruft](/help/forms/developing/invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

[Erstellen von Flash Builder-Programmen, die SSO-Authentifizierung mithilfe von HTTP-Token durchführen](/help/forms/developing/creating-flash-builder-applications-perform.md#creating-flash-builder-applications-that-perform-sso-authentication-using-http-tokens)

Weitere Informationen zum Anzeigen von Prozessdaten in einem Flex-Diagrammsteuerelement finden Sie unter [Anzeigen von AEM Forms-Prozessdaten in Flex-Diagrammen](https://www.adobe.com/devnet/livecycle/articles/populating_flexcontrols.html).

>[!NOTE]
>
>*Vergewissern Sie sich, dass Sie die Datei „crossdomain.xml“ an der richtigen Stelle platzieren. Wenn Sie beispielsweise AEM Forms auf JBoss bereitgestellt haben, platzieren Sie diese Datei am folgenden Speicherort: &lt;install_directory>\Adobe_Experience_Manager_forms\jboss\server\lc_turnkey\deploy\jboss-web.deployer\ROOT.war*

## Einschließen der AEM Forms Flex-Bibliotheksdatei {#including-the-aem-forms-flex-library-file}

Um AEM Forms-Prozesse mithilfe von Remoting programmgesteuert aufzurufen, fügen Sie die Datei „adobe-remoting-provider.swc“ zum Klassenpfad Ihres Flex-Projekts hinzu. Diese SWC-Datei befindet sich am folgenden Speicherort:

* *&lt;install_directory>\Adobe_Experience_Manager_forms\sdk\misc\DataServices\Client-Libraries*

   wobei &lt;*install_directory*> der Ordner ist, in dem AEM Forms installiert ist.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Umgang mit Dokumenten mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms)](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Authentifizieren von mit Flex erstellten Client-Anwendungen](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

## Umgang mit Dokumenten mit Remoting {#handling-documents-with-remoting}

Einer der wichtigsten nicht primitiven Java-Typen, die in AEM Forms verwendet werden, ist die Klasse `com.adobe.idp.Document`. Normalerweise ist ein Dokument erforderlich, um einen Vorgang mit AEM Forms aufzurufen. Es handelt sich in erster Linie um ein PDF-Dokument, kann jedoch andere Dokumenttypen wie SWF, HTML, XML oder eine DOC-Datei enthalten. (Weitere Informationen unter [Übergeben von Daten an AEM Forms-Services mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

Eine mit Flex erstellte Client-Anwendung kann ein Dokument nicht direkt anfordern. Beispielsweise können Sie Adobe Reader nicht starten, um eine URL anzufordern, die eine PDF-Datei erzeugt. Anfragen für Dokumenttypen wie PDF- und Microsoft Word-Dokumente geben ein Ergebnis zurück, das eine URL ist. Der Client ist dafür verantwortlich, den Inhalt der URL anzuzeigen. Der Document Management-Service hilft beim Generieren der URL- und Content-Type-Informationen. Anfragen für XML-Dokumente geben das vollständige XML-Dokument im Ergebnis zurück.

### Übergeben eines Dokuments als Eingabeparameter {#passing-a-document-as-an-input-parameter}

Eine mit Flex erstellte Client-Anwendung kann ein Dokument nicht direkt an einen AEM Forms-Prozess übergeben. Stattdessen verwendet die Client-Anwendung eine Instanz der `mx.rpc.livecycle.DocumentReference`Klasse „ActionScript“ zum Übergeben von Eingabeparametern an einen Vorgang, der eine `com.adobe.idp.Document`-Instanz erwartet. Eine Flex-Client-Anwendung verfügt über mehrere Optionen zum Einrichten eines `DocumentReference`-Objekts:

* Wenn sich das Dokument auf dem Server befindet und der Dateispeicherort bekannt ist, setzen Sie die Eigenschaft „referenceType“ des „DocumentReference“-Objekts auf „REF_TYPE_FILE“. Geben Sie für die Eigenschaft „fileRef“ den Speicherort der Datei an, wie im folgenden Beispiel gezeigt:

```java
 ... var docRef: DocumentReference = new DocumentReference(); 
 docRef.referenceType = DocumentReference.REF_TYPE_FILE; 
 docRef.fileRef = "C:/install/adobe/cs2/How to Uninstall.pdf"; ...
```

* Wenn sich das Dokument auf dem Server befindet und Sie dessen URL kennen, setzen Sie die Eigenschaft „referenceType“ des „DocumentReference“-Objekts auf „REF_TYPE_URL“. Setzen Sie die Eigenschaft „url“ auf die URL, wie im folgenden Beispiel gezeigt wird:

```java
... var docRef: DocumentReference = new DocumentReference(); 
docRef.referenceType = DocumentReference.REF_TYPE_URL; 
docRef.url = "https://companyserver:8080/DocumentManager/116/7855"; ...
```

* Um ein „DocumentReference“-Objekt aus einer Textzeichenfolge in der Client-Anwendung zu erstellen, legen Sie die Eigenschaft „referenceType“ des „DocumentReference“-Objekts auf „REF_TYPE_INLINE“ fest. Legen Sie die Texteigenschaft auf den Text fest, der in das Objekt eingefügt werden soll, wie im folgenden Beispiel gezeigt:

```java
... var docRef: DocumentReference = new DocumentReference(); 
docRef.referenceType = DocumentReference.REF_TYPE_INLINE; 
docRef.text = "Text for my document";  // Optionally, you can override the server’s default character set  // if necessary:  // docRef.charsetName=CharacterSetName  ...
```

* Wenn sich das Dokument nicht auf dem Server befindet, verwenden Sie das Servlet „Remoting Upload“, um ein Dokument in AEM Forms hochzuladen. Neu in AEM Forms ist die Möglichkeit, sichere Dokumente hochzuladen. Beim Hochladen eines sicheren Dokuments müssen Sie einen Benutzer verwenden, der die Rolle *Document Upload Application User* hat. Ohne diese Rolle kann der Benutzer kein sicheres Dokument hochladen. Es wird empfohlen, Single Sign-on zum Hochladen eines sicheren Dokuments zu verwenden. (Weitere Informationen unter [Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting).)

>[!NOTE]
>Wenn AEM Forms so konfiguriert ist, dass unsichere Dokumente hochgeladen werden können, können Sie zum Hochladen eines Dokuments einen Benutzer verwenden, der nicht die Rolle „Document Upload Application User“ hat. Ein Benutzer kann auch über die Berechtigung zum Hochladen von Dokumenten verfügen. Wenn AEM Forms jedoch so konfiguriert ist, dass nur sichere Dokumente zugelassen werden, stellen Sie sicher, dass der Benutzer über die Rolle „Document Upload Application User“ oder die Berechtigung „Document Upload“ verfügt. (Weitere Informationen unter [Konfigurieren von AEM Forms zum Akzeptieren sicherer und unsicherer Dokumente](invoking-aem-forms-using-remoting.md#configuring-aem-forms-to-accept-secure-and-unsecure-documents).)

Sie verwenden standardmäßige Flash-Upload-Funktionen für die vorgesehene Upload-URL: `https://SERVER:PORT/remoting/lcfileupload`. Anschließend können Sie das `DocumentReference`-Objekt immer dann verwenden, wenn ein Eingabeparameter vom Typ `Document` erwartet wird.
` private function startUpload():void  {  fileRef.addEventListener(Event.SELECT, selectHandler);  fileRef.addEventListener("uploadCompleteData", completeHandler);  try  {   var success:Boolean = fileRef.browse();  }    catch (error:Error)  {   trace("Unable to browse for files.");  }  }      private function selectHandler(event:Event):void {  var request:URLRequest = new  URLRequest("https://SERVER:PORT/remoting/lcfileupload")  try   {   fileRef.upload(request);   }    catch (error:Error)   {   trace("Unable to upload file.");   }  }    private function completeHandler(event:DataEvent):void  {   var params:Object = new Object();   var docRef:DocumentReference = new DocumentReference();   docRef.url = event.data as String;   docRef.referenceType = DocumentReference.REF_TYPE_URL;  }`Der Remoting-Schnellstart verwendet das Remoting-Upload-Servlet, um eine PDF-Datei an den `MyApplication/EncryptDocument`-Prozess zu übergeben. (Weitere Informationen unter [Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting).)

```java
 
private
function startUpload(): void  { 
 fileRef.addEventListener(Event.SELECT, selectHandler); 
 fileRef.addEventListener("uploadCompleteData", completeHandler); 
 try  { 
  var success: Boolean = fileRef.browse(); 
 }  
 catch (error: Error)  { 
  trace("Unable to browse for files."); 
 } 
}   
private
function selectHandler(event: Event): void { 
 var request: URLRequest = new  URLRequest("https://SERVER:PORT/remoting/lcfileupload")  try  { 
  fileRef.upload(request); 
 }  
 catch (error: Error)  { 
  trace("Unable to upload file."); 
 } 
}  
private
function completeHandler(event: DataEvent): void  { 
 var params: Object = new Object(); 
 var docRef: DocumentReference = new DocumentReference(); 
 docRef.url = event.data as String; 
 docRef.referenceType = DocumentReference.REF_TYPE_URL; 
}
```

Der Remoting-Schnellstart verwendet das Remoting-Upload-Servlet, um eine PDF-Datei an die `MyApplication/EncryptDocument`-Prozess zu übergeben. (Weitere Informationen unter [Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting).)

### Zurückgeben eines Dokuments an eine Client-Anwendung {#passing-a-document-back-to-a-client-application}

Eine Client-Anwendung empfängt ein Objekt vom Typ `mx.rpc.livecycle.DocumentReference` für einen Service-Vorgang, der eine `com.adobe.idp.Document`-Instanz als Ausgabeparameter zurückgibt. Da eine Client-Anwendung „ActionScript“-Objekte und nicht Java verarbeitet, können Sie kein Java-basiertes „Document“-Objekt an einen Flex-Client zurückgeben. Stattdessen generiert der Server eine URL für das Dokument und übergibt die URL zurück an den Client. Die `referenceType`-Eigenschaft des Objekts `DocumentReference` gibt an, ob sich der Inhalt im `DocumentReference`-Objekt befindet oder von einer URL aus der `DocumentReference.url`-Eigenschaft ausgelesen werden muss. Die `DocumentReference.contentType`-Eigenschaft gibt den Typ des Dokuments an.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Einschließen der AEM Forms Flex-Bibliotheksdatei](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Authentifizieren von mit Flex erstellten Client-Anwendungen](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

[Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)

## Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mit Remoting {#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting}

Führen Sie die folgenden Aufgaben aus, um einen AEM Forms-Prozess aus einem mit Flex erstellten Programm aufzurufen:

1. Erstellen Sie eine `mx:RemoteObject`-Instanz.
1. Erstellen Sie eine `ChannelSet`-Instanz.
1. Übergeben Sie erforderliche Eingabewerte.
1. Verarbeiten Sie die Rückgabewerte.

>[!NOTE]
>In diesem Abschnitt wird beschrieben, wie Sie einen AEM Forms-Prozess aufrufen und ein Dokument hochladen, wenn AEM Forms für das Hochladen unsicherer Dokumente konfiguriert ist. Weitere Informationen zum Aufrufen von AEM Forms-Prozessen und Hochladen sicherer Dokumente sowie zum Konfigurieren von AEM Forms für die Annahme sicherer und unsicherer Dokumente finden Sie unter [Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting).

**Erstellen einer mx:RemoteObject-Instanz**

Sie erstellen eine `mx:RemoteObject`-Instanz, um einen in Workbench erstellten AEM Forms-Prozess aufzurufen. Um eine `mx:RemoteObject`-Instanz zu erstellen, geben Sie die folgenden Werte an:

* **id**: Der Name der `mx:RemoteObject`-Instanz, die den aufzurufenden Prozess darstellt.
* **Ziel**: Der Name des aufzurufenden AEM Forms-Prozesses. Um zum Beispiel den Prozess `MyApplication/EncryptDocument` aufzurufen, geben Sie `MyApplication/EncryptDocument` an.
* **result**: Der Name der Flex-Methode, die das Ergebnis verarbeitet.

Geben Sie innerhalb des Tags `mx:RemoteObject` ein Tag `<mx:method>` an, das den Namen der Aufrufmethode des Prozesses angibt. Normalerweise lautet der Name einer Forms-Aufruffunktion `invoke`.

Im folgenden Code-Beispiel wird eine `mx:RemoteObject`-Instanz erstellt, die den `MyApplication/EncryptDocument`-Prozess aufruft.

```java
 <mx:RemoteObject id="EncryptDocument" destination="MyApplication/EncryptDocument" result="resultHandler(event);">
          <mx:method name="invoke" result="handleExecuteInvoke(event)"/>
      </mx:RemoteObject>
```

**Erstellen eines Kanals in AEM Forms**

Ein Client-Programm kann AEM Forms aufrufen, indem ein Kanal in MXML oder ActionScript angegeben wird, wie im folgenden ActionScript-Beispiel gezeigt wird. Der Kanal muss ein `AMFChannel`, `SecureAMFChannel`, `HTTPChannel` oder `SecureHTTPChannel` sein.

```java
     ...
     private function refresh():void{
         var cs:ChannelSet= new ChannelSet();
         cs.addChannel(new AMFChannel("my-amf",
             "https://yourlcserver:8080/remoting/messagebroker/amf"));
         EncryptDocument.setCredentials("administrator", "password");
         EncryptDocument.channelSet = cs;
     }
     ...
```

Weisen Sie die `ChannelSet`-Instanz dem Feld `channelSet` der `mx:RemoteObject`-Instanz zu (wie im vorherigen Code-Beispiel gezeigt). Im Allgemeinen importieren Sie beim Aufruf der Methode `ChannelSet.addChannel` die Kanalklasse in einer Import-Anweisung, anstatt den voll qualifizierten Namen anzugeben.

**Übergeben von Eingabewerten**

Ein in Workbench erstellter Prozess kann null oder mehr Eingabeparameter annehmen und einen Ausgabewert zurückgeben. Ein Client-Programm übergibt Eingabeparameter in einem `ActionScript`-Objekt mit Feldern, die den Parametern entsprechen, die zum AEM Forms-Prozess gehören. Der kurzlebige Prozess mit dem Namen `MyApplication/EncryptDocument` erfordert einen Eingabeparameter namens `inDoc`. Der Name des vom Prozess offen gelegten Vorgangs lautet `invoke` (der Standardname für einen kurzlebigen Prozess). (Siehe [Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM-Formulare nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Im folgenden Code-Beispiel wird ein PDF-Dokument an den `MyApplication/EncryptDocument`-Prozess übergeben:

```java
     ...
     var params:Object = new Object();
 
     //Document is an instance of DocumentReference
     //that store an unsecured PDF document
     params["inDoc"] = pdfDocument;
 
     // Invoke an operation synchronously:
     EncryptDocument.invoke(params);
     ...
```

In diesem Code-Beispiel ist `pdfDocument` eine `DocumentReference`-Instanz, die ein ungesichertes PDF-Dokument enthält. Weitere Informationen zur `DocumentReference` finden Sie unter [Verarbeiten von Dokumenten mit AEM Forms Remoting (für AEM-Formulare nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting).

**Aufrufen einer bestimmten Version eines Services**

Sie können eine bestimmte Version eines Forms-Services aufrufen, indem Sie einen `_version`-Parameter in der Parameterzuordnung des Aufrufs verwenden. So rufen Sie beispielsweise Version 1.2 des `MyApplication/EncryptDocument`-Services auf::

```java
 var params:Object = new Object();
 params["inDoc"] = pdfDocument;
 params["_version"] = "1.2"
 var token:AsyncToken = echoService.echoString(params);
```

Der `version`-Parameter muss eine Zeichenfolge sein, die einen einzigen Punkt enthält. Die Werte links vom Punkt, Hauptversion, und rechts vom Punkt, Nebenversion, müssen Ganzzahlen sein. Wenn dieser Parameter nicht angegeben ist, wird die aktive Kopfversion aufgerufen.

**Verarbeitung der zurückgegebenen Werte**

AEM Forms-Prozessausgabeparameter werden in ActionScript-Objekte umgewandelt, aus denen das Client-Programm bestimmte Parameter nach Namen extrahiert, wie im folgenden Beispiel gezeigt. (Der Ausgabewert des `MyApplication/EncryptDocument`-Prozesses heißt `outDoc`.)

```java
     ...
     var res:Object = event.result;
     var docRef:DocumentReference = res["outDoc"] as DocumentReference;
     ...
```

**Aufrufen des Prozesses MyApplication/EncryptDocument**

Sie können den Prozess `MyApplication/EncryptDocument` aufrufen, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie eine `mx:RemoteObject`-Instanz entweder über ActionScript oder über MXML. Siehe Erstellen einer mx:RemoteObject-Instanz.
1. Richten Sie eine `ChannelSet`-Instanz ein, um mit AEM Forms zu kommunizieren, und verknüpfen Sie sie mit der `mx:RemoteObject`-Instanz. Siehe Erstellen eines Kanals in AEM Forms.
1. Rufen Sie die Methode `login` von ChannelSet oder die Methode `setCredentials` des Services auf, um den Wert der Benutzer-ID und das Kennwort anzugeben. (Siehe [Verwenden von Single Sign-On](invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Füllen Sie eine `mx.rpc.livecycle.DocumentReference`-Instanz mit einem ungesicherten PDF-Dokument, das an den Prozess `MyApplication/EncryptDocument` übergeben wird. (Siehe [Übergeben eines Dokuments als Eingabeparameter](invoking-aem-forms-using-remoting.md#passing-a-document-as-an-input-parameter).)
1. Verschlüsseln Sie das PDF-Dokument, indem Sie die Methode `invoke` der `mx:RemoteObject`-Instanz aufrufen. Übergeben Sie das `Object`, das den Eingabeparameter enthält (d. h. das ungesicherte PDF-Dokument). Siehe Übergeben von Eingabewerten.
1. Rufen Sie das kennwortverschlüsselte PDF-Dokument ab, das vom Prozess zurückgegeben wird. Siehe Verarbeitung der zurückgegebenen Werte.

[Schnellstart: Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-by-passing-an-unsecure-document-using-deprecated-for-aem-forms-aem-forms-remoting)

## Authentifizieren von mit Flex erstellten Client-Anwendungen {#authenticating-client-applications-built-with-flex}

Es gibt mehrere Möglichkeiten, wie der AEM Forms-Benutzer „Manager“ eine Remoting-Anfrage von einer Flex-Anwendung authentifizieren kann, einschließlich Single Sign-On in AEM Forms über den zentralen Anmelde-Service, einfachen Authentifizierung und benutzerdefinierte Authentifizierung. Wenn weder Single Sign-on noch der anonyme Zugriff aktiviert ist, führt eine Remoting-Anfrage entweder zur einfachen Authentifizierung (Standard) oder zur benutzerdefinierten Authentifizierung.

Die einfache Authentifizierung beruht auf der standardmäßigen J2EE-Basisauthentifizierung aus dem Web-Anwendungs-Container. Bei der einfachen Authentifizierung führt ein HTTP 401-Fehler zu einer Herausforderung für den Browser. Wenn Sie also versuchen, mittels „RemoteObject“ eine Verbindung zu einer Forms-Anwendung herzustellen und sich noch nicht über die Flex-Anwendung angemeldet haben, werden Sie vom Browser aufgefordert, einen Benutzernamen und ein Kennwort einzugeben.

Bei der benutzerdefinierten Authentifizierung sendet der Server einen Fehler an den Client, um anzugeben, dass eine Authentifizierung erforderlich ist.

>[!NOTE]
>Informationen zum Ausführen der Authentifizierung mit HTTP-Token finden Sie unter [Erstellen von Flash Builder-Anwendungen, die die SSO-Authentifizierung mithilfe von HTTP-Token durchführen](/help/forms/developing/creating-flash-builder-applications-perform.md#creating-flash-builder-applications-that-perform-sso-authentication-using-http-tokens).

### Verwenden der benutzerdefinierten Authentifizierung {#using-custom-authentication}

Sie aktivieren die benutzerdefinierte Authentifizierung in der Administration-Console, indem Sie die Authentifizierungsmethode im Remoting-Endpunkt von „Einfach“ in „Benutzerdefiniert“ ändern. Wenn Sie die benutzerdefinierte Authentifizierung verwenden, ruft Ihre Client-Anwendung die `ChannelSet.login`-Methode zur Anmeldung und die `ChannelSet.logout`-Methode zur Abmeldung auf.

>[!NOTE]
>In der vorherigen Version von AEM Forms haben Sie Anmeldeinformationen an ein Ziel gesendet, indem Sie die `RemoteObject.setCredentials`-Methode aufgerufen haben. Die `setCredentials`-Methode hat die Anmeldeinformationen erst beim ersten Versuch der Komponente, eine Verbindung zum Server herzustellen, an den Server übergeben. Wenn die Komponente ein fehlerhaftes Ereignis ausgegeben hat, konnten Sie daher nicht sicher sein, ob der Fehler aufgrund eines Authentifizierungsfehlers oder aus einem anderen Grund aufgetreten ist. Die `ChannelSet.login`-Methode stellt eine Verbindung zum Server her, wenn Sie sie aufrufen, damit Sie Authentifizierungsprobleme sofort verarbeiten können. Sie können auch weiterhin die `setCredentials`-Methode verwenden, allerdings wird die Verwendung der `ChannelSet.login`-Methode empfohlen.

Da mehrere Ziele dieselben Kanäle und das dazugehörige „ChannelSet“-Objekt verwenden können, wird der Benutzer bei der Anmeldung bei einem Ziel auch bei allen anderen Zielen, die denselben Kanal oder dieselben Kanäle verwenden, angemeldet. Wenn zwei Komponenten unterschiedliche Anmeldeinformationen auf dasselbe „ChannelSet“-Objekt anwenden, werden die zuletzt angewendeten Anmeldeinformationen verwendet. Wenn mehrere Komponenten dasselbe authentifizierte „ChannelSet“-Objekt verwenden, werden bei Aufruf der `logout`-Methode alle Komponenten bei den Zielen abgemeldet.

Im folgenden Beispiel werden die Methoden `ChannelSet.login` und `ChannelSet.logout` mit einem „RemoteObject“-Steuerelement verwendet. Diese Anwendung führt die folgenden Aktionen durch:

* Sie erstellt ein `ChannelSet`-Objekt im `creationComplete`-Handler, das die von der `RemoteObject`-Komponente verwendeten Kanäle angibt.
* Sie übergibt Anmeldeinformationen an den Server durch Aufruf der `ROLogin`-Funktion als Antwort auf ein Schaltflächen-Klickereignis
* Sie verwendet die „RemoteObject“-Komponente, um als Reaktion auf ein Schaltflächen-Klickereignis eine Zeichenfolge an den Server zu senden. Der Server gibt dieselbe Zeichenfolge an die „RemoteObject“-Komponente zurück.
* Sie verwendet das Ergebnisereignis der „RemoteObject“-Komponente, um die Zeichenfolge in einem „TextArea“-Steuerelement anzuzeigen.
* Sie meldet sich vom Server ab, indem die `ROLogout`-Funktion als Antwort auf ein Schaltflächen-Klickereignis aufgerufen wird.

```java
 <?xml version=”1.0”?>
 <!-- security/SecurityConstraintCustom.mxml -->
 <mx:Application xmlns:mx=”https://www.adobe.com/2006/mxml” width=”100%”
     height=”100%” creationComplete=”creationCompleteHandler();”>
 
     <mx:Script>
         <![CDATA[
             import mx.controls.Alert;
             import mx.messaging.config.ServerConfig;
             import mx.rpc.AsyncToken;
             import mx.rpc.AsyncResponder;
             import mx.rpc.events.FaultEvent;
             import mx.rpc.events.ResultEvent;
             import mx.messaging.ChannelSet;
 
             // Define a ChannelSet object.
             public var cs:ChannelSet;
 
             // Define an AsyncToken object.
             public var token:AsyncToken;
 
             // Initialize ChannelSet object based on the
             // destination of the RemoteObject component.
             private function creationCompleteHandler():void {
                 if (cs == null)
                 cs = ServerConfig.getChannelSet(remoteObject.destination);
             }
 
             // Login and handle authentication success or failure.
             private function ROLogin():void {
                 // Make sure that the user is not already logged in.
                 if (cs.authenticated == false) {
                     token = cs.login(“sampleuser”, “samplepassword”);
                     // Add result and fault handlers.
                     token.addResponder(new AsyncResponder(LoginResultEvent,
                     LoginFaultEvent));
                 }
             }
 
             // Handle successful login.
             private function LoginResultEvent(event:ResultEvent,
                 token:Object=null):void  {
                     switch(event.result) {
                         case “success”:
                             authenticatedCB.selected = true;
                             break;
                             default:
                     }
                 }
 
                 // Handle login failure.
                 private function LoginFaultEvent(event:FaultEvent,
                     token:Object=null):void {
                         switch(event.fault.faultCode) {
                             case “Client.Authentication”:
                                 default:
                                 authenticatedCB.selected = false;
                                 Alert.show(“Login failure: “ + event.fault.faultString);
                     }
                 }
 
                 // Logout and handle success or failure.
                 private function ROLogout():void {
                     // Add result and fault handlers.
                     token = cs.logout();
                     token.addResponder(new
                         AsyncResponder(LogoutResultEvent,LogoutFaultEvent));
                 }
 
                 // Handle successful logout.
                 private function LogoutResultEvent(event:ResultEvent,
                     token:Object=null):void {
                         switch (event.result) {
                             case “success”:
                                 authenticatedCB.selected = false;
                                 break;
                                 default:
                     }
                 }
 
                 // Handle logout failure.
                 private function LogoutFaultEvent(event:FaultEvent,
                     token:Object=null):void {
                         Alert.show(“Logout failure: “ + event.fault.faultString);
                 }
                 // Handle message recevied by RemoteObject component.
                 private function resultHandler(event:ResultEvent):void {
                     ta.text += “Server responded: “+ event.result + “\n”;
                 }
 
                 // Handle fault from RemoteObject component.
                 private function faultHandler(event:FaultEvent):void {
                     ta.text += “Received fault: “ + event.fault + “\n”;
                 }
             ]]>
     </mx:Script>
     <mx:HBox>
         <mx:Label text=”Enter a text for the server to echo”/>
         <mx:TextInput id=”ti” text=”Hello World!”/>
         <mx:Button label=”Login”
             click=”ROLogin();”/>
         <mx:Button label=”Echo”
             enabled=”{authenticatedCB.selected}”
             click=”remoteObject.echo(ti.text);”/>
         <mx:Button label=”Logout”
             click=”ROLogout();”/>
         <mx:CheckBox id=”authenticatedCB”
             label=”Authenticated?”
             enabled=”false”/>
     </mx:HBox>
     <mx:TextArea id=”ta” width=”100%” height=”100%”/>
 
     <mx:RemoteObject id=”remoteObject”
         destination=”myDest”
         result=”resultHandler(event);”
         fault=”faultHandler(event);”/>
 </mx:Application>
```

Die Methoden `login` und `logout` geben ein „AsyncToken“-Objekt zurück. Weisen Sie dem „AsyncToken“-Objekt Ereignis-Handler für das Ergebnisereignis zur Verarbeitung eines erfolgreichen Aufrufs und für das Fehlerereignis zur Verarbeitung eines Fehlers zu.

### Verwenden von Single Sign-on {#using-single-sign-on}

Benutzer von AEM Forms können eine Verbindung zu mehreren AEM Forms-Web-Anwendungen herstellen, um eine Aufgabe auszuführen. Da Benutzer von einer Web-Anwendung zur anderen wechseln, ist es nicht effizient, von ihnen die separate Anmeldung bei jeder Web-Anwendung zu verlangen. Mit dem Single-Sign-On-Mechanismus von AEM Forms können Benutzer sich einmal anmelden und dann auf alle AEM Forms-Web-Anwendungen zugreifen. Da die Entwickler von AEM Forms Client-Anwendungen für die Verwendung mit AEM Forms erstellen können, müssen auch sie den Single-Sign-On-Mechanismus nutzen können.

Jede AEM Forms-Web-Anwendung ist in einer eigenen Web-Archiv-Datei (WAR) gepackt, die dann Teil einer EAR-Paketdatei (Enterprise Archive) wird. Da ein Anwendungs-Server die Freigabe von Sitzungsdaten über verschiedene Web-Anwendungen hinweg nicht zulässt, verwendet AEM Forms HTTP-Cookies, um Authentifizierungsinformationen zu speichern. Authentifizierungs-Cookies ermöglichen es einem Benutzer, sich bei einer Forms-Anwendung anzumelden und dann eine Verbindung zu anderen AEM Forms-Web-Anwendungen herzustellen. Diese Technik wird als Single Sign-on bezeichnet.

Entwickler von AEM Forms schreiben Client-Anwendungen, um die Funktionalität von Formularleitfäden (nicht mehr unterstützt) zu erweitern und Workspace anzupassen. Beispielsweise kann eine Workspace-Anwendung einen Prozess starten. Die Client-Anwendung verwendet dann einen Remoting-Endpunkt, um Daten vom Forms-Services abzurufen.

Wenn ein AEM Forms-Service mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms) aufgerufen wird, übergibt die Client-Anwendung das Authentifizierungs-Cookie als Teil der Anfrage. Da der Benutzer sich bereits authentifiziert hat, ist keine zusätzliche Anmeldung erforderlich, um eine Verbindung zwischen der Client-Anwendung und dem AEM Forms-Service herzustellen.

>[!NOTE]
>Wenn ein Cookie ungültig ist oder fehlt, gibt es keine implizite Umleitung zu einer Anmeldeseite. Daher können Sie weiterhin einen anonymen Service aufrufen.

Sie können den Single-Sign-On-Mechanismus von AEM Forms umgehen, indem Sie eine Client-Anwendung schreiben, die sich selbst an- und abmeldet. Wenn Sie den Single-Sign-On-Mechanismus umgehen, können Sie mit Ihrer Anwendung entweder eine einfache oder eine benutzerdefinierte Authentifizierung verwenden.

Da dieser Mechanismus nicht den AEM Forms-Single-Sign-On-Mechanismus verwendet, wird kein Authentifizierungs-Cookie in den Client geschrieben. Die Anmeldedaten werden im `ChannelSet`-Objekt für den Remoting-Kanal gepeichert. Daher erfolgen alle `RemoteObject` -Aufrufe, die Sie über dasselbe `ChannelSet` ausführen, im Kontext dieser Anmeldeinformationen.

### Einrichten von Single Sign-on in AEM Forms {#setting-up-single-sign-on-in-aem-forms}

Um Single Sign-on in AEM Forms zu verwenden, installieren Sie die Workflow-Komponente für Formulare, die den zentralen Anmelde-Service enthält. Nachdem sich ein Benutzer erfolgreich angemeldet hat, gibt der zentrale Anmelde-Service dem Benutzer ein Authentifizierungscookie zurück. Jede nachfolgende Anforderung an eine Forms-Webanwendung enthält das Cookie. Wenn das Cookie gültig ist, gilt der Benutzer als authentifiziert und muss sich nicht erneut anmelden.

### Schreiben einer Client-Anwendung, die Single Sign-on verwendet {#writing-a-client-application-that-uses-single-sign-on}

Bei Verwendung des Single-Sign-On-Mechanismus wird erwartet, dass sich Benutzer mit dem zentralen Anmelde-Service anmelden, bevor sie eine Client-Anwendung starten. Das heißt, eine Client-Anwendung meldet sich nicht über den Browser oder durch Aufrufen der `ChannelSet.login`-Methode an.

Wenn Sie den AEM Forms-Single-Sign-On-Mechanismus verwenden, konfigurieren Sie den Remoting-Endpunkt so, dass er eine benutzerdefinierte Authentifizierung verwendet statt der Standardauthentifizierung. Andernfalls führt ein Authentifizierungsfehler bei Verwendung der Standardauthentifizierung zu einer Browserabfrage, die der Benutzer nicht sehen sollte. Stattdessen erkennt die Anwendung den Authentifizierungsfehler und zeigt dann eine Meldung an, die den Benutzer anweist, sich mit dem zentralen Anmelde-Service anzumelden.

Eine Client-Anwendung greift über einen Remoting-Endpunkt auf AEM Forms zu, indem sie die `RemoteObject`-Komponente verwendet, wie im folgenden Beispiel gezeigt.

```java
 <?xml version="1.0"?>
 <mx:Application
        backgroundColor="#FFFFFF">
 
       <mx:Script>
          <![CDATA[
 
            import mx.controls.Alert;
            import mx.rpc.events.FaultEvent;
 
            // Prompt user to login on a fault.
            private function faultHandler(event:FaultEvent):void
            {
             if(event.fault.faultCode=="Client.Authentication")
             {
                 Alert.show(
                     event.fault.faultString + "\n" +
                     event.fault.faultCode + "\n" +
                     "Please login to continue.");
             }
         }
          ]]>
       </mx:Script>
 
       <mx:RemoteObject id="srv"
           destination="product"
           fault="faultHandler(event);"/>
 
       <mx:DataGrid
           width="100%" height="100%"
           dataProvider="{srv.getProducts.lastResult}"/>
 
       <mx:Button label="Get Data"
           click="srv.getProducts();"/>
 
 </mx:Application>
```

**Anmelden als neuer Benutzer während der Ausführung der Flex-Anwendung**

Eine mit Flex erstellte Anwendung bindet das Authentifizierungs-Cookie bei jeder Anfrage an einen AEM Forms-Service ein. Aus Leistungsgründen überprüft AEM Forms das Cookie nicht bei jeder Anforderung. AEM Forms erkennt jedoch, wenn ein Authentifizierungs-Cookie durch ein anderes Authentifizierungs-Cookie ersetzt wird.

Sie starten beispielsweise eine Client-Anwendung und während die Anwendung aktiv ist, verwenden Sie den zentralisierten Anmelde-Service, um sich abzumelden. Anschließend können Sie sich als ein anderer Benutzer anmelden. Bei der Anmeldung als anderer Benutzer wird das vorhandene Authentifizierungs-Cookie durch ein Authentifizierungs-Cookie für den neuen Benutzer ersetzt.

Bei der nächsten Anfrage der Client-Anwendung erkennt AEM Forms, dass sich das Cookie geändert hat, und meldet den Benutzer ab. Daher schlägt die erste Anforderung nach einer Cookie-Änderung fehl. Alle nachfolgenden Anfragen werden im Kontext des neuen Cookies gestellt und sind erfolgreich.

**Abmelden**

Um sich von AEM Forms abzumelden und eine Sitzung ungültig zu machen, muss das Authentifizierungs-Cookie vom Computer des Clients gelöscht werden. Da Single Sign-On dazu dient, einem Benutzer das einmalige Anmelden zu ermöglichen, sollte eine Client-Anwendung das Cookie nicht löschen. Mit dieser Aktion wird der Benutzer effektiv abgemeldet.

Daher wird durch den Aufruf der `RemoteObject.logout`-Methode in einer Client-Anwendung eine Fehlermeldung auf dem Client generiert, die angibt, dass die Sitzung nicht abgemeldet wird. Stattdessen kann der Benutzer den zentralen Anmelde-Service verwenden, um sich abzumelden und das Authentifizierungs-Cookie zu löschen.

**Abmelden, während die Flex-Anwendung noch ausgeführt wird**

Sie können eine mit Flex erstellte Client-Anwendung starten und den zentralen Anmelde-Service verwenden, um sich abzumelden. Im Rahmen des Abmeldevorgangs wird das Authentifizierungs-Cookie gelöscht. Wenn eine Remoting-Anforderung ohne Cookie oder mit einem ungültigen Cookie erfolgt, wird die Benutzersitzung ungültig. Diese Aktion ist im Endeffekt eine Abmeldung. Wenn die Client-Anwendung das nächste Mal versucht, eine Verbindung zu einem AEM Forms-Service herzustellen, wird der Benutzer aufgefordert, sich anzumelden.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Umgang mit Dokumenten mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms)](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Einschließen der AEM Forms Flex-Bibliotheksdatei](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)

## Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting {#passing-secure-documents-to-invoke-processes-using-remoting}

Sie können sichere Dokumente an AEM Forms übergeben, wenn Sie einen Prozess aufrufen, für den ein oder mehrere Dokumente erforderlich sind. Durch Übergabe eines sicheren Dokuments schützen Sie Geschäftsinformationen und vertrauliche Dokumente. In diesem Fall kann ein Dokument auf ein PDF-Dokument, ein XML-Dokument, ein Word-Dokument usw. verweisen. Die Übergabe eines sicheren Dokuments von einer in Flex geschriebenen Client-Anwendung an AEM Forms ist erforderlich, wenn AEM Forms für sichere Dokumente konfiguriert ist. (Weitere Informationen finden Sie unter [Konfigurieren von AEM Forms zum Akzeptieren sicherer und unsicherer Dokumente](invoking-aem-forms-using-remoting.md#configuring-aem-forms-to-accept-secure-and-unsecure-documents).)

Verwenden Sie beim Übergeben eines sicheren Dokuments Single Sign-On und geben Sie einen AEM Forms-Benutzer an, der über die Rolle *Document Upload Application User* verfügt. Ohne diese Rolle kann der Benutzer kein sicheres Dokument hochladen. Sie können Benutzern programmgesteuert eine Rolle zuweisen. (Weitere Informationen finden Sie unter [Verwalten von Rollen und Berechtigungen](/help/forms/developing/users.md#managing-roles-and-permissions).)

>[!NOTE]
>Wenn Sie eine neue Rolle erstellen und Mitglieder dieser Rolle sichere Dokumente hochladen sollen, vergewissern Sie sich, dass Sie die Berechtigung zum Hochladen von Dokumenten angeben.

AEM Forms unterstützt einen Vorgang mit dem Namen `getFileUploadToken`, der ein Token zurückgibt, das an das Upload-Servlet übergeben wird. Die `DocumentReference.constructRequestForUpload`-Methode benötigt eine URL zu AEM Forms zusammen mit dem Token, das von der `LC.FileUploadAuthenticator.getFileUploadToken`-Methode zurückgegeben wird. Diese Methode gibt ein `URLRequest`-Objekt zurück, das beim Aufruf des Upload-Servlets verwendet wird. Der folgende Code veranschaulicht diese Anwendungslogik.

```java
     ...
         private function startUpload():void
         {
             fileRef.addEventListener(Event.SELECT, selectHandler);
             fileRef.addEventListener("uploadCompleteData", completeHandler);
             try
             {
         var success:Boolean = fileRef.browse();
             }
             catch (error:Error)
             {
                 trace("Unable to browse for files.");
             }
 
         }
 
          private function selectHandler(event:Event):void
             {
             var authTokenService:RemoteObject = new RemoteObject("LC.FileUploadAuthenticator");
             authTokenService.addEventListener("result", authTokenReceived);
             authTokenService.channelSet = cs;
             authTokenService.getFileUploadToken();
             }
 
         private function authTokenReceived(event:ResultEvent):void
             {
             var token:String = event.result as String;
             var request:URLRequest = DocumentReference.constructRequestForUpload("http://localhost:8080", token);
 
             try
             {
           fileRef.upload(request);
             }
             catch (error:Error)
             {
             trace("Unable to upload file.");
             }
             }
 
         private function completeHandler(event:DataEvent):void
         {
 
             var params:Object = new Object();
             var docRef:DocumentReference = new DocumentReference();
             docRef.url = event.data as String;
             docRef.referenceType = DocumentReference.REF_TYPE_URL;
         }
         ...
```

)

### Konfigurieren von AEM Forms zum Akzeptieren sicherer und unsicherer Dokumente {#configuring-aem-forms-to-accept-secure-and-unsecure-documents}

Mit Administration-Console können Sie, wenn Sie ein Dokument von einer Flex-Clientanwendung an einen AEM Forms-Prozess übergeben, angeben, ob Dokumente sicher sind. Standardmäßig ist AEM Forms so konfiguriert, dass sichere Dokumente akzeptiert werden. Gehen Sie wie folgt vor, um AEM Forms so zu konfigurieren, dass sichere Dokumente akzeptiert werden:

1. Melden Sie sich bei Administration Console an.
1. Klicken Sie auf **Einstellungen**.
1. Klicken Sie auf **Zentrale Systemeinstellungen.**
1. Klicken Sie auf Konfigurationen.
1. Vergewissern Sie sich, dass die Option „Upload unsicherer Dokumente aus Flex-Anwendungen zulassen“ nicht aktiviert ist.

>[!NOTE]
>Um AEM Forms so zu konfigurieren, dass unsichere Dokumente akzeptiert werden, wählen Sie die Option „Upload unsicherer Dokumente aus Flex-Anwendungen zulassen“ aus. Starten Sie dann eine Anwendung oder einen Service neu, um sicherzustellen, dass die Einstellung wirksam wird.

### Schnellstart: Aufrufen eines kurzlebigen Prozesses durch Übergeben eines sicheren Dokuments mithilfe von Remoting {#quick-start-invoking-a-short-lived-process-by-passing-a-secure-document-using-remoting}

Das folgende Codebeispiel ruft `MyApplication/EncryptDocument.`„Ein Benutzer muss sich anmelden, um auf den Button &#39;Datei auswählen&#39; zu klicken, der zum Hochladen einer PDF-Datei und zum Aufrufen des Prozesses verwendet wird“ auf. Das heißt, nach der Authentifizierung des Benutzers ist der Button „Datei auswählen“ aktiviert. Die folgende Abbildung zeigt die Flex-Clientanwendung, nachdem ein Benutzer authentifiziert wurde. Beachten Sie, dass das Kontrollkästchen „Authentifiziert“ aktiviert ist.

![iu_iu_secureremotelogin](assets/iu_iu_secureremotelogin.png)

Wenn AEM Forms so konfiguriert ist, dass nur sichere Dokumente hochgeladen werden können und der Benutzer nicht die Rolle *Dokumenten-Upload-Anwendungsbenutzer* hat, wird eine Ausnahme ausgelöst. Wenn der Benutzer über diese Rolle verfügt, wird die Datei hochgeladen und der Prozess aufgerufen.

```java
 <?xml version="1.0" encoding="utf-8"?>
 <mx:Application  xmlns="*"
      creationComplete="initializeChannelSet();">
        <mx:Script>
        <![CDATA[
      import mx.rpc.livecycle.DocumentReference;
      import flash.net.FileReference;
      import flash.net.URLRequest;
      import flash.events.Event;
      import flash.events.DataEvent;
      import mx.messaging.ChannelSet;
      import mx.messaging.channels.AMFChannel;
      import mx.rpc.events.ResultEvent;
      import mx.collections.ArrayCollection;
      import mx.rpc.AsyncToken;
      import mx.controls.Alert;
      import mx.rpc.events.FaultEvent;
      import mx.rpc.AsyncResponder;
 
      // Classes used in file retrieval
      private var fileRef:FileReference = new FileReference();
      private var docRef:DocumentReference = new DocumentReference();
      private var parentResourcePath:String = "/";
      private var now1:Date;
      private var serverPort:String = "hiro-xp:8080";
 
      // Define a ChannelSet object.
      public var cs:ChannelSet;
 
      // Define an AsyncToken object.
      public var token:AsyncToken;
 
       // Holds information returned from AEM Forms
      [Bindable]
      public var progressList:ArrayCollection = new ArrayCollection();
 
 
      // Handles a successful login
     private function LoginResultEvent(event:ResultEvent,
         token:Object=null):void  {
             switch(event.result) {
                 case "success":
                     authenticatedCB.selected = true;
                     btnFile.enabled = true;
                     btnLogout.enabled = true;
                     btnLogin.enabled = false;
                         break;
                     default:
                 }
             }
 
 
 // Handle login failure.
 private function LoginFaultEvent(event:FaultEvent,
     token:Object=null):void {
     switch(event.fault.faultCode) {
                 case "Client.Authentication":
                         default:
                         authenticatedCB.selected = false;
                         Alert.show("Login failure: " + event.fault.faultString);
                 }
             }
 
 
      // Set up channel set to invoke AEM Forms
      private function initializeChannelSet():void {
        cs = new ChannelSet();
        cs.addChannel(new AMFChannel("remoting-amf", "https://" + serverPort + "/remoting/messagebroker/amf"));
        EncryptDocument2.channelSet = cs;
      }
 
     // Call this method to upload the file.
      // This creates a file picker and lets the user select a PDF file to pass to the EncryptDocument process.
      private function uploadFile():void {
        fileRef.addEventListener(Event.SELECT, selectHandler);
        fileRef.addEventListener(DataEvent.UPLOAD_COMPLETE_DATA,completeHandler);
        fileRef.browse();
      }
 
      // Gets called for selected file. Does the actual upload via the file upload servlet.
      private function selectHandler(event:Event):void {
              var authTokenService:RemoteObject = new RemoteObject("LC.FileUploadAuthenticator");
         authTokenService.addEventListener("result", authTokenReceived);
         authTokenService.channelSet = cs;
         authTokenService.getFileUploadToken();
      }
 
     private function authTokenReceived(event:ResultEvent):void
     {
     var token:String = event.result as String;
     var request:URLRequest = DocumentReference.constructRequestForUpload("https://hiro-xp:8080", token);
 
     try
     {
           fileRef.upload(request);
     }
     catch (error:Error)
     {
         trace("Unable to upload file.");
     }
 }
 
      // Called once the file is completely uploaded.
      private function completeHandler(event:DataEvent):void {
 
        // Set the docRef’s url and referenceType parameters
        docRef.url = event.data as String;
        docRef.referenceType=DocumentReference.REF_TYPE_URL;
        executeInvokeProcess();
      }
 
     //This method invokes the EncryptDocument process
      public function executeInvokeProcess():void {
         //Create an Object to store the input value for the EncryptDocument process
           now1 = new Date();
 
         var params:Object = new Object();
         params["inDoc"]=docRef;
 
         // Invoke the EncryptDocument process
         var token:AsyncToken;
         token = EncryptDocument2.invoke(params);
         token.name = name;
      }
 
      // AEM Forms  login method
      private function ROLogin():void {
         // Make sure that the user is not already logged in.
 
         //Get the User and Password
         var userName:String = txtUser.text;
         var pass:String = txtPassword.text;
 
        if (cs.authenticated == false) {
             token = cs.login(userName, pass);
 
         // Add result and fault handlers.
         token.addResponder(new AsyncResponder(LoginResultEvent,    LoginFaultEvent));
                 }
             }
 
      // This method handles a successful process invocation
      public function handleResult(event:ResultEvent):void
      {
            //Retrieve information returned from the service invocation
          var token:AsyncToken = event.token;
          var res:Object = event.result;
          var dr:DocumentReference = res["outDoc"] as DocumentReference;
          var now2:Date = new Date();
 
           // These fields map to columns in the DataGrid
          var progObject:Object = new Object();
          progObject.filename = token.name;
          progObject.timing = (now2.time - now1.time).toString();
          progObject.state = "Success";
          progObject.link = "<a href='" + dr.url + "'> open </a>";
          progressList.addItem(progObject);
      }
 
      // Prompt user to login on a fault.
       private function faultHandler(event:FaultEvent):void
            {
             if(event.fault.faultCode=="Client.Authentication")
             {
                 Alert.show(
                     event.fault.faultString + "\n" +
                     event.fault.faultCode + "\n" +
                     "Please login to continue.");
             }
            }
 
       // AEM Forms  logout method
     private function ROLogout():void {
         // Add result and fault handlers.
         token = cs.logout();
         token.addResponder(new AsyncResponder(LogoutResultEvent,LogoutFaultEvent));
     }
 
     // Handle successful logout.
     private function LogoutResultEvent(event:ResultEvent,
         token:Object=null):void {
         switch (event.result) {
         case "success":
                 authenticatedCB.selected = false;
                 btnFile.enabled = false;
                 btnLogout.enabled = false;
                 btnLogin.enabled = true;
                 break;
                 default:
             }
     }
 
     // Handle logout failure.
     private function LogoutFaultEvent(event:FaultEvent,
             token:Object=null):void {
             Alert.show("Logout failure: " + event.fault.faultString);
     }
 
          private function resultHandler(event:ResultEvent):void {
          // Do anything else here.
          }
        ]]>
 
      </mx:Script>
      <mx:RemoteObject id="EncryptDocument" destination="MyApplication/EncryptDocument" result="resultHandler(event);">
          <mx:method name="invoke" result="handleResult(event)"/>
      </mx:RemoteObject>
 
       <!--//This consists of what is displayed on the webpage-->
      <mx:Panel id="lcPanel" title="EncryptDocument  (Deprecated for AEM forms) AEM Forms Remoting Example"
           height="25%" width="25%" paddingTop="10" paddingLeft="10" paddingRight="10"
           paddingBottom="10">
         <mx:Label width="100%" color="blue"
                text="Select a PDF file to pass to the EncryptDocument process"/>
        <mx:DataGrid x="10" y="0" width="500" id="idProgress" editable="false"
           dataProvider="{progressList}" height="231" selectable="false" >
          <mx:columns>
            <mx:DataGridColumn headerText="Filename" width="200" dataField="filename" editable="false"/>
            <mx:DataGridColumn headerText="State" width="75" dataField="state" editable="false"/>
            <mx:DataGridColumn headerText="Timing" width="75" dataField="timing" editable="false"/>
            <mx:DataGridColumn headerText="Click to Open" dataField="link" editable="false" >
             <mx:itemRenderer>
                <mx:Component>
                   <mx:Text x="0" y="0" width="100%" htmlText="{data.link}"/>
                </mx:Component>
             </mx:itemRenderer>
            </mx:DataGridColumn>
          </mx:columns>
        </mx:DataGrid>
        <mx:Button label="Select File" click="uploadFile()"  id="btnFile" enabled="false"/>
        <mx:Button label="Login" click="ROLogin();" id="btnLogin"/>
        <mx:Button label="LogOut" click="ROLogout();" enabled="false" id="btnLogout"/>
        <mx:HBox>
         <mx:Label text="User:"/>
         <mx:TextInput id="txtUser" text=""/>
         <mx:Label text="Password:"/>
         <mx:TextInput id="txtPassword" text="" displayAsPassword="true"/>
         <mx:CheckBox id="authenticatedCB"
             label="Authenticated?"
             enabled="false"/>
     </mx:HBox>
      </mx:Panel>
 </mx:Application>
```

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Umgang mit Dokumenten mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms)](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Einschließen der AEM Forms Flex-Bibliotheksdatei](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Authentifizieren von mit Flex erstellten Client-Anwendungen](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

## Aufrufen benutzerdefinierter Komponenten-Services mithilfe von Remoting {#invoking-custom-component-services-using-remoting}

Sie können Services aufrufen, die sich in einer benutzerdefinierten Komponente befinden, indem Sie Remoting verwenden. Nehmen wir zum Beispiel die Komponente „Bank“, die den Kundendienst enthält. Sie können Vorgänge, die zum Kundendienst gehören, mithilfe einer in Flex geschriebenen Clientanwendung aufrufen. Bevor Sie den Schnellstart für diesen Abschnitt ausführen können, müssen Sie die benutzerdefinierte Komponente „Bank“ erstellen.

Der Kundendienst stellt einen Vorgang mit dem Namen `createCustomer` zur Verfügung. In dieser Diskussion wird beschrieben, wie Sie eine Flex-Clientanwendung erstellen, die den Kundendienst aufruft und einen Kunden erstellt. Dieser Vorgang erfordert ein komplexes Objekt vom Typ `com.adobe.livecycle.sample.customer.Customer` das den neuen Kunden darstellt. Die folgende Abbildung zeigt die Client-Anwendung, die den Kundendienst aufruft und einen neuen Kunden erstellt. Der `createCustomer`-Vorgang gibt einen Wert für die Kundenkennung zurück. Der Wert der Kennung wird im Textfeld „Kundenkennung“ angezeigt.

![iu_iu_flexnewcust](assets/iu_iu_flexnewcust.png)

In der folgenden Tabelle sind die Steuerelemente aufgeführt, die Teil dieser Client-Anwendung sind.

<table>
 <thead>
  <tr>
   <th><p>Name des Steuerelements</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>txtFirst</p></td>
   <td><p>Gibt den Vornamen des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>txtLast</p></td>
   <td><p>Gibt den Nachnamen des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>txtPhone</p></td>
   <td><p>Gibt die Telefonnummer des Kunden an.</p></td>
  </tr>
  <tr>
   <td><p>txtStreet</p></td>
   <td><p>Gibt den Straßennamen des Kunden an.</p></td>
  </tr>
  <tr>
   <td><p>txtState</p></td>
   <td><p>Gibt den Bundesstaat des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>txtZIP</p></td>
   <td><p>Gibt die Postleitzahl des Kunden an. </p></td>
  </tr>
  <tr>
   <td><p>txtCity</p></td>
   <td><p>Gibt den Ort des Kunden an.</p></td>
  </tr>
  <tr>
   <td><p>txtCustId</p></td>
   <td><p>Gibt den ID-Wert des Kunden an, zu dem das neue Konto gehört. Dieses Textfeld wird durch den Rückgabewert des Vorgangs <code>createCustomer</code> des Kundendienstes ausgefüllt. </p></td>
  </tr>
 </tbody>
</table>

### Zuordnen komplexer AEM Forms-Datentypen {#mapping-aem-forms-complex-data-types}

Einige AEM Forms-Vorgänge erfordern komplexe Datentypen als Eingabewerte. Diese komplexen Datentypen definieren die vom Vorgang verwendeten Laufzeitwerte. Der Vorgang `createCustomer` des Kundendienstes erfordert beispielsweise eine `Customer`-Instanz, die die vom Service benötigten Laufzeitwerte enthält. Ohne komplexen Typ gibt der Kundendienst eine Ausnahme aus und führt den Vorgang nicht aus.

Erstellen Sie beim Aufrufen eines AEM Forms-Services ActionScript-Objekte, die den erforderlichen komplexen AEM Forms-Typen zugeordnet sind. Erstellen Sie für jeden komplexen Datentyp, den ein Vorgang erfordert, ein separates ActionScript-Objekt.

Verwenden Sie in der ActionScript-Klasse das Metadaten-Tag `RemoteClass`, das dem komplexen AEM Forms-Typ zugeordnet werden soll. Wenn Sie z. B. den `createCustomer`-Vorgang des Kundendienstes aufrufen, erstellen Sie eine ActionScript-Klasse, die dem Datentyp `com.adobe.livecycle.sample.customer.Customer` zugeordnet ist.

Die folgende ActionScript-Klasse namens „Kunde“ zeigt, wie sie dem AEM Forms-Datentyp `com.adobe.livecycle.sample.customer.Customer` zugeordnet wird.

```java
 package customer
 
 {
     [RemoteClass(alias="com.adobe.livecycle.sample.customer.Customer")]
     public class Customer
     {
            public var name:String;
            public var street:String;
            public var city:String;
            public var state:String;
            public var phone:String;
            public var zip:int;
        }
 }
```

Der vollständig qualifizierte Datentyp des komplexen AEM Forms-Typs wird dem Alias-Tag zugewiesen.

Die Felder der ActionScript-Klasse entsprechen den Feldern, die zum komplexen AEM Forms-Typ gehören. Die sechs Felder in der Customer ActionScript-Klasse stimmen mit den Feldern überein, die zu `com.adobe.livecycle.sample.customer.Customer` gehören.

>[!NOTE]
>Eine gute Möglichkeit, die Feldnamen zu einem komplexen Forms-Typ zu ermitteln, besteht darin, die WSDL eines Services in einem Webbrowser anzuzeigen. Eine WSDL gibt die komplexen Typen eines Services und die entsprechenden Datenelemente an. Die folgende WSDL wird für den Kundendienst verwendet: `https://[yourServer]:[yourPort]/soap/services/CustomerService?wsdl.`

Die ActionScript-Klasse „Kunde“ gehört zu einem Paket namens „Kunde“. Es wird empfohlen, alle ActionScript-Klassen, die komplexen AEM Forms-Datentypen zugeordnet sind, in ihrem eigenen Paket zu platzieren. Erstellen Sie einen Ordner im src-Ordner des Flex-Projekts und legen Sie die ActionScript-Datei im Ordner ab, wie in der folgenden Abbildung dargestellt.

![iu_iu_customeras](assets/iu_iu_customeras.png)

### Kurzanleitung: Aufrufen des benutzerdefinierten Kundendienstes mithilfe von Remoting {#quick-start-invoking-the-customer-custom-service-using-remoting}

Im folgenden Beispiel-Code wird der Kundendienst aufgerufen und ein neuer Kunde erstellt. Wenn Sie diesen Beispiel-Code ausführen, stellen Sie sicher, dass Sie alle Textfelder ausfüllen. Stellen Sie außerdem sicher, dass Sie die Datei „Customer.as“ erstellen, die `com.adobe.livecycle.sample.customer.Customer` entspricht.

>[!NOTE]
>Bevor Sie diese Kurzanleitung ausführen können, müssen Sie die benutzerdefinierte Bank-Komponente erstellen und bereitstellen.

```java
 <?xml version="1.0" encoding="utf-8"?>
 <mx:Application  layout="absolute" backgroundColor="#B1ABAB">
 
 <mx:Script>
            <![CDATA[
 
      import flash.net.FileReference;
      import flash.net.URLRequest;
      import flash.events.Event;
      import flash.events.DataEvent;
      import mx.messaging.ChannelSet;
      import mx.messaging.channels.AMFChannel;
      import mx.rpc.events.ResultEvent;
      import mx.collections.ArrayCollection;
      import mx.rpc.AsyncToken;
      import mx.managers.CursorManager;
      import mx.rpc.remoting.mxml.RemoteObject;
 
 
      // Custom class that corresponds to an input to the
      // AEM Forms encryption method
      import customer.Customer;
 
      // Classes used in file retrieval
      private var fileRef:FileReference = new FileReference();
      private var parentResourcePath:String = "/";
      private var serverPort:String = "hiro-xp:8080";
      private var now1:Date;
      private var fileName:String;
 
      // Prepares parameters for encryptPDFUsingPassword method call
      public function executeCreateCustomer():void
      {
 
        var cs:ChannelSet= new ChannelSet();
     cs.addChannel(new AMFChannel("remoting-amf", "https://" + serverPort + "/remoting/messagebroker/amf"));
 
     customerService.setCredentials("administrator", "password");
     customerService.channelSet = cs;
 
     //Create a Customer object required to invoke the Customer service's
     //createCustomer operation
     var myCust:Customer = new Customer();
 
     //Get values from the user of the Flex application
     var fullName:String = txtFirst.text +" "+txtLast.text ;
     var Phone:String = txtPhone.text;
     var Street:String = txtStreet.text;
     var State:String = txtState.text;
     var Zip:int = parseInt(txtZIP.text);
     var City:String = txtCity.text;
 
     //Populate Customer fields
     myCust.name = fullName;
     myCust.phone = Phone;
     myCust.street= Street;
     myCust.state= State;
     myCust.zip = Zip;
     myCust.city = City;
 
     //Invoke the Customer service's createCustomer operation
     var params:Object = new Object();
        params["inCustomer"]=myCust;
     var token:AsyncToken;
        token = customerService.createCustomer(params);
        token.name = name;
      }
 
      private function handleResult(event:ResultEvent):void
      {
          // Retrieve the information returned from the service invocation
          var token:AsyncToken = event.token;
          var res:Object = event.result;
          var custId:String = res["CustomerId"] as String;
 
          //Assign to the custId to the text box
          txtCustId.text = custId;
      }
 
 
      private function resultHandler(event:ResultEvent):void
      {
 
      }
            ]]>
 </mx:Script>
 <mx:RemoteObject id="customerService" destination="CustomerService" result="resultHandler(event);">
 <mx:method name="createCustomer" result="handleResult(event)"/>
 </mx:RemoteObject>
 
 
 <mx:Style source="../bank.css"/>
     <mx:Grid>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="New Customer" fontSize="16" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="First Name:" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtFirst"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:Button label="Create Customer" id="btnCreateCustomer" click="executeCreateCustomer()"/>
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Last Name" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtLast"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Phone" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtPhone"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Street" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtStreet"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="State" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtState"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="ZIP" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtZIP"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="City" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtCity"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                             <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Customer Identifier" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtCustId" editable="false"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                 </mx:Grid>
 </mx:Application>
 
```

**Formatvorlage**

Diese Kurzanleitung enthält eine Formatvorlage mit dem Namen *bank.css*. Der folgende Code stellt die verwendete Formatvorlage dar.

```css
 /* CSS file */
 global
 {
          backgroundGradientAlphas: 1.0, 1.0;
          backgroundGradientColors: #525152,#525152;
          borderColor: #424444;
          verticalAlign: middle;
          color: #FFFFFF;
          font-size:12;
          font-weight:normal;
 }
 
 ApplicationControlBar
 {
          fillAlphas: 1.0, 1.0;
          fillColors: #393839, #393839;
 }
 
 .textField
 {
          backgroundColor: #393839;
          background-disabled-color: #636563;
 }
 
 
 .button
 {
          fillColors: #636563, #424242;
 }
 
 .dropdownMenu
 {
          backgroundColor: #DDDDDD;
          fillColors: #636563, #393839;
          alternatingItemColors: #888888, #999999;
 }
 
 .questionLabel
 {
 
 }
 
 ToolTip
 {
        backgroundColor: black;
        backgroundAlpha: 1.0;
        cornerRadius: 0;
        color: white;
 }
 
 DateChooser
 {
        cornerRadius: 0; /* pixels */
        headerColors: black, black;
        borderColor: black;
        themeColor: black;
        todayColor: red;
        todayStyleName: myTodayStyleName;
        headerStyleName: myHeaderStyleName;
        weekDayStyleName: myWeekDayStyleName;
        dropShadowEnabled: true;
 }
 
 .myTodayStyleName
 {
        color: white;
 }
 
 .myWeekDayStyleName
 {
        fontWeight: normal;
 }
 
 .myHeaderStyleName
 {
        color: red;
        fontSize: 16;
        fontWeight: bold;
 }
```

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Umgang mit Dokumenten mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms)](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Einschließen der AEM Forms Flex-Bibliotheksdatei](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Authentifizieren von mit Flex erstellten Client-Anwendungen](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

[Übergeben sicherer Dokumente zum Aufrufen von Prozessen mithilfe von Remoting](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)
