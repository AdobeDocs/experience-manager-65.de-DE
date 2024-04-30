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
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 100%

---

# OWASP – Top 10{#owasp-top}

Das [Open Web Application Security Project](https://owasp.org/) (OWASP) führt eine Liste zu den seiner Meinung nach [zehn häufigsten Sicherheitsrisiken für Web-Anwendungen](https://owasp.org/www-project-top-ten/).

Diese sind unten aufgeführt – zusammen mit einer Erläuterung, wie CRX mit ihnen umgeht.

## 1. Injection {#injection}

* SQL – Vorbeugung per Design: Das Standard-Repository umfasst und erfordert keine herkömmliche Datenbank, denn alle Daten werden im Content-Repository gespeichert. Der Zugriff ist komplett auf authentifizierte Benutzende beschränkt und kann nur durch die JCR-API durchgeführt werden. SQL wird nur für Suchanfragen unterstützt (SELECT). Darüber hinaus bietet SQL Unterstützung für Werte-Binding.
* LDAP – Eine LDAP-Injection ist nicht möglich, da das Authentifizierungsmodul die Eingaben filtert und den Benutzerimport mithilfe der bind-Methode durchführt.
* BS – Aus der Anwendung heraus wird keine Shell-Ausführung durchgeführt.

## 2. Cross-Site-Scripting (XSS) {#cross-site-scripting-xss}

Die allgemeine Praxis zur Schadensbegrenzung besteht in der Codierung aller Ausgaben benutzergenerierter Inhalte mithilfe einer Server-seitigen XSS-Schutzbibliothek, die auf dem [OWASP Encoder](https://owasp.org/www-project-java-encoder/) und [AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) basiert.

XSS hat sowohl bei den Tests als auch bei der Entwicklung eine hohe Priorität und alle festgestellten Probleme werden (in der Regel) umgehend behoben.

## 3. Fehler in Authentifizierung und Session Management {#broken-authentication-and-session-management}

AEM nutzt fundierte, bewährte Authentifizierungstechniken und greift hierzu auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) und [Apache Sling](https://sling.apache.org/) zurück. In AEM werden keine Browser-/HTTP-Sitzungen verwendet.

## 4. Unsichere direkte Objektreferenzen {#insecure-direct-object-references}

Jeglicher Zugriff auf Datenobjekte wird durch ein Repository vermittelt und daher durch die rollenbasierte Zugriffssteuerung beschränkt.

## 5. Cross-Site Request Forgery (CSRF) {#cross-site-request-forgery-csrf}

Auf das Risiko der Cross-Site Request Forgery (CSRF) wird durch die automatische Einschleusung eines kryptografischen Tokens in alle Formulare und AJAX-Anforderungen sowie durch die Verifizierung dieses Tokens auf dem Server bei jedem POST eingegangen.

Darüber hinaus ist AEM mit einem Referrer-Header-basierten Filter ausgestattet, der so konfiguriert werden kann, dass er *nur* POST-Anforderungen von bestimmten Hosts (in einer Liste definiert) zulässt.

## 6. Sicherheitsrelevante Fehlkonfiguration {#security-misconfiguration}

Es kann nicht garantiert werden, dass sämtliche Software immer korrekt konfiguriert ist. Allerdings versucht Adobe, so viel Hilfe wie möglich bereitzustellen und die Konfiguration so einfach wie möglich zu gestalten. Darüber hinaus ist AEM mit [integrierten Sicherheitsintegritätsprüfungen](/help/sites-administering/operations-dashboard.md) ausgestattet, die Ihnen bei der Überwachung der Sicherheitskonfiguration auf einen Blick helfen.

In der [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) finden Sie weitere Informationen, die Ihnen Schritt für Schritt Härtungsanweisungen bereitstellen.

## 7. Unsicherer kryptografischer Speicher {#insecure-cryptographic-storage}

Die Kennwörter werden als kryptografische Hashes im Benutzerknoten gespeichert. Solche Knoten können standardmäßig nur von der Administratorin bzw. dem Administrator und von der Benutzerin bzw. dem Benutzer selbst gelesen werden.

Sensible Daten wie Drittanbieter-Ameldedaten sind in verschlüsselter Form mithilfe einer FIPS 140-2-zertifizierten kryptografischen Bibliothek gespeichert.

## 8. Fehlgeschlagene Beschränkung des URL-Zugriffs {#failure-to-restrict-url-access}

Das Repository ermöglicht die Einstellung von [feinabgestimmten Rechten (wie durch JCR angegeben)](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) für jede Person bzw. Gruppe unter jedem beliebigen Pfad über Zugriffssteuerungseinträge. Zugriffbeschränkungen werden durch das Repository durchgesetzt.

## 9. Unzureichende Transportschichtsicherheit {#insufficient-transport-layer-protection}

Dieses Risiko wird durch die Server-Konfiguration gemindert (z. B. ausschließliche Verwendung von HTTPS).

## 10. Ungeprüfte Um- und Weiterleitungen {#unvalidated-redirects-and-forwards}

Dieses Risiko wird durch die Beschränkung aller Umleitungen an benutzerseitig bereitgestellte Ziele auf interne Standorte gemindert.
