---
title: Erstellen oder konfigurieren Sie einen überwachten Ordner
seo-title: Erstellen oder konfigurieren Sie einen überwachten Ordner
description: Erfahren Sie, wie Sie einen überwachten Ordner erstellen oder löschen oder die Eigenschaften eines vorhandenen überwachten Ordner ändern.
seo-description: Erfahren Sie, wie Sie einen überwachten Ordner erstellen oder löschen oder die Eigenschaften eines vorhandenen überwachten Ordner ändern.
uuid: 659d4d8c-99b8-40dd-b884-bfee4d476fe1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 0ce7b338-6686-49b3-b58b-e7ab6b670708
exl-id: b15d8d3b-5e47-4c33-95fe-440fcf96be83
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1844'
ht-degree: 94%

---

# Erstellen oder konfigurieren Sie einen überwachten Ordner {#create-or-configure-a-watched-folder}

Ein Administrator kann einen Netzwerkordner konfigurieren, der als *überwachter Ordner* bezeichnet wird, sodass ein vorkonfigurierter Dienstvorgang zur Verarbeitung einer Datei gestartet wird, wenn ein Benutzer eine Datei (z. B. eine PDF-Datei) in diesem überwachten Ordner ablegt. Nachdem der angegebene Vorgang ausgeführt wurde, speichert der Vorgang die geänderte Datei in einem angegebenen Ausgabeordner. Ausführliche Informationen zum Verwalten eines überwachten Ordners finden Sie in der [Administrationshilfe](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md).

Sie können die Benutzeroberfläche des überwachten Ordners für folgende Vorgänge verwenden:

* Einen überwachten Ordner erstellen
* Die Eigenschaften eines vorhandenen überwachten Ordners ändern
* Einen überwachten Ordner löschen

## Einen überwachten Ordner erstellen {#create-a-watched-folder}

Bevor Sie einen überwachten Ordner konfigurieren, stellen Sie Folgendes sicher:

* Überwachte Ordner ist eine erweiterte Funktion von AEM Forms. Dafür wird das Add-On-Paket für AEM Forms benötigt. Stellen Sie sicher, dass das entsprechende Add-On-Paket für AEM Forms installiert und konfiguriert ist.
* Sie können den überwachten Ordner auf einem freigegebenen oder lokalen Speicher erstellen. Sorgen Sie dafür, dass der AEM Forms-Benutzer, der den überwachten Ordner ausführen darf, über Lese- und Schreibberechtigungen für den überwachten Ordner verfügt.
* Sie können einen Dienst, Arbeitsablauf oder ein Skript verwenden, um einen Prozess mithilfe überwachter Ordner zu automatisieren. Stellen Sie sicher, dass der entsprechende Service, der Arbeitsablauf oder ein Skript erstellt wurde und ausgeführt werden kann. Informationen zum Erstellen eines Dienstes, Workflows und Skripts finden Sie unter [Verschiedene Methoden zur Verarbeitung von Dateien](/help/forms/using/watched-folder-in-aem-forms.md#various-methods-for-processing-files).
* Ein überwachter Ordner besitzt verschiedene Eigenschaften, siehe [Eigenschaften für überwachte Ordner](watched-folder-in-aem-forms.md#watchedfolderproperties).

Führen Sie die folgenden Schritte aus, um einen überwachten Ordner zu erstellen:

1. Tippen Sie auf **Adobe Experience Manager** in der oberen linken Ecke des Bildschirms.
1. Tippen Sie auf **Werkzeuge** > **Formulare** > **Überwachten Ordner konfigurieren**. Eine Liste der bereits konfigurierten überwachten Ordner wird angezeigt.
1. Tippen Sie auf **Neu**. Eine Liste mit den Feldern, die erforderlich sind, um den überwachten Ordner zu erstellen, wird angezeigt:

   * **Name:** Gibt den überwachten Ordner an. Verwenden Sie nur alphanumerische Zeichen für den Namen.
   * **Pfad:** Gibt den Speicherort des überwachten Ordners an. In einer Clusterumgebung muss diese Einstellung auf einen freigegebenen Netzwerkordner zeigen, auf den jeder Benutzer, der AEM auf anderen Knoten des Clusters ausführt, zugreifen kann.
   * **Prozessdateien, die Folgendes verwenden:** Den Typ des zu startenden Prozesses. Zur Auswahl stehen Workflow, Skript oder Dienst.
   * **Dienstname/Skript-Pfad/Workflow-Pfad:** Das Verhalten des Feldes basiert auf dem Wert, der für das Feld **Prozessdateien, die Folgendes verwenden** definiert wird. Sie können die folgenden Werte festlegen:

      * Für einen Workflow geben Sie das Workflow-Modell an, das ausgeführt werden soll. Beispiel: /etc/workflow/models/&lt;Workflow-Name>/jcr:content/model
      * Für ein Skript geben Sie den JCR-Pfad des auszuführenden Skripts an. Beispiel: /etc/watchfolder/test/testScript.ecma
      * Für einen Dienst geben Sie den Filter an, der zum Suchen nach einem OSGi-Dienst verwendet werden soll. Der Dienst ist als Implementierung der com.adobe.aemfd.watchfolder.service.api.ContentProcessor-Schnittstelle registriert. Beispiel: Der folgende Code ist eine benutzerdefinierte Implementierung der ContentProcessor-Schnittstelle mit der benutzerdefinierten Eigenschaft „foo=bar“.

   >[!NOTE]
   >
   >Wenn Sie einen **Dienst** für das Feld **Prozessdateien, die Folgendes verwenden** gewählt haben, muss der Wert des Feldes „Dienstname“ (inputProcessorType) in Klammern gesetzt werden. Beispielsweise (foo = bar).

   ```java
   @Component(metatype = true, immediate = true, label = "WF Test Service", description = "WF Test Service")
   @Service(value = {OutputWriter.class, ContentProcessor.class})
   @Property(name = "foo", value = "bar")
   public class OutputWriter implements ContentProcessor {
   ```

   * **Ausgabedateimuster:** Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die von einem überwachten Ordner verwendet werden, um den Namen und den Speicherort der Ausgabedateien und Ordner zu bestimmen. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).


1. Tippen Sie auf **Erweitert**. Die Registerkarte „Erweitert“ enthält weitere Felder. Die meisten dieser Felder enthalten einen Standardwert.

   * **Payload Mapper-Filter:** Wenn Sie einen überwachten Ordner erstellen, wird eine Ordnerstruktur innerhalb des überwachten Ordners erstellt. Die Ordnerstruktur enthält Ordner für Phasen, Ergebnisse, Beibehaltung, Eingabe und Fehler. Die Ordnerstruktur kann als Nutzdateneingabe für den Workflow verwendet werden und die Ausgabe eines Workflow übernehmen. Sie kann gegebenenfalls auch Fehlerquellen auflisten.  Die Struktur der Nutzdaten unterscheidet sich von der Struktur eines überwachten Ordners anders. Sie können benutzerdefinierte Skripte schreiben, um die Struktur eines überwachten Ordners den Nutzdaten zuzuordnen. Ein solches Skript wird als „Payload-Mapper-Filter“ bezeichnet. Zwei Standard-Mapper-Implementierungen sind verfügbar. Wenn Sie keine[ benutzerdefinierte Implementierung](/help/forms/using/watched-folder-in-aem-forms.md#creating-a-custom-payload-mapper-filter) haben, verwenden Sie eine Standard-Implementierung:

      * **Standard-Mapper:** Verwenden Sie den Standard-Payload-Mapper, um den Eingabe- und Ausgabe-Inhalt der überwachten Ordner in separaten Eingabe- und Ausgabeordnern in der Payload zu belassen.
      * **Einfacher dateibasierter Payload-Mapper:** Verwenden Sie den einfachen dateibasierten Payload-Mapper, um Eingabe- und Ausgabe-Inhalte direkt im Nutzdatenordner zu beizubehalten. Er erstellt keine zusätzliche Hierarchie, wie Standard-Mapper.
   * **Modus ausführen:** Geben Sie eine kommagetrennte Liste der zulässigen Ausführungsmodi für die Ausführung des Workflows an.
   * **Zeitüberschreitung für Stage-Dateien nach:** Geben Sie die Anzahl Sekunden an, nach denen für eine Eingabedatei/einen Ordner, der bereits zur Verarbeitung abgerufen wurde, eine Zeitüberschreitung eintritt und ein Fehler gemeldet wird. Die Zeitüberschreitungsfunktion wird nur aktiviert, wenn der Wert für diese Eigenschaft eine positive Zahl ist.
   * **Stage-Dateien mit Zeitüberschreitung bei Einschränkung löschen:** Wenn diese Option aktiviert ist, wird der Mechanismus **Zeitüberschreitung für Stage-Dateien nach** nur bei aktivierten Einschränkungen für den überwachten Ordner aktiviert.
   * **Überprüfen des Eingabeordners alle:** Geben Sie das Intervall in Sekunden an, innerhalb dessen der überwachte Ordner auf Eingaben überprüft wird. Außer wenn die Einstellung „Einschränken“ aktiviert ist, muss das Abfrageintervall länger sein als die Verarbeitungsdauer für einen durchschnittlichen Auftrag. Anderenfalls könnte es zu einer Überlastung des Systems kommen. Der Wert für den Intervall muss größer als oder gleich eins sein.
   * **Muster für auszuschließende Dateien:** Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die von einem überwachten Ordner verwendet wird, um zu ermitteln, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Alle Dateien oder Ordner, die diesem angegebenen Muster entsprechen, werden nicht für die Verarbeitung überprüft. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **Muster für einzuschließende Dateien:** Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die vom überwachten Ordner verwendet wird, um zu ermitteln, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Beispiel: Wenn das Muster für einzuschließende Dateien &quot;input&amp;ast;&quot;lautet, werden alle Dateien und Ordner angezeigt, die mit &quot;input&amp;ast&quot;übereinstimmen. abgeholt werden. Der Standardwert ist &amp;ast; und zeigt alle Dateien und Ordner an. Weitere Informationen zu Dateimustern finden Sie unter [Über Dateimuster](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **Wartezeit:** Geben Sie die Zeit in Millisekunden an, die gewartet wird, bevor ein Ordner oder eine Datei nach der Erstellung überprüft wird. Wenn die Wartezeit beispielsweise 3.600.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei nach Ablauf von mindestens 59 Minuten abgerufen. Der Standardwert ist 0.

      Diese Einstellung ist nützlich, um sicherzustellen, dass der gesamte Inhalt einer Datei oder eines Ordners in den Eingabeordner kopiert wurde. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und das Herunterladen der Datei zehn Minuten dauert, legen Sie die Wartezeit auf 10&amp;ast;60 &amp;ast;1000 Millisekunden fest. Dieses Intervall verhindert, dass der überwachte Ordner die Datei bereits überprüft, wenn sie noch keine 10 Minuten alt ist.

   * **Ergebnisse löschen, die älter sind als:** Geben Sie die Anzahl der Tage an, nach denen die Dateien und Ordner gelöscht werden, die älter als der angegebene Wert sind. Diese Einstellung hilft dafür zu sorgen, dass der Ergebnisordner nicht voll wird. Ein Wert von „-1“ Tage bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.
   * **Ergebnis-Ordnername:** Geben Sie den Namen des Ordners ein, um die Ergebnisse zu speichern. Wenn die Ergebnisse nicht in diesem Ordner angezeigt werden, überprüfen Sie den Fehlerordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Sie können einen absoluten oder relativen Pfad mit folgendem Dateimuster verwenden:

      * %F = Dateinamenpräfix
      * %E = Dateinamenerweiterung
      * %Y = Jahr (vollständig)
      * %y = Jahr (letzte zwei Stellen)
      * %M = Monat
      * %D = Tag des Monats
      * %d = Tag des Jahres
      * %H = Stunde (24-Stunden-Format)
      * %h = Stunde (12-Stunden-Format)
      * %m = Minute
      * %s = Sekunde
      * %l = Millisekunde
      * %R = Zufallszahl (zwischen 0 und 9)
      * %P = Prozess- oder Auftrags-ID
      * Wenn es beispielsweise der 17. Juli 2009, 20 Uhr, ist und Sie C:/Test/WF0/failure/%Y/%M/%D/%H/ angeben, ist der Ergebnisordner C:/Test/WF0/failure/2009/07/17/20.
      * Wenn der Pfad nicht absolut, sondern relativ ist, wird der Ordner im überwachten Ordner erstellt. Der Standardwert ist „result/%Y/%M/%D/“, der Ergebnisordner im überwachten Ordner. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **Fehler-Ordnername:** Geben Sie den Ordner an, in dem die Dateien gespeichert sind. Dieser Speicherort ist stets relativ zum überwachten Ordner. Sie können Dateimuster verwenden, wie für „Ergebnisordner“ beschrieben.
   * **„Bewahren“-Ordnername:** Der Speicherort, an dem Dateien nach erfolgreicher Überprüfung und Aufnahme gespeichert werden. Dies kann ein absoluter, relativer oder leerer Ordnerpfad sein. Sie können Dateimuster verwenden, wie für „Ergebnisordner“ beschrieben. Der Standardwert ist „preserve/%Y/%M/%D/“.
   * **Stapelgröße:** Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Mit dieser Einstellung können Sie eine Überlastung des Systems verhindern, da das gleichzeitige Überprüfen zu vieler Dateien zu einem Absturz führen kann. Der Standardwert ist 2. 

      Wenn das Überprüfungsintervall kurz ist, wird der Eingabeordner häufig von den Threads überprüft. Falls häufig Dateien im überwachten Ordner abgelegt werden, sollten Sie ein kurzes Überprüfungsintervall wählen. Wenn Dateien nicht häufig abgelegt werden, verwenden Sie ein größeres Überprüfungsintervall, damit die anderen Dienste die Threads verwenden können.

   * **throttleOn:** Wenn diese Option aktiviert ist, wird die Anzahl der Aufträge für den überwachten Ordner begrenzt, die AEM Forms zu jeder Zeit verarbeiten kann. Der Wert für die Stapelgröße bestimmt die maximale Anzahl an Aufträgen. Weitere Informationen finden Sie unter [Einschränken](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-throttling).
   * **Vorhandene Dateien mit ähnlichem Namen überschreiben:** Bei Festlegung auf „True“ werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf „False“ wird an die Namen von Dateien und Ordnern ein numerisches Indexsuffix angehängt. Der Standardwert ist „False“.
   * **Dateien bei Fehler beibehalten:** Bei Festlegung auf „True“ bleiben Eingabedateien im Falle eines Fehlers erhalten. Der Standardwert lautet true.
   * **Dateien mit Muster einbeziehen:** Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die vom überwachten Ordner verwendet wird, um zu ermitteln, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Wenn beispielsweise das Muster für einzuschließende Dateien eingegeben wird, werden alle Dateien und Ordner aufgenommen, die mit der Eingabe übereinstimmen. Weitere Informationen finden Sie in der [Administration-Hilfe](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md).
   * **Überwachten Ordner asynchron aufrufen:** Gibt den Aufruftyp als „asynchron“ oder „synchron“ an. Der Standardwert ist „asynchron“. „Asynchron“ wird für langlebige Prozesse empfohlen, während „synchron“ für transiente und kurzlebige Prozesse empfohlen wird.
   * **Überwachten Ordner aktivieren:** Wenn diese Option aktiviert ist, wird der überwachte Ordner aktiviert. Der Standardwert ist „true“.



## Die Eigenschaften eines vorhandenen überwachten Ordners ändern  {#modify-properties-of-an-existing-watched-folder}

Zusätzlich zum Namen des überwachten Ordners können Sie alle Eigenschaften eines vorhandenen überwachten Ordners ändern. Führen Sie die folgenden Schritte aus, um die Eigenschaften eines vorhandenen überwachten Ordner zu ändern:

1. Tippen Sie auf das Symbol **Adobe Experience Manager** in der oberen linken Ecke des Bildschirms.
1. Tippen Sie auf **Werkzeuge** > **Formulare** > **Überwachten Ordner konfigurieren.**. Eine Liste der bereits konfigurierten überwachten Ordner wird angezeigt.
1. Wählen Sie auf der linken Seite des Bildschirms des überwachten Ordners den überwachten Ordner aus und tippen Sie auf **Bearbeiten.** Eine Liste mit den Feldern, die erforderlich sind, um den überwachten Ordner zu erstellen, wird angezeigt. Die Felder, die auf der Registerkarte **Grundeinstellungen** aufgeführt sind, sind Pflichtfelder. Die Registerkarte „Erweitert“ enthält weitere Felder. Die meisten dieser Felder enthalten einen Standardwert. Sie können diese Eigenschaften entsprechend Ihren Anforderungen ändern.
1. Wenn Sie die Eigenschaften geändert haben, tippen Sie auf **Aktualisierung**. Die geänderten Eigenschaften werden gespeichert.
