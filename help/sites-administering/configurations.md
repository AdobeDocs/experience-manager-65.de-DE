---
title: Konfigurationen und der Konfigurationsbrowser
description: Machen Sie sich mit AEM Konfigurationen und der Verwaltung der Workspace-Einstellungen in AEM vertraut.
translation-type: tm+mt
source-git-commit: 8f5159d92f64b218d9e2e72d119e6de9d3e01ce6
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 2%

---


# Konfigurationen und der Konfigurationsbrowser {#configuration-browser}

AEM Konfigurationen dienen zur Verwaltung von Einstellungen in AEM und dienen als Arbeitsbereiche.

## Was ist eine Konfiguration? {#what-is-a-configuration}

Eine Konfiguration kann aus zwei verschiedenen Perspektiven betrachtet werden.

* [Ein Administrator](#configurations-administrator) verwendet Konfigurationen als Arbeitsbereiche in AEM, um Einstellungsgruppen zu definieren und zu verwalten.
* [Ein Entwickler](#configurations-developer) verwendet den zugrunde liegenden Konfigurationsmechanismus, der Konfigurationen implementiert, um die Einstellungen in AEM beizubehalten und nachzuschlagen.

Zusammenfassung: Aus der Ansicht eines Administrators ergeben sich bei Konfigurationen die Arbeitsbereiche zur Verwaltung von Einstellungen in AEM, während der Entwickler verstehen sollte, wie AEM diese Konfigurationen im Repository verwendet und verwaltet.

Konfigurationen dienen unabhängig von Ihrer Perspektive zwei Hauptzielen in AEM:

* Konfigurationen ermöglichen bestimmte Funktionen für bestimmte Benutzergruppen.
* Konfigurationen definieren Zugriffsrechte für diese Funktionen.

## Konfigurationen als Administrator {#configurations-administrator}

Sowohl der AEM-Administrator als auch die Autoren können Konfigurationen als Arbeitsbereiche betrachten. Diese Arbeitsbereiche können verwendet werden, um Gruppen von Einstellungen sowie deren zugehörigen Inhalt für organisatorische Zwecke zu sammeln, indem Zugriffsrechte für diese Funktionen implementiert werden.

Konfigurationen können für viele verschiedene Funktionen in AEM erstellt werden.

* [Cloud-Konfigurationen](/help/sites-administering/configurations.md)
* [Context Hub-Segmente](/help/sites-administering/segmentation.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitbare Vorlagen](/help/sites-authoring/templates.md)

### Beispiel {#administrator-example}

Ein Administrator kann beispielsweise zwei Konfigurationen für bearbeitbare Vorlagen erstellen.

* WKND-General
* WKND-Magazin

Der Admin kann dann allgemeine Seitenvorlagen mit der WKND-General Konfiguration und dann Vorlagen für das Magazin unter WKND-Magazine erstellen.

Der Administrator kann dann den WKND-General mit dem gesamten Inhalt der WKND-Site verknüpfen. Die WKND-Magazine-Konfiguration würde jedoch nur mit der Magazin-Site verknüpft.

Dies geschieht folgendermaßen:

* Wenn ein Autor eine neue Seite für die Zeitschrift erstellt, kann der Autor aus allgemeinen Vorlagen (WKND-Allgemein) oder Zeitschriftenvorlagen (WKND-Magazine) wählen.
* Wenn ein Autor eine neue Seite für einen anderen Teil der Site erstellt, der nicht die Zeitschrift ist, kann der Autor nur aus den allgemeinen Vorlagen (WKND-Allgemein) wählen.

Ähnliche Setups sind nicht nur für bearbeitbare Vorlagen, sondern auch für Cloud-Konfigurationen, ContextHub-Segmente und Inhaltsfragmentmodelle möglich.

### Verwenden des Konfigurationsbrowsers {#using-configuration-browser}

Der Konfigurationsbrowser ermöglicht es einem Administrator, Zugriffsrechte für Konfigurationen in AEM einfach zu erstellen, zu verwalten und zu konfigurieren.

>[!NOTE]
>
>Konfigurationen können nur mit dem Konfigurationsbrowser erstellt werden, wenn der Benutzer über `admin` Rechte verfügt. `admin` Rechte sind auch erforderlich, um der Konfiguration Zugriffsrechte zuzuweisen oder eine Konfiguration anderweitig zu ändern.

#### Erstellen einer Konfiguration {#creating-a-configuration}

Es ist ganz einfach, mithilfe des Konfigurationsbrowsers eine neue Konfiguration in AEM zu erstellen.

1. Melden Sie sich bei AEM als Cloud Service an und wählen Sie im Hauptmenü **Tools** -> **Allgemein** -> **Konfigurationsbrowser**.
1. Tippen oder klicken Sie auf **Erstellen**.
1. Geben Sie einen **Titel** und einen **Namen** für Ihre Konfiguration ein.

   ![Konfiguration erstellen](assets/configuration-create.png)

   * Der **Titel** sollte beschreibend sein.
   * Der **Name** wird zum Knotennamen im Repository.
      * Es wird automatisch auf der Grundlage des Titels generiert und entsprechend [AEM Benennungskonventionen angepasst.](/help/sites-developing/naming-conventions.md)
      * Er kann bei Bedarf angepasst werden.
1. Überprüfen Sie die Art der Konfigurationen, die Sie zulassen möchten.
   * [Cloud-Konfigurationen](/help/sites-administering/configurations.md)
   * [Context Hub-Segmente](/help/sites-administering/segmentation.md)
   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
   * [Bearbeitbare Vorlagen](/help/sites-authoring/templates.md)
1. Tippen oder klicken Sie auf **Erstellen**.

>[!TIP]
>
>Konfigurationen können verschachtelt sein.

#### Bearbeiten von Konfigurationen und deren Zugriffsrechten {#access-rights}

Wenn Sie Konfigurationen als Arbeitsbereiche betrachten, können Zugriffsrechte für diese Konfigurationen festgelegt werden, um zu erzwingen, wer auf diese Arbeitsbereiche zugreifen darf oder nicht.

1. Melden Sie sich bei AEM als Cloud Service an und wählen Sie im Hauptmenü **Tools** -> **Allgemein** -> **Konfigurationsbrowser**.
1. Wählen Sie die zu ändernde Konfiguration aus und tippen Sie dann in der Symbolleiste auf **Eigenschaften** oder klicken Sie auf diese.
1. Wählen Sie alle zusätzlichen Funktionen aus, die Sie der Konfiguration hinzufügen möchten
   >[!NOTE]
   >
   >Es ist nicht möglich, die Auswahl einer Funktion aufzuheben, nachdem die Konfiguration erstellt wurde.
1. Verwenden Sie die Schaltfläche &quot; **Effektive Berechtigungen** &quot;, um eine Rollenmatrix und die Berechtigungen, die derzeit für Konfigurationen gewährt werden, Ansicht.
   ![Fenster &quot;Effektive Berechtigungen&quot;](assets/configuration-effective-permissions.png)
1. Um neue Berechtigungen zuzuweisen, geben Sie den Benutzer- oder Gruppennamen in das Feld Benutzer oder Gruppe **auswählen** im Abschnitt **Neue Berechtigungen** ein.
   * Die Angebote für das Feld &quot;Benutzer oder Gruppe **auswählen** &quot;werden basierend auf vorhandenen Benutzern und Rollen automatisch ausgefüllt.
1. Wählen Sie den gewünschten Benutzer oder die entsprechende Rolle aus den Ergebnissen der automatischen Vervollständigung aus.
   * Sie können mehrere Benutzer oder Rollen auswählen.
1. Überprüfen Sie die Zugriffsoptionen, die die ausgewählten Benutzer oder Rollen haben sollen, und klicken Sie auf **Hinzufügen**.
   ![hinzufügen Zugriffsrechte auf eine Konfiguration](assets/configuration-edit.png)
1. Wiederholen Sie die Schritte, um Benutzer oder Rollen auszuwählen und nach Bedarf zusätzliche Zugriffsrechte zuzuweisen.
1. Tippen oder klicken Sie auf **Speichern &amp; Schließen** , wenn Sie fertig sind.

## Konfigurationen als Entwickler {#configurations-developer}

Als Entwickler ist es wichtig zu wissen, wie AEM als Cloud Service mit Konfigurationen funktioniert und wie Konfigurationsauflösung verarbeitet wird.

### Trennung von Konfiguration und Inhalt {#separation-of-config-and-content}

Obwohl der [Administrator und die Benutzer Konfigurationen als Arbeitsplätze](#configurations-administrator) zur Verwaltung verschiedener Einstellungen und Inhalte betrachten, ist es wichtig, zu verstehen, dass Konfigurationen und Inhalte von AEM im Repository getrennt gespeichert und verwaltet werden.

* `/content` ist die Heimat aller Inhalte.
* `/conf` ist die Heimat aller Konfigurationen.

Content verweist über eine `cq:conf` Eigenschaft auf die zugehörige Konfiguration. AEM führt eine Suche basierend auf dem Inhalt durch und es ist eine kontextuelle `cq:conf` Eigenschaft, um die entsprechende Konfiguration zu finden.

### Beispiel {#developer-example}

Nehmen wir an, Sie haben einen Anwendungscode, der an DAM-Einstellungen interessiert ist.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Der Ausgangspunkt der Konfigurationssuche ist eine Inhaltsressource, normalerweise irgendwo unter `/content`. Dies kann eine Seite, eine Komponente innerhalb einer Seite, ein Asset oder ein DAM-Ordner sein. Dies ist der eigentliche Inhalt, für den wir die richtige Konfiguration suchen, die in diesem Zusammenhang gilt.

Mit dem `Conf` Objekt können wir nun das spezifische Konfigurationselement abrufen, an dem wir interessiert sind. In diesem Fall ist es `dam/imageserver`eine Sammlung von Einstellungen im Zusammenhang mit der `imageserver`. Der `getItem` Aufruf gibt einen zurück `ValueMap`. Anschließend lesen wir eine `bgkcolor` Zeichenfolgeneigenschaft und geben den Standardwert &quot;FFFFFF&quot;ein, falls die Eigenschaft (oder das gesamte Konfigurationselement) nicht vorhanden ist.

Sehen wir uns nun den entsprechenden JCR-Inhalt an:

```text
/content/dam/wknd
    + jcr:content
      - cq:conf = "/conf/wknd"
    + image.png [dam:Asset]

/conf/wkns
    + settings
      + dam
        + imageserver [cq:Page]
          + jcr:content
            - bgkcolor = "FF0000"
```

In diesem Beispiel gehen wir von einem WKND-spezifischen DAM-Ordner und einer entsprechenden Konfiguration aus. Ab diesem Ordner `/content/dam/wknd`sehen wir, dass es eine String-Eigenschaft mit dem Namen gibt, `cq:conf` die auf die Konfiguration verweist, die für die Unterstruktur gelten soll. Die Eigenschaft wird in der Regel auf `jcr:content` einem Asset-Ordner oder einer Seite festgelegt. Diese `conf` Links sind explizit, daher ist es einfach, ihnen zu folgen, indem Sie sich den Inhalt in CRXDE ansehen.

Wenn wir hineinspringen `/conf`, folgen wir der Referenz und sehen, dass es einen `/conf/wknd` Knoten gibt. Dies ist eine Konfiguration. Beachten Sie, dass die Suche vollständig transparent für den Anwendungscode ist. Der Beispielcode hat keinen eigenen Verweis darauf, er ist hinter dem `Conf` Objekt versteckt. Welche Konfiguration angewendet wird, wird vollständig über den JCR-Inhalt gesteuert.

Die Konfiguration enthält einen festen `settings` Knoten, der die eigentlichen Elemente enthält, einschließlich der `dam/imageserver` , die wir in unserem Fall benötigen. Ein solches Element kann als &quot;Dokument für Einstellungen&quot;betrachtet werden und wird in der Regel durch ein Element dargestellt, `cq:Page` das den eigentlichen Inhalt `jcr:content` enthält.

Schließlich sehen wir die Eigenschaft, `bgkcolor` die unser Beispielcode benötigt. Die `ValueMap` Rückmeldung `getItem` erfolgt auf der Grundlage des `jcr:content` Knotens der Seite.

### Konfigurationsauflösung {#configuration-resolution}

Das grundlegende Beispiel oben zeigte eine einzelne Konfiguration. Es gibt jedoch viele Fälle, in denen Sie unterschiedliche Konfigurationen haben möchten, wie z.B. eine globale Standardkonfiguration, eine andere für jede Marke und vielleicht eine spezifische für Ihre Unterprojekte.

Um dies zu unterstützen, verfügt die Konfigurationssuche in AEM über einen Vererbungs- und Ausweichmechanismus in der folgenden Reihenfolge:

1. `/conf/<siteconfig>/<parentconfig>/<myconfig>`
   * Spezifische Konfiguration, auf die `cq:conf` in `/content`
   * Die Hierarchie ist willkürlich und kann genau wie Ihre Site-Struktur entworfen werden, es ist nicht Aufgabe des Anwendungscodes, dies zu wissen
   * Zur Laufzeit durch Benutzer mit Konfigurationsberechtigungen ändern
1. `/conf/<siteconfig>/<parentconfig>`
   * Übergeordnete Elemente für Ausweichkonfigurationen
   * Zur Laufzeit durch Benutzer mit Konfigurationsberechtigungen ändern
1. `/conf/<siteconfig>`
   * Übergeordnete Elemente für Ausweichkonfigurationen
   * Zur Laufzeit durch Benutzer mit Konfigurationsberechtigungen ändern
1. `/conf/global`
   * Globale Systemeinstellungen
   * In der Regel gelten globale Standardwerte für Ihre Installation
   * Durch eine `admin` Rolle festgelegt
   * Zur Laufzeit durch Benutzer mit Konfigurationsberechtigungen ändern
1. `/apps`
   * Anwendungsstandardwerte
   * Korrigiert durch Anwendungsbereitstellung
   * Schreibgeschützt zur Laufzeit
1. `/libs`
   * AEM Standard
   * Nur änderbar durch Adobe, Projektzugriff nicht erlaubt
   * Korrigiert durch Anwendungsbereitstellung
   * Schreibgeschützt zur Laufzeit

### Verwenden von Konfigurationen {#using-configurations}

Die Konfigurationen in AEM basieren auf Sling Context-Aware Konfigurationen. Die Sling-Pakete bieten eine Dienst-API, mit der kontextsensitive Konfigurationen abgerufen werden können. Kontextsensitive Konfigurationen sind Konfigurationen, die sich auf eine Inhaltsressource oder eine Ressourcenstruktur beziehen, wie im vorherigen Beispiel [beschrieben.](#developer-example)

Weitere Informationen zu Context-Aware-Konfigurationen, Beispielen und deren Verwendung [finden Sie in der Sling-Dokumentation.](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)

### ConfMgr Web Console {#confmgr-web-console}

Zu Debuggings- und Testzwecken befindet sich eine **ConfMgr** -Webkonsole `https://<host>:<port>/system/console/conf`, in der Konfigurationen für einen bestimmten Pfad/Element angezeigt werden können.

![ConfMgr](assets/configuration-confmgr.png)

Geben Sie einfach Folgendes an:

* **Inhalts-Pfad**
* **Item**
* **User**

Klicken Sie auf **Auflösen** , um zu sehen, welche Konfigurationen aufgelöst wurden und Beispielcode erhalten, der diese Konfigurationen löst.

### Kontextsensitive Konfiguration Web Console {#context-aware-web-console}

Zu Debuggings- und Testzwecken befindet sich eine **kontextabhängige Konfigurationswebkonsole** , `https://<host>:<port>/system/console/slingcaconfig`mit der kontextbezogene Konfigurationen im Repository abgefragt und deren Eigenschaften angezeigt werden können.

![Webkonsole für kontextabhängige Konfiguration](assets/configuration-context-aware-console.png)

Geben Sie einfach Folgendes an:

* **Inhalts-Pfad**
* **Konfigurationsname**

Klicken Sie auf **Auflösen** , um die verknüpften Kontextpfade und Eigenschaften für die ausgewählte Konfiguration abzurufen.
