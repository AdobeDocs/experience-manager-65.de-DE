---
title: OWASP – Top 10
description: Erfahren Sie, wie AEM mit den zehn wichtigsten OWASP-Sicherheitsrisiken umgeht.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 8b2a2f1d-8286-4ba5-8fe2-627509c72a45
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 33%

---

# OWASP – Top 10{#owasp-top}

Die [Sicherheitsprojekt für Webanwendungen öffnen](https://owasp.org/) (OWASP) führt eine Liste dessen, was sie als [Top 10 der Sicherheitsrisiken von Web-Anwendungen](https://owasp.org/www-project-top-ten/).

Diese sind unten aufgeführt, zusammen mit einer Erläuterung, wie CRX mit ihnen umgeht.

## 1. Einspritzung {#injection}

* SQL - Vom Design verhindert: Die standardmäßige Repository-Einrichtung umfasst keine herkömmliche Datenbank, und es ist auch keine herkömmliche Datenbank erforderlich. Alle Daten werden im Content-Repository gespeichert. Der Zugriff ist auf authentifizierte Benutzer beschränkt und kann nur über die JCR-API erfolgen. SQL wird nur für Suchabfragen unterstützt (SELECT). Darüber hinaus bietet SQL Unterstützung für die Wertbindung.
* LDAP - LDAP-Einschleusung ist nicht möglich, da das Authentifizierungsmodul die Eingabe filtert und den Benutzerimport mit der Bind-Methode durchführt.
* Betriebssystem: Es wird keine Shell-Ausführung innerhalb des Programms durchgeführt.

## 2. Cross-Site-Scripting (XSS) {#cross-site-scripting-xss}

Die allgemeine Praxis zur Schadensbegrenzung besteht in der Codierung aller Ausgaben benutzergenerierter Inhalte mithilfe einer Server-seitigen XSS-Schutzbibliothek, die auf dem [OWASP Encoder](https://owasp.org/www-project-java-encoder/) und [AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) basiert.

XSS hat sowohl bei den Tests als auch bei der Entwicklung eine hohe Priorität und alle festgestellten Probleme werden (in der Regel) umgehend behoben.

## 3. Fehler in Authentifizierung und Session Management {#broken-authentication-and-session-management}

AEM nutzt fundierte, bewährte Authentifizierungstechniken und greift hierzu auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) und [Apache Sling](https://sling.apache.org/) zurück. In AEM werden keine Browser-/HTTP-Sitzungen verwendet.

## 4. Unsichere direkte Objektverweise {#insecure-direct-object-references}

Der gesamte Zugriff auf Datenobjekte wird durch das Repository vermittelt und daher durch die rollenbasierte Zugriffssteuerung eingeschränkt.

## 5. Cross-Site Request Forgery (CSRF) {#cross-site-request-forgery-csrf}

Auf das Risiko der Cross-Site Request Forgery (CSRF) wird durch die automatische Einschleusung eines kryptografischen Tokens in alle Formulare und AJAX-Anforderungen sowie durch die Verifizierung dieses Tokens auf dem Server bei jedem POST eingegangen.

Darüber hinaus ist AEM mit einem Referrer-Header-basierten Filter ausgestattet, der so konfiguriert werden kann, dass er *nur* POST-Anforderungen von bestimmten Hosts (in einer Liste definiert) zulässt.

## 6. Fehlerhafte Sicherheitskonfiguration {#security-misconfiguration}

Es ist unmöglich zu garantieren, dass die gesamte Software immer korrekt konfiguriert ist. Adobe ist jedoch bestrebt, möglichst viele Anleitungen zu geben und die Konfiguration so einfach wie möglich zu gestalten. Darüber hinaus wird AEM ausgeliefert mit [Integrierte Sicherheits-Konsistenzprüfungen](/help/sites-administering/operations-dashboard.md) Damit können Sie die Sicherheitskonfiguration auf einen Blick überwachen.

Überprüfen Sie die [Sicherheitscheckliste](/help/sites-administering/security-checklist.md) Für weitere Informationen, die Ihnen Schritt-für-Schritt-Härtungsanweisungen bereitstellen.

## 7. Unsichere kryptografische Speicherung {#insecure-cryptographic-storage}

Kennwörter werden als kryptografische Hashes im Benutzerknoten gespeichert. Standardmäßig können solche Knoten nur vom Administrator und vom Benutzer selbst gelesen werden.

Sensible Daten wie Anmeldeinformationen von Drittanbietern werden mithilfe einer nach FIPS 140-2 zertifizierten kryptografischen Bibliothek verschlüsselt gespeichert.

## 8. URL-Zugriff nicht einschränken {#failure-to-restrict-url-access}

Das Repository ermöglicht die Einstellung von [Fein abgestimmte Berechtigungen (wie durch JCR angegeben)](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) für jeden Benutzer bzw. jede Gruppe unter jedem beliebigen Pfad über Zugriffssteuerungseinträge. Zugriffbeschränkungen werden durch das Repository durchgesetzt.

## 9. Unzureichende Transportschichtsicherheit {#insufficient-transport-layer-protection}

Wird durch die Server-Konfiguration gemildert (z. B. nur HTTPS).

## 10. Ungeprüfte Um- und Weiterleitungen {#unvalidated-redirects-and-forwards}

Dieses Risiko wird durch die Beschränkung aller Umleitungen an benutzerseitig bereitgestellte Ziele auf interne Standorte gemindert.
