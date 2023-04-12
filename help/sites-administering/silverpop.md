---
title: Integrieren mit Silverpop Engage
seo-title: Integrating with Silverpop Engage
description: Erfahren Sie, wie Sie AEM mit Silverpop Engage integrieren.
seo-description: Learn how to integrate AEM with Silverpop Engage
uuid: e17deeb6-5339-4ead-9086-cbe2167cdec6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 01029a80-f80e-450c-9c73-16d0662af26d
docset: aem65
exl-id: 6c4b8aaa-bda0-4066-a3fc-d91a5ab1621c
source-git-commit: 2981f11565db957fac323f81014af83cab2c0a12
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 41%

---

# Integrieren mit Silverpop Engage{#integrating-with-silverpop-engage}

<!-- THIS ENTIRE TOPIC APPEARS OBSOLETE BECAUSE SILVERPOP NO LONGER EXISTS AND THERE ARE NO REDIRECTS FOR THE DOWNLOAD URL BELOW THAT IS 404.
>[!NOTE]
>
>Silverpop integration is **not** available out of the box. You must download the Silverpop integration package `https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem620/product/cq-mcm-integrations-silverpop-content` from Package Share and install it on your instance. After you have installed the package, you can configure it as described in this document. -->

Durch die Integration von AEM mit Silverpop Engage können Sie in AEM erstellte E-Mails per Silverpop verwalten und senden. Darüber hinaus können Sie die Silverpop-Funktionen zur Lead-Verwaltung über AEM Forms auf AEM-Seiten verwenden.

Die Integration bietet die folgenden Funktionen:

* Die Möglichkeit, E-Mails in AEM zu erstellen und zur Verteilung in Silverpop zu veröffentlichen.
* Die Möglichkeit, die Aktion eines AEM Formulars festzulegen, um einen Silverpop-Abonnenten zu erstellen.

Nachdem Silverpop Engage konfiguriert wurde, können Sie Newsletter oder E-Mails über Silverpop Engage veröffentlichen.

## Erstellen einer Silverpop-Konfiguration {#creating-a-silverpop-configuration}

Silverpop-Konfigurationen können über **Cloud Services**, **Instrumente** oder **API-Endpunkte**. Alle Methoden werden in diesem Abschnitt beschrieben.

### Konfigurieren von Silverpop über Cloud Services {#configuring-silverpop-via-cloudservices}

So erstellen Sie eine Silverpop-Konfiguration in Cloud Services:

1. Tippen oder klicken Sie in AEM auf **Tools** > **Bereitstellung** > **Cloud-Services**. (Oder gehen Sie direkt zu `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Klicken Sie unter den Drittanbieterdiensten auf **Silverpop Engage** und dann auf **Konfigurieren**. Das Fenster für die Silverpop-Konfiguration wird geöffnet.

   >[!NOTE]
   >
   >Silverpop Engage ist nur dann als Option bei Diensten von Drittanbietern verfügbar, wenn Sie das Paket von Package Share herunterladen.

1. Geben Sie einen Titel und optional einen Namen ein und klicken Sie auf **Erstellen**. Das Konfigurationsfenster mit den **Silverpop-Einstellungen** wird geöffnet.
1. Geben Sie den Benutzernamen und das Kennwort ein und wählen Sie einen API-Endpunkt aus der Dropdown-Liste aus.
1. Klicken **Stellen Sie eine Verbindung zu Silverpop her.** Wenn Sie eine erfolgreiche Verbindung hergestellt haben, wird ein Dialogfeld angezeigt. Klicken **OK** sodass Sie das Fenster verlassen. Sie können auf Silverpop zugreifen, indem Sie auf **Wechseln zu Silverpop Engage** klicken.
1. Silverpop wurde konfiguriert. Sie können die Konfiguration bearbeiten, indem Sie auf **Bearbeiten** klicken.
1. Außerdem kann das Silverpop Engage-Framework für personalisierte Aktionen konfiguriert werden, indem Titel und Name angegeben werden (optional). Klicken Sie auf Erstellen , um das Framework für die bereits konfigurierte Silverpop-Verbindung erfolgreich zu erstellen.

   Importierte Datenerweiterungsspalten können später über die AEM-Komponente verwendet werden - **Text und Personalisierung**.

### Konfigurieren von Silverpop über Tools {#configuring-silverpop-via-tools}

So erstellen Sie eine Silverpop-Konfiguration in Tools:

1. Tippen oder klicken Sie in AEM auf **Tools** > **Bereitstellung** > **Cloud-Services**. Oder navigieren Sie über `https://<hostname>:<port>/misadmin#/etc` direkt dorthin.
1. Wählen Sie **Tools**, **Cloud Service-Konfigurationen** und dann **Silverpop Engage**.
1. Klicken Sie auf **Neu**.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

1. Im **Seite erstellen** -Fenster, geben Sie die **Titel** und optional die **Name** und klicken Sie auf **Erstellen**.
1. Geben Sie die Konfigurationsinformationen ein, wie in Schritt 4 des vorherigen Verfahrens beschrieben. Führen Sie dieses Verfahren aus, damit Sie die Konfiguration von Silverpop abschließen können.

### Hinzufügen mehrerer Konfigurationen {#adding-multiple-configurations}

So fügen Sie mehrere Konfigurationen hinzu:

1. Klicken Sie auf der Begrüßungsseite auf **Cloud Services** und klicken Sie auf **Silverpop Engage**. Klicken **Konfigurationen anzeigen** -Schaltfläche, die angezeigt wird, wenn eine oder mehrere Silverpop-Konfigurationen verfügbar sind. Alle verfügbaren Konfigurationen werden aufgelistet.
1. Klicken Sie auf **+** neben Verfügbare Konfigurationen. Er öffnet die **Erstellen von Konfigurationen** Fenster. Befolgen Sie die vorherigen Konfigurationsschritte, damit Sie eine Konfiguration erstellen können.

### Konfigurieren von API-Endpunkten für die Verbindung mit Silverpop {#configuring-api-end-points-for-connecting-to-silverpop}

Derzeit hat AEM sechs ungesicherte Endpunkte (Engage 1 - 6). Silverpop bietet nun zwei neue Endpunkte und geänderte Endpunkte für die bestehenden Endpunkte.

Gehen Sie wie folgt vor, um die API-Endpunkte zu konfigurieren:

1. Navigieren Sie zu `/libs/mcm/silverpop/components/silverpoppage/dialog/items/general/items/apiendpoint/options node` auf `https://<hostname>:<port>/crxde.`
1. Klicken Sie mit der rechten Maustaste und wählen Sie **Erstellen** und dann **Knoten erstellen**.
1. Geben Sie unter **Name** den Namen `sp-e0` ein und wählen Sie unter **Typ** den Typ `cq:Widget` aus.
1. Fügen Sie dem neu hinzugefügten Knoten zwei Eigenschaften hinzu:

   1. **Name**: `text`, **Typ**: `String`, **Wert**: `Engage 0`
   1. **Name**: `value`, **Typ**: `String`, **Wert**: `https://api0.silverpop.com`

   ![chlimage_1-42](assets/chlimage_1-42.png)

   Klicken Sie auf &quot;Alle speichern&quot;.

1. Erstellen Sie einen weiteren Knoten, für den Sie unter **Name** den Namen `sp-e7` und unter **Typ** den Typ `cq:Widget` angeben.

   Fügen Sie dem neu hinzugefügten Knoten zwei Eigenschaften hinzu:

   1. **Name**: `text`, **Typ**: `String`, **Wert**: `Pilot`
   1. **Name**: `value`, **Typ**: `String`, **Wert**: `https://apipilot.silverpop.com/XMLAPI`

1. Um die vorhandenen API-Endpunkte zu ändern (Engage 1 - 6), klicken Sie auf jeden dieser Endpunkte einzeln und ersetzen Sie die Werte wie folgt:

   | **Knotenname** | **Vorhandener Endpunktwert** | **Neuer Endpunktwert** |
   |---|---|---|
   | sp-e1 | `https://api.engage1.silverpop.com/XMLAPI` | `https://api1.silverpop.com` |
   | sp-e2 | `https://api.engage2.silverpop.com/XMLAPI` | `https://api2.silverpop.com` |
   | sp-e3 | `https://api.engage3.silverpop.com/XMLAPI` | `https://api3.silverpop.com` |
   | sp-e4 | `https://api.engage4.silverpop.com/XMLAPI` | `https://api4.silverpop.com` |
   | sp-e5 | `https://api.engage5.silverpop.com/XMLAPI` | `https://api5.silverpop.com` |
   | sp-e6 | `https://api.pilot.silverpop.com/XMLAPI` | `https://api6.silverpop.com` |

1. Klicken Sie auf **Alle speichern**. AEM ist nun bereit, über gesicherte Endpunkte eine Verbindung mit Silverpop herzustellen.

   ![chlimage_1-7](assets/chlimage_1-7.jpeg)
