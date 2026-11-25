---
title: Herstellen einer Verbindung mit Microsoft Translator
description: Erfahren Sie, wie Sie AEM sofort mit Microsoft Translator verbinden können, um Ihren Übersetzungs-Workflow zu automatisieren.
feature: Language Copy
role: Admin
exl-id: ca575a30-fc3e-4f38-9aa7-dbecbc089f87
solution: Experience Manager, Experience Manager Sites
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: d9d38edd-df1b-480c-8f5e-72b62576f390
    internal-label: Site and page features
subfeature_v2:
  - id: e15a4109-ae5d-497d-b301-31149e35aed4
    internal-label: Language Copy Wizard
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: f63514691265918da2fa40cc493889c6cd0d23d1
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 58%
---
# Herstellen einer Verbindung mit Microsoft Translator {#connecting-to-microsoft-translator}

AEM bietet einen integrierten Connector für [Microsoft Translator](https://www.microsoft.com/de-de/translator/business/) zur Übersetzung von Seiteninhalten oder Assets. Nachdem Sie eine Lizenz von Microsoft für die Verwendung von Microsoft Translator erhalten haben, konfigurieren Sie den Connector entsprechend den Anweisungen auf dieser Seite.

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsetikett | Der Anzeigename für den Übersetzungsdienst |
| Übersetzungszuteilung | (Optional) Bei nutzergenerierten Inhalten die Zuteilung, die neben übersetzten Texten angezeigt wird, beispielsweise `Translations by Microsoft` |
| Workspace-ID | (Optional) Die ID Ihrer angepassten Microsoft Translator-Engine, die verwendet werden soll |
| Mitgliedschaftsschlüssel | Ihr Microsoft-Abonnementschlüssel für Microsoft Translator |

Mit dem folgenden Verfahren wird eine Microsoft Translator-Konfiguration erstellt.

1. Klicken Sie im [Navigationsbereich](/help/sites-authoring/basic-handling.md#first-steps) auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.
1. Navigieren Sie zu dem Ort, an dem Sie die Konfiguration erstellen möchten. Normalerweise ist dies in Ihrem Site-Stammverzeichnis oder es kann eine globale Standardkonfiguration sein.
1. Klicken Sie auf die Schaltfläche **Erstellen**.
1. Legen Sie Ihre Konfiguration fest.
   1. Wählen Sie **Microsoft Translator** in der Dropdown-Liste aus.
   1. Geben Sie einen Titel für Ihre Konfiguration ein. Durch den Titel wird die Konfiguration in der Cloud Services-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert.
   1. Geben Sie optional einen Namen für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird.

   ![Erstellen einer Übersetzungskonfiguration](assets/create-translation-config.png)

1. Klicken Sie auf **Erstellen**.
1. Geben Sie im Fenster **Konfiguration bearbeiten** die in der vorherigen Tabelle beschriebenen Werte für den Übersetzungs-Service ein.

   ![Bearbeiten einer Übersetzungskonfiguration](assets/msft-config-ui.png)

1. Klicken Sie auf **Verbinden**, um die Verbindung zu überprüfen.
1. Klicken Sie auf **Speichern und schließen**.

## Veröffentlichen der Übersetzungs-Service-Konfigurationen {#publishing-the-translator-service-configurations}

Veröffentlichen Sie als letzten Schritt Ihre Microsoft Translator-Konfigurationen, um veröffentlichte übersetzte Inhalte zu unterstützen. Verwenden Sie dazu die Aktion [Veröffentlichen eines Baums](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree).

## Microsoft Translator-API-Feldzuordnung {#microsoft-translator-api-field-mapping}

Die Microsoft Translator-API v3 akzeptiert Übersetzungsanfragen unter `https://api.cognitive.microsofttranslator.com/translate?api-version=3.0`. Die erforderlichen Parameter, einschließlich [&#128279;](https://learn.microsoft.com/en-us/azure/ai-services/translator/text-translation/reference/v3/translate) Zielsprache, finden Sie in der Microsoft-Übersetzungs-API-Referenz.

Die folgende Tabelle verknüpft die AEM-Konfigurationsfelder mit der Microsoft-API.

| AEM-Feld | Zweck in AEM | Microsoft-API-Beziehung |
|---|---|---|
| Workspace-ID | Gibt die benutzerdefinierte Microsoft Translator-Engine an, die verwendet werden soll. | Benutzerdefinierte Übersetzungssysteme werden über den `category`-Anforderungsparameter ausgewählt. Die Microsoft-API erwartet eine benutzerdefinierte Übersetzerkategorie-ID, keine Workspace-ID allein. Bestätigen Sie den für Ihren Connector und die benutzerdefinierte Modellkonfiguration erforderlichen Wert. |
| Übersetzungsetikett | Stellt einen Anzeigenamen für den Übersetzungs-Service bereit. | Kein entsprechender Übersetzungsanforderungsparameter. |
| Übersetzungszuteilung | Definiert eine optionale Attribution neben übersetzten benutzergenerierten Inhalten. | Kein entsprechender Übersetzungsanforderungsparameter. |
| Mitgliedschaftsschlüssel | Authentifiziert den Zugriff auf das Microsoft Translator-Abonnement. | Wird beim Anfordern eines Zugriffs-Tokens in der `Ocp-Apim-Subscription-Key`-Kopfzeile gesendet. Das Token wird dann bei Übersetzungsanfragen in der `Authorization: Bearer <access-token>`-Kopfzeile gesendet. |

Bei einer globalen Microsoft Translator-Ressource wird der Token-Endpunkt `https://api.cognitive.microsoft.com/sts/v1.0/issueToken`. Regionale und Multi-Service-Ressourcen verwenden regionsspezifische Token-Endpunkte. Unter [Microsoft Translator-Authentifizierung](https://learn.microsoft.com/en-us/azure/ai-services/translator/text-translation/reference/authentication) finden Sie die Endpunkt- und Kopfzeilenanforderungen für Ihren Ressourcentyp.
