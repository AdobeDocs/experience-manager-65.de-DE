---
title: Arten von Endpunkten
seo-title: Arten von Endpunkten
description: Erfahren Sie mehr über die verschiedenen Arten von Endpunkten.
seo-description: Erfahren Sie mehr über die verschiedenen Arten von Endpunkten.
uuid: c899245c-14cc-4035-9440-95a5b6c1e47f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8fe572e0-8a53-4129-940f-3fdb990073fe
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Arten von Endpunkten {#types-of-endpoints}

Bevor ein Dienst verwendet werden kann, müssen Sie einen Endpunkt konfigurieren und aktivieren. Ein Endpunkt gibt an, wie ein Dienst aufgerufen werden soll.

>[!NOTE]
>
>In Workbench werden Endpunkte als „Startpunkte“ bezeichnet.

Einem Dienst können die folgenden Typen von Endpunkten hinzugefügt werden: Nicht alle Dienste unterstützen alle Endpunkte:

**** E-Mail: Ermöglicht es einem Benutzer, einen Dienst durch Senden einer E-Mail mit einer oder mehreren Dateianlagen an ein angegebenes E-Mail-Konto aufzurufen. Bevor Sie einen Email-Endpunkt konfigurieren können, müssen Sie die erforderlichen E-Mail-Konten konfigurieren. (Siehe E-Mail-Endpunkte konfigurieren.)

**** Überwachter Ordner: Ermöglicht dem Benutzer, einen Dienst aufzurufen, indem er eine Datei in einem Ordner ablegt, der in einem definierten Intervall überprüft wird. (Siehe Endpunkte für überwachte Ordner konfigurieren.)

**** TaskManager: Ermöglicht einem Workspace-Benutzer, den Dienst aufzurufen.

**** Remoting: Aktiviert eine mit Flex erstellte Anwendung zum Aufrufen des Dienstes mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms). Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt und Flex-Clients können Remoteobjekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

**** SOAP: Aktiviert eine Clientanwendung, die mithilfe der AEM Forms-Anwendungsprogrammierschnittstelle (API) zum Aufrufen des Dienstes im SOAP-Modus entwickelt wurde. Ein SOAP-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. 

**Hinweis**: Die *Sicherheit kann aus Document Security-Dokumenten entfernt werden, wenn der SOAP-Endpunkt beim Anzeigen der Dokumente in Adobe Acrobat oder Adobe Reader verwendet wird. Detailinformationen zum Deaktivieren von SOAP-Endpunkten für LCRM-Dokumente finden Sie unter[SOAP-Endpunkte für Document Security-Dokumente deaktivieren](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*.

**** EJB: Aktiviert eine Clientanwendung, die mithilfe der AEM Forms-Anwendungsprogrammierschnittstelle (API) zum Aufrufen des Dienstes mit dem Enterprise JavaBeans-Modus (EJB) entwickelt wurde. Ein EJB-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt.

**** WSDL: Aktiviert eine Clientanwendung, die mithilfe der AEM Forms-Anwendungsprogrammierschnittstelle (API) zum Aufrufen des Dienstes mit der Web Service Definition Language (WSDL) entwickelt wurde. Die Seite „Core-Konfigurationen“ enthält eine Option zum Aktivieren der WSDL-Generierung für alle AEM Forms-Dienste. (Siehe Allgemeine AEM Forms-Einstellungen konfigurieren.)

**** REST: Prozesse, die in Workbench erstellt wurden, können so konfiguriert werden, dass Sie sie über REST-Anforderungen (Repräsentational State Transfer) aufrufen können. REST-Anforderungen werden von HTML-Seiten aus gesendet. Das heißt, Sie können einen AEM Forms-Prozess direkt von einer Webseite mithilfe einer REST-Anforderung aufrufen.

Die Endpunkte E-Mail, TaskManager, überwachter Ordner und Remoting stellen nur einen bestimmten Vorgang des Dienstes zur Verfügung. Beim Hinzufügen dieser Endpunkte muss in einem zweiten Konfigurationsschritt eine Methode zum Aufrufen des Dienstes, zum Festlegen von Konfigurationsparametern und zum Angeben der Zuordnungen von Eingabe- und Ausgabeparameter ausgewählt werden.
