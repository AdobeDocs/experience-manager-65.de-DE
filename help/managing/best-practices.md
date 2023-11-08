---
title: Verwalten von Projekten – Checkliste mit Best Practices
description: Die Verwaltung eines Projekts zur Implementierung von Adobe Experience Manager (AEM) erfordert Planung und Know-how. Die Checklisten für Projekte bieten eine Zusammenstellung der Best Practices für die Projektabwicklung. Sie führen Sie durch alle Phasen des Projektlebenszyklus und bieten eine allgemeine Überwachung Ihres Status.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing-checklist, introduction
content-type: reference
docset: aem65
exl-id: 94b91996-d2b2-4d4a-b770-334cfa2dc0b7
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '3238'
ht-degree: 17%

---

# Verwalten von Projekten – Checkliste mit Best Practices{#managing-projects-best-practices-checklist}

Die Verwaltung eines Projekts zur Implementierung von Adobe Experience Manager (AEM) erfordert Planung und Verständnis, damit Sie sich der Probleme und (damit zusammenhängenden) Entscheidungen bewusst sind, die Sie vor und während der Implementierung des Projekts treffen müssen.

Die Best Practices beinhalten Folgendes:

* Ein [interaktive Checkliste](/help/managing/best-practices-checklist.md) mit dem Sie den Fortschritt bei diesen Best Practices verfolgen und überwachen können.

   * Definiert Eingaben und Lieferziele nach Phase, Meilenstein und Persona.
   * Bietet automatisierte Übersichten (Qualität, Zustand und Vollständigkeit) zur Angabe des Fortschritts und des Projektstatus.

* Die Dokumentation basiert auf der [Checkliste](/help/managing/best-practices-checklist.md) , die Folgendes beschreibt:

   * [Projekt-Heartbeat](#projectheartbeat)-Analyse
   * Überblick über den [Status nach Rolle](#status-by-role)
   * [Phasen und Meilensteine](#phases-and-milestones).
   * [Schlüsselrolle](#persona) und ihre Beteiligung an allen (relevanten) Phasen.
   * [Glossar](/help/managing/best-practices-glossary.md) der [erforderlichen Dokumente und Ergebnisse](#required-documents-and-deliverables)

* [Weitere Informationen](/help/managing/best-practices-further-reference.md) Material, um weitere Details zu bestimmten Bereichen bereitzustellen.

## Projekt-Heartbeat-Dashboard {#project-heartbeat-dashboard}

Die **Projekt-Heartbeat** Das Arbeitsblatt bietet einen grafischen Überblick über kritische Metriken für Ihr Projekt:

* **Phasenqualität**

   * Gibt die Qualität der [Erforderliche Dokumente und Ergebnisse](#required-documents-and-deliverables) über das Projekt hinweg.

* **Phasenkonsistenz**

   * Ein allgemeiner Statusindikator für Ihr Projekt, der nützlich ist, um gefährdete Bereiche hervorzuheben.

* **Phasenvollständigkeit**

   * Dies gibt zu jedem Zeitpunkt während des Projekts an, wie viel bereits für jede Phase Ihres Projekts abgeschlossen wurde.

## Status nach Rolle {#status-by-role}

Die **Status nach Rolle** Das Arbeitsblatt zeigt eine detaillierte Aufschlüsselung der [**Gesundheit**, **Qualität und **Vollständigkeit**](#projectheartbeat) von **[Phase](#phases-and-milestones)** und **[Persona](#persona)**.

## Phasen und Meilensteine {#phases-and-milestones}

Der Projektplan ist in verschiedene (allgemeine) Phasen unterteilt.

Jede Phase enthält ihre eigenen Milestones. Für jede [Rolle](#persona) werden die zutreffenden Milestones gemeinsam mit den Dokumenten aufgelistet, die zur Erreichung bestimmter Ergebnisse notwendig sind.

>[!NOTE]
>
>Es besteht keine direkte 1:1-Beziehung zwischen den einzelnen erforderlichen Dokumenten und den Lieferzielen.

### Vorbereitung {#preparation}

Die Vorbereitung des Projekts bildet die Grundlage für das gesamte Projekt. Definieren Sie Schlüsselanforderungen zusammen mit klaren Zielen und Erwartungen für:

* **Geschäftsgrundsatz**

   * Die wesentlichen Gründe und die Begründung für die Durchführung des Projekts.

* **Umfang und Zeitplan**

   * Es sollten ein grundlegender Umfang und ein grober Zeitplan zur Verfügung gestellt werden, um festzulegen, was erforderlich ist und in welchem Zeitrahmen. Wenn dies zur Klärung der Situation beiträgt, können Sie auch festlegen, was außerhalb des Anwendungsbereichs liegt.

Die Art und Weise, wie Sie Ihr Projekt vorbereiten, planen und ausführen und Ihre Lösung implementieren, ist von den Einschränkungen betroffen, unter denen Sie arbeiten. Beispielsweise festes Budget, feste Zeitleiste, Inhaltsmenge, erforderliche Qualität.

Wie immer wirkt sich die Anpassung eines der Faktoren auf die anderen aus. Wenn Sie beispielsweise die Zeit verkürzen, aber dasselbe Qualitätsniveau erfordern, wird der Preis wahrscheinlich steigen, während gleichzeitig die Menge der Inhalte, die Sie berücksichtigen können, reduziert wird. Haushalt ist oft ein Schlüsselfaktor, sodass solche Beziehungen nicht vergessen werden können.

Die vier Faktoren:

![projectphases_fourphases](assets/projectphases_fourphases.png)

#### Milestones {#milestones}

* **Validierung**

  In dieser Phase müssen Sie die Ziele für das Projekt validieren und bestätigen. Beispiel:

   * Was möchten Sie erreichen/bereitstellen?
   * Wer profitiert davon?
   * Wie sieht der Anwendungsbereich aus?

      * Wenn dies zur Klärung der Situation beiträgt, können Sie auch festlegen, was außerhalb des Anwendungsbereichs liegt.

   * Wie definieren Sie Erfolg?
   * Wie misst du Erfolg?
   * Welche technischen und geschäftlichen Anforderungen gibt es?
   * Gibt es veraltete Systeme, die ersetzt werden müssen, und wenn ja, müssen Daten migriert werden?
   * Wer ist involviert?
   * Wie misst man den Fortschritt?
   * Wie oft überprüfen Sie den Fortschritt während der Projektlaufzeit?

* **Budget**

  Bevor Sie mit einem Projekt beginnen, benötigen Sie eine zuverlässige, realistische Schätzung der Kosten für die Implementierung:

   * Verwenden Sie Informationen aus dem Validierungs-Meilenstein als Grundlage für die Schätzungen.
   * Seien Sie realistisch in Ihren Schätzungen.
   * Beachten und beachten Sie alle Client-Richtlinien, Prozesse oder Einschränkungen, denen der Client unterliegt.
   * Berücksichtigen Sie Verfahren für unvorhergesehene Ausgaben und Überprüfungen, wenn zu einem späteren Zeitpunkt eine Überprüfung oder Verfeinerung des Haushalts erforderlich ist.
   * Denken Sie daran, dass die Kosten in vielen Formen entstehen, wie zum Beispiel Käufe, Nutzung von Ressourcen und Gebühren.

### Planung {#planning}

Die Planung des Projekts vertieft die Vorbereitung. Hier sollten Sie damit beginnen, die Ziele und Erwartungen in einen klar definierten Fahrplan umzuwandeln, der aus konkreten Aufgaben besteht, die durch klare Kommunikation verbunden sind, mit strengen Überprüfungen zur Messung des Fortschritts.

#### Milestones {#milestones-1}

* **Übergabe**

  Durch eine saubere Übergabe wird sichergestellt, dass die entsprechenden Personen/Gruppen sich ihrer Verantwortung im Rahmen des Projekts bewusst sind.

  Umfassende Informationen sollten bereitgestellt/generiert werden, um sicherzustellen, dass sie alle relevanten Aspekte einschließlich Roadmap, Umfang, Ziele, Anforderungen und KPIs vollständig verstehen.

* **Risikobewertung**

  Um unangenehme Überraschungen zu vermeiden, verwenden Sie die Risikobewertung, um potenzielle Risiken zusammen mit ihren Auswirkungen und Wahrscheinlichkeiten zu ermitteln und zu quantifizieren.

  Dies sollte frühzeitig im Projektlebenszyklus erfolgen, um sicherzustellen, dass etwaige Schwachstellen erkannt und bewertet werden. Auf der Grundlage der Ergebnisse können Sie Ihren Interessengruppen mitteilen, ob die vollständigen Anforderungen erfüllt werden können und ob es gegebenenfalls möglich ist, geeignete Maßnahmen zu planen und zu verfolgen.

* **Kommunikation**

  Kommunikation ist immer der Schlüssel zum Erfolg eines jeden Projekts. Vermitteln Sie klar und effizient, um sicherzustellen, dass alle:

   * Auf dieselben grundlegenden Ziele hinarbeiten
   * Aus derselben Informationsbasis
   * Mit denselben Kanälen

* **Kick Off**

  Das Meeting zum Projektstart dient dazu, auf den Start des Projekts hinzuweisen. Es bietet eine gute Gelegenheit,

   * Laden Sie alle interessierten Parteien (oder zumindest Gruppenvertreter) ein.
   * Präsentieren Sie wichtige Fakten zum Projekt.
   * Beantworte Fragen.
   * Stellen Sie sicher, dass alle über dieselbe Wissensgrundlage verfügen.
   * Beziehen Sie sich von allen, die beteiligt sein werden - dies muss verdient werden.

      * Durch die Einbeziehung von Hauptakteuren (einschließlich potenzieller Autoren) zu Beginn des Projekts erhöhen Sie Ihre Chancen, ihr Engagement für das Projekt zu erreichen.

### Entwicklungsvorbereitung {#development-preparation}

Die Planung der Entwicklung ist entscheidend, um sicherzustellen, dass Ihr Projekt auf einem soliden Design eines Teams basiert, das über die erforderlichen Kenntnisse verfügt.

#### Milestones {#milestones-2}

* **Entwicklungsteam - Fortbildung**

  Bevor Sie mit einem Projekt beginnen, sollten Sie sicherstellen, dass Ihr Entwicklungsteam angemessen besetzt ist und dass alle Teammitglieder für die vorliegende Aufgabe geschult sind.

* **Inhaltsarchitektur**

  Die Inhaltsarchitektur definiert und beschreibt die zukünftige Architektur des Inhalts, einschließlich:

   * Inhaltsstruktur, einschließlich Assets
   * Grundstrukturen, einschließlich Kampagnen usw.
   * Multisite- und mehrsprachige Strukturen (MSM, Übersetzung usw.)
   * Unterstützende Inhalte (einschließlich Tags und Tagging-Konzepten)
   * Caching und Strategien zur Wiederverwendung von Inhalten

* **Systemarchitektur**

  Die Systemarchitektur definiert die konzeptionelle Ansicht Ihres Systems, einschließlich (unter anderem):

   * [Systemstruktur](/help/sites-deploying/recommended-deploys.md#deployment-scenarios) für alle erforderlichen Umgebungen
   * Subsysteme
   * Drittanbietersysteme
   * Schnittstellen, Hardware, Software und menschliche Interaktionen
   * Server für jede Umgebung; siehe [Technische Anforderungen](/help/sites-deploying/technical-requirements.md) und [Hardware-Skalierungsrichtlinien](/help/managing/hardware-sizing-guidelines.md);

   * Prozesse für jede Umgebung, z. B. Bereitstellungs- und Wartungsanforderungen
   * Wartungsaktivitäten (Datastore GC, TarPM-Optimierung usw.)
   * [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de)-Caching
   * [Clustering](/help/sites-deploying/recommended-deploys.md#deployment-scenarios) beim Veröffentlichen/automatischen Teilen;
   * Leistung für die Client-Seite (JS minify, concat, css sprites, Gesamtanzahl der HTTP-Anforderungen und andere)

* **Anwendungsarchitektur**

  Die Anwendungsarchitektur definiert und beschreibt das Verhalten der vorgeschlagenen Anwendungen.

  Der Schwerpunkt liegt auf Folgendem:

   * Interaktion der Benutzer untereinander und mit den Benutzern.
   * Die Daten, die von Anwendungen genutzt und erzeugt werden sollen, anstatt ihrer internen Struktur.

  Die Begriffsbestimmungen sollten Folgendes umfassen:

   * Grundlegende Code-Struktur für das Projekt
   * Code-Artefakte (Pakete, Pakete usw.)
   * Aufschlüsselung der Vorlagen/Komponenten und ihrer Beziehungen
   * Allgemeine Details der erforderlichen Anpassungen (spezifische Überlagerungen folgen später)
   * Entwurf der für die Lösung erforderlichen Workflows (z. B. Inhaltserstellung, Genehmigung, Veröffentlichung, Transformationen, Importe und Exporte)
   * Besondere Berücksichtigung komplexer Module wie MSM, Commerce, Drittanbieterintegration

* **Systemintegration**

  Für die Systemintegration müssen Sie Folgendes planen (und dann implementieren):

   * Wie alle Teilsysteme und [Lösungsintegrationen](/help/sites-administering/integration.md) zusammengeführt werden, um als einheitliches System zu fungieren
   * Integration von Drittanbietersystemen zusammen mit besonderen Überlegungen wie Offline-/Online-, Client-/Browser-seitig oder Fallover-Handhabung bei Ausfall eines Drittanbietersystems

* **Testkonzept**

  Bevor Sie mit der Entwicklung beginnen, sollten Sie ein tiefgehendes und umfassendes Konzept aller [testing](/help/sites-developing/planning.md) Anforderungen für Ihr Projekt.

  Dies sollte (unter anderem) Folgendes umfassen:

   * Details aller durchzuführenden Tests
   * Vorbereitung des für diese Tests erforderlichen Inhalts
   * Angaben zu den zu verwendenden Testwerkzeugen
   * Allgemeine Angabe, wer an Tests beteiligt sein wird, insbesondere Gruppen außerhalb des Qualitätssicherungsteams
   * Details zur Testautomatisierung, z. B. mit Selenium oder AEM Entwicklermodus

* **Experience Design**

  Experience Design (XD) umfasst das Entwerfen des Benutzererlebnisses für Ihre Lösung.

  Das Benutzererlebnis sollte sowohl für Ihre Autoren als auch für die Endbenutzer Ihrer Website analysiert und entwickelt werden.

* **Support-Setup**

  Vor der Entwicklung sollten alle erforderlichen Support-Prozesse für die Bereitstellung, Freigabe, Prüfung und Berichterstellung eingerichtet werden.

  Siehe auch [Adobe Support Portal](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home?lang=de#support).

### Betriebsplanung und -betrieb {#operations-planning-and-operations}

Auf ähnlicher Grundlage müssen die Vorgänge entsprechend geplant werden, um sicherzustellen, dass Sie über die erforderlichen Umgebungen verfügen - für alle Phasen des Projektlebenszyklus. Sie benötigen auch die entsprechenden Prozesse, um sie zu verwalten.

#### Milestones {#milestones-3}

* **Berechtigungen**

  Sie müssen ein Rollen- und Berechtigungskonzept für alle Benutzer/Gruppen planen und implementieren, die die Lösung verwenden.

  Beispiel:

   * Eine Liste der Rollen (d. h. Gruppen) mit `read`/ `write` Zugriffsdefinitionen für jede

   * Festlegung der Verwendung von Berechtigungen, die einen Einfluss auf die Veröffentlichungsumgebung haben, z. B. `replicate`
   * Für Benutzer mit minimalen Berechtigungen sollten Workflows definiert werden
   * Benutzer in der Gruppe `editor` sollten weder über `admin`-Rechte verfügen noch Teil der Gruppe `administrators` sein

  Weitere Informationen finden Sie unter [Benutzeradministration und Sicherheit](/help/sites-administering/security.md).

* **Überwachung und Wartung**

  Überwachung und Wartung sind Schlüsselaspekte, um den reibungslosen Ablauf der Lösung nach der Einführung zu gewährleisten. Dazu müssen Sie Folgendes definieren:

   * Was muss überwacht werden?
   * Wartungsaufgaben, sowohl für reguläre als auch für Sonderfälle

  Siehe auch [Überwachung und Wartung](/help/sites-deploying/monitoring-and-maintaining.md) für weitere Informationen.

* **Migration**

  Alle Inhalte aus dem alten System sollten für die Migration überprüft und validiert werden.

* **Wiederherstellungsplan**

  Stellen Sie sicher, dass Sie einen Wiederherstellungsplan haben. In einer Notsituation muss dies verfügbar sein, um die Verwendung von AEM sicherzustellen. Dies sollte Situationen wie Sicherung, Wiederherstellung, Fallover und andere abdecken.

### Entwicklung {#development}

Entwicklung ist eine entscheidende Phase, die mehr erfordert als nur Programmieren.

#### Milestones {#milestones-4}

* **Entwicklungsumgebung**

  Planen und dokumentieren Sie Ihre Entwicklungsumgebung, einschließlich:

   * Architektur
   * [Entwicklungswerkzeugen](/help/sites-developing/dev-tools.md)

      * Eine typische Umgebung besteht aus:

         * ein System zur Problemverfolgung, z. B. Jira
         * eine IDE, z. B. Eclipse
         * ein Build-Management-Tool, wie Maven
         * einem Werkzeug für die fortwährende Integration, wie etwa Jenkins;
         * ein Tool zur Versionskontrolle, wie GIT/SVN
         * einen Repository-Manager für Build-Artefakte, z. B. Archiva/Nexus

   * Integration/Abhängigkeiten von Software von Drittanbietern
   * [Integration/Abhängigkeiten von der Lösung;](/help/sites-administering/integration.md)
   * Bereitstellungskapazität

* **Testsystem**

  Planen und dokumentieren Sie Ihre Testumgebung, einschließlich:

   * Architektur
   * Abhängigkeiten von Entwicklungs-Builds, einschließlich nächtlicher Builds
   * Möglichkeiten oder Einschränkungen zum Testen der Softwareintegration/Abhängigkeiten von Drittanbietern
   * Testwerkzeuge
   * Automatisierte Teststrategie

* **Produktionssystem**

  Planen und dokumentieren Sie Ihre Produktionsumgebung, einschließlich:

   * Architektur
   * Bereitstellungskapazität
   * Integration/Abhängigkeiten von Software von Drittanbietern
   * Sicherheitseinstellungen
   * Bestätigung der Grundleistung durch Ausführen eines [Tough Day](/help/sites-developing/tough-day.md)-Tests bei der Produktionskonfiguration;
   * Anforderungen an Leistungstests, siehe [Best Practices für Qualitätssicherung](/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance)

* **Integration**

  Planen, dokumentieren und testen Sie alle Aspekte des Systems und [Lösungsintegration](/help/sites-administering/integration.md), einschließlich:

   * Eine automatisierte Teststrategie
   * Automatisierte Prozesse in [Anwendungen von der Entwicklung in den Test verschieben, dann Produktion](/help/managing/enterprise-devops.md#code-movement)
   * Automatisierte Prozesse in [Verschieben von Inhalten aus der Produktion in die Test- und Entwicklungsumgebung](/help/managing/enterprise-devops.md#content-movement)

* **Migration**

  Planen, dokumentieren und testen Sie alle Aspekte der Inhaltsmigration, einschließlich:

   * Inhaltsarchitektur
   * Migrationsstrategie

* **Kommunikation**

  Stellen Sie sicher, dass alle Team-Mitglieder und Projektmitarbeiter bei Bedarf auf dem neuesten Stand gehalten werden.

* **Dokumentation**

  Dokumentieren Sie die Lösung vollständig, einschließlich:

   * Betriebshandbuch
   * Alle Anpassungen, die sich auf Aktualisierungen auswirken können
   * Versionshinweise

### Leistung und Tests {#performance-and-testing}

Sobald die neue Anwendung verfügbar ist, muss sie strengen Tests unterzogen werden, sowohl hinsichtlich der Funktionalität als auch [Leistung](/help/sites-deploying/configuring-performance.md).

>[!NOTE]
>
>Jedes Testteam sollte die Möglichkeit haben, neutral zu bleiben und die Testergebnisse zu liefern.
>
>Es liegt in der Verantwortung des Projektmanagers, die Auswirkungen der Ergebnisse zu bewerten und geeignete Maßnahmen zu treffen.

#### Milestones {#milestones-5}

* **Endbenutzerakzeptanztest**

  [Anwenderakzeptanztests](/help/sites-developing/acceptance-signoff.md) (UAT) ist entscheidend, um sicherzustellen, dass

   * Die Lösung erfüllt die Benutzer-/Kundenanforderungen
   * Der Kunde/die Benutzer akzeptieren die Lösung (Funktion, Design und Leistung)

  eine formelle Checkliste sollte für die Kundenübergabe erstellt werden, die idealerweise automatisiert ist und nächtlich gegenüber einer Momentaufnahme durchgeführt wird. Die Ergebnisse sollten an den Projekt-Manager oder das Entwickler-Tam weitergeleitet werden.

* **Leistungs- und Belastungstests**

  Leistungs- und Belastungstests werden verwendet, um sicherzustellen, dass die Lösung die erforderlichen Leistungsniveaus bei durchschnittlicher Belastung und Spitzenlast erfüllt.

  Weitere Informationen zu Leistungstests finden Sie unter:

   * [Leistungstests](/help/sites-deploying/configuring-performance.md)
   * [Planen und Ausführen von Tests](/help/sites-developing/planning.md)

   * [Allgemeine Leistungsrichtlinien](/help/sites-deploying/configuring-performance.md#basic-performance-guidelines)

  >[!NOTE]
  >
  >Dieser Prozess muss während der normalen Nutzung von AEM fortgesetzt werden, aber diese ersten Schritte sind die wichtigsten.

### Rollout {#rollout}

Der Rollout einer neuen Anwendung bedarf sorgfältiger Planung, um einen reibungslosen Ablauf der Live-Schaltung zu gewährleisten. Dazu gehört die Bestätigung eines hohen Sicherheitsniveaus, die Schulung aller potenziellen Benutzer und die Durchführung mehrerer Testläufe, um zu bestätigen, dass alle Probleme gelöst wurden.

#### Milestones {#milestones-6}

* **Vorbereitung**

  Die Vorbereitung und Planung tragen zu einem reibungslosen Rollout bei.

* **Schulung**

  Stellen Sie sicher, dass alle beteiligten Mitarbeiter geschult wurden.

  Siehe [Adobe Experience Manager](https://training.adobe.com/training/courses.html#solution=adobeExperienceManager) im Kurskatalog.

* **Trainierte Administratoren**

  Stellen Sie sicher, dass Ihre Lösungsadministratoren über Folgendes verfügen:

   * entsprechend geschult wurden
   * Das entsprechende Lehrmaterial erhalten
   * Die entsprechende Dokumentation erhalten

* **Schulte Benutzer**

  Stellen Sie sicher, dass Ihre Autoren über Folgendes verfügen:

   * entsprechend geschult wurden
   * Das entsprechende Lehrmaterial erhalten
   * die entsprechende Dokumentation erhalten haben, z. B. das Benutzerhandbuch

* **Penetrationstests**

  Penetrationstests simulieren einen Angriff auf ein Computersystem, um potenzielle Sicherheitsmängel zu identifizieren.

* **Penetration/Sicherheitstests**

  Um die Sicherheit Ihrer Lösung zu gewährleisten, führen Sie spezifische Penetrationstests zusammen mit einer größeren Auswahl an Sicherheitstests durch.

  Weitere Informationen finden Sie in der [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).

### Live-Schaltung {#go-live}

Die Live-Schaltung sollte so reibungslos wie möglich verlaufen. Auch hier müssen die letzten Schritte für eine saubere Ausführung geplant werden.

#### Milestones {#milestones-7}

* **Vorbereitung**

  Die Vorbereitung und Planung tragen dazu bei, dass ein reibungsloses Leben gewährleistet ist.

* **Sicherheit**

  Bestätigen Sie die Sicherheit Ihrer Lösung für interne und externe Benutzer und deren Inhalt.

* **Notfallversorgung**

  Stellen Sie sicher, dass alle Systeme, Verfahren und Mechanismen, die für Ausweichmanöver erforderlich sind, vorhanden sind, bevor Sie live geschaltet werden.

* **Support**

  Stellen Sie sicher, dass die Support-Services vorhanden und bereit sind.

* **Übergang**

  Planen und führen Sie die Umstellung auf Ihre Produktionsumgebung und -benutzer aus.

* **Rollout**

  Bereiten Sie Ihre Rauchtests vor und führen Sie sie aus.

## Rolle {#persona}

Die Checklisten werden rollenabhängig entworfen. Dies sind die Rollen, die erheblich am Projektlebenszyklus beteiligt sind.

Es gibt auch einige [andere Person](#other-persona) die an bestimmten Aufgaben beteiligt sind.

### Projektsponsor {#project-sponsor}

Der Projektsponsor ist:

* Zuständig für die Bereitstellung/Präsentation des Geschäftsszenarios für das Projekt.
* Schlüssel zur Gestaltung und Definition des Projektumfangs, einschließlich:

   * Definition und Kriterien für den Erfolg
   * die wichtigsten KPIs

* Geben Sie die wichtigsten Meilensteine basierend auf der Client-Roadmap an.

### Projekt-Manager {#project-manager}

Der Projekt-Manager ist:

* Zuständig für die Gesamtbereitstellung des Projekts basierend auf den Anforderungen (z. B. Umfang, KPIs, Erfolgskriterien und Definition), die vom Projektsponsor bereitgestellt werden.
* Zuständig für die Festlegung des Budgets und die Bereitstellung der Ressourcen für das Projekt auf der Grundlage dieses Budgets.
* Der zentrale Punkt der Kommunikation für alle am Projekt beteiligten Personen.

### Architekt {#architect}

Der Lösungsarchitekte:

* ist für das allgemeine Design der Lösung und des Systems verantwortlich.
* hilft dabei, die Implementierungsstrategie für AEM festzulegen; Zum Beispiel, ob eine Clusterinstallation oder ein Cold-Standby implementiert werden soll oder wenn ein Content Delivery Network (CDN) benötigt wird.
* definiert außerdem die Architektur der AEM-Lösung basierend auf den Anforderungen des Kunden, Dies kann das Konzept für Benutzerrollen (mit verwandten Rechten), die Beziehung zwischen Vorlagen und Komponenten oder die Verwendung der Verwaltung mehrerer Sites umfassen.

### Geschäftsanalyst {#business-analyst}

Geschäftsanalyst:

* ist in erster Linie für die Erfassung und Analyse der allgemeinen Anforderungen verantwortlich und wandelt diese dann in Spezifikationen um:

   * zur Verwendung durch den Projekt-Manager bei der Projektplanung;
   * , damit das Entwicklungsteam während der Entwicklung und Entwicklung von dort aus arbeiten kann.

* Arbeiten Sie eng mit dem Kunden zusammen, um die Anforderungen zu analysieren. Diese stimmen mit Folgendem überein:

   * Die Definition von Erfolg.
   * Die Erfolgskriterien.
   * KPIs (geschäftlich und leistungsbasiert).

### Entwicklungsleiter {#development-lead}

Der Entwicklungsvorsprung:

* ist für die technische Durchführung des Projekts verantwortlich.
* ist für die Auswahl einer Entwicklungsmethodik verantwortlich, die den Kundenanforderungen entspricht.
* Erstellung der Entwicklungsstrategie:

   * Sicherstellen, dass sie mit den Geschäfts- und Leistungs-KPIs abgestimmt ist
   * unter Berücksichtigung der Erfolgskriterien und der Definition

* arbeitet eng mit dem Architekten zusammen (insbesondere bei der Erstellung der Entwicklungsstrategie für AEM), um Aspekte wie die Beziehung zwischen Vorlagen und Komponenten, die Integrationsstrategie für Anwendungen von Drittanbietern und spezielle Funktionen zu definieren.

### Qualitätsleiter {#quality-lead}

Qualitätsvorsprung:

* ist für die Qualität des Versands verantwortlich; stellt sicher, dass er die Erfolgskriterien und alle vom Kunden definierten KPIs erfüllt.
* Definiert die Qualitätsmetriken, passt sie an alle Interessengruppen an, erstellt die Testpläne und stellt sicher, dass sie ausgeführt werden.
* Erstellt Berichte und stellt sie an Projektbeteiligte bereit.

### Systemtechniker {#system-engineer}

Der Systemtechniker:

* ist für die Überwachung der Projektinfrastruktur verantwortlich.
* ist verantwortlich für:

   * Einrichtung interner Entwicklungs- und Testumgebungen
   * für die Anpassung dieser Systeme an die Client-Systeme

* Bietet Hardware-Empfehlungen, überwacht die verschiedenen Implementierungen und bietet Betriebsunterstützung sowohl vor als auch nach der Live-Schaltung.

### Sicherheitsleitfaden {#security-lead}

Der Sicherheitsleiter:

* ist für das Gesamtsicherheitskonzept der Lösung verantwortlich und stellt sicher, dass sie mit allen Anforderungen und Richtlinien des Kunden übereinstimmt.
* Bietet ein Sicherheitskonzept, Sicherheitsoperationen und Empfehlungen für hardwarebasierte Sicherheitskonzepte wie Zonen und Firewalls.

### Sonstige Persona {#other-persona}

* Interessenträger

   * Personen (häufig aus dem Unternehmen), die ein Interesse am Erfolg des Projekts haben (Anteil). Sie tragen oft zum Budget bei.

* Legal

   * Bei Vertragsverhandlungen ist rechtliche Beratung erforderlich.

* Ausbilder

   * Je nach Umfang und Art des Projekts können spezialisierte Trainer eingesetzt werden, um Schulungen für die jeweiligen Gruppen zu entwickeln und vorzustellen.

* Technische Schriftsteller

   * Je nach Umfang und Art des Projekts können spezialisierte technische Autoren zum Schreiben von Richtlinien und Handbüchern für bestimmte Gruppen verwendet werden. Beispielsweise ein Wartungshandbuch für Systemadministratoren oder ein Benutzerhandbuch für Autoren.

* Systemadministratoren

   * Zuständig für den laufenden Betrieb des Systems.

* Autoren und Endbenutzer

   * Die Personen, die das System zur Erstellung und Pflege Ihrer Website-Inhalte verwenden.

## Erforderliche Dokumente und Ergebnisse {#required-documents-and-deliverables}

Die Checklisten enthalten die **erforderlichen Dokumente** und **Ergebnisse** für jeden Milestone.

* Es besteht keine 1:1-Beziehung zwischen diesen Dokumenten. Beispielsweise kann eine Gruppe erforderlicher Dokumente zu einem einzelnen Versand führen.
* Ein von einer Person bereitstellbares Dokument kann während desselben Meilensteins für eine andere Person erforderlich sein.

### Erforderliche Dokumente {#required-documents}

Die **Erforderliche Dokumente** werden von der entsprechenden Person bei der Produktion ihrer Ergebnisse benötigt.

Für jeden **Erforderliches Dokument**, sollte die Persona Folgendes angeben:

* **Y/N**: ob sie empfangen wurde.
* **1-3**: ein Hinweis auf die Qualität des empfangenen Dokuments.

### Lieferziele {#deliverables}

Für jeden Meilenstein ist die entsprechende Person für die Bereitstellung bestimmter Dokumente verantwortlich und erfüllt daher ihre Verantwortung für einen bestimmten Meilenstein.

Für jeden **Zustellbar** muss die Persona Folgendes angeben:

* **J/N:** ob es abgeschlossen wurde.

Ergebnisse werden oft als **erforderliche Dokumente** entweder für den derzeitigen oder zukünftige Milestones verwendet.

## Verwandte Best Practices {#related-best-practices}

Best Practices für die Bereitstellung, Verwaltung, Entwicklung oder Bearbeitung finden Sie unter folgenden Themen:

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

   * Adobe Experience Cloud - [Planen für Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/services/core-services.html)
