---
title: Arten von Endpunkten
description: Erfahren Sie mehr über die verschiedenen Typen von Endpunkten. Verschiedene Arten von Endpunkten wie E-Mail, überwachter Ordner und viele andere können Diensten hinzugefügt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 380cab7f-e7f7-4cb7-bd20-ea530a349fac
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 60%

---

# Arten von Endpunkten {#types-of-endpoints}

Bevor ein Dienst verwendet werden kann, müssen Sie einen Endpunkt konfigurieren und aktivieren. Ein Endpunkt gibt an, wie ein Dienst aufgerufen werden soll.

>[!NOTE]
>
>In Workbench werden Endpunkte als Startpunkte bezeichnet.

Die folgenden Typen von Endpunkten können Diensten hinzugefügt werden. Nicht alle Dienste unterstützen alle Endpunkte:

**E-Mail**: Ermöglicht es einem Benutzer, einen Service durch Senden einer E-Mail mit einer oder mehreren Dateianlagen an ein angegebenes E-Mail-Konto aufzurufen. Bevor Sie einen Email-Endpunkt konfigurieren können, müssen Sie die erforderlichen E-Mail-Konten konfigurieren. (Siehe E-Mail-Endpunkte konfigurieren.)

**Überwachter Ordner**: Ermöglicht es einem Benutzer, einen Service aufzurufen, indem er eine Datei in einem Ordner ablegt, der in einem bestimmten Intervall überprüft wird. (Siehe Endpunkte für überwachte Ordner konfigurieren.)

**TaskManager**: Ermöglicht es einem Workspace-Benutzer, den Service aufzurufen.

**Remoting**: Ermöglicht es einem Programm, das mit Flex erstellt wurde, den Service mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt) aufzurufen. Für jeden aktivierten Dienst wird automatisch ein Remoting-Endpunkt erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt. Flex-Clients können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

**SOAP**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe des SOAP-Modus aufzurufen. Ein SOAP-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. 

**Hinweis**: *Die Sicherheit kann aus Sicherheitsdokumenten entfernt werden, wenn der SOAP-Endpunkt verwendet wird, während die Dokumente in Adobe Acrobat oder Adobe Reader angezeigt werden. Detailinformationen zum Deaktivieren von SOAP-Endpunkten für LCRM-Dokumente finden Sie unter [SOAP-Endpunkte für Document Security-Dokumente deaktivieren](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*.

**EJB**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe des Enterprise JavaBeans-Modus (EJB) aufzurufen. Ein EJB-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt.

**WSDL**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe der Web Service Definition Language (WSDL) aufzurufen. Die Seite „Core-Konfigurationen“ enthält eine Option zum Aktivieren der WSDL-Generierung für alle AEM Forms-Dienste. (Siehe Allgemeine AEM Forms-Einstellungen konfigurieren.)

**REST**: In Workbench erstellte Prozesse können so konfiguriert werden, dass sie über Representational State Transfer-Anforderungen (REST) aufgerufen werden können. REST-Anfragen werden von HTML-Seiten gesendet. Das heißt, Sie können einen AEM Formularprozess direkt von einer Webseite aus mit einer REST-Anfrage aufrufen.

Die Endpunkte E-Mail, TaskManager, überwachter Ordner und Remoting stellen nur einen bestimmten Vorgang des Dienstes bereit. Das Hinzufügen dieser Endpunkte erfordert einen zweiten Konfigurationsschritt, um eine Methode zum Aufrufen des Dienstes, zum Festlegen von Konfigurationsparametern und zum Festlegen von Zuordnungen von Eingabe- und Ausgabeparametern auszuwählen.
