---
title: Opt-in für Adobe Analytics und Adobe Target
description: Erfahren Sie, wie Sie ein Opt-in für Adobe Analytics und Adobe Target durchführen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 3603e929-2aa1-4c25-ad9a-b10ff52a59f4
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 100%

---

# Opt-in für Adobe Analytics und Adobe Target{#opting-into-adobe-analytics-and-adobe-target}

AEM verfügt über ein Opt-in-Verfahren, das die Integration in Adobe Analytics und Adobe Target erleichtert. Es ist als vorab geladene Aufgabe, die der Administratorbenutzergruppe zugewiesen ist, im Lieferumfang enthalten.

Wenn Sie sich als Admin anmelden, ist diese Aufgabe (**Analytics und Targeting konfigurieren**) über den [Posteingang](/help/sites-authoring/inbox.md#out-of-the-box-administrative-tasks) verfügbar. Basierend auf den von Ihnen angegebenen Anmeldeinformationen wird Ihnen beim Konfigurieren und Integrieren dieser Dienste geholfen.

Um die Integration zu konfigurieren, haben Sie folgende Möglichkeiten:

* Konfigurieren Sie die Integration über die Aufgabe.

  Sie können dies sofort oder später erledigen. Die Aufgabe verbleibt im Posteingang, bis eine Aktion durchgeführt wird. In beiden Fällen ist die Konfiguration direkt auf der Benutzeroberfläche oder mithilfe einer vordefinierten `.properties`-Datei möglich.

* Lehnen Sie die Integration ab.

  Erwägen Sie die Verwendung dieser Option, falls Sie es vorziehen, [die Integration manuell zu konfigurieren](/help/sites-administering/marketing-cloud.md). Siehe auch [Integrieren von AEM in Adobe Target und Adobe Analytics mithilfe von DTM](https://helpx.adobe.com/de/experience-manager/using/integrate-digital-marketing-solutions.html).

* Konfigurieren Sie das Setup und die Bereitstellung über ein Skript.

## Konfigurieren der Integration {#configuring-the-integration}

Führen Sie das Opt-in für folgende Integrationen durch:

* Analytics, um die Verwendung der Funktionen für Seiten-Tracking und Analyse zu aktivieren
* Target, um die Verwendung der Personalisierungsfunktionen zu aktivieren 

Für beide Optionen müssen Sie die Benutzerkontoinformationen und die nachzuverfolgenden Seiten angeben.

>[!NOTE]
>
>Optional können Sie die Analytics- und Target-Kontoinformationen mit einer Eigenschaftendatei angeben, die beim Server-Start gelesen wird. Siehe [Angeben von Kontoinformationen mit einer Eigenschaftendatei](/help/sites-administering/opt-in.md#providing-account-information-using-a-properties-file).

Beim Opt-in für die Integration werden von AEM die folgenden Aufgaben durchgeführt:

* Erstellen der Cloud-Konfigurationen, die die Verbindung zu Analytics und Target ermöglichen
* Erstellen der Frameworks zur Ermittlung der nachzuverfolgenden Daten
* Konfigurieren der Web-Seiten für die Nutzung dieser Dienste

>[!NOTE]
>
>„AT.js“ ist die standardmäßige Client-Bibliothek. Dies wird über die [Target-Cloud-Service-Konfiguration](/help/sites-administering/target-configuring.md#creating-a-target-cloud-configuration) festgelegt.
>
>Adobe empfiehlt, „AT.js“ als Client-Bibliothek zu verwenden.

So führen Sie das Opt-in über die vorab geladene, vorkonfigurierte Standardaufgabe durch:

1. Wählen Sie im [Posteingang über **Öffnen** die Aufgabe „Analytics &amp; Targeting konfigurieren“](/help/sites-authoring/inbox.md#taking-action-on-an-item) aus.

   ![optin-01](assets/optin-01.png)

1. Für Analytics:

   1. Geben Sie die Benutzerkontoinformationen für Analytics ein und klicken Sie dann auf die Schaltfläche **Hinzufügen**.
   1. Die entsprechenden Anmeldeinformationen werden authentifiziert.
   1. Nachdem das Analytics-Konto authentifiziert wurde, wählen Sie die gewünschte Analytics-Report Suite aus. AEM ruft diese Analytics-Report Suites ab. Der Status wird in **Hinzugefügt** geändert.

1. Für Target:

   1. Geben Sie die Benutzerkontoinformationen für Target ein und klicken Sie dann auf die entsprechende Schaltfläche **Hinzufügen**.
   1. Die entsprechenden Anmeldeinformationen werden authentifiziert. Der Status wird in **Hinzugefügt** geändert.

1. Wählen Sie **Weiter** aus.
1. Wählen Sie die Websites aus, für die Analytics bzw. Target verwendet werden soll.

1. Wählen Sie **Fertig**, um den Vorgang abzuschließen.

   >[!CAUTION]
   >
   >Nachdem Sie den Opt-in für die Konfiguration durchgeführt haben, müssen Sie die betroffenen Websites/Seiten veröffentlichen, um diese Änderungen auf Ihrer Veröffentlichungsinstanz zu replizieren.

## Opt-out für die Integration {#opting-out-of-the-integration}

Sie können in folgenden Fällen ein Opt-out für die Integration in Analytics und Target durchführen:

* Sie wünschen keine Integration in diese Produkte.
* Sie ziehen es vor, die Integrationen manuell zu konfigurieren.

  Informationen zur manuellen Konfiguration der Integrationen finden Sie unter [Integrieren mit Adobe Analytics](/help/sites-administering/adobeanalytics.md) und [Integrieren mit Adobe Target](/help/sites-administering/target.md).

Für den Opt-out müssen Sie die vorab geladene Aufgabe durchführen:

* Wählen Sie im [Posteingang die Option zum **Durchführen** der Aufgabe „Analytics &amp; Targeting konfigurieren“](/help/sites-authoring/inbox.md#taking-action-on-an-item).

## Angeben von Kontoinformationen mit einer Eigenschaftendatei {#providing-account-information-using-a-properties-file}

Installieren Sie eine Eigenschaftendatei, die von AEM beim Server-Start gelesen wird, um die Kontoeigenschaften für die Integration in Analytics und Target zu konfigurieren. Bei Verwendung der Eigenschaftendatei nutzt der Opt-in-Assistent automatisch die Eigenschaften aus der Datei, und die Cloud-Konfiguration wird entsprechend erstellt.

Die Eigenschaftendatei ist eine Textdatei mit dem Namen „marketingcloud.properties“, die Sie im von AEM verwendeten Arbeitsverzeichnis speichern (normalerweise in demselben Verzeichnis wie die JAR-Datei). Die Datei enthält die folgenden Eigenschaften:

* analytics.server: Die URL des verwendeten Analytics-Rechenzentrums
* analytics.company: Das Unternehmen, das Ihrem Analytics-Benutzerkonto zugeordnet ist
* analytics.username: Ihr Analytics-Benutzername
* analytics.secret: Das Geheimnis, das Ihrem Analytics-Benutzernamen zugeordnet ist
* analytics.reportsuite: Der Name der zu verwendenden Analytics-Report Suite
* target.clientcode: Der Clientcode, der Ihrem Target-Konto zugeordnet ist
* target.email: Die E-Mail-Adresse, die Sie zum Authentifizieren Ihres Target-Kontos verwenden
* target.password: Das Kennwort, das Ihrer E-Mail-Adresse zugeordnet ist

Eigenschaften und Werte sind jeweils durch ein Gleichheitszeichen (=) voneinander getrennt. Die Analytics-Eigenschaften haben das Präfix `analytics` und die Target-Eigenschaften das Präfix `target`. Geben Sie zum Konfigurieren eines Dienstes Werte für alle Eigenschaften des Dienstes an. Falls Sie keinen Dienst konfigurieren möchten, geben Sie einfach keine Werte für den Dienst an.

Die folgende `.properties`-Beispieldatei enthält die Eigenschaftswerte für die Erstellung einer Cloud-Konfiguration für Analytics:

```xml
analytics.server=https://test.omniture.com/login/
analytics.company=MyCompany
analytics.username=sbroders
analytics.secret=12345678
analytics.reportsuite=myreportsuite
target.clientcode=
target.email=
target.password=
```

Im folgenden Verfahren wird beschrieben, wie Sie den Opt-in für die Integration mit der Eigenschaftendatei durchführen.

1. Erstellen Sie die Datei `marketingcloud.properties` in dem Arbeitsverzeichnis, das für den AEM-Prozess verwendet wird (Autoreninstanz).

   >[!NOTE]
   >
   >Das Arbeitsverzeichnis ist normalerweise das Verzeichnis, in dem sich die JAR- oder `license.properties`-Datei befindet.
   >
   >Es kann aber auch von der Systemeigenschaft als absoluter Pfad definiert werden:
   >
   >`mac.provisioning.file.container`

1. Fügen Sie die Eigenschaftswerte gemäß Ihren Analytics- und/oder Target-Konten hinzu.
1. Starten Sie den Server bzw. starten Sie ihn neu und melden Sie sich dann mit einem Administratorkonto an.
1. Öffnen Sie die Aufgabe „Analytics und Targeting konfigurieren“, wie unter [Konfigurieren der Integration](/help/sites-administering/opt-in.md#configuring-the-integration) beschrieben. Anstatt Ihre Kontoinformationen anzufragen, nutzt der Assistent die Werte aus der `.properties`-Datei.

   Wählen Sie **Hinzufügen** für den entsprechenden Dienst und fahren Sie anschließend mit dem Assistenten fort.

   ![optin-02](assets/optin-02.png)

## Informationen zu Cloud-Konfigurationen {#about-the-cloud-configurations}

Wenn Sie die Integration in Analytics und Target konfigurieren, erstellt AEM automatisch die erforderlichen Cloud-Konfigurationen und Frameworks. Die Analytics-Cloud-Konfiguration wird beispielsweise als bereitgestelltes Analytics-Konto bezeichnet.

Sie müssen die Cloud-Konfigurationen nicht ändern. Sie können aber die Frameworks wie gewünscht konfigurieren. (Siehe [Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften](/help/sites-administering/adobeanalytics-mapping.md) und [Hinzufügen eines Ziel-Frameworks](/help/sites-administering/target.md).)

>[!NOTE]
>
>Wenn Sie den Opt-in für den Adobe Target-Konfigurationsassistenten durchführen, wird die „präzise Zielgruppenerfassung“ aktiviert.
>
>Präzise Zielgruppenerfassung bedeutet, dass für die Cloud Service-Konfiguration gewartet wird, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Aus diesem Grund kann hinsichtlich der Leistung eine präzise Zielgruppenbestimmung eine Verzögerung von einigen Millisekunden verursachen, bevor das Laden des Inhalts erfolgt.
>
>Die präzise Zielgruppenerfassung ist auf der Autoreninstanz immer aktiviert. Auf der Veröffentlichungsinstanz können Sie die präzise Zielgruppenerfassung aber global deaktivieren, indem Sie in der Cloud Service-Konfiguration das Häkchen neben „Präzise Zielgruppenerfassung“ entfernen (**http://localhost:4502/etc/cloudservices.html**). Sie können die präzise Zielgruppenerfassung auch für einzelne Komponenten aktivieren und deaktivieren, unabhängig von Ihrer Einstellung in der Cloud-Service-Konfiguration.
>
>Wenn Sie ***bereits*** Zielkomponenten erstellt haben und Sie diese Einstellung ändern, wirken sich Ihre Änderungen nicht auf diese Komponenten aus. Nehmen Sie alle Änderungen an diesen Komponenten direkt vor.

>[!CAUTION]
>
>Wenn Sie den Opt-in für die Analytics-Konfiguration durchführen und eine bestimmte `reportsuite` ausgewählt ist, wird das Framework auf den Ausführungsmodus für die Veröffentlichung beschränkt. Dies bedeutet, dass das Tracking nur für die Veröffentlichungsinstanz funktioniert.
>
>Falls das Tracking auch für eine Autoreninstanz benötigt wird, sollte der Wert in `all` geändert werden.

## Konfigurieren des Setups und der Bereitstellung per Skript {#configuring-the-setup-and-provisioning-via-script}

Es kann sein, dass Sie als Admin das Setup und die Bereitstellung per Skript auslösen möchten, anstatt manuell den Assistenten durchlaufen zu müssen. Gehen Sie hierzu wie folgt vor:

* Senden Sie eine POST-Anfrage mit den erforderlichen Parametern an **/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json**.

Welche Parameter Sie senden müssen, hängt von Folgendem ab:

* Wenn Sie die Datei **marketingcloud.properties** verwenden möchten, in die alle erforderlichen Anmeldeinformationen eingefügt sind, müssen Sie die folgenden Parameter senden:

   * `automaticProvisioning`= `true`
   * `servicename`= `analytics|target`
   * `path`=Pfad zu einer AEM-Seite, um die erstellten Cloud Service-Konfigurationen anzufügen

  Eine Curl-Anforderung, mit der sowohl die Analytics- als auch die Target-Konfiguration erstellt und an die Seite „we-retail“ angefügt wird, lautet beispielsweise wie folgt:

  ```shell
  curl -v -u admin:admin -X POST -d"automaticProvisioning=true&servicename=target&servicename=analytics&path=/content/we-retail" http://localhost:4502/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json
  ```

* Wenn Sie die Datei **marketingcloud.properties** nicht verwenden möchten, müssen Sie die Anmeldeinformationen und Parameter senden. Zum Beispiel:
   * automaticProvisioning= `true`
   * servicename= `analytics|target`
   * path=Pfad zu einer AEM-Seite, um die erstellten Cloud Service-Konfigurationen anzufügen; es können mehrere Pfade definiert werden
   * analytics.server= `https://servername`
   * analytics.company= `Name of company`
   * analytics.username= `me`
   * analytics.secret= `secret`
   * analytics.reportsuite= `we-retail`
   * target.clientcode= `mycompany`
   * target.email= `me@adobe.com`
   * target.password= `password`

  In diesem Fall würde die Curl-Anforderung, mit der die Analytics- und Target-Konfiguration erstellt und an die Seite „we-retail“ angefügt wird, wie folgt lauten:

  ```shell
  curl -v -u admin:admin -X POST -d"automaticProvisioning=false&servicename=target&servicename=analytics&path=/content/we-retail&analytics.server=https://servername/&analytics.company=Name of company&analytics.username=me&analytics.secret=secret&analytics.reportsuite=weretail&target.clientcode=mycompany&target.email=me@adobe.com&target.password=password" http://localhost:4502/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json
  ```
