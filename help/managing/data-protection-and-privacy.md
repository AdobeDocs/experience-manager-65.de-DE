---
title: Datenschutzbestimmungen – Einhaltung durch Adobe Experience Manager
description: Erfahren Sie mehr über die Adobe Experience Manager-Unterstützung für die verschiedenen Datenschutzbestimmungen. Dazu gehören die Datenschutz-Grundverordnung (DSGVO) der EU, das kalifornische Verbraucherdatenschutzgesetz und die Einhaltung der Vorschriften bei der Implementierung eines neuen AEM.
uuid: 9b0b8101-929c-4232-8c6e-1f9b8b2e0aa2
contentOwner: AEM Docs
topic-tags: introduction, grdp
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
discoiquuid: 0bcd7ac4-3071-466d-bd11-701f35ccf5bd
docset: aem65
exl-id: 46c1ca14-78f6-4b33-9fdf-1b90a9875f66
source-git-commit: d8ae63edd71c7d27fe93d24b30fb00a29332658d
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 41%

---

# Adobe Experience Manager – Einhaltung von Datenschutzbestimmungen {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion der Adobe auf Datenschutzprobleme und deren Bedeutung für Sie als Adobe finden Sie unter [Datenschutzzentrum der Adobe](https://www.adobe.com/de/privacy.html).

Adobe stellt Dokumentationen und Verfahren bereit (mit APIs, sofern verfügbar), damit der Datenschutzadministrator oder AEM Administrator Datenschutzanfragen bearbeiten kann. Es kann Ihnen dabei helfen, diese Vorschriften einzuhalten. Die dokumentierten Verfahren ermöglichen es Kunden, die regulatorischen Anforderungen manuell oder durch Aufruf von APIs, sofern verfügbar, über ein externes Portal oder einen externen Dienst auszuführen.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager beschränkt.
>
>Daten aus einem anderen Adobe-On-Demand-Dienst erfordern zusammen mit allen damit verbundenen Datenschutzanfragen, dass für diesen Dienst Maßnahmen ergriffen werden.
>
>Weitere Informationen finden Sie unter [Datenschutzzentrum der Adobe](https://www.adobe.com/de/privacy.html).

## Einführung {#introduction}

Instanzen von Adobe Experience Manager und die darauf ausgeführten Anwendungen werden von Adobe-Kunden kontrolliert und betrieben.

Daher sind Datenschutzbestimmungen wie die DSGVO, der CCPA und andere größtenteils Sache der Kunden.

In einer kurzen Einführung enthalten die Vorschriften für Datenschutz und Datenschutz neue Regeln, denen die Rollen folgender Personen folgen müssen:

* Unternehmens-Entitäten (CCPA) und/oder Datenverantwortliche (DSGVO)

* Dienstleister (CCPA) und/oder Auftragsverarbeiter (DSGVO)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. Erweiterte Definition personenbezogener Daten, um alle eindeutigen Kennungen einzuschließen; wie in direkt und indirekt identifizierbaren Daten.

2. Verschärfte Anforderungen an das Einverständnis.

3. Verstärkter Fokus auf Löschrechte (Datenlöschung).

4. Opt-out vom Verkauf von Daten.

Für Adobe Experience Manager gilt:

* Die Instanzen und die darauf ausgeführten Anwendungen liegen in der Verantwortung unserer Kunden und werden von ihnen betrieben.

   * Der Kunde verwaltet u. a. die regulatorischen Rollen, einschließlich Geschäftseinheiten und Dienstleister, Datenverantwortlicher und Datenverarbeiter.

   * Die Adobe Experience Platform Privacy Service ist nicht Teil des Workflows für AEM, wie in der folgenden Abbildung dargestellt.

* AEM umfasst Dokumentationen und Verfahren für den Datenschutzadministrator und/oder AEM-Administrator des Kunden, die Datenschutzanfragen manuell oder über APIs (sofern verfügbar) zu bearbeiten.

* Es wurde kein neuer Service und keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale von Kunden dokumentiert, die Datenschutzanfragen bearbeiten.

* AEM enthält keine nativen Tools zur Unterstützung des Workflows für Datenschutzanfragen.

   * Adobe bietet dem Datenschutzadministrator und AEM Administrator des Kunden Dokumentationen und Vorgehensweisen, mit denen er Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell ausführen kann.

Adobe bietet Verfahren für die Verarbeitung von Datenschutzanfragen im Zusammenhang mit Zugriff, Löschen und Opt-out für Adobe Experience Manager. Manchmal sind APIs verfügbar, die von einem kundenentwickelten Portal oder von Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Die folgende Abbildung zeigt, wie ein Workflow für Datenschutzanfragen aussehen könnte (unter Verwendung von Adobe Experience Manager 6.5):

![Datenschutz](assets/data-protection-and-privacy-01.png)

## Befolgung der Vorschriften durch Adobe Experience Manager {#aem-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie eine Regelungsdokumentation für Produktbereiche von AEM.

## AEM Foundation {#aem-foundation}

Siehe [Umgang mit Datenschutzanfragen für die AEM Foundation](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## AEM der Aktivierung der Sammlung von aggregierten Nutzungsstatistiken {#aem-opting-into-aggregate-usage-statistics-collection}

Siehe [Aggregierte Sammlung von Nutzungsstatistiken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Siehe [AEM Sites – Einhaltung von Datenschutzbestimmungen.](/help/sites-administering/gdpr-compliance-sites.md)

## AEM Commerce {#aem-commerce}

Siehe [AEM Commerce – Einhaltung von Datenschutzbestimmungen](/help/sites-administering/gdpr-compliance-commerce.md).

## AEM Mobile {#aem-mobile}

Siehe [AEM Mobile – Einhaltung von Datenschutzbestimmungen](/help/mobile/aem-mobile-gdpr-compliance.md).

## AEM-Integration mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager-Integrationen verfügen über datenschutzfreundliche Dienste (z. B. DSGVO oder CCPA). In AEM werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.

Weitere Informationen finden Sie in den folgenden Themen:

* [Adobe Target – Datenschutzübersicht](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=en)

* [Adobe Analytics-Datenschutz-Workflow](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html)

## AEM Communities {#aem-communities}

AEM Communities gibt den betroffenen Personen das Recht auf ihre Datenübertragbarkeit, ihr Recht auf Zugriff und ihr Recht auf Vergessenwerden durch [vordefinierte APIs](/help/communities/user-ugc-management-service.md). Diese APIs ermöglichen das Löschen und den Massenexport benutzergenerierter Inhalte sowie die Deaktivierung von Benutzerkonten, die über autorisierbare IDs identifiziert werden. Das permanente Löschen des Benutzerkontos ist jedoch durch das Löschen des Benutzerknotens in CRXDE Lite realisierbar, wodurch die Notwendigkeit eines einfachen Opt-out aus dem System abgedeckt wird.

Darüber hinaus bietet AEM Communities aufgrund der Massenmoderationskonsole, die es privilegierten Mitgliedern ermöglicht, Beiträge und Details der Benutzer zu finden und zu löschen, eingebauten Datenschutz. Die Mitgliederverwaltungskonsole ermöglicht die Beschränkung auf den Punkt, an dem ein Mitarbeiter verboten wird. Darüber hinaus werden die betroffenen Personen ermächtigt, die von ihnen erstellten Beiträge zu löschen.

## AEM Forms {#aem-forms}

AEM Forms umfasst Komponenten und Workflows, die Daten erfassen, verarbeiten und speichern, um Geschäftsprozesse zu koordinieren und digitale Transaktionen abzuschließen. Verschiedene Komponenten verwenden verschiedene Datenspeicher und ermöglichen auch die Integration in benutzerdefinierte Datenspeicher. In der folgenden Dokumentation werden Verfahren und Richtlinien für den Zugriff auf und die Verarbeitung von Benutzerdaten erläutert, um Datenschutzarbeitsabläufe (z. B. DSGVO oder CCPA) für eine Komponente zu unterstützen.

* [Formularportal](/help/forms/using/forms-portal-handling-user-data.md)
* [Korrespondenzverwaltung](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integration mit Adobe Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Forms-zentrierte Workflows auf OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [Forms JEE-Workflows](/help/forms/using/forms-workflow-jee-handling-user-data.md) (Nur AEM Forms JEE)
* [Document Security](/help/forms/using/document-security-handling-user-data.md) (Nur AEM Forms JEE)
* [Benutzerverwaltung](/help/forms/using/user-management-handling-user-data.md) (Nur AEM Forms JEE)
