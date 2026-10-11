---
title: OWASP – Top 10
description: Erfahren Sie, wie AEM mit den zehn häufigsten OWASP-Sicherheitsrisiken umgeht.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 8b2a2f1d-8286-4ba5-8fe2-627509c72a45
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
    internal-label: Administration and security
subfeature_v2:
  - id: c35bc059-fd80-4a01-91a6-e48da3c76758
    internal-label: Security practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 90%
---
# OWASP – Top 10{#owasp-top}

Das [Open Web Application Security Project](https://owasp.org/) (OWASP) führt eine Liste zu den seiner Meinung nach [zehn häufigsten Sicherheitsrisiken für Web-Anwendungen](https://owasp.org/www-project-top-ten/).

Diese sind unten aufgeführt – zusammen mit einer Erläuterung, wie CRX mit ihnen umgeht.

## &#x200B;1. Einspritzung {#injection}

* SQL – Vorbeugung per Design: Das Standard-Repository umfasst und erfordert keine herkömmliche Datenbank, denn alle Daten werden im Content-Repository gespeichert. Der Zugriff ist komplett auf authentifizierte Benutzende beschränkt und kann nur durch die JCR-API durchgeführt werden. SQL wird nur für Suchanfragen unterstützt (SELECT). Darüber hinaus bietet SQL Unterstützung für Werte-Binding.
* LDAP – Eine LDAP-Injection ist nicht möglich, da das Authentifizierungsmodul die Eingaben filtert und den Benutzerimport mithilfe der bind-Methode durchführt.
* BS – Aus der Anwendung heraus wird keine Shell-Ausführung durchgeführt.

## &#x200B;2. Cross-Site-Scripting (XSS) {#cross-site-scripting-xss}

Die allgemeine Praxis zur Schadensbegrenzung besteht in der Codierung aller Ausgaben benutzergenerierter Inhalte mithilfe einer Server-seitigen XSS-Schutzbibliothek, die auf dem [OWASP Encoder](https://owasp.org/www-project-java-encoder/) und [AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) basiert.

XSS hat sowohl bei den Tests als auch bei der Entwicklung eine hohe Priorität und alle festgestellten Probleme werden (in der Regel) umgehend behoben.

## &#x200B;3. Fehlerhafte Authentifizierung und Sitzungsverwaltung {#broken-authentication-and-session-management}

AEM nutzt fundierte, bewährte Authentifizierungstechniken und greift hierzu auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) und [Apache Sling](https://sling.apache.org/) zurück. In AEM werden keine Browser-/HTTP-Sitzungen verwendet.

## &#x200B;4. Unsichere direkte Objektverweise {#insecure-direct-object-references}

Jeglicher Zugriff auf Datenobjekte wird durch ein Repository vermittelt und daher durch die rollenbasierte Zugriffssteuerung beschränkt.

## 5. Cross-Site Request Forgery (CSRF) {#cross-site-request-forgery-csrf}

Auf das Risiko der Cross-Site Request Forgery (CSRF) wird durch die automatische Einschleusung eines kryptografischen Tokens in alle Formulare und AJAX-Anforderungen sowie durch die Verifizierung dieses Tokens auf dem Server bei jedem POST eingegangen.

Darüber hinaus ist AEM mit einem Referrer-Header-basierten Filter ausgestattet, der so konfiguriert werden kann, dass er *nur* POST-Anforderungen von bestimmten Hosts (in einer Liste definiert) zulässt.

## &#x200B;6. Fehlerhafte Sicherheitskonfiguration {#security-misconfiguration}

Es kann nicht garantiert werden, dass sämtliche Software immer korrekt konfiguriert ist. Allerdings versucht Adobe, so viel Hilfe wie möglich bereitzustellen und die Konfiguration so einfach wie möglich zu gestalten. Darüber hinaus ist AEM mit [integrierten Sicherheitsintegritätsprüfungen](/help/sites-administering/operations-dashboard.md) ausgestattet, die Ihnen bei der Überwachung der Sicherheitskonfiguration auf einen Blick helfen.

In der [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) finden Sie weitere Informationen, die Ihnen Schritt für Schritt Härtungsanweisungen bereitstellen.

## &#x200B;7. Unsicherer kryptografischer Speicher {#insecure-cryptographic-storage}

Die Kennwörter werden als kryptografische Hashes im Benutzerknoten gespeichert. Solche Knoten können standardmäßig nur von der Administratorin bzw. dem Administrator und von der Benutzerin bzw. dem Benutzer selbst gelesen werden.

Sensible Daten wie Drittanbieter-Ameldedaten sind in verschlüsselter Form mithilfe einer FIPS 140-2-zertifizierten kryptografischen Bibliothek gespeichert.

## &#x200B;8. URL-Zugriff kann nicht eingeschränkt werden {#failure-to-restrict-url-access}

Das Repository ermöglicht die Einstellung von [feinabgestimmten Rechten (wie durch JCR angegeben)](https://experienceleague.adobe.com/en/tools/aem-api-documentation/spec/jcr/2.0/16_Access_Control_Management.html) für jede Person bzw. Gruppe unter jedem beliebigen Pfad über Zugriffssteuerungseinträge. Zugriffbeschränkungen werden durch das Repository durchgesetzt.

## &#x200B;9. Unzureichender Schutz der Transportschicht {#insufficient-transport-layer-protection}

Dieses Risiko wird durch die Server-Konfiguration gemindert (z. B. ausschließliche Verwendung von HTTPS).

## &#x200B;10. Nicht validierte Weiterleitungen und Weiterleitungen {#unvalidated-redirects-and-forwards}

Dieses Risiko wird durch die Beschränkung aller Umleitungen an benutzerseitig bereitgestellte Ziele auf interne Standorte gemindert.
