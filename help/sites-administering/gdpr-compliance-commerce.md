---
title: AEM Commerce – Einhaltung der DSGVO
description: Erfahren Sie mehr über die Verarbeitungsprozeduren für DSGVO-Anfragen in AEM Commerce und wie sie verwendet werden.
contentOwner: carlino
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
solution: Experience Manager, Experience Manager Sites
feature: Compliance
role: Admin, Developer, Leader, User
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
    internal-label: Administration and security
subfeature_v2:
  - id: c42c36cf-eeed-484a-8b39-a33a68192a07
    internal-label: Compliance
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 80%
---
# AEM Commerce – Einhaltung der DSGVO{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO dient in den folgenden Abschnitten als Beispiel, die jeweiligen Informationen gelten jedoch für alle Datenschutzvorschriften und -bestimmungen wie DSGVO, CCPA usw.

Die Datenschutz-Grundverordnung der Europäischen Union ist seit Mai 2018 in Kraft. Weitere Informationen finden Sie auf der [DSGVO-Seite im Adobe Privacy Center](https://business.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [AEM – Einhaltung der DSGVO](/help/managing/data-protection-and-privacy.md).

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

Bei den vorkonfigurierten Commerce-Integrationen von Adobe bildet AEM die Ebene für das Kundenerlebnis, auf der Dienste genutzt und Daten zurück an die an Kunden gerichtete Commerce-Plattform übermittelt werden, die in einem Headless-Modus ausgeführt wird.

Bei einigen Commerce-Plattformen werden Profilinformationen (`/home/users`) und Commerce-Token (zur Anmeldung bei der Commerce-Plattform) in AEM gespeichert. Informationen zu diesen Nutzungsszenarien finden Sie unter [Handhabung von DSGVO-bezogenen Anfragen zur AEM-Plattform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Handhabung von DSGVO-bezogenen Anfragen in AEM Commerce {#handling-gdpr-requests-for-aem-commerce}

Für die Salesforce Commerce Cloud-Integration speichert AEM Commerce keine DSGVO-relevanten Informationen. Leiten Sie die Anfrage an die [Salesforce Cloud](https://documentation.b2c.commercecloud.salesforce.com/DOC1/index.jsp) weiter.

Im Rahmen der Integration von hybris mit HCL WebSphere® Commerce werden bestimmte Daten in AEM gespeichert. Verwenden Sie die [DSGVO-Anweisungen für AEM Platform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) und berücksichtigen Sie dabei die folgenden Fragen:

1. **Wo werden meine Daten gespeichert/verwendet?** Zwischengespeicherte Benutzerprofilinformationen wie Name, Commerce-Benutzerkennung, Token, Kennwort und Adressdaten wie in AEM angezeigt.
1. **An wen gebe ich die erfassten DSGVO-Daten weiter?** Jegliche in Bezug auf die DSGVO relevanten Daten, die in AEM Commerce aktualisiert werden, werden nicht gespeichert (mit Ausnahme relevanter Profilinformationen, wie oben beschrieben), jedoch mittels Proxy zurück an die Commerce-Plattform übermittelt.
1. **Wie kann ich meine Benutzerdaten löschen**? Löschen Sie das Benutzerprofil in AEM und rufen Sie die Benutzerlöschung auf der Commerce-Plattform auf.

>[!NOTE]
>
>Konsultieren Sie bei Bedarf das [hybris-Wiki](https://wiki.hybris.com/) oder die [Dokumentation zu HCL WebSphere® Commerce](https://help.hcltechsw.com/commerce/index.html).
