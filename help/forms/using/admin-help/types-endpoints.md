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
exl-id: 380cab7f-e7f7-4cb7-bd20-ea530a349fac
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 59%

---

# Arten von Endpunkten {#types-of-endpoints}

Bevor ein Dienst verwendet werden kann, müssen Sie einen Endpunkt konfigurieren und aktivieren. Ein Endpunkt gibt an, wie ein Dienst aufgerufen werden soll.

>[!NOTE]
>
>In Workbench werden Endpunkte als „Startpunkte“ bezeichnet.

Einem Dienst können die folgenden Typen von Endpunkten hinzugefügt werden: Nicht alle Dienste unterstützen alle Endpunkte:

**E-Mail:** Ermöglicht es einem Benutzer, einen Dienst aufzurufen, indem er eine E-Mail-Nachricht mit einem oder mehreren Dateianlagen an ein angegebenes E-Mail-Konto sendet. Bevor Sie einen Email-Endpunkt konfigurieren können, müssen Sie die erforderlichen E-Mail-Konten konfigurieren. (Siehe E-Mail-Endpunkte konfigurieren.)

**Überwachter Ordner:** Ermöglicht es einem Benutzer, einen Dienst aufzurufen, indem eine Datei in einem Ordner abgelegt wird, der in einem bestimmten Intervall überprüft wird. (Siehe Endpunkte für überwachte Ordner konfigurieren.)

**TaskManager:** Ermöglicht es einem Workspace-Benutzer, den Dienst aufzurufen.

**Remoting:** Aktiviert eine mit Flex erstellte Anwendung zum Aufrufen des Dienstes mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting. Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt und Flex-Clients können Remoteobjekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

**SOAP:** Aktiviert eine Client-Anwendung, die mithilfe der AEM Forms-Programmierungs-APIs entwickelt wurde, um den Dienst im SOAP-Modus aufzurufen. Ein SOAP-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. 

**Hinweis**:  *Die Sicherheit kann aus Document Security-Dokumenten entfernt werden, wenn der SOAP-Endpunkt beim Anzeigen der Dokumente in Adobe Acrobat oder Adobe Reader verwendet wird. Detailinformationen zum Deaktivieren von SOAP-Endpunkten für LCRM-Dokumente finden Sie unter [SOAP-Endpunkte für Document Security-Dokumente deaktivieren](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*.

**EJB:** Aktiviert eine Client-Anwendung, die mithilfe der AEM Forms-Programmierungs-APIs entwickelt wurde, um den Dienst mit dem Enterprise JavaBeans-Modus (EJB) aufzurufen. Ein EJB-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt.

**WSDL:** Aktiviert eine Client-Anwendung, die mithilfe der AEM Forms-Programmierungs-APIs entwickelt wurde, um den Dienst mithilfe von WSDL (Web Service Definition Language) aufzurufen. Die Seite „Core-Konfigurationen“ enthält eine Option zum Aktivieren der WSDL-Generierung für alle AEM Forms-Dienste. (Siehe Allgemeine AEM Forms-Einstellungen konfigurieren.)

**REST:** In Workbench erstellte Prozesse können so konfiguriert werden, dass Sie sie über REST-Anfragen (Reational State Transfer) aufrufen können. REST-Anforderungen werden von HTML-Seiten aus gesendet. Das heißt, Sie können einen AEM Forms-Prozess direkt von einer Webseite mithilfe einer REST-Anforderung aufrufen.

Die Endpunkte E-Mail, TaskManager, überwachter Ordner und Remoting stellen nur einen bestimmten Vorgang des Dienstes zur Verfügung. Beim Hinzufügen dieser Endpunkte muss in einem zweiten Konfigurationsschritt eine Methode zum Aufrufen des Dienstes, zum Festlegen von Konfigurationsparametern und zum Angeben der Zuordnungen von Eingabe- und Ausgabeparameter ausgewählt werden.
