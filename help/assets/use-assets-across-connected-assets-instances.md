---
title: Verwenden von Connected Assets zum Freigeben von DAM-Assets in  [!DNL Sites]
description: Verwenden Sie Assets, die in einer Remote [!DNL Adobe Experience Manager Assets] deployment when creating your web pages on another [!DNL Adobe Experience Manager Sites] -Implementierung verfügbar sind.
contentOwner: AG
translation-type: tm+mt
source-git-commit: d05dc3af0a885e51758194783e773695086d7956
workflow-type: tm+mt
source-wordcount: '2263'
ht-degree: 98%

---


# Verwenden von Connected Assets zum Freigeben von DAM-Assets in [!DNL Experience Manager Sites] {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In großen Unternehmen ist die zur Erstellung von Websites erforderliche Infrastruktur möglicherwiese verteilt. Manchmal befinden sich die Funktionen und digitale Assets zum Erstellen von Web-Seiten in verschiedenen Implementierungen. Ein Grund können geografisch verteilte vorhandene Implementierungen sein, die zusammenarbeiten müssen. Ein weiterer Grund können Akquisitionen sein, die zu einer heterogenen Infrastruktur führen, die die übergeordnete Firma gemeinsam nutzen möchte.

Benutzer können Web-Seiten in [!DNL Experience Manager Sites] erstellen. [!DNL Experience Manager Assets] ist das DAM (Digital Asset Management)-System, das die erforderlichen Assets für Websites bereitstellt. [!DNL Experience Manager] unterstützt nun dank Integration von [!DNL Sites] und [!DNL Assets] das obige Nutzungsszenario.

## Überblick über Connected Assets {#overview-of-connected-assets}

Beim Bearbeiten von Seiten als Ziel im [!UICONTROL Seiteneditor] können die Autoren nahtlos Assets aus einer anderen [!DNL Assets]-Bereitstellung, die als Asset-Quelle dient, suchen, durchsuchen und einbetten. Die Administratoren erstellen eine einmalige Integration einer Bereitstellung von [!DNL Experience Manager] mit [!DNL Sites]-Funktion mit einer anderen Bereitstellung von [!DNL Experience Manager] mit [!DNL Assets]-Funktion.

Für [!DNL Sites]-Autoren stehen die Remote-Assets als schreibgeschützte lokale Assets zur Verfügung. Die Funktion unterstützt die nahtlose Suche und die gleichzeitige Verwendung einiger weniger Remote-Assets. Wenn Sie viele Remote-Assets auf einmal für die [!DNL Sites]-Implementierung verfügbar machen möchten, sollten Sie die Assets als Stapel migrieren. Siehe [Handbuch zur Migration von Experience Manager-Assets](/help/assets/assets-migration-guide.md).

### Voraussetzungen und unterstützte Implementierungen {#prerequisites}

Bevor Sie diese Funktion verwenden oder konfigurieren, stellen Sie Folgendes sicher:

* Die Benutzer sind Teil von entsprechenden Benutzergruppen für jede Implementierung.
* Bei Implementierungstypen von [!DNL Adobe Experience Manager] ist eines der unterstützten Kriterien erfüllt. [!DNL Experience Manager] 6.5  [!DNL Assets] funktioniert  [!DNL Experience Manager] als Cloud Service. Weitere Informationen zur Funktionsweise dieser Funktion in [!DNL Experience Manager as a Cloud Service] finden Sie unter [Verbundene Assets in Experience Manager als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html).

   |  | [!DNL Sites] as a Cloud Service | [!DNL Experience Manager] 6.5 [!DNL Sites] auf AMS | [!DNL Experience Manager] 6.5 [!DNL Sites] On-Premise |
   |---|---|---|---|
   | **[!DNL Experience Manager Assets]as a[!DNL Cloud Service]** | Unterstützt | Unterstützt | Unterstützt |
   | **[!DNL Experience Manager]6.5 [!DNL Assets] auf AMS** | Unterstützt | Unterstützt | Unterstützt |
   | **[!DNL Experience Manager]6.5 [!DNL Assets] On-Premise** | Nicht unterstützt | Nicht unterstützt | Nicht unterstützt |

### Unterstützte Dateiformate {#mimetypes}

Autoren können in Content Finder nach Bildern und den folgenden Dokumenten suchen und die gefundenen Assets im Seiteneditor verwenden. Dokumente werden der Komponente `Download` und Bilder der Komponente `Image` hinzugefügt. Autoren können die Remote-Assets auch zu jeder benutzerdefinierten [!DNL Experience Manager]-Komponente hinzufügen, die die standardmäßigen `Download`- oder `Image`-Komponenten erweitert. Folgende Formate werden unterstützt:

* **Bildformate**: Die Formate, die von der [Bildkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=de) unterstützt werden. [!DNL Dynamic Media]-Bilder werden nicht unterstützt.
* **Dokumentenformate**: Siehe [Unterstützte Dokumentformate](assets-formats.md#supported-document-formats).

### Beteiligte Benutzer und Gruppen {#users-and-groups-involved}

Nachfolgend erfahren Sie mehr über die verschiedenen Rollen, die am Konfigurieren und Verwenden der Funktionen und entsprechenden Benutzergruppen beteiligt sind. Der lokale Umfang wird für den Anwendungsfall verwendet, in dem ein Autor eine Web-Seite erstellt. Der Remote-Umfang wird für die DAM-Implementierung verwendet, die die erforderlichen Assets hostet. Der [!DNL Sites]-Autor ruft diese Remote-Assets ab.

| Rolle | Anwendungsbereich | Benutzergruppe | Benutzername im Beispiel | Anforderung |
|---|---|---|---|---|
| [!DNL Sites]-Administrator | Lokal | [!DNL Experience Manager] `administrators` | `admin` | Einrichten von [!DNL Experience Manager], Konfigurieren der Integration mit der Remote[!DNL Assets]-Implementierung. |
| DAM-Benutzer | Lokal | `Authors` | `ksaner` | Wird zum Anzeigen und Duplizieren der abgerufenen Assets unter `/content/DAM/connectedassets/` verwendet. |
| [!DNL Sites]-Autor | Lokal | <ul><li>`Authors` (mit Lesezugriff auf das Remote-DAM und Autorenzugriff auf lokale [!DNL Sites]) </li> <li>`dam-users` lokal  [!DNL Sites]</li></ul> | `ksaner` | Endbenutzer sind [!DNL Sites]-Autoren, die diese Integration für die Beschleunigung ihrer Inhalte verwenden. Die Autoren suchen und durchsuchen Assets im Remote-DAM mit [!UICONTROL Content Finder] und verwenden die erforderlichen Bilder auf lokalen Web-Seiten. Die Anmeldeinformationen des DAM-Benutzers `ksaner` werden verwendet. |
| [!DNL Assets]-Administrator | Remote | [!DNL Experience Manager] `administrators` | `admin` auf Remote-[!DNL Experience Manager] | Cross-Origin Resource Sharing (CORS) konfigurieren. |
| DAM-Benutzer | Remote | `Authors` | `ksaner` auf Remote-[!DNL Experience Manager] | Autorenrolle in der Remote[!DNL Experience Manager]-Implementierung. Suchen und Durchsuchen von Assets in Connected Assets mit dem [!UICONTROL Content Finder]. |
| DAM-Distributor (technischer Benutzer) | Remote | [!DNL Sites] `Authors` | `ksaner` auf Remote-[!DNL Experience Manager] | Dieser Benutzer in der Remote-Implementierung wird vom lokalen [!DNL Experience Manager]-Server (nicht vom [!DNL Sites]-Autor) zum Abrufen der Remote-Assets im Auftrag des [!DNL Sites]-Autors verwendet. Diese Rolle unterscheidet sich von den beiden oben aufgeführten `ksaner`-Rollen und gehört einer anderen Benutzergruppe an. |

## Konfigurieren einer Verbindung zwischen [!DNL Sites]- und [!DNL Assets]-Implementierungen {#configure-a-connection-between-sites-and-assets-deployments}

Ein [!DNL Experience Manager]-Administrator kann diese Integration erstellen. Nach der Erstellung werden die erforderlichen Berechtigungen über Benutzergruppen festgelegt. Die Benutzergruppen werden für die [!DNL Sites]-Implementierung und die DAM-Implementierung definiert.

Gehen Sie wie folgt vor, um die Verbindung zwischen Connected Assets und lokalen [!DNL Sites] zu konfigurieren:

1. Greifen Sie mithilfe des folgenden Befehls auf eine vorhandene [!DNL Sites]-Implementierung zu oder erstellen Sie eine Implementierung:

   1. Führen Sie im Ordner der JAR-Datei den folgenden Befehl auf einem Terminal aus, um die einzelnen [!DNL Experience Manager]-Server zu erstellen.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. Nach einigen Minuten wird der [!DNL Experience Manager]-Server erfolgreich gestartet. Betrachten Sie diese [!DNL Sites]-Implementierung als lokale Maschine zum Erstellen von Web-Seiten, z. B. `https://[local_sites]:4502`.

1. Stellen Sie sicher, dass die Benutzer und Rollen im lokalen Bereich der [!DNL Sites]-Implementierung und in der [!DNL Assets]-Implementierung auf AMS vorhanden sind. Erstellen Sie einen technischen Benutzer in der [!DNL Assets]-Implementierung und fügen Sie ihn der in [Beteiligte Benutzer und Gruppen](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved) erwähnten Benutzergruppe hinzu.

1. Greifen Sie auf die lokale [!DNL Sites]-Implementierung unter `https://[local_sites]:4502` zu. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Connected Assets-Konfiguration]** und geben Sie die folgenden Werte ein:

   1. Der Speicherort von [!DNL Assets] ist `https://[assets_servername_ams]:[port]`.
   1. Anmeldeinformationen eines DAM-Distributors (technischer Benutzer).
   1. Geben Sie im Feld **[!UICONTROL Bereitstellungspunkt]** den lokalen [!DNL Experience Manager]-Pfad ein, aus dem [!DNL Experience Manager] die Assets abruft. Beispielsweise den Ordner `remoteassets`.
   1. Passen Sie die Werte für den **[!UICONTROL Schwellenwert zum Optimieren der ursprünglichen Binärübertragung]** an Ihr Netzwerk an. Eine Asset-Ausgabedarstellung, deren Größe diesen Schwellenwert überschreitet, wird asynchron übertragen.
   1. Wählen Sie **[!UICONTROL Mit Connected Assets gemeinsam verwendeter Datenspeicher]** aus, wenn Sie zum Speichern Ihrer Assets einen Datenspeicher verwenden und der Datenspeicher der gemeinsam verwendete Speicher beider Implementierungen ist. In diesem Fall spielt die Schwellenwertbegrenzung keine Rolle, da sich die tatsächlichen Asset-Binärdateien im Datenspeicher befinden und nicht übertragen werden.

   ![Eine typische Konfiguration für Connected Assets](assets/connected-assets-typical-config.png)

   *Abbildung: Eine typische Konfiguration für Connected Assets.*

1. Da die Assets bereits verarbeitet und die Ausgabedarstellungen abgerufen wurden, deaktivieren Sie die Workflow-Starter. Passen Sie die Starterkonfigurationen in der lokalen ([!DNL Sites]-)Bereitstellung an, um den Ordner `connectedassets` auszuschließen, aus dem Remote-Assets abgerufen werden.

   1. Klicken Sie in einer [!DNL Sites]-Implementierung auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Starter]**.

   1. Suchen Sie nach Startern mit Workflows wie **[!UICONTROL DAM-Update-Asset]** und **[!UICONTROL DAM-Metadaten-Writeback]**.

   1. Wählen Sie den Workflow-Starter aus und klicken Sie in der Aktionsleiste auf **[!UICONTROL Eigenschaften]**.

   1. Ändern Sie im [!UICONTROL Eigenschaften]-Assistenten die **[!UICONTROL Pfad]**-Felder in die folgenden Zuordnungen, um ihre regulären Ausdrücke zu aktualisieren und den Bereitstellungspunkt **[!UICONTROL connectedassets]** auszuschließen.

   | Vorher | Nachher |
   |---|---|
   | `/content/dam(/((?!/subassets).)*/)renditions/original` | `/content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*/)renditions/original` | `/content/dam(/((?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*)/jcr:content/metadata` | `/content/dam(/((?!connectedassets).)*/)jcr:content/metadata` |

   >[!NOTE]
   >
   >Wenn Autoren ein Asset abrufen, werden alle in der Remote-Implementierung verfügbaren Ausgabedarstellungen abgerufen. Überspringen Sie diesen Konfigurationsschritt, wenn Sie mehr Ausgabedarstellungen eines abgerufenen Assets erstellen möchten. Der Workflow [!UICONTROL DAM-Update-Asset] wird gestartet und es werden mehr Ausgabedarstellungen erstellt. Diese Ausgabedarstellungen sind nur für die lokale [!DNL Sites]-implementierung verfügbar und nicht für die Remote-DAM-Bereitstellung.

1. Fügen Sie die [!DNL Sites]-Implemetierung als **[!UICONTROL zulässigen Ursprung]** in der Remote[!DNL Assets']-CORS-Konfiguration hinzu.

   1. Melden Sie sich mit den Anmeldeinformationen des Administrators an. Suchen Sie nach `Cross-Origin`. Öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.

   1. Klicken Sie zum Erstellen einer CORS-Konfiguration für die [!DNL Sites]-Implemetierung auf das Symbol ![_assets_add_](assets/do-not-localize/assets_add_icon.png) neben der **[!UICONTROL Adobe Granite-Richtlinie für das gemeinsame Nutzen von Ressourcen über Ursprünge hinweg]**.

   1. Geben Sie im Feld für den **[!UICONTROL zulässigen Ursprung]** die URL der lokalen [!DNL Sites] ein, z. B. `https://[local_sites]:[port]`. Speichern Sie die Konfiguration.

## Verwenden von Remote-Assets  {#use-remote-assets}

Die Website-Autoren verwenden Content Finder zum Verbinden mit der DAM-Implemetierung. Die Autoren können die Remote-Assets durchsuchen und in eine Komponente ziehen. Halten Sie zum Authentifizieren beim Remote-DAM die von Ihrem Administrator bereitgestellten Anmeldeinformationen des DAM-Benutzers bereit.

Autoren können in lokalen und Remote-DAM-Implemetierungen verfügbare Assets auf derselben Web-Seite nutzen. Verwenden Sie Content Finder, um zwischen der Suche im lokalen und im Remote-DAM zu wechseln.

Es werden nur die Tags von Remote-Assets abgerufen, die über ein exakt entsprechendes Tag – mit derselben Taxonomie-Hierarchie – verfügen, das in der lokalen [!DNL Sites]-Implemetierung verfügbar ist. Alle anderen Tags werden verworfen. Autoren können mit allen Tags in der Remote[!DNL Experience Manager]-Implementierung nach Remote-Assets suchen, da eine Volltextsuche verfügbar ist.

### Beispiel für die Verwendung {#walk-through-of-usage}

Verwenden Sie die oben beschriebenen Einstellungen, um die Funktionsweise der Funktionen im Authoring-Erlebnis zu überprüfen. Verwenden Sie Dokumente oder Bilder Ihrer Wahl in der Remote-DAM-Implemetierung.

1. Navigieren Sie zur [!DNL Assets]-Benutzeroberfläche in der Remote-Implementierung, indem Sie im [!DNL Experience Manager]-Arbeitsbereich auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien]** zugreifen. Sie können `https://[assets_servername_ams]:[port]/assets.html/content/dam` auch in einem Browser aufrufen. Laden Sie die Assets Ihrer Wahl hoch.
1. Klicken Sie in der [!DNL Sites]-Implemetierung in der Profilaktivierung oben rechts auf **[!UICONTROL Identität annehmen als]**. Geben Sie `ksaner` als Benutzernamen ein, wählen Sie die bereitgestellte Option und klicken Sie auf **[!UICONTROL OK]**.
1. Öffnen Sie eine We.Retail-Web-Seite unter **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bearbeiten Sie die Seite. Sie können `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` auch in einem Browser aufrufen, um die Seite zu bearbeiten.

   Klicken Sie oben links auf der Seite auf **[!UICONTROL Seitliches Bedienfeld ein/aus]**.

1. Öffnen Sie die Registerkarte [!UICONTROL Assets] und klicken Sie auf **[!UICONTROL Bei Connected Assets anmelden]**.
1. Geben Sie die Benutzerdaten – `ksaner` als Benutzername und `password` als Kennwort – ein. Der Benutzer hat Autorenberechtigungen für beide [!DNL Experience Manager]-Implementierungen.
1. Suchen Sie nach dem Asset, das Sie dem DAM hinzugefügt haben. Die Remote-Assets werden im linken Bereich angezeigt. Filtern Sie nach Bildern oder Dokumenten und weiter nach unterstützten Dokumenttypen. Ziehen Sie die Bilder auf eine `Image`-Komponente und die Dokumente auf eine `Download`-Komponente.

   Die abgerufenen Assets sind in der lokalen [!DNL Sites]-Implementierung schreibgeschützt. Sie können weiterhin die Optionen verwenden, die Ihre [!DNL Sites]-Komponenten bereitstellen, um das abgerufene Asset zu bearbeiten. Die Bearbeitung durch Komponenten erfolgt zerstörungsfrei.

   ![Optionen zum Filtern von Dokumenttypen und Bildern bei der Suche nach Assets auf Remote-DAM](assets/filetypes_filter_connected_assets.png)

   *Abbildung: Optionen zum Filtern von Dokumenttypen und Bildern bei der Suche nach Assets auf Remote-DAM.*

1. Ein Site-Autor wird benachrichtigt, wenn ein Asset asynchron abgerufen wird und wenn eine Abruf-Aufgabe fehlschlägt. Beim oder auch nach dem Authoring können die Autoren detaillierte Informationen zu Abruf-Aufgaben und -Fehlern in der Benutzeroberfläche von [Async-Aufträgen](/help/sites-administering/asynchronous-jobs.md) anzeigen.

   ![Benachrichtigung zum asynchronen Abrufen von Assets, die im Hintergrund ausgeführt werden.](assets/assets_async_transfer_fails.png)

   *Abbildung: Benachrichtigung zum asynchronen Abrufen von Assets, die im Hintergrund ausgeführt werden.*

1. Beim Veröffentlichen einer Seite zeigt [!DNL Experience Manager] eine vollständige Liste der auf der Seite verwendeten Assets an. Stellen Sie sicher, dass die Remote-Assets zum Zeitpunkt der Veröffentlichung erfolgreich abgerufen wurden. Informationen zum Überprüfen des Status der einzelnen abgerufenen Assets finden Sie in der Benutzeroberfläche für [Async-Aufträge](/help/sites-administering/asynchronous-jobs.md).

   >[!NOTE]
   >
   >Auch wenn ein oder mehrere Remote-Assets nicht abgerufen wurden, wird die Seite veröffentlicht. Die Komponente, die das Remote-Asset verwendet, wird leer veröffentlicht. Im [!DNL Experience Manager]-Benachrichtigungsbereich werden Benachrichtigungen zu Fehlern angezeigt, die auf der Seite „Async-Aufträge“ angezeigt werden.

>[!CAUTION]
>
>Nach der Verwendung auf einer Web-Seite können die abgerufenen Remote-Assets von jedem durchsucht und verwendet werden, der über die Berechtigung zum Zugriff auf den lokalen Ordner verfügt. Die abgerufenen Assets werden im lokalen Ordner gespeichert (`connectedassets` in der obigen Anleitung). Die Assets sind außerdem über [!UICONTROL Content Finder] durchsuchbar und im lokalen Repository sichtbar.

Die abgerufenen Assets können wie jedes andere lokale Element verwendet werden. Nur die zugehörigen Metadaten können nicht bearbeitet werden.

## Einschränkungen und Best Practices {#tips-and-limitations}

* Um Einblicke in die Asset-Nutzung zu erhalten, konfigurieren Sie die Funktion [Asset-Einblicke](/help/assets/asset-insights.md) in der [!DNL Sites]-Instanz.

### Berechtigungen und Asset-Verwaltung {#permissions-and-managing-assets}

* Lokale Assets werden nicht mit den ursprünglichen Assets auf der Remote-Implementierung synchronisiert. Das Ändern, Löschen oder Widerrufen von Berechtigungen auf der DAM-Implementierung wird nicht auf absteigende Hierarchien angewendet.
* Lokale Assets sind schreibgeschützte Kopien. [!DNL Experience Manager]-Komponenten nehmen zerstörungsfreie Änderungen an Assets vor. Sonstige Änderungen sind nicht zulässig.
* Lokal abgerufene Assets sind nur für Autoren verfügbar. Asset-Update-Workflows können nicht angewendet werden und Metadaten können nicht bearbeitet werden.
* Es werden nur Bilder und die aufgelisteten Dokumentenformate unterstützt. [!DNL Dynamic Media]-Assets, Inhaltsfragmente und Experience Fragments werden nicht unterstützt.
* [!DNL Experience Manager] ruft die Metadatenschemas nicht ab. Das bedeutet, dass möglicherweise nicht alle abgerufenen Metadaten angezeigt werden. Wenn das Schema separat aktualisiert wird, werden alle Eigenschaften angezeigt.
* Alle [!DNL Sites]-Autoren erhalten Leseberechtigungen für die abgerufenen Kopien, auch wenn sie keine Zugriffsberechtigungen für die Remote-DAM-Implemetierung haben.
* Keine API-Unterstützung, um die Integration anzupassen.
* Die Funktion unterstützt die nahtlose Suche und Verwendung von Remote-Assets. Wenn Sie viele Remote-Assets auf einmal für die lokale Implementierung verfügbar machen möchten, sollten Sie die Assets migrieren. Weitere Informationen finden Sie im [Handbuch zur Assets-Migration](assets-migration-guide.md).
* Es ist nicht möglich, ein Remote-Asset als Seitenminiaturansicht in der Benutzeroberfläche der [!UICONTROL Seiteneigenschaften] zu verwenden. Sie können eine Miniaturansicht einer Web-Seite in der Benutzeroberfläche [!UICONTROL Seiteneigenschaften] von [!UICONTROL Miniaturansicht] aus festlegen, indem Sie auf [!UICONTROL Bild auswählen] klicken.

### Einrichten und Lizenzieren {#setup-licensing}

* Die [!DNL Assets]-Implementierung auf [!DNL Adobe Managed Services] wird unterstützt.
* [!DNL Sites] kann jeweils nur eine Verbindung zu einem [!DNL Assets]-Repository herstellen.
* Eine Lizenz für [!DNL Assets], die als Remote-Repository dient.
* Eine oder mehrere Lizenzen für [!DNL Sites], die als lokale Autorenimplementierung dienen.

### Nutzung {#usage}

* Benutzer können bei der Inhaltserstellung nach Remote-Assets suchen und diese auf die lokale Seite ziehen. Es werden keine anderen Funktionen unterstützt.
* Nach 5 Sekunden tritt bei Abrufvorgängen ein Timeout auf. Autoren können beispielsweise bei Netzwerkproblemen Probleme beim Abrufen von Assets haben. Autoren können es erneut versuchen, indem sie das Remote-Asset aus [!UICONTROL Content Finder] in den [!UICONTROL Seiteneditor] ziehen.
* An abgerufenen Assets können einfache, zerstörungsfreie Änderungen sowie Änderungen, die von der `Image`-Komponente unterstützt werden, vorgenommen werden. Assets sind schreibgeschützt.
* Die einzige Methode zum erneuten Abrufen des Assets besteht darin, es auf eine Seite zu ziehen. Es gibt keine API-Unterstützung oder andere Methoden zum erneuten Abrufen eines Assets, um es zu aktualisieren.
* Wenn Assets aus dem DAM eingestellt werden, werden sie weiterhin auf [!DNL Sites]-Seiten verwendet.

## Fehlerbehebung bei Problemen   {#troubleshoot}

Gehen Sie wie folgt vor, um eine Fehlerbehebung für das allgemeine Fehlerszenario durchzuführen:

* Wenn Sie im [!UICONTROL Content Finder] nicht nach Remote-Assets suchen können, überprüfen Sie erneut, ob die erforderlichen Rollen und Berechtigungen eingerichtet sind.
* Ein aus dem Remote-DAM abgerufenes Asset kann aus verschiedenen Gründen nicht auf einer Web-Seite veröffentlicht werden. Es existiert nicht auf dem Remote-Server, es fehlen entsprechende Berechtigungen zum Abrufen oder ein Netzwerkfehler liegt vor. Stellen Sie sicher, dass das Asset nicht aus dem Remote-DAM entfernt wird. Stellen Sie sicher, dass die entsprechenden Berechtigungen eingerichtet und die Voraussetzungen erfüllt sind. Wiederholen Sie den Vorgang zum Hinzufügen des Assets zur Seite und veröffentlichen Sie erneut. Überprüfen Sie die [Liste asynchroner Aufträge](/help/sites-administering/asynchronous-jobs.md) auf Fehler beim Abrufen von Assets.
* Wenn Sie von der lokalen [!DNL Sites]-Bereitstellung aus nicht auf die Remote-DAM-Bereitstellung zugreifen können, stellen Sie sicher, dass seitenübergreifende Cookies erlaubt sind. Wenn seitenübergreifende Cookies blockiert werden, werden die beiden Bereitstellungen von [!DNL Experience Manager] möglicherweise nicht authentifiziert. Beispielsweise kann [!DNL Google Chrome] im Inkognito-Modus Cookies von Drittanbietern blockieren. Um Cookies im [!DNL Chrome]-Browser zuzulassen, klicken Sie auf das Augensymbol in der Adressleiste, navigieren Sie zu „Site funktioniert nicht“ > „Blockiert“, wählen Sie die Remote-DAM-URL aus und lassen Sie das Anmelde-Token-Cookie zu. Alternativ finden Sie in der Hilfe Informationen zum [Aktivieren von Cookies von Drittanbietern](https://support.google.com/chrome/answer/95647).

   ![Cookie-Fehler in Chrome im Inkognito-Modus](assets/chrome-cookies-incognito-dialog.png)
