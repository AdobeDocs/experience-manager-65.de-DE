---
title: Bearbeiten der Eigenschaften von Inhaltsseiten
description: Definieren Sie die erforderlichen Eigenschaften für eine Seite in Adobe Experience Manager.
exl-id: 3cd9374f-6f16-40fb-97cf-5f9a750b8dd2
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '1872'
ht-degree: 63%

---

# Bearbeiten der Seiteneigenschaften{#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden, andere nicht und die Live Copy-Informationen werden entsprechend verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt.

### Einfach {#basic}

* **Titel**

  Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.

  Dies ist ein Pflichtfeld.

* **Tags**

  Hier können Sie Tags zur Seite hinzufügen oder daraus entfernen, indem Sie die Liste im Auswahlfeld aktualisieren:

   * Nach Auswahl eines Tags wird dieses unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Sie können ein neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.

      * Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
      * Das neue Tag wird mit einem kleinen Stern auf der rechten Seite angezeigt, der angibt, dass es sich um ein neues Tag handelt.

   * Mit der Dropdown-Funktion können Sie aus vorhandenen Tags auswählen.
   * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein „x“ angezeigt, mit dem Sie das Tag löschen können.

  Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

* **In Navigation ausblenden**

  Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.

* **Branding**

  Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

   * **Überschreiben**: Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
      * Der Wert wird von allen untergeordneten Seiten geerbt, es sei denn, deren Werte für **Überschreiben** sind auch eingestellt.
   * **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
      * Der Wert wird nach einem Pipe-Zeichen an den Seitentitel angehängt, z. B. „Cycling Tuscany | Always ready for the WKND“.
* **Seitentitel**

  Ein Titel zur Verwendung auf der Seite. Wird normalerweise von Titelkomponenten verwendet. Wenn dies leer gelassen wird, wird der **Titel** verwendet.

* **Navigationstitel**

  Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten). Wenn dies leer gelassen wird, wird der **Titel** verwendet.

* **Untertitel**

  Ein Untertitel zur Verwendung auf der Seite.

* **Beschreibung**

  Ihre Beschreibung der Seite, ihr Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit**

  Datum und Uhrzeit der Aktivierung der veröffentlichten Seite. Nach der Veröffentlichung ruht diese Seite bis zum angegebenen Zeitpunkt.

  Lassen Sie diese Felder für Seiten leer, die Sie sofort veröffentlichen möchten (im normalen Szenario).

* **Ausschaltzeit**

  Der Zeitpunkt, zu dem die veröffentlichte Seite deaktiviert wird.

  Lassen Sie diese Felder bei sofortiger Ausführung leer.

* **Vanity-URL**

  Geben Sie eine Vanity-URL für diese Seite ein, die Ihnen eine kürzere und/oder ausdrucksstärkere URL erlauben kann.

  Wenn z. B. die Vanity-URL `welcome` auf die Seite gesetzt wird, die durch den Pfad `/v1.0/startpage` für die Website `http://example.com,` identifiziert wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`.

  >[!CAUTION]
  >
  >Vanity-URLs:
  >
  >* Muss eindeutig sein. Stellen Sie sicher, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
  >* unterstützen keine Regex-Muster.
  >* sollten nicht auf eine vorhandene Seite eingestellt sein.
  >

  Konfigurieren Sie den Dispatcher, um den Zugriff auf Vanity-URLs zu aktivieren. Weitere Einzelheiten finden Sie unter [Aktivieren des Zugriffs auf Vanity-URLs](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#enabling-access-to-vanity-urls-vanity-urls).

* **Vanity-URL umleiten**

  Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.

### Erweitert {#advanced}

* **Sprache**

  Die Seitensprache.

* **Sprach-Stamm**

  Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.

* **Umleiten**

  Geben Sie die Seite an, zu der diese Seite automatisch umgeleitet werden soll.

* **Design**

  Geben Sie das [Design](/help/sites-developing/designer.md) an, das für diese Seite verwendet werden soll.

* **Alias**

  Geben Sie einen Alias an, der für diese Seite verwendet werden soll.

   * Beispiel: Wenn Sie einen Alias `private` für die Seite `/content/wknd/us/en/magazine/members-only` definieren, kann auf diese Seite über `/content/wknd/us/en/magazine/private` zugegriffen werden.
   * Durch die Erstellung eines Alias wird die Eigenschaft `sling:alias`, die sich nur auf die Ressource und nicht auf den Repository-Pfad auswirkt, auf dem Seitenknoten festgelegt.
   * Seiten, auf die Alias im Editor zugreifen, können nicht veröffentlicht werden. [Veröffentlichungsoptionen](/help/sites-authoring/publishing-pages.md) im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.
   * Weitere Informationen finden Sie unter [Lokalisierte Seitennamen unter Best Practices für SEO und URL-Verwaltung](/help/managing/seo-and-url-management.md#localized-page-names).

* **Vererbt von &lt;*path*>**

  Gibt an, ob die Seite vererbt wurde und von wo.

* **Cloud-Konfiguration**

  Der Pfad zur Konfiguration.

* **Zugelassene Vorlagen**

  [Liste verfügbarer Vorlagen definieren](/help/sites-authoring/templates.md#allowingatemplate) innerhalb dieser Unterverzweigung.

* **Aktivieren** (Authentifizierungspflicht)

  Aktivieren (oder deaktivieren) Sie die Authentifizierung, damit Sie auf die Seite zugreifen können.

  >[!NOTE]
  >
  >Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](/help/sites-authoring/editing-page-properties.md#permissions)** definiert.

  >[!CAUTION]
  >
  >Die **[Berechtigungen](/help/sites-authoring/editing-page-properties.md#main-pars-procedure-949394300)** -Registerkarte ermöglicht die Bearbeitung von CUG-Konfigurationen basierend auf dem Vorhandensein der `granite:AuthenticationRequired` Mixin. Wenn Seitenberechtigungen mit veralteten CUG-Konfigurationen konfiguriert werden, die auf dem Vorhandensein von `cq:cugEnabled` -Eigenschaft verwenden, wird eine Warnmeldung unter **Authentifizierungspflicht** und die Option nicht bearbeitet werden kann, sind die [Berechtigungen](/help/sites-authoring/editing-page-properties.md#permissions) bearbeitbar.
  >
  >
  >In diesem Fall müssen die CUG-Berechtigungen in der [klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) bearbeitet werden.

* **Anmeldeseite**

  Die Seite, die für die Anmeldung verwendet werden soll.

* **Exportkonfiguration**

  Geben Sie eine Exportkonfiguration an.

### Miniaturansicht  {#thumbnail}

Zeigt das Miniaturbild der Seite an. Sie haben folgende Möglichkeiten:

* **Vorschau generieren**

  Erstellen Sie eine Vorschau der Seite, die Sie als Miniaturansicht verwenden möchten.

* **Bild hochladen**

  Laden Sie ein Bild hoch, das Sie als Miniaturansicht verwenden möchten.

* **Bild auswählen**

  Wählen Sie ein vorhandenes Asset aus, das Sie als Miniaturansicht verwenden möchten.

* **Zurück zur letzten Version**

  Diese Option wird verfügbar, nachdem Sie die Miniaturansicht geändert haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

### Social Media {#social-media}

* **Freigabe in Social Media**

  Definiert die auf der Seite verfügbaren Freigabeoptionen. Stellt die Optionen bereit, die für die [Kernkomponente freigeben](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/sharing.html?lang=en).

   * **Benutzerfreigabe für Facebook aktivieren**
   * **Benutzerfreigabe für Pinterest aktivieren**
   * **Bevorzugte XF-Variante**
Experience Fragment-Variante definieren, die zum Generieren von Metadaten für eine Seite verwendet wird

### Cloud Services {#cloud-services}

* **Cloud Services**

  Definieren Sie Eigenschaften für [Cloud-Services](/help/sites-developing/extending-cloud-config.md).

### Personalisierung {#personalization}

* **ContextHub-Konfigurationen**

  Wählen Sie die [ContextHub-Konfiguration](/help/sites-developing/ch-configuring.md) und den [Segmentpfad](/help/sites-administering/segmentation.md).

* **Konfiguration für Targeting**

  Wählen Sie eine [Marke, um einen Bereich für das Targeting anzugeben](/help/sites-authoring/target-adobe-campaign.md).

  >[!NOTE]
  >Für diese Option muss das Benutzerkonto der `Target Adminstrators`-Gruppe angehören.

### Berechtigungen {#permissions}

* **Berechtigungen**

  Auf dieser Registerkarte können Sie:

   * [Berechtigungen hinzufügen](/help/sites-administering/user-group-ac-admin.md)
   * [Geschlossene Benutzergruppe bearbeiten](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)

   * [Effektive Berechtigungen](/help/sites-administering/user-group-ac-admin.md) anzeigen 

  >[!CAUTION]
  >
  >Auf der Registerkarte **Berechtigungen** können Sie CUG-Konfigurationen abhängig vom Vorhandensein des Mixins `granite:AuthenticationRequired` konfigurieren. Wenn Seitenberechtigungen mit veralteten CUG-Konfigurationen konfiguriert werden, die auf dem Vorhandensein von `cq:cugEnabled` -Eigenschaft, wird eine Warnmeldung angezeigt und die CUG-Berechtigungen können nicht bearbeitet werden. Die Authentifizierungspflicht für [Erweitert](/help/sites-authoring/editing-page-properties.md#advanced) Registerkarte bearbeitbar.
  >
  >
  >In diesem Fall müssen die CUG-Berechtigungen in der [klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) bearbeitet werden.

  >[!NOTE]
  >
  >Die Registerkarte „Berechtigungen“ gestattet es nicht, leere CUG-Gruppen zu erstellen, was allerdings nützlich sein kann, um allen Benutzenden den Zugriff zu verwehren. Dazu muss CRX Explorer verwendet werden. Siehe Dokument . [Verwaltung von Benutzern, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md) für weitere Informationen.

### Blueprint {#blueprint}

* **Blueprint**

  Legen Sie Eigenschaften für eine Blueprint-Seite fest, die für die [Verwaltung mehrerer Websites](/help/sites-administering/msm.md) verwendet wird. Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.

### Live Copy {#live-copy}

* **Live Copy**

  Legen Sie Eigenschaften für eine Live Copy-Seite fest, die für die [Verwaltung mehrerer Websites](/help/sites-administering/msm.md) verwendet wird. Steuert die Umstände, unter denen Änderungen von der Blueprint-Seite propagiert werden.

### Site-Struktur {#site-structure}

* Stellen Sie Links zu Seiten bereit, die Site-weite Funktionen bieten, wie z. B. **Anmeldeseite**, **Offline-Seite**, unter anderem.

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-1}

Sie können Seiteneigenschaften definieren:

* In der Konsole **Sites**:

   * [beim Erstellen einer neuen Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page) (ein Teil der Eigenschaften)

   * durch Klicken oder Tippen auf **Eigenschaften**

      * Für eine einzelne Seite
      * Für mehrere Seiten (nur eine Teilmenge der Eigenschaften steht zur Massenbearbeitung zur Verfügung)

* Im Seiteneditor:

   * mithilfe der Option **Seiteninformationen** (anschließend **Eigenschaften öffnen**)

### In der Sites-Konsole (einzelne Seite) {#from-the-sites-console-single-page}

durch Klicken oder Tippen auf **Eigenschaften**, um die Seiteneigenschaften festzulegen:

1. Navigieren Sie in der **Sites-Konsole** zu der Seite, für die Sie Eigenschaften anzeigen und bearbeiten möchten.

1. Wählen Sie die Option **Eigenschaften** für die gewünschte Seite aus, indem Sie wahlweise Folgendes verwenden:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#selectionmode)

   Die Seiteneigenschaften werden in den entsprechenden Registerkarten angezeigt.

1. Sie können die Eigenschaften nach Bedarf anzeigen oder bearbeiten.

1. Dann verwenden Sie **Speichern** Speichern Sie Ihre Aktualisierungen, gefolgt von **Schließen** damit Sie zur Konsole zurückkehren können.

### Beim Bearbeiten einer Seite {#when-editing-a-page}

Beim Bearbeiten einer Seite können Sie **Seiteninformationen** um die Seiteneigenschaften zu definieren:

1. Öffnen Sie die Seite, für die Sie Eigenschaften bearbeiten möchten.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Auswahlmenü zu öffnen:

   ![screen_shot_2018-03-22at095740](assets/screen_shot_2018-03-22at095740.png)

1. Auswählen **Eigenschaften öffnen** und ein Dialogfeld geöffnet, in dem Sie die Eigenschaften bearbeiten können, sortiert nach der entsprechenden Registerkarte. Die folgenden Schaltflächen stehen rechts in der Symbolleiste zur Verfügung:

   * **Abbrechen**
   * **Speichern und schließen**

1. Mit der Schaltfläche **Speichern und schließen** können Sie Änderungen speichern.

### In der Sites-Konsole (mehrere Seiten) {#from-the-sites-console-multiple-pages}

Aus dem **Sites** Console können Sie mehrere Seiten auswählen und dann **Eigenschaften anzeigen** , um die Seiteneigenschaften anzuzeigen und/oder zu bearbeiten. Dies wird als Massenbearbeitung von Seiteneigenschaften bezeichnet.

>[!NOTE]
>
>Die Massenbearbeitung von Eigenschaften ist auch für Assets verfügbar. Sie ist ähnlich, unterscheidet sich aber in einigen Punkten. Weitere Informationen dazu finden Sie unter [Bearbeiten von Eigenschaften für mehrere Assets](/help/assets/metadata.md).
>
>Es gibt auch die [Bulk Editor](/help/sites-administering/bulk-editor.md). Mit diesem Editor können Sie mithilfe von GQL (Google Query Language) aus mehreren Seiten nach Inhalten suchen und den Inhalt dann direkt mit dem Bulk Editor bearbeiten, bevor Sie Ihre Änderungen an den ursprünglichen Seiten speichern.

Sie können mehrere Seiten für die Massenbearbeitung mit verschiedenen Methoden auswählen, darunter:

* Beim Durchsuchen der **Sites**-Konsole
* Nach Verwendung von **Suche**, um einen Seitensatz zu finden

![epp-01](assets/epp-01.png)

Nach Auswahl der Seiten und anschließendem Klicken oder Tippen auf die Option **Eigenschaften** werden die Masseneigenschaften angezeigt:

![epp-02](assets/epp-02.png)

Sie können nur Massenbearbeitungen von Seiten durchführen, die:

* den gleichen Ressourcentyp haben
* nicht Teil einer Live Copy sind

   * Ist eine der Seiten Teil einer Live Copy, wird beim Öffnen der Eigenschaften eine Meldung angezeigt.

Nachdem Sie die Massenbearbeitung eingegeben haben, haben Sie folgende Möglichkeiten:

* **Anzeigen**

  Beim Anzeigen der Seiteneigenschaften für mehrere Seiten sehen Sie Folgendes:

   * eine Liste der betroffenen Seiten

      * Sie können die Auswahl bei Bedarf aufheben oder auswählen.

   * Registerkarten

      * Wie beim Anzeigen von Eigenschaften für eine einzelne Seite werden die Eigenschaften unter Registerkarten angeordnet.

   * Eine Untergruppe von Eigenschaften

      * Eigenschaften, die auf allen ausgewählten Seiten verfügbar sind und explizit als für die Massenbearbeitung verfügbar definiert wurden, sind sichtbar.
      * Wenn Sie die Seitenauswahl auf eine Seite reduzieren, sind alle Eigenschaften sichtbar.

   * Gemeinsame Eigenschaften mit einem gemeinsamen Wert

      * Nur Eigenschaften mit einem gemeinsamen Wert werden im Ansichtsmodus angezeigt.
      * Wenn das Feld mehrwertig ist (z. B. Tags), werden Werte nur angezeigt, wenn *all* sind häufig. Wenn nur einige häufig vorkommen, werden sie nur bei der Bearbeitung angezeigt.

  Wenn keine Eigenschaften mit einem gemeinsamen Wert vorhanden sind, wird eine Meldung angezeigt.

* **Bearbeiten**

  Beim Bearbeiten der Seiteneigenschaften für mehrere Seiten:

   * Sie können die Werte in den verfügbaren Feldern aktualisieren.

      * Die neuen Werte werden auf alle gewählten Seiten angewendet, wenn Sie **Fertig** wählen.
      * Wenn es sich um ein mehrwertiges Feld handelt (z. B. Tags), können Sie entweder einen neuen Wert anhängen oder einen gemeinsamen Wert entfernen.

   * Gemeinsame Felder, die unterschiedliche Werte auf den verschiedenen Seiten aufweisen, werden durch einen speziellen Wert wie den Text gekennzeichnet `<Mixed Entries>`.

>[!NOTE]
>
>Die Seitenkomponente kann so konfiguriert werden, dass die für die Massenbearbeitung verfügbaren Felder angegeben werden. Informationen dazu finden Sie unter [Konfigurieren der Seite für Massenbearbeitung von Seiteneigenschaften](/help/sites-developing/bulk-editing.md).
