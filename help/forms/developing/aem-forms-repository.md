---
title: Arbeiten mit AEM Forms Repository
seo-title: Arbeiten mit AEM Forms Repository
description: 'null'
seo-description: 'null'
uuid: 6ead49f9-ca0d-4ee4-86a6-0a9ced6ec4f8
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d2c95881-6c02-4e34-85af-84607df54287
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Working with AEM Forms Repository {#working-with-aem-forms-repository}

**Informationen zum Repository-Dienst**

Der Repository-Dienst stellt Dienste zur Ressourcenspeicherung und -verwaltung für AEM Forms bereit. When developers create an *AEM Forms* application, they can deploy the assets in the repository instead of the file system. Die Elemente können alle Typen von Zusätzen umfassen, darunter XML-Formulare, PDF-Formulare (einschließlich Acrobat-Formularen), Formularfragmente, Bilder, Profile, Richtlinien, SWF-Dateien, DDX-Dateien, XML-Schemas, WSDL-Dateien und Testdaten.

Betrachten Sie zum Beispiel die folgende Forms-Anwendung mit dem Namen *Applications/FormsApplication*:

![ww_ww_formrepository](assets/ww_ww_formrepository.png)

Beachten Sie, dass sich im FormsFolder eine Datei mit dem Namen &quot;Loan.xdp&quot;befindet. Um auf diesen Formularentwurf zuzugreifen, geben Sie den vollständigen Pfad an (einschließlich Version): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Informationen zum Erstellen einer Forms-Anwendung mit Workbench finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63).

Der Pfad zu einer Ressource im AEM Forms-Repository lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Die folgenden Werte zeigen einige Beispiele für URI-Werte:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>Sie können das AEM Forms-Repository über einen Webbrowser durchsuchen. Um das Repository zu durchsuchen, geben Sie die folgende URL in einen Webbrowser ein https://[Servername]:[Serverport]/Repository. Mithilfe eines Webbrowsers können Sie die Ergebnisse für den Schnellstart überprüfen, die mit dem Abschnitt Arbeiten mit AEM Forms-Repository verknüpft sind. Wenn Sie beispielsweise Inhalte zum AEM Forms-Repository hinzufügen, können Sie den Inhalt in einem Webbrowser anzeigen. (See [Quick Start (SOAP mode): Writing a resource using the Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).)

Die Repository-API bietet eine Reihe von Vorgängen, mit denen Sie Informationen aus dem Repository speichern und abrufen können. Sie können beispielsweise eine Liste der Ressourcen abrufen oder spezifische Ressourcen abrufen, die im Repository gespeichert werden, wenn eine Ressource im Rahmen der Verarbeitung einer Anwendung benötigt wird.

>[!NOTE]
>
>Die Repository-API kann nicht für die Interaktion mit Content Services (nicht mehr unterstützt) verwendet werden. Für die Interaktion mit Content Services (nicht mehr unterstützt) verwenden Sie die Document Management-API.

Mithilfe der Repository-Dienst-API können Sie die folgenden Aufgaben ausführen:

* Erstellen von Ordnern. Siehe [Erstellen von Ordnern](aem-forms-repository.md#creating-folders).
* Schreiben Sie Ressourcen und ihre Eigenschaften. Siehe [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).
* Listet Ressourcen in einer bestimmten Sammlung oder in Verbindung mit anderen Ressourcen auf. Siehe [Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).
* Lesen Sie Ressourcen und ihre Eigenschaften. Siehe [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).
* Aktualisieren Sie Ressourcen und ihre Eigenschaften. Siehe [Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources).
* Suchen Sie nach Ressourcen, einschließlich ihres Verlaufs, der zugehörigen Ressourcen und Eigenschaften. Siehe [Suchen nach Ressourcen](aem-forms-repository.md#searching-for-resources).
* Legen Sie Beziehungen zwischen Ressourcen fest. Siehe [Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships).
* Verwalten Sie die Steuerung des Ressourcenzugriffs, einschließlich Sperren und Entsperren von Ressourcen sowie Lese- und Schreibzugriffssteuerungslisten (ACLs). Siehe [Sperren von Ressourcen](aem-forms-repository.md#locking-resources).
* Löschen Sie Ressourcen und ihre Eigenschaften. Siehe [Löschen von Ressourcen](aem-forms-repository.md#deleting-resources).

>[!NOTE]
>
>Mithilfe der Repository-API können Sie die Steuerung des Ressourcenzugriffs nicht verwalten, nach Ressourcen suchen oder mithilfe eines ECM-Repositorys Ressourcenbeziehungen angeben.

>[!NOTE]
>
>Wenn eine verschlüsselte PDF-Datei in das Repository geschrieben wird, kann die automatisierte Funktion zum Extrahieren von Beziehungen nicht verwendet werden. Andernfalls kann eine verschlüsselte PDF im Repository gespeichert und später abgerufen werden. Der Abruf kann die PDF entschlüsseln, nachdem sie aus dem Repository abgerufen wurde.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von Ordnern {#creating-folders}

Ordner (Ressourcensammlungen) werden zum Speichern von Objekten (Dateien oder Ressourcen) in organisierten Gruppierungen verwendet. Ordner können Ressourcen und andere Ordner enthalten, die auch als Unterordner bezeichnet werden. Ressourcen können jeweils nur in einem Ordner gespeichert werden.

Dateien übernehmen Zugriffssteuerungslisten (ACLs) aus Ordnern und Unterordner übernehmen ACLs aus ihren übergeordneten Ordnern. Daher müssen die übergeordneten Ordner vorhanden sein, bevor Sie untergeordnete Ordner erstellen können. Die IDE ermöglicht die Interaktion nur auf Ordner-für-Ordner-Basis, nicht auf Datei-für-Datei-Basis. Sie können keine Versionsordner erstellen, und dies ist nicht erforderlich. ein Ordner selbst keine Daten enthält. Vielmehr handelt es sich nur um einen Container für Ressourcen, die Daten enthalten. Die standardmäßige Zugriffsberechtigung für ACL ist auf Systemebene. Das bedeutet, dass Benutzer über Berechtigungen auf Systemebene verfügen müssen (Lese-, Schreib-, Durchlauf- und Verwaltungsberechtigungen), bis ihnen jemand Berechtigungen für einen bestimmten Ordner erteilt. ACLs funktionieren nur in der IDE.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um einen Ordner zu erstellen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie den Dienstclient.
1. Erstellen Sie den Ordner.
1. Schreiben Sie den Ordner in das Repository.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressourcensammlung programmgesteuert erstellen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Erstellen Sie den Ordner**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressourcensammlung zu erstellen und die Ressourcensammlung mit Identifizierungsinformationen wie UUID, Ordnername und Beschreibung zu füllen.

**Den Ordner in das Repository schreiben**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressourcensammlung zu schreiben und den URI des Zielordners anzugeben.

**Siehe auch**

[Erstellen von Ordnern mit der Java-API](aem-forms-repository.md#create-folders-using-the-java-api)

[Erstellen von Ordnern mit der Webdienst-API](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Erstellen von Ordnern mit der Java-API {#create-folders-using-the-java-api}

Erstellen Sie einen Ordner mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Projektdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Erstellen Sie den Ordner

   Um eine Ressourcensammlung zu erstellen, müssen Sie zunächst ein `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` Objekt erstellen.

   Rufen Sie die `repositoryInfomodelFactoryBean` Methode des `newResourceCollection` Objekts auf und übergeben Sie die folgenden Parameter:

   * Eine `com.adobe.repository.infomodel.Id` UID-ID, die der Ressource zugewiesen wird.
   * Eine `com.adobe.repository.infomodel.Lid` UID-ID, die der Ressource zugewiesen wird.
   * Eine `java.lang.String` mit dem Namen der Ressourcensammlung. Beispiel, `FormsFolder`.
   Die Methode gibt ein `com.adobe.repository.infomodel.bean.ResourceCollection` Objekt zurück, das den neuen Ordner darstellt.

   Legen Sie die Beschreibung des Ordners mithilfe der `setDescription` Methode fest und übergeben Sie den folgenden Parameter:

   * Eine `String` , die die Ressourcensammlung beschreibt. In diesem Beispiel `"test Folder"` wird `.`


1. Den Ordner in das Repository schreiben

   Rufen Sie die `ResourceRepositoryClient` Methode des `writeResource` Objekts auf und übergeben Sie den URI des Ordners und des `ResourceCollection` Objekts. Beispielsweise kann der URI für den Ordner der folgende Wert sein `/Applications/FormsApplication/1.0/`.

   Die Methode gibt eine Instanz des neu erstellten `com.adobe.repository.infomodel.bean.Resource` Objekts zurück. Sie können beispielsweise den Bezeichnerwert der neuen Ressource abrufen, indem Sie die `com.adobe.repository.infomodel.bean.Resource` Objektmethode `getId` aufrufen.

**Siehe auch**

[Erstellen von Ordnern](aem-forms-repository.md#creating-folders)

[Kurzanleitung (SOAP-Modus): Erstellen eines Ordners mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Ordnern mit der Webdienst-API {#create-folders-using-the-web-service-api}

Erstellen Sie einen Ordner mithilfe der Repository Service API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie ihre `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Erstellen Sie den Ordner

   Erstellen Sie den Ordner mit dem Standardkonstruktor für die `ResourceCollection` Klasse und übergeben Sie die folgenden Parameter:

   * Ein `Id` Objekt, das durch Aufrufen des Standardkonstruktors für die `Id` Klasse erstellt und dem `Resource` Objektfeld `id` zugewiesen wird.
   * Ein `Lid` Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid` Klasse erstellt und dem `Resource` Objektfeld `lid` zugewiesen wird.
   * Eine Zeichenfolge, die den Namen der Ressourcensammlung enthält, die dem `Resource` Objektfeld zugewiesen `name` wird. Der in diesem Beispiel verwendete Name lautet `"testfolder"`.
   * Eine Zeichenfolge, die die Beschreibung der Ressourcensammlung enthält, die dem `Resource` Objektfeld zugewiesen `description` ist. Die in diesem Beispiel verwendete Beschreibung lautet `"test folder"`.

1. Den Ordner in das Repository schreiben

   Rufen Sie die `RepositoryServiceService` Objektmethode `writeResource` auf und übergeben Sie die folgenden Parameter:

   * Der Pfad, in dem der Ordner erstellt werden soll.
   * Das `ResourceCollection` Objekt, das den Ordner darstellt.
   * Für `null` die anderen beiden Parameter übergeben.

**Siehe auch**

[Erstellen von Ordnern](aem-forms-repository.md#creating-folders)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen schreiben {#writing-resources}

Sie können Ressourcen an einem bestimmten Speicherort im Repository erstellen. Die natürliche Dateigröße unterliegt Datenbankbeschränkungen und Sitzungszeitlimit. Bei der Standardkonfiguration sind die Dateien auf 25 MB beschränkt. Um die maximale Dateigröße zu erhöhen oder zu verringern, müssen Sie die Datenbankkonfiguration ändern.

Das Schreiben von Ressourcen entspricht dem Speichern von Daten im Repository. Sobald Sie eine Ressource in das Repository schreiben, wird sie für alle Clients im Repository-Ökosystem verfügbar. Wenn Sie Ressourcen wie XML-Schemata, XDP-Dateien und XSD-Dateien in das Repository schreiben, werden die Inhalte basierend auf dem MIME-Typ analysiert. Wenn der MIME-Typ unterstützt wird, bestimmt der Parser, ob eine implizite Beziehung zu anderen Inhalten besteht. Wenn beispielsweise ein CSS (Cascading Stylesheet) über eine relative URL verfügt, die auf eine gängige CSS verweist, wird erwartet, dass Sie auch die allgemeine CSS in das Repository senden. Die Beziehung zwischen den beiden Ressourcen wird als ausstehende Beziehung für einen nicht anpassbaren Zeitraum von 30 Tagen gespeichert. Wenn Sie die allgemeine CSS innerhalb des Zeitraums von 30 Tagen an das Repository senden, wird die Beziehung aufgebaut.

Wenn Sie eine Ressource erstellen, wird die Zugriffssteuerungsliste (ACL) vom übergeordneten Ordner übernommen. Der Stammordner verfügt über Berechtigungen auf Systemebene, bis eine ursprüngliche Ressource oder ein anfänglicher Ordner erstellt wurde. An diesem Punkt erhält die Ressource oder der Ordner die standardmäßigen Zugriffsrechte für ACL.

Sie können Ressourcen programmgesteuert mit der Java-API des Repository-Dienstes oder der Webdienst-API schreiben.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Gehen Sie wie folgt vor, um eine Ressource zu schreiben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Geben Sie den URI der zu lesenden Ressource an.
1. Lesen Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Geben Sie den URI des Zielordners für die Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu lesenden Ressource enthält. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*folder*&quot;.

**Ressource erstellen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu erstellen, und füllen Sie die Ressource mit Identifizierungsinformationen wie UUID, Ressourcenname und Beschreibung.

**Ressourceninhalt angeben**

Rufen Sie die Methode des Repository-Dienstes auf, um Ressourceninhalte zu erstellen und diesen Inhalt in der Ressource zu speichern.

**Ressource in den Zielordner schreiben**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu schreiben und den URI des Zielordners anzugeben.

**Siehe auch**

[Ressourcen mit der Java-API schreiben](aem-forms-repository.md#write-resources-using-the-java-api)

[Schreiben von Ressourcen mit der Webdienst-API](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Ressourcen mit der Java-API schreiben {#write-resources-using-the-java-api}

Erstellen Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den URI des Zielordners für die Ressource an

   Geben Sie den URI des Zielordners für die Ressource an. In diesem Fall wird der URI des Ordners gespeichert, da die Ressource namens im Ordner `testResource`gespeichert `testFolder` wird `"/testFolder"`. Der URI wird als `java.lang.String` Objekt gespeichert.

1. Ressource erstellen

   Um eine Ressource zu erstellen, müssen Sie zunächst ein `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` Objekt erstellen.

   Rufen Sie die `RepositoryInfomodelFactoryBean` Methode des `newResource` Objekts auf, mit der ein `com.adobe.repository.infomodel.bean.Resource` Objekt erstellt wird. In diesem Beispiel werden die folgenden Parameter bereitgestellt:

   * Ein `com.adobe.repository.infomodel.Id` Objekt, das durch Aufrufen des Standardkonstruktors für die `Id` Klasse erstellt wird.
   * Ein `com.adobe.repository.infomodel.Lid` Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid` Klasse erstellt wird.
   * Eine `java.lang.String` Datei, die den Dateinamen der Ressource enthält.
   Um die Beschreibung der Ressource anzugeben, rufen Sie die `Resource` Methode des `setDescription` Objekts auf und übergeben Sie eine Zeichenfolge, die die Beschreibung enthält. In diesem Beispiel lautet die Beschreibung `"test resource"`.

1. Ressourceninhalt angeben

   Um Inhalte für die Ressource zu erstellen, rufen Sie die `RepositoryInfomodelFactoryBean` Methode des `newResourceContent` Objekts auf, die ein `com.adobe.repository.infomodel.bean.ResourceContent` Objekt zurückgibt. Add content to the `ResourceContent` object. In diesem Beispiel wird dies durch die folgenden Aufgaben erreicht:

   * Aufrufen der `ResourceContent` Objektmethode `setDataDocument` und Übergeben eines `com.adobe.idp.Document` Objekts
   * Aufrufen der `ResourceContent` Objektmethode `setSize` und Übergeben der Größe in Byte des `Document` Objekts
   Fügen Sie der Ressource den Inhalt hinzu, indem Sie die `Resource` Methode des `setContent` Objekts aufrufen und das `ResourceContent` Objekt übergeben. For more information, see [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Ressource in den Zielordner schreiben

   Rufen Sie die `ResourceRepositoryClient` Methode des `writeResource` Objekts auf und übergeben Sie den URI des Ordners sowie das `Resource` Objekt.

**Siehe auch**

[Ressourcen schreiben](aem-forms-repository.md#writing-resources)

[Kurzanleitung (SOAP-Modus): Schreiben einer Ressource mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Schreiben von Ressourcen mit der Webdienst-API {#write-resources-using-the-web-service-api}

Erstellen Sie eine Ressource mithilfe der Repository Service API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI des Zielordners für die Ressource an

   Geben Sie den URI des Zielordners für die Ressource an. In diesem Fall wird der URI des Ordners gespeichert, da die Ressource namens im Ordner `testResource`gespeichert `testFolder` wird `"/testFolder"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einem `System.String` Objekt.

1. Ressource erstellen

   Um eine Ressource zu erstellen, rufen Sie den Standardkonstruktor für die `Resource` Klasse auf. In diesem Beispiel werden die folgenden Informationen im `Resource` Objekt gespeichert:

   * Ein `com.adobe.repository.infomodel.Id` Objekt, das durch Aufrufen des Standardkonstruktors für die `Id` Klasse erstellt und dem `Resource` Objektfeld `id` zugewiesen wird.
   * Ein `com.adobe.repository.infomodel.Lid` Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid` Klasse erstellt und dem `Resource` Objektfeld `lid` zugewiesen wird.
   * Eine Zeichenfolge, die den Dateinamen der Ressource enthält, der dem `Resource` Objektfeld zugewiesen `name` wird. Der in diesem Beispiel verwendete Name lautet `"testResource"`.
   * Eine Zeichenfolge, die die Beschreibung der Ressource enthält, die dem `Resource` Objektfeld zugewiesen `description` ist. Die in diesem Beispiel verwendete Beschreibung lautet `"test resource"`.

1. Ressourceninhalt angeben

   Um Inhalte für die Ressource zu erstellen, rufen Sie den Standardkonstruktor für die `ResourceContent` Klasse auf. Fügen Sie dann dem `ResourceContent` Objekt Inhalt hinzu. In diesem Beispiel wird dies durch die folgenden Aufgaben erreicht:

   * Zuweisen eines `BLOB` Objekts, das ein Dokument enthält, zum `ResourceContent``dataDocument` Objektfeld.
   * Zuweisen der Größe in Byte des `BLOB` Objekts zum `ResourceContent` Objektfeld `size` .
   Fügen Sie der Ressource den Inhalt hinzu, indem Sie das `ResourceContent` Objekt dem `Resource` Objektfeld zuweisen `content` .

1. Ressource in den Zielordner schreiben

   Rufen Sie die `RepositoryServiceService` Methode des `writeResource` Objekts auf und übergeben Sie den URI des Ordners sowie das `Resource` Objekt. Für `null` die anderen beiden Parameter übergeben.

**Siehe auch**

[Ressourcen schreiben](aem-forms-repository.md#writing-resources)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen auflisten {#listing-resources}

Sie können Ressourcen entdecken, indem Sie Ressourcen auflisten. Für das Repository wird eine Abfrage durchgeführt, um alle Ressourcen zu finden, die mit einer bestimmten Ressourcensammlung zusammenhängen.

Nachdem Sie Ihre Ressourcen organisiert haben, können Sie die von Ihnen erstellte Struktur überprüfen, indem Sie einen bestimmten Zweig der Struktur sehen, ähnlich wie bei einem Betriebssystem.

Auflisten von Ressourcen funktioniert nach Beziehung: Ressourcen sind Mitglieder von Ordnern. Die Mitgliedschaft wird durch eine Beziehung des Typs &quot;Mitglied von&quot;repräsentiert. Wenn Sie Ressourcen in einem bestimmten Ordner auflisten, suchen Sie nach Ressourcen, die mit einem bestimmten Ordner durch die Beziehung &quot;Mitglied von&quot;zusammenhängen. Beziehungen sind in Richtung: Ein Mitglied einer Beziehung hat eine Quelle, die Mitglied des Ziels ist. Die Quelle ist die Ressource; das Ziel ist der übergeordnete Ordner.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Gehen Sie wie folgt vor, um Ressourcen aufzulisten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie den Dienstclient.
1. Geben Sie den Ordnerpfad an.
1. Rufen Sie die Liste der Ressourcen ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressourcensammlung programmgesteuert erstellen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Ordnerpfad angeben**

Erstellen Sie eine Zeichenfolge, die den Pfad des Ordners enthält, der die Ressourcen enthält. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*folder*&quot;.

**Rufen Sie die Liste der Ressourcen ab**

Rufen Sie die Methode des Repository-Dienstes auf, um die Liste der Ressourcen abzurufen, und geben Sie den Pfad des Zielordners an.

**Siehe auch**

[Ressourcen mit der Java-API auflisten](aem-forms-repository.md#list-resources-using-the-java-api)

[Ressourcen mit der Webdienst-API auflisten](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Ressourcen mit der Java-API auflisten {#list-resources-using-the-java-api}

Ressourcen mithilfe der Repository Service API (Java) auflisten:

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Ordnerpfad angeben

   Geben Sie den URI der zu abfragenden Ressourcensammlung an. In diesem Fall lautet der URI `"/testFolder"`. Der URI wird als `java.lang.String` Objekt gespeichert.

1. Rufen Sie die Liste der Ressourcen ab

   Rufen Sie die `ResourceRepositoryClient` Methode des `listMembers` Objekts auf und übergeben Sie den URI des Ordners.

   Die Methode gibt eine `java.util.List` von `com.adobe.repository.infomodel.bean.Resource` Objekten zurück, die die Quelle eines `com.adobe.repository.infomodel.bean.Relation` Typs sind `Relation.TYPE_MEMBER_OF` und deren Ziel der URI der Ressourcensammlung ist. Sie können dies durchlaufen, `List` um die einzelnen Ressourcen abzurufen. In diesem Beispiel werden der Name und die Beschreibung der einzelnen Ressourcen angezeigt.

**Siehe auch**

[Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).

[Kurzanleitung (SOAP-Modus): Auflisten von Ressourcen mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ressourcen mit der Webdienst-API auflisten {#list-resources-using-the-web-service-api}

Ressourcen mithilfe der Repository Service API (Webdienst) auflisten:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Ordnerpfad angeben

   Geben Sie eine Zeichenfolge an, die den URI des abzufragenden Ordners enthält. In diesem Fall lautet der URI `"/testFolder"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einem `System.String` Objekt.

1. Rufen Sie die Liste der Ressourcen ab

   Rufen Sie die `RepositoryServiceService` Methode des `listMembers` Objekts auf und übergeben Sie den URI des Ordners als ersten Parameter. Für `null` die anderen beiden Parameter übergeben.

   Die Methode gibt ein Array von Objekten zurück, die in `Resource` Objekte umgewandelt werden können. Sie können das Objektarray durchlaufen, um jede der zugehörigen Ressourcen abzurufen. In diesem Beispiel werden der Name und die Beschreibung der einzelnen Ressourcen angezeigt.

**Siehe auch**

[Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen lesen {#reading-resources}

Sie können Ressourcen von einem bestimmten Speicherort im Repository abrufen, um deren Inhalt und Metadaten zu lesen. Der Workflow wird durch ein Initialisierungsformular vorn beendet. Der Prozess verfügt über alle erforderlichen Berechtigungen zum Lesen des Formulars. Das System ruft das Datenformular ab und liest den Inhalt aus dem Repository. Das Repository gewährt Zugriff auf den Inhalt und die Metadaten (die Möglichkeit, die Ressource zu erkennen).

Das Repository verfügt über die folgenden vier Berechtigungstypen:

* **traverse**: ermöglicht die Auflistung von Ressourcen; zum Lesen von Ressourcenmetadaten, jedoch nicht von Ressourceninhalten
* **lautet**: ermöglicht Ihnen das Lesen von Ressourceninhalten
* **schreiben**: ermöglicht Ihnen das Schreiben von Ressourceninhalten
* **Verwaltung von Zugriffssteuerungslisten (ACLs)**: ermöglicht Ihnen die Bearbeitung von ACLs für Ressourcen

Benutzer können nur Prozesse ausführen, wenn sie über die Berechtigung zum Ausführen des Prozesses verfügen. IDE-Benutzer benötigen für die Synchronisierung mit dem Repository die Berechtigung zum Durchlaufen und Lesen. ACLs gelten nur zur Entwurfszeit, da die Laufzeit im Systemkontext erfolgt.

Sie können Ressourcen programmgesteuert mit der Java-API des Repository-Dienstes oder der Webdienst-API lesen.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Gehen Sie wie folgt vor, um eine Ressource zu lesen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Geben Sie den URI der zu lesenden Ressource an.
1. Lesen Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Geben Sie den URI der zu lesenden Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu lesenden Ressource enthält. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*resource*&quot;.

**Ressource lesen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu lesen, und geben Sie den URI an.

**Siehe auch**

[Ressourcen mithilfe der Java-API lesen](aem-forms-repository.md#read-resources-using-the-java-api)

[Lesen von Ressourcen mit der Webdienst-API](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Ressourcen mithilfe der Java-API lesen {#read-resources-using-the-java-api}

Lesen Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der zu lesenden Ressource an

   Geben Sie einen Zeichenfolgenwert an, der den URI der abzurufenden Ressource darstellt. Wenn die Ressource beispielsweise den Namen *testResource* hat, der sich in einem Ordner mit dem Namen *testFolder* befindet, geben Sie an, `/testFolder/testResource`.

1. Ressource lesen

   Rufen Sie die `ResourceRepositoryClient` Methode des `readResource` Objekts auf und übergeben Sie den URI der Ressource als Parameter. Diese Methode gibt eine `Resource` Instanz zurück, die die Ressource darstellt.

**Siehe auch**

[Ressourcen lesen](aem-forms-repository.md#reading-resources)

[Kurzanleitung (SOAP-Modus): Lesen einer Ressource mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Lesen von Ressourcen mit der Webdienst-API {#reading-resources-using-the-web-service-api}

Lesen Sie eine Ressource mithilfe der Repository Service API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet. (Siehe [Erstellen einer .NET-Client-Assembly, die Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)verwendet.)
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe [Erstellen einer .NET-Client-Assembly, die Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)verwendet.)

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der zu lesenden Ressource an

   Geben Sie eine Zeichenfolge an, die den URI der abzurufenden Ressource enthält. In diesem Fall lautet der URI des Felds, da sich die Ressource mit dem Namen `testResource` im Ordner `testFolder`befindet `"/testFolder/testResource"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einem `System.String` Objekt.

1. Ressource lesen

   Rufen Sie die `RepositoryServiceService` Methode des `readResource` Objekts auf und übergeben Sie den URI der Ressource als ersten Parameter. Für `null` die anderen beiden Parameter übergeben.

**Siehe auch**

[Ressourcen lesen](aem-forms-repository.md#reading-resources)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen aktualisieren {#updating-resources}

Sie können den Inhalt der Ressourcen im Repository abrufen und aktualisieren. Wenn Sie Ressourcen aktualisieren, bleibt die Zugriffssteuerung auf diese Ressourcen zwischen den Versionen unverändert. Bei der Ausführung einer Aktualisierung haben Sie die Möglichkeit, die Hauptversion zu erhöhen. Wenn Sie die Hauptversion nicht inkrementieren, wird die Nebenversion automatisch aktualisiert.

Wenn Sie eine Ressource aktualisieren, wird die neue Version basierend auf den angegebenen Ressourcenattributen erstellt. Wenn Sie eine Ressource aktualisieren, geben Sie zwei wichtige Parameter an: Ziel-URI und eine Ressourceninstanz, die alle aktualisierten Metadaten enthält. Beachten Sie, dass das Attribut bei keiner Änderung eines bestimmten Attributs (z. B. des Namens) in der von Ihnen übergebenen Instanz weiterhin erforderlich ist. Die Beziehungen, die beim Analysieren des Inhalts erstellt werden, werden der jeweiligen Version hinzugefügt und nur nach Angabe weitergeleitet.

Wenn Sie beispielsweise eine XDP-Datei aktualisieren und sie Verweise auf andere Ressourcen enthält, werden diese zusätzlichen Verweise ebenfalls aufgezeichnet. Angenommen, form.xdp Version 1.0 hat zwei externe Verweise: ein Logo und ein Stylesheet und Sie aktualisieren dann form.xdp, sodass es jetzt drei Verweise hat: ein Logo, ein Stylesheet und eine Schemadatei. Während der Aktualisierung fügt das Repository die dritte Beziehung (zur Schemadatei) zu seiner ausstehenden Beziehungstabelle hinzu. Sobald die Schemadatei im Repository vorhanden ist, wird die Beziehung automatisch aufgebaut. Wenn form.xdp Version 2.0 das Logo jedoch nicht mehr verwendet, hat form.xdp Version 2.0 keine Beziehung zum Logo.

Alle Aktualisierungsvorgänge sind atomar und transaktional. Wenn zum Beispiel zwei Benutzer dieselbe Ressource lesen und beide entscheiden, Version 1.0 auf Version 2.0 zu aktualisieren, wird einer von ihnen erfolgreich sein und einer von ihnen schlägt fehl, die Integrität des Repositorys wird gewahrt und beide erhalten eine Meldung, die den Erfolg oder Fehler bestätigt. Wenn die Transaktion nicht übernommen wird, wird sie bei einem Datenbankfehler zurückgesetzt und abhängig vom Anwendungsserver ein Timeout oder eine Rollback durchgeführt.

Sie können Ressourcen programmgesteuert mit der Java-API des Repository-Dienstes oder der Webdienst-API aktualisieren.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Gehen Sie wie folgt vor, um eine Ressource zu aktualisieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Rufen Sie die zu aktualisierende Ressource ab.
1. Aktualisieren Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Abrufen der zu aktualisierenden Ressource**

Lesen Sie die Ressource. Weitere Informationen finden Sie unter Ressourcen [lesen](aem-forms-repository.md#reading-resources).

**Ressource aktualisieren**

Legen Sie die neuen Informationen in der Ressource fest und rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu aktualisieren, geben Sie den URI, die aktualisierte Ressource und die Art und Weise an, wie die Versionsinformationen aktualisiert werden sollen.

**Siehe auch**

[Aktualisieren von Ressourcen mit der Java-API](aem-forms-repository.md#update-resources-using-the-java-api)

[Aktualisieren von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Aktualisieren von Ressourcen mit der Java-API {#update-resources-using-the-java-api}

Aktualisieren Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Abrufen der zu aktualisierenden Ressource

   Geben Sie den URI der Ressource an, die abgerufen und gelesen werden soll. In diesem Beispiel lautet der URI der Ressource `"/testFolder/testResource"`.

1. Ressource aktualisieren

   Aktualisieren Sie die Informationen des `Resource` Objekts. Um die Beschreibung in diesem Beispiel zu aktualisieren, rufen Sie die `Resource` Methode des `setDescription` Objekts auf und übergeben Sie die neue Zeichenfolge als Parameter.

   Rufen Sie dann die `ServiceClientFactory` Methode des `updateResource` Objekts auf und übergeben Sie die folgenden Parameter:

   * Ein `java.lang.String` Objekt, das den URI der Ressource enthält.
   * Das `Resource` Objekt, das die aktualisierten Ressourceninformationen enthält.
   * Ein `boolean` Wert, der angibt, ob die Haupt- oder Nebenversion aktualisiert werden soll. In diesem Beispiel `true` wird ein Wert von übergeben, der angibt, dass die Hauptversion inkrementiert werden soll.

**Siehe auch**

[Ressourcen aktualisieren](aem-forms-repository.md#updating-resources)

[Kurzanleitung (SOAP-Modus): Aktualisieren einer Ressource mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Aktualisieren von Ressourcen mithilfe der Webdienst-API {#update-resources-using-the-web-service-api}

Aktualisieren einer Ressource mithilfe der Repository API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Abrufen der zu aktualisierenden Ressource

   Geben Sie den URI der Ressource an, die abgerufen und gelesen werden soll. In diesem Beispiel lautet der URI der Ressource `"/testFolder/testResource"`. Weitere Informationen finden Sie unter Ressourcen [lesen](aem-forms-repository.md#reading-resources).

1. Ressource aktualisieren

   Aktualisieren Sie die Informationen des `Resource` Objekts. Um in diesem Beispiel die Beschreibung zu aktualisieren, weisen Sie dem `Resource` Objektfeld einen neuen Wert zu `description` .

1. Rufen Sie die `RepositoryServiceService` Methode des `updateResource` Objekts auf und übergeben Sie die folgenden Parameter:

   * Ein `System.String` Objekt, das den URI der Ressource enthält.
   * Das `Resource` Objekt, das die aktualisierten Ressourceninformationen enthält.
   * Ein `boolean` Wert, der angibt, ob die Haupt- oder Nebenversion aktualisiert werden soll. In diesem Beispiel `true` wird ein Wert von übergeben, der angibt, dass die Hauptversion inkrementiert werden soll.
   * Für `null` die verbleibenden beiden Parameter übergeben.

**Siehe auch**

[Ressourcen aktualisieren](aem-forms-repository.md#updating-resources)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Suchen nach Ressourcen {#searching-for-resources}

Sie können Abfragen erstellen, die zum Suchen nach Ressourcen im Repository verwendet werden, einschließlich Verlauf, zugehörige Ressourcen und Eigenschaften.

Sie können zugehörige Ressourcen abrufen, um Abhängigkeiten zwischen einem Formular und seinen Fragmenten zu ermitteln. Wenn Sie beispielsweise ein Formular haben, können Sie festlegen, welche Fragmente oder externen Ressourcen es verwendet. Wenn Sie ein Bild haben, können Sie auch herausfinden, welche Formulare das Bild verwenden. Sie können auch anhand von Eigenschaften nach verwandten Ressourcen suchen. Sie können beispielsweise nach allen Formularen suchen, die ein Bild mit einem angegebenen Namen verwenden, oder nach jedem Bild, das von einem Formular mit einem angegebenen Namen verwendet wird. Sie können auch mithilfe der Ressourceneigenschaften suchen. Beispielsweise können Sie eine Abfrage durchführen, um alle Formulare oder Ressourcen zu finden, deren Name mit einer angegebenen Zeichenfolge beginnt, die &quot;%&quot;und &quot;_&quot;enthalten kann. Denken Sie daran, dass Suchvorgänge, die auf Eigenschaften basieren, nicht auf Beziehungen basieren; Diese Suchvorgänge basieren auf der Annahme, dass Sie über spezifische Kenntnisse zu einer bestimmten Ressource verfügen.

**Abfrageanweisungen**

Eine *Abfrage* enthält eine oder mehrere Anweisungen, die logisch mit Bedingungen verbunden sind. Eine *Anweisung* besteht aus einem linken Operanden, einem Operator und einem rechten Operanden. Darüber hinaus können Sie die Sortierreihenfolge für die Suchergebnisse festlegen. Die *Sortierreihenfolge* enthält Informationen, die einer SQL- `ORDER BY` Klausel entsprechen, und besteht aus Elementen, die die Attribute enthalten, auf denen die Suche basiert, sowie einem Wert, der angibt, ob eine aufsteigende oder absteigende Reihenfolge verwendet werden soll.

Sie können mithilfe der Java-API des Repository-Dienstes programmgesteuert nach Ressourcen suchen. Derzeit ist es nicht möglich, die Web-Service-API für die Suche nach Ressourcen zu verwenden.

**Sortierverhalten**

Die Sortierreihenfolge wird nicht berücksichtigt, wenn die `ResourceRepositoryClient` Objektmethode aufgerufen und eine Sortierreihenfolge angegeben `searchProperties` wird. Angenommen, Sie erstellen eine Ressource mit drei benutzerdefinierten Eigenschaften, bei denen die Attributnamen `name`, `secondName`und `asecondName`. Als Nächstes erstellen Sie ein Element für die Sortierreihenfolge im Attributnamen und legen den `ascending` Wert auf `true`.

Dann rufen Sie die `ResourceRepositoryClient` Objektmethode auf und übergeben die `searchProperties` Sortierreihenfolge. Die Suche gibt die richtige Ressource mit den drei Eigenschaften zurück. Die Eigenschaften werden jedoch nicht nach Attributnamen sortiert. Sie werden in der Reihenfolge zurückgegeben, in der sie hinzugefügt wurden: `name`, `secondName`und `asecondName`.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Gehen Sie wie folgt vor, um nach Ressourcen zu suchen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Geben Sie den Zielordner für die Suche an.
1. Geben Sie die Attribute an, die bei der Suche verwendet werden.
1. Erstellen Sie die bei der Suche verwendete Abfrage.
1. Erstellen Sie die Sortierreihenfolge für die Suchergebnisse.
1. Suchen Sie nach den Ressourcen.
1. Rufen Sie die Ressourcen aus dem Suchergebnis ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Geben Sie den Zielordner für die Suche an**

Erstellen Sie eine Zeichenfolge, die den Basispfad enthält, aus dem die Suche durchgeführt werden soll. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*folder*&quot;.

**Geben Sie die Attribute an, die bei der Suche verwendet werden**

Sie können Ihre Suche auf den Attributen in den Ressourcen aufbauen. Geben Sie die Werte der Attribute an, auf denen die Suche durchgeführt werden soll.

**Erstellen der bei der Suche verwendeten Abfrage**

Erstellen Sie eine Abfrage mithilfe von Anweisungen und Bedingungen. Jede Anweisung gibt das Attribut an, auf dem die Suche basieren soll, die zu verwendende Bedingung und den bei der Suche zu verwendenden Attributwert.

**Erstellen der Sortierreihenfolge für die Suchergebnisse**

Die Sortierreihenfolge besteht aus Elementen, von denen jedes eines der Attribute enthält, die bei der Suche verwendet werden, sowie einem Wert, der angibt, ob die Reihenfolge aufsteigend oder absteigend ist.

**Ressourcen suchen**

Suchen Sie mithilfe des Ordners, der Abfrage und der Sortierreihenfolge nach Ressourcen. Geben Sie außerdem die Suchtiefe und eine Obergrenze für die Anzahl der zurückzugebenden Ergebnisse an.

**Ressourcen aus dem Suchergebnis abrufen**

Durchsuchen Sie die zurückgegebene Liste der Ressourcen und extrahieren Sie die Informationen zur weiteren Verarbeitung.

**Siehe auch**

[Ressourcen mit der Java-API suchen](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Ressourcen mit der Java-API suchen {#search-for-resources-using-the-java-api}

Suchen Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den Zielordner für die Suche an

   Geben Sie den URI des Basispfades an, aus dem die Suche ausgeführt werden soll. In diesem Beispiel lautet der URI der Ressource `/testFolder`.

1. Geben Sie die Attribute an, die bei der Suche verwendet werden

   Geben Sie die Werte für die Attribute an, auf denen die Suche durchgeführt werden soll. Die Attribute befinden sich in einem `com.adobe.repository.infomodel.bean.Resource` Objekt. In diesem Beispiel wird die Suche mit dem Attribut name durchgeführt. Daher wird ein `java.lang.String` mit dem Namen des `Resource` Objekts verwendet, was in diesem `testResource` Fall der Fall ist.

1. Erstellen der bei der Suche verwendeten Abfrage

   Um eine Abfrage zu erstellen, erstellen Sie ein `com.adobe.repository.query.Query` Objekt, indem Sie den Standardkonstruktor für die `Query` Klasse aufrufen und der Abfrage Anweisungen hinzufügen.

   Um eine Anweisung zu erstellen, rufen Sie den Konstruktor für die `com.adobe.repository.query.Query.Statement` Klasse auf und übergeben Sie die folgenden Parameter:

   * Ein linker Operand, der die Konstante für das Ressourcenattribut enthält. In diesem Beispiel wird der statische Wert verwendet, da der Name der Ressource als Grundlage für die Suche verwendet `Resource.ATTRIBUTE_NAME` wird.
   * Ein Operator, der die bei der Suche nach dem Attribut verwendete Bedingung enthält. Der Operator muss eine der statischen Konstanten in der `Query.Statement` Klasse sein. In diesem Beispiel `Query.Statement.OPERATOR_BEGINS_WITH` wird der statische Wert verwendet.
   * Ein rechter Operand mit dem Attributwert, auf dem die Suche durchgeführt werden soll. In diesem Beispiel wird das Attribut name verwendet, ein Attribut, das den Wert `String` enthält `"testResource"`.
   Geben Sie den Namespace des linken Operanden an, indem Sie die `Query.Statement` Methode des `setNamespace` Objekts aufrufen und einen der statischen Werte in der `com.adobe.repository.infomodel.bean.ResourceProperty` Klasse übergeben. In diesem Beispiel `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY` wird verwendet.

   Fügen Sie der Abfrage jede Anweisung hinzu, indem Sie die `Query` Methode des `addStatement` Objekts aufrufen und das `Query.Statement` Objekt übergeben.

1. Erstellen der Sortierreihenfolge für die Suchergebnisse

   Um die in den Suchergebnissen verwendete Sortierreihenfolge festzulegen, erstellen Sie ein `com.adobe.repository.query.sort.SortOrder` Objekt, indem Sie den Standardkonstruktor für die `SortOrder` Klasse aufrufen und der Sortierreihenfolge Elemente hinzufügen.

   Um ein Element für die Sortierreihenfolge zu erstellen, rufen Sie einen der Konstruktoren für die `com.adobe.repository.query.sort.SortOrder.Element` Klasse auf. In diesem Beispiel `Resource.ATTRIBUTE_NAME` wird der statische Wert als erster Parameter verwendet, da der Name der Ressource als Grundlage für die Suche verwendet wird, und die aufsteigende Reihenfolge (ein `boolean` Wert von `true`) als zweiter Parameter angegeben.

   Fügen Sie jedes Element zur Sortierreihenfolge hinzu, indem Sie die `SortOrder` Methode des `addSortElement` Objekts aufrufen und das `SortOrder.Element` Objekt übergeben.

1. Ressourcen suchen

   Um nach `resources` anhand von Attributeigenschaften zu suchen, rufen Sie die `ResourceRepositoryClient` `searchProperties` Objektmethode auf und geben Sie die folgenden Parameter ein:

   * Eine `String` Datei, die den Basispfad enthält, aus dem die Suche ausgeführt werden soll. In diesem Fall wird `"/testFolder"` verwendet.
   * Die bei der Suche verwendete Abfrage.
   * Die Suchtiefe. In diesem Fall `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` wird angegeben, dass der Basispfad und alle zugehörigen Ordner verwendet werden sollen.
   * Ein `int` Wert, der die erste Zeile angibt, aus der die nicht paginierte Ergebnismenge ausgewählt werden soll. In diesem Beispiel `0` wird angegeben.
   * Ein `int` Wert, der die maximale Anzahl der zurückzugebenden Ergebnisse angibt. In diesem Beispiel `10` wird angegeben.
   * Die bei der Suche verwendete Sortierreihenfolge.
   Die Methode gibt eine `java.util.List` von `Resource` Objekten in der angegebenen Sortierreihenfolge zurück.

1. Ressourcen aus dem Suchergebnis abrufen

   Um die im Suchergebnis enthaltenen Ressourcen abzurufen, durchlaufen Sie den Bericht `List` und konvertieren Sie jedes Objekt in ein `Resource` , um die Informationen zu extrahieren. In diesem Beispiel wird der Name der einzelnen Ressourcen angezeigt.

**Siehe auch**

[Suchen nach Ressourcen](aem-forms-repository.md#searching-for-resources)

[Kurzanleitung (SOAP-Modus): Suchen nach Ressourcen mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von Ressourcenbeziehungen {#creating-resource-relationships}

Sie können Beziehungen zwischen Ressourcen im Repository angeben. Es gibt drei Arten von Beziehungen:

* **Abhängigkeit**: eine Beziehung, in der eine Ressource von anderen Ressourcen abhängt, d. h. alle zugehörigen Ressourcen werden im Repository benötigt.
* **Mitgliedschaft (Dateisystem)**: eine Beziehung, in der sich eine Ressource innerhalb eines angegebenen Ordners befindet.
* **Benutzerdefiniert**: eine Beziehung, die Sie zwischen Ressourcen angeben. Wenn beispielsweise eine Ressource nicht mehr unterstützt und eine andere in das Repository eingefügt wurde, können Sie Ihre eigene Ersatzbeziehung angeben.

Sie können eigene benutzerspezifische Beziehungen erstellen. Wenn Sie beispielsweise eine HTML-Datei im Repository speichern und sie ein Bild verwendet, können Sie eine benutzerspezifische Beziehung angeben, um die HTML-Datei mit dem Bild zu verknüpfen (da normalerweise nur XML-Dateien mit Bildern verknüpft werden, die eine durch das Repository definierte Abhängigkeitsbeziehung verwenden). Ein weiteres Beispiel für eine benutzerspezifische Beziehung wäre, wenn Sie eine andere Ansicht des Repositorys mit einer zyklischen Diagrammstruktur anstelle einer Baumstruktur erstellen möchten. Sie können ein Kreisdiagramm zusammen mit einem Viewer definieren, um diese Beziehungen zu durchlaufen. Schließlich könnten Sie angeben, dass eine Ressource eine andere Ressource ersetzt, auch wenn die beiden Ressourcen völlig unterschiedlich sind. In diesem Fall können Sie einen Beziehungstyp außerhalb des reservierten Bereichs definieren und eine Beziehung zwischen diesen beiden Ressourcen herstellen. Ihre Anwendung wäre der einzige Client, der die Beziehung erkennen und verarbeiten könnte, und könnte zur Durchführung von Suchvorgängen zu dieser Beziehung verwendet werden.

Sie können Beziehungen zwischen Ressourcen programmgesteuert angeben, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Gehen Sie wie folgt vor, um eine Beziehung zwischen zwei Ressourcen festzulegen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen.
1. Erstellen Sie die Beziehung.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Geben Sie die URIs der zu verknüpfenden Ressourcen an**

Erstellen Sie Zeichenfolgen, die die URIs der Ressource enthalten, die zugeordnet werden soll. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*resource*&quot;.

**Beziehung erstellen**

Rufen Sie die Methode des Repository-Dienstes auf, um den Beziehungstyp zu erstellen und anzugeben.

**Siehe auch**

[Erstellen von Beziehungsressourcen mit der Java-API](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Erstellen von Beziehungsressourcen mit der Webdienst-API](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Erstellen von Beziehungsressourcen mit der Java-API {#create-relationship-resources-using-the-java-api}

Erstellen Sie Beziehungsressourcen mithilfe der Java-API des Repository-Dienstes:

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie die URIs der zu verknüpfenden Ressourcen an

   Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen. In diesem Fall sind die URIs, da die Ressourcen benannt `testResource1` und `testResource2` sich im Ordner mit dem Namen befinden `testFolder`, `"/testFolder/testResource1"` und `"/testFolder/testResource2"`. Die URIs werden als `java.lang.String` Objekte gespeichert. In diesem Beispiel werden die Ressourcen zuerst in das Repository geschrieben und ihre URIs abgerufen. Weitere Informationen zum Erstellen einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Beziehung erstellen

   Rufen Sie die `ResourceRepositoryClient` Objektmethode `createRelationship` auf und übergeben Sie die folgenden Parameter:

   * Der URI der Quellressource.
   * Der URI der Zielressource.
   * Der Beziehungstyp, der eine der statischen Konstanten in der `com.adobe.repository.infomodel.bean.Relation` Klasse ist. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch Angabe des Werts festgelegt `Relation.TYPE_DEPENDANT_OF`.
   * Ein `boolean` Wert, der angibt, ob die Zielressource automatisch auf den `com.adobe.repository.infomodel.Id`basierten Bezeichner der neuen Kopfressource aktualisiert wird. In diesem Beispiel `true` wird der Wert aufgrund der Abhängigkeitsbeziehung angegeben.
   Sie können auch eine Liste der zugehörigen Ressourcen für eine bestimmte Ressource abrufen, indem Sie die `ResourceRepositoryClient` `getRelated` Objektmethode aufrufen und die folgenden Parameter übergeben:

   * Der URI der Ressource, für die zugehörige Ressourcen abgerufen werden sollen. In diesem Beispiel wird die Quellressource ( `"/testFolder/testResource1"`) angegeben.
   * Ein `boolean` Wert, der angibt, ob die angegebene Ressource die Quellressource in der Beziehung ist. In diesem Beispiel `true` wird der Wert angegeben, da dies der Fall ist.
   * Der Beziehungstyp, der eine der statischen Konstanten in der `Relation` Klasse ist. In diesem Beispiel wird eine Abhängigkeit angegeben, indem der gleiche Wert wie zuvor verwendet wird: `Relation.TYPE_DEPENDANT_OF`.
   Die `getRelated` Methode gibt eine Reihe `java.util.List` von `Resource` Objekten zurück, über die Sie die zugehörigen Ressourcen iterieren können, wobei Sie die im `List` Abschnitt enthaltenen Objekte während des `Resource` Vorgangs in die entsprechenden Objekte umwandeln. In diesem Beispiel `testResource2` wird erwartet, dass sie in der Liste der zurückgegebenen Ressourcen enthalten ist.

**Siehe auch**

[Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships)

[Kurzanleitung (SOAP-Modus): Beziehungen zwischen Ressourcen mithilfe der Java-API erstellen](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Beziehungsressourcen mit der Webdienst-API {#create-relationship-resources-using-the-web-service-api}

Erstellen Sie Beziehungsressourcen mithilfe der Repository API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie die URIs der zu verknüpfenden Ressourcen an

   Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen. In diesem Fall sind die URIs, da die Ressourcen benannt `testResource1` und `testResource2` sich im Ordner mit dem Namen befinden `testFolder`, `"/testFolder/testResource1"` und `"/testFolder/testResource2"`. Bei Verwendung einer Sprache, die Microsoft .NET Framework entspricht (z. B. C#), werden die URIs als `System.String` Objekte gespeichert. In diesem Beispiel werden die Ressourcen zuerst in das Repository geschrieben und ihre URIs abgerufen. Weitere Informationen zum Erstellen einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Beziehung erstellen

   Rufen Sie die `RepositoryServiceService` Objektmethode `createRelationship` auf und übergeben Sie die folgenden Parameter:

   * Der URI der Quellressource.
   * Der URI der Zielressource.
   * Die Art der Beziehung. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch Angabe des Werts festgelegt `3`.
   * Ein `boolean` Wert, der angibt, ob der Beziehungstyp angegeben wurde. In diesem Beispiel `true` wird der Wert angegeben.
   * Ein `boolean` Wert, der angibt, ob die Zielressource automatisch auf den `Id`basierten Bezeichner der neuen Kopfressource aktualisiert wird. In diesem Beispiel `true` wird der Wert aufgrund der Abhängigkeitsbeziehung angegeben.
   * Ein `boolean` Wert, der angibt, ob der Zielkopf angegeben wurde. In diesem Beispiel `true` wird der Wert angegeben.
   * Für `null` den letzten Parameter übergeben.
   Sie können auch eine Liste der zugehörigen Ressourcen für eine bestimmte Ressource abrufen, indem Sie die `RepositoryServiceService` `getRelated` Objektmethode aufrufen und die folgenden Parameter übergeben:

   * Der URI der Ressource, für die zugehörige Ressourcen abgerufen werden sollen. In diesem Beispiel wird die Quellressource ( `"/testFolder/testResource1"`) angegeben.
   * Ein `boolean` Wert, der angibt, ob die angegebene Ressource die Quellressource in der Beziehung ist. In diesem Beispiel `true` wird der Wert angegeben, da dies der Fall ist.
   * Ein `boolean` Wert, der angibt, ob die Quellressource angegeben wurde. In diesem Beispiel `true` wird der Wert angegeben.
   * Ein Array von Ganzzahlen, das die Beziehungstypen enthält. In diesem Beispiel wird eine Abhängigkeitsbeziehung angegeben, indem der gleiche Wert im Array wie zuvor verwendet wird: `3`.
   * Für `null` die verbleibenden beiden Parameter übergeben.
   Die `getRelated` Methode gibt ein Array von Objekten zurück, die in `Resource` Objekte umgewandelt werden können, über die Sie die zugehörigen Ressourcen abrufen können. In diesem Beispiel `testResource2` wird erwartet, dass sie in der Liste der zurückgegebenen Ressourcen enthalten ist.

**Siehe auch**

[Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen sperren {#locking-resources}

Sie können eine Ressource oder einen Satz von Ressourcen sperren, um sie exklusiv von einem bestimmten Benutzer oder für mehrere Benutzer freizugeben. Ein freigegebenes Schloss ist ein Hinweis darauf, dass mit der Ressource etwas passieren wird, aber es hindert niemanden daran, mit dieser Ressource zu handeln. Eine freigegebene Sperre sollte als Signalmechanismus betrachtet werden. Ein exklusives Sperren bedeutet, dass der Benutzer, der die Ressource gesperrt hat, die Ressource ändern wird, und das Schloss stellt sicher, dass niemand anders dies tun kann, bis der Benutzer keinen Zugriff mehr auf die Ressource benötigt und die Sperre aufgehoben hat. Wenn ein Repository-Administrator eine Ressource entsperrt, werden alle exklusiven und freigegebenen Sperren für diese Ressource automatisch entfernt. Diese Aktion ist für Situationen gedacht, in denen ein Benutzer nicht mehr verfügbar ist und die Ressource nicht entsperrt hat.

Wenn eine Ressource gesperrt ist, wird beim Anzeigen der Registerkarte &quot;Ressourcen&quot;in Workbench ein Sperrsymbol angezeigt, wie in der folgenden Abbildung dargestellt.

![lr_lr_lockrepository](assets/lr_lr_lockrepository.png)

Sie können den Zugriff auf Ressourcen programmgesteuert über die Java-API oder die Webdienst-API des Repository-Dienstes steuern.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Gehen Sie wie folgt vor, um Ressourcen zu sperren und zu entsperren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Geben Sie den URI der zu sperrenden Ressource an.
1. Sperren Sie die Ressource.
1. Rufen Sie die Sperren für die Ressource ab.
1. Ressource entsperren

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Geben Sie den URI der zu sperrenden Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu sperrenden Ressource enthält. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*resource*&quot;.

**Ressource sperren**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu sperren, und geben Sie den URI, den Sperrtyp und die Sperrtiefe an.

**Sperren der Ressource abrufen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Sperren für die Ressource abzurufen, und geben Sie den URI an.

**Ressource entsperren**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu entsperren, und geben Sie den URI an.

**Siehe auch**

[Sperren von Ressourcen mithilfe der Java-API](aem-forms-repository.md#lock-resources-using-the-java-api)

[Sperren von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Sperren von Ressourcen mithilfe der Java-API {#lock-resources-using-the-java-api}

Sperren Sie Ressourcen mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der zu sperrenden Ressource an

   Geben Sie den URI der zu sperrenden Ressource an. In diesem Fall lautet der URI des Felds, da sich die Ressource mit dem Namen `testResource` im Ordner `testFolder`befindet `"/testFolder/testResource"`. Der URI wird als `java.lang.String` Objekt gespeichert.

1. Ressource sperren

   Rufen Sie die `ResourceRepositoryClient` Objektmethode `lockResource` auf und übergeben Sie die folgenden Parameter:

   * Der URI der Ressource.
   * Der Sperrbereich. In diesem Beispiel wird der Sperrbereich als `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE`&quot;Sperrbereich&quot;festgelegt, da die Ressource für die ausschließliche Verwendung gesperrt wird.
   * Die Sperrtiefe. Da die Sperrung in diesem Beispiel nur für die jeweilige Ressource und nicht für deren Mitglieder oder untergeordnete Elemente gilt, wird die Sperrtiefe als `Lock.DEPTH_ZERO`.
   >[!NOTE]
   >
   >Die überladene Version der `lockResource` Methode, die vier Parameter erfordert, gibt eine Ausnahme aus. Stellen Sie sicher, dass Sie die `lockResource` Methode verwenden, für die drei Parameter erforderlich sind, wie in dieser exemplarischen Vorgehensweise gezeigt.

1. Sperren der Ressource abrufen

   Rufen Sie die `ResourceRepositoryClient` Methode des `getLocks` Objekts auf und übergeben Sie den URI der Ressource als Parameter. Die Methode gibt eine Liste von Sperrobjekten zurück, über die Sie iterieren können. In diesem Beispiel werden der Sperreneigentümer, die Sperrtiefe und der Umfang für jedes Objekt gedruckt, indem jeweils die `getOwnerUserId`-, `getDepth`und `getType` -methoden der Sperrobjekte aufgerufen werden.

1. Ressource entsperren

   Rufen Sie die `ResourceRepositoryClient` Methode des `unlockResource` Objekts auf und übergeben Sie den URI der Ressource als Parameter. Weitere Informationen finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Siehe auch**

[Ressourcen sperren](aem-forms-repository.md#locking-resources)

[Kurzanleitung (SOAP-Modus): Sperren einer Ressource mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Sperren von Ressourcen mithilfe der Webdienst-API {#lock-resources-using-the-web-service-api}

Sperren Sie Ressourcen mithilfe der Repository Service API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit Base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der zu sperrenden Ressource an

   Geben Sie eine Zeichenfolge an, die den URI der zu sperrenden Ressource enthält. In diesem Fall ist der URI des Felds, da sich die Ressource mit dem Namen `testResource` im Ordner befindet `testFolder`, `"/testFolder/testResource"`vorhanden. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einem `System.String` Objekt.

1. Ressource sperren

   Rufen Sie die `RepositoryServiceService` Objektmethode `lockResource` auf und übergeben Sie die folgenden Parameter:

   * Der URI der Ressource.
   * Der Sperrbereich. In diesem Beispiel wird der Sperrbereich als `11`&quot;Sperrbereich&quot;festgelegt, da die Ressource für die ausschließliche Verwendung gesperrt wird.
   * Die Sperrtiefe. Da die Sperrung in diesem Beispiel nur für die jeweilige Ressource und nicht für deren Mitglieder oder untergeordnete Elemente gilt, wird die Sperrtiefe als `2`.
   * Ein `int` Wert, der die Anzahl der Sekunden angibt, bis die Sperre abläuft. In diesem Beispiel wird der Wert von verwendet `1000` .
   * Für `null` den letzten Parameter übergeben.

1. Sperren der Ressource abrufen

   Rufen Sie die `RepositoryServiceService` Methode des `getLocks` Objekts auf und übergeben Sie den URI der Ressource als ersten Parameter und `null` als zweiten Parameter. Die Methode gibt ein `object` Array mit `Lock` Objekten zurück, durch die Sie iterieren können. In diesem Beispiel werden der Inhaber der Sperre, die Tiefe und der Umfang für jedes Objekt gedruckt, indem auf die Felder `Lock`, `ownerUserId`und `depth` `type` Felder jedes Objekts zugegriffen wird.

1. Ressource entsperren

   Rufen Sie die `RepositoryServiceService` Methode des `unlockResource` Objekts auf und übergeben Sie den URI der Ressource als ersten Parameter und `null` als zweiten Parameter.

**Siehe auch**

[Ressourcen sperren](aem-forms-repository.md#locking-resources)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Löschen von Ressourcen {#deleting-resources}

Sie können Ressourcen programmgesteuert über die Java-API (SOAP) des Repository-Dienstes löschen.

Wenn Sie eine Ressource löschen, ist der Löschvorgang normalerweise dauerhaft, in einigen Fällen können jedoch ECM-Repositorys die Versionen der Ressource gemäß ihren Verlaufsmechanismen speichern. Daher ist es beim Löschen einer Ressource wichtig sicherzustellen, dass Sie diese Ressource nie mehr benötigen. Häufige Gründe für das Löschen einer Ressource sind die Notwendigkeit, den verfügbaren Speicherplatz in der Datenbank zu erhöhen. Sie können eine Version einer Ressource löschen. Wenn Sie dies tun, müssen Sie jedoch die Ressourcenkennung und nicht deren logische ID (LID) oder Pfad angeben. Wenn Sie einen Ordner löschen, werden alle darin enthaltenen Ordner, einschließlich Unterordner und Ressourcen, automatisch gelöscht.

Zugehörige Ressourcen werden nicht gelöscht. Wenn Sie beispielsweise ein Formular mit der Datei &quot;logo.gif&quot;haben und &quot;logo.gif&quot;löschen, wird eine Beziehung in der Tabelle für die ausstehende Beziehung gespeichert. Alternativ können Sie bei veralteter Version den Objektstatus der neuesten Version auf veraltet setzen.

Ein Löschvorgang ist in ECM-Systemen nicht transaktionssicher. Wenn Sie beispielsweise versuchen, 100 Ressourcen zu löschen und der Vorgang bei der 50. Ressource fehlschlägt, werden die ersten 49 Instanzen gelöscht, der Rest jedoch nicht. Andernfalls lautet das Standardverhalten &quot;Rollback&quot;(Nicht-Verpflichtung).

>[!NOTE]
>
>Bei Verwendung der `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()` Methode mit dem ECM-Repository (EMC Documentum Content Server und IBM FileNet P8 Content Manager) wird die Transaktion nicht rückgängig gemacht, wenn der Löschvorgang bei einer der angegebenen Ressourcen fehlschlägt. Dies bedeutet, dass gelöschte Dateien nicht gelöscht werden können.

>[!NOTE]
>
>For more information about the Repository service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Gehen Sie wie folgt vor, um eine Ressource zu löschen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Repository-Dienstes.
1. Geben Sie den URI der zu löschenden Ressource an.
1. Löschen Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Dienstclients erreicht.

**Geben Sie den URI der zu löschenden Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu löschenden Ressource enthält. Die Syntax enthält Schrägstriche, wie im folgenden Beispiel: &quot;/*path*/*resource*&quot;. Wenn die zu löschende Ressource ein Ordner ist, wird der Löschvorgang rekursiv ausgeführt.

**Ressource löschen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu löschen, und geben Sie den URI an.

**Siehe auch**

[Ressourcen mithilfe der Java-API löschen](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Löschen von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Ressourcen mithilfe der Java-API(SOAP) löschen {#delete-resources-using-the-java-api-soap}

Löschen Sie eine Ressource mithilfe der Repository API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie ein `ResourceRepositoryClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der zu löschenden Ressource an

   Geben Sie den URI der abzurufenden Ressource an. Da sich die Ressource testResourceToBeDeleted in dem Ordner testFolder befindet, wird deren URI `/testFolder/testResourceToBeDeleted`verwendet. Der URI wird als `java.lang.String` Objekt gespeichert. In diesem Beispiel wird die Ressource zuerst in das Repository geschrieben und der zugehörige URI abgerufen. Weitere Informationen zum Erstellen einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Ressource löschen

   Rufen Sie die `ResourceRepositoryClient` Methode des `deleteResource` Objekts auf und übergeben Sie den URI der Ressource als Parameter.

**Siehe auch**

[Löschen von Ressourcen](aem-forms-repository.md#deleting-resources)

[Kurzanleitung (SOAP-Modus): Suchen nach Ressourcen mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Löschen von Ressourcen mithilfe der Webdienst-API {#delete-resources-using-the-web-service-api}

Löschen Sie eine Ressource mithilfe der Repository API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit Base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Clientassembly ein `RepositoryServiceService` Objekt, indem Sie dessen Standardkonstruktor aufrufen. Legen Sie seine `Credentials` Eigenschaft mithilfe eines `System.Net.NetworkCredential` Objekts fest, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der zu löschenden Ressource an

   Geben Sie den URI der abzurufenden Ressource an. In diesem Fall lautet der URI des Felds, da sich die Ressource mit dem Namen `testResourceToBeDeleted` im Ordner `testFolder`befindet `"/testFolder/testResourceToBeDeleted"`. In diesem Beispiel wird die Ressource zuerst in das Repository geschrieben und der zugehörige URI abgerufen. Weitere Informationen zum Erstellen einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Ressource löschen

   Rufen Sie die `RepositoryServiceService` Methode des `deleteResources` Objekts auf und übergeben Sie ein `System.String` Array, das den URI der Ressource als ersten Parameter enthält. Für `null` den zweiten Parameter übergeben.

**Siehe auch**

[Löschen von Ressourcen](aem-forms-repository.md#deleting-resources)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
