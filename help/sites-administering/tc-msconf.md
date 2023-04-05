---
title: Herstellen einer Verbindung zu Microsoft&reg; Übersetzer
description: Erfahren Sie, wie Sie AEM mit Microsoft&reg verbinden. Übersetzer.
uuid: 5e3916ec-36a0-4d31-94ff-c340a462411a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: a7958411-b509-428e-bbe2-42efe8fd1add
feature: Language Copy
exl-id: ca575a30-fc3e-4f38-9aa7-dbecbc089f87
source-git-commit: 95638b6dd9527c567b38d8cd9da14633bd4142b5
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 14%

---

# Verbindung zu Microsoft® Translator herstellen{#connecting-to-microsoft-translator}

Erstellen Sie eine Konfiguration für den Microsoft® Translator-Cloud-Service, um Ihr Microsoft® Übersetzungskonto für die Übersetzung von AEM Seiteninhalten, Community-Inhalten oder Assets zu verwenden.

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsetikett | Der Anzeigename für den Übersetzungs-Service. |
| Übersetzungszuteilung | (Optional) Für nutzergenerierte Inhalte wird die Zuteilung neben übersetzten Texten angezeigt, beispielsweise `Translations by Microsoft`.. |
| Workspace-ID | (Optional) Die Kennung Ihrer benutzerdefinierten Microsoft® Translator-Engine, die verwendet werden soll. |
| Mitgliedschaftsschlüssel | Ihr Microsoft® Abonnementschlüssel für Microsoft® Translator. |

Nachdem Sie die Konfiguration erstellt haben, müssen Sie [Aktivieren](/help/sites-administering/tc-msconf.md#activating-the-translator-service-configurations).

Im folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche verwendet, um eine Microsoft® Translator-Konfiguration zu erstellen.

1. Klicken oder tippen Sie in der Leiste auf Tools > Cloud Services .
1. Wählen Sie im Bereich &quot;Microsoft® Translator&quot;die Option Konfigurationen anzeigen aus.
1. Klicken Sie auf den Link + neben Verfügbare Konfigurationen.

   ![chlimage_1-382](assets/chlimage_1-382.png)

1. Geben Sie einen Titel für Ihre Konfiguration ein. Der Titel identifiziert die Konfiguration in der Cloud Services-Konsole und in den Dropdownlisten &quot;Seiteneigenschaften&quot;. Der Standardname basiert auf dem Titel. Geben Sie optional einen Namen für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird. Verwenden Sie den Standardwert für die Eigenschaft &quot;Parent Configuration&quot;, die dem Pfad des Repository-Knotens entspricht.
1. Klicken Sie auf „Erstellen“.
1. Geben Sie im angezeigten Dialogfeld Werte für die Eigenschaften ein und klicken Sie auf &quot;OK&quot;.

## Beispiele für Microsoft® Translator-Cloud Service-Konfigurationen {#sample-microsoft-translator-cloud-service-configurations}

Die folgenden Microsoft® Translator-Cloud-Dienstkonfigurationen werden mit den Geometrixx-Beispielen installiert. Einige Beispielkonfigurationen verwenden ein Microsoft® Translation-Testkonto, das für maximal 2.000.000 kostenlose übersetzte Zeichen pro Monat sorgt.

### Testlizenz für Microsoft® Translator {#microsoft-translator-trial-license}

Bei der Konfiguration der Microsoft® Translator-Testlizenz handelt es sich um eine Beispielkonfiguration, die mit dem Geometrixx Outdoors-Beispielpaket installiert wird. Diese Konfiguration verwendet ein Microsoft® Translator-Konto mit einem kostenlosen Abonnement, das 2.000.000 übersetzten Zeichen pro Monat ermöglicht.

### Microsoft® Translator-Testlizenz - Geometrixx outdoors {#microsoft-translator-trial-license-geometrixx-outdoors}

Die Microsoft® Translator-Testlizenz - Geometrixx-Outdoors-Konfiguration ist eine Beispielkonfiguration, die mit Geometrixx Outdoors installiert wird. Diese Konfiguration verwendet dasselbe kostenlose Microsoft® Translator-Konto wie die Testlizenzkonfiguration für Microsoft® Translator. Das Konto verfügt über ein kostenloses Abonnement, mit dem pro Monat 2.000.000 Zeichen übersetzt werden können.

Diese Microsoft® Translator-Konfiguration ist für die Verwendung mit dem Inhaltstyp der Geometrixx Outdoors-Beispiel-Site optimiert.

### Aktualisieren der Testlizenzkonfiguration für Microsoft® Translator {#upgrading-the-microsoft-translator-trial-license-configuration}

Microsoft® Übersetzungs-Konfigurationsseiten bieten einen bequemen Link zur Microsoft®-Website, um ein für Produktionssysteme geeignetes Kontoabonnement zu erhalten.

1. Klicken oder tippen Sie in der Leiste auf Tools > Vorgänge > Cloud > Cloud Services .
1. Klicken oder tippen Sie im Bereich &quot;Microsoft® Translator&quot;auf Konfigurationen anzeigen und dann auf Microsoft® Translator-Testlizenz (Microsoft® Translation Configuration).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Klicken Sie auf der Konfigurationsseite auf Abonnement aktualisieren . Verwenden Sie die Microsoft®-Webseite, die geöffnet wird, um Ihr Konto zu konfigurieren.

   ![chlimage_1-384](assets/chlimage_1-384.png)

### Anpassen der Microsoft® Translator-Engine {#customizing-your-microsoft-translator-engine}

Microsoft® Übersetzungskonfigurationsseiten bieten einen bequemen Link zur Microsoft®-Website zur Anpassung Ihrer Microsoft® Translator-Engine. ([https://www.microsoft.com/en-us/research/project/microsoft-translator-hub/](https://www.microsoft.com/en-us/research/project/microsoft-translator-hub/))

1. Klicken oder tippen Sie in der Leiste auf Tools > Vorgänge > Cloud > Cloud Services .
1. Klicken oder tippen Sie im Bereich &quot;Microsoft® Translator&quot;auf Konfigurationen anzeigen und dann auf die Konfiguration, die Sie anpassen möchten.
1. Klicken Sie auf der Konfigurationsseite auf Übersetzer anpassen . Verwenden Sie die Microsoft®-Webseite, die geöffnet wird, um Ihren Dienst anzupassen.

## Aktivieren der Übersetzungs-Service-Konfigurationen {#activating-the-translator-service-configurations}

Aktivieren Sie Ihre Cloud Service-Konfigurationen, um übersetzte Inhalte zu unterstützen, die auf die Veröffentlichungsinstanz repliziert werden. Verwenden Sie zum Aktivieren der Repository-Knoten, die die Microsoft® Translator- oder Cloud Service-Konfigurationen von Drittanbietern speichern, die Methode von [Aktivieren eines vollständigen Abschnitts (Baum)](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree). Die Knoten befinden sich unter den folgenden übergeordneten Knoten:

* Microsoft® Translation Service: /libs/settings/cloudconfigs/translation/msft-translation
* Drittanbieterübersetzungen: /etc/cloudservices/machine-translation
