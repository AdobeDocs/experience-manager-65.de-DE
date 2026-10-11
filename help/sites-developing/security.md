---
title: Sicherheit
description: Anwendungssicherheit beginnt bereits in der Entwicklungsphase
exl-id: c4f7f45f-224b-4fc3-b4b0-f5b21b8a466f
solution: Experience Manager, Experience Manager Sites
feature: Developing,Security
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
    internal-label: Administration and security
subfeature_v2:
  - id: c35bc059-fd80-4a01-91a6-e48da3c76758
    internal-label: Security practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 96%
---
# Sicherheit{#security}

Anwendungssicherheit beginnt bereits in der Entwicklungsphase. Adobe empfiehlt, die folgenden Best Practices für die Sicherheit umzusetzen.

## Verwenden von Anfragesitzungen {#use-request-session}

Gemäß dem Prinzip der geringsten Rechte empfiehlt Adobe, dass jeder Zugriff auf das Repository über die an die Benutzeranfrage gebundene Sitzung und eine angemessene Zugriffskontrolle erfolgt.

## Schützen vor Cross-Site-Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Mit Cross-Site-Scripting (XSS) können Angreifer Code in Web-Seiten einfügen, die von anderen Benutzenden aufgerufen werden. Diese Sicherheitslücke kann von böswilligen Web-Benutzenden ausgenutzt werden, um die Zugriffssteuerung zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Bei Entwicklung und Tests hat das Vermeiden von XSS höchste Priorität.

Der XSS-Schutzmechanismus, der von AEM bereitgestellt wird, basiert auf der [AntiSamy Java™ Library](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) von [OWASP (Open Web Application Security Project)](https://owasp.org/). Die standardmäßige AntiSamy-Konfiguration finden Sie unter

`/libs/cq/xssprotection/config.xml`

Es ist wichtig, dass Sie diese Konfiguration an Ihre eigenen Sicherheitsanforderungen anpassen, indem Sie die Konfigurationsdatei überlagern. Die offizielle [AntiSamy-Dokumentation](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) bietet alle notwendigen Informationen, um Ihre Sicherheitsanforderungen zu implementieren.

>[!NOTE]
>
>Adobe empfiehlt, immer mit der [von AEM bereitgestellten XSSAPI](https://experienceleague.adobe.com/en/tools/aem-api-documentation/6-5/javadoc/com/adobe/granite/xss/XSSAPI.html) auf die XSS-Schutz-API zuzugreifen.

Auch kann eine Firewall in der Web-Anwendung wie [mod_security für Apache](https://www.modsecurity.org) die Sicherheit der Bereitstellungsumgebung zuverlässig und zentral steuern und diese vor bisher unerkannten Cross-Site-Scripting-Angriffen schützen.

## Zugreifen auf Cloud-Service-Informationen {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs für die Cloud-Service-Informationen und die OSGi-Einstellungen, die zum Sichern Ihrer Instanz erforderlich sind, werden im Rahmen des [produktionsbereiten Modus](/help/sites-administering/production-ready.md) automatisiert. Das bedeutet, dass Sie die Konfiguration nicht manuell ändern müssen. Sie sollten sie dennoch überprüfen, bevor Sie Ihre Bereitstellung live schalten.

Wenn Sie Ihre [AEM-Instanz mit Adobe Experience Cloud integrieren](/help/sites-administering/marketing-cloud.md), verwenden Sie [Cloud-Service-Konfigurationen](/help/sites-developing/extending-cloud-config.md). Informationen zu diesen Konfigurationen sowie alle erfassten Statistiken werden im Repository gespeichert. Wenn Sie diese Funktionalität verwenden, empfiehlt Adobe, dass Sie überprüfen, ob die Standardsicherheit dieser Informationen Ihren Anforderungen entspricht.

Das webservicesupport-Modul schreibt Statistiken und Konfigurationsinformationen unter:

`/etc/cloudservices`

Mit den Standardberechtigungen:

* Autorenumgebung: `read` für `contributors`

* Veröffentlichungsumgebung: `read` für `everyone`

## Schützen Sie sich vor Cross-Site Request Forgery-Angriffen {#protect-against-cross-site-request-forgery-attacks}

Weitere Informationen zu den Sicherheitsmechanismen, die AEM zur Abschwächung von CSRF-Angriffen einsetzt, finden Sie im Abschnitt [Sling Referrer Filter](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) der Sicherheits-Checkliste und in der [Dokumentation zum CSRF Protection Framework](/help/sites-developing/csrf-protection.md).
