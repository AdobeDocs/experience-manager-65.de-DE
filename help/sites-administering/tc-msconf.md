---
title: Herstellen einer Verbindung zu Microsoft® Translator
description: Erfahren Sie, wie Sie Adobe Experience Manager mit Microsoft&reg; Translator verbinden.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: ca575a30-fc3e-4f38-9aa7-dbecbc089f87
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 98%

---

# Herstellen einer Verbindung mit Microsoft® Translator{#connecting-to-microsoft-translator}

Erstellen Sie eine Konfiguration für den Microsoft® Translator-Clouddienst, um Ihr Microsoft® Translator-Konto zum Übersetzen von AEM-Seiteninhalten, Community-Inhalten oder Assets zu nutzen.

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsetikett | Der Anzeigename für den Übersetzungs-Service. |
| Übersetzungszuteilung | (Optional) Für nutzergenerierte Inhalte wird die Zuteilung neben übersetzten Texten angezeigt, beispielsweise `Translations by Microsoft`.. |
| Arbeitsbereichs-ID | (Optional) Die ID Ihrer benutzerdefinierten Microsoft® Translator-Engine, die verwendet werden soll. |
| Abonnementschlüssel | Ihr Microsoft®-Abonnementschlüssel für Microsoft® Translator. |

Nachdem Sie die Konfiguration erstellt haben, müssen Sie sie [aktivieren](/help/sites-administering/tc-msconf.md#activating-the-translator-service-configurations).

Beim folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche verwendet, um eine Microsoft® Translator-Konfiguration zu erstellen.

1. Klicken oder tippen Sie in der Leiste auf „Tools“ > „Cloud Services“.
1. Wählen Sie danach im Bereich „Microsoft® Translator“ die Option „Konfigurationen anzeigen“ aus.
1. Klicken Sie auf den Link „+“ neben „Verfügbare Konfigurationen“.

   ![chlimage_1-382](assets/chlimage_1-382.png)

1. Geben Sie einen Titel für Ihre Konfiguration ein. Mit dem Titel wird die Konfiguration auf der Cloud Services-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert. Der Standardname basiert auf dem Titel. Geben Sie optional einen Namen für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird. Sie sollten den Standardwert für die Eigenschaft „Übergeordnete Konfiguration“ verwenden. Dies ist der Pfad des Repository-Knotens.
1. Klicken Sie auf „Erstellen“.
1. Geben Sie im angezeigten Dialogfeld die Werte für die Eigenschaften ein und klicken Sie auf „OK“.

## Beispiele für Konfigurationen des Microsoft® Translator-Clouddiensts {#sample-microsoft-translator-cloud-service-configurations}

Die folgenden Konfigurationen des Microsoft® Translator-Clouddiensts werden mit den Geometrixx-Beispielen installiert. Für einige Beispielkonfigurationen wird ein Microsoft® Translator-Testkonto verwendet, mit dem pro Monat kostenlos maximal 2 000 000 Zeichen übersetzt werden können.

### Microsoft® Translator-Testlizenz {#microsoft-translator-trial-license}

Die Konfiguration der Microsoft® Translator-Testlizenz ist eine Beispielkonfiguration, die mit dem Geometrixx Outdoors-Beispielpaket installiert wird. Bei dieser Konfiguration wird ein Microsoft® Translator-Konto mit einem kostenlosen Abonnement verwendet, mit dem pro Monat 2 000 000 Zeichen übersetzt werden können.

### Microsoft® Translator-Testlizenz – Geometrixx-outdoors {#microsoft-translator-trial-license-geometrixx-outdoors}

Die Konfiguration „Microsoft® Translator-Testlizenz – Geometrixx-outdoors“ ist eine Beispielkonfiguration, die mit Geometrixx Outdoors installiert wird. Bei dieser Konfiguration wird dasselbe kostenlose Microsoft® Translator-Konto wie für die Konfiguration „Microsoft® Translator-Testlizenz“ verwendet. Das Konto verfügt über ein kostenloses Abonnement, mit dem pro Monat 2.000.000 Zeichen übersetzt werden können.

Diese Microsoft® Translator-Konfiguration ist für die Verwendung mit dem Inhaltstyp der Beispiel-Site von Geometrixx Outdoors optimiert.

### Aktualisieren der Microsoft® Translator-Testlizenkonfiguration {#upgrading-the-microsoft-translator-trial-license-configuration}

Die Konfigurationsseiten von Microsoft® Translator enthalten einen direkten Link zur Microsoft®-Website, über die Sie ein für Produktionssysteme geeignetes Kontoabonnement erhalten können.

1. Klicken oder tippen Sie in der Leiste auf „Tools“ > „Vorgänge“ > „Cloud“ > „Cloud Services“.
1. Klicken oder tippen Sie im Bereich „Microsoft® Translator“ auf „Konfigurationen anzeigen“ und dann auf „Microsoft® Translator-Testlizenz“ (Microsoft® Translator-Konfiguration).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Klicken Sie auf der Konfigurationsseite auf „Abonnement aktualisieren“. Verwenden Sie die dadurch geöffnete Microsoft®-Web-Seite, um Ihr Konto zu konfigurieren.

   ![chlimage_1-384](assets/chlimage_1-384.png)

### Anpassen der Microsoft® Translator-Engine {#customizing-your-microsoft-translator-engine}

Die Seiten der Microsoft® Translation-Konfiguration enthalten einen direkten Link zur Microsoft®-Website, auf der die Microsoft® Translator-Engine angepasst werden kann. ([https://www.microsoft.com/de-de/research/project/microsoft-translator-hub/](https://www.microsoft.com/de-de/research/project/microsoft-translator-hub/))

1. Klicken oder tippen Sie in der Leiste auf „Tools“ > „Vorgänge“ > „Cloud“ > „Cloud Services“.
1. Klicken oder tippen Sie im Bereich „Microsoft® Translator“ auf „Konfigurationen anzeigen“ und dann auf die Konfiguration, die Sie anpassen möchten.
1. Klicken Sie auf der Konfigurationsseite auf „Translator anpassen“. Verwenden Sie die sich öffnende Microsoft®-Web-Seite, um Ihren Dienst anzupassen.

## Aktivieren der Translator-Service-Konfigurationen {#activating-the-translator-service-configurations}

Aktivieren Sie Ihre Cloud Service-Konfigurationen, um übersetzte Inhalte zu unterstützen, die auf die Publish-Instanz repliziert werden. Verwenden Sie zum Aktivieren der Repository-Knoten, die die Microsoft® Translator- oder Cloud Service-Konfigurationen von Drittanbietern speichern, die Methode [Aktivieren eines vollständigen Abschnitts (Baumstruktur)](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree). Die Knoten befinden sich unter den folgenden übergeordneten Knoten:

* Microsoft® Translation Service: /libs/settings/cloudconfigs/translation/msft-translation
* Drittanbieterübersetzungen: /etc/cloudservices/machine-translation
