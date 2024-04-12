---
title: Häufig gestellte Fragen zu AEM
description: Verwenden Sie diese häufig gestellten Fragen, um allgemeine Workflows oder Probleme im Zusammenhang mit AEM nachzuvollziehen sowie eine entsprechende Fehlersuche oder Konfiguration vorzunehmen.
exl-id: 182c464a-ff7a-467b-9eb5-8ffac335a87a
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 97%

---

# Häufig gestellte Fragen (FAQ) zu AEM {#aem-faqs}

Hier finden Sie Antworten auf Fragen im Zusammenhang mit der Problembehebung und Konfiguration in AEM.

## Sites {#sites}

### Wie konfiguriere ich eine Binary-Less-Verteilung? {#how-do-i-configure-binary-less-distribution}

Eine Binary-Less-Verteilung wird für Bereitstellungen über einen freigegebenen Datenspeicher unterstützt und beinhaltet die Verwendung von Agenten, die den Vault-basierten Package-Builder „Distribution Package Exporter“ (werkseitige PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) nutzen.

Bei aktiviertem Binary-Less-Modus enthalten die verteilten Inhaltspakete Verweise auf Binärdaten und nicht die Binärdaten selbst.

#### Wie aktiviere ich die Binary-Less-Verteilung? {#how-do-i-enable-binary-less-distribution}

Stellen Sie zur Aktivierung der Binary-Less-Verteilung einen freigegebenen Blob-Speicher bereit.
Überprüfen Sie die `useBinaryReferences`-Eigenschaft in der OSGi-Konfiguration mit der werkseitigen PID (`org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*, die der Agent verwendet.

#### Wie kann ich Berechtigungen aktivieren, während ich eine Sprachkopie für Inhaltsautorinnen und Inhaltsautoren in AEM erstelle? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Zum Erstellen der Sprachkopie-Funktion benötigen Autorinnen und Autoren Berechtigungen für den Speicherort `/content/projects`.

Wenn Autorinnen und Autoren auch Projekte verwalten müssen, fügen Sie sie als vorübergehende Lösung der Gruppe `projects-administrators` hinzu.

#### Wie ändere ich das Format während der Erstellung einer Sprachkopie für ein Projekt? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Erstellen Sie einen Sprachstamm und eine Sprachkopie innerhalb des Stamms, bevor Sie ein Übersetzungsprojekt erstellen.

Beispiel: 
Erstellen Sie einen Sprach-Stamm unter `/content/geometrixx` mit dem Namen `fr_LU` (und dem Titel „Französisch (Luxemburg)“). Erstellen Sie anschließend eine Sprachkopie der Seite aus dem Bereich „Verweise“ und navigieren Sie zur Option `Create structure only` in `Create & Translate`. Erstellen Sie abschließend ein Übersetzungsprojekt und fügen Sie dann die Sprachkopie zum Übersetzungsauftrag hinzu.

Einzelheiten finden Sie unter den folgenden zusätzlichen Themen:

* [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md)
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md)

#### Wie lassen sich AEM-Funktionen im Zusammenhang mit Anmeldeversuchen und ACL- oder Berechtigungsänderungen prüfen? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM bietet nun die Möglichkeit, administrative Änderungen zu protokollieren, um Fehlerbehebungen und Audits zu erleichtern. Standardmäßig werden die Informationen in der Datei `error.log` protokolliert. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern.
Informationen dazu, wie Sie Einträge in einer separaten Protokolldatei speichern, finden Sie unter [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

#### Wie kann ich SSL standardmäßig aktivieren? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 bietet einen SSL-Assistenten sowie eine Benutzeroberfläche zum Konfigurieren der Jetty- und Granite Jetty-SSL-Unterstützung.

Informationen dazu, wie Sie SSL standardmäßig aktivieren können, finden Sie unter [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md).

#### Welche Architektur empfiehlt sich bei der Nutzung der AEM Content Services über eine mobile App, idealerweise React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Die Content Services basieren auf Sling-Modellen und AEM-Entwicklerinnen und -Entwickler müssen ein Sling-Modell-POJO für jede zu exportierende Komponente bereitstellen.

Erläuterungen dazu, wie AEM Content Services von einer React-Anwendung genutzt werden, erhalten Sie im Tutorial [Erste Schritte mit AEM Content Services](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de).

Wenn Entwicklerinnen und Entwickler eine Komponentenstruktur exportieren möchten, können sie auch die `ComponentExporter`- und `ContainerExporter`-Schnittstellen implementieren sowie mithilfe von `ModelFactory` die untergeordneten Komponenten durchlaufen und ihre Modelldarstellung zurückgeben. Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling :: Sling Models](https://sling.apache.org/documentation/bundles/models.html)

#### Deaktivieren des AEM 6.4-Umfrage-Popups {#how-to-disable-aem-survey-pop-up}

Sie können sich für die Erfassung von Nutzungsstatistiken entscheiden, indem Sie entweder die Touch-Benutzeroberfläche oder die Web-Konsole verwenden. Ausführliche Anweisungen finden Sie unter[ Entscheidung für die aggregierte Erfassung von Nutzungsstatistiken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

#### Gibt es eine gute Ressource, die die wichtigsten Funktionen für ein Upgrade auf AEM 6.4 hervorhebt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Lesen Sie die Informationen unter [Verstehen der Gründe für die Aktualisierung auf AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html). Dort finden Sie eine Übersicht über die wichtigsten Funktionen für den Fall, dass Sie eine Aktualisierung auf die neueste Version von Adobe Experience Manager in Betracht ziehen.

## Assets {#assets}

### Warum wiederholt sich der Assets-Workflow beim Hochladen von MP4-Dateien (z. B. mit der Drag-and-Drop-Methode)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Wenn die Person, die die Filmdateien hochlädt, keine Löschberechtigungen unter dem Asset-Knoten hat, schlägt das Löschen der Chunk-Knoten fehl und der Upload wird neu gestartet.

#### Welche Standardeinstellungen gelten für native Konfigurationen beim Erstellen der Sprachkopie? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wenn Sie über die Touch-Benutzeroberfläche eine Sprachkopie erstellen (**Verweise** > **Sprachkopie aktualisieren**), wird unter der neuen Sprache ein neuer DAM-Ordner erstellt und von dort aus wird auf Assets verwiesen.

Dies ist die Standardeinstellung für vordefinierte Konfigurationen. Sie können in Übersetzungskonfigurationen für die Option **Seiten-Assets übersetzen** die Einstellung **Nicht übersetzen** festlegen.
Klicken Sie dazu in AEM 6.4 auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.

#### Wie lässt sich eine AEM-Komponente deaktivieren, die zu einem exponentiellen Wachstum des AEM-Segmentspeichers führt (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Sie können den OSGi Component Disabler deaktivieren. Informationen zur Nutzung dieses Dienstes finden Sie unter [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als Problemumgehung können Sie die Komponente auch manuell deaktivieren und zwar entweder über die Benutzeroberfläche oder per `curl`-Befehl (siehe nachstehendes Beispiel) nach jedem Neustart von AEM.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Wie lassen sich Admin-Konsolen anpassen? {#how-to-customize-admin-consoles}

AEM bietet verschiedene Methoden zum Anpassen von Konsolen und der Seitenbearbeitungsfunktionen Ihrer Autoreninstanz. Informationen zum Erstellen einer benutzerdefinierten Konsole und zum Anpassen einer Standardansicht für eine Konsole finden Sie unter [ Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md).

#### Was ist der Unterschied zwischen CoralUI 2- und CoralUI 3-basierten Komponenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Für Coral3 wurde ein neuer Satz Sling-Komponenten der Granite-Benutzeroberflächen-Foundation erstellt, die sich unter [/libs/granite/ui/components/coral/foundation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html)Es gibt einen Satz für CoralUI 2-basierte Komponenten und einen Satz für CoralUI 3-basierte Komponenten. Bei dem neuen Satz handelt es sich nicht nur um eine eingefügte Kopie des alten Satzes, sondern dieser wird vielmehr bereinigt (z. B. Optimierung, Entfernung veralteter Funktionen). Daher wird empfohlen, dass eine Seite entweder nur CoralUI 3-basierte oder nur CoralUI 2-basierte Sätze verwendet.

Ausführliche Informationen finden Sie im [Migrationsleitfaden für CoralUI 3-basierte Komponenten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Anpassen der Suchkomponente in AEM Assets {#how-to-customize-the-search-component-in-aem-assets}

Weitere Informationen zum Suchboost/Ranking und zur Implementierung finden Sie im [Handbuch zur Implementierung der einfachen Suche](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html?lang=de).

Bei der Implementierung der einfachen Suche handelt es sich um die Materialien vom Summit Lab „AEM Search Demystified“ von 2017.

#### Ist es möglich, ein Plugin für WordPress zu erstellen, das es Kundinnen und Kunden ermöglicht, auf die Adobe-Asset-Auswahl zuzugreifen, um Bilder auszuwählen? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, Kundinnen und Kunden, die WordPress verwenden, können Adobe-Asset-Auswahl verwenden, um Bilder vom AEM Assets-Server auszuwählen und sie zu Beiträgen auf der WordPress-Site hinzuzufügen.

Weitere Informationen finden Sie unter [Asset-Auswahl](../assets/search-assets.md#assetpicker).
