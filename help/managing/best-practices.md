---
title: Verwalten von Projekten – Checkliste mit Best Practices
description: Die Verwaltung eines Projekts zur Implementierung von Adobe Experience Manager (AEM) erfordert Planung und Know-how. Die Checklisten für Projekte bieten eine Zusammenstellung der Best Practices für die Projektabwicklung. Sie führen Sie durch alle Phasen des Projektlebenszyklus und bieten eine allgemeine Statusüberwachung.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing-checklist, introduction
content-type: reference
docset: aem65
exl-id: 94b91996-d2b2-4d4a-b770-334cfa2dc0b7
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Admin,Architect,Data Architect,Developer,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '3214'
ht-degree: 100%

---

# Verwalten von Projekten – Checkliste für Best Practices{#managing-projects-best-practices-checklist}

Die Verwaltung eines Projekts zur Implementierung von Adobe Experience Manager (AEM) erfordert Planung und Know-how. Nur so werden Sie sich der Probleme und (entsprechenden) Entscheidungen bewusst, die Sie vor und während der Umsetzung des Projekts treffen müssen.

Als Hilfestellung für Sie umfassen die Best Practices Folgendes:

* eine [interaktive Checkliste](/help/managing/best-practices-checklist.md), die es ermöglicht den Fortschritt mit diesen Best Practices nachzuverfolgen und zu überwachen:

   * Sie definiert Inputs und die zu erbringenden Leistungen nach Phase, Meilenstein und Rolle.
   * Sie stellt automatische Übersichten (Qualität, Konsistenz und Vollständigkeit) bereit, um den Fortschritt und die Konsistenz des Projekts anzuzeigen.

* Dokumentation, die auf der [Checkliste](/help/managing/best-practices-checklist.md) basiert, mit folgenden Details:

   * [Projekt-Heartbeat](#projectheartbeat)-Analyse
   * Überblick über den [Status nach Rolle](#status-by-role)
   * [Phasen und Meilensteine](#phases-and-milestones);
   * [Schlüsselrolle](#persona) und deren Beteiligung in jeder (relevanten) Phase.
   * [Glossar](/help/managing/best-practices-glossary.md) der [erforderlichen Dokumente und Ergebnisse](#required-documents-and-deliverables)

* [weiterführendes Referenzmaterial](/help/managing/best-practices-further-reference.md) für zusätzliche Informationen zu bestimmten Bereichen.

## Dashboard zum Projekt-Heartbeat {#project-heartbeat-dashboard}

Das Arbeitsblatt zum **Projekt-Heartbeat** liefert einen grafischen Überblick über die wichtigsten Metriken des Projekts:

* **Phasenqualität**

   * Zeigt die Qualität der [erforderlichen Dokumente und zu erbringenden Leistungen](#required-documents-and-deliverables) für das gesamte Projekt an.

* **Phasenkonsistenz**

   * Eine detaillierte Statusanzeige für das Projekt; nützlich, um Bereiche herauszustellen, die gefährdet sein könnten.

* **Phasenvollständigkeit**

   * Zeigt zu jedem Zeitpunkt des Projekts an, wie viel bereits in den jeweiligen Phasen des Projekts abgeschlossen wurde.

## Status nach Rolle {#status-by-role}

Das Arbeitsblatt **Status nach Rolle** zeigt eine detaillierte Aufstellung der [**Konsistenz**, Qualität und **Vollständigkeit**](#projectheartbeat), sortiert nach **[Phase](#phases-and-milestones)** und **[Rolle](#persona)**.

## Phasen und Meilensteine {#phases-and-milestones}

Der Projektplan wird in einzelne (grobe) Phasen unterteilt.

Jede Phase enthält ihre eigenen Milestones. Für jede [Rolle](#persona) werden die zutreffenden Milestones gemeinsam mit den Dokumenten aufgelistet, die zur Erreichung bestimmter Ergebnisse notwendig sind.

>[!NOTE]
>
>Es gibt keine direkte 1:1-Beziehung zwischen den einzelnen erforderlichen Dokumenten und zu erbringenden Leistungen.

### Vorbereitung {#preparation}

Die Vorbereitung des Projekts bildet die Grundlage für das gesamte Projekt. Definieren Sie Schlüsselanforderungen gemeinsam mit klaren Zielen und Erwartungen für die folgenden Bereiche:

* **Geschäftsgrundsatz**

   * Die wesentlichen Gründe und Rechtfertigungen für die Umsetzung des Projekts.

* **Umfang und Zeitplan**

   * Ein grundlegender Umfang und grober Zeitplan sollten zur Verfügung gestellt werden, um zu definieren, was notwendig ist und in welchem Zeitrahmen. Wenn es zur Klärung der Situation beiträgt, können Sie auch definieren, was außerhalb dieses Umfangs liegt.

Wie Sie Ihr Projekt planen, ausführen und Ihre Lösung implementieren, ist abhängig von den Einschränkungen, denen Sie unterliegen, z. B. festes Budget, fester Zeitplan, Menge des Inhalts, erforderliche Qualität.

Wie immer hat die Anpassung eines dieser Faktoren Auswirkungen auf die anderen. Eine Verkürzung der Zeit bei gleichbleibender Qualität beispielsweise führt wahrscheinlich zu einem Preisanstieg bei gleichzeitiger Reduktion der Menge an Inhalten, die bearbeitet werden können. Das Budget ist häufig ein Schlüsselfaktor und ein solcher Aspekt darf nicht vergessen werden.

Die vier Faktoren:

![projectphases_fourphases](assets/projectphases_fourphases.png)

#### Milestones {#milestones}

* **Validierung**

  In dieser Phase müssen Sie die Ziele für das Projekt validieren und bestätigen. Beispiel:

   * Was möchten Sie erreichen/bereitstellen?
   * Wer profitiert davon?
   * Was ist der Umfang?

      * Wenn es zur Klärung der Situation beiträgt, können Sie auch definieren, was außerhalb dieses Umfangs liegt.

   * Wie definieren Sie Erfolg?
   * Wie messen Sie Erfolg?
   * Welche technischen und geschäftlichen Anforderungen gibt es?
   * Gibt es bestehende alte Systeme, die ersetzt werden müssen, und wenn ja, müssen Daten verschoben werden?
   * Wer ist beteiligt?
   * Wie messen Sie den Fortschritt?
   * Wie oft überprüfen Sie den Fortschritt während der Dauer des Projekts?

* **Budget**

  Bevor Sie ein Projekt beginnen, benötigen Sie eine zuverlässige, realistische Schätzung der Kosten für dessen Implementierung:

   * Verwenden Sie die Informationen aus den Validierungs-Meilensteinen als Grundlage für die Berechnung.
   * Seien Sie bei den Schätzungen realistisch.
   * Berücksichtigen Sie Richtlinien, Verfahren oder Einschränkungen, denen die Kundin oder der Kunde möglicherweise unterliegt.
   * Berücksichtigen Sie Notfallpläne und Überprüfungsverfahren für den Fall, dass eine Überprüfung oder Verfeinerung des Budgets zu einem späteren Zeitpunkt notwendig sein sollte.
   * Bedenken Sie, dass Kosten auf viele Arten entstehen, z. B. durch Einkäufe, Verwendung von Ressourcen und Gebühren.

### Planung {#planning}

Die Planung des Projekts vertieft die Vorbereitung. Beginnen Sie damit, Ihre Ziele und Erwartungen in eine sorgfältig formulierte Roadmap umzuwandeln, die aus konkreten Aufgaben besteht, an eine klare Kommunikation gebunden ist und strenge Überprüfungen zur Messung des Fortschritts enthält.

#### Milestones {#milestones-1}

* **Übergabe**

  Durch eine saubere Übergabe wird sichergestellt, dass die entsprechenden Personen/Gruppen sich ihrer Verantwortung im Rahmen des Projekts bewusst sind.

  Vollständige Details sollten zur Verfügung gestellt bzw. erstellt werden, um zu gewährleisten, dass alle relevanten Aspekte vollständig klar sind, einschließlich Roadmap, Umfang, Anforderungen und KPIs.

* **Risikobewertung**

  Nutzen Sie die Risikobewertung, um unangenehme Überraschungen zu vermeiden und potenzielle Risiken gemeinsam mit deren Auswirkungen und Wahrscheinlichkeit zu erkennen und zu quantifizieren.

  Dies sollte früh im Projektlebenszyklus erfolgen, um sicherzustellen, dass jegliche Schwächen identifiziert und bewertet werden. Basierend auf den Ergebnissen können Sie die Projektbeteiligten darüber informieren, ob die Anforderungen vollständig umgesetzt werden können und, falls notwendig, ob es möglich ist, die Umsetzung und Nachverfolgung entsprechender Maßnahmen zu planen.

* **Kommunikation**

  Kommunikation ist immer der Schlüssel zum Erfolg eines jeden Projekts. Kommunizieren Sie klar und effizient, um sicherzustellen, dass alle Beteiligten:

   * an denselben grundlegenden Zielen arbeiten;
   * dieselbe Informationsgrundlage nutzen;
   * dieselben Kanäle verwenden.

* **Projektstart**

  Das Meeting zum Projektstart dient dazu, auf den Start des Projekts hinzuweisen. Bietet eine gute Gelegenheit für Folgendes:

   * Einladung aller interessierten Parteien (oder zumindest repräsentativer Personen aller Gruppen);
   * Präsentation von wichtigen Fakten zum Projekt;
   * Beantwortung von Fragen.
   * Stellen Sie sicher, dass alle Beteiligten über die gleiche Wissensgrundlage verfügen.
   * Sichern Sie sich das Engagement aller Beteiligten – es muss verdient werden.

      * Durch Einbeziehung der Hauptbeteiligten (einschließlich voraussichtlicher Autorinnen und Autoren) zu Beginn des Projekts erhöhen Sie Ihre Chancen, deren Engagement für das Projekt zu sichern.

### Entwicklungsvorbereitung {#development-preparation}

Die Entwicklungsplanung ist der Schlüssel, um zu gewährleisten, dass das Projekt auf einer soliden Grundlage und einem Team, das über die notwendigen Kenntnisse verfügt, aufbaut.

#### Milestones {#milestones-2}

* **Entwicklungs-Team – Besetzt und geschult**

  Bevor Sie mit einem Projekt beginnen, sollten Sie sicherstellen, dass Ihr Entwicklungs-Team angemessen besetzt ist und dass alle Team-Mitglieder für die vorliegende Aufgabe geschult sind.

* **Inhaltsarchitektur**

  Die Inhaltsarchitektur definiert und beschreibt die zukünftige Architektur des Inhalts, einschließlich:

   * Inhaltsstruktur, einschließlich Assets
   * Grundstrukturen, einschließlich Kampagnen usw.
   * Strukturen mit mehreren Sites und Sprachen (MSM, Übersetzung)
   * Unterstützende Inhalte (einschließlich Tags und Tagging-Konzepte)
   * Strategien für das Caching und die Wiederverwendung von Inhalten

* **Systemarchitektur**

  Die Systemarchitektur definiert die konzeptionelle Ansicht Ihres Systems, einschließlich (unter anderem):

   * [Systemstruktur](/help/sites-deploying/recommended-deploys.md#deployment-scenarios) für alle erforderlichen Umgebungen
   * Untersysteme
   * Drittanbietersysteme
   * Schnittstellen, Hardware, Software und menschliche Interaktionen
   * Server für jede Umgebung; siehe [Technische Anforderungen](/help/sites-deploying/technical-requirements.md) und [Hardware-Skalierungsrichtlinien](/help/managing/hardware-sizing-guidelines.md);

   * Prozesse für jede Umgebung, z. B. Bereitstellungs- und Wartungsanforderungen
   * Wartungsaktivitäten (Datastore GC, TarPM-Optimierung usw.)
   * [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de)-Caching
   * [Clustering](/help/sites-deploying/recommended-deploys.md#deployment-scenarios) beim Veröffentlichen/automatischen Teilen;
   * Leistung für die Client-Seite (JS minify, concat, CSS-Sprites, Gesamtanzahl der HTTP-Anfragen und Sonstiges)

* **Anwendungsarchitektur**

  Die Anwendungsarchitektur definiert und beschreibt das Verhalten der vorgeschlagenen Anwendungen.

  Ihr Fokus liegt auf Folgendem:

   * Interaktion der Anwendungen miteinander und mit Benutzenden
   * Daten, die von den Anwendungen genutzt und produziert werden sollen, nicht ihre interne Struktur

  Die Definitionen sollten Folgendes umfassen:

   * Grundlegende Code-Struktur für das Projekt
   * Code-Artefakte (Bundles, Pakete usw.)
   * Aufschlüsselung der Vorlagen/Komponenten und ihrer Beziehungen
   * Allgemeine Details der erforderlichen Anpassungen (spezifische Überlagerungen werden später folgen)
   * Entwurf der für die Lösung erforderlichen Workflows (z. B. Inhaltserstellung, Genehmigung, Veröffentlichung, Transformationen, Importe und Exporte)
   * Besondere Berücksichtigung komplexer Module wie MSM, Commerce, Drittanbieterintegration

* **Systemintegration**

  Die Systemintegration erfordert Ihre Planung (die Implementierung erfolgt danach):

   * Zusammenführen sämtlicher Teilsysteme und [Lösungsintegrationen](/help/sites-administering/integration.md) zu einem schlüssig operierenden System
   * Integrieren von Drittsystemen zusammen mit besonderer Berücksichtigung von Aspekten wie offline/online, Client-/Browser-seitig oder Handhabung der Ausfallsicherung, wenn ein Drittsystem ausfällt

* **Testkonzept**

  Bevor Sie mit der Entwicklung beginnen, sollten Sie ein tiefgehendes und umfassendes Konzept für alle [Testanforderungen](/help/sites-developing/planning.md) des Projekts erstellen.

  Dies sollte (unter anderem) Folgendes umfassen:

   * Details aller durchzuführenden Tests
   * Vorbereitung des für diese Tests erforderlichen Inhalts
   * Informationen zu den zu verwendenden Testwerkzeugen
   * Detaillierte Angaben dazu, wer an Tests beteiligt sein wird, insbesondere Gruppen außerhalb des Qualitätssicherungs-Teams
   * Details zur Testautomatisierung, z. B. mit Selenium oder dem AEM-Entwicklungsmodus

* **Experience Design**

  Experience Design (XD) umfasst das Entwerfen des Benutzererlebnisses für Ihre Lösung.

  Das Benutzererlebnis sollte sowohl für Ihre Autorinnen und Autoren als auch für die Endbenutzenden Ihrer Website analysiert und entwickelt werden.

* **Support-Setup**

  Vor der Entwicklung sollten alle Unterstützungsprozesse erstellt werden, die zur Bereitstellung, zur Veröffentlichung, zum Testen und zur Meldung von Problemen notwendig sind.

  Informationen finden Sie auch im [Adobe Support-Portal](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support).

### Betriebsplanung und Betrieb {#operations-planning-and-operations}

Auch die Abläufe müssen angemessen geplant werden, damit Sie über die notwendigen Umgebungen verfügen – in sämtlichen Phasen des Projektzyklus. Sie benötigen auch die entsprechenden Prozesse, um sie zu verwalten.

#### Milestones {#milestones-3}

* **Berechtigungen**

  Sie müssen ein Rollen- und Rechtekonzept für alle Benutzenden/Gruppen planen und implementieren, die die Lösung verwenden.

  Beispiel:

   * Eine Liste von Rollen (d. h. Gruppen) mit jeweils festgelegten `read`/`write`-Zugriffsdefinitionen

   * Festlegung der Verwendung von Berechtigungen, die einen Einfluss auf die Veröffentlichungsumgebung haben, z. B. `replicate`
   * Für Benutzer mit minimalen Berechtigungen sollten Workflows definiert werden
   * Benutzer in der Gruppe `editor` sollten weder über `admin`-Rechte verfügen noch Teil der Gruppe `administrators` sein

  Weitere Informationen finden Sie unter [Benutzeradministration und Sicherheit](/help/sites-administering/security.md).

* **Überwachung und Wartung**

  Überwachung und Wartung sind Schlüsselaspekte, um den reibungslosen Ablauf der Lösung nach der Einführung zu gewährleisten. Hierzu ist Folgendes zu definieren:

   * Was muss überwacht werden
   * Wartungsaufgaben, sowohl für reguläre als auch für Sonderfälle

  Weitere Informationen finden Sie unter [Überwachung und Wartung](/help/sites-deploying/monitoring-and-maintaining.md).

* **Migration**

  Alle Inhalte aus dem alten System sollten für die Migration überprüft und validiert werden.

* **Wiederherstellungsplan**

  Stellen Sie sicher, dass Sie einen Wiederherstellungsplan haben. Dieser muss in Notfällen verfügbar sein, damit die Verwendung von AEM für die Produktion sichergestellt ist. Dies sollte u. a. Situationen wie Backup, Wiederherstellung und Ausfallsicherung abdecken.

### Entwicklung {#development}

Entwicklung ist eine entscheidende Phase, die mehr erfordert als nur Programmieren.

#### Milestones {#milestones-4}

* **Bereitstellungsumgebung**

  Planen und dokumentieren Sie Ihre Entwicklungsumgebung, einschließlich:

   * Architektur
   * [Entwicklungswerkzeugen](/help/sites-developing/dev-tools.md)

      * Eine typische Umgebung besteht aus:

         * einem Nachverfolgungssystem für Probleme, z. B. Jira
         * einer IDE, z. B. Eclipse
         * einem Build-Management-Tool, z. B. Maven
         * einem Werkzeug für die fortwährende Integration, wie etwa Jenkins;
         * einem Tool für die Versionskontrolle, z. B. GIT/SVN
         * einem Repository-Manager für Build-Artefakte, z. B. Archiva/Nexus

   * Integration/Abhängigkeiten von Software von Drittanbietern
   * [Integration/Abhängigkeiten von der Lösung;](/help/sites-administering/integration.md)
   * Bereitstellungsintervall

* **Testsystem**

  Planen und dokumentieren Sie Ihre Testumgebung, einschließlich:

   * Architektur
   * Abhängigkeiten von Entwicklungs-Builds, z. B. nächtliche Builds
   * Möglichkeiten oder Einschränkungen beim Testen der Integration/Abhängigkeiten von Software von Drittanbietern
   * Test-Tools
   * Strategie für automatisierte Tests

* **Produktionssystem**

  Planen und dokumentieren Sie Ihre Produktionsumgebung, einschließlich:

   * Architektur
   * Bereitstellungsintervall
   * Integration/Abhängigkeiten von Software von Drittanbietern
   * Sicherheitskonfiguration
   * Bestätigung der Grundleistung durch Ausführen eines [Tough Day](/help/sites-developing/tough-day.md)-Tests bei der Produktionskonfiguration;
   * Anforderungen an Leistungstests; siehe [Best Practices für Qualitätssicherung](/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance)

* **Integration**

  Planen, dokumentieren und testen Sie alle Aspekte des Systems und der [Lösungsintegration](/help/sites-administering/integration.md), einschließlich:

   * eine Strategie für automatisierte Tests
   * automatisierte Prozesse zum [Verschieben von Anwendungen von der Entwicklung zum Test, anschließend in die Produktion](/help/managing/enterprise-devops.md#code-movement)
   * automatisierte Prozesse zum [Verschieben von Inhalten von der Produktion zu Test und Entwicklung](/help/managing/enterprise-devops.md#content-movement)

* **Migration**

  Planen, dokumentieren und testen Sie alle Aspekte der Inhaltsmigration, einschließlich:

   * Inhaltsarchitektur
   * Migrationsstrategie

* **Kommunikation**

  Stellen Sie sicher, dass alle Team-Mitglieder und Projektbeteiligten bei Bedarf auf dem neuesten Stand gehalten werden.

* **Dokumentation**

  Dokumentieren Sie die Lösung vollständig, einschließlich:

   * Benutzerhandbuch
   * alle Anpassungen, die sich auf Upgrades auswirken können
   * Versionshinweise

### Leistung und Tests {#performance-and-testing}

Sobald die neue Anwendung verfügbar ist, muss sie in Bezug auf Funktionalität und [Leistung](/help/sites-deploying/configuring-performance.md) strengen Tests unterzogen werden.

>[!NOTE]
>
>Jedes testende Team sollte die Möglichkeit haben, beim Liefern der Testergebnisse neutral zu bleiben.
>
>Es obliegt der Projektleitung, die Auswirkungen der Ergebnisse zu bewerten und über geeignete Maßnahmen zu entscheiden.

#### Milestones {#milestones-5}

* **Test zur Endbenutzerakzeptanz**

  [Tests zur Benutzerakzeptanz](/help/sites-developing/acceptance-signoff.md) sind essenziell, um zu gewährleisten, dass:

   * die Lösung die Anforderungen der Kundschaft/Benutzenden erfüllt
   * Kundschaft/Benutzende die Lösung akzeptieren (Funktion, Design und Leistung)

  eine formelle Checkliste sollte für die Kundenübergabe erstellt werden, die idealerweise automatisiert ist und nächtlich gegenüber einer Momentaufnahme durchgeführt wird. Die Ergebnisse sollten an den Projekt-Manager oder das Entwickler-Tam weitergeleitet werden.

* **Leistungs- und Belastungstests**

  Leistungs- und Belastungstests werden verwendet, um sicherzustellen, dass die Lösung die erforderlichen Leistungsniveaus bei durchschnittlicher und bei höchster Belastung erfüllt.

  Weitere Informationen zu Leistungstests finden Sie unter:

   * [Leistungstests](/help/sites-deploying/configuring-performance.md)
   * [Planen und Ausführen von Tests](/help/sites-developing/planning.md)

   * [Allgemeine Leistungsrichtlinien](/help/sites-deploying/configuring-performance.md#basic-performance-guidelines)

  >[!NOTE]
  >
  >Dieser Prozess muss auch während der normalen Verwendung von AEM fortgeführt werden; die ersten Phasen sind jedoch am wichtigsten.

### Rollout {#rollout}

Der Rollout einer neuen Anwendung bedarf sorgfältiger Planung, um einen reibungslosen Ablauf der Live-Schaltung zu gewährleisten. Dazu gehört die Bestätigung eines hohen Sicherheitsniveaus, die Schulung aller potenziellen Benutzenden und die Durchführung mehrerer Testläufe, um zu bestätigen, dass alle Probleme behoben wurden.

#### Milestones {#milestones-6}

* **Vorbereitung**

  Vorbereitung und Planung tragen zu einem reibungslosen Rollout bei.

* **Schulung**

  Stellen Sie sicher, dass alle beteiligten Mitarbeitenden geschult wurden.

  Siehe [Adobe Experience Manager](https://training.adobe.com/training/courses.html#solution=adobeExperienceManager) im Kurskatalog.

* **Administratorschulung**

  Stellen Sie sicher, dass die Admins:

   * geschult wurden;
   * das entsprechende Schulungsmaterial erhalten haben;
   * die entsprechende Dokumentation erhalten haben.

* **Benutzerschulung**

  Stellen Sie sicher, dass die Autorinnen und Autoren:

   * geschult wurden;
   * das entsprechende Schulungsmaterial erhalten haben;
   * die entsprechende Dokumentation erhalten haben, z. B. das Benutzerhandbuch.

* **Penetrationstests**

  Penetrationstests simulieren einen Angriff auf ein Computer-System, um potenzielle Sicherheitslücken aufzudecken.

* **Penetrations-/Sicherheitstests**

  Führen Sie bestimmte Penetrationstests gemeinsam mit einem breiten Spektrum an Sicherheitstests durch, um die Sicherheit der Lösung zu gewährleisten.

  Weitere Informationen finden Sie in der [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).

### Live-Schaltung {#go-live}

Die Live-Schaltung sollte so reibungslos wie möglich verlaufen. Abermals sei daran erinnert, dass die letzten Schritte der Planung bedürfen, um eine saubere Ausführung zu erreichen.

#### Milestones {#milestones-7}

* **Vorbereitung**

  Vorbereitung und Planung helfen dabei, eine reibungslose Live-Schaltung sicherzustellen.

* **Sicherheit**

  Bestätigen Sie die Sicherheit der Lösung sowohl für interne als auch externe Benutzende und deren Inhalte.

* **Notfallversorgung**

  Stellen Sie sicher, dass alle Systeme, Verfahren und Mechanismen, die für die Notfallversorgung notwendig sind, vor der Live-Schaltung der Lösung vorhanden sind.

* **Support**

  Stellen Sie sicher, dass Support-Dienste vorhanden sind und bereitstehen.

* **Übergang**

  Planen Sie den Übergang in die Produktionsumgebung sowie zu den Benutzenden und führen Sie diesen aus.

* **Rollout**

  Bereiten Sie Feuerproben vor und führen Sie diese durch.

## Rolle {#persona}

Die Checklisten werden rollenabhängig entworfen. Diese Rollen sind wesentlich in den Projektzyklus involviert.

Es gibt auch [andere Rollen](#other-persona), die an bestimmten Aufgaben beteiligt sind.

### Projekt-Sponsorin oder Projekt-Sponsor {#project-sponsor}

Die Projekt-Sponsorin bzw. der Projekt-Sponsor ist:

* zuständig für die Bereitstellung/Präsentation des Business-Cases für das Projekt
* die Schlüsselfigur bei der Definition und Erstellung des Projektumfangs, einschließlich:

   * der Definition von Erfolg und den Kriterien hierfür;
   * der grundlegenden KPIs;

* erstellt Meilensteine basierend auf der Roadmap der Kundin oder des Kunden.

### Projekt-Manager {#project-manager}

Der Projekt-Manager ist:

* zuständig für die allgemeine Projektabwicklung, basierend auf den Vorgaben (z. B. Umfang, KPIs, Erfolgskriterien und -definition), die von der Projekt-Sponsorin bzw. dem Projekt-Sponsor aufgestellt werden;
* zuständig für die Festlegung des Budgets und, basierend auf diesem Budget, der für das Projekt zur Verfügung stehenden Ressourcen;
* der Hauptkontakt für sämtliche in das Projekt involvierte Rollen.

### Architektin oder Architekt {#architect}

Die Lösungsarchitektin oder der Lösungsarchitekt:

* ist für den allgemeinen Entwurf der Lösung und des Systems zuständig;
* hilft dabei, die Implementierungsstrategie für AEM festzulegen; beispielsweise bei der Frage, ob eine Cluster-Installation oder ein Cold-Standby implementiert werden soll oder wann ein Content Delivery Network (CDN) notwendig ist;
* definiert außerdem die Architektur der AEM-Lösung basierend auf den Anforderungen des Kunden, dies kann das Konzept für Benutzerrollen (mit den damit in Verbindung stehenden Rechten), das Verhältnis zwischen Vorlagen und Komponenten oder Informationen dazu einschließen, wann Multi-Site-Management verwendet werden sollte.

### Geschäftsanalyst {#business-analyst}

Die Geschäftsanalystin oder der Geschäftsanalyst:

* ist hauptsächlich dafür zuständig, die allgemeinen Anforderungen zu ermitteln und zu analysieren und diese dann in Spezifikationen umzuwandeln:

   * zur Verwendung durch den Projekt-Manager bei der Projektplanung;
   * als Vorlage für das Entwicklungs-Team während der Design- und Entwicklungsphasen;

* arbeitet eng mit der Kundin bzw. dem Kunden zusammen, um die Anforderungen zu analysieren. Diese werden verglichen mit:

   * der Erfolgsdefinition;
   * den Erfolgskriterien;
   * den KPIs (für Geschäft und Leistung).

### Entwicklungsleitung {#development-lead}

Die Entwicklungsleitung:

* ist zuständig für die technische Abwicklung des Projekts;
* ist zuständig für die Auswahl einer Entwicklungsmethode, die im Einklang mit den Kundenvorgaben steht;
* erstellt die Entwicklungsstrategie:

   * zur Sicherstellung, dass diese im Einklang mit den Geschäfts- und Leistungs-KPIs steht;
   * unter Berücksichtigung der Erfolgskriterien und -definition;

* arbeitet eng mit der Architektin bzw. dem Architekten zusammen (besonders bei der Erstellung der Entwicklungsstrategie für AEM), um Aspekte, wie etwa die Beziehung zwischen Vorlage und Komponenten, eine Strategie zur Integration von Drittanwendungen und spezielle Funktionen zu definieren.

### Leitung der Qualitätssicherung {#quality-lead}

Die Leitung der Qualitätssicherung:

* ist zuständig für die Lieferqualität und stellt sicher, dass diese die Erfolgskriterien und sämtliche von der Kundin bzw. dem Kunden vorgegebenen KPIs einhält;
* definiert die Qualitätsparameter, richtet diese an allen Projektbeteiligten aus, erstellt Testpläne und stellt sicher, dass diese auch ausgeführt werden;
* erstellt Berichte über das Projekt und liefert diese an die Projektbeteiligten.

### Systemtechnikerin oder Systemtechniker {#system-engineer}

Die Systemtechnikerin oder der Systemtechniker:

* ist zuständig für die Beaufsichtigung der Projektinfrastruktur;
* ist verantwortlich für:

   * die Einrichtung der internen Entwicklungs- und Testumgebungen;
   * die Anpassung dieser Systeme an die Kundensysteme;

* gibt Hardware-Empfehlungen, überprüft die diversen Implementierungen und bietet Hilfe beim Betrieb, sowohl vor als auch nach der Live-Schaltung.

### Leitung der Sicherheit {#security-lead}

Die Leitung der Sicherheit:

* ist zuständig für das allgemeine Sicherheitskonzept der Lösung und stellt sicher, dass dieses im Einklang mit sämtlichen Vorgaben und Richtlinien der Kundin bzw. des Kunden steht;
* liefert ein Sicherheitskonzept, Sicherheitsprozesse und Empfehlungen für Hardware-basierte Sicherheitskonzepte wie Zonen und Firewalls.

### Weitere Rollen {#other-persona}

* Projektbeteiligte

   * Personen (oftmals aus dem Unternehmen), die ein Interesse am Erfolg des Projekts haben. Sie tragen oft zum Budget bei.

* Rechtliches

   * Die Beteiligung der Rechtsabteilung ist bei der Aushandlung von Verträgen vorgeschrieben.

* Ausbilderinnen und Ausbilder

   * Je nach Größe und der Typ des Projekts können spezialisierte Ausbilderinnen und Ausbilder eingesetzt werden, um Schulungen für die betreffenden Gruppen zu entwickeln und diesen zu präsentieren.

* Technische Redakteurinnen und Redakteure

   * Je nach Größe und der Typ des Projekts können spezialisierte technische Redakteurinnen und Redakteure eingesetzt werden, um Richtlinien und Handbücher für bestimmte Gruppen zu schreiben, z. B. Wartungshandbücher für Systemadmins oder Benutzerhandbücher für Autorinnen und Autoren.

* Systemadministrierende

   * Sind zuständig für den laufenden Betrieb des Systems.

* Autorinnen und Autoren sowie Endbenutzende

   * Die Personen, die das System verwenden, um Website-Inhalte zu erstellen und zu verwalten.

## Erforderliche Dokumente und zu erbringende Leistungen {#required-documents-and-deliverables}

Die Checklisten enthalten die **erforderlichen Dokumente** und **Ergebnisse** für jeden Milestone.

* Es besteht keine 1:1-Beziehung zwischen diesen beiden Aspekten. So kann beispielsweise eine Gruppe erforderlicher Dokumente in nur einer zu erbringenden Leistung münden.
* Die zu erbringende Leistung einer Rolle kann ein erforderliches Dokument für eine andere Rolle während desselben Meilensteins sein.

### Erforderliche Dokumente {#required-documents}

Die **erforderlichen Dokumente** werden von der entsprechenden Rolle beim Bereitstellen der zu erbringenden Leistungen benötigt.

Bei jedem **erforderlichen Dokument** sollte die Person in der Rolle Folgendes angeben:

* **J/N:** ob es abgeschlossen wurde.
* **1–3**: ein Hinweis auf die Qualität des empfangenen Dokuments.

### Zu erbringende Leistungen {#deliverables}

Die entsprechende Rolle ist bei jedem Meilenstein für die Lieferung bestimmter Dokumente zuständig und erfüllt damit ihre Pflicht in Bezug auf diesen bestimmten Meilenstein.

Für jede **zu erbringende Leistung** muss die Person in der Rolle Folgendes angeben:

* **J/N:** ob es abgeschlossen wurde.

Ergebnisse werden oft als **erforderliche Dokumente** entweder für den derzeitigen oder zukünftige Milestones verwendet.

## Verwandte Best Practices {#related-best-practices}

Weitere Informationen zu Best Practices zur Bereitstellung, Administration, Entwicklung oder Erstellung finden Sie in den folgenden Dokumenten:

* Andere Best Practices und Richtlinien in Bezug auf die Verwaltung eines AEM-Projektes:
   * [Hardware-Skalierungsrichtlinien](/help/managing/hardware-sizing-guidelines.md)
   * [DevOp-Strategien für Unternehmen](/help/managing/enterprise-devops.md)
   * [Best Practices für SEO und URL-Verwaltung](/help/managing/seo-and-url-management.md)
   * [AEM und Richtlinien für barrierefreies Webdesign](/help/managing/web-accessibility.md)
   * [Datenschutz-Grundverordnung](/help/managing/data-protection-and-privacy.md)* [Best Practices für Bereitstellung und Wartung](/help/sites-deploying/best-practices.md)
* [Best Practices für die Verwaltung](/help/sites-administering/administer-best-practices.md)
* [Best Practices für die Entwicklung](/help/sites-developing/best-practices.md)
* [Best Practices für die Inhaltserstellung](/help/sites-authoring/best-practices.md)

## Schlüsselbereiche der Dokumentation {#key-documentation-areas}

* AEM-Dokumentation
Zusätzlich sind die folgenden Abschnitte der AEM-Dokumentation von besonderem Interesse (allerdings ist diese Liste nicht vollständig):

   * [Sicherheit](/help/sites-developing/security.md)
   * [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
   * [DevOp-Strategien für Unternehmen](/help/managing/enterprise-devops.md)
   * [Hardware-Skalierungsrichtlinien](/help/managing/hardware-sizing-guidelines.md)
   * AEM-Konzepte:

      * [Entwickeln – Grundlagen](/help/sites-developing/the-basics.md)
      * [MSM-Konzepte](/help/sites-administering/msm.md)
      * [HTML-Vorlagensprache (HTL)](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de)

* Verwandte Dokumentation

   * Adobe Experience Cloud - [Planen für Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/services/core-services.html?lang=de)
