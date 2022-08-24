---
title: Allgemeine AEM Forms-Einstellungen
seo-title: General AEM Forms settings
description: Erfahren Sie, wie Sie die Seite „Core-Konfigurationen“ in Administration Console konfigurieren, was zu einer Verbesserung der Leistung des Systems beitragen kann.
seo-description: Learn to configure the Core Configurations page settings in administration console that can help improve system performance.
uuid: 940680fd-b7ab-4376-aa5b-e139223522ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bd648c38-731b-420e-973d-a4728b69868e
exl-id: e1519477-b5a8-4947-8597-26b945a3b819
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '1713'
ht-degree: 98%

---

# Allgemeine AEM Forms-Einstellungen {#general-aem-forms-settings}

Auf der Seite „Core-Konfigurationen“ in Administration Console finden Sie Einstellungen, mit deren Hilfe Sie die Leistung des Systems verbessern können. Nach dem Konfigurieren oder Aktualisieren dieser Einstellungen müssen Sie den Anwendungsserver neu starten.

Informationen zum Aktivieren des abgesicherten Sicherungsmodus finden Sie unter [Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus](/help/forms/using/admin-help/enabling-disabling-safe-backup-mode.md#enabling-and-disabling-safe-backup-mode).


>[!NOTE]
>
>Die Dateien im temporären Ordner sowie die dauerhaft genutzten Dokumente im Stammordner des globalen Dokumentenspeichers (GDS) können vertrauliche Benutzerinformationen enthalten, z. B. Informationen, für die spezielle Berechtigungen erforderlich sind, wenn der Zugriff über die APIs oder Benutzeroberflächen erfolgt. Aus diesem Grund ist es wichtig, dass dieser Ordner mithilfe einer der vom Betriebssystem angebotenen Methoden ordnungsgemäß abgesichert wird. Es wird empfohlen, dass nur das Betriebssystemkonto, das zum Ausführen des Anwendungsservers dient, Lese- und Schreibzugriff auf diesen Ordner hat.


1. Klicken Sie in der Administrationskonsole auf **[!UICONTROL „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“]**.
1. Ändern Sie auf der Seite „Core-Konfigurationen“ die folgenden Einstellungen nach Bedarf und klicken Sie auf **[!UICONTROL OK]**. Einzelheiten zu den Optionen finden Sie unter [Optionen für die Core-Konfigurationen](configure-general-aem-forms-settings.md#core-configurations-options).


## Optionen für die Core-Konfigurationen {#core-configurations-options}

**Speicherort des temporären Ordners** Der Ordnerpfad, in dem AEM Forms temporäre Produktdateien erstellt. Wenn der Wert dieser Einstellung leer ist, wird als Speicherort standardmäßig ein Ordner unterhalb des Systemordners „temp“ gewählt. Stellen Sie sicher, dass der temporäre Ordner ein beschreibbarer Ordner ist.

>[!NOTE]
>
>Stellen Sie sicher, dass sich der temporäre Ordner im lokalen Dateisystem befindet. AEM Forms unterstützt keine temporären Ordner an einem Remote-Standort.

**Stammordner des globalen Dokumentenspeichers** Der Stammordner des globalen Dokumentenspeichers (GDS) wird für folgende Zwecke verwendet:

* Speichern von dauerhaft genutzten Dokumenten. Dauerhaft genutzte Dokumente verfügen nicht über einen Ablaufzeitpunkt und bleiben bestehen, bis sie entfernt werden (z. B. in einem Workflow-Prozess verwendete PDF-Dateien). Die dauerhaft genutzten Dokumente bilden einen wichtigen Teil für den gesamten Systemstatus. Wenn einige oder alle diese Dokumente verloren gehen oder beschädigt werden, kann der Formularserver instabil werden. Aus diesem Grund muss dieser Ordner auf einem RAID-Gerät gespeichert werden.
* Speichern von temporären Dokumenten, die während der Verarbeitung benötigt werden.

>[!NOTE]
>
>Sie können die Dokumentenspeicherung auch in der AEM Forms-Datenbank aktivieren. Die Systemleistung ist jedoch bei der Verwendung des GDS höher.

* Übertragen von Dokumenten zwischen Knoten in einem Cluster. Wenn Sie AEM Forms in einer Clusterumgebung ausführen, muss auf diesen Ordner von allen Knoten im Cluster zugegriffen werden können.
* Empfangen eingehender Parameter von Remote-API-Aufrufen.

Wenn Sie keinen GDS-Stammordner angeben, wird als Ordner standardmäßig der Ordner des Anwendungsservers gewählt:

* `[JBOSS_HOME]/server/<server>/svcnative/DocumentStorage`
* `[WEBSPHERE_HOME]/installedApps/adobe/'server'/DocumentStorage`
* `[WEBLOGIC_HOME]/user_projects/<domain>/'server'/adobe/AEMformsserver/DocumentStorage`

>[!NOTE]
>
>Das Ändern des Wertes dieser Einstellung für den Stammordner des globalen Dokumentenspeichers muss mit besonderer Sorgfalt erfolgen. Der Ordner des GDS wird zum Speichern sowohl von in einem Prozess dauerhaft genutzten Dateien als auch von kritischen AEM Forms-Produktkomponenten verwendet. Das Ändern des Speicherorts des GDS-Ordners stellt eine wesentliche Systemänderung dar. Die fehlerhafte Konfiguration des Speicherorts des GDS-Ordners führt dazu, dass AEM Forms nicht mehr funktionsfähig ist, und kann eine vollständige Neuinstallation von AEM Forms erforderlich machen. Wenn Sie einen neuen Speicherort für den Ordner des globalen Dokumentenspeichers angeben, muss der Anwendungsserver heruntergefahren und die Daten migriert werden, bevor der Server neu gestartet werden kann. Der Systemadministrator muss unter Beibehaltung der internen Ordnerstruktur alle Dateien aus dem alten an den neuen Speicherort verschieben. 

>[!NOTE]
>
>Geben Sie für den temporären Ordner („temp“) und den GDS-Ordner nicht denselben Ordner an..

Zusätzliche Informationen zum GDS-Ordner finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzelserver).](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de)

**Speicherort des Ordners für Adobe Server-Schriftarten** Geben Sie den Pfad zu dem Ordner ein, der die Adobe-Server-Schriftarten enthält. Diese Schriftarten werden mit AEM Forms installiert. Der Standardspeicherort dieser Schriftarten ist der Ordner [aem-forms root]/fonts. Wenn auf diesen Ordner nicht zugegriffen werden kann, können Sie die Schriftarten an einen anderen Speicherort kopieren und über diese Einstellung den neuen Speicherort angeben.

**Speicherort des Ordners für Kundenschriftarten** Geben Sie den Pfad zu einem Ordner ein, der zusätzliche Schriftarten enthält, die Sie verwenden möchten.

***Hinweis **: Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.*

**Speicherort des Ordners für Systemschriftarten** Geben Sie den Pfad zu dem von Ihrem Betriebssystem vorgegebenen Schriftartenordner ein. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.

**Speicherort der Data Service-Konfigurationsdatei** Gibt den Speicherort der Datei „services-config.xml“ an. Diese Datei ist standardmäßig in die Datei „adobe-core-appserver.ear“ eingebettet und für Benutzer nicht zugänglich. Eine Kopie der Standarddatei „services-config.xml“ befindet sich im Ordner „[AEM Forms-Stammordner]\sdk\misc\DataServices\Server-Configuration“. Wenn Sie Änderungen an dieser Datei vorgenommen und sie verschoben haben, geben Sie in dieses Feld den neuen Speicherort ein.

Mithilfe der Konfigurationsdatei für Data Services können Sie die Einstellungen von Data Services anpassen, wie z. B. den Authentifizierungstyp oder die Debugausgabe. 

Diese Einstellung ist standardmäßig leer.

**Standardmäßige Maximalgröße für Inline-Dokumente (Byte)**: Die maximale Anzahl von Bytes, die im Speicher beibehalten werden, wenn Dokumente zwischen verschiedenen AEM Forms-Komponenten übergeben werden. Mit dieser Einstellung können Sie die Leistung anpassen. Dokumente, die diesen Wert unterschreiten, werden im Arbeitsspeicher gespeichert und bleiben in der Datenbank erhalten. Dokumente, die diesen Höchstwert überschreiten, werden auf der Festplatte gespeichert. 

Dies ist eine obligatorische Einstellung. Der Standardwert ist 65536 Bytes.

**Standard-Zeitsperre für Entsorgung (Sekunden)**: Die maximale Zeit in Sekunden, während der ein Dokument, das zwischen verschiedenen AEM Forms-Komponenten weitergeleitet wird, als aktiv angesehen wird. Nach Ablauf dieser Zeit können alle Dateien entfernt werden, die zum Speichern dieses Dokuments verwendet wurden. Mit dieser Einstellung können Sie die Auslastung des Festplattenspeicherplatzes steuern. 

Dies ist eine obligatorische Einstellung. Der Standardwert ist 600 Sekunden.

**Sweep-Intervall für Dokumente (Sekunden)**: Die Zeit in Sekunden, die zwischen zwei Versuchen vergehen soll, Dateien zu löschen, die nicht mehr benötigt werden und zuvor zum Weiterleiten der Dokumentdaten zwischen Services verwendet wurden.

Dies ist eine obligatorische Einstellung. Der Standardwert ist 30 Sekunden.

**FIPS aktivieren**: Wählen Sie diese Option zum Aktivieren des FIPS-Modus. FIPS 140-2 (Federal Information Processing Standard) ist ein von der US-Regierung definierter Kryptographiestandard. Im FIPS-Modus wird der Datenschutz von AEM Forms auf gemäß FIPS 140-2 zugelassene Algorithmen eingeschränkt, die das Verschlüsselungsmodul „RSA BSAFE Crypto-C 2.1“ verwenden.

Im FIPS-Modus werden die in Adobe Acrobat®-Versionen vor 7.0 verwendeten Verschlüsselungsalgorithmen nicht unterstützt. Wenn der FIPS-Modus aktiviert ist und Sie den Encryption-Dienst zum Verschlüsseln von PDFs mit einem Kennwort mit einer Kompatibilitätsstufe verwenden, die auf Acrobat 5 festgelegt ist, kommt es bei dem Verschlüsselungsversuch zu einem Fehler.

Im Allgemeinen wendet der Assembler-Dienst bei aktiviertem FIPS keine Kennwortverschlüsselung auf Dokumente an. Wird dies dennoch versucht, wird eine FIPSModeException-Ausnahme ausgelöst, die angibt, dass „Kennwortverschlüsselung im FIPS-Modus nicht zulässig“ ist. Darüber hinaus wird das DDX-Element (Document Description XML) PDFsFromBookmarks im FIPS-Modus nicht unterstützt, wenn das Basisdokument kennwortverschlüsselt ist.

>[!NOTE]
>
>AEM Forms überprüft keinen Code, um die FIPS-Kompatibilität sicherzustellen. Sie bietet einen FIPS-Betriebsmodus, sodass gemäß FIPS zugelassene Algorithmen für Kryptographiedienste aus den FIPS-zugelassenen Bibliotheken (RSA) verwendet werden.

**WSDL aktivieren**: Wählen Sie diese Option, um die WSDL-Generierung (Web Service Definition Language) für alle Services zu aktivieren, die Teil von AEM Forms sind.

Aktivieren Sie diese Option in Entwicklungsumgebungen, in denen Entwickler mithilfe der WSDL-Generierung Clientanwendungen erstellen. In einer Produktionsumgebung können Sie die WSDL-Generierung deaktivieren, um zu verhindern, dass interne Details eines Dienstes preisgegeben werden.

**Dokumentenspeicher in der Datenbank aktivieren**: Wählen Sie diese Option, um dauerhaft genutzte Dokumente in der AEM Forms-Datenbank zu speichern. Wenn Sie diese Option aktivieren, benötigen Sie weiterhin einen GDS-Ordner. Allerdings werden bei Auswahl dieser Option AEM Forms-Sicherungen vereinfacht. Wenn Sie den GDS verwenden, umfasst die Sicherung, dass das AEM Forms-System in den Sicherungsmodus versetzt wird und anschließend die Sicherungen der Datenbank und des GDS ausgeführt werden. Wenn Sie die Datenbankoption auswählen, umfasst die Sicherung das Ausführen der Datenbanksicherung für eine neue Installation oder das Ausführen der Datenbanksicherung und die einmalige Sicherung des GDS für eine Aktualisierung. Es ist möglicherweise eine zusätzliche Verwaltung Ihrer Datenbank erforderlich, um Aufträge und Daten im Vergleich zu einer Konfiguration des GDS zu entfernen. (Siehe Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird.)

**DSC-Aufrufstatistik aktivieren**: Wenn diese Option ausgewählt ist, verfolgt AEM Forms Aufrufstatistiken, z. B. die Anzahl der Aufrufe, die für das Aufrufen erforderliche Zeit und die Anzahl der Fehler in den Aufrufen. Diese Informationen werden in einer JMX-Bean gespeichert, sodass Sie die Java™ JConsole oder die Software eines anderen Herstellers zum Anzeigen der Statistiken verwenden können. Wenn Sie diese Statistiken nicht anzeigen möchten, deaktivieren Sie diese Option, um die Leistung von AEM Forms zu verbessern.

**RDS aktivieren**: Durch die Auswahl dieser Option wird das Remote Development Services (RDS)-Servlet in AEM Forms aktiviert. Wenn diese Option aktiviert ist, können clientseitige Werkzeuge mit Data Services interagieren, um zum Erstellen von Zielen oder Endpunkten Modelle bereitzustellen oder deren Bereitstellung wieder aufzuheben oder zu ermitteln, welche Modelle in Endpunkten bereitgestellt wurden. Standardmäßig ist diese Option nicht aktiviert. 

**Nicht gesicherte RDS-Anfrage zulassen**: Wenn diese Option ausgewählt ist, müssen RDS-Anfragen keine HTTPS verwenden. Standardmäßig ist diese Option nicht ausgewählt und die Kommunikation mit Data Services muss über „https“-Anforderungen ausgeführt werden.

**Nicht gesichertes Hochladen von Dokumenten aus Flex-Programmen zulassen**: Das Datei-Upload-Servlet für das Hochladen von Dokumenten aus Adobe Flex®-Programmen in AEM Forms erfordert, dass Benutzer authentifiziert und autorisiert werden, bevor sie Dokumente hochladen können. Dem Benutzer muss die Rolle „Document Upload Application User“ oder eine andere Rolle, die die Berechtigung zum Hochladen von Dokumenten enthält, zugewiesen sein. Dadurch wird verhindert, dass nicht autorisierte Benutzer Dokumente auf den AEM Forms-Server hochladen. Wählen Sie diese Option, wenn Sie diese Sicherheitsfunktion in einer Entwicklungsumgebung oder für die Abwärtskompatibilität mit vorherigen Versionen von AEM Forms deaktivieren wollen. Standardmäßig ist diese Option nicht aktiviert. Weitere Informationen finden Sie unter &quot;AEM Formulare mithilfe von AEM Forms Remoting aufrufen&quot;in Programmieren mit AEM Formularen.

**Nicht gesichertes Hochladen von Dokumenten von Java SDK-Programmen zulassen**: Hochladevorgänge mit HTTP DocumentManager müssen gesichert sein. HTTP-Uploads erfordern standardmäßig, dass Benutzer authentifiziert und dazu berechtigt sind, bevor sie Dokumente hochladen können. Dem Benutzer muss die Rolle „Dienstbenutzer“ oder eine andere Rolle, die die Berechtigung zum Aufrufen von Diensten enthält, zugewiesen sein. Dadurch wird verhindert, dass nicht autorisierte Benutzer Dokumente auf den Formularserver hochladen. Wählen Sie diese Option, wenn Sie diese Sicherheitsfunktion in einer Entwicklungsumgebung oder für die Abwärtskompatibilität mit vorherigen Versionen von AEM Forms oder basierend auf Ihrer Firewall-Einrichtung deaktivieren möchten. Standardmäßig ist diese Option nicht aktiviert. Weitere Informationen finden Sie unter &quot;AEM Formulare mithilfe der Java-API aufrufen&quot;in Programmieren mit AEM Formularen.
