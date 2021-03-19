---
title: AEM Mobile – Einhaltung der Datenschutz-Grundverordnung
seo-title: AEM Mobile – Einhaltung der Datenschutz-Grundverordnung
description: '"AEM Mobile – Einhaltung der Datenschutz-Grundverordnung"'
seo-description: 'null'
uuid: 817c434f-4b78-40f7-99d6-6efafdedb77e
contentOwner: trushton
discoiquuid: 9399dd3d-a485-4f53-a6f2-7b190da4235b
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 89%

---


# AEM Mobile – Einhaltung der Datenschutz-Grundverordnung {#aem-mobile-gdpr-readiness}

>[!IMPORTANT]
>
>GDPR wird als Beispiel in den folgenden Abschnitten verwendet, aber die betreffenden Details gelten für alle Datenschutz- und Datenschutzbestimmungen. wie GDPR, CCPA usw.

## AEM Mobile – Unterstützung der Datenschutz-Grundverordnung {#aem-mobile-gdpr-support}

AEM Mobile kann Kunden bei der Erfüllung ihrer DSGVO-Compliancepflichten unterstützen. In AEM Mobile werden keine personenbezogenen Daten gespeichert. Wenn Sie über eine Adobe ID verfügen, können Sie sich damit bei Adobe Experience Mobile anmelden.

[https://aemmobile.adobe.com/signin/index.html](https://aemmobile.adobe.com/signin/index.html)

## Adobe Digital Publishing Suite {#adobe-digital-publishing-suite}

Das Produkt von Adobe für digitales Publishing (Vorgänger von AEM Mobile) unterstützt die Initiativen von Adobe zur Einhaltung der Datenschutz-Grundverordnung. Weitere Informationen finden Sie unter [https://www.adobe.com/de/privacy/general-data-protection-regulation.html](https://www.adobe.com/de/privacy/general-data-protection-regulation.html). Im Folgenden erhalten Sie nähere Informationen zur Unterstützung für DSGVO-relevante Funktionen in Digital Publishing Suite. Dazu gehören auch Informationen, wie Sie zusammen mit Adobe DSGVO-Anfragen intitiieren können.

Um sicherzustellen, dass Sie AEM Mobile nicht mit dem älteren Produkt Digital Publishing Suite verwechseln, können Sie sich hier bei Digital Publishing Suite anmelden:

[https://digitalpublishing.acrobat.com/de/welcome.html](https://digitalpublishing.acrobat.com/de/welcome.html)

### Initiieren von DSGVO-Anfragen {#initiating-a-gdpr-request}

Wenden Sie sich an den Adobe-Kundendienst, um eine DSGVO-Anfrage zu Digital Publishing Suite zu initiieren.

Die folgenden IDs sind erforderlich, um nach Kundendaten zu suchen. Etwaig erhaltene Untergruppen implizieren, dass die anderen IDs für diesen Benutzer nicht gültig waren.

Obligatorisch:

* Vertrags-ID des Kunden: *dpsc-contractId*

Geben Sie mindestens 1 der folgenden Punkte ein:

* Die vom Kunde bereitgestellte OAuth-ID des Endbenutzers (die ID, die im Direct-Entitlement-System des Kunden verwendet wird): *dpsc-directEntitlementId*
* Bei Windows-App-Benutzern die App Store-ID des Endbenutzers: *dpsc-windowsAppStoreId*
* Die E-Mail-Adresse, die der Endbenutzer für die Interaktion mit der DPS-App verwendet hat: *email*

### Häufig gestellte Fragen (FAQ) {#frequently-asked-questions-faq}

**Löscht Adobe meine App Store-Käufe bei der Initiierung einer LÖSCHANFRAGE?**

Adobe löscht vorhandene Informationen zu App Store-Käufen (Abonnements usw.), doch die Käufe sind nach wie vor in den App Stores verzeichnet. Wenn die App (der Endbenutzer) im App Store angemeldet ist, werden diese Kaufbelege wieder aufgenommen und anschließend an Adobe geschickt. Diese werden dann als neue Käufe betrachtet und von der App wiederhergestellt, um wieder Zugriff zu erlangen.

**Löscht die Adobe die vom Kunden angegebenen Berechtigungen, wenn eine DELETE-Anforderung initiiert wird?**

Adobe löscht Informationen, die Adobe zu zusätzlichen direkten Berechtigungsgenehmigungen von Kunden vorliegen. Wenn sich die App (der Endbenutzer) beim OAuth-Mechanismus anmeldet, den der Kunde genutzt hat, sendet sie (er) Informationen an Adobe. Die Services greifen dabei die zusätzlichen Berechtigungen erneut auf.

**Was ist vom Endbenutzer zu erwarten?**

Da der Schlüssel für die Zuweisung von Berechtigungen zur App sich auf dem Gerät als Teil der Viewer-Software befindet, sollte der Endbenutzer die App deinstallieren. Der Endbenutzer sollte wissen, dass bei einer Deinstallation der App vorhandene (mit dem App Store-Benutzer verknüpfte) Käufe und direkte (mit dem OAuth-Benutzer des Kunden verknüpfte) Berechtigungsgenehmigungen dennoch wiederhergestellt werden.

**Was passiert, wenn eine App auf einem Gerät für andere freigegeben wird?**

Adobe verfügt nur über sehr wenige Informationen, die direkt mit einem bestimmten Benutzer verknüpft sind. Das Unternehmen verknüpft die Daten mithilfe einer zufällig erstellten UUID, die in den Daten der App gespeichert ist und bei jeder App-Anfrage übergeben wird. Das bedeutet, dass die Endbenutzer, die die App auf demselben Gerät gemeinsam nutzen, dieselbe UUID verwenden, und dass alle Daten als Daten der Person betrachtet werden, die die DSGVO-Anfrage stellt. Sowohl bei Zugriffs- als auch Löschanfragen sieht DPSC Personen, die eine App gemeinsam nutzen, als eine einzige Person an.

**Welche personenbezogenen Daten werden mit Analytics verfolgt?**

Kein. Es werden Daten zurückverfolgt. Dabei handelt es sich jedoch um Daten auf App-Ebene (und nicht um personenbezogene Daten). Hierzu gehören Ereignisse wie Starts, Abstürze, Schließvorgänge, Aktivitäten, Käufe oder Folio-Überlagerungen. Geografische Orte, Namen, Geräte-IDs oder IP-Adressen werden nicht zurückverfolgt.

**Der Endbenutzer hat Informationen bereitgestellt, es wurde jedoch nichts gefunden. Warum nicht?**

Während der Weiterentwicklung von Digital Publishing Suite wurden Veränderungen an Dienstimplementierungen vorgenommen und mehr und mehr Daten wurden verschleiert. Wenn keine Daten anhand der vom Benutzer bereitgestellten Daten gefunden wurden, können die Daten des Benutzers nicht zu diesem zurückverfolgt werden.

### Beispiel {#example}

Wenden Sie sich an den Adobe-Kundendienst, um eine DSGVO-Anfrage zu initiieren.

Hier finden Sie ein Beispiel der Eingaben und der sich daraus ergebenden Ausgaben einer DSGVO-Anfrage über Digital Publishing Suite:

#### Eingaben: {#inputs}

```
dpsc-contractId = “12345-1234-12416234” 
directEntitlementId = “1234-1234-1234” 
windowsAppStoreId = “testWinAppStoreId” 
email = “test@what.com”
```

#### Ausgaben:{#outputs}

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

