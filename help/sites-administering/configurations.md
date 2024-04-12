---
title: Konfigurationen und der Konfigurations-Browser
description: Machen Sie sich mit AEM-Konfigurationen und der Verwaltung der Einstellungen für den Arbeitsbereich in AEM vertraut.
exl-id: 1be5849b-748c-48e8-afa8-35a9026c27b3
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 100%

---

# Konfigurationen und der Konfigurations-Browser {#configuration-browser}

AEM-Konfigurationen dienen zur Verwaltung von Einstellungen in AEM und als Arbeitsbereiche.

## Was ist eine Konfiguration? {#what-is-a-configuration}

Eine Konfiguration kann aus zwei verschiedenen Blickwinkeln betrachtet werden.

* [Ein Administrator](#configurations-administrator) verwendet Konfigurationen als Arbeitsbereiche in AEM, um Gruppen von Einstellungen zu definieren und zu verwalten.
* [Ein Entwickler](#configurations-developer) verwendet den zugrunde liegenden Konfigurationsmechanismus, der Konfigurationen implementiert, um Einstellungen in AEM beizubehalten und einzusehen.

Zusammenfassend: Aus Sicht eines Administrators sind Konfigurationen das Erstellen von Arbeitsbereichen zum Verwalten von Einstellungen in AEM, während der Entwickler verstehen sollte, wie AEM diese Konfigurationen im Repository verwendet und verwaltet.

Unabhängig von Ihrem Blickwinkel dienen Konfigurationen in AEM zwei Hauptzwecken:

* Konfigurationen ermöglichen bestimmte Funktionen für bestimmte Benutzergruppen.
* Konfigurationen definieren Zugriffsrechte für diese Funktionen.

## Konfigurationen als Administrator {#configurations-administrator}

AEM-Admins und Autorinnen bzw. Autoren können Konfigurationen als Arbeitsbereiche betrachten. Diese Arbeitsbereiche können verwendet werden, um Gruppen von Einstellungen sowie deren zugehörigen Inhalt für organisatorische Zwecke zu erfassen, indem Zugriffsrechte für diese Funktionen implementiert werden.

Konfigurationen können für viele verschiedene Funktionen in AEM erstellt werden.

* [Cloud-Konfigurationen](/help/sites-administering/configurations.md)
* [Context-Hub-Segmente](/help/sites-administering/segmentation.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitbare Vorlagen](/help/sites-authoring/templates.md)

### Beispiel {#administrator-example}

Admins können beispielsweise zwei Konfigurationen für bearbeitbare Vorlagen erstellen.

* WKND-General
* WKND-Magazin

Der Administrator kann dann allgemeine Seitenvorlagen mit der Konfiguration „WKND-General“ und magazinspezifische Vorlagen unter „WKND-Magazin“ erstellen.

Der Administrator kann dann „WKND-General“ mit allen Inhalten der WKND-Site verknüpfen. Die Konfiguration „WKND-Magazin“ würde jedoch nur mit der Magazin-Site verknüpft.

Dies geschieht folgendermaßen:

* Wenn eine Inhaltsautorin bzw. ein Inhaltsautor eine neue Seite für das Magazin erstellt, lässt sich zwischen allgemeinen Vorlagen (WKND-General) oder Magazinvorlagen (WKND-Magazin) wählen.
* Wenn die Inhaltsautorin bzw. der Inhaltsautor eine neue Seite für einen anderen Teil der Website erstellt, der nicht das Magazin ist, lässt sich nur aus den allgemeinen Vorlagen (WKND-General) auswählen.

Ähnliche Setups sind nicht nur für bearbeitbare Vorlagen möglich, sondern auch für Cloud-Konfigurationen, ContextHub-Segmente und Inhaltsfragmentmodelle.

### Verwenden des Konfigurations-Browsers {#using-configuration-browser}

Mit dem Konfigurations-Browser kann ein Administrator auf einfache Weise Zugriffsrechte für Konfigurationen in AEM erstellen, verwalten und konfigurieren.

>[!NOTE]
>
>Es ist nur möglich, Konfigurationen mit dem Konfigurations-Browser zu erstellen, wenn der Benutzer über `admin`-Rechte verfügt. Administratorrechte sind auch erforderlich, um der Konfiguration Zugriffsrechte zuzuweisen oder eine Konfiguration anderweitig zu ändern.

#### Erstellen einer Konfiguration {#creating-a-configuration}

Es ist einfach, mithilfe des Konfigurations-Browsers eine Konfiguration in AEM zu erstellen.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü **Tools** > **Allgemein** > **Konfigurations-Browser** aus.
1. Klicken Sie auf **Erstellen**.
1. Geben Sie einen **Titel** und einen **Namen** für Ihre Konfiguration an.

   ![Erstellen einer Konfiguration](assets/configuration-create.png)

   * Der **Titel** sollte beschreibend sein.
   * Der **Name** wird zum Knotennamen im Repository.
      * Er wird automatisch auf Grundlage des Titels generiert und gemäß den [AEM-Namenskonventionen](/help/sites-developing/naming-conventions.md) angepasst.
      * Er kann bei Bedarf angepasst werden.
1. Markieren Sie die Art der Konfigurationen, die zugelassen werden sollen.
   * [Cloud-Konfigurationen](/help/sites-administering/configurations.md)
   * [Context-Hub-Segmente](/help/sites-administering/segmentation.md)
   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
   * [Bearbeitbare Vorlagen](/help/sites-authoring/templates.md)
1. Klicken Sie auf **Erstellen**.

>[!TIP]
>
>Konfigurationen können verschachtelt sein.

#### Bearbeiten von Konfigurationen und deren Zugriffsrechten {#access-rights}

Wenn Sie Konfigurationen als Arbeitsbereiche betrachten, können Zugriffsrechte für diese Konfigurationen festgelegt werden, um zu erzwingen, wer auf diese Arbeitsbereiche zugreifen darf und wer nicht.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü **Tools** > **Allgemein** > **Konfigurations-Browser** aus.
1. Wählen Sie die zu ändernde Konfiguration aus und klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Wählen Sie alle zusätzlichen Funktionen aus, die Sie der Konfiguration hinzufügen möchten.

   >[!NOTE]
   >
   >Es ist nicht möglich, die Auswahl einer Funktion aufzuheben, nachdem die Konfiguration erstellt wurde.

1. Verwenden Sie die Schaltfläche **Gültige Berechtigungen**, um eine Matrix der Rollen und der ihnen derzeit gewährten Berechtigungen für Konfigurationen anzuzeigen.
   ![Fenster „Gültige Berechtigungen“](assets/configuration-effective-permissions.png)
1. Um neue Berechtigungen zuzuweisen, geben Sie den Benutzer- oder Gruppennamen in das Feld **Benutzer oder Gruppe wählen** im Abschnitt **Neue Berechtigung hinzufügen** ein.
   * Das Feld **Benutzer oder Gruppe wählen** bietet eine automatische Vervollständigung basierend auf vorhandenen Benutzern und Rollen.
1. Wählen Sie den entsprechenden Benutzer oder die entsprechende Rolle aus den Ergebnissen der automatischen Vervollständigung aus.
   * Sie können mehrere Benutzer oder Rollen auswählen.
1. Markieren Sie die gewünschten Zugriffsoptionen für die ausgewählten Benutzenden/Rollen aus und klicken Sie auf **Hinzufügen**.
   ![Zugriffsrechte zu einer Konfiguration hinzufügen](assets/configuration-edit.png)
1. Wiederholen Sie die Schritte, um Benutzende oder Rollen auszuwählen und nach Bedarf zusätzliche Zugriffsrechte zuzuweisen.
1. Wählen Sie **Speichern und schließen** aus, wenn Sie fertig sind.

## Konfigurationen als Entwickler {#configurations-developer}

Als Entwickler ist es wichtig zu wissen, wie AEM as a Cloud Service mit Konfigurationen funktioniert und wie eine Konfigurationsauflösung verarbeitet wird.

### Trennung von Konfiguration und Inhalt {#separation-of-config-and-content}

Obwohl der [Administrator und die Benutzer Konfigurationen möglicherweise als Arbeitsplätze](#configurations-administrator) zum Verwalten unterschiedlicher Einstellungen und Inhalte betrachten, ist es wichtig zu verstehen, dass Konfigurationen und Inhalte von AEM separat im Repository gespeichert und verwaltet werden.

* `/content` nimmt alle Inhalte auf.
* `/conf` nimmt alle Konfigurationen auf.

Inhalt referenziert seine zugehörige Konfiguration über eine `cq:conf`-Eigenschaft. AEM führt basierend auf dem Inhalt und seiner Kontexteigenschaft `cq:conf` eine Suche durch, um die entsprechende Konfiguration zu finden.

### Beispiel {#developer-example}

Nehmen wir für dieses Beispiel an, Sie haben Programm-Code, der an DAM-Einstellungen interessiert ist.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Der Ausgangspunkt aller Konfigurationsabfragen ist eine Inhaltsressource unter `/content`. Dies kann eine Seite, eine Komponente innerhalb einer Seite, ein Asset oder ein DAM-Ordner sein. Dies ist der eigentliche Inhalt, für den wir nach der richtigen Konfiguration suchen, die in diesem Zusammenhang gilt.

Mit dem `Conf`-Objekt können wir nun das spezifische Konfigurationselement abrufen, an dem wir interessiert sind. In diesem Fall ist es `dam/imageserver`, was eine Sammlung von Einstellungen im Zusammenhang mit `imageserver` ist. Der Aufruf `getItem` gibt ein `ValueMap` zurück. Anschließend lesen Sie eine `bgkcolor`-Zeichenfolgeneigenschaft aus und geben den Standardwert „FFFFFF“ an, falls die Eigenschaft (oder das gesamte Konfigurationselement) nicht vorhanden ist.

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

In diesem Beispiel gehen Sie von einem WKND-spezifischen DAM-Ordner und einer entsprechenden Konfiguration aus. Ausgehend von diesem Ordner `/content/dam/wknd` wird eine Zeichenfolgeneigenschaft mit dem Namen `cq:conf` angezeigt, die auf die Konfiguration verweist, die für die Unterstruktur gelten soll. Die Eigenschaft wird auf `jcr:content` eines Asset-Ordners oder einer Asset-Seite festgelegt. Diese `conf`-Links sind explizit, sodass es einfach ist, ihnen zu folgen, indem Sie sich den Inhalt in CRXDE ansehen.

Wenn Sie in `/conf` springen, können Sie dem Verweis folgen und sehen, dass es einen `/conf/wknd`-Knoten gibt. Dies ist eine Konfiguration. Die Suche ist für den Anwendungs-Code transparent. Der Beispiel-Code hat niemals einen dedizierten Verweis darauf, er verbirgt sich vielmehr hinter dem `Conf`-Objekt. Welche Konfiguration gilt, wird durch den JCR-Inhalt gesteuert.

Sie können sehen, dass die Konfiguration einen fest benannten `settings`-Knoten mit den tatsächlichen Elementen enthält, einschließlich `dam/imageserver`, was in diesem Fall benötigt wird. Ein solches Element kann als „Einstellungsdokument“ betrachtet werden und wird durch eine `cq:Page` dargestellt, die `jcr:content` mit dem tatsächlichen Inhalt enthält.

Schließlich können Sie die Eigenschaft `bgkcolor` sehen, die der Beispiel-Code benötigt. Die `ValueMap`, die Sie von `getItem` erhalten, basiert auf dem `jcr:content`-Knoten der Seite.

### Konfigurationsauflösung {#configuration-resolution}

Das grundlegende Beispiel oben zeigte eine einzelne Konfiguration. Es gibt jedoch viele Fälle, in denen unterschiedliche Konfigurationen wünschenswert sind, z. B. eine globale Standardkonfiguration, eine andere für jede Marke und möglicherweise eine spezifische für Ihre Unterprojekte.

Um dies zu unterstützen, verfügt die Konfigurationssuche in AEM über einen Vererbungs- und Ausweichmechanismus in der folgenden Reihenfolge ihrer Präferenz:

1. `/conf/<siteconfig>/<parentconfig>/<myconfig>`
   * Spezifische Konfiguration, auf die von `cq:conf` irgendwo in `/content` verwiesen wird
   * Die Hierarchie ist willkürlich und kann genau wie Ihre Site-Struktur entworfen werden, es ist nicht Aufgabe des Programm-Codes, dies zu wissen
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/conf/<siteconfig>/<parentconfig>`
   * Übergeordnete Elemente für Ausweichkonfigurationen
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/conf/<siteconfig>`
   * Übergeordnete Elemente für Ausweichkonfigurationen
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/conf/global`
   * Globale Systemeinstellungen
   * Globale Standardeinstellungen für Ihre Installation
   * Durch eine `admin`-Rolle festgelegt
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/apps`
   * Programmstandardwerte
   * Mit der Programmbereitstellung festgelegt
   * Zur Laufzeit schreibgeschützt
1. `/libs`
   * AEM-Produktstandardwerte
   * Nur von Adobe änderbar, Projektzugriff nicht erlaubt
   * Mit der Programmbereitstellung festgelegt
   * Zur Laufzeit schreibgeschützt

### Verwenden von Konfigurationen {#using-configurations}

Die Konfigurationen in AEM basieren auf kontextabhängigen Sling-Konfigurationen. Die Sling-Bundles bieten eine Dienst-API, mit der kontextabhängige Konfigurationen abgerufen werden können. Kontextabhängige Konfigurationen sind Konfigurationen, die sich auf eine Inhaltsressource oder einen Ressourcenbaum beziehen, wie [im vorherigen Beispiel beschrieben](#developer-example) wurde.

Weitere Informationen zu kontextabhängigen Konfigurationen, Beispiele und deren Verwendung finden Sie in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

### ConfMgr-Web-Konsole {#confmgr-web-console}

Zu Debuggings- und Testzwecken gibt es eine **ConfMgr**-Web-Konsole unter `https://<host>:<port>/system/console/conf`, die Konfigurationen für einen bestimmten Pfad/ein bestimmtes Element anzeigen kann.

![ConfMgr](assets/configuration-confmgr.png)

Geben Sie einfach Folgendes an:

* **Inhalts-Pfad**
* **Element**
* **Benutzer**

Um zu sehen, welche Konfigurationen aufgelöst werden und Beispiel-Code erhalten, der diese Konfigurationen auflöst, wählen Sie **Auflösen** aus.

### Web-Konsole für kontextabhängige Konfigurationen {#context-aware-web-console}

Zu Debuggings- und Testzwecken gibt es eine Web-Konsole für **kontextabhängige Konfigurationen** unter `https://<host>:<port>/system/console/slingcaconfig`, mit der Sie kontextabhängige Konfigurationen im Repository abfragen und ihre Eigenschaften anzeigen können.

![Web-Konsole für kontextabhängige Konfigurationen](assets/configuration-context-aware-console.png)

Geben Sie einfach Folgendes an:

* **Inhalts-Pfad**
* **Konfigurationsname**

Um die zugehörigen Kontextpfade und Eigenschaften für die ausgewählte Konfiguration abzurufen, wählen Sie **Auflösen** aus.
