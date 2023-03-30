---
title: AEM Commerce – Einhaltung der Datenschutz-Grundverordnung
seo-title: AEM Commerce - GDPR Readiness
description: "AEM Commerce\_– Einhaltung der Datenschutz-Grundverordnung"
seo-description: null
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
source-git-commit: 71842228dd3cb1ce3b79728912e8333d25fccefc
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 13%

---

# AEM Commerce – Einhaltung der Datenschutz-Grundverordnung{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, die betroffenen Informationen gelten jedoch für alle Datenschutz- und Datenschutzbestimmungen. wie DSGVO und CCPA.

Die Datenschutz-Grundverordnung der Europäischen Union ist seit Mai 2018 in Kraft. Siehe [DSGVO-Seite im Adobe Privacy Center](https://business.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Siehe [AEM Einhaltung der DSGVO](/help/managing/data-protection-and-privacy.md) für weitere Informationen.

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

Mit den vordefinierten Commerce-Integrationen von Adobe ist AEM die Erlebnisebene, die Dienste nutzt und Daten an die Commerce-Plattform des Kunden zurücksendet, die im Headless-Modus ausgeführt wird.

Bei einigen Commerce-Plattformen speichert Adobe Profilinformationen ( `/home/users`) und Commerce-Token (zur Anmeldung in der Commerce-Plattform) in AEM. Lesen Sie für diese Anwendungsfälle [Umgang mit DSGVO-Anfragen für die AEM Plattform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Handhabung von DSGVO-bezogenen Anfragen in AEM Commerce {#handling-gdpr-requests-for-aem-commerce}

Für die Salesforce-Commerce Cloud-Integration speichert AEM Commerce keine DSGVO-relevanten Informationen. Weiterleiten der Anfrage an die [Salesforce Cloud](https://documentation.b2c.commercecloud.salesforce.com/DOC1/index.jsp).

Für die hybris- und HCL WebSphere® Commerce-Integrationen gibt es einige Daten in AEM. Verwenden Sie die [DSGVO-Anweisungen für AEM Platform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) und berücksichtigen diese Fragen:

1. **Wo werden meine Daten gespeichert/verwendet?** Zwischengespeicherte Benutzerprofilinformationen wie Name, Commerce-Benutzer-ID, Token, Kennwort und Adressdaten, wie aus AEM gezeigt.
1. **Für wen gebe ich die erfassten DSGVO-Daten frei?** Jede Aktualisierung der DSGVO-relevanten Daten in AEM Commerce wird nicht gespeichert (mit Ausnahme der relevanten Profilinformationen, wie oben erwähnt), sondern an die Commerce-Plattform zurückgesendet.
1. **Löschen meiner Benutzerdaten**? Löschen Sie das Benutzerprofil in AEM und rufen Sie die Benutzerlöschung auf der Commerce-Plattform auf.

>[!NOTE]
>
>Sehen Sie sich die [Hybris Wiki](https://wiki.hybris.com/) oder [HCL WebSphere® Commerce-Dokumentation](https://help.hcltechsw.com/commerce/index.html), falls erforderlich.
