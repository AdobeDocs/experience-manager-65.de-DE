---
title: Arbeiten mit dem AEM Forms-Repository
description: Verwalten Sie das AEM Forms-Repository zum Erstellen von Ordnern, Schreiben, Auflisten, Lesen, Aktualisieren und Suchen von Ressourcen mithilfe der Java-API und der Webservice-API. Erfahren Sie außerdem, wie Sie Ressourcenbeziehungen erstellen und Ressourcen sperren oder löschen können.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: a07e51ca-fea0-4719-8071-1b7e805de2ae
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '9036'
ht-degree: 100%

---

# Arbeiten mit dem AEM Forms-Repository {#working-with-aem-forms-repository}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Repository-Service**

Der Repository-Service stellt Services für die Ressourcenspeicherung und -verwaltung in AEM Forms bereit. Wenn Entwickler ein *AEM Forms*-Programm erstellen, können sie die Elemente im Repository statt im Dateisystem bereitstellen. Die Elemente können alle Typen von Zusätzen umfassen, darunter XML-Formulare, PDF-Formulare (einschließlich Acrobat-Formularen), Formularfragmente, Bilder, Profile, Richtlinien, SWF-Dateien, DDX-Dateien, XML-Schemas, WSDL-Dateien und Testdaten.

Nehmen Sie zum Beispiel das folgende Forms-Programm mit dem Namen *Applications/FormsApplication*:

![ww_ww_formrepository](assets/ww_ww_formrepository.png)

Beachten Sie, dass sich im Ordner „FormsFolder“ eine Datei mit dem Namen „Loan.xdp“ befindet. Um auf diesen Formularentwurf zuzugreifen, geben Sie den vollständigen Pfad an (einschließlich der Version): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Informationen zum Erstellen eines Forms-Programms mit Workbench finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).

Der Pfad zu einer Ressource im AEM Forms-Repository lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Die folgenden Werte zeigen einige Beispiele für URI-Werte:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>Sie können das AEM Forms-Repository mithilfe eines Webbrowsers durchsuchen. Um das Repository zu durchsuchen, geben Sie die URL `https://[server name]:[server port]/repository` in einen Webbrowser ein. Sie können die Ergebnisse der Kurzanleitung, die mit dem Abschnitt „Arbeiten mit dem AEM Forms-Repository“ verbunden sind, mit einem Webbrowser überprüfen. Wenn Sie beispielsweise Inhalte zum AEM Forms-Repository hinzufügen, können Sie diese Inhalte in einem Webbrowser anzeigen. (Siehe [Kurzanleitung (SOAP-Modus): Schreiben einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).)

Die Repository-API bietet eine Reihe von Vorgängen, mit denen Sie Informationen aus dem Repository speichern und abrufen können. Beispielsweise können Sie eine Liste von Ressourcen oder spezifische Ressourcen abrufen, die im Repository gespeichert sind, wenn eine Ressource im Rahmen der Verarbeitung eines Programms benötigt wird.

>[!NOTE]
>
>Die Repository-API kann nicht für die Interaktion mit Content Services (veraltet) verwendet werden. Um mit Content Services (veraltet) zu interagieren, verwenden Sie die Document Management-API.

Mithilfe der Repository-Service-API können Sie die folgenden Aufgaben ausführen:

* Erstellen von Ordnern. Weitere Informationen finden Sie unter [Erstellen von Ordnern](aem-forms-repository.md#creating-folders).
* Schreiben Sie Ressourcen und ihre Eigenschaften. Siehe [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).
* Listen Sie Ressourcen in einer bestimmten Sammlung oder in Verbindung mit anderen Ressourcen auf. Siehe [Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).
* Lesen Sie Ressourcen und ihre Eigenschaften. Siehe [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).
* Aktualisieren Sie die Ressourcen und ihre Eigenschaften. Siehe [Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources).
* Suchen Sie nach Ressourcen, einschließlich ihres Verlaufs, verbundener Ressourcen und Eigenschaften. Siehe [Suchen nach Ressourcen](aem-forms-repository.md#searching-for-resources).
* Geben Sie Beziehungen zwischen Ressourcen an. Siehe [Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships).
* Verwalten Sie die Zugriffskontrolle für Ressourcen, einschließlich Sperren und Entsperren von Ressourcen sowie Lesen und Schreiben von Zugriffssteuerungslisten (ACLs). Siehe [Sperren von Ressourcen](aem-forms-repository.md#locking-resources).
* Löschen Sie Ressourcen und ihre Eigenschaften. Siehe [Löschen von Ressourcen](aem-forms-repository.md#deleting-resources).

>[!NOTE]
>
>Mithilfe der Repository-API können Sie nicht die Zugriffskontrolle auf Ressourcen verwalten, nach Ressourcen suchen oder mithilfe eines ECM-Repositorys Ressourcenbeziehungen angeben.

>[!NOTE]
>
>Wenn eine verschlüsselte PDF in das Repository geschrieben wird, kann die automatisierte Beziehungsextraktionsfunktion nicht verwendet werden. Ansonsten kann eine verschlüsselte PDF im Repository gespeichert und später abgerufen werden. Der Abrufende kann wählen, ob die PDF entschlüsselt werden soll, nachdem sie aus dem Repository abgerufen wurde.

>[!NOTE]
>
>Weitere Informationen zum Repository-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen eines Ordners {#creating-folders}

Ordner (Ressourcensammlungen) werden zum Speichern von Objekten (Dateien oder Ressourcen) in organisierten Gruppierungen verwendet. Ordner können Ressourcen und andere Ordner enthalten, die auch als Unterordner bezeichnet werden. Ressourcen können jeweils nur in einem Ordner gespeichert werden.

Dateien erben Zugriffssteuerungslisten (ACLs) aus Ordnern, und Unterordner erben ACLs von ihren übergeordneten Ordnern. Daher müssen die übergeordneten Ordner vorhanden sein, bevor Sie untergeordnete Ordner erstellen können. Die IDE ermöglicht die Interaktion nur auf Ordnerbasis, nicht auf Dateibasis. Sie können Ordner nicht versionieren, und das ist auch nicht nötig, da ein Ordner selbst keine Daten enthält. Stattdessen handelt es sich lediglich um einen Container für Ressourcen, die Daten enthalten. Die standardmäßige ACL ist eine Berechtigung auf Systemebene. Das bedeutet, dass Benutzer über Berechtigungen auf Systemebene (Lesen, Schreiben, Durchlaufen, Verwalten von ACLs) verfügen müssen, bis ihnen jemand Berechtigungen für einen bestimmten Ordner erteilt. ACLs funktionieren nur in der IDE.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie in der [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um einen Ordner zu erstellen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie den Service-Client.
1. Erstellen Sie den Ordner.
1. Schreiben Sie den Ordner in das Repository.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Service-Client erstellen**

Bevor Sie eine Ressourcensammlung programmgesteuert erstellen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Erstellen Sie den Ordner**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressourcenerfassung zu erstellen und die Ressourcenerfassung mit identifizierenden Informationen, einschließlich der UUID, dem Ordnernamen und der Beschreibung, zu füllen.

**Den Ordner in das Repository schreiben**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressourcenerfassung zu schreiben und die URI des Zielordners anzugeben.

**Siehe auch**

[Erstellen von Ordnern mit der Java-API](aem-forms-repository.md#create-folders-using-the-java-api)

[Erstellen von Ordnern mit der Web Service-API](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Erstellen von Ordnern mit der Java-API {#create-folders-using-the-java-api}

Erstellen Sie einen Ordner mit der Repository Service-API (Java):

1. Projektdateien einschließen

   Fügen Sie Projektdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, in dem Sie sein Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, dass Verbindungseigenschaften enthält.

1. Erstellen Sie den Ordner

   Um eine Ressourcensammlung zu erstellen, müssen Sie zunächst ein `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean`-Objekt erstellen.

   Rufen Sie die `newResourceCollection`-Methode des `repositoryInfomodelFactoryBean`-Objekts auf und übergeben Sie die folgenden Parameter:

   * Eine `com.adobe.repository.infomodel.Id` UUID-Kennung, die der Ressource zugewiesen werden soll.
   * A `com.adobe.repository.infomodel.Lid` UUID-Kennung, die der Ressource zugewiesen werden soll.
   * Eine `java.lang.String` mit dem Namen der Ressourcensammlung. Beispiel: `FormsFolder`.

   Die Methode gibt ein `com.adobe.repository.infomodel.bean.ResourceCollection`-Objekt zurück, das den neuen Ordner darstellt.

   Legen Sie die Beschreibung des Ordners mithilfe der `setDescription`-Methode fest und übergeben Sie die folgenden Parameter:

   * Eine `String`, die die Ressourcenkollektion beschreibt. In diesem Beispiel wird `"test Folder"` `.` benutzt

1. Den Ordner in das Repository schreiben

   Rufen Sie die `writeResource`-Methode des `ResourceRepositoryClient`-Objekts auf und übergeben Sie die URI des Ordners und des `ResourceCollection`-Objekts. Die URI zum Ordner kann beispielsweise der folgende Wert sein: `/Applications/FormsApplication/1.0/`.

   Die Methode gibt eine Instanz des neu erstellten `com.adobe.repository.infomodel.bean.Resource`-Objekts zurück. Sie können beispielsweise den Kennungswert der neuen Ressource abrufen, indem Sie die`getId`-Method des `com.adobe.repository.infomodel.bean.Resource` Objekts aufrufen.

**Siehe auch**

[Erstellen eines Ordners](aem-forms-repository.md#creating-folders)

[Kurzanleitung (SOAP-Modus): Erstellen eines Ordners mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Ordnern mit der Web Service-API {#create-folders-using-the-web-service-api}

Erstellen Sie einen Ordner mit der Repository Service-API (Web-Dienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt durch Aufrufen des Standardkonstruktors. Legen Sie dessen `Credentials`-Eigenschaft mithilfe eines `System.Net.NetworkCredential`-Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Erstellen Sie den Ordner

   Erstellen Sie den Ordner mit dem Standardkonstruktor für die `ResourceCollection`-Klasse und übergeben Sie die folgenden Parameter:

   * Ein `Id`-Objekt, das durch Aufrufen des Standardkonstruktors für die `Id`-Klasse und das `id`-Feld des `Resource`-Objekts zugewiesen wird.
   * Ein `Lid`-Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid`-Klasse und das `lid`-Feld des `Resource`-Objekts zugewiesen wird.
   * Eine Zeichenfolge, die den Namen der Ressourcensammlung enthält, die dem `name`-Feld des `Resource`-Objekts zugewiesen wird. Der in diesem Beispiel verwendete Name lautet `"testfolder"`.
   * Eine Zeichenfolge, die die Beschreibung der Ressourcensammlung enthält, die dem `description`-Feld des `Resource`-Objekts zugewiesen wird. Die in diesem Beispiel verwendete Beschreibung lautet `"test folder"`.

1. Den Ordner in das Repository schreiben

   Rufen Sie die `writeResource`-Methode des `RepositoryServiceService`-Objekts auf und übergeben Sie die folgenden Parameter:

   * Der Pfad, in dem der Ordner erstellt werden soll.
   * Das `ResourceCollection`-Objekt, das den Ordner darstellt.
   * Übergeben Sie `null` für die beiden anderen Parameter.

**Siehe auch**

[Erstellen eines Ordners](aem-forms-repository.md#creating-folders)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Schreiben von Ressourcen {#writing-resources}

Sie können Ressourcen an einem bestimmten Speicherort im Repository erstellen. Die natürliche Dateigröße unterliegt den Datenbankbeschränkungen und dem Zeitlimit der Sitzung. Für die Standardkonfiguration sind Dateien auf 25 MB beschränkt. Sie müssen die Datenbankkonfiguration ändern, um die maximale Dateigröße zu erhöhen oder zu verringern.

Das Schreiben von Ressourcen entspricht dem Speichern von Daten im Repository. Nachdem Sie eine Ressource in das Repository geschrieben haben steht sie für alle Clients im Repository-Ökosystem zur Verfügung. Wenn Sie Ressourcen wie z.B. XML-Schemata, XDP-Dateien und XSD-Dateien in das Repository schreiben, werden die Inhalte anhand des MIME-Typs analysiert. Wenn der MIME-Typ unterstützt wird, bestimmt der Parser, ob eine implizite Beziehung zu anderen Inhalten besteht. Wenn beispielsweise ein Cascading Style Sheet (CSS) über eine relative URL verfügt, die auf eine gemeinsame CSS verweist, wird erwartet, dass Sie die gemeinsame CSS ebenfalls in das Repository senden. Die Beziehung zwischen den beiden Ressourcen wird als ausstehende Beziehung für einen Zeitraum von 30 Tagen gespeichert. Dieser kann nicht angepasst werden. Wenn Sie die gemeinsame CSS innerhalb des 30-tägigen Zeitraums an das Repository senden, wird die Beziehung etabliert.

Wenn Sie eine Ressource erstellen, wird die Zugriffssteuerungsliste (ACL) vom übergeordneten Ordner übernommen. Der Stammordner verfügt über Berechtigungen auf Systemebene, bis eine erste Ressource oder ein erster Ordner erstellt wird. Ab diesem Zeitpunkt erhält die Ressource oder der Ordner standardmäßige ACL-Berechtigungen.

Sie können Ressourcen programmgesteuert schreiben, indem Sie die Java-API des Repository-Dienstes oder die Web-Dienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie in [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um eine Ressource zu schreiben, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Geben Sie den URI der zu lesenden Ressource an.
1. Lesen Sie die Ressource.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Geben Sie die URI des Zielordners für die Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu lesenden Ressource enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: „/*path*/*Ordner*“.

**Ressource erstellen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu erstellen, und füllen Sie die Ressource mit identifizierenden Informationen, einschließlich der UUID, dem Ressourcennamen und der Beschreibung.

**Ressourceninhalt festlegen**

Rufen Sie die Methode des Repository-Dienstes auf, um Ressourceninhalte zu erstellen und diesen Inhalt in der Ressource zu speichern.

**Die Ressource in den Zielordner schreiben**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu schreiben, und geben Sie die URI des Zielordners an.

**Siehe auch**

[Schreiben von Ressourcen mit der Java-API](aem-forms-repository.md#write-resources-using-the-java-api)

[Schreiben von Ressourcen mit der Web-Dienst-API](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Schreiben von Ressourcen mit der Java-API {#write-resources-using-the-java-api}

Schreiben Sie eine Ressource mit der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das Object `ServiceClientFactory` übergeben, das Verbindungseigenschaften enthält.

1. Die URI des Zielordners für die Ressource angeben

   Geben Sie die URI des Zielordners für die Ressource an. In diesem Fall, da die Ressource mit Namen `testResource` im Ordner mit dem Namen `testFolder` gespeichert wird, lautet der URI des Ordners `"/testFolder"`. Der URI wird als ein `java.lang.String`-Objekt gespeichert.

1. Ressource erstellen

   Um eine Ressource zu erstellen, müssen Sie zunächst ein `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean`-Objekt erstellen.

   Rufen Sie die `newResource`-Methode des `RepositoryInfomodelFactoryBean`-Objekts auf, die ein `com.adobe.repository.infomodel.bean.Resource`-Objekt erstellt. In diesem Beispiel werden die folgenden Parameter bereitgestellt:

   * Ein `com.adobe.repository.infomodel.Id`-Objekt, das durch Aufrufen des Standardkonstruktors für die `Id`-Klasse erstellt wird.
   * Ein `com.adobe.repository.infomodel.Lid`-Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid`-Klasse erstellt wird.
   * Ein `java.lang.String` enthält den Dateinamen der Ressource.

   Um die Beschreibung der Ressource anzugeben, rufen Sie die `setDescription`-Methode des `Resource`-Objekts auf und übergeben Sie eine Zeichenfolge, die die Beschreibung enthält. In diesem Beispiel lautet der Ordner `"test resource"`.

1. Ressourceninhalte angeben

   Um Inhalte für die Ressource zu erstellen, rufen Sie die `newResourceContent`-Methode des `RepositoryInfomodelFactoryBean`-Objekts auf, welche ein `com.adobe.repository.infomodel.bean.ResourceContent`-Objekt zurückgibt. Fügen Sie dem `ResourceContent`-Objekt Inhalt hinzu. In diesem Beispiel wird dies durch die folgenden Aufgaben erreicht:

   * Aufrufen der `setDataDocument`-Methode des `ResourceContent`-Objekts und Übergabe in ein `com.adobe.idp.Document`-Objekt
   * Aufrufen der `setSize`-Methode des `ResourceContent`-Objekts und Übergabe der Größe in Byte des `Document`-Objekts.

   Fügen Sie der Ressource den Inhalt hinzu, indem Sie die `setContent`-Methode des `Resource`-Objekts aufrufen und in das `ResourceContent`-Objekt übergeben. Weitere Informationen finden Sie unter [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Die Ressource in den Zielordner schreiben

   Rufen Sie die Methode `writeResource` des `ResourceRepositoryClient`-Objekts auf und übergeben Sie den URI des Ordners sowie das `Resource`-Objekt.

**Siehe auch**

[Schreiben von Ressourcen](aem-forms-repository.md#writing-resources)

[Kurzanleitung (SOAP-Modus): Schreiben einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Schreiben von Ressourcen mit der Web-Dienst-API {#write-resources-using-the-web-service-api}

Schreiben Sie eine Ressource mithilfe der Repository Service-API (Web-Dienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Legen Sie die `Credentials`-Eigenschaft mithilfe eines `System.Net.NetworkCredential`-Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Die URI des Zielordners für die Ressource angeben

   Geben Sie die URI des Zielordners für die Ressource an. In diesem Fall, da die Ressource mit dem Namen `testResource` im Ordner mit dem Namen `testFolder` gespeichert wird, lautet der URI des Ordners `"/testFolder"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einem `System.String`-Objekt.

1. Ressource erstellen

   Um eine Ressource zu erstellen, rufen Sie den Standardkonstruktor für die `Resource`-Klasse auf. In diesem Beispiel werden die folgenden Informationen im `Resource`-Objekt gespeichert:

   * Ein `com.adobe.repository.infomodel.Id`-Objekt, das durch Aufrufen des Standardkonstruktors für die `Id`-Klasse aufgerufen wird und dem `id`-Feld des `Resource`-Objekts zugewiesen wird.
   * Ein `com.adobe.repository.infomodel.Lid`-Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid`-Klasse aufgerufen wird und dem `lid`-Feld des `Resource`-Objekts zugewiesen wird.
   * Eine Zeichenfolge, die den Dateinamen der Ressource enthält, die dem `name`-Feld des `Resource`-Objekts zugewiesen wird. Der in diesem Beispiel verwendete Name lautet `"testResource"`.
   * Eine Zeichenfolge, die die Beschreibung der Ressource enthält, die dem `description`-Feld des `Resource`-Objekts zugewiesen wird. Die in diesem Beispiel verwendete Beschreibung lautet `"test resource"`.

1. Ressourceninhalte angeben

   Um Inhalte für die Ressource zu erstellen, rufen Sie den Standardkonstruktor für die `ResourceContent`-Klasse auf. Fügen Sie dann Inhalt zum `ResourceContent`-Objekt hinzu. In diesem Beispiel wird dies durch die folgenden Aufgaben erreicht:

   * Zuweisen eines `BLOB`-Objekts, das ein Dokument für das `dataDocument`-Feld des `ResourceContent`-Objekts enthält.
   * Zuweisen der Größe in Byte des `BLOB`-Objekts für das `size`-Feld des `ResourceContent`-Objekts.

   Fügen Sie der Ressource den Inhalt hinzu, indem Sie das `ResourceContent`-Objekt dem `content`-Feld des `Resource`-Objekts zuweisen.

1. Die Ressource in den Zielordner schreiben

   Rufen Sie die Methode `writeResource` des `RepositoryServiceService`-Objekts auf und übergeben Sie den URI des Ordners sowie das `Resource`-Objekt. Übergeben Sie `null` für die beiden anderen Parameter.

**Siehe auch**

[Schreiben von Ressourcen](aem-forms-repository.md#writing-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Auflisten von Ressourcen {#listing-resources}

Sie können Ressourcen durch die Auflistung von Ressourcen identifizieren. Für das Repository wird eine Abfrage durchgeführt, um alle Ressourcen zu finden, die mit einer bestimmten Ressourcensammlung verbunden sind.

Nachdem Sie Ihre Ressourcen organisiert haben, können Sie die von Ihnen erstellte Struktur überprüfen, indem Sie einen bestimmten Zweig der Struktur sehen, ähnlich wie bei einem Betriebssystem.

Auflisten von Ressourcen funktioniert nach Beziehung: Ressourcen sind Mitglieder von Ordnern. Die Mitgliedschaft wird durch eine Beziehung des Typs „Mitglied von“ repräsentiert. Wenn Sie Ressourcen in einem bestimmten Ordner auflisten, fragen Sie nach Ressourcen, die mit einem bestimmten Ordner durch die Beziehung „Mitglied von“ verbunden sind. Beziehungen sind gerichtet: Ein Mitglied einer Beziehung hat eine Quelle, die Mitglied der Zielgruppe ist. Die Quelle ist die Ressource; das Ziel ist der übergeordnete Ordner.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie in [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Gehen Sie wie folgt vor, um Ressourcen aufzulisten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie den Service-Client.
1. Geben Sie den Ordnerpfad an.
1. Rufen Sie die Liste der Ressourcen ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Service-Client erstellen**

Bevor Sie eine Ressourcensammlung programmgesteuert erstellen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Geben Sie den Ordnerpfad an**

Erstellen Sie eine Zeichenfolge, die den Pfad des Ordners mit den Ressourcen enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: „/*path*/*Ordner*“.

**Liste der Ressourcen abrufen**

Rufen Sie die Methode des Repository-Service auf, um die Liste der Ressourcen abzurufen, und geben Sie den Pfad des Zielordners an.

**Siehe auch**

[Auflisten von Ressourcen mit Verwendung der Java-API](aem-forms-repository.md#list-resources-using-the-java-api)

[Auflisten von Ressourcen mithilfe der Webservice-API](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Auflisten von Ressourcen mit Verwendung der Java-API {#list-resources-using-the-java-api}

Auflisten von Ressourcen mit der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den Ordnerpfad an

   Geben Sie die URI der abzufragenden Ressourcensammlung an. In diesem Fall lautet die URI `"/testFolder"`. Die URI wird als `java.lang.String`-Objekt gespeichert.

1. Liste der Ressourcen abrufen

   Rufen Sie die die `listMembers`-Methode des `ResourceRepositoryClient`-Objekts auf und übergeben Sie die URI des Ordners.

   Die Methode gibt eine `java.util.List` von `com.adobe.repository.infomodel.bean.Resource`-Objekten zurück, die die Quelle eines `com.adobe.repository.infomodel.bean.Relation` des Typs `Relation.TYPE_MEMBER_OF` sind und die die Ressourcenerfassung-URI als Ziel haben. Sie können diese `List` durchlaufen, um die einzelnen Ressourcen abzurufen. In diesem Beispiel werden der Name und die Beschreibung jeder Ressource angezeigt.

**Siehe auch**

[Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).

[Kurzanleitung (SOAP-Modus): Auflisten von Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Auflisten von Ressourcen mithilfe der Webservice-API {#list-resources-using-the-web-service-api}

Auflisten von Ressourcen mithilfe der Repository Service-API (Web Service):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Legen Sie die `Credentials`-Eigenschaft mithilfe eines `System.Net.NetworkCredential`-Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den Ordnerpfad an

   Geben Sie eine Zeichenfolge an, die die URI des zu abgefragenden Ordners enthält. In diesem Fall lautet die URI `"/testFolder"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie die URI in einem `System.String`-Objekt.

1. Liste der Ressourcen abrufen

   Rufen Sie die `listMembers`-Methode des `RepositoryServiceService`-Objekts auf und übergeben Sie die URI des Ordners als den ersten Parameter. Übergeben Sie `null` für die beiden anderen Parameter.

   Die Methode gibt ein Array von Objekten zurück, die in `Resource`-Objekte umgewandelt werden können. Sie können durch das Objekt-Array navigieren, um jede der zugehörigen Ressourcen abzurufen. In diesem Beispiel werden der Name und die Beschreibung jeder Ressource angezeigt.

**Siehe auch**

[Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Lesen von Ressourcen {#reading-resources}

Sie können Ressourcen von einem bestimmten Speicherort im Repository abrufen, um ihren Inhalt und ihre Metadaten zu lesen. Der Workflow wird durch ein Initialisierungsformular eingeleitet. Der Prozess verfügt über alle Berechtigungen, die zum Lesen des Formulars erforderlich sind. Das System ruft das Datenformular ab und liest den Inhalt aus dem Repository. Das Repository gewährt Zugriff auf den Inhalt und die Metadaten (die Möglichkeit, überhaupt zu wissen, ob die Ressource vorhanden ist).

Das Repository verfügt über die folgenden vier Berechtigungstypen:

* **traverse**: ermöglicht es, Ressourcen aufzulisten, genauer, Ressourcenmetadaten zu lesen, jedoch keine Ressourceninhalte
* **read**: ermöglicht das Lesen des Ressourceninhalts.
* **write**: ermöglicht das Schreiben von Ressourceninhalten.
* **Verwalten von Zugriffssteuerungslisten (ACLs)**: ermöglicht die Bearbeitung von ACLs für Ressourcen.

Benutzer können Prozesse nur ausführen, wenn sie über die Berechtigung zum Ausführen des Prozesses verfügen. IDE-Benutzer benötigen Berechtigungen zum Durchlaufen und Lesen, damit mit dem Repository synchronisiert werden kann. ACLs gelten nur zur Entwurfszeit, da die Laufzeit im Systemkontext erfolgt.

Sie können Ressourcen programmgesteuert lesen, indem Sie die Java-API des Repository-Services oder die Webservice-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Gehen Sie wie folgt vor, um eine Ressource zu lesen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Geben Sie den URI der zu lesenden Ressource an.
1. Lesen Sie die Ressource.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Angeben des URI der Ressource, die gelesen werden soll**

Erstellen Sie eine Zeichenfolge, die den URI der zu lesenden Ressource enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: „/*path*/*resource*“.

**Lesen der Ressource**

Rufen Sie die Methode des Repository-Services auf, um die Ressource zu lesen, und geben Sie den URI an.

**Siehe auch**

[Lesen von Ressourcen mithilfe der Java-API](aem-forms-repository.md#read-resources-using-the-java-api)

[Lesen von Ressourcen mit der Webservice-API](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Lesen von Ressourcen mithilfe der Java-API {#read-resources-using-the-java-api}

So lesen Sie eine Ressource mithilfe der Repository Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Angeben des URI der zu lesenden Ressource

   Geben Sie einen Zeichenfolgenwert an, der den URI der abzurufenden Ressource darstellt. Angenommen, die Ressource heißt zum Beispiel *testResource* und befindet sich in einem Ordner mit dem Namen *testFolder*, dann geben Sie `/testFolder/testResource` an.

1. Lesen der Ressource

   Rufen Sie die Methode `readResource` des `ResourceRepositoryClient`-Objekts auf und übergeben Sie den URI der Ressource als Parameter. Diese Methode gibt eine `Resource`-Instanz zurück, die die Ressource darstellt.

**Siehe auch**

[Lesen von Ressourcen](aem-forms-repository.md#reading-resources)

[Kurzanleitung (SOAP-Modus): Lesen einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Lesen von Ressourcen mit der Webservice-API {#reading-resources-using-the-web-service-api}

So lesen Sie eine Ressource mit Hilfe der Repository Service-API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Codierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)
   * Referenzieren Sie die Microsoft .NET-Client-Assembly. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Codierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Legen Sie seine `Credentials`-Eigenschaft mithilfe eines `System.Net.NetworkCredential`-Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Angeben des URI der zu lesenden Ressource

   Geben Sie eine Zeichenfolge an, die die URI der abzurufenden Ressource enthält. In diesem Fall, da sich die Ressource mit dem Namen `testResource` im Ordner mit dem Namen `testFolder` befindet, lautet die URI `"/testFolder/testResource"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie die URI in einem `System.String`-Objekt.

1. Lesen der Ressource

   Rufen Sie die `readResource`-Methode des `RepositoryServiceService`-Objekts auf und übergeben Sie die URI der Ressource als den ersten Parameter. Übergeben Sie `null` für die beiden anderen Parameter.

**Siehe auch**

[Lesen von Ressourcen](aem-forms-repository.md#reading-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Aktualisieren von Ressourcen {#updating-resources}

Sie können den Inhalt der Ressourcen im Repository abrufen und aktualisieren. Wenn Sie Ressourcen aktualisieren, bleibt die Zugriffssteuerung auf diese Ressourcen zwischen den Versionen unverändert. Bei einer Aktualisierung haben Sie die Möglichkeit, die Hauptversion auf eine höhere Zahl zu setzen. Wenn Sie die Hauptversion nicht inkrementieren, wird die Nebenversion automatisch aktualisiert.

Wenn Sie eine Ressource aktualisieren, wird die neue Version anhand der angegebenen Ressourcenattributen erstellt. Beim Aktualisieren einer Ressource geben Sie zwei wichtige Parameter an: den Ziel-URI und eine Ressourceninstanz, die alle aktualisierten Metadaten enthält. Wenn Sie ein bestimmtes Attribut (z. B. den Namen) nicht ändern, ist das Attribut in der übergebenen Instanz weiterhin erforderlich. Die Beziehungen, die beim Analysieren des Inhalts erstellt werden, werden der jeweiligen Version hinzugefügt und nur weitergeleitet, wenn sie angegeben werden.

Wenn Sie beispielsweise eine XDP-Datei aktualisieren, die Verweise auf andere Ressourcen enthält, werden diese zusätzlichen Verweise ebenfalls aufgezeichnet. Angenommen, die Datei „form.xdp“ Version 1.0 enthält zwei externe Verweise: ein Logo und ein Stylesheet, und Sie aktualisieren anschließend „form.xdp“, sodass es jetzt drei Verweise enthält: ein Logo, ein Stylesheet und eine Schemadatei. Während der Aktualisierung fügt das Repository die dritte Beziehung (zur Schemadatei) zu seiner ausstehenden Beziehungstabelle hinzu. Sobald die Schemadatei im Repository vorhanden ist, wird die Beziehung automatisch hergestellt. Wenn jedoch „form.xdp-Version 2.0“ das Logo nicht mehr verwendet, weist „form.xdp-Version 2.0“ keine Beziehung zum Logo auf.

Alle Aktualisierungsvorgänge sind atomisch und transaktional. Wenn beispielsweise zwei Benutzer dieselbe Ressource lesen und beide Version 1.0 auf Version 2.0 aktualisieren möchten, wird einer von ihnen erfolgreich sein und einer von ihnen schlägt fehl, wird die Integrität des Repositorys gewahrt und beide erhalten eine Meldung, die den Erfolg oder Fehler bestätigt. Wenn die Transaktion nicht bestätigt wird, wird sie im Fall eines Datenbankfehlers zurückgesetzt und abhängig vom Anwendungs-Server erfolgt eine Zeitüberschreitung oder eine Zurücksetzung.

Sie können Ressourcen programmgesteuert aktualisieren, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen über den Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Gehen Sie wie folgt vor, um eine Ressource zu aktualisieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Rufen Sie die zu aktualisierende Ressource ab.
1. Aktualisieren Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Zu aktualisierende Ressource abrufen**

Lesen Sie die Ressource. Weitere Informationen finden Sie unter [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).

**Aktualisieren der Ressource**

Legen Sie die neuen Informationen in der Ressource fest und rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu aktualisieren. Geben Sie dabei den URI, die aktualisierte Ressource und die Art und Weise an, wie die Versionsinformationen aktualisiert werden sollen.

**Siehe auch**

[Aktualisieren von Ressourcen mithilfe der Java-API](aem-forms-repository.md#update-resources-using-the-java-api)

[Aktualisieren von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Aktualisieren von Ressourcen mithilfe der Java-API {#update-resources-using-the-java-api}

Aktualisieren einee Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Zu aktualisierende Ressource abrufen

   Geben Sie den URI der Ressource an, die abgerufen und gelesen werden soll. In diesem Beispiel lautet die URI der Ressource `"/testFolder/testResource"`.

1. Aktualisieren der Ressource

   Aktualisieren der `Resource`-Objektinformationen. In diesem Beispiel rufen Sie zur Aktualisierung der Beschreibung die Methode `setDescription` des `Resource`-Objekts auf und übergeben die neue Beschreibungszeichenfolge als Parameter.

   Rufen Sie dann das `ServiceClientFactory`-Objekt `updateResource` und übergeben Sie die folgenden Parameter:

   * Ein `java.lang.String`-Objekt, das den URI der Ressource enthält.
   * Das `Resource`-Objekt, das die aktualisierten Ressourceninformationen enthält.
   * Ein `boolean`-Wert, der angibt, ob die Haupt- oder Nebenversion aktualisiert werden soll. In diesem Beispiel wird ein Wert von `true` übergeben, um anzugeben, dass die Hauptversion erhöht werden soll.

**Siehe auch**

[Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources)

[Kurzanleitung (SOAP-Modus): Aktualisieren einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Aktualisieren von Ressourcen mithilfe der Webdienst-API {#update-resources-using-the-web-service-api}

Aktualisieren einer Ressource mithilfe der Repository-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Legen Sie seine `Credentials`-Eigenschaft mit einem `System.Net.NetworkCredential`-Objekt fest, das den Benutzernamen und das Kennwort enthält.

1. Zu aktualisierende Ressource abrufen

   Geben Sie den URI der abzurufenden Ressource an und lesen Sie die Ressource. In diesem Beispiel lautet der URI der Ressource `"/testFolder/testResource"`. Weitere Informationen finden Sie unter [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).

1. Aktualisieren der Ressource

   Aktualisieren Sie die `Resource`-Objektinformationen. Um in diesem Beispiel die Beschreibung zu aktualisieren, weisen Sie dem Feld `description` des Objekts `Resource` einen neuen Wert zu.

1. Rufen Sie die Methode `RepositoryServiceService` des Objekts `updateResource` auf und übergeben Sie die folgenden Parameter:

   * Ein `System.String`-Objekt, das den URI der Ressource enthält.
   * Das `Resource`-Objekt, das die aktualisierten Ressourceninformationen enthält.
   * Ein `boolean`-Wert, der angibt, ob die Haupt- oder Nebenversion aktualisiert werden soll. In diesem Beispiel wird ein Wert von `true` übergeben, um anzugeben, dass die Hauptversion erhöht werden soll.
   * Übergeben Sie `null` für die beiden übrigen Parameter.

**Siehe auch**

[Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Suchen nach Ressourcen {#searching-for-resources}

Sie können Abfragen erstellen, um nach Ressourcen im Repository zu suchen, einschließlich des Verlaufs, verwandter Ressourcen und Eigenschaften.

Sie können verwandte Ressourcen abrufen, um Abhängigkeiten zwischen einem Formular und seinen Fragmenten zu ermitteln. Wenn Sie beispielsweise über ein Formular verfügen, können Sie bestimmen, welche Fragmente oder externen Ressourcen es verwendet. Wenn Sie ein Bild haben, können Sie auch herausfinden, welche Formulare das Bild verwenden. Sie können auch anhand von Eigenschaften nach verwandten Ressourcen suchen. Sie können beispielsweise nach allen Formularen suchen, die ein Bild mit einem bestimmten Namen verwenden, oder nach allen Bildern suchen, die von einem Formular mit einem bestimmten Namen verwendet werden. Sie können auch anhand von Ressourceneigenschaften suchen. Sie können beispielsweise eine Abfrage durchführen, um alle Formulare oder Ressourcen zu finden, deren Name mit einer bestimmten Zeichenfolge beginnt, die auch Platzhalter wie „%“ und „_“ enthalten kann. Denken Sie daran, dass die Suche auf der Grundlage von Eigenschaften nicht auf Beziehungen basiert; solche Suchen basieren auf der Annahme, dass Sie über spezifisches Wissen zu einer bestimmten Ressource verfügen.

**Abfrageanweisungen**

Eine *Abfrage* enthält eine oder mehrere Anweisungen, die durch Bedingungen logisch verbunden sind. Eine *Anweisung* besteht aus einem linken Operanden, einem Operator und einem rechten Operanden. Darüber hinaus können Sie die Sortierreihenfolge für die Suchergebnisse festlegen. Die *Sortierreihenfolge* enthält Informationen, die einer SQL-`ORDER BY`-Klausel entsprechen, und besteht aus Elementen mit den Attributen, auf denen die Suche basiert, sowie einem Wert, der angibt, ob eine aufsteigende oder absteigende Reihenfolge verwendet werden soll.

Sie können mithilfe der Java-API des Repository-Dienstes programmgesteuert nach Ressourcen suchen. Derzeit ist es nicht möglich, die Webdienst-API für die Suche nach Ressourcen zu verwenden.

**Sortierverhalten**

Die Sortierreihenfolge wird nicht beachtet, wenn die `searchProperties`-Methode des `ResourceRepositoryClient`-Objekts aufgerufen und eine Sortierreihenfolge angegeben wird. Angenommen, Sie erstellen eine Ressource mit drei benutzerdefinierten Eigenschaften, wobei deren Attributnamen `name`, `secondName` und `asecondName` lauten. Als Nächstes erstellen Sie ein Sortierreihenfolgen-Element für den Attributnamen und setzen den `ascending`-Wert auf `true`.

Dann rufen Sie die `searchProperties`-Methode des `ResourceRepositoryClient`-Objekts auf und geben die Sortierreihenfolge an. Die Suche gibt die richtige Ressource mit den drei Eigenschaften zurück. Die Eigenschaften werden jedoch nicht nach Attributnamen sortiert. Sie werden in der Reihenfolge zurückgegeben, in der sie hinzugefügt wurden: `name`, `secondName`und `asecondName`.

>[!NOTE]
>
>Weitere Informationen über den Repository-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Gehen Sie folgendermaßen vor, um nach Ressourcen zu suchen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Geben Sie den Zielordner für die Suche an.
1. Geben Sie die bei der Suche verwendeten Attribute an.
1. Erstellen Sie die bei der Suche verwendete Abfrage.
1. Erstellen Sie die Sortierreihenfolge für die Suchergebnisse.
1. Suchen Sie nach den Ressourcen.
1. Rufen Sie die Ressourcen aus dem Suchergebnis ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Zielordner für die Suche angeben**

Erstellen Sie eine Zeichenfolge, die den Basispfad enthält, von dem aus die Suche durchgeführt werden soll. Die Syntax enthält Schrägstriche, wie in diesem Beispiel: „/*Pfad*/*Ordner*“.

**Angabe der für die Suche verwendeten Attribute**

Sie können Ihre Suche auf die in den Ressourcen enthaltenen Attribute gründen. Geben Sie die Werte der Attribute an, nach denen die Suche durchgeführt werden soll.

**Erstellen Sie die Abfrage für die Suche**

Erstellen Sie eine Abfrage mithilfe von Anweisungen und Bedingungen. Jede Anweisung gibt das Attribut an, auf dem die Suche basieren soll, die zu verwendende Bedingung und den bei der Suche zu verwendenden Attributwert.

**Erstellen der Sortierreihenfolge für die Suchergebnisse**

Die Sortierreihenfolge besteht aus Elementen, die je eines der bei der Suche verwendeten Attribute und einen Wert enthalten, der angibt, ob in aufsteigender oder absteigender Reihenfolge gesucht werden soll.

**Suche nach Ressourcen**

Suchen Sie mithilfe des Ordners, der Abfrage und der Sortierreihenfolge nach den Ressourcen. Geben Sie außerdem die Suchtiefe und eine Obergrenze für die Anzahl der zurückzugebenden Ergebnisse an.

**Abrufen der Ressourcen aus dem Suchergebnis**

Iterieren Sie durch die zurückgegebene Liste der Ressourcen und extrahieren Sie die Informationen für die weitere Verarbeitung.

**Siehe auch**

[Suche nach Ressourcen mit der Java-API](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Suche nach Ressourcen mit der Java-API {#search-for-resources-using-the-java-api}

Suchen Sie mithilfe der Repository-Service-API (Java) nach einer Ressource:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den Zielordner für die Suche an

   Geben Sie den URI des Basispfads an, von dem aus die Suche ausgeführt werden soll. In diesem Beispiel lautet der URI der Ressource `/testFolder`.

1. Geben Sie die bei der Suche verwendeten Attribute an

   Geben Sie die Werte für die Attribute an, nach denen die Suche durchgeführt werden soll. Die Attribute befinden sich in einem `com.adobe.repository.infomodel.bean.Resource`-Objekt. In diesem Beispiel wird die Suche nach dem Namensattribut durchgeführt; daher wird ein `java.lang.String` verwendet, das den Namen des `Resource`-Objekts enthält, der in diesem Fall `testResource` lautet.

1. Erstellen der bei der Suche verwendeten Abfrage

   Um eine Abfrage zu erstellen, erstellen Sie ein `com.adobe.repository.query.Query`-Objekt, indem Sie den Standardkonstruktor für die `Query`-Klasse aufrufen und der Abfrage Anweisungen hinzufügen.

   Um eine Anweisung zu erstellen, rufen Sie den Konstruktor für die `com.adobe.repository.query.Query.Statement`-Klasse auf und übergeben Sie die folgenden Parameter:

   * Ein linker Operand, der die Konstante des Ressourcen-Attributs enthält. Da in diesem Beispiel der Name der Ressource als Grundlage für die Suche verwendet wird, wird der statische Wert `Resource.ATTRIBUTE_NAME` verwendet.
   * Ein Operator, der die bei der Suche nach dem Attribut verwendete Bedingung enthält. Der Operator muss eine der statischen Konstanten in der `Query.Statement` -Klasse sein. In diesem Beispiel wird der statische Wert `Query.Statement.OPERATOR_BEGINS_WITH` verwendet.
   * Ein rechter Operand, der den Attributwert enthält, nach dem gesucht werden soll. In diesem Beispiel wird das Namensattribut, ein `String` mit dem Wert `"testResource"`, verwendet.

   Geben Sie den Namespace des linken Operanden an, indem Sie die `setNamespace`-Methode des `Query.Statement`-Objekts aufrufen und einen der in der `com.adobe.repository.infomodel.bean.ResourceProperty`-Klasse enthaltenen statischen Werte übergeben. In diesem Beispiel wird `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY` verwendet.

   Fügen Sie jede Anweisung der Abfrage hinzu, indem Sie die `addStatement`-Methode des `Query`-Objekts aufrufen und das `Query.Statement`-Objekt übergeben.

1. Erstellen der Sortierreihenfolge für die Suchergebnisse

   Um die in den Suchergebnissen verwendete Sortierreihenfolge festzulegen, erstellen Sie ein `com.adobe.repository.query.sort.SortOrder`-Objekt, indem Sie den Standardkonstruktor für die `SortOrder`-Klasse aufrufen, und fügen Sie Elemente für die Sortierreihenfolge hinzu.

   Um ein Element für die Sortierreihenfolge zu erstellen, rufen Sie einen der Konstruktoren für die `com.adobe.repository.query.sort.SortOrder.Element`-Klasse auf. Da in diesem Beispiel der Name der Ressource als Grundlage für die Suche verwendet wird, wird als erster Parameter der statische Wert `Resource.ATTRIBUTE_NAME` und als zweiter Parameter die aufsteigende Reihenfolge (ein `boolean`-Wert von `true`) angegeben.

   Fügen Sie jedes Element der Sortierreihenfolge hinzu, indem Sie die `addSortElement`-Methode des `SortOrder`-Objekts aufrufen und das `SortOrder.Element`-Objekt übergeben.

1. Suche nach Ressourcen

   Um nach `resources` auf der Grundlage von Attributeigenschaften zu suchen, rufen Sie die `searchProperties`-Methode des `ResourceRepositoryClient`-Objekts auf und geben die folgenden Parameter ein:

   * Ein `String` mit dem Basispfad, von dem aus die Suche ausgeführt werden soll. In diesem Fall wird `"/testFolder"` verwendet.
   * Die bei der Suche verwendete Abfrage.
   * Die Tiefe der Suche. In diesem Fall wird `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` verwendet, um anzugeben, dass der Basispfad und alle zugehörigen Ordner verwendet werden sollen.
   * Ein `int`-Wert, der die erste Zeile angibt, aus der die nicht paginierte Ergebnismenge ausgewählt werden soll. In diesem Beispiel wird `0` festgelegt.
   * Ein `int`-Wert, der die maximale Anzahl der zurückzugebenden Ergebnisse angibt. In diesem Beispiel wird `10` festgelegt.
   * Die bei der Suche verwendete Sortierreihenfolge.

   Die Methode gibt ein `java.util.List` von `Resource`-Objekten in der angegebenen Sortierreihenfolge zurück.

1. Abrufen der Ressourcen aus dem Suchergebnis

   Um die im Suchergebnis enthaltenen Ressourcen abzurufen, iterieren Sie durch die `List` und wandeln jedes Objekt in eine `Resource` um, um seine Informationen zu extrahieren. In diesem Beispiel wird der Name jeder Ressource angezeigt.

**Siehe auch**

[Suchen nach Ressourcen](aem-forms-repository.md#searching-for-resources)

[Kurzanleitung (SOAP-Modus): Suchen nach Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von Ressourcenbeziehungen {#creating-resource-relationships}

Sie können Beziehungen zwischen Ressourcen im Repository angeben. Es gibt drei Arten von Beziehungen:

* **Abhängigkeit**: eine Beziehung, in der eine Ressource von anderen Ressourcen abhängig ist, was bedeutet, dass alle damit verbundenen Ressourcen im Repository benötigt werden.
* **Mitgliedschaft (Dateisystem)**: eine Beziehung, in der sich eine Ressource in einem bestimmten Ordner befindet.
* **Benutzerdefiniert**: eine Beziehung, die Sie zwischen Ressourcen angeben. Wenn beispielsweise eine Ressource veraltet ist und eine andere in das Repository eingefügt wird, können Sie Ihre eigene Ersatzbeziehung festlegen.

Sie können auch eigene benutzerdefinierte Beziehungen anlegen. Wenn Sie beispielsweise eine HTML-Datei im Repository speichern und ein Bild verwendet wird, können Sie eine benutzerdefinierte Beziehung festlegen, um die HTML-Datei mit dem Bild zu verknüpfen (denn normalerweise werden nur XML-Dateien über eine repository-definierte Abhängigkeitsbeziehung mit Bildern verknüpft sind). Ein weiteres Beispiel für eine benutzerdefinierte Beziehung wäre, wenn Sie eine andere Ansicht des Repositorys mit einer zyklischen Diagrammstruktur anstatt einer Baumstruktur erstellen möchten. Sie können ein Kreisdiagramm zusammen mit einem Viewer definieren, um diese Beziehungen zu durchlaufen. Schließlich könnten Sie angeben, dass eine Ressource eine andere Ressource ersetzt, obwohl die beiden Ressourcen völlig verschieden sind. In diesem Fall können Sie einen Beziehungstyp außerhalb des reservierten Bereichs definieren und eine Beziehung zwischen diesen beiden Ressourcen erstellen. Ihr Programm wäre der einzige Client, der die Beziehung erkennen und verarbeiten könnte, und es könnte für die Suche nach dieser Beziehung verwendet werden.

Sie können Beziehungen zwischen Ressourcen programmgesteuert angeben, indem Sie die Java-API des Repository-Service oder die Web Service-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Gehen Sie wie folgt vor, um eine Beziehung zwischen zwei Ressourcen anzugeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen.
1. Erstellen Sie die Beziehung.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**URIs der Ressourcen angeben, die verknüpft werden sollen**

Erstellen Sie Zeichenfolgen, die die URIs der Ressource enthalten, die verknüpft werden soll. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: „/*Pfad*/*Ressource*“.

**Beziehung erstellen**

Rufen Sie die Methode des Repository-Service auf, um den Beziehungstyp zu erstellen und festzulegen.

**Siehe auch**

[Erstellen von Beziehungsressourcen mit der Java-API](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Erstellen von Beziehungsressourcen mithilfe der Web Service-API](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Erstellen von Beziehungsressourcen mit der Java-API {#create-relationship-resources-using-the-java-api}

Erstellen Sie mithilfe der Java-API des Repository-Service Beziehungsressourcen und führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe des entsprechenden Konstruktors ein `ResourceRepositoryClient`-Objekt und übergeben Sie ihm ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie die URIs der zu verknüpfenden Ressourcen an

   Geben Sie die URIs der zu verknüpfenden Ressourcen an. Da die Ressourcen in diesem Fall `testResource1` und `testResource2` heißen und sich im Ordner `testFolder` befinden, lauten ihre URIs `"/testFolder/testResource1"` und `"/testFolder/testResource2"`. Die URIs werden als `java.lang.String`-Objekte gespeichert. In diesem Beispiel werden die Ressourcen zuerst in das Repository geschrieben und ihre URIs abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Erstellen Sie die Beziehung

   Rufen Sie die Methode `createRelationship` des `ResourceRepositoryClient`-Objekts auf und übergeben Sie ihr die folgenden Parameter:

   * Der URI der Quellressource.
   * Der URI der Zielressource.
   * Typ der Beziehung, wobei es sich um eine der statischen Konstanten in der Klasse `com.adobe.repository.infomodel.bean.Relation` handelt. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch Angabe des Werts `Relation.TYPE_DEPENDANT_OF` festgelegt.
   * Ein `boolean`-Wert, der angibt, ob die Zielressource automatisch auf der `com.adobe.repository.infomodel.Id`-basierten Kennung der neuen Hauptressource aktualisiert wird. In diesem Beispiel wird aufgrund der Abhängigkeitsbeziehung der Wert `true` festgelegt ist.

   Sie können auch eine Liste verwandter Ressourcen für eine bestimmte Ressource abrufen, indem Sie die Methode `getRelated` des `ResourceRepositoryClient`-Objekts aufrufen und die folgenden Parameter übergeben:

   * Der URI der Ressource, für die verwandte Ressourcen abgerufen werden sollen. In diesem Beispiel wird die Quellressource ( `"/testFolder/testResource1"`) angegeben.
   * Ein `boolean`-Wert, der angibt, ob die angegebene Ressource die Quellressource in der Beziehung ist. In diesem Beispiel wird der Wert `true` angegeben, weil dies der Fall ist.
   * Der Beziehungstyp, der eine der statischen Konstanten in der Klasse `Relation` ist. In diesem Beispiel wird eine Abhängigkeitsbeziehung mit demselben Wert angegeben, der bereits zuvor verwendet wurde: `Relation.TYPE_DEPENDANT_OF`.

   Die `getRelated`-Methode gibt ein `java.util.List` von `Resource`-Objekten zurück, durch die Sie iterieren können, um jede der zugehörigen Ressourcen abzurufen, wobei Sie die in `List` enthaltenen Objekte in `Resource` umwandeln. In diesem Beispiel wird erwartet, dass `testResource2` in der Liste der zurückgegebenen Ressourcen enthalten ist.

**Siehe auch**

[Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships)

[Kurzanleitung (SOAP-Modus): Erstellen von Beziehungen zwischen Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Beziehungsressourcen mithilfe der Web Service-API {#create-relationship-resources-using-the-web-service-api}

Erstellen Sie Beziehungsressourcen mithilfe der Repository-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Setzen Sie seine `Credentials`-Eigenschaft mit einem `System.Net.NetworkCredential`-Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie die URIs der zu verknüpfenden Ressourcen an

   Geben Sie die URIs der zu verknüpfenden Ressourcen an. Da die Ressourcen in diesem Fall `testResource1` und `testResource2` heißen und sich in dem Ordner `testFolder` befinden, lauten ihre URIs `"/testFolder/testResource1"` und `"/testFolder/testResource2"`. Bei Verwendung einer mit dem Microsoft .NET Framework kompatiblen Sprache (beispielsweise C#) werden die URIs als `System.String`-Objekte gespeichert. In diesem Beispiel werden die Ressourcen zuerst in das Repository geschrieben und ihre URIs abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Erstellen Sie die Beziehung

   Rufen Sie die Methode `createRelationship` des `RepositoryServiceService`-Objekts auf und übergeben Sie ihr die folgenden Parameter:

   * Der URI der Quellressource.
   * Der URI der Zielressource.
   * Der Beziehungstyp. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch Angabe des Werts `3` hergestellt.
   * Ein `boolean`-Wert, der angibt, ob der Beziehungstyp angegeben wurde. In diesem Beispiel wird der Wert `true` festgelegt.
   * Ein `boolean`-Wert, der angibt, ob die Zielressource automatisch auf die `Id`-basierte Kennung der neuen Hauptressource aktualisiert wird. In diesem Beispiel wird aufgrund der Abhängigkeitsbeziehung der Wert `true` festgelegt.
   * Ein `boolean`-Wert, der angibt, ob die Ziel-Kopfzeile angegeben wurde. In diesem Beispiel wird der Wert `true` festgelegt.
   * Übergeben Sie `null` als letzten Parameter.

   Sie können auch eine Liste verwandter Ressourcen für eine bestimmte Ressource abrufen, indem Sie die `getRelated`-Methode des `RepositoryServiceService`-Objekts aufrufen und die folgenden Parameter übergeben:

   * Der URI der Ressource, für die verwandte Ressourcen abgerufen werden sollen. In diesem Beispiel wird die Quellressource ( `"/testFolder/testResource1"`) angegeben.
   * Ein `boolean`-Wert, der angibt, ob die angegebene Ressource die Quellressource in der Beziehung ist. In diesem Beispiel wird der Wert `true` festgelegt, da dies der Fall ist.
   * Ein `boolean`-Wert, der angibt, ob die Quellressource angegeben wurde. In diesem Beispiel wird der Wert `true` bereitgestellt.
   * Ein Array von Ganzzahlen, das die Beziehungstypen enthält. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch die Verwendung desselben Wertes im Array, der bereits zuvor verwendet wurde, angegeben: `3`.
   * Übergeben Sie `null` für die beiden übrigen Parameter.

   Die `getRelated`-Methode gibt ein Array von Objekten zurück, die in `Resource`-Objekte umgewandelt werden können, durch die Sie iterieren können, um jede der zugehörigen Ressourcen abzurufen. In diesem Beispiel wird erwartet, dass `testResource2` in der Liste der zurückgegebenen Ressourcen enthalten ist.

**Siehe auch**

[Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen sperren {#locking-resources}

Sie können eine Ressource oder eine Gruppe von Ressourcen für die ausschließliche Nutzung durch einen bestimmten Benutzer oder die gemeinsame Nutzung durch mehrere Benutzer sperren. Eine freigegebene Sperre ist ein Hinweis darauf, dass mit der Ressource etwas passieren wird, aber es hindert niemanden daran, Aktionen mit dieser Ressource durchzuführen. Eine freigegebene Sperre sollte als Signalmechanismus betrachtet werden. Eine exklusive Sperre bedeutet, dass der Benutzer, der die Ressource gesperrt hat, die Ressource ändern wird. Die Sperre stellt sicher, dass niemand anders dies tun kann, bis der Benutzer den Zugriff auf die Ressource nicht mehr benötigt und die Sperre freigegeben hat. Wenn ein Repository-Administrator eine Ressource entsperrt, werden alle exklusiven und freigegebenen Sperren für diese Ressource automatisch entfernt. Dieser Aktionstyp ist für Situationen gedacht, in denen ein Benutzer nicht mehr verfügbar ist und die Ressource nicht entsperrt hat.

Wenn eine Ressource gesperrt ist, wird auf der Registerkarte „Ressourcen“ in der Workbench ein Schlosssymbol angezeigt, wie in der folgenden Abbildung dargestellt.

![lr_lr_lockrepository](assets/lr_lr_lockrepository.png)

Sie können den Zugriff auf Ressourcen programmgesteuert kontrollieren, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen über den Repository-Dienst finden Sie unter [Dienstereferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Gehen Sie folgendermaßen vor, um Ressourcen zu sperren und zu entsperren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Geben Sie den URI der Ressource an, die gesperrt werden soll.
1. Ressource sperren.
1. Rufen Sie die Sperren für die Ressource ab.
1. Ressource entsperren

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Geben Sie den URI der Ressource an, die gesperrt werden soll**

Erstellen Sie eine Zeichenfolge, die den URI der Ressource enthält, die gesperrt werden soll. Die Syntax enthält Schrägstriche, wie in diesem Beispiel: „/*path*/*resource*“.

**Ressource sperren**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu sperren, und geben Sie den URI, den Typ der Sperre und die Sperrtiefe an.

**Sperren für die Ressource abrufen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Sperren für die Ressource abzurufen, und geben Sie den URI an.

**Ressource entsperren**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu entsperren und den URI anzugeben.

**Siehe auch**

[Sperren von Ressourcen mit der Java-API](aem-forms-repository.md#lock-resources-using-the-java-api)

[Sperren von Ressourcen mit der Webdienst-API](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Sperren von Ressourcen mit der Java-API {#lock-resources-using-the-java-api}

Sperren von Ressourcen mit der Repository-Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der Ressource an, die gesperrt werden soll

   Geben Sie den URI der Ressource an, die gesperrt werden soll. Da sich in diesem Fall die Ressource `testResource` in dem Ordner `testFolder` befindet, lautet ihr URI `"/testFolder/testResource"`. Der URI wird als `java.lang.String`-Objekt gespeichert.

1. Ressource sperren

   Rufen Sie die `lockResource`-Methode des `ResourceRepositoryClient`-Objekts auf und übergeben Sie die folgenden Parameter:

   * Der URI der Ressource.
   * Der Sperrbereich. Da in diesem Beispiel die Ressource für die ausschließliche Verwendung gesperrt wird, wird der Sperrbereich als `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE` angegeben.
   * Die Sperrtiefe. In diesem Beispiel wird die Sperrtiefe mit `Lock.DEPTH_ZERO` angegeben, da die Sperre nur für die betreffende Ressource und nicht für ihre Mitglieder oder Unterelemente gelten soll.

   >[!NOTE]
   >
   >Die überladene Version der `lockResource`-Methode, die vier Parameter erfordert, löst eine Ausnahme aus. Stellen Sie sicher, dass Sie die `lockResource`-Methode verwenden, die drei Parameter erfordert, wie in dieser Anleitung gezeigt.

1. Sperren für die Ressource abrufen

   Rufen Sie die `getLocks`-Methode des `ResourceRepositoryClient`-Objekts auf und übergeben Sie den URI der Ressource als Parameter. Die Methode gibt eine Liste von Sperrobjekten zurück, durch die Sie iterieren können. In diesem Beispiel werden der Sperreigentümer, die Sperrtiefe und der Geltungsbereich für jedes Objekt durch Aufrufen der Methoden `getOwnerUserId`, `getDepth` und `getType` des jeweiligen Sperrobjekts ausgegeben.

1. Ressource entsperren

   Rufen Sie die `unlockResource`-Methode des `ResourceRepositoryClient`-Objekts auf und übergeben Sie den URI der Ressource als Parameter. Weitere Informationen finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Siehe auch**

[Ressourcen sperren](aem-forms-repository.md#locking-resources)

[Kurzanleitung (SOAP-Modus): Sperren einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Sperren von Ressourcen mit der Webdienst-API {#lock-resources-using-the-web-service-api}

Sperren Sie Ressourcen mithilfe der Repository Service API (Web Service):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, welche die Repository-WSDL mit Base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Legen Sie seine `Credentials`-Eigenschaft mit einem `System.Net.NetworkCredential`-Objekt fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der Ressource an, die gesperrt werden soll

   Geben Sie eine Zeichenfolge an, die den URI der zu sperrenden Ressource enthält. Da sich die Ressource mit dem Namen `testResource` im Ordner `testFolder` befindet, lautet ihr URI in diesem Fall `"/testFolder/testResource"`. Wenn Sie eine mit dem Microsoft .NET Framework kompatible Sprache (beispielsweise C#) verwenden, speichern Sie den URI in einem `System.String`-Objekt.

1. Ressource sperren

   Rufen Sie die `lockResource`-Methode des `RepositoryServiceService`-Objekts auf und übergeben Sie die folgenden Parameter:

   * Der URI der Ressource.
   * Der Sperrbereich. Da in diesem Beispiel die Ressource für die ausschließliche Verwendung gesperrt wird, wird der Sperrbereich als `11` angegeben.
   * Die Sperrtiefe. In diesem Beispiel wird die Sperrtiefe mit `2` angegeben, da die Sperre nur für die betreffende Ressource und nicht für ihre Mitglieder oder Unterelemente gelten soll.
   * Ein `int`-Wert, der die Anzahl der Sekunden angibt, bis die Sperre abläuft. In diesem Beispiel wird der Wert von `1000` verwendet.
   * Übergeben Sie `null` als letzten Parameter.

1. Sperren für die Ressource abrufen

   Rufen Sie die `getLocks`-Methode des `RepositoryServiceService`-Objekts auf und übergeben Sie den URI der Ressource als ersten Parameter und `null` als zweiten Parameter. Die Methode gibt ein `object`-Array zurück, das `Lock`-Objekte enthält, durch die Sie iterieren können. In diesem Beispiel werden Sperreigentümer, -tiefe und -umfang für jedes Objekt durch Zugriff auf die Felder `ownerUserId`, `depth` und `type` jedes `Lock`-Objekts ausgegeben.

1. Ressource entsperren

   Rufen Sie die `unlockResource`-Methode des `RepositoryServiceService`-Objekts auf und übergeben Sie den URI der Ressource als ersten Parameter und `null` als zweiten Parameter.

**Siehe auch**

[Ressourcen sperren](aem-forms-repository.md#locking-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Löschen von Ressourcen {#deleting-resources}

Sie können Ressourcen programmgesteuert von einem bestimmten Speicherort im Repository löschen, indem Sie die Java-API (SOAP) des Repository-Dienstes verwenden.

Wenn Sie eine Ressource löschen, ist die Löschung normalerweise dauerhaft, obwohl in einigen Fällen ECM-Repositories die Versionen der Ressource entsprechend ihrer Verlaufsmechanismen speichern können. Daher ist es wichtig, dass Sie beim Löschen einer Ressource sicherstellen, dass Sie diese Ressource nie wieder benötigen. Zu den häufigen Gründen für das Löschen einer Ressource gehört die Notwendigkeit, den verfügbaren Speicherplatz in der Datenbank zu vergrößern. Sie können eine Version einer Ressource löschen, müssen dabei aber die Ressourcenkennung und nicht ihre logische Kennung (LID) oder den Pfad angeben. Wenn Sie einen Ordner löschen, wird alles in diesem Ordner, einschließlich der Unterordner und Ressourcen, automatisch gelöscht.

Zugehörige Ressourcen werden nicht gelöscht. Wenn Sie beispielsweise ein Formular haben, das die Datei „logo.gif“ verwendet, und Sie „logo.gif“ löschen, wird eine Beziehung in der Tabelle der ausstehenden Beziehungen gespeichert. Alternativ können Sie bei veralteten Versionen den Objektstatus der neuesten Version auf „veraltet“ setzen.

Ein Löschvorgang ist in ECM-Systemen nicht transaktionssicher. Wenn Sie beispielsweise versuchen, 100 Ressourcen zu löschen und der Vorgang für die 50. Ressource fehlschlägt, werden die ersten 49 Instanzen gelöscht, der Rest jedoch nicht. Andernfalls ist das Standardverhalten das Rollback (Nicht-Zusage).

>[!NOTE]
>
>Bei Verwendung der `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()`-Methode mit einem ECM-Repository (EMC Documentum Content Server und IBM FileNet P8 Content Manager) wird die Transaktion nicht zurückgesetzt, wenn der Löschvorgang für eine der angegebenen Ressourcen fehlschlägt, was bedeutet, dass die gelöschten Dateien nicht rückgängig gemacht werden können.

>[!NOTE]
>
>Weitere Informationen über den Repository-Dienst finden Sie unter [Dienstereferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Um eine Ressource zu löschen, gehen Sie folgendermaßen vor:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Repository-Service-Client.
1. Geben Sie den URI der Ressource an, die gelöscht werden soll.
1. Löschen Sie die Ressource.

**Projektdateien einbeziehen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch das Erstellen eines Service-Clients erreicht.

**Geben Sie den URI der Ressource an, die gelöscht werden soll**

Erstellen Sie eine Zeichenfolge, die den URI der zu löschenden Ressource enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel: „/*Pfad*/*Ressource*“. Handelt es sich bei der zu löschenden Ressource um einen Ordner, erfolgt die Löschung rekursiv.

**Ressource löschen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu löschen, und geben Sie den URI an.

**Siehe auch**

[Löschen von Ressourcen mithilfe der Java-API](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Löschen von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Löschen von Ressourcen mithilfe der Java-API (SOAP) {#delete-resources-using-the-java-api-soap}

Löschen Sie eine Ressource mithilfe der Repository-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen des Service-Clients

   Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der Ressource an, die gelöscht werden soll

   Geben Sie den URI der abzurufenden Ressource an. Da sich die Ressource testResourceToBeDeleted in dem Ordner testFolder befindet, lautet ihr URI in diesem Fall `/testFolder/testResourceToBeDeleted`. Der URI wird als `java.lang.String`-Objekt gespeichert. In diesem Beispiel wird die Ressource zuerst in das Repository geschrieben und ihr URI abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Ressource löschen

   Rufen Sie die `ResourceRepositoryClient`-Methode des Objekts `deleteResource` auf und übergeben Sie den URI der Ressource als Parameter.

**Siehe auch**

[Löschen von Ressourcen](aem-forms-repository.md#deleting-resources)

[Kurzanleitung (SOAP-Modus): Suchen nach Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Löschen von Ressourcen mithilfe der Webdienst-API {#delete-resources-using-the-web-service-api}

Löschen einer Ressource mithilfe der Repository-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, welche die Repository-WSDL mit Base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen des Service-Clients

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `RepositoryServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen. Legen Sie seine `Credentials`-Eigenschaft mit einem `System.Net.NetworkCredential`-Objekt fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der Ressource an, die gelöscht werden soll

   Geben Sie den URI der abzurufenden Ressource an. Da sich in diesem Fall die Ressource `testResourceToBeDeleted` in dem Ordner `testFolder` befindet, lautet ihr URI `"/testFolder/testResourceToBeDeleted"`. In diesem Beispiel wird die Ressource zuerst in das Repository geschrieben und ihr URI abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Ressource löschen

   Rufen Sie die `RepositoryServiceService`-Methode des Objekts `deleteResources` auf und übergeben Sie ein `System.String`-Array, das den URI der Ressource als ersten Parameter enthält. Übergeben Sie `null` als zweiten Parameter.

**Siehe auch**

[Löschen von Ressourcen](aem-forms-repository.md#deleting-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
