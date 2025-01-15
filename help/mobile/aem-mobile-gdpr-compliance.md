---
title: Adobe Experience Manager Mobile - Einhaltung der DSGVO
description: Erfahren Sie, wie Adobe Experience Manager Sie bei der Erfüllung Ihrer DSGVO-Compliance-Verpflichtungen unterstützen kann.
contentOwner: trushton
exl-id: d06e675f-fb61-47da-85de-e0b50dd44153
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 1%

---

# AEM Mobile - Einhaltung der DSGVO {#aem-mobile-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, die behandelten Details gelten jedoch für alle Datenschutzbestimmungen wie die DSGVO und den CCPA.

{{ue-over-mobile}}

## AEM Mobile-DSGVO-Support {#aem-mobile-gdpr-support}

AEM Mobile ist bereit, Kunden bei der Erfüllung ihrer DSGVO-Compliance-Verpflichtungen zu unterstützen. In AEM Mobile werden keine personenbezogenen Daten gespeichert. Wenn Sie über die entsprechenden Berechtigungen verfügen, können Sie sich mit Ihrer Adobe ID bei Adobe Experience Mobile anmelden.

<!-- [https://aemmobile.adobe.com/signin/index.html](https://aemmobile.adobe.com/signin/index.html) -->

## Adobe Digital Publishing Suite {#adobe-digital-publishing-suite}

Das Digital-Publishing-Produkt Adobe (das AEM Mobile vorausgeht) unterstützt Initiativen zur Einhaltung der DSGVO durch die Adobe. Siehe [https://business.adobe.com/privacy/general-data-protection-regulation.html](https://business.adobe.com/de/privacy/general-data-protection-regulation.html). Im Folgenden finden Sie Details zur Unterstützung für DSGVO-relevante Funktionen im Digital Publishing Suite-Produkt, einschließlich der Verwendung von Adobe zur Initiierung von DSGVO-bezogenen Anfragen.

Um sicherzustellen, dass Sie AEM Mobile nicht mit dem älteren Digital Publishing Suite-Produkt verwechseln, können Sie sich hier beim Digital Publishing Suite-Produkt anmelden:

[https://acrobat.adobe.com/us/en/](https://acrobat.adobe.com/us/en/)

### Initiieren einer DSGVO-Anfrage {#initiating-a-gdpr-request}

Wenden Sie sich an die Kundenunterstützung von Adobe, damit Sie eine DSGVO-Anfrage für die Digital Publishing Suite stellen können.

Die folgenden IDs sind erforderlich, um Kundendaten zu finden. Jede empfangene Teilmenge impliziert, dass die anderen IDs für diesen Benutzer nicht anwendbar waren.

Obligatorisch

* Vertrags-ID des Kunden: *dpsc-tractId*

Geben Sie mindestens eine der folgenden Optionen an:

* Der Kunde des Endbenutzers hat die OAuth-ID (die ID, die im direkten Berechtigungssystem des Kunden verwendet wird) angegeben: *dpsc-directEntitlementId*
* Für Benutzer der Windows-App die App Store-ID des Endbenutzers: *dpsc-windowsAppStoreId*
* Die E-Mail-Adresse, die der Endbenutzer für die Interaktion mit der DPS-App verwendet hat: *email*

### Häufig gestellte Fragen (FAQ) {#frequently-asked-questions-faq}

**Löscht Adobe meine App Store-Käufe, wenn eine DELETE-Anfrage initiiert wird?**

Adobe löscht Informationen über App-Store-Käufe (Abonnements usw.), aber Käufe werden weiterhin in den App-Stores aufgezeichnet. Wenn die App (Endbenutzer) im App Store angemeldet ist, werden diese Quittungen erneut aufgenommen und an Adobe gesendet. Später werden diese als neue Käufe betrachtet und von der App wiederhergestellt, wobei erneut auf zugegriffen wird.

**Löscht Adobe von Kundinnen oder Kunden bereitgestellte Berechtigungen beim Initiieren einer DELETE-Anfrage?**

Adobe löscht Informationen über die zusätzlichen direkten Berechtigungen des Kunden. Wenn sich die App (Endbenutzer) beim OAuth-Mechanismus anmeldet, den der Kunde verwendet hat, sendet sie Informationen an Adobe und die Services nehmen die zusätzlichen Berechtigungen wieder auf.

**Was wird vom Endbenutzer erwartet?**

Da sich der Schlüssel für die Zuweisung von Berechtigungen für die App auf dem Gerät als Teil der Viewer-Software befindet, sollte der Endbenutzer die App deinstallieren. Der Endbenutzer sollte erkennen, dass bei einer erneuten Installation der App vorhandene Käufe (die mit dem App Store-Benutzer verknüpft sind) und direkte Berechtigungen (die mit dem OAuth-Benutzer des Kunden verknüpft sind) weiterhin wiederhergestellt werden.

**Was passiert, wenn eine App von Personen auf einem Gerät gemeinsam genutzt wird?**

Adobe enthält nur minimale Informationen, die direkt mit einem bestimmten Benutzer verknüpft sind. Es verknüpft die Daten mit einer zufällig erstellten UUID, die in den Daten der App gespeichert ist und bei jeder Anfrage, die die App initiiert, übergeben wird. Das bedeutet, dass Endbenutzer, die die App auf demselben Gerät nutzen, dieselbe UUID verwenden und alle Daten als Eigentum der Person betrachtet werden, die die DSGVO-Anfrage stellt. Bei Zugriffs- und Löschanfragen berücksichtigt DPSC Personen, die eine App gemeinsam nutzen, als eine Person.

**Welche personenbezogenen Daten werden mit Analytics verfolgt?**

Ohne. Es werden Daten verfolgt, aber sie befinden sich auf Programmebene (nicht personenbezogen). Dazu gehören Ereignisse wie Starts, Abstürze, Schließen, Aktivitäten, Käufe oder Folioüberlagerungen. Geografische Standorte, Namen, Geräte-IDs oder IP-Adressen werden nicht verfolgt.

**Der Endbenutzer gab seine Informationen ein, es wurde jedoch nichts gefunden. Warum nicht?**

Im Zuge der Weiterentwicklung der Digital Publishing Suite wurden Service-Implementierungen verändert und mehr Daten verschleiert. Wenn anhand der vom Benutzer bereitgestellten Daten keine Daten gefunden wurden, bedeutet dies, dass die Daten des Benutzers nicht auf diese Person zurückverfolgt werden können.

### Beispiel {#example}

Wenden Sie sich an die Kundenunterstützung von Adobe, damit Sie eine DSGVO-Anfrage einleiten können.

Im Folgenden finden Sie ein Beispiel für die Ein- und Ausgabe einer Digital Publishing Suite-DSGVO-Anfrage:

#### Eingänge: {#inputs}

```
dpsc-contractId = "12345-1234-12416234" 
directEntitlementId = "1234-1234-1234" 
windowsAppStoreId = "testWinAppStoreId" 
email = "test@what.com"
```

#### Ausgaben {#outputs}

```
{

    "jobId": "test-1524750204384",

    "product": "DPSC",

    "action": "access",

    "userIDS": [

        {

        "namespace": "email",

        "value": "test@what.com"

        },

        {

        "namespace": "windowsAppStoreId",

        "value": "testWinAppStoreId"

        },

        {

        "namespace": "directEntitlementId",

        "value": "1234-1234-1234"

        }

    ],

    "receiptData": {

    "recordsFound": 6,

    "recordsAffected": 0,

    "tablesModified": 0,

    "subscriptionsFound": 24,

    "entitlementsFound": 24

    },

    "records": {

        "DPS_Stage_EntitlementUserDevices": [

        {

            "user_id": "testc685-c9ca-4c1e-a11b-07d10ec724cf",

            "device_id": "appleStore:test1b16-f032-4d9c-9200-0d19999405c4",

            "account_id": "test@what.com"

        },

        {

            "user_id": "test967d-5179-4dc6-958c-facd9d94da38",

            "device_id": "appleStore:test3f07-d5aa-4b32-8fac-b2b690b7ccd7",

            "account_id": "test@what.com"

        },

        {

            "user_id": "test1838-6494-4e74-912c-1edf61581d0e",

            "device_id": "appleStore:test3813-f8cc-49ce-b021-50eb0814a3bb",

            "account_id": "1234-1234-1234"

        },

        {

            "user_id": "test5468-1a11-4e4c-be43-274181a9ef81",

            "device_id": "appleStore:testf082-2783-498d-ab62-b1b2e3eb67ae",

            "account_id": "1234-1234-1234"

        }

        ],

            "DPS_Stage_EntitlementUsers": [

        {

            "id": "store:test04a7-33a3-4b90-863d-79981ead0f19:appleStore",

            "part_id": "0",

            "alias_user_id": "testWinAppStoreId"

        },

        {

            "id": "internal:testd2da-0606-4444-87ef-0d5a1d4a121d:adobe",

            "part_id": "0",

            "user_id": "test@what.com"

        }

        ],

            "DPS_Stage_Subscriptions": [

        {

            "id": "appleStore:testc685-c9ca-4c1e-a11b-07d10ec724cf",

            "account_id": "test3531-a209-4391-beb9-951c7822244e",

            "overflow": "test4e59-86a8-4b75-b699-77e980c287ab",

            "entitlement_count": "12"

        },

        {

            "id": "appleStore:test5468-1a11-4e4c-be43-274181a9ef81",

            "account_id": "test491b-379e-4d24-96ef-e481bf8d3062",

            "overflow": "test931b-7422-485d-85a5-134828187b6c",

            "entitlement_count": "12"

        }

        ],

            "DPS_Stage_Entitlements": [

        {

            "id": "samsungStore:testc685-c9ca-4c1e-a11b-07d10ec724cf",

            "account_id": "test7332-60a0-42b8-a508-474668d83d2e",

            "overflow": "test9bc3-94d0-43cf-b132-0629868f7d9d",

            "entitlement_count": "12"

        },

        {

            "id": "appleStore:test5468-1a11-4e4c-be43-274181a9ef81",

            "account_id": "testf766-102a-460d-8f5a-42f7bb9d68b7",

            "overflow": "test4d96-2197-45a8-9caf-2aa2846b770c",

            "entitlement_count": "12"

        }

        ],

            "s3Buckets": {

            "name": "DPS-Entitlements-Overflow",

            "folder": "stage/",

            "overflows": {

            "subscriptions": [

            "test4e59-86a8-4b75-b699-77e980c287ab",

            "test931b-7422-485d-85a5-134828187b6c"

        ],

            "entitlements": [

            "test9bc3-94d0-43cf-b132-0629868f7d9d",

            "test4d96-2197-45a8-9caf-2aa2846b770c"

                ]

            }

        }

    }

}
```
