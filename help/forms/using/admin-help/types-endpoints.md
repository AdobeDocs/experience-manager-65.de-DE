---
title: Typen von Endpunkten
description: Erfahren Sie mehr über die verschiedenen Typen von Endpunkten. Verschiedene Typen von Endpunkten wie E-Mail, überwachter Ordner und viele andere können zu Diensten hinzugefügt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 380cab7f-e7f7-4cb7-bd20-ea530a349fac
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '455'
ht-degree: 100%

---

# Arten von Endpunkten {#types-of-endpoints}

Bevor ein Dienst verwendet werden kann, müssen Sie einen Endpunkt konfigurieren und aktivieren. Ein Endpunkt gibt an, wie ein Dienst aufgerufen werden soll.

>[!NOTE]
>
>In Workbench werden Endpunkte als Startpunkte bezeichnet.

Die folgenden Typen von Endpunkten können zu Diensten hinzugefügt werden. Nicht alle Dienste unterstützen alle Endpunkte:

**E-Mail**: Ermöglicht es einem Benutzer, einen Service durch Senden einer E-Mail mit einer oder mehreren Dateianlagen an ein angegebenes E-Mail-Konto aufzurufen. Bevor Sie einen Email-Endpunkt konfigurieren können, müssen Sie die erforderlichen E-Mail-Konten konfigurieren. (Siehe E-Mail-Endpunkte konfigurieren.)

**Überwachter Ordner**: Ermöglicht es einem Benutzer, einen Service aufzurufen, indem er eine Datei in einem Ordner ablegt, der in einem bestimmten Intervall überprüft wird. (Siehe Endpunkte für überwachte Ordner konfigurieren.)

**TaskManager**: Ermöglicht es einem Workspace-Benutzer, den Service aufzurufen.

**Remoting**: Ermöglicht es einem Programm, das mit Flex erstellt wurde, den Service mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt) aufzurufen. Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt, und Flex-Kundinnen und -Kunden können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Service aufzurufen.

**SOAP**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe des SOAP-Modus aufzurufen. Ein SOAP-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. 

**Hinweis**: *Die Sicherheit kann aus Sicherheitsdokumenten entfernt werden, wenn der SOAP-Endpunkt verwendet wird, während die Dokumente in Adobe Acrobat oder Adobe Reader angezeigt werden. Detailinformationen zum Deaktivieren von SOAP-Endpunkten für LCRM-Dokumente finden Sie unter [SOAP-Endpunkte für Document Security-Dokumente deaktivieren](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*.

**EJB**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe des Enterprise JavaBeans-Modus (EJB) aufzurufen. Ein EJB-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt.

**WSDL**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe der Web Service Definition Language (WSDL) aufzurufen. Die Seite „Core-Konfigurationen“ enthält eine Option zum Aktivieren der WSDL-Generierung für alle AEM Forms-Dienste. (Siehe Allgemeine AEM Forms-Einstellungen konfigurieren.)

**REST**: In Workbench erstellte Prozesse können so konfiguriert werden, dass sie über Representational State Transfer-Anforderungen (REST) aufgerufen werden können. REST-Anfragen werden von HTML-Seiten gesendet. Das heißt, Sie können mithilfe einer REST-Anfrage einen AEM Forms-Prozess direkt von einer Web-Seite aufrufen. 

Die Endpunkte „E-Mail“, „Task Manager“ und „Überwachter Ordner“ stellen nur einen bestimmten Vorgang des Dienstes zur Verfügung. Das Hinzufügen dieser Endpunkte erfordert einen zweiten Konfigurationsschritt, um eine den Dienst aufrufende Methode auszuwählen, Konfigurationsparameter festzulegen und Zuordnungen von Ein- und Ausgabeparametern anzugeben.
