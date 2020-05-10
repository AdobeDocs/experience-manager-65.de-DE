---
title: Use Connected Assets to share DAM assets in [!DNL Adobe Experience Manager Sites] authoring workflow.
description: Verwenden Sie Assets, die in einer [!DNL Adobe Experience Manager Assets] deployment when creating your web pages on another [!DNL Adobe Experience Manager Sites] Remote-Bereitstellung verfügbar sind.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5f3af7041029a1b4dd1cbb4c65bd488b62c7e10c
workflow-type: tm+mt
source-wordcount: '2081'
ht-degree: 48%

---


# Verwenden von Connected Assets zum Freigeben von DAM-Assets in [!DNL Experience Manager Sites] {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In großen Unternehmen ist die zur Erstellung von Websites erforderliche Infrastruktur möglicherwiese verteilt. Manchmal befinden sich die Funktionen und digitale Assets zum Erstellen von Webseiten in verschiedenen Bereitstellungen. Ein Grund dafür kann die räumlich verteilte Verteilung vorhandener Implementierungen sein, die für eine gleichzeitige Arbeit erforderlich sind. Ein weiterer Grund kann Akquisitionen sein, die zu einer heterogenen Infrastruktur führen, die die übergeordnete Firma gemeinsam nutzen möchte.

Benutzer können Webseiten in erstellen [!DNL Experience Manager Sites]. [!DNL Experience Manager Assets] ist das DAM-System (Digital Asset Management), das die erforderlichen Assets für Websites bereitstellt. [!DNL Experience Manager] unterstützt nun den oben genannten Anwendungsfall durch Integration [!DNL Sites] und [!DNL Assets].

## Übersicht über Connected Assets {#overview-of-connected-assets}

When editing pages in [!UICONTROL Page Editor], the authors can seamlessly search, browse, and embed assets from a different [!DNL Assets] deployment. Die Administratoren erstellen eine einmalige Integration einer Bereitstellung von [!DNL Sites] mit einer anderen (Remote-) Bereitstellung von [!DNL Assets].

For the [!DNL Sites] authors, the remote assets are available as read-only local assets. Die Funktion unterstützt die nahtlose Suche und die gleichzeitige Verwendung einiger weniger Remote-Assets. To make many remote assets available on a [!DNL Sites] deployment in one-go, consider migrating the assets in bulk. Siehe Migrationshandbuch für [Experience Manager Assets](/help/assets/assets-migration-guide.md).

### Voraussetzungen und unterstützte Bereitstellungen {#prerequisites}

Bevor Sie diese Funktion verwenden oder konfigurieren, stellen Sie Folgendes sicher:

* Die Benutzer sind Teil von entsprechenden Benutzergruppen für jede Bereitstellung.
* Bei Bereitstellungstypen von Adobe Experience Manager ist eines der unterstützten Kriterien erfüllt. [!DNL Experience Manager] 6.5 [!DNL Assets] funktioniert [!DNL Experience Manager] als Cloud-Dienst. Weitere Informationen finden Sie unter [Funktionen für verbundene Assets in Experience Manager als Cloud-Dienst](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html).

   |  | [!DNL Sites] als Cloud-Dienst | [!DNL Experience Manager] 6.5 [!DNL Sites] zu AMS | [!DNL Experience Manager] 6.5 [!DNL Sites] Vor Ort |
   |---|---|---|---|
   | **[!DNL Experience Manager Assets]als Cloud-Dienst ** | Unterstützt | Unterstützt | Unterstützt |
   | **[!DNL Experience Manager]6.5[!DNL Assets]zu AMS ** | Unterstützt | Unterstützt | Unterstützt |
   | **[!DNL Experience Manager]6.5[!DNL Assets]Vor Ort ** | Nicht unterstützt | Nicht unterstützt | Nicht unterstützt |

### Unterstützte Dateiformate {#mimetypes}

Autoren können in Content Finder nach Bildern und den folgenden Dokumenten suchen und die gesuchten Assets im Seiten-Editor verwenden. Dokumente können zur `Download`-Komponente und Bilder zur `Image`-Komponente hinzugefügt werden. Authors can also add the remote assets in any custom [!DNL Experience Manager] component that extends the default `Download` or `Image` components. Folgende Formate werden unterstützt:

* **Bildformate**: Die Formate, die von der [Image-Komponente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/image.html) unterstützt werden. [!DNL Dynamic Media] Bilder werden nicht unterstützt.
* **Dokument-Formate**: Weitere Informationen finden Sie [in den von Connected Assets](assets-formats.md#supported-document-formats)unterstützten Videoformaten.

### Beteiligte Benutzer und Gruppen {#users-and-groups-involved}

Nachfolgend erfahren Sie mehr über die verschiedenen Rollen, die am Konfigurieren und Verwenden der Funktionen und entsprechenden Benutzergruppen beteiligt sind. Der lokale Bereich wird für den Anwendungsfall verwendet, in dem ein Autor eine Webseite erstellt. Der Remote-Umfang wird für die DAM-Bereitstellung verwendet, die die erforderlichen Assets hostet. The [!DNL Sites] author fetches these remote assets.

| Rolle | Anwendungsbereich | Benutzergruppe | Benutzername im Beispiel | Anforderung |
|---|---|---|---|---|
| [!DNL Sites] administrator | Lokal | [!DNL Experience Manager] `administrators` | `admin` | Set up [!DNL Experience Manager] and configure integration with the remote [!DNL Assets] deployment. |
| DAM-Benutzer | Lokal | `Authors` | `ksaner` | Wird zum Anzeigen und Duplizieren der abgerufenen Assets unter `/content/DAM/connectedassets/` verwendet. |
| [!DNL Sites] author | Lokal | `Authors` (mit Lesezugriff auf den Remote-DAM und Zugriff des Autors auf lokale [!DNL Sites]) | `ksaner` | End user are [!DNL Sites] authors who use this integration to improve their content velocity. The authors search and browse assets in remote DAM using [!UICONTROL Content Finder] and using the required images in local web pages. Die Anmeldeinformationen des DAM-Benutzers `ksaner` werden verwendet. |
| [!DNL Assets] administrator | Remote | [!DNL Experience Manager] `administrators` | `admin` on remote [!DNL Experience Manager] | Cross-Origin Resource Sharing (CORS) konfigurieren. |
| DAM-Benutzer | Remote | `Authors` | `ksaner` on remote [!DNL Experience Manager] | Author role on the remote [!DNL Experience Manager] deployment. Search and browse assets in Connected Assets using the [!UICONTROL Content Finder]. |
| DAM-Distributor (technischer Benutzer) | Remote | [!DNL Sites] `Authors` | `ksaner` on remote [!DNL Experience Manager] | This user present on the remote deployment is used by [!DNL Experience Manager] local server (not the [!DNL Sites] author role) to fetch the remote assets, on behalf of [!DNL Sites] author. Diese Rolle unterscheidet sich von den beiden oben aufgeführten `ksaner`-Rollen und gehört einer anderen Benutzergruppe an. |

## Configure a connection between [!DNL Sites] and [!DNL Assets] deployments {#configure-a-connection-between-sites-and-assets-deployments}

An [!DNL Experience Manager] administrator can create this integration. Once created, the permissions required to use it are established via user groups that are defined on the [!DNL Sites] deployment and on the DAM deployment.

To configure Connected Assets and local [!DNL Sites] connectivity, follow these steps.

1. Access an existing [!DNL Sites] deployment or create a deployment using the following command:

   1. In the folder of the JAR file, execute the following command on a terminal to create each [!DNL Experience Manager] server.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. After a few minutes, the [!DNL Experience Manager] server starts successfully. Consider this [!DNL Sites] deployment as the local machine for web page authoring, say at `https://[local_sites]:4502`.

1. Ensure that the users and roles with local scope exist on the [!DNL Sites] deployment and on the [!DNL Assets] deployment on AMS. Create a technical user on [!DNL Assets] deployment and add to the user group mentioned in [users and groups involved](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Zugriff auf die lokale [!DNL Sites] Bereitstellung unter `https://[local_sites]:4502`. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Connected Assets-Konfiguration]** und geben Sie die folgenden Werte ein:

   1. [!DNL Assets] ist `https://[assets_servername_ams]:[port]`.
   1. Anmeldeinformationen eines DAM-Distributors (technischer Benutzer).
   1. In **[!UICONTROL Mount Point]** field, enter the local [!DNL Experience Manager] path where [!DNL Experience Manager] fetches the assets. Beispielsweise den Ordner `remoteassets`.
   1. Passen Sie die Werte für den **[!UICONTROL Schwellenwert zum Optimieren der ursprünglichen Binärübertragung]** an Ihr Netzwerk an. Ein Asset-Wiedergabeformat, dessen Größe diesen Schwellenwert überschreitet, wird asynchron übertragen.
   1. Select **[!UICONTROL Datastore Shared with Connected Assets]**, if you use a datastore to store your assets and the Datastore is the common storage between both deployments. In diesem Fall spielt die Schwellenwertbegrenzung keine Rolle, da sich die tatsächlichen Asset-Binärdateien im Datenspeicher befinden und nicht übertragen werden.
      ![Eine typische Konfiguration für Connected Assets](assets/connected-assets-typical-config.png)
   *Abbildung: Eine typische Konfiguration für Connected Assets.*

1. Da die Assets bereits verarbeitet und die Ausgabeformate abgerufen wurden, deaktivieren Sie die Workflow-Starter. Adjust the launcher configurations on the local ([!DNL Sites]) deployment to exclude the `connectedassets` folder, in which the remote assets are fetched.

   1. On [!DNL Sites] deployment, click **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.

   1. Suchen Sie nach Startern mit Workflows wie **[!UICONTROL DAM-Update-Asset]** und **[!UICONTROL DAM-Metadaten-Writeback]**.

   1. Wählen Sie den Workflow-Starter aus und klicken Sie in der Aktionsleiste auf **[!UICONTROL Eigenschaften]**.

   1. In the [!UICONTROL Properties] wizard, change the **[!UICONTROL Path]** fields as the following mappings to update their regular expressions to exclude the mount point **[!UICONTROL connectedassets]**.
   | Vorher | Nachher |
   |---|---|
   | `/content/dam(/((?!/subassets).)*/)renditions/original` | `/content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/*/)renditions/original` | `/content/dam(/((?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/*)/jcr:content/metadata` | `/content/dam(/((?!connectedassets).)*/)jcr:content/metadata` |

   >[!NOTE]
   >
   >Alle in der Remote-Bereitstellung verfügbaren Darstellungen werden abgerufen, wenn Autoren ein Asset abrufen. Überspringen Sie diesen Konfigurationsschritt, wenn Sie mehr Wiedergabedarstellungen eines abgerufenen Assets erstellen möchten. The [!UICONTROL DAM Update Asset] workflow gets triggered and creates more renditions. These renditions are available only on the local [!DNL Sites] deployment and not on the remote DAM deployment.

1. Add the [!DNL Sites] instance as one of the **[!UICONTROL Allowed Origins]** on the remote [!DNL Assets'] CORS configuration.

   1. Melden Sie sich mit den Anmeldeinformationen des Administrators an. Suchen nach `Cross-Origin`. Öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.

   1. To create a CORS configuration for [!DNL Sites] instance, click ![aem_assets_add_icon](assets/aem_assets_add_icon.png) icon next to **[!UICONTROL Adobe Granite Cross-Origin Resource Sharing Policy]**.

   1. In the field **[!UICONTROL Allowed Origins]**, input the URL of the local [!DNL Sites], that is, `https://[local_sites]:[port]`. Speichern Sie die Konfiguration.

## Verwenden von Remote-Assets   {#use-remote-assets}

Die Website-Autoren verwenden Content Finder zum Verbinden mit der DAM-Instanz. Die Autoren können die Remote-Assets durchsuchen und in eine Komponente ziehen. Halten Sie zum Authentifizieren beim Remote-DAM die von Ihrem Administrator bereitgestellten Anmeldeinformationen des DAM-Benutzers bereit.

Autoren können die auf den lokalen DAM- und Remote-DAM-Instanzen verfügbaren Assets auf einer einzigen Webseite verwenden. Verwenden Sie Content Finder, um zwischen der Suche im lokalen und im Remote-DAM zu wechseln.

Only those tags of remote assets are fetched that have an exact corresponding tag along with the same taxonomy hierarchy, available on the local [!DNL Sites] instance. Alle anderen Tags werden verworfen. Authors can search for remote assets using all the tags present on the remote [!DNL Experience Manager] deployment, as it offers a full-text search.

### Beispiel für die Verwendung {#walk-through-of-usage}

Verwenden Sie die oben beschriebenen Einstellungen, um die Funktionsweise der Funktionen im Authoring-Erlebnis zu überprüfen. Verwenden Sie Dokumente oder Bilder Ihrer Wahl in der Remote-DAM-Bereitstellung.

1. Navigate to the [!DNL Assets] interface on the remote deployment by accessing **[!UICONTROL Assets]** > **[!UICONTROL Files]** from [!DNL Experience Manager] workspace. Sie können `https://[assets_servername_ams]:[port]/assets.html/content/dam` auch in einem Browser aufrufen. Laden Sie die Assets Ihrer Wahl hoch.
1. On the [!DNL Sites] instance, in the profile activator in the upper-right corner, click **[!UICONTROL Impersonate as]**. Geben Sie `ksaner` als Benutzernamen ein, wählen Sie die bereitgestellte Option und klicken Sie auf **[!UICONTROL OK]**.
1. Öffnen Sie eine We.Retail-Webseite unter **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bearbeiten Sie die Seite. Sie können `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` auch in einem Browser aufrufen, um die Seite zu bearbeiten.

   Klicken Sie oben links auf der Seite auf **[!UICONTROL Seitliches Bedienfeld ein/aus]**.

1. Open the [!UICONTROL Assets] tab and click **[!UICONTROL Log in to Connected Assets]**.
1. Geben Sie die Benutzerdaten – `ksaner` als Benutzername und `password` als Kennwort – ein. This user has authoring permissions on both the [!DNL Experience Manager] deployments.
1. Suchen Sie nach dem Asset, das Sie dem DAM hinzugefügt haben. Die Remote-Assets werden im linken Bereich angezeigt. Filtern Sie nach Bildern oder Dokumenten und weiter nach unterstützten Dokumenttypen. Ziehen Sie die Bilder auf eine `Image`-Komponente und die Dokumente auf eine `Download`-Komponente.

   The fetched assets are read-only on the local [!DNL Sites] deployment. You can still use the options provided by your [!DNL Sites] components to edit the fetched asset. Die Bearbeitung durch Komponenten erfolgt zerstörungsfrei.

   ![Optionen zum Filtern von Dokumenttypen und Bildern bei der Suche nach Assets auf Remote-DAM](assets/filetypes_filter_connected_assets.png)

   *Abbildung: Optionen zum Filtern von Dokumenttypen und Bildern bei der Suche nach Assets auf Remote-DAM.*

1. Ein Site-Autor wird benachrichtigt, wenn ein Asset asynchron abgerufen wird und wenn eine Abruf-Aufgabe fehlschlägt. Beim oder auch nach dem Authoring können die Autoren detaillierte Informationen zu Abruf-Aufgaben und -Fehlern in der Benutzeroberfläche von [Async-Aufträgen](/help/assets/asynchronous-jobs.md) anzeigen.

   ![Benachrichtigung zum asynchronen Abrufen von Assets, die im Hintergrund ausgeführt werden.](assets/assets_async_transfer_fails.png)

   *Abbildung: Benachrichtigung zum asynchronen Abrufen von Assets, die im Hintergrund ausgeführt werden.*

1. When publishing a page, [!DNL Experience Manager] displays a complete list of assets that are used in the page. Stellen Sie sicher, dass die Remote-Assets zum Zeitpunkt der Veröffentlichung erfolgreich abgerufen wurden. Informationen zum Überprüfen des Status der einzelnen abgerufenen Assets finden Sie in der Benutzeroberfläche für [Async-Aufträge](/help/assets/asynchronous-jobs.md).

   >[!NOTE]
   >
   >Auch wenn ein oder mehrere Remote-Assets nicht abgerufen wurden, wird die Seite veröffentlicht. Die Komponente, die das Remote-Asset verwendet, wird leer veröffentlicht. The [!DNL Experience Manager] notification area displays a notification for errors that show in async jobs page.

>[!CAUTION]
>
>Sobald die abgerufenen Remote-Assets in einer Web-Seite verwendet werden, können sie von allen Benutzern durchsucht und verwendet werden, die über die Zugriffsberechtigung für den lokalen Ordner verfügen, in dem die abgerufenen Assets gespeichert sind (im obigen Beispiel `connectedassets`). Die Assets sind außerdem über [!UICONTROL Content Finder] durchsuchbar und im lokalen Repository sichtbar.

Die abgerufenen Assets können wie jedes andere lokale Element verwendet werden. Nur die zugehörigen Metadaten können nicht bearbeitet werden.

## Beschränkungen {#limitations}

### Berechtigungen und Verwalten von Assets {#permissions-and-managing-assets}

* Lokale Assets werden nicht mit den ursprünglichen Assets auf der Remote-Bereitstellung synchronisiert. Das Ändern, Löschen oder Widerrufen von Berechtigungen auf der DAM-Bereitstellung wird nicht auf absteigende Hierarchien angewendet.
* Lokale Assets sind schreibgeschützte Kopien. [!DNL Experience Manager] Komponenten führen zerstörungsfreie Bearbeitungen an Assets durch. Sonstige Änderungen sind nicht zulässig.
* Lokal abgerufene Assets sind nur für Autoren verfügbar. Asset-Update-Workflows können nicht angewendet werden und Metadaten können nicht bearbeitet werden.
* Es werden nur Bilder und die aufgelisteten Dokumentenformate unterstützt. [!DNL Dynamic Media] Assets, Inhaltsfragmente und Erlebnisfragmente werden nicht unterstützt.
* Metadatenschemata werden nicht abgerufen.
* All [!DNL Sites] authors have read permissions on the fetched copies, even if authors do not have access to the remote DAM deployment.
* Keine API-Unterstützung, um die Integration anzupassen.
* Die Funktion unterstützt die nahtlose Suche und Verwendung von Remote-Assets. Wenn Sie viele Remote-Assets auf einmal für die lokale Bereitstellung verfügbar machen möchten, sollten Sie die Assets migrieren. Weitere Informationen finden Sie im [Handbuch zur Assets-Migration](assets-migration-guide.md).
* Es ist nicht möglich, ein Remote-Asset als Seitenminiaturansicht in der Benutzeroberfläche der [!UICONTROL Seiteneigenschaften] zu verwenden. Sie können eine Miniaturansicht einer Webseite in der Benutzeroberfläche &quot; [!UICONTROL Seiteneigenschaften] &quot;in der [!UICONTROL Miniaturansicht] festlegen, indem Sie auf Bild [!UICONTROL auswählen]klicken.

### Einrichten und Lizenzieren {#setup-licensing}

* [!DNL Assets] Bereitstellung auf [!DNL Adobe Managed Services] wird unterstützt.
* [!DNL Sites] kann eine Verbindung zu einem einzelnen [!DNL Assets] Repository herstellen.
* A license of [!DNL Assets] working as remote repository.
* One or more licenses of [!DNL Sites] working as local authoring deployment.

### Nutzung {#usage}

* Die einzige unterstützte Funktionalität ist die Suche nach Remote-Assets und das Ziehen der Remote-Assets auf der lokalen Seite, um Inhalte zu erstellen.
* Nach 5 Sekunden tritt bei Abrufvorgängen ein Timeout auf. Autoren können beispielsweise bei Netzwerkproblemen Probleme beim Abrufen von Assets haben. Authors can reattempt by dragging the remote asset from [!UICONTROL Content Finder] to [!UICONTROL Page Editor].
* Einfache, zerstörungsfreie Änderungen sowie Änderungen, die von der -`Image`-Komponente unterstützt werden, können an abgerufenen Assets vorgenommen werden. Assets sind schreibgeschützt.

## Fehlerbehebung bei Problemen   {#troubleshoot}

Führen Sie die folgenden Schritte aus, um häufige Fehler zu beheben:

* If you cannot search for remote assets from the [!UICONTROL Content Finder] then ensure that the required roles and permissions are in place.
* Ein aus dem Remote-Damm abgerufenes Asset kann aus einem oder mehreren Gründen nicht auf einer Webseite veröffentlicht werden. Es existiert nicht auf einem Remote-Server, es fehlen entsprechende Berechtigungen zum Abrufen oder ein Netzwerkfehler kann die Ursache sein. Stellen Sie sicher, dass das Asset nicht aus dem Remote-DAM entfernt wird. Stellen Sie sicher, dass entsprechende Berechtigungen vorhanden sind und die Voraussetzungen erfüllt sind. Wiederholen Sie den Vorgang zum Hinzufügen des Assets zur Seite und veröffentlichen Sie es erneut. Überprüfen Sie die [Liste asynchroner Aufträge](/help/assets/asynchronous-jobs.md) auf Fehler beim Abrufen von Assets.
