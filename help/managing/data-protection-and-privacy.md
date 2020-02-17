---
title: Datenschutzbestimmungen und Datenschutzbestimmungen - Adobe Experience Manager-Bereitschaft
seo-title: Adobe Experience Manager Readiness for Data Protection and Data Privacy Regulations; wie GDPR, CCPA usw.
description: 'Erfahren Sie mehr über die Unterstützung von Adobe Experience Manager für die verschiedenen Datenschutzbestimmungen und Datenschutzbestimmungen. einschließlich der EU-Datenschutzverordnung (GDPR), des kalifornischen Datenschutzgesetzes für Verbraucher und der Frage, wie bei der Umsetzung eines neuen AEM-Projekts einzuhalten ist. '
seo-description: 'Erfahren Sie mehr über die Unterstützung von Adobe Experience Manager für die verschiedenen Datenschutzbestimmungen und Datenschutzbestimmungen. einschließlich der EU-Datenschutzverordnung (GDPR), des kalifornischen Datenschutzgesetzes für Verbraucher und der Frage, wie bei der Umsetzung eines neuen AEM-Projekts einzuhalten ist. '
uuid: 9b0b8101-929c-4232-8c6e-1f9b8b2e0aa2
contentOwner: aheimoz
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: grdp
discoiquuid: 0bcd7ac4-3071-466d-bd11-701f35ccf5bd
docset: aem65
translation-type: tm+mt
source-git-commit: 9b16c8ae2ee28c60f35f9e0f990d79173463c33b

---


# Adobe Experience Manager Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Bitte konsultieren Sie die Rechtsabteilung Ihres Unternehmens, um sich über die Datenschutzbestimmungen zu informieren.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie im Datenschutzzentrum von [Adobe](https://www.adobe.com/privacy.html).

Adobe stellt Dokumentation und Vorgehensweisen bereit (mit APIs, sofern verfügbar), damit der Datenschutzadministrator oder AEM-Administrator Datenschutzanforderungen bearbeiten und unsere Kunden bei der Einhaltung dieser Vorschriften unterstützen kann. Die dokumentierten Verfahren ermöglichen es den Kunden, die Regelungsanforderungen manuell oder, falls verfügbar, über ein externes Portal oder einen externen Dienst in APIs auszuführen.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager beschränkt.
>
>Daten eines anderen Adobe On-Demand-Dienstes erfordern zusammen mit allen damit zusammenhängenden Datenschutzanforderungen Maßnahmen, die für diesen Dienst durchgeführt werden müssen.
>
>Weitere Informationen finden Sie im Datenschutzzentrum von [Adobe](https://www.adobe.com/privacy.html).

## Einführung {#introduction}

Instanzen von Adobe Experience Manager und die darauf ausgeführten Anwendungen gehören unseren Kunden und werden von ihnen betrieben.

Daher sind Datenschutzbestimmungen wie GDPR, CCPA und andere weitgehend in der Verantwortung der Kunden.

Die Vorschriften für den Datenschutz und den Datenschutz enthalten in Kürze neue Regeln, denen die Rollen folgender Personen folgen müssen:

* Geschäftseinheiten (CCPA) und/oder Datenkontrolleure (GDPR)

* Serviceanbieter (CCPA) und/oder Datenprozessoren (GDPR)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. erweiterte Definition personenbezogener Daten, um alle eindeutigen IDs einzuschließen; wie in direkt oder indirekt identifizierbaren Daten.

2. Verbesserte Anforderungen an die Zustimmung.

3. Verbesserter Fokus auf Löschrechte (Datenlöschung).

4. Ausschluss des Verkaufs von Daten.

Für Adobe Experience Manager:

* Die Instanzen und Anwendungen, die auf ihnen ausgeführt werden, gehören dem Kunden und werden von ihm betrieben.

   * Das bedeutet, dass der Kunde die regulatorischen Rollen, einschließlich Geschäftseinheiten und Dienstanbieter, Datencontroller und Datenprozessor, unter anderem verwaltet.

   * Der Datenschutzdienst für Adobe Experience Platform ist nicht Teil des Arbeitsablaufs für AEM, wie in der Abbildung unten dargestellt.

* AEM umfasst Dokumentation und Verfahren für den Datenschutzadministrator des Kunden und/oder AEM-Administrator, um die Datenschutzregulierungsanforderungen auszuführen. entweder manuell oder über APIs, falls verfügbar.

* Es wurde kein neuer Dienst oder keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale des Kunden dokumentiert, die Datenschutzanforderungen bearbeiten.

* AEM enthält keine standardmäßigen Werkzeuge zur Unterstützung des Arbeitsablaufs für Datenschutzanforderungen.

   * Adobe stellt Dokumentation und Vorgehensweisen für den Datenschutzadministrator und/oder AEM-Administrator bereit, damit diese Anforderungen im Zusammenhang mit den Datenschutzbestimmungen manuell ausführen können.

Adobe stellt Verfahren für die Verarbeitung von Datenschutzanforderungen im Zusammenhang mit Zugriff, Löschen und Ausschließen für Adobe Experience Manager bereit. In einigen Fällen stehen APIs zur Verfügung, die von einem vom Kunden entwickelten Portal oder Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Das folgende Diagramm zeigt, wie ein Arbeitsablauf für Datenschutzanforderungen aussehen könnte (dargestellt mit Adobe Experience Manager 6.5):

![Datenschutz und Datenschutz](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager und Regulatory Readiness {#aem-and-regulatory-readiness}

Die Dokumentation zu den Produktbereichen von AEM finden Sie in den folgenden Abschnitten.

## AEM Foundation {#aem-foundation}

Siehe [Umgang mit Datenschutz- und Datenschutzanforderungen für die AEM Foundation](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## AEM-Aktivierung zur aggregierten Sammlung von Nutzungsstatistiken {#aem-opting-into-aggregate-usage-statistics-collection}

Siehe [Aggregierte Sammlung von Nutzungsstatistiken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Siehe [AEM-Sites - Datenschutz und Datenschutzbereitschaft.](/help/sites-administering/gdpr-compliance-sites.md)

## AEM Commerce {#aem-commerce}

Siehe [AEM Commerce - Datenschutz und Datenschutzbereitschaft](/help/sites-administering/gdpr-compliance-commerce.md).

## AEM Mobile {#aem-mobile}

Siehe [AEM Mobile - Datenschutz und Datenschutzbereitschaft](/help/mobile/aem-mobile-gdpr-compliance.md).

## AEM-Integration mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager-Integrationen sind mit datenschutzfertigen Diensten (z. B. GDPR oder CCPA) ausgestattet. In AEM werden keine persönlichen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe Target - Datenschutzübersicht](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics Data Privacy Workflow](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)

## AEM Communities {#aem-communities}

AEM Communities bietet [gebrauchsfertige APIs](/help/communities/user-ugc-management-service.md), mit deren Hilfe Einzelpersonen (sogenannte „Datensubjekte“) gemäß DSGVO das Recht auf Übertragbarkeit ihrer Daten, auf Zugriff auf ihre Daten und auf Löschung ihrer Daten („Recht auf Vergessenwerden“) vollumfänglich eingeräumt werden kann. Diese APIs ermöglichen die Massenlöschung sowie den Massenexport von benutzergenerierten Inhalten und das Deaktivieren von Benutzerkonten über deren autorisierbare ID. Das dauerhafte Löschen eines Benutzerkontos erfolgt dagegen durch Löschen des entsprechenden Benutzerknotens in CRXDE Lite, wodurch die DSGVO-Anforderung zur Bereitstellung einer einfachen Möglichkeit für die Abmeldung beim System erfüllt wird.

Darüber hinaus gewährleistet AEM Communities mit der Konsole für die Massenmoderation den im Rahmen der DSGVO geforderten Datenschutz durch Technik („Privacy by Design“), mit deren Hilfe privilegierte Mitglieder die Beiträge und Daten der Benutzer suchen und löschen können. Die Konsole für die Mitgliederverwaltung ermöglicht es zudem, den Zugriff insoweit einzuschränken, dass Mitwirkende ausgeschlossen werden können. Darüber hinaus ermöglicht sie es Datensubjekten, von ihnen erstellte Beiträge zu löschen.

## AEM Forms {#aem-forms}

AEM Forms beinhaltet Komponenten und Workflows, die zur Orchestrierung von Geschäftsprozessen und zum Abschließen von digitalen Transaktionen Daten erfassen, verarbeiten und speichern. Die einzelnen Komponenten verwenden unterschiedliche Datenspeicher und ermöglichen darüber hinaus die Integration mit benutzerdefinierten Datenspeichern. In der folgenden Dokumentation werden Verfahren und Richtlinien für den Zugriff auf und die Verarbeitung von Benutzerdaten zur Unterstützung von Datenschutz- und Datenschutzarbeitsabläufen (z. B. GDPR oder CCPA) für eine Komponente erläutert.

* [Formularportal](/help/forms/using/forms-portal-handling-user-data.md)
* [Korrespondenzverwaltung](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integration mit Adobe Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Forms-zentrierte Workflows auf OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [Forms JEE-Workflows](/help/forms/using/forms-workflow-jee-handling-user-data.md) (nur AEM Forms JEE)
* [Document Security](/help/forms/using/document-security-handling-user-data.md) (nur AEM Forms JEE)
* [Benutzerverwaltung](/help/forms/using/user-management-handling-user-data.md) (nur AEM Forms JEE)
