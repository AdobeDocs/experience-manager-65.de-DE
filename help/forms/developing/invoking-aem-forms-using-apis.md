---
title: Aufrufen von AEM Forms mithilfe von APIs
description: Erfahren Sie, wie Sie AEM Forms-Dienste über eine Java™-API, Web-Dienste, Remoting und REST aufrufen können.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
role: Developer
exl-id: 0e92d1ad-12bd-4bfd-81cc-9be8e376c5ca
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 100%

---

# Aufrufen von AEM Forms mithilfe von APIs {#invoking-aem-forms-using-apis}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Adobe Experience Manager Forms ist eine auf J2EE basierende Unternehmenssoftware, die aus Diensten besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Dienstvorgänge nutzen oder produzieren normalerweise Dokumente. Mithilfe von AEM Forms können Sie Forms Workflow mit elektronischen Formularen, Dokumentensicherheit und der Dokumenterstellung in einem integrierten und kohärenten Satz von Diensten kombinieren. Der Zugriff auf diese Dienste kann von innerhalb und außerhalb der Firewall erfolgen.

Client-Anwendungen können AEM Forms-Dienste programmgesteuert über eine Java™-API, Web-Dienste, Remoting und REST aufrufen. Über die Administrationskonsole können Sie einen Dienst so konfigurieren, dass ein Endpunkt bereitgestellt wird, über den AEM Forms-Dienste programmgesteuert aufgerufen werden können. Standardmäßig sind die meisten Dienste so vorkonfiguriert, dass sie Remoting-, Java- und Web-Dienst-Endpunkte bereitstellen.

Ihre Geschäftsanforderungen bestimmen, welche Aufrufmethode verwendet werden soll. Beispielsweise können Sie mit der Java™-API AEM Forms-Funktionen in Ihre Java™-Unternehmensanwendungen integrieren, z. B. Java™-Entität und Message-Beans. Ebenso können Sie AEM Forms-Funktionen mithilfe von Webdiensten in .NET-Projekte (oder andere Projekte, die mit Entwicklungsumgebungen entwickelt wurden, die Webdienststandards unterstützen) integrieren.

Für die Ausführung von Diensten ist ein Dienstcontainer erforderlich, ähnlich wie Enterprise JavaBeans™ (EJBs) einen J2EE-Container benötigen. AEM Forms umfasst nur eine Implementierung eines Dienstcontainers. Der Dienstcontainer ist für die Verwaltung der Lebensdauer eines Dienstes zuständig, einschließlich seiner Bereitstellung und der Sicherstellung, dass alle Anforderungen an den richtigen Dienst gesendet werden. Er verwaltet auch Dokumente, die ein Dienst nutzt oder produziert.

>[!NOTE]
>
>„Programmieren mit AEM Forms“ enthält keine Informationen zum Aufrufen von AEM Forms mithilfe von überwachten Ordnern oder E-Mails.
