---
title: Bearbeiten der Seiteneigenschaften
seo-title: Bearbeiten der Seiteneigenschaften
description: Die Eigenschaften einer Seite können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.
seo-description: Die Eigenschaften einer Seite können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.
uuid: 63d37d1b-52da-489d-b02b-e8b3d17571d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 23768c73-ac64-4727-8313-160c8c131b05
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Bearbeiten der Seiteneigenschaften{#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt:

### Einfach {#basic}

* **Titel**

   Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.

   Dies ist ein Pflichtfeld.

* **Tags**

   Hier können Sie der Seite Tags hinzufügen (oder davon entfernen), indem Sie die Liste im Auswahlfeld aktualisieren:

   * Wenn Sie ein Tag ausgewählt haben, wird es unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Ein vollkommen neues Tag kann angegeben werden, indem Sie den Namen in ein leeres Auswahlfeld eingeben.

      Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken. Das neue Tag wird dann in einem Feld angezeigt. Ein kleiner Stern auf der rechten Seite markiert es als neues Tag.

   * In der Dropdown-Liste können Sie aus vorhandenen Tags auswählen.
   * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein x angezeigt, mit dessen Hilfe Sie das Tag löschen können.

* **In Navigation ausblenden**

   Ein Umschalter gibt an, ob die Seite in der Seitennavigation ein- oder ausgeblendet sein soll.

* **Seitentitel**

   Ein Titel zur Verwendung auf der Seite.

* **Navigationstitel**

   Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten). Wenn dieses Feld leer bleibt, wird der **Titel** verwendet.

* **Untertitel**

   Ein Untertitel zur Verwendung auf der Seite.

* **Beschreibung**

   Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit**

   Datum und Uhrzeit der Aktivierung der veröffentlichten Seite. Nach der Veröffentlichung ruht die Seite bis zu diesem Zeitpunkt. 

   Lassen Sie diese Felder leer, wenn die Seite sofort veröffentlicht werden soll (der Normalfall).

* **Ausschaltzeit**

   Datum und Uhrzeit der Deaktivierung der veröffentlichten Seite.

   Lassen Sie diese Felder wiederum leer, wenn die Seite sofort veröffentlicht werden soll.

* **Vanity-URL**

   Ermöglicht die Eingabe einer Vanity-URL für diese Seite. Dadurch können Sie eine kürzere, ausdrucksstärkere URL verwenden.

   For example, if the Vanity URL is set to w `elcome`to the page identified by the path / `v1.0/startpage`for the website h `ttp://example.com,` then h `ttp://example.com/welcome`would be the vanity URL of h `ttp://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Vanity-URLs:
   >
   >* müssen eindeutig sein, Sie müssen also darauf achten, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
   >* unterstützen keine Regex-Muster.


* **Vanity-URL umleiten**

   Gibt an, ob für die Seite eine Vanity-URl verwendet werden soll.

### Erweitert {#advanced}

* **Sprache**

   Die Seitensprache.

* **Umleiten**

   Geben Sie eine Seite an, zu der die Seite automatisch umgeleitet werden soll.

* **Design**

   Geben Sie das [Design](/help/sites-developing/designer.md) an, das für diese Seite verwendet werden soll.

* **Alias**

   Geben Sie einen Alias an, der für diese Seite verwendet werden soll.

* **Geschlossene Benutzergruppe aktivieren**

   Aktiviert (oder deaktiviert) die Verwendung [geschlossener Benutzergruppen](/help/sites-administering/cug.md) (CUGs).

* **Anmeldeseite**

   Die für die Anmeldung zu verwendende Seite.

* **Zugelassene Gruppen**

   Gruppen, die sich bei der CUG anmelden können.

* **Bereich**

   Bereichsname für die CUG.

* **Konfiguration exportieren**

   Geben Sie eine Exportkonfiguration an.

### Miniaturansicht {#thumbnail}

* **Seitenminiatur**

   Zeigt das Miniaturbild der Seite an. Sie haben folgende Möglichkeiten:

   * **Vorschau generieren**

      Erstellen Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.

   * **Bild hochladen**

      Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.

### Cloud-Services {#cloud-services}

* **Cloud-Services**

   Legen Sie Eigenschaften für [Cloud-Services](/help/sites-developing/extending-cloud-config.md) fest.

### Personalisierung  {#personalization}

* **Personalisierung**

   Wählen Sie eine [Marke aus, um einen Bereich für das Targeting anzugeben](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

### Berechtigungen {#permissions}

* **Berechtigungen** (Touch-optimierte Benutzeroberfläche)

   Zeigen Sie die [effektiven Berechtigungen an und fügen Sie neue Berechtigungen hinzu](/help/sites-administering/user-group-ac-admin.md).

### Blueprint {#blueprint}

* **Blueprint**

   Legen Sie Eigenschaften für eine Blueprint-Seite fest, die für die [Verwaltung mehrerer Websites](/help/sites-administering/msm.md) verwendet wird. Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.

### Live Copy {#live-copy}

* **Live Copy**

   Legen Sie Eigenschaften für eine Live Copy-Seite fest, die für die [Verwaltung mehrerer Websites](/help/sites-administering/msm.md) verwendet wird. Steuert die Umstände, unter denen Änderungen von der Blueprint-Seite propagiert werden.

### Site-Struktur {#site-structure}

* Geben Sie Links zu Seiten an, die siteübergreifende Funktionalität bieten, z. B. **Anmeldungsseite**, **Offline-Seite** und andere.

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-2}

### Bearbeiten von Seiteneigenschaften für eine bestimmte Seite {#editing-page-properties-for-a-specific-page}

Durch Seiteneigenschaften werden verschiedene Parameter einer Seite festgelegt, z. B. Titel, wann die Seite auf der Website angezeigt wird usw.

1. Öffnen Sie die zu bearbeitende Seite.

1. Öffnen Sie im Sidekick die Registerkarte **Seite** und wählen Sie anschließend **Seiteneigenschaften...**

   Ein Dialogfeld mit mehreren Registerkarten wird geöffnet.

1. Nehmen Sie die erforderlichen Änderungen vor und klicken Sie dann auf **OK**, um zu speichern.

