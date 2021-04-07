---
title: OWASP – Top 10
seo-title: OWASP – Top 10
description: Erfahren Sie, wie AEM mit den 10 häufigsten OWASP-Sicherheitsrisiken umgeht.
seo-description: Erfahren Sie, wie AEM mit den 10 häufigsten OWASP-Sicherheitsrisiken umgeht.
uuid: a5a7e130-e15b-47ae-ba21-448f9ac76074
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: e5323ae8-bc37-4bc6-bca6-9763e18c8e76
exl-id: 8b2a2f1d-8286-4ba5-8fe2-627509c72a45
feature: Sicherheit
translation-type: tm+mt
source-git-commit: 9134130f349c6c7a06ad9658a87f78a86b7dbf9c
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 89%

---

# OWASP – Top 10{#owasp-top}

Das [Open Web Application Security Project](https://www.owasp.org) (OWASP) führt eine Liste zu den ihrer Meinung nach [10 häufigsten Sicherheitsrisiken für Webanwendungen](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

Diese sind unten aufgeführt – zusammen mit einer Erläuterung, wie CRX mit ihnen umgeht.

## 1. Injection {#injection}

* SQL – Vorbeugung durch konstruktive Maßnahmen: Das Standard-Repository umfasst und erfordert keine herkömmliche Datenbank, denn alle Daten werden im Inhalts-Repository gespeichert. Der Zugriff ist komplett auf authentifizierte Benutzer beschränkt und kann nur durch die JCR-API durchgeführt werden. SQL wird nur für Suchanfragen unterstützt (Auswählen). Darüber hinaus bietet SQL Unterstützung für Werte-Binding.
* LDAP – Die LDAP-Injection ist nicht möglich, da das Authentifizierungsmodul die Eingaben filtert und den Benutzerimport mithilfe der bind-Methode durchführt.
* BS – Aus der Anwendung heraus wird keine Shell-Ausführung durchgeführt.

## 2. Cross-Site Scripting (XSS)  {#cross-site-scripting-xss}

Die allgemeine Praxis zur Schadensbegrenzung besteht in der Codierung aller Ausgaben benutzergenerierter Inhalte mithilfe einer serverseitigen XSS-Schutzbibliothek, die auf dem [OWASP Encoder](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project) und [AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) basiert.

XSS hat sowohl bei den Tests als auch bei der Entwicklung eine hohe Priorität und alle festgestellten Probleme werden (in der Regel) umgehend behoben.

## 3. Fehler in Authentifizierung und Session Management {#broken-authentication-and-session-management}

AEM nutzt fundierte, bewährte Authentifizierungstechniken und greift hierzu auf [Apache Jackrabbit](https://jackrabbit.apache.org/) und [Apache Sling](https://sling.apache.org/) zurück. In AEM werden keine Browser-/HTTP-Sitzungen verwendet.

## 4. Unsichere direkte Objektreferenzen {#insecure-direct-object-references}

Jeglicher Zugriff auf Datenobjekte wird durch ein Repository vermittelt und daher durch die rollenbasierte Zugriffssteuerung beschränkt.

## 5. Cross-Site Request Forgery (CSRF)  {#cross-site-request-forgery-csrf}

Cross-Site Request Forgery (CSRF) wird durch die automatische Injektion eines kryptografischen Tokens in alle Formulare und AJAX Anforderungen sowie die Überprüfung dieses Tokens auf dem Server für jede POST abgemildert.

Darüber hinaus verfügt AEM über einen Werber-Header-basierten Filter, der so konfiguriert werden kann, dass nur *nur* Anfragen von bestimmten Hosts (in einer Liste definiert) zulässig sind.

## 6. Sicherheitsrelevante Fehlkonfiguration {#security-misconfiguration}

Es kann nicht garantiert werden, dass sämtliche Software immer korrekt konfiguriert ist. Allerdings versuchen wir, so viel Hilfe wie möglich bereitzustellen und die Konfiguration so einfach wie möglich zu gestalten. Darüber hinaus ist AEM mit [integrierten Sicherheitsintegritätsprüfungen](/help/sites-administering/operations-dashboard.md) ausgestattet, die Ihnen bei der Überwachung der Sicherheitskonfiguration auf einen Blick helfen.

In der [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) finden Sie weitere Informationen, die Ihnen Schritt für Schritt Härtungsanweisungen bereitstellen.

## 7. Unsicherer kryptografischer Speicher {#insecure-cryptographic-storage}

Die Kennwörter werden als kryptografische Hashes im Benutzerknoten gespeichert. Solche Knoten können standardmäßig nur vom Administrator und vom Benutzer selbst gelesen werden.

Sensible Daten wie die Drittanbieteranmeldedaten sind in verschlüsselter Form mithilfe einer FIPS 140-2-zertifizierten kryptografischen Bibliothek gespeichert

## 8. Fehlgeschlagene Beschränkung des URL-Zugriffs  {#failure-to-restrict-url-access}

Das Repository ermöglicht die Einstellung von [feinabgestimmten Rechten (wie durch JCR angegeben)](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html) für jeden Benutzer bzw. jede Gruppe unter jedem beliebigen Pfad über Zugriffssteuerungseinträge. Zugriffbeschränkungen werden durch das Repository durchgesetzt.

## 9. Unzureichende Transportschichtsicherheit {#insufficient-transport-layer-protection}

Dieses Risiko wird durch die Serverkonfiguration gemindert (z. B. nur HTTPS).

## 10. Ungeprüfte Um- und Weiterleitungen {#unvalidated-redirects-and-forwards}

Dieses Risiko wird durch die Beschränkung aller Umleitungen an benutzerseitig bereitgestellte Ziele auf interne Standorte gemindert.
