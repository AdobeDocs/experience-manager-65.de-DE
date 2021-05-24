---
title: AEM Commerce – Einhaltung der Datenschutz-Grundverordnung
seo-title: AEM Commerce – Einhaltung der Datenschutz-Grundverordnung
description: '"AEM Commerce – Einhaltung der Datenschutz-Grundverordnung"'
seo-description: 'null'
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 70%

---

# AEM Commerce – Einhaltung der Datenschutz-Grundverordnung{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, die betroffenen Informationen gelten jedoch für alle Datenschutz- und Datenschutzbestimmungen. wie DSGVO, CCPA usw.

Die Datenschutz-Grundverordnung der Europäischen Union ist seit Mai 2018 in Kraft. Weitere Informationen finden Sie auf der [DSGVO-Seite im Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Weitere Details hierzu finden Sie unter [Einhaltung der Datenschutz-Grundverordnung mit AEM](/help/managing/data-protection-and-privacy.md).

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

Bei unseren gebrauchsfertigen Commerce-Integrationen bildet AEM die Ebene für das Kundenerlebnis, auf der Dienste genutzt und Daten zurück an die an Kunden gerichtete Commerce-Plattform übermittelt werden, die in einem Headless-Modus ausgeführt wird.

Bei einigen Commerce-Plattformen speichern wir Profilinformationen ( `/home/users`) und Commerce-Token (zur Anmeldung bei der Commerce-Plattform) in AEM. Informationen zu diesen Nutzungsszenarien finden Sie unter [Handhabung von DSGVO-bezogenen Anfragen mit der AEM-Plattform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Handhabung von DSGVO-bezogenen Anfragen in AEM Commerce {#handling-gdpr-requests-for-aem-commerce}

Im Rahmen der Integration mit der Salesforce Commerce Cloud speichert AEM Commerce keine in Bezug auf die DSGVO relevanten Informationen. Übermitteln Sie entsprechende Anfragen an die [Salesforce Cloud](https://documentation.demandware.com/).

Für die hybris- und IBM WebSphere-Integrationen gibt es einige Daten in AEM. Konsultieren Sie hierzu die [Anweisungen bezüglich der Einhaltung der DSGVO mit der AEM-Plattform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) und berücksichtigen Sie dabei folgenden Fragen:

1. **Wo werden die Daten gespeichert/verwendet?** Zwischengespeicherte Benutzerprofilinformationen wie Name, Commerce-Benutzerkennung, Token, Kennwort, Adressdaten usw. werden aus AEM angezeigt.
1. **An wen werden die in Bezug auf die DSGVO relevanten Daten weitergeben?** Jegliche in Bezug auf die DSGVO relevanten Daten, die in AEM Commerce aktualisiert werden, werden nicht gespeichert (mit Ausnahme relevanter Profilinformationen, wie oben beschrieben), jedoch mittels Proxy zurück an die Commerce-Plattform übermittelt.
1. **Wie lösche ich die Benutzerdaten?** Löschen Sie das Benutzerprofil in AEM und rufen Sie die Funktion zum Löschen von Benutzern auf der Commerce-Plattform auf.

>[!NOTE]
>
>Konsultieren Sie bei Bedarf die [hybris Wiki](https://wiki.hybris.com/) oder die [Dokumentation zu Websphere Commerce](https://www-01.ibm.com/support/docview.wss?uid=swg27036450).
