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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 33%

---

# OWASP – Top 10{#owasp-top}

Die [Webanwendungs-Sicherheitsprojekt öffnen](https://owasp.org/) (OWASP) verwaltet eine Liste dessen, was sie als [Die zehn häufigsten Sicherheitsrisiken für Webanwendungen](https://owasp.org/www-project-top-ten/).

Diese sind unten aufgeführt, zusammen mit einer Erläuterung, wie CRX mit ihnen umgeht.

## 1. Injektion {#injection}

* SQL - In der Konzeption verhindert: Die standardmäßige Repository-Einrichtung umfasst keine herkömmliche Datenbank und erfordert auch keine. Alle Daten werden im Inhalts-Repository gespeichert. Der Zugriff ist auf authentifizierte Benutzer beschränkt und kann nur über die JCR-API erfolgen. SQL wird nur für Suchabfragen (SELECT) unterstützt. Darüber hinaus bietet SQL Unterstützung für die Wertbindung.
* LDAP - Eine LDAP-Injektion ist nicht möglich, da das Authentifizierungsmodul die Eingabe filtert und den Benutzerimport mithilfe der Bindungsmethode durchführt.
* BS - In der Anwendung wird keine Shell-Ausführung ausgeführt.

## 2. Cross-Site Scripting (XSS) {#cross-site-scripting-xss}

Die allgemeine Praxis zur Schadensbegrenzung besteht in der Codierung aller Ausgaben benutzergenerierter Inhalte mithilfe einer Server-seitigen XSS-Schutzbibliothek, die auf dem [OWASP Encoder](https://owasp.org/www-project-java-encoder/) und [AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) basiert.

XSS hat sowohl bei den Tests als auch bei der Entwicklung eine hohe Priorität und alle festgestellten Probleme werden (in der Regel) umgehend behoben.

## 3. Fehler in Authentifizierung und Session Management {#broken-authentication-and-session-management}

AEM nutzt fundierte, bewährte Authentifizierungstechniken und greift hierzu auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) und [Apache Sling](https://sling.apache.org/) zurück. In AEM werden keine Browser-/HTTP-Sitzungen verwendet.

## 4. Unsichere direkte Objektreferenzen {#insecure-direct-object-references}

Der Zugriff auf Datenobjekte wird vom Repository vermittelt und daher durch rollenbasierte Zugriffskontrolle eingeschränkt.

## 5. Cross-Site Request Forgery (CSRF) {#cross-site-request-forgery-csrf}

Auf das Risiko der Cross-Site Request Forgery (CSRF) wird durch die automatische Einschleusung eines kryptografischen Tokens in alle Formulare und AJAX-Anforderungen sowie durch die Verifizierung dieses Tokens auf dem Server bei jedem POST eingegangen.

Darüber hinaus ist AEM mit einem Referrer-Header-basierten Filter ausgestattet, der so konfiguriert werden kann, dass er *nur* POST-Anforderungen von bestimmten Hosts (in einer Liste definiert) zulässt.

## 6. Sicherheitsfehler {#security-misconfiguration}

Es ist unmöglich zu garantieren, dass alle Software immer korrekt konfiguriert ist. Adobe bemüht sich jedoch, möglichst viele Anleitungen zur Verfügung zu stellen und die Konfiguration so einfach wie möglich zu gestalten. Außerdem AEM mit [Integrierte Sicherheits-Gesundheitskontrollen](/help/sites-administering/operations-dashboard.md) die Ihnen dabei helfen, die Sicherheitskonfiguration auf einen Blick zu verfolgen.

Überprüfen Sie die [Sicherheitscheckliste](/help/sites-administering/security-checklist.md) für weitere Informationen, die Ihnen eine schrittweise Anleitung zum Härten bieten.

## 7. Unsicherer kryptografischer Speicher {#insecure-cryptographic-storage}

Passwörter werden als kryptografische Hashes im Benutzerknoten gespeichert. Standardmäßig sind solche Knoten nur vom Administrator und vom Benutzer selbst lesbar.

Sensible Daten wie Drittanbieter-Anmeldeinformationen werden in verschlüsselter Form mit einer FIPS 140-2-zertifizierten kryptografischen Bibliothek gespeichert.

## 8. Fehler beim Einschränken des URL-Zugriffs {#failure-to-restrict-url-access}

Das Repository ermöglicht die Festlegung von [Präzise Berechtigungen (gemäß JCR)](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) für jeden einzelnen Benutzer oder jede Gruppe an einem beliebigen Pfad über Zugriffssteuerungseinträge. Zugriffbeschränkungen werden durch das Repository durchgesetzt.

## 9. Unzureichende Transportschichtsicherheit {#insufficient-transport-layer-protection}

Wird durch die Serverkonfiguration abgemildert (z. B. nur HTTPS verwenden).

## 10. Ungeprüfte Um- und Weiterleitungen {#unvalidated-redirects-and-forwards}

Dieses Risiko wird durch die Beschränkung aller Umleitungen an benutzerseitig bereitgestellte Ziele auf interne Standorte gemindert.
