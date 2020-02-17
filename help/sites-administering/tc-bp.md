---
title: Best Practices für die Übersetzung
seo-title: Best Practices für die Übersetzung
description: Hier finden Sie Best Practices für die Einrichtung und Ausführung von Übersetzungsprojekten – zusammengestellt von Technik- und Beratungsteams von Adobe.
seo-description: Hier finden Sie Best Practices für die Einrichtung und Ausführung von Übersetzungsprojekten – zusammengestellt von Technik- und Beratungsteams von Adobe.
uuid: 3bac1d73-9696-4c9b-8bdd-6f00fac40cf7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 1554010e-a1d1-4edf-b28f-9eead8f83b4a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Best Practices für die Übersetzung{#translation-best-practices}

## Allgemein {#general}

Das Erstellen bzw. Erweitern einer globalen Webpräsenz kann ein komplexer Prozess sein, aber mit Voraussicht und Planung kann AEM Ihre Bemühungen vereinfachen und Ihre globalen Unternehmensziele unterstützen.

* **Planen Sie die globale Expansion** , bevor Sie Ihre erste Site implementieren. Es ist für gewöhnlich schwieriger, eine vorhandene Website für globale Abdeckung anzupassen, wenn die Website kurzfristig implementiert wurde, als wenn Sie von Anfang an auf eine globale Expansion hin planen:

   * Prüfen Sie den aktuellen Status der Lokalisierungsreife Ihrer Organisation. Determine whether you have the **tools**, **processes** and **resources** in place to support global expansion.
   * Be aware of **global regulations** and **regional language preferences**. Entwerfen Sie flexible Inhaltsstrukturen und -prozesse, die für eine in ständigem Wandel befindliche globale Geschäftsumgebung geeignet sind.

* Determine a **governance** model that supports your global business and use AEM mechanisms like MSM and user permissions to enforce your chosen model. Legen Sie beispielsweise fest, ob Inhalte zentral verfasst und an Regionen/Länder verteilt oder von ihnen abgerufen werden. Legen Sie fest, welche Inhalte in Regionen entsperrt und geändert werden können. Legen Sie fest, wer für das Initiieren und Verwalten von Übersetzungen zuständig ist.
* Falls die Ressourcensituation es erlaubt, sollten Übersetzungsaktivitäten von einem zentralen Team verwaltet werden, das Fachwissen hinsichtlich der nötigen Tools, Prozesse und Lieferantenbeziehungen entwickeln kann.
* **Planen**, **Prototypen** und **testen** Sie Ihre globale Struktur und Ihre Prozesse, um sicherzustellen, dass sie das Unternehmen unterstützen und dass Sie die erforderliche Unterstützung von Interessengruppen in den geografischen Regionen erhalten.

## Site-Struktur {#site-structure}

* Beginnen Sie den Entwurf der Site-Struktur mit der Untersuchung Ihrer Inhalte und stellen Sie fest, wo und in welcher Sprache Inhalte verfasst werden. Dieser Ort muss die höchste Ebene Ihrer Website darstellen.
* Bewährt und empfohlen ist eine **sprachbasierte Struktur** mit höchstens drei Ebenen zwischen den Autorenaktivitäten auf höchster Ebene und den landesspezifischen Websites.
* Verwenden Sie für sprachen- bzw. länderspezifische Websites eine Benennungskonvention, die **W3C-Standards** entspricht.
* Legen Sie fest, wie Inhalte nach Regionen und Ländern verteilt werden. Berücksichtigen Sie Länder, in denen dieselbe Sprache gesprochen wird. Es wird empfohlen, Sprach-Master zu erstellen, eine Ebene nicht aktivierter Seiten, auf denen übersetzte Inhalte überprüft und geändert und dann an eine länderspezifische Website mit der jeweiligen Sprache verteilt oder von ihr abgerufen werden können.
* Zum Erstellen von Sprach-Mastern gibt es zwei Ansätze, einen mit Sprachkopien und einen mit MSM-/Live Copies.

   * Der Ansatz mit den Sprachkopien wird vom standardmäßigen Übersetzungsintegrations-Framework von AEM verwendet und stellt daher die einfachste Methode für den Anfang dar. Das Framework bietet eine Benutzeroberfläche, die es zunächst einfach macht, inhaltliche Änderungen vom Master der Hauptsprache an Sprach-Master weiterzugeben und zu übersetzen. Mit dem Wachstum des Projekts wird die Workflow-Automatisierung jedoch immer notwendiger für die Verwaltung der Übersetzung der steigenden Anzahl von Seiten und/oder Sprachen.
   * Der Ansatz mit MSM/Live Copies ist möglicherweise eine Alternative für fortgeschrittene Anwendungsfälle mit größeren, komplexeren Websites. Zur Verwaltung der komplexen Vererbungsverhältnisse zwischen der Hauptsprache und den Sprach-Mastern sowie zur Verringerung des Risikos, bestehende Übersetzungen zu überschreiben, sind starke Governance und effiziente Workflow-Automatisierung erforderlich. Diese Verwaltung ist mithilfe von Übersetzungs-Connectors möglich. See [MSM and Multilingual Sites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites) for more information.

* Wenn bei der Master-Sprache globale Varianten vorliegen, ist eine Option, mit MSM eine Live Copy vom globalen Master zur Übersetzung zu erstellen. Wenn beispielsweise in einem Master in amerikanischem Englisch eine Bearbeitung durchgeführt wird, erstellen Sie einen Master in internationalem Englisch als Live Copy und Grundlage für die Übersetzung in andere Sprachen.
* Verwenden Sie MSM zur Erstellung von länderspezifischen Websites aus den übersetzten Sprach-Mastern und für den Rollout von Inhalten an Websites mit derselben Sprache. Beispielsweise kann der französische Sprach-Master an die Websites von Frankreich, Belgien und die Schweiz bereitgestellt werden.
* Planen Sie, erstellen Sie Prototypen und führen Sie Tests durch, bevor Sie die Implementierung beginnen.

## Übersetzungsprozesse und -methoden {#translation-processes-and-methods}

* Engage a **localization service provider (LSP)** with expertise in translation and related localization activities. Lokalisierungsdienstleister helfen bei der Skalierung Ihres globalen Unternehmens, indem sie ein Spektrum an Ressourcen und Technologien zur Verfügung stellen, welche die Effizienz verbessern und Übersetzungskosten sparen:

   * Einige Lokalisierungsdienstleister sind auch Technologieanbieter. Es gibt auch eigenständige Technologieanbieter, die vielen Lokalisierungsdienstleistern die Arbeit auf ihren Übersetzungsplattformen ermöglichen.
   * The **AEM Translation Framework** supports integration with a variety of translation technology providers for both machine and human translation.
   * Erfahren Sie, wie Sie [Connectors für Lokalisierungsdienstleister in Ihr AEM-System integrieren](/help/sites-administering/translation.md), um die Übersetzung von Inhalten zu automatisieren, bzw. wie Sie zum Testen oder in Fällen, wo kein Lokalisierungsdienstleister bzw. Übersetzungstechnologieanbieter vorhanden ist, Übersetzungsprojekte erstellen, exportieren und importieren.

* Choose a **translation method** that best suits the content.

   * **Humanübersetzungen** eignen sich am besten für Inhalte, bei denen Messaging und Qualitätserwartungen hoch sind und der Inhalt einige Zeit auf der Site leben wird, z. B. Marketingseiten.
   * **Eine maschinelle Übersetzung** kann eine gute Wahl für große Mengen von Übersetzungen sein, wenn die Zeit bis zur Veröffentlichung kritisch ist, die Qualitätsanforderungen gelockert werden oder die menschlichen Übersetzungskosten untragbar sind. Support-Wissensdatenbanken und benutzergenerierte Inhalte werden üblicherweise maschinell übersetzt.

* Nutzen Sie die Fachkenntnisse von Lokalisierungsdienstleistern, Adobe Consulting und Systemintegratoren zum Planen Ihrer multilingualen Site-Struktur sowie zum Erstellen von Prototypen und zum Testen davon.

