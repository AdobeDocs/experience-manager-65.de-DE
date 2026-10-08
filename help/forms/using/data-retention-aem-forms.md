---
title: Datenaufbewahrung in AEM Forms
description: Erfahren Sie, wie Adobe Experience Manager (AEM) Forms standardmäßig als Pass-Through-Server fungiert und keine Formulardaten von Endbenutzern speichert, um den Datenschutz zu unterstützen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin, User
solution: Experience Manager Forms
feature: Adaptive Forms
source-git-commit: ca1448119778a2bcfeca7189aab5b360d992d99d
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 2%
---
# Datenaufbewahrung in AEM Forms {#data-retention-in-aem-forms}

Speichert AEM Forms Formulardaten? Standardmäßig nein. Adobe Experience Manager (AEM) Forms fungiert als Pass-Through-Server für Daten, die über adaptive Forms erfasst werden, und speichert keine Endbenutzerdaten im AEM-Repository. Stattdessen übergibt der Server die übermittelten Daten an das Ziel, dessen Eigentümer Sie sind und das Sie konfigurieren. Dieses Standardverhalten hilft Ihnen, Ihre Datenschutz- und Compliance-Ziele zu erreichen. Es gilt sowohl für AEM Forms on OSGi als auch für AEM Forms on JEE.

Da AEM Forms eine erweiterbare Plattform ist, können Sie AEM anpassen, um dieses Standardverhalten zu ändern. Wenn Ihre Anpassung die über ein adaptives Formular übermittelten Daten im AEM-Repository speichert oder in AEM-Protokolle schreibt, müssen Sie sicherstellen, dass diese Daten nicht auf Ihren Produktions- und Staging-Systemen gespeichert werden.

## Standardverhalten mit vordefinierten Funktionen {#default-behavior}

Wenn Sie vordefinierte adaptive Forms-Funktionen verwenden, speichert AEM Forms keine Endbenutzerdaten. Der Server übergibt die übermittelten Daten direkt an das Ziel, dessen Eigentümer Sie sind und das Sie konfigurieren.

Zu den vorkonfigurierten Mechanismen, die ein Formular mit einem Ziel verbinden, dessen Eigentümer Sie sind, gehören das Formulardatenmodell (FDM), vorkonfigurierte Connectoren und Übermittlungsaktionen. Jeder dieser Schritte sendet Daten an einen Speicherort, den Sie besitzen und konfigurieren, sodass er nicht im AEM-Repository beibehalten wird. Ein Formular kann auch einen externen Dienst oder einen Drittanbieterdienst, z. B. eine REST-API, aus einer Regel oder einer Übermittlungsaktion aufrufen und Daten an diesen Dienst weiterleiten, ohne die Daten in AEM zu persistieren.

Wenn Sie AEM-Workflows mit langlebigen Prozessen verwenden, die einen Genehmigungsschritt beinhalten, kann AEM Forms Daten im Speicher und in einem temporären Speicher speichern, um den Vorgang abzuschließen. Informationen zum Verhindern, dass diese Daten in AEM gespeichert werden, finden Sie [ Abschnitt „Daten in langlebigen Workflow-Prozessen](#long-lived-workflow-processes).

Die Übermittlungsaktion Forms Portal speichert erfasste oder über Adaptive Forms übermittelte Daten, die Daten werden jedoch an einem von Ihnen angegebenen und verwalteten Speicherort gespeichert und nicht im AEM-Repository oder in den Protokollen. Weitere Informationen finden Sie unter [Sichere Daten, die von der Übermittlungsaktion des Formularportals gespeichert werden](/help/forms/using/hardening-securing-aem-forms-environment.md#secure-data-saved-by-forms-portal-submit-action).

## Daten werden übertragen {#data-in-transit}

Obwohl in AEM Forms keine Endbenutzerdaten standardmäßig gespeichert werden, werden die Daten immer noch zwischen dem Endbenutzer, AEM Forms und dem von Ihnen konfigurierten Ziel verschoben. Sichern Sie diesen Traffic mit Transport Layer Security (TLS), damit Daten während der Übertragung verschlüsselt werden.

Um die Verbindung zwischen dem Browser und AEM zu sichern, aktivieren Sie HTTPS auf der AEM-Instanz. Die Schritte finden Sie unter [SSL/TLS By Default](/help/sites-administering/ssl-by-default.md).

Stellen Sie außerdem sicher, dass die Endpunkte, an die AEM Forms Daten sendet, z. B. Cloud-Konfigurationen, URLs für Übermittlungsaktionen und Formulardatenmodell-Datenquellen, sichere HTTPS-Endpunkte verwenden. Da AEM Forms die Daten, die es durchläuft, nicht speichert, gilt die Verschlüsselung im Ruhezustand nicht für diese Daten. Weitere Hinweise zum Sichern der Verbindung finden Sie unter [Sichere Transportschicht](/help/forms/using/hardening-securing-aem-forms-environment.md#secure-transport-layer).

## Formulardatenmodell für externe Datenspeicher {#form-data-model}

Verwenden Sie zum Lesen und Schreiben von Daten in einen Datenspeicher ein Formulardatenmodell (FDM). FDM ist der empfohlene Mechanismus, um ein Formular mit einer Datenquelle zu verbinden, deren Eigentümer Sie sind und die Sie verwalten, z. B. einer Datenbank oder einem RESTful-Webservice.

Weitere Informationen finden Sie unter [Einführung in die Datenintegration von AEM Forms](/help/forms/using/data-integration.md). Anleitungen zum Schützen der Daten, die ein FDM verarbeitet, finden Sie unter [Sichere Daten, die vom Formulardatenmodell (FDM) verarbeitet werden](/help/forms/using/hardening-securing-aem-forms-environment.md#secure-data-handled-by-form-data-model-fdm).

## Daten in langlebigen Workflow-Prozessen {#long-lived-workflow-processes}

Wenn Sie langlebige Workflow-Prozesse verwenden, kann AEM Daten vorübergehend als Teil der Workflow-Payload speichern. Die Workflow-Variablen, die diese Payload enthalten, werden in den Metadaten der Workflow-Instanz im AEM-Repository gespeichert und können personenbezogene Daten (PII) oder vertrauliche personenbezogene Daten (SPD) enthalten, die von Endbenutzern beim Ausfüllen eines adaptiven Formulars bereitgestellt werden.

Verwenden Sie die Datenexternalisierungsfunktion von AEM, um diese Daten in einem Repository zu speichern, das Sie besitzen und verwalten, z. B. Azure Blob-Speicher, anstatt in AEM. Wenn Sie die Variablen externalisieren, werden die Daten nicht im AEM-Repository gespeichert, sondern in Ihrem eigenen Daten-Repository.

Die Schritte zum Externalisieren von Daten finden Sie unter [Parametrisieren sensibler Daten in Workflow-Variablen und Speichern in externen Datenspeichern](/help/forms/using/aem-forms-workflow.md#externalize-wf-variables).

## Anpassung und Protokollierung {#customization-and-logging}

AEM ist eine anpassbare Lösung. Wenn Sie AEM anpassen, stellen Sie sicher, dass Ihre Anpassung keine Daten im AEM-Repository oder in den Protokollen speichert.

Wenn Sie Standardfunktionen verwenden, schreibt AEM Forms keine Formulardaten von Endbenutzern in Protokolle.

Benutzerdefinierter Code kann Daten in Protokolle schreiben. Wenn Sie während der Entwicklung Ablaufverfolgung oder Protokollierung hinzufügen, entfernen Sie Ablaufverfolgungen und Daten, die an Protokolle gesendet werden, bevor Sie Ihren Code in Staging- und Produktionsumgebungen bereitstellen.

## Häufig gestellte Fragen zur Datenaufbewahrung in AEM Forms {#faq}

**Speichert AEM Forms Formulardaten?**

Nein. Standardmäßig fungiert Adobe Experience Manager (AEM) Forms als Passthrough-Server für Daten, die über Adaptive Forms erfasst werden, und speichert keine Endbenutzerdaten im AEM-Repository. Der Server übergibt gesendete Daten an das Ziel, dessen Eigentümer Sie sind, und konfiguriert es, z. B. eine Formulardatenmodell-Datenquelle, ein Übermittlungsaktionsziel oder eine externe API. Dieses Standardverhalten gilt sowohl für AEM Forms unter OSGi als auch für AEM Forms unter JEE.

**Wo werden Daten adaptiver Formulare gespeichert?**

Die übermittelten Daten des adaptiven Formulars werden in dem Ziel gespeichert, dessen Eigentümer Sie sind und das Sie konfigurieren, und nicht im Adobe Experience Manager (AEM)-Repository. Vorkonfigurierte Mechanismen wie das Formulardatenmodell (FDM), Connectoren und Übermittlungsaktionen senden Daten an Ihren eigenen Speicherort. Ein Formular kann auch Daten an einen externen Service weiterleiten, z. B. eine REST-API, ohne sie in AEM zu persistieren. Die Forms Portal-Übermittlungsaktion speichert auch Daten an einem Speicherort, den Sie selbst bereitstellen und dessen Eigentümer Sie sind.

**Speichern langlebige Workflows Formulardaten?**

Langlebige Workflow-Prozesse in Adobe Experience Manager (AEM) Forms können Daten vorübergehend als Teil der Workflow-Payload speichern, die in den Metadaten der Workflow-Instanz im AEM-Repository gespeichert wird. Um diese Daten in einem Repository zu speichern, das Sie besitzen und verwalten, z. B. Azure Blob Storage, anstatt in AEM, verwenden Sie die Datenexternalisierungsfunktion von [AEM für Workflow-Variablen](/help/forms/using/aem-forms-workflow.md#externalize-wf-variables).

**Schreibt AEM Forms Daten in Protokolle?**

Nein. Mit Standardfunktionen schreibt Adobe Experience Manager (AEM) Forms keine Formulardaten von Endbenutzern in Protokolle. Da AEM eine anpassbare Plattform ist, kann benutzerdefinierter Code Daten in Protokolle schreiben. Wenn Sie während der Entwicklung Ablaufverfolgung oder Protokollierung hinzufügen, entfernen Sie diese Ablaufverfolgungen und alle protokollierten Daten, bevor Sie sie in Staging- und Produktionsumgebungen bereitstellen. Bei einer Anpassung dürfen keine Daten im AEM-Repository oder in Protokollen gespeichert werden.

**Wie werden Daten während der Übertragung geschützt?**

Übertragene Daten werden in Adobe Experience Manager (AEM) Forms mit Transport Layer Security (TLS) geschützt. Aktivieren Sie HTTPS auf der AEM-Instanz, um die Verbindung zwischen dem Browser und AEM zu sichern. Stellen Sie außerdem sicher, dass die Endpunkte, an die AEM Forms Daten sendet, z. B. Cloud-Konfigurationen, Übermittlungsaktion-URLs und Formulardatenmodell-Datenquellen, sichere HTTPS-Endpunkte verwenden. Da AEM Forms die Daten, die es durchläuft, nicht speichert, gilt die Verschlüsselung im Ruhezustand nicht für diese Daten.

## Verwandte Ressourcen {#related-resources}

* [Einführung in die AEM Forms-Datenintegration](/help/forms/using/data-integration.md)
* [Parametrisieren Sie vertrauliche Daten entsprechend den Workflow-Variablen und speichern Sie sie in externen Datenspeichern.](/help/forms/using/aem-forms-workflow.md#externalize-wf-variables)
* [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md)
* [Härtung und Sicherung von AEM Forms in OSGi-Umgebungen](/help/forms/using/hardening-securing-aem-forms-environment.md)
