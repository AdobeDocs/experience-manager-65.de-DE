---
title: Opt-in für Adobe Analytics und Adobe Target
description: Erfahren Sie, wie Sie sich für Adobe Analytics und Adobe Target anmelden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 3603e929-2aa1-4c25-ad9a-b10ff52a59f4
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 47%

---

# Opt-in für Adobe Analytics und Adobe Target{#opting-into-adobe-analytics-and-adobe-target}

AEM verfügt über ein Anmeldeverfahren, das Sie bei der Integration mit Adobe Analytics und Adobe Target unterstützt. Es ist als vorab geladene Aufgabe, die der Administratorbenutzergruppe zugewiesen ist, im Lieferumfang enthalten.

Wenn Sie sich als Administrator anmelden, wird diese Aufgabe (**Konfigurieren von Analytics und Targeting**) ist über verfügbar. [Posteingang](/help/sites-authoring/inbox.md#out-of-the-box-administrative-tasks). Basierend auf den von Ihnen angegebenen Anmeldedaten hilft es Ihnen, diese Dienste zu konfigurieren und zu integrieren.

Sie haben die folgenden Optionen zum Konfigurieren der Integration:

* Konfigurieren Sie die Integration über die Aufgabe.

  Sie können dies sofort oder später erledigen. Die Aufgabe verbleibt im Posteingang, bis eine Aktion durchgeführt wird. In beiden Fällen ist die Konfiguration direkt auf der Benutzeroberfläche oder mithilfe einer vordefinierten `.properties`-Datei möglich.

* Lehnen Sie die Integration ab.

  Erwägen Sie die Verwendung dieser Option, falls Sie es vorziehen, [die Integration manuell zu konfigurieren](/help/sites-administering/marketing-cloud.md). Siehe auch [Integrieren von AEM in Adobe Target und Adobe Analytics mithilfe von DTM](https://helpx.adobe.com/de/experience-manager/using/integrate-digital-marketing-solutions.html).

* Konfigurieren Sie die Einrichtung und Bereitstellung mithilfe eines Skripts.

## Konfigurieren der Integration {#configuring-the-integration}

Opt-in für die Integration mit:

* Analytics , um die Verwendung ihrer Seitenverfolgungs- und Analysefunktionen zu ermöglichen.
* Target, um die Verwendung der Personalisierungsfunktionen zu aktivieren 

Für jede Option müssen Sie die Benutzerkontoinformationen angeben und die nachverfolgten Seiten angeben.

>[!NOTE]
>
>Sie können optional Analytics- und Target-Kontoinformationen mithilfe einer Eigenschaftendatei bereitstellen, die beim Serverstart gelesen wird. Siehe [Bereitstellen von Kontoinformationen mithilfe einer Eigenschaftendatei](/help/sites-administering/opt-in.md#providing-account-information-using-a-properties-file).

Wenn Sie sich für die Integration entscheiden, führt AEM die folgenden Aufgaben aus:

* Erstellt die Cloud-Konfigurationen, die die Verbindung zu Analytics und Target ermöglichen.
* Erstellt die Frameworks, die die nachverfolgten Daten bestimmen.
* Konfiguriert die Webseiten für die Verwendung dieser Dienste.

>[!NOTE]
>
>AT.js ist die Standard-Client-Bibliothek. Dies wird unter Ihrer [Target-Cloud-Services-Konfiguration](/help/sites-administering/target-configuring.md#creating-a-target-cloud-configuration).
>
>Adobe empfiehlt die Verwendung von AT.js als Client-Bibliothek.

So wählen Sie die vorab geladene, vordefinierte Aufgabe aus:

1. Wählen Sie im [Posteingang über **Öffnen** die Aufgabe „Analytics &amp; Targeting konfigurieren“](/help/sites-authoring/inbox.md#taking-action-on-an-item) aus.

   ![optin-01](assets/optin-01.png)

1. Für Analytics:

   1. Geben Sie die Benutzerkontoinformationen für Analytics ein und klicken Sie dann auf die entsprechende **Hinzufügen** Schaltfläche.
   1. Die entsprechenden Anmeldeinformationen werden authentifiziert.
   1. Wenn das Analytics-Konto authentifiziert ist, wählen Sie die zu verwendende Analytics Report Suite aus. AEM ruft diese Analytics Report Suites ab. Der Status wird in **Hinzugefügt** geändert.

1. Für Target:

   1. Geben Sie die Benutzerkontoinformationen für Target ein und klicken Sie dann auf die entsprechende **Hinzufügen** Schaltfläche.
   1. Die entsprechenden Anmeldeinformationen werden authentifiziert. Der Status wird in **Hinzugefügt** geändert.

1. Wählen Sie **Weiter** aus.
1. Wählen Sie die Websites aus, für die Analytics bzw. Target verwendet werden soll.

1. Wählen Sie **Fertig**, um den Vorgang abzuschließen.

   >[!CAUTION]
   >
   >Nachdem Sie den Opt-in für die Konfiguration durchgeführt haben, müssen Sie die betroffenen Websites/Seiten veröffentlichen, um diese Änderungen auf Ihrer Veröffentlichungsinstanz zu replizieren.

## Abmelden von der Integration {#opting-out-of-the-integration}

Deaktivieren Sie die Integration mit Analytics und Target, wenn Sie eine der folgenden Aktionen durchführen:

* Sie möchten nicht in diese Produkte integrieren.
* Konfigurieren Sie die Integrationen lieber manuell.

  Informationen zur manuellen Konfiguration der Integrationen finden Sie unter [Integrieren mit Adobe Analytics](/help/sites-administering/adobeanalytics.md) und [Integrieren mit Adobe Target](/help/sites-administering/target.md).

Für den Opt-out müssen Sie die vorab geladene Aufgabe durchführen:

* Wählen Sie im [Posteingang die Option zum **Durchführen** der Aufgabe „Analytics &amp; Targeting konfigurieren“](/help/sites-authoring/inbox.md#taking-action-on-an-item).

## Bereitstellen von Kontoinformationen mithilfe einer Eigenschaftendatei {#providing-account-information-using-a-properties-file}

Installieren Sie eine Eigenschaftendatei, die beim Serverstart gelesen AEM, um die Kontoeigenschaften für die Integration mit Analytics und Target zu konfigurieren. Wenn Sie die Eigenschaftendatei verwenden, verwendet der Opt-in-Assistent automatisch die Eigenschaften aus der Datei und die Cloud-Konfiguration wird entsprechend erstellt.

Die Eigenschaftendatei ist eine Textdatei mit dem Namen &quot;marketingcloud.properties&quot;, die Sie in dem Arbeitsverzeichnis speichern, das der AEM-Prozess verwendet (normalerweise dasselbe Verzeichnis wie die JAR-Datei). Die Datei enthält die folgenden Eigenschaften:

* analytics.server: Die URL des verwendeten Analytics-Rechenzentrums.
* analytics.company: Das Unternehmen, das mit Ihrem Analytics-Benutzerkonto verknüpft ist.
* analytics.username: Ihr Analytics-Benutzername.
* analytics.secret: Das Geheimnis, das mit Ihrem Analytics-Benutzernamen verknüpft ist.
* analytics.reportsuite: Der Name der zu verwendenden Analytics Report Suite.
* target.clientcode: Der Clientcode, der mit Ihrem Target-Konto verknüpft ist.
* target.email: Die E-Mail-Adresse, die Sie zur Authentifizierung Ihres Target-Kontos verwenden.
* target.password: Das Kennwort, das Ihrer E-Mail-Adresse zugeordnet ist.

Eigenschaften und Werte werden durch gleiche Zeichen (=) getrennt. Die Analytics-Eigenschaften haben das Präfix `analytics` und die Target-Eigenschaften das Präfix `target`. Geben Sie zum Konfigurieren eines Dienstes Werte für alle Eigenschaften für diesen Dienst an. Wenn Sie keinen Dienst konfigurieren möchten, geben Sie keine Werte für diesen Dienst an.

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

1. Fügen Sie die Eigenschaftswerte entsprechend Ihren Analytics- und/oder Target-Konten hinzu.
1. Starten oder starten Sie den Server neu und melden Sie sich dann über ein Administratorkonto an.
1. Öffnen Sie die Aufgabe &quot;Analytics &amp; Targeting konfigurieren&quot;, wie in [Konfigurieren der Integration](/help/sites-administering/opt-in.md#configuring-the-integration). Anstatt Ihre Kontoinformationen anzufragen, nutzt der Assistent die Werte aus der `.properties`-Datei.

   Wählen Sie **Hinzufügen** für den entsprechenden Dienst und fahren Sie anschließend mit dem Assistenten fort.

   ![optin-02](assets/optin-02.png)

## Über die Cloud-Konfigurationen {#about-the-cloud-configurations}

Wenn Sie die Integration mit Analytics und Target konfigurieren, erstellt AEM automatisch die erforderlichen Cloud-Konfigurationen und Frameworks. Die Analytics-Cloud-Konfiguration heißt beispielsweise &quot;Bereitgestelltes Analytics-Konto&quot;.

Sie müssen die Cloud-Konfigurationen nicht ändern. Sie können die Frameworks jedoch nach Bedarf konfigurieren. (Siehe [Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften](/help/sites-administering/adobeanalytics-mapping.md) und [Hinzufügen eines Ziel-Frameworks](/help/sites-administering/target.md).)

>[!NOTE]
>
>Wenn Sie den Opt-in für den Adobe Target-Konfigurationsassistenten durchführen, wird die „präzise Zielgruppenerfassung“ aktiviert.
>
>Präzise Zielgruppenerfassung bedeutet, dass für die Cloud Service-Konfiguration gewartet wird, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Aus diesem Grund kann hinsichtlich der Leistung eine präzise Zielgruppenbestimmung eine Verzögerung von einigen Millisekunden verursachen, bevor das Laden des Inhalts erfolgt.
>
>Die präzise Zielgruppenerfassung ist auf der Autoreninstanz immer aktiviert. Auf der Veröffentlichungsinstanz können Sie die präzise Zielgruppenerfassung aber global deaktivieren, indem Sie in der Cloud Service-Konfiguration das Häkchen neben „Präzise Zielgruppenerfassung“ entfernen (**http://localhost:4502/etc/cloudservices.html**). Sie können die präzise Zielgruppenerfassung auch für einzelne Komponenten aktivieren und deaktivieren, unabhängig von Ihrer Einstellung in der Cloud-Service-Konfiguration.
>
>Wenn Sie ***bereits*** Zielkomponenten erstellt haben und Sie diese Einstellung ändern, wirken sich Ihre Änderungen nicht auf diese Komponenten aus. Sie müssen alle Änderungen an diesen Komponenten direkt vornehmen.

>[!CAUTION]
>
>Wenn Sie den Opt-in für die Analytics-Konfiguration durchführen und eine bestimmte `reportsuite` ausgewählt ist, wird das Framework auf den Ausführungsmodus für die Veröffentlichung beschränkt. Dies bedeutet, dass das Tracking nur für die Veröffentlichungsinstanz funktioniert.
>
>Falls das Tracking auch für eine Autoreninstanz benötigt wird, sollte der Wert in `all` geändert werden.

## Konfigurieren der Einrichtung und Bereitstellung über ein Skript {#configuring-the-setup-and-provisioning-via-script}

Als Administrator möchten Sie möglicherweise die Einrichtung und Bereitstellung eines Triggers mit einem Skript durchführen, anstatt den Assistenten manuell zu durchlaufen. Sie können dies tun, indem Sie:

* Senden einer POST-Anfrage an **/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json** mit den erforderlichen Parametern.

Welche Parameter Sie senden, hängt von folgenden Faktoren ab:

* Wenn Sie die **marketingcloud.properties** Datei mit allen erforderlichen Anmeldeinformationen eingeben, müssen Sie die folgenden Parameter senden:

   * `automaticProvisioning`= `true`
   * `servicename`= `analytics|target`
   * `path`=Pfad zu einer AEM-Seite, um die erstellten Cloud Service-Konfigurationen anzufügen

  Eine Curl-Anforderung, mit der sowohl die Analytics- als auch die Target-Konfiguration erstellt und an die Seite „we-retail“ angefügt wird, lautet beispielsweise wie folgt:

  ```shell
  curl -v -u admin:admin -X POST -d"automaticProvisioning=true&servicename=target&servicename=analytics&path=/content/we-retail" http://localhost:4502/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json
  ```

* Wenn Sie die **marketingcloud.properties** -Datei, dann müssen Sie die Anmeldedaten und Parameter senden. Beispiel:
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
