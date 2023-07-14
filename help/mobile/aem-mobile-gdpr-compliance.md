---
title: Adobe Experience Manager Mobile - Einhaltung der DSGVO
description: Adobe Experience Manager Mobile - Einhaltung der DSGVO
uuid: 817c434f-4b78-40f7-99d6-6efafdedb77e
contentOwner: trushton
exl-id: d06e675f-fb61-47da-85de-e0b50dd44153
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 1%

---

# AEM Mobile - Einhaltung der DSGVO {#aem-mobile-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, die betroffenen Informationen gelten jedoch für alle Datenschutz- und Datenschutzbestimmungen. wie DSGVO und CCPA.

## DSGVO-Unterstützung von AEM Mobile {#aem-mobile-gdpr-support}

AEM Mobile ist bereit, Kunden bei der Einhaltung der DSGVO zu unterstützen. In AEM Mobile werden keine personenbezogenen Daten gespeichert. Wenn Sie bereitgestellt wurden, können Sie sich mit Ihrer Adobe ID bei Adobe Experience Mobile anmelden.

<!-- [https://aemmobile.adobe.com/signin/index.html](https://aemmobile.adobe.com/signin/index.html) -->

## Adobe Digital Publishing Suite {#adobe-digital-publishing-suite}

Das Digital Publishing-Produkt von Adobe (vor AEM Mobile) unterstützt Initiativen zur DSGVO-Bereitschaft der Adobe. Siehe [https://business.adobe.com/privacy/general-data-protection-regulation.html](https://business.adobe.com/de/privacy/general-data-protection-regulation.html). Im Folgenden finden Sie Details zur Unterstützung DSGVO-relevanter Funktionen im Digital Publishing Suite-Produkt, einschließlich der Verwendung von Adobe zur Initiierung von DSGVO-Anfragen.

Um sicherzustellen, dass Sie AEM Mobile nicht mit dem älteren Digital Publishing Suite-Produkt verwechseln, können Sie sich hier beim Digital Publishing Suite-Produkt anmelden:

[https://acrobat.adobe.com/us/en/](https://acrobat.adobe.com/us/en/)

### Initiieren einer DSGVO-Anfrage {#initiating-a-gdpr-request}

Wenden Sie sich an die Kundenunterstützung von Adobe, damit Sie eine DSGVO-Anfrage für die Digital Publishing Suite starten können.

Die folgenden IDs sind erforderlich, um Kundendaten zu finden. Jede erhaltene Untergruppe impliziert, dass die anderen IDs für diesen Benutzer nicht anwendbar waren.

Obligatorisch:

* Vertrags-ID des Kunden: *dpsc-contractId*

Geben Sie mindestens 1 der folgenden Werte an:

* Die vom Endbenutzer bereitgestellte OAuth-ID (die ID, die im Direktberechtigungssystem des Kunden verwendet wird): *dpsc-directEntitlementId*
* Für Windows-App-Benutzer die App Store ID des Endbenutzers: *dpsc-windowsAppStoreId*
* Die E-Mail-Adresse, die der Endbenutzer für die Interaktion mit der DPS-App verwendet hat: *email*

### Häufig gestellte Fragen (FAQ) {#frequently-asked-questions-faq}

**Löscht Adobe meine App Store-Käufe beim Starten einer DELETE-Anfrage?**

Adobe löscht Informationen über App Store-Käufe (Abonnements usw.), die Käufe werden jedoch weiterhin in den App Stores aufgezeichnet. Wenn die App (der Endbenutzer) im App Store angemeldet ist, werden diese Quittungen erneut abgerufen und an Adobe und später gesendet. Diese werden als neue Käufe betrachtet und von der App wiederhergestellt, damit sie erneut Zugriff erhalten.

**Löscht Adobe vom Kunden bereitgestellte Berechtigungen beim Initiieren einer DELETE-Anfrage?**

Adobe löscht Informationen, über die sie über die zusätzlichen direkten Berechtigungszertifikate des Kunden verfügt. Wenn sich die App (der Endbenutzer) beim vom Kunden verwendeten OAuth-Mechanismus anmeldet, werden Informationen an Adobe gesendet und die Dienste rufen die zusätzlichen Berechtigungen erneut ab.

**Was wird vom Endbenutzer erwartet?**

Da sich der Schlüssel für die Zuweisung von Berechtigungen zur App im Rahmen der Viewer-Software auf dem Gerät befindet, sollte der Endbenutzer die App deinstallieren. Der Endbenutzer sollte wissen, dass bei einer Neuinstallation der App vorhandene Käufe (die mit dem App Store-Benutzer verknüpft sind) und direkte Berechtigungszertifikate (die mit dem OAuth-Benutzer des Kunden verknüpft sind) weiterhin wiederhergestellt werden.

**Was passiert, wenn eine App von Personen auf einem Gerät gemeinsam genutzt wird?**

Adobe verfügt über minimale Informationen, die direkt mit einem bestimmten Benutzer verknüpft sind. Sie verknüpft die Daten mit einer zufällig erstellten UUID, die in den Daten der App gespeichert und in jeder von der App initiierten Anfrage übergeben wird. Das bedeutet, dass Endbenutzer, die die App auf demselben Gerät nutzen, dieselbe UUID verwenden und alle Daten als Eigentum der Person betrachtet werden, die die DSGVO-Anfrage sendet. Sowohl bei Zugriffs- als auch bei Löschanfragen betrachtet das DPSC Personen, die eine App teilen, als eine Person.

**Welche personenbezogenen Daten werden mit Analytics verfolgt?**

Ohne. Es werden Daten verfolgt, aber sie befinden sich auf App-Ebene (nicht auf persönlicher Ebene). Dazu gehören Ereignisse wie Starts, Abstürze, Schließen, Aktivitäten, Käufe oder Folio-Überlagerungen. Geografische Standorte, Namen, Geräte-IDs oder IP-Adressen werden nicht verfolgt.

**Der Endbenutzer gab seine Informationen an, es wurde jedoch nichts gefunden. Warum nicht?**

Mit der Weiterentwicklung des Digital Publishing Suite-Produkts wurden die Service-Implementierungen geändert und mehr Daten wurden verschleiert. Wenn mithilfe der vom Benutzer bereitgestellten Daten keine Daten gefunden wurden, bedeutet dies, dass die Daten des Benutzers nicht an diese Person zurückverfolgt werden können.

### Beispiel {#example}

Wenden Sie sich an die Kundenunterstützung von Adobe, damit Sie eine DSGVO-Anfrage starten können.

Im Folgenden finden Sie ein Beispiel für Eingaben und resultierende Ausgaben einer DSGVO-Anfrage der Digital Publishing Suite:

#### Eingaben: {#inputs}

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
