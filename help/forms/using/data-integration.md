---
title: Datenintegration für AEM Forms
seo-title: AEM Forms Data Integration
description: Mit der Datenintegration können Sie AEM Forms mit unterschiedlichen Datenquellen integrieren und ein Formulardatenmodell zum Erstellen und Arbeiten mit adaptiven Formularen und interaktiver Kommunikation erstellen.
seo-description: Data Integration lets you integrate AEM Forms with disparate data sources and create form data model to create and work with adaptive forms and interactive communications.
uuid: 01df045e-1b26-437c-9674-fd223ecd5097
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
discoiquuid: e397c6ce-d73f-4183-8445-1897a8906960
docset: aem65
feature: Form Data Model
exl-id: dd1146e4-952d-4dfa-8084-46c6096c4177
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '521'
ht-degree: 100%

---

# [!DNL AEM Forms]-Datenintegration {#aem-forms-data-integration}

![](do-not-localize/data-integeration.png)

Unternehmensinfrastrukturen umfassen unterschiedliche Back-End-Systeme oder Datenquellen wie Datenbanken, Webservices, REST-Services, OData-Services und CRM-Lösungen. Zusammen bilden sie ein Informationssystem, das Daten für Unternehmensanwendungen zur Abwicklung des Tagesgeschäfts bereitstellt. Umgekehrt erfassen die Anwendungen Daten und senden sie zurück, um die Datenquellen zu aktualisieren.

Für [!DNL AEM Forms]-Programme wie adaptive Formulare und interaktive Kommunikation ist die Integration in Datenquellen erforderlich, damit Kundendaten abgerufen, während Formulare gerendert werden und die interaktive Kommunikation erstellt wird. Es gibt Anwendungsfälle, bei denen Daten basierend auf Benutzereingaben in adaptiven Formularen aus Datenquellen abgerufen werden. Zusätzlich können die übermittelten Daten im adaptiven Formular zurückgeschrieben werden, um die jeweiligen Datenquellen zu aktualisieren.

Verteilte, modulare Systeme bieten ihre Vorteile, die Herausforderung besteht jedoch darin, Datenverknüpfungen datenquellenübergreifend zu integrieren und zu erstellen. Datenintegration ist der Schlüssel zu einer funktionsfähigen und effizienten Unternehmensinfrastruktur mit unterschiedlichen Datenquellen, die für den Austausch von Geschäftsdaten mit Anwendungen verbunden sind.

## Übersicht über die Datenintegration {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms]-Datenintegration ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit [!DNL AEM Forms]. In der intuitiven Benutzeroberfläche können Sie eine einheitliche Datendarstellung der Geschäftsbereiche und Services für sämtliche verbundenen Datenquellen erstellen. Diese einheitliche Darstellung wird als Formulardatenmodell bezeichnet. Es handelt sich um eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell werden als Datenmodellobjekte bezeichnet. Ein Formulardatenmodell gibt Ihnen folgende Möglichkeiten:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Services aus verbundenen Datenquellen.
* Erstellen benutzerdefinierter Datenmodellobjekten und -eigenschaften.
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten innerhalb und zwischen Datenquellen.
* Aufrufen von Services für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Nachdem Sie ein Formulardatenmodell erstellt haben, können Sie es in verschiedenen Workflows für adaptive Formulare und interaktive Kommunikation verwenden, zum Beispiel:

* Erstellen adaptiver Formulare und interaktiver Kommunikation basierend auf dem Formulardatenmodell
* Ausfüllen adaptiver Formulare und interaktiver Kommunikation aus konfigurierten Datenquellen 
* Aufrufen von Datenquellendiensten/-vorgängen mit Regeln für adaptive Formulare
* Übermittelte Formulardaten in Datenquellen schreiben

## Erste Schritte mit der Datenintegration {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration besteht darin, Datenquellen, die Informationen speichern, die Sie in Anwendungsfällen für adaptive Formulare und interaktive Kommunikation verwenden möchten, zu identifizieren und zu konfigurieren. Als Nächstes erstellen Sie ein Formulardatenmodell, das Datenmodellobjekt, Eigenschaften und Dienste aus einer oder mehreren Datenquellen verwendet. Sie können adaptive Formulare und interaktive Kommunikation basierend auf einem Formulardatenmodell erstellen, bei dem adaptive Formularfelder oder Platzhalter in interaktiver Kommunikation an die jeweiligen Datenquelleneigenschaften gebunden sind.

Mit [!DNL AEM Forms] können Sie auch ein Formulardatenmodell erstellen, das unabhängig von Datenquellen ist, und Datenmodellobjekte und -eigenschaften im Formulardatenmodell später mit Datenquellen verknüpfen. Dadurch werden alle Abhängigkeiten von Datenquellen beseitigt, während Sie an einem Formulardatenmodell arbeiten.

Lesen Sie folgende Informationen für die ersten Schritte mit der Datenintegration, um sie zu verstehen und zu implementieren.

* [Konfigurieren von Datenquellen](../../forms/using/configure-data-sources.md)
* [Erstellen des Formulardatenmodells](../../forms/using/create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](../../forms/using/work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells](../../forms/using/using-form-data-model.md)
