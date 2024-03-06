---
title: Häufig gestellte Fragen zu AEM
description: Verwenden Sie diese häufig gestellten Fragen, um allgemeine Workflows oder Probleme in AEM zu verstehen, zu konfigurieren und zu beheben.
exl-id: 182c464a-ff7a-467b-9eb5-8ffac335a87a
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 40%

---

# Häufig gestellte Fragen (FAQ) zu AEM {#aem-faqs}

Erfahren Sie mehr über die Antworten auf einige AEM Probleme bei der Fehlerbehebung und Konfiguration.

## Sites {#sites}

### Wie konfiguriere ich eine Binary-Less-Verteilung? {#how-do-i-configure-binary-less-distribution}

Eine Binärdatei-lose Verteilung wird für Bereitstellungen über einen freigegebenen Datenspeicher unterstützt und beinhaltet Agenten, die den Vault-basierten Package Exporter von Verteilungspaketen verwenden (werkseitige PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) Package Builder.

Bei aktiviertem Binary-Less-Modus enthalten die verteilten Inhaltspakete Verweise auf Binärdaten und nicht die Binärdaten selbst.

#### Wie aktiviere ich eine Binary-Less-Verteilung? {#how-do-i-enable-binary-less-distribution}

Stellen Sie zur Aktivierung der Binary-Less-Verteilung einen freigegebenen Blob-Speicher bereit.
Überprüfen Sie die `useBinaryReferences`-Eigenschaft in der OSGi-Konfiguration mit der werkseitigen PID (`org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*, die der Agent verwendet.

#### Wie kann ich beim Erstellen von Sprachkopien für Inhaltsautoren in AEM Berechtigungen aktivieren? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Zum Erstellen der Sprachkopie-Funktion benötigen Autorinnen und Autoren Berechtigungen für den Speicherort `/content/projects`.

Wenn Autorinnen und Autoren auch Projekte verwalten müssen, fügen Sie sie als vorübergehende Lösung der Gruppe `projects-administrators` hinzu.

#### Wie kann das Format beim Erstellen der Sprachkopie für ein Projekt geändert werden? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Erstellen Sie einen Sprachstamm und eine Sprachkopie im Stammverzeichnis, bevor Sie ein Übersetzungsprojekt erstellen.

Beispiel: 
Erstellen Sie einen Sprach-Stamm unter `/content/geometrixx` mit dem Namen `fr_LU` (und dem Titel „Französisch (Luxemburg)“). Erstellen Sie anschließend eine Sprachkopie der Seite aus dem Bereich „Verweise“ und navigieren Sie zur Option `Create structure only` in `Create & Translate`. Erstellen Sie abschließend ein Übersetzungsprojekt und fügen Sie dann die Sprachkopie zum Übersetzungsauftrag hinzu.

Weitere Informationen finden Sie in den folgenden zusätzlichen Ressourcen:

* [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md)
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md)

#### Wie lassen sich AEM-Funktionen im Zusammenhang mit Anmeldeversuchen und ACL- oder Berechtigungsänderungen prüfen? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM bietet nun die Möglichkeit, administrative Änderungen zu protokollieren, um Fehlerbehebungen und Audits zu erleichtern. Standardmäßig werden die Informationen in der Datei `error.log` protokolliert. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern.
Informationen dazu, wie Sie Einträge in einer separaten Protokolldatei speichern, finden Sie unter [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

#### Wie wird SSL standardmäßig aktiviert? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 ist im Lieferumfang des SSL-Assistenten enthalten und bietet eine Benutzeroberfläche zum Konfigurieren der Jetty- und Granite Jetty-SSL-Unterstützung.

Informationen zum Aktivieren von SSL standardmäßig finden Sie unter [SSL standardmäßig](/help/sites-administering/ssl-by-default.md).

#### Welche Architektur wird empfohlen, wenn AEM Content Services von einer mobilen App verwendet werden, idealerweise React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Die Content Services basieren auf Sling-Modellen und AEM-Entwicklerinnen und -Entwickler müssen ein Sling-Modell-POJO für jede zu exportierende Komponente bereitstellen.

Erläuterungen dazu, wie AEM Content Services von einer React-Anwendung genutzt werden, erhalten Sie im Tutorial [Erste Schritte mit AEM Content Services](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de).

Wenn die Entwickler außerdem eine Komponentenstruktur exportieren möchten, können sie auch die `ComponentExporter` und `ContainerExporter` -Schnittstellen und verwenden Sie `ModelFactory` um die untergeordneten Komponenten zu iterieren und ihre Modelldarstellung zurückzugeben. Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling :: Sling Models](https://sling.apache.org/documentation/bundles/models.html)

#### Wie kann AEM 6.4 Umfrage-Popup deaktiviert werden? {#how-to-disable-aem-survey-pop-up}

Sie können die Erfassung von Nutzungsstatistiken über die Touch-Benutzeroberfläche oder die Web-Konsole aktivieren. Detaillierte Anweisungen finden Sie unter [Aggregierte Sammlung von Nutzungsstatistiken aktivieren](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

#### Gibt es eine gute Ressource, die die wichtigsten Funktionen für die Aktualisierung auf AEM 6.4 hervorhebt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Siehe [Gründe für die Aktualisierung AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) beschreibt die allgemeine Aufschlüsselung der wichtigsten Funktionen für Kunden, die ein Upgrade auf die neueste Version von Adobe Experience Manager in Erwägung ziehen.

## Assets {#assets}

### Warum wiederholt sich der Assets-Workflow beim Hochladen von MP4-Dateien (z. B. mittels Drag &amp; Drop-Methode)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Wenn der Benutzer beim Hochladen der Filmdateien keine Löschberechtigungen unter dem Asset-Knoten hat, schlagen die Löschungs-Chunk-Knoten fehl und der Upload wird neu gestartet.

#### Welche Standardeinstellungen gelten für native Konfigurationen beim Erstellen der Sprachkopie? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wenn Sie eine Sprachkopie über die Touch-Benutzeroberfläche erstellen (**Verweise** > **Sprachkopie aktualisieren**), wird unter der neuen Sprache ein neuer DAM-Ordner erstellt und von dort aus auf Assets verwiesen.

Dies ist die Standardeinstellung für vordefinierte Konfigurationen. Sie können in Übersetzungskonfigurationen für die Option **Seiten-Assets übersetzen** die Einstellung **Nicht übersetzen** festlegen.
Klicken Sie dazu in AEM 6.4 auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.

#### Wie lässt sich eine AEM-Komponente deaktivieren, die zu einem exponentiellen Wachstum des AEM-Segmentspeichers führt (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Sie können den OSGi Component Disabler deaktivieren. Informationen zur Verwendung dieses Dienstes finden Sie unter [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als Problemumgehung können Sie die Komponente auch manuell deaktivieren und zwar entweder über die Benutzeroberfläche oder per `curl`-Befehl (siehe nachstehendes Beispiel) nach jedem Neustart von AEM.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Wie lassen sich Admin-Konsolen anpassen? {#how-to-customize-admin-consoles}

AEM bietet verschiedene Methoden zum Anpassen von Konsolen und der Seitenbearbeitungsfunktionen Ihrer Autoreninstanz. Informationen zum Erstellen einer benutzerdefinierten Konsole und Anpassen einer Standardansicht für eine Konsole finden Sie unter [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md).

#### Was ist der Unterschied zwischen den auf CoralUI 2 und CoralUI 3 basierenden Komponenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Für Coral3 wurde ein neuer Satz Sling-Komponenten der Granite-Benutzeroberflächen-Foundation erstellt, die sich unter [/libs/granite/ui/components/coral/foundation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Es gibt einen Satz für CoralUI 2-basierte Komponenten und einen Satz für CoralUI 3-basierte Komponenten. Der neue Satz ist nicht nur ein Copy &amp; Paste des alten Sets, sondern wird bereinigt (z. B. Straffung, Entfernung veralteter Funktionen). Daher wird empfohlen, dass eine Seite nur einen CoralUI 3-basierten oder CoralUI 2-basierten Satz verwendet.

Weitere Informationen finden Sie unter [Migrationshandbuch für CoralUI 3-basiert](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Wie kann die Suchkomponente in AEM Assets angepasst werden? {#how-to-customize-the-search-component-in-aem-assets}

Weitere Informationen zur Suchsteigerung/Rangfolge und weitere Implementierungsinformationen finden Sie unter [Implementierungshandbuch für einfache Suchen](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html?lang=de).

Bei der Implementierung der einfachen Suche handelt es sich um die Materialien vom Summit Lab „AEM Search Demystified“ von 2017.

#### Ist es möglich, ein Plugin für WordPress zu erstellen, das es einem Kunden ermöglicht, auf die Adobe Asset-Auswahl zuzugreifen, um Bilder auszuwählen? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, ein Kunde, der WordPress verwendet, kann mit der Adobe Asset-Auswahl Bilder von seinem AEM Assets-Server auswählen, um sie zu Beiträgen auf seiner WordPress-Site hinzuzufügen.

Siehe Abschnitt [Asset-Auswahl](../assets/search-assets.md#assetpicker) für weitere Informationen.
