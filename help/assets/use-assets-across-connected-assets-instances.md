---
title: Verwenden von verknüpften Assets, um DAM-Assets im Authoring-Arbeitsablauf für Adobe Experience Manager-Sites freizugeben
description: Verwenden Sie beim Erstellen Ihrer Webseiten in einer anderen Experience Manager-Site-Bereitstellung verfügbare Elemente in einer Remote-Bereitstellung der Adobe Experience Manager-Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a107f3d3f10e2f5b5aed7722aee467a838f9d13d

---


# Verwenden von Connected Assets zum Freigeben von DAM-Assets in AEM Sites {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In großen Unternehmen ist die zur Erstellung von Websites erforderliche Infrastruktur möglicherwiese verteilt. Manchmal befinden sich die Funktionen und digitale Assets zum Erstellen von Webseiten in verschiedenen Bereitstellungen. Häufig sind geografisch verteilte Bereitstellungen zur Zusammenarbeit erforderlich oder Akquisitionen führen zu einer heterogenen Infrastruktur, die das übergeordnete Unternehmen konsolidieren möchte. Aber häufig führt auch Wachstum dazu, dass eine eigene Instanz für das Asset-Management erforderlich wird.

AEM Sites bietet Funktionen zum Erstellen von Webseiten, während AEM Assets das Digital Asset Management (DAM)-System ist, das die für Websites erforderlichen Assets bereitstellt. AEM unterstützt nun dank Integration von AEM Sites und AEM Assets das obige Nutzungsszenario.

## Übersicht über Connected Assets {#overview-of-connected-assets}

Beim Bearbeiten von Seiten im Seiten-Editor können die Autoren Assets aus einer anderen AEM Assets-Bereitstellung durchsuchen und einbetten. Zur Erstellung eines AEM-Administrators führen Sie eine einmalige Integration einer lokalen AEM Sites-Bereitstellung mit einer anderen (Remote-)Bereitstellung von AEM Assets durch.

Für Sites-Autoren stehen die Remote-Assets als schreibgeschützte lokale Assets zur Verfügung. Die Funktion unterstützt die nahtlose Suche und die gleichzeitige Verwendung einiger weniger Remote-Assets. Wenn Sie viele Remote-Assets auf einmal für die lokale Bereitstellung verfügbar machen möchten, sollten Sie die Assets als Stapel migrieren. Weitere Informationen finden Sie im [Handbuch zur Assets-Migration](/help/assets/assets-migration-guide.md).

### Voraussetzungen und unterstützte Bereitstellungen {#prerequisites}

Bevor Sie diese Funktion verwenden oder konfigurieren, stellen Sie Folgendes sicher:

* Die Benutzer sind Teil von entsprechenden Benutzergruppen für jede Bereitstellung.
* Bei Bereitstellungstypen von Adobe Experience Manager ist eines der unterstützten Kriterien erfüllt. AEM 6.5 Assets funktioniert mit AEM als Cloud-Dienst. Weitere Informationen finden Sie unter [Funktionen für verbundene Assets in AEM als Cloud-Dienst](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html).

   |  | AEM-Sites als Cloud-Dienst | AEM 6.5-Sites auf AMS | AEM 6.5-Sites vor Ort |
   |---|---|---|---|
   | **AEM Assets als Cloud-Dienst** | Unterstützt | Unterstützt | Unterstützt |
   | **AEM 6.5 Assets auf AMS** | Nicht unterstützt | Unterstützt | Unterstützt |
   | **AEM 6.5 Assets lokal** | Nicht unterstützt | Nicht unterstützt | Nicht unterstützt |

### Unterstützte Dateiformate {#mimetypes}

Autoren können in der Inhaltssuche nach Bildern und den folgenden Dokumenttypen suchen und die gesuchten Assets im Seiteneditor verwenden. Documents can be added to the `Download` component and images can be added to the `Image` component. Authors can also add the remote assets in any custom AEM component that extends the default `Download` or `Image` components.

* Microsoft Word (DOC und DOCX)
* Microsoft Excel (XLS und XLSX)
* Microsoft PowerPoint (PPT und PPTX)
* Adobe PDF (PDF)
* OpenDocument Text (ODT)
* Rich Text Format (RTF)
* Nur Text (TXT)
* Webseiten (HTML)

### Beteiligte Benutzer und Gruppen {#users-and-groups-involved}

Nachfolgend erfahren Sie mehr über die verschiedenen Rollen, die am Konfigurieren und Verwenden der Funktionen und entsprechenden Benutzergruppen beteiligt sind. Im Anwendungsbeispiel wird eine Website von einem Autor im lokalen Umfang erstellt. Der Remote-Bereich wird für die DAM-Bereitstellung verwendet, bei der die erforderlichen Assets gehostet werden. Der Sites-Autor ruft diese Remote-Assets ab.

| Rolle | Anwendungsbereich | Benutzergruppe | Benutzername im Verlauf | Anforderung |
|----------------------------------|--------|------------------------------------------------------------------------------|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AEM Sites-Administrator | Lokal | AEM-Administrator | `admin` | Einrichten von AEM, Konfigurieren der Integration mit der Assets-Remote-Bereitstellung. |
| DAM-Benutzer | Lokal | Autor | `ksaner` | Used to view and duplicate the fetched assets at `/content/DAM/connectedassets/`. |
| AEM Sites-Autor | Lokal | Autor (mit Lesezugriff auf das Remote-DAM und Autorenzugriff auf lokale Sites) | `ksaner` | Endbenutzer sind Sites-Autoren, die diese Integration für die Beschleunigung ihrer Inhalte verwenden. Die Autoren suchen und durchsuchen Assets in Remote DAM mit der Inhaltssuche und verwenden die erforderlichen Bilder auf lokalen Webseiten. The credentials of `ksaner` DAM user are used. |
| AEM Assets-Administrator | Remote | AEM-Administrator | `admin` auf Remote AEM | Cross-Origin Resource Sharing (CORS) konfigurieren. |
| DAM-Benutzer | Remote | Autor | `ksaner` auf Remote AEM | Autorenrolle in der Remote-AEM-Bereitstellung. Suchen und Durchsuchen von Assets in Connected Assets mit dem Content Finder. |
| DAM-Distributor (technischer Benutzer) | Remote | Paketersteller und Site-Autoren | `ksaner` auf Remote AEM | Dieser Benutzer in der Remote-Bereitstellung wird vom lokalen AEM-Server (nicht vom Site-Autor) zum Abrufen der Remote-Assets im Auftrag des Site-Autors verwendet. Diese Rolle unterscheidet sich von den beiden oben aufgeführten `ksaner`-Rollen und gehört einer anderen Benutzergruppe an. |

## Konfigurieren einer Verbindung zwischen Sites- und Assets-Bereitstellungen {#configure-a-connection-between-sites-and-assets-deployments}

Ein AEM-Administrator kann diese Integration erstellen. Nach der Erstellung werden die erforderlichen Berechtigungen mithilfe von Benutzergruppen gewährt, die für die Site-Bereitstellung und die DAM-Bereitstellung definiert werden.

Gehen Sie wie folgt vor, um die Verbindung zwischen verbundenen Assets und lokalen Sites zu konfigurieren.

1. Greifen Sie mithilfe des folgenden Befehls auf eine vorhandene AEM Sites-Bereitstellung zu oder erstellen Sie eine Bereitstellung:

   1. Führen Sie im Ordner der JAR-Datei den folgenden Befehl auf einem Terminal aus, um die einzelnen AEM-Server zu erstellen.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. Nach einigen Minuten wird der AEM-Server erfolgreich gestartet. Betrachten Sie diese AEM Sites-Bereitstellung als lokale Maschine zum Erstellen von Webseiten, z. B. `https://[local_sites]:4502`.

1. Stellen Sie sicher, dass die Benutzer und Rollen im lokalen Bereich der AEM Sites-Bereitstellung und in der AEM Assets-Bereitstellung auf AMS vorhanden sind. Create a technical user on Assets deployment and add to the user group mentioned in [users and groups involved](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Access the local AEM Sites deployment at `https://[local_sites]:4502`. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Connected Assets-Konfiguration]** und geben Sie die folgenden Werte ein:

   1. AEM Assets-Speicherort ist `https://[assets_servername_ams]:[port]`.
   1. Anmeldeinformationen eines DAM-Distributors (technischer Benutzer).
   1. Geben Sie im Feld **[!UICONTROL Bereitstellungspunkt]** den lokalen AEM-Pfad ein, aus dem AEM die Assets abruft. For example, `remoteassets` folder.

   1. Adjust the values of **[!UICONTROL Original Binary transfer optimization Threshold]** depending on your network. Ein Asset-Wiedergabeformat, dessen Größe diesen Schwellenwert überschreitet, wird asynchron übertragen.
   1. Wählen Sie **[!UICONTROL Mit Connected Assets gemeinsam verwendeter Datenspeicher]**, wenn Sie zum Speichern Ihrer Assets einen Datenspeicher verwenden und der Datenspeicher der gemeinsam verwendete Speicher beider AEM-Bereitstellungen ist. In diesem Fall spielt die Schwellenwertbegrenzung keine Rolle, da sich die tatsächlichen Asset-Binärdateien im Datenspeicher befinden und nicht übertragen werden.
   ![Eine typische Konfiguration für Connected Assets](assets/connected-assets-typical-config.png)

   *Abbildung: Eine typische Konfiguration für verbundene Assets*

1. Da die Assets bereits verarbeitet und die Wiedergabeformate abgerufen wurden, deaktivieren Sie die Workflow-Launcher. Passen Sie die Launcher-Konfigurationen in der lokalen (AEM Sites-)Bereitstellung an, um den Ordner `connectedassets` auszuschließen, aus dem Remote-Assets abgerufen werden.

   1. Klicken Sie in einer AEM Sites-Bereitstellung auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launcher]**.

   1. Suchen Sie nach Launchern mit Workflows wie **[!UICONTROL DAM-Update-Asset]** und **[!UICONTROL DAM-Metadaten-Writeback]**.

   1. Wählen Sie den Workflow-Launcher und klicken Sie in der Aktionsleiste auf **[!UICONTROL Eigenschaften]**. 

   1. Ändern Sie im Eigenschaften-Assistent die **[!UICONTROL Pfad]**-Felder in die folgenden Zuordnungen, um ihre regulären Ausdrücke zu aktualisieren und den Bereitstellungspunkt **[!UICONTROL connectedassets]** auszuschließen.
   | Vorher | Nachher |
   |---|---|
   | /content/dam(/((?!/subassets).)*/)renditions/original | /content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original |
   | /content/dam(/.*/)renditions/original | /content/dam(/((?!connectedassets).)*/)renditions/original |
   | /content/dam(/.*)/jcr:content/metadata | /content/dam(/((?!connectedassets).)*/)jcr:content/metadata |

   >[!NOTE]
   >
   >Alle in der Remote-AEM-Bereitstellung verfügbaren Darstellungen werden abgerufen, wenn Autoren ein Asset abrufen. Überspringen Sie diesen Konfigurationsschritt, wenn Sie mehr Wiedergabedarstellungen eines abgerufenen Assets erstellen möchten. Der Workflow „DAM-Update-Asset“ wird gestartet und es werden mehr Wiedergabedarstellungen erstellt. Diese Wiedergabedarstellungen sind nur für die lokale Sites-Bereitstellung verfügbar und nicht für die Remote-DAM-Bereitstellung.

1. Fügen Sie die AEM Sites-Instanz als **[!UICONTROL zulässigen Ursprung]** in der Remote-CORS-Konfiguration von AEM Assets hinzu.

   1. Melden Sie sich mit Administratorberechtigungen an. Suchen Sie ursprungsübergreifend. Öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.

   1. To create a CORS configuration for AEM Sites instance, click ![aem_assets_add_icon](assets/aem_assets_add_icon.png) icon next to **[!UICONTROL Adobe Granite Cross-Origin Resource Sharing Policy]**.

   1. Geben Sie im Feld für den **[!UICONTROL zulässigen Ursprung]** die URL der lokalen Sites ein, z. B. `https://[local_sites]:[port]` Speichern Sie die Konfiguration.

## Verwenden von Remote-Assets {#use-remote-assets}

Die Websiteautoren verwenden den Content Finder zum Verbinden mit der DAM-Instanz. Die Autoren können die Remote-Assets in einer Komponente suchen, suchen und ziehen. Halten Sie zum Authentifizieren beim Remote-DAM die von Ihrem Administrator bereitgestellten Anmeldeinformationen des DAM-Benutzers bereit.

Autoren können Assets verwenden, die sowohl in lokalen als auch in Remote-DAM-Instanzen in einer einzigen Webseite verfügbar sind. Verwenden Sie den Content Finder, um zwischen der Suche im lokalen und im Remote-DAM zu wechseln.

Es werden nur die Tags von Remote-Assets abgerufen, die über ein exakt entsprechendes Tag verfügen - mit derselben Taxonomie-Hierarchie -, das in der lokalen Site-Instanz verfügbar ist. Alle anderen Tags werden verworfen. Autoren können mit allen Tags in der Remote-AEM-Bereitstellung nach Remote-Assets suchen, da AEM eine Volltextsuche bietet.

### Beispiel für die Verwendung {#walk-through-of-usage}

Verwenden Sie die oben beschriebenen Einstellungen, um die Funktionsweise der Funktionen im Authoring-Erlebnis zu überprüfen. Verwenden Sie Dokumente oder Bilder Ihrer Wahl in der Remote-DAM-Bereitstellung.

1. Navigieren Sie zur Assets-Benutzeroberfläche in der Remote-Bereitstellung, indem Sie im AEM-Arbeitsbereich auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien]** zugreifen. Alternativ können Sie auch `https://[assets_servername_ams]:[port]/assets.html/content/dam` in einem Browser darauf zugreifen. Laden Sie die Assets Ihrer Wahl hoch.
1. Klicken Sie auf der Sites-Instanz in der Profilaktivierung oben rechts auf **[!UICONTROL Identität annehmen als]**. Geben Sie `ksaner` als Benutzernamen ein, wählen Sie die bereitgestellte Option und klicken Sie auf **[!UICONTROL OK]**.
1. Öffnen Sie eine We.Retail-Webseite unter **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bearbeiten Sie die Seite. Sie können auch `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` in einem Browser auf eine Seite zugreifen, um sie zu bearbeiten.

   Klicken Sie in der oberen linken Ecke der Seite auf **[!UICONTROL Seitenbedienfeld]** ein/aus.

1. Open the Assets tab and click **[!UICONTROL Log in to Connected Assets]**.
1. Provide the credentials -- `ksaner` as user name and `password` as password. Der Benutzer hat Autorenberechtigungen für beide AEM-Bereitstellungen.
1. Suchen Sie nach dem Asset, das Sie dem DAM hinzugefügt haben. Die Remote-Assets werden im linken Bereich angezeigt. Filtern Sie nach Bildern oder Dokumenten und weiter nach unterstützten Dokumenttypen. Ziehen Sie die Bilder auf eine `Image` Komponente und Dokumente auf eine `Download` Komponente.

   Die abgerufenen Assets sind in der lokalen AEM-Sites-Bereitstellung schreibgeschützt. Sie können weiterhin die Optionen verwenden, die Ihre AEM Sites-Komponenten bereitstellen, um das abgerufene Asset zu bearbeiten. Die Bearbeitung durch Komponenten erfolgt zerstörungsfrei.

   ![Optionen zum Filtern von Dokumenttypen und Bildern bei der Suche nach Assets auf Remote-DAM](assets/filetypes_filter_connected_assets.png)

   *Abbildung: Optionen zum Filtern von Dokumenttypen und Bildern bei der Suche nach Assets auf Remote-DAM*

1. Ein Site-Autor wird benachrichtigt, wenn ein Asset asynchron abgerufen wird und wenn eine Abruf-Aufgabe fehlschlägt. Beim oder auch nach dem Authoring können die Autoren detaillierte Informationen zu Abruf-Aufgaben und -Fehlern in der Benutzeroberfläche von [Async-Aufträgen](/help/assets/asynchronous-jobs.md) anzeigen.

   ![Benachrichtigung zum asynchronen Abrufen von Assets, die im Hintergrund ausgeführt werden.](assets/assets_async_transfer_fails.png)

   *Abbildung: Benachrichtigung zum asynchronen Abrufen von Assets, die im Hintergrund ausgeführt werden.*

1. Beim Veröffentlichen einer Seite zeigt AEM eine vollständige Liste der auf der Seite verwendeten Assets an. Stellen Sie sicher, dass die Remote-Assets zum Zeitpunkt der Veröffentlichung erfolgreich abgerufen wurden. Informationen zum Überprüfen des Status der einzelnen abgerufenen Assets finden Sie in der Benutzeroberfläche für [Async-Aufträge](/help/assets/asynchronous-jobs.md).

   >[!NOTE]
   >
   >Auch wenn ein oder mehrere Remote-Assets nicht abgerufen wurden, wird die Seite veröffentlicht. Die Komponente, die das Remote-Asset verwendet, wird leer veröffentlicht. Im AEM-Benachrichtigungsbereich werden Benachrichtigungen zu Fehlern angezeigt, die auf der Seite „Async-Aufträge“ angezeigt werden.

>[!CAUTION]
>
>Sobald die abgerufenen Remote-Assets in einer Webseite verwendet werden, können sie von allen Benutzern durchsucht und verwendet werden, die über die Zugriffsberechtigung für den lokalen Ordner verfügen, in dem die abgerufenen Assets gespeichert sind (im obigen Beispiel `connectedassets`). The assets are also searchable and visible in the local repository via [!UICONTROL Content Finder].

Die abgerufenen Assets können wie jedes andere lokale Element verwendet werden. Nur die zugehörigen Metadaten können nicht bearbeitet werden.

## Beschränkungen {#limitations}

**Berechtigungen und Verwalten von Assets**

* Lokale Assets werden nicht mit den ursprünglichen Assets auf der Remote-Bereitstellung synchronisiert. Das Ändern, Löschen oder Widerrufen von Berechtigungen auf der DAM-Bereitstellung wird nicht auf absteigende Hierarchien angewendet.
* Lokale Assets sind schreibgeschützte Kopien. AEM-Komponenten nehmen zerstörungsfreie Änderungen an Assets vor. Sonstige Änderungen sind nicht zulässig.
* Lokal abgerufene Assets sind nur für Autoren verfügbar. Asset-Update-Workflows können nicht angewendet werden und Metadaten können nicht bearbeitet werden.
* Es werden nur Bilder und die aufgelisteten Dokumentformate unterstützt. Dynamische Medienelemente, Inhaltsfragmente und Erlebnisfragmente werden nicht unterstützt.
* Metadatenschemata werden nicht abgerufen.
* Alle Sites-Autoren erhalten Leseberechtigungen für die abgerufenen Kopien, auch wenn sie keine Zugriffsberechtigungen für die Remote-DAM-Bereitstellung haben.
* Keine API-Unterstützung, um die Integration anzupassen.
* Die Funktion unterstützt die nahtlose Suche und Verwendung von Remote-Assets. Wenn Sie viele Remote-Assets auf einmal für die lokale Bereitstellung verfügbar machen möchten, sollten Sie die Assets migrieren. Weitere Informationen finden Sie im [Handbuch zur Assets-Migration](assets-migration-guide.md).
* Es ist nicht möglich, ein Remote-Asset als Miniaturansicht für eine Webseite auf der Registerkarte [!UICONTROL Miniaturansicht] in den [!UICONTROL Seiteneigenschaften] zu verwenden, indem Sie auf Bild [!UICONTROL auswählen]klicken.

**Einrichten und Lizenzieren**

* Die Bereitstellung von AEM Assets unter AMS wird unterstützt.
* AEM Sites kann jeweils nur eine Verbindung zu einem AEM Assets-Repository herstellen.
* Eine Lizenz von AEM Assets, die als Remote-Repository dient.
* Eine oder mehrere Lizenzen für AEM Sites, die als lokale Autorenbereitstellung dienen.

**Nutzung**

* Nur die unterstützte Funktion ist die Suche nach Remote-Assets und das Ziehen der Remote-Assets auf der lokalen Seite, um Inhalte zu erstellen.
* Nach 5 Sekunden tritt bei Abrufvorgängen ein Timeout auf. Autoren können beispielsweise bei Netzwerkproblemen Probleme beim Abrufen von Assets haben. Authors can re-attempt by dragging the remote asset from [!UICONTROL Content Finder] to [!UICONTROL Page Editor].
* Simple edits that are non-destructive and the edit supported via the AEM `Image` component, can be done on fetched assets. Assets sind schreibgeschützt.

## Fehlerbehebung bei Problemen {#troubleshoot}

Führen Sie die folgenden Schritte aus, um häufige Fehler zu beheben:

* Wenn Sie über den Content Finder nicht nach Remote-Assets suchen können, überprüfen Sie erneut, dass Sie über die erforderlichen Rollen und Berechtigungen verfügen.
* Ein Asset, das aus einem Remote-DAM abgerufen wurde, kann aus folgenden Gründen nicht auf einer Webseite veröffentlicht werden: Es ist im Remote-Speicher nicht vorhanden, es fehlen die Berechtigungen für den Abruf oder es liegt ein Netzwerkfehler vor. Vergewissern Sie sich, dass das Asset nicht aus dem Remote-DAM entfernt wird oder die Berechtigungen nicht geändert werden. sicherstellen, dass geeignete Voraussetzungen erfüllt sind; Versuchen Sie erneut, das Asset der Seite hinzuzufügen und veröffentlichen Sie es erneut. Überprüfen Sie die [Liste asynchroner Aufträge](/help/assets/asynchronous-jobs.md) auf Fehler beim Abrufen von Assets.
