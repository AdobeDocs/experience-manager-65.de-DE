---
title: Häufig gestellte Fragen (FAQ) zu AEM
seo-title: Häufig gestellte Fragen zu AEM 6.4
description: Ziehen Sie diese FAQ heran, um allgemeine Workflows oder Probleme im Zusammenhang mit AEM nachzuvollziehen und zu beheben bzw. entsprechende Konfigurationen vorzunehmen.
seo-description: Ziehen Sie diese FAQ heran, um allgemeine Workflows oder Probleme im Zusammenhang mit AEM nachzuvollziehen und zu beheben bzw. entsprechende Konfigurationen vorzunehmen.
uuid: 17d34923-f1ce-463b-8e9d-a713edcce51b
contentOwner: jsyal
discoiquuid: a3bb5695-6593-413d-9c2f-4c164e663b15
docset: aem65
exl-id: 182c464a-ff7a-467b-9eb5-8ffac335a87a
source-git-commit: 68c36d4e3a14567a4d115ee64a4474bcaf9aa386
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 74%

---

# Häufig gestellte Fragen (FAQ) zu AEM {#aem-faqs}

Hier finden Sie Antworten auf Fragen im Zusammenhang mit der Problembehebung und Konfiguration in AEM.

## Sites {#sites}

### Wie konfiguriere ich eine Binary-Less-Verteilung?  {#how-do-i-configure-binary-less-distribution}

Eine Binary-Less-Verteilung wird für Bereitstellungen über einen freigegebenen Datenspeicher unterstützt und beinhaltet die Verwendung von Agenten, die den Vault-basierten Package Builder „Distribution Package Exporter“ (werkseitige PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) nutzen.

Bei aktiviertem Binary-Less-Modus enthalten die verteilten Inhaltspakete Verweise auf Binärdaten und nicht die Bindärdaten selbst.

#### Wie aktiviere ich die Binary-Less-Verteilung?  {#how-do-i-enable-binary-less-distribution}

Stellen Sie zur Aktivierung der Binary-Less-Verteilung einen freigegebenen Blob-Speicher bereit.
Überprüfen Sie die Eigenschaft `useBinaryReferences` in der OSGi-Konfiguration mit der werkseitigen PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*, die Ihr Agent verwendet.

#### Wie kann ich die Fehlermeldungen beim Navigieren durch die Seitenhierarchie in der AEM Sites-Konsole anpassen? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Rufen Sie den Bereich „Netzwerk“ (des Chrome-Browsers) auf, um persönliche Einstellungen festzulegen (ohne minimierte JavaScript-Version).

Sehen Sie sich die Spalte `Initiator` an, um festzustellen, wer der Initiator einer Anfrage war. Sie enthält die Dateien und die Zeilennummern, von wo aus die AJAX-Aufrufe ausgeführt werden. Später können Sie die Fehlerverarbeitungsfunktion nachverfolgen und die Fehlermeldung gemäß Ihren Anforderungen ändern.

#### Wie kann ich Berechtigungen aktivieren, während ich eine Sprachkopie für „content-authors“ in AEM erstelle?  {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Um eine Sprachkopie-Funktion zu erstellen, benötigen Inhaltsautoren Berechtigungen am `/content/projects`-Speicherort.

Wenn die Autoren auch Projekte verwalten müssen, können Sie den Autor zur Gruppe `project-administrators` hinzufügen.

#### Wie ändere ich das Format während der Erstellung einer Sprachkopie für ein Projekt? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Vor dem Erstellen eines Übersetzungsprojekts müssen Sie einen Sprach-Stamm und eine Sprachkopie innerhalb des Stamms erstellen.

Beispiel:
Erstellen Sie einen Sprachstamm unter `/content/geometrixx` mit dem Namen `fr_LU` (und dem Titel Französisch (Luxemburg)). Erstellen Sie anschließend eine Sprachkopie der Seite aus dem Bedienfeld &quot;Verweise&quot;und navigieren Sie zur Option `Create structure only` in `Create & Translate`. Erstellen Sie abschließend ein Übersetzungsprojekt und fügen Sie dann die Sprachkopie zum Übersetzungsauftrag hinzu.

Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

* [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md)
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md)

#### Wie lassen sich AEM-Funktionen im Zusammenhang mit Anmeldeversuchen und ACL- oder Berechtigungsänderungen prüfen? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM bietet nun die Möglichkeit, administrative Änderungen zu protokollieren, um Fehlerbehebungen und Audits zu erleichtern. Standardmäßig werden die Informationen in der Datei `error.log` protokolliert. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern.
Informationen dazu, wie Sie Einträge in einer separaten Protokolldatei speichern, finden Sie unter [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

#### Wie lässt sich SSL standardmäßig aktivieren? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 bietet einen SSL-Assistenten sowie eine Benutzeroberfläche zum Konfigurieren der Jetty- und Granite Jetty-SSL-Unterstützung.

Informationen dazu, wie Sie SSL standardmäßig aktivieren können, finden Sie unter [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md).

#### Welche Architektur empfiehlt sich bei der Nutzung der AEM Content Services über eine mobilen App, idealerweise React Native?  {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Die Content Services basieren auf den Sling-Modellen und die AEM Entwickler müssen für jede exportierte Komponente ein Sling-Modell-Pojo bereitstellen.

Erläuterungen dazu, wie AEM Content Services von einer React-Anwendung genutzt werden, erhalten Sie im Tutorial [Erste Schritte mit AEM Content Services](https://helpx.adobe.com/de/experience-manager/kt/sites/using/content-services-tutorial-use.html).

Wenn Entwickler außerdem eine Komponentenstruktur exportieren möchten, können sie auch die Schnittstellen `ComponentExporter` und `ContainerExporter` implementieren sowie `ModelFactory` verwenden, um die untergeordneten Komponenten zu iterieren und ihre Modelldarstellung zurückzugeben. Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling: Sling-Modelle](https://sling.apache.org/documentation/bundles/models.html)

#### Wie lässt sich das AEM 6.4-Umfrage-Popup deaktivieren? {#how-to-disable-aem-survey-pop-up}

Sie können die Sammlung von Nutzungsstatistiken über die Touch-optimierte Benutzeroberfläche oder die Web-Konsole aktivieren. Eine ausführliche Anleitung finden Sie unter [Aggregierte Sammlung von Nutzungsstatistiken aktivieren](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

#### Gibt es eine Übersicht über die wichtigsten Funktionen, die mit der Aktualisierung auf AEM 6.4 zur Verfügung stehen?  {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Unter [Gründe für die Aktualisierung AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) finden Sie eine Beschreibung der allgemeinen Aufschlüsselung der wichtigsten Funktionen für Kunden, die ein Upgrade auf die neueste Version von Adobe Experience Manager erwägen.

## Assets {#assets}

### Warum wiederholt sich der Assets-Workflow beim Hochladen von MP4-Dateien (z. B. bei Verwendung der Drag-and-Drop-Methode)?  {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Wenn der Benutzer, der die Filmdateien hochlädt, nicht über die Berechtigungen zum Löschen für den Asset-Knoten verfügt, schlägt die Löschung von Chunk-Knoten fehl und der Upload wird neu gestartet.

#### Was sind die Standardeinstellungen für OOTB -Konfigurationen beim Erstellen von Sprachkopien? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wenn Sie eine Sprachkopie über die Touch-Benutzeroberfläche erstellen (**Verweise** -> **Sprachkopie aktualisieren**), wird unter der neuen Sprache ein neuer DAM-Ordner erstellt und von dort aus werden Assets referenziert.

Dies ist die Standardeinstellung für OOTB-Konfigurationen. Sie können in Übersetzungskonfigurationen für die Option **Seiten-Assets übersetzen** die Einstellung **Nicht übersetzen** festlegen.
Klicken Sie dazu in AEM 6.4 auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.

#### Wie lässt sich eine AEM-Komponente deaktivieren, die zu einem exponentiellen Wachstum des AEM-Segmentspeichers führt (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Sie können den OSGi Component Disabler deaktivieren. Informationen zur Verwendung dieses Diensts finden Sie unter [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als Problemumgehung können Sie die Komponente auch manuell deaktivieren und zwar entweder über die Benutzeroberfläche oder per `curl`-Befehl (siehe nachstehendes Beispiel) nach jedem Neustart von AEM.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Wie lassen sich Admin-Konsolen anpassen? {#how-to-customize-admin-consoles}

AEM bietet verschiedene Mechanismen, mit denen Sie die Konsolen und die Seitenbearbeitungsfunktionen Ihrer Authoring-Instanz anpassen können. Informationen zum Erstellen von benutzerdefinierten Konsolen und Anpassen einer Standardansicht für eine Konsole finden Sie unter [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md).

#### Was ist der Unterschied zwischen CoralUI 2- und CoralUI 3-basierten Komponenten?  {#what-is-the-difference-between-coralui-and-coralui-based-components}

Ein neuer Satz von Sling-Komponenten von Granite UI Foundation wird für Coral3 erstellt und befindet sich unter [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) befinden. Es gibt einen Satz von CoralUI 2-basierten Komponenten und einen Satz von CoralUI 3-basierten Komponenten. Bei dem neuen Satz handelt es sich nicht um eine bloße Kopie des alten Satzes, sondern um eine bereinigte Version (u. .a optimiert und ohne veraltete Funktionen). Entsprechend empfiehlt es sich, dass eine Seite entweder ausschließlich den CoralUI 3-basierten oder aber den CoralUI 2-basierten Satz verwendet.

Weitere Informationen finden Sie im [Migrationsleitfaden für CoralUI 3-basierte Komponenten](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Wie lässt sich die Suchkomponente in AEM Assets anpassen? {#how-to-customize-the-search-component-in-aem-assets}

Um mehr über Suchoptimierung/Ranking zu erfahren und weitere Informationen zur Implementierung zu erhalten, ziehen Sie den [Leitfaden für die Implementierung der einfachen Suche](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html) heran.

Bei der Implementierung der einfachen Suche handelt es sich um die Materialien vom Summit Lab „AEM Search Demystified“ von 2017.

#### Ist es möglich, ein Plug-in für WordPress zu erstellen, das einem Kunden den Zugriff auf die Adobe Asset-Auswahl ermöglicht, um Bilder auszuwählen? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, WordPress-Kunden können mithilfe der Asset-Auswahl von Adobe Bilder von ihrem AEM Assets-Server auszuwählen, um sie zu Beiträgen auf ihrer WordPress-Site hinzuzufügen.

Weitere Informationen finden Sie unter [Asset-Wähler](../assets/search-assets.md#assetpicker).
