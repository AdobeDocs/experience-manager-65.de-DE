---
title: Aufrufen von AEM Forms mithilfe von APIs
seo-title: Aufrufen von AEM Forms mithilfe von APIs
description: 'null'
seo-description: 'null'
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Aufrufen von AEM Forms mithilfe von APIs {#invoking-aem-forms-using-apis}

Adobe Experience Manager Forms ist eine J2EE-basierte Unternehmenssoftware, die aus Diensten besteht, die in einer freigegebenen Infrastruktur arbeiten. Dienstvorgänge nutzen oder produzieren normalerweise Dokumente. Mit AEM Forms können Sie den Arbeitsablauf für Formulare mit elektronischen Formularen, Document Security und der Dokumenterstellung in einem integrierten und zusammenhängenden Satz von Diensten kombinieren. Auf diese Dienste kann von innen und außerhalb der Firewall zugegriffen werden.

Clientanwendungen können AEM Forms-Dienste programmgesteuert über eine Java-API, Webdienste, Remoting und REST aufrufen. Mit Administration Console können Sie einen Dienst so konfigurieren, dass ein Endpunkt offen gelegt wird, über den AEM Forms-Dienste programmgesteuert aufgerufen werden können. Standardmäßig sind die meisten Dienste vorkonfiguriert, um Remoting-, Java- und Webdienst-Endpunkte anzuzeigen.

Ihre Geschäftsanforderungen bestimmen, welche Aufrufmethode verwendet werden soll. Beispielsweise können Sie mit der Java-API AEM Forms-Funktionen in Ihre Java-Unternehmensanwendungen integrieren, z. B. Java Entity und Message Beans. Ebenso können Sie AEM Forms-Funktionen mithilfe von Webdiensten in .NET-Projekte (oder andere Projekte, die mit Entwicklungsumgebungen entwickelt wurden, die Webdienststandards unterstützen) integrieren.

Dienste erfordern einen Dienstcontainer, ähnlich wie Enterprise JavaBeans™ (EJBs) einen J2EE-Container benötigen. AEM Forms enthält nur eine Implementierung eines Dienstcontainers. Der Dienstcontainer ist für die Verwaltung der Lebensdauer eines Dienstes zuständig, einschließlich dessen Bereitstellung und der Sicherstellung, dass alle Anforderungen an den richtigen Dienst gesendet werden. Es verwaltet auch Dokumente, die ein Dienst nutzt oder produziert.

>[!NOTE]
>
>Die Programmierung mit AEM Forms enthält keine Informationen zum Aufrufen von AEM Forms mithilfe von überwachten Ordnern oder per E-Mail.

