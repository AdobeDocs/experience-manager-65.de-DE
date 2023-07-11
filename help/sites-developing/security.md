---
title: Sicherheit
description: Anwendungssicherheit beginnt in der Entwicklungsphase
exl-id: c4f7f45f-224b-4fc3-b4b0-f5b21b8a466f
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 27%

---

# Sicherheit{#security}

Anwendungssicherheit beginnt in der Entwicklungsphase. Adobe empfiehlt die Anwendung der folgenden Best Practices für die Sicherheit.

## Anforderungssitzung verwenden {#use-request-session}

Gemäß dem Prinzip der geringsten Rechte empfiehlt Adobe, dass jeder Zugriff auf das Repository über die an die Benutzeranfrage gebundene Sitzung und eine angemessene Zugriffskontrolle erfolgt.

## Protect gegen Cross-Site Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Cross-Site Scripting (XSS) ermöglicht es Angreifern, Code in Webseiten einzufügen, die von anderen Benutzern angesehen werden. Diese Sicherheitslücke kann von böswilligen Webbenutzern ausgenutzt werden, um Zugriffskontrollen zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Die Prävention von XSS hat sowohl bei der Entwicklung als auch beim Testen höchste Priorität.

Der von AEM bereitgestellte XSS-Schutzmechanismus basiert auf dem [AntiSamy Java™ Library](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) von [OWASP (Open Web Application Security Project)](https://owasp.org/). Die standardmäßige AntiSamy-Konfiguration finden Sie unter

`/libs/cq/xssprotection/config.xml`

Es ist wichtig, dass Sie diese Konfiguration an Ihre eigenen Sicherheitsanforderungen anpassen, indem Sie die Konfigurationsdatei überlagern. Der Beamte [AntiSamy-Dokumentation](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) liefert Ihnen alle Informationen, die Sie zur Implementierung Ihrer Sicherheitsanforderungen benötigen.

>[!NOTE]
>
>Adobe empfiehlt, immer auf die XSS-Schutz-API zuzugreifen, indem Sie die [Von AEM bereitgestellte XSSAPI](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/xss/XSSAPI.html).

Außerdem eine Webanwendungs-Firewall, z. B. [mod_security für Apache](https://www.modsecurity.org)kann eine zuverlässige, zentrale Kontrolle über die Sicherheit der Bereitstellungsumgebung bieten und vor zuvor nicht erkannten Cross-Site-Scripting-Angriffen schützen.

## Zugang zu Cloud Service-Informationen {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs für die Cloud Service-Informationen und die OSGi-Einstellungen, die zum Sichern Ihrer Instanz erforderlich sind, werden im Rahmen der [Produktionsbereiter Modus](/help/sites-administering/production-ready.md). Dies bedeutet zwar, dass Sie die Konfiguration nicht manuell ändern müssen, es wird jedoch empfohlen, sie zu überprüfen, bevor Sie mit Ihrer Implementierung live gehen.

Wenn Sie [Integrieren Ihrer AEM-Instanz mit Adobe Experience Cloud](/help/sites-administering/marketing-cloud.md), verwenden Sie [Cloud Service-Konfigurationen](/help/sites-developing/extending-cloud-config.md). Informationen zu diesen Konfigurationen sowie alle erfassten Statistiken werden im Repository gespeichert. Adobe empfiehlt, dass Sie bei Verwendung dieser Funktion überprüfen, ob die Standardsicherheit für diese Informationen Ihren Anforderungen entspricht.

Das webservicesupport-Modul schreibt Statistiken und Konfigurationsinformationen unter:

`/etc/cloudservices`

Mit den Standardberechtigungen:

* Autorenumgebung: `read` für `contributors`

* Veröffentlichungsumgebung: `read` für `everyone`

## Schützen Sie sich vor Cross-Site Request Forgery-Angriffen {#protect-against-cross-site-request-forgery-attacks}

Weitere Informationen zu den Sicherheitsmechanismen, die AEM zur Abschwächung von CSRF-Angriffen einsetzt, finden Sie im Abschnitt [Sling Referrer Filter](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) der Sicherheits-Checkliste und in der [Dokumentation zum CSRF Protection Framework](/help/sites-developing/csrf-protection.md).
