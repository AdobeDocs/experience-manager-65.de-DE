---
title: Best Practices für die Übersetzung
seo-title: Best Practices für die Übersetzung
description: Hier finden Sie Best Practices für die Einrichtung und Ausführung von Übersetzungsprojekten – zusammengestellt von Technik- und Beratungsteams von Adobe.
seo-description: Hier finden Sie Best Practices für die Einrichtung und Ausführung von Übersetzungsprojekten – zusammengestellt von Technik- und Beratungsteams von Adobe.
uuid: 3bac1d73-9696-4c9b-8bdd-6f00fac40cf7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features, best-practices
content-type: reference
discoiquuid: 1554010e-a1d1-4edf-b28f-9eead8f83b4a
feature: Sprachkopie
exl-id: 01a81c4b-cb30-4f7e-b281-7194ebb5fc70
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 100%

---

# Best Practices für die Übersetzung{#translation-best-practices}

## Allgemein {#general}

Das Erstellen bzw. Erweitern einer globalen Web-Präsenz kann ein komplexer Prozess sein, aber mit Voraussicht und Planung kann AEM Ihre Bemühungen vereinfachen und Ihre globalen Unternehmensziele unterstützen.

* **Planen Sie die globale Expansion**, bevor Sie Ihre erste Website implementieren. Es ist für gewöhnlich schwieriger, eine vorhandene Website für globale Abdeckung anzupassen, wenn die Website kurzfristig implementiert wurde, als wenn Sie von Anfang an auf eine globale Expansion hin planen:

   * Prüfen Sie den aktuellen Status der Lokalisierungsreife Ihrer Organisation. Stellen Sie fest, ob Sie über die für eine globale Expansion notwendigen **Tools**, **Prozesse** und **Ressourcen** verfügen.
   * Beachten Sie **lokal unterschiedliche Rechtsvorschriften** und **regionale sprachliche Präferenzen**. Entwerfen Sie flexible Inhaltsstrukturen und -prozesse, die für eine in ständigem Wandel befindliche globale Geschäftsumgebung geeignet sind.

* Wählen Sie ein **Governance**-Modell, das die globale Geschäftstätigkeit unterstützt, und verwenden Sie AEM-Mechanismen (z. B. MSM und Benutzerberechtigungen), um das gewählte Modell durchzusetzen. Legen Sie beispielsweise fest, ob Inhalte zentral verfasst und an Regionen/Länder verteilt oder von ihnen abgerufen werden. Legen Sie fest, welche Inhalte in Regionen entsperrt und geändert werden können. Legen Sie fest, wer für das Initiieren und Verwalten von Übersetzungen zuständig ist.
* Falls die Ressourcensituation es erlaubt, sollten Übersetzungsaktivitäten von einem zentralen Team verwaltet werden, das Fachwissen hinsichtlich der nötigen Tools, Prozesse und Lieferantenbeziehungen entwickeln kann.
* **Planen** Sie Ihre globale Struktur und Ihre Prozesse, **erstellen Sie Prototypen** davon und **testen** Sie sie, um sicherzustellen, dass sie Ihr Unternehmen unterstützen und dass Sie über die notwendige Unterstützung der Stakeholder in den Regionen verfügen.

## Site-Struktur  {#site-structure}

* Beginnen Sie den Entwurf der Site-Struktur mit der Untersuchung Ihrer Inhalte und stellen Sie fest, wo und in welcher Sprache Inhalte verfasst werden. Dieser Ort muss die höchste Ebene Ihrer Website darstellen.
* Bewährt und empfohlen ist eine **sprachbasierte Struktur** mit höchstens drei Ebenen zwischen den Autorenaktivitäten auf höchster Ebene und den landesspezifischen Websites.
* Verwenden Sie für sprachen- bzw. länderspezifische Websites eine Benennungskonvention, die **W3C-Standards** entspricht.
* Legen Sie fest, wie Inhalte nach Regionen und Ländern verteilt werden. Berücksichtigen Sie Länder, in denen dieselbe Sprache gesprochen wird. Es wird empfohlen, Sprachstämme zu erstellen, eine Ebene nicht aktivierter Seiten, auf denen übersetzte Inhalte überprüft und geändert und dann an eine länderspezifische Website mit der jeweiligen Sprache verteilt oder von ihr abgerufen werden können.
* Zum Erstellen von Sprachstämmen gibt es zwei Ansätze, einen mit Sprachkopien und einen mit MSM-/Live Copies.

   * Der Ansatz mit den Sprachkopien wird vom standardmäßigen Übersetzungsintegrations-Framework von AEM verwendet und stellt daher die einfachste Methode für den Anfang dar. Das Framework bietet eine Benutzeroberfläche, die es zunächst einfach macht, inhaltliche Änderungen vom Stamm der Hauptsprache an Sprachstämme weiterzugeben und zu übersetzen. Mit dem Wachstum des Projekts wird die Workflow-Automatisierung jedoch immer notwendiger für die Verwaltung der Übersetzung der steigenden Anzahl von Seiten und/oder Sprachen.
   * Der Ansatz mit MSM/Live Copies ist möglicherweise eine Alternative für fortgeschrittene Anwendungsfälle mit größeren, komplexeren Websites. Zur Verwaltung der komplexen Vererbungsverhältnisse zwischen der Hauptsprache und den Sprachstämmen sowie zur Verringerung des Risikos, bestehende Übersetzungen zu überschreiben, sind starke Governance und effiziente Workflow-Automatisierung erforderlich. Diese Verwaltung ist mithilfe von Übersetzungs-Connectors möglich. In [MSM und mehrsprachige Websites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites) finden Sie weitere Informationen.

* Wenn bei der primären Sprache globale Varianten vorliegen, ist eine Option, mit MSM eine Live Copy vom globalen Stamm zur Übersetzung zu erstellen. Wenn beispielsweise in einem Stamm in amerikanischem Englisch eine Bearbeitung durchgeführt wird, erstellen Sie einen Stamm in internationalem Englisch als Live Copy und Grundlage für die Übersetzung in andere Sprachen.
* Verwenden Sie MSM zur Erstellung von länderspezifischen Websites aus den übersetzten Sprachstämmen und für den Rollout von Inhalten an Websites mit derselben Sprache. Beispielsweise kann der französische Sprachstamm an die Websites von Frankreich, Belgien und die Schweiz bereitgestellt werden.
* Planen Sie, erstellen Sie Prototypen und führen Sie Tests durch, bevor Sie die Implementierung beginnen.

## Übersetzungsprozesse und -methoden  {#translation-processes-and-methods}

* Engagieren Sie einen **Lokalisierungsdienstleister** mit Fachkenntnissen in Übersetzung und relevanten Lokalisierungstätigkeiten. Lokalisierungsdienstleister helfen bei der Skalierung Ihres globalen Unternehmens, indem sie ein Spektrum an Ressourcen und Technologien zur Verfügung stellen, welche die Effizienz verbessern und Übersetzungskosten sparen:

   * Einige Lokalisierungsdienstleister sind auch Technologieanbieter. Es gibt auch eigenständige Technologieanbieter, die vielen Lokalisierungsdienstleistern die Arbeit auf ihren Übersetzungsplattformen ermöglichen.
   * Das **AEM-Übersetzungs-Framework** unterstützt die Integration mit einer Vielzahl von Übersetzungstechnologieanbietern für maschinelle und menschliche Übersetzung.
   * Erfahren Sie, wie Sie [Connectoren für Lokalisierungsdienstleister in Ihr AEM-System integrieren](/help/sites-administering/translation.md), um die Übersetzung von Inhalten zu automatisieren, bzw. wie Sie zum Testen oder in Fällen, wo kein Lokalisierungsdienstleister bzw. Übersetzungstechnologieanbieter vorhanden ist, Übersetzungsprojekte erstellen, exportieren und importieren.

* Wählen Sie die **Übersetzungsmethode**, die am besten für den Inhalt geeignet ist.

   * Die **menschliche Übersetzung** ist am besten für Inhalte geeignet, bei denen viel Wert auf Anspruch und Qualität des Texts gelegt wird und wenn Inhalte für längere Zeit auf der Website aktiv sind, z. B. auf Marketingseiten.
   * Die **maschinelle Übersetzung** kann für große Übersetzungsvolumen verwendet werden, bei denen die Zeit bis zur Veröffentlichung zu kurz ist, der Qualitätsanspruch nur zweitrangig ist oder die Kosten für eine menschliche Übersetzung zu hoch sind. Support-Wissensdatenbanken und benutzergenerierte Inhalte werden üblicherweise maschinell übersetzt.

* Nutzen Sie die Fachkenntnisse von Lokalisierungsdienstleistern, Adobe Consulting und Systemintegratoren zum Planen Ihrer multilingualen Site-Struktur sowie zum Erstellen von Prototypen und zum Testen davon.
