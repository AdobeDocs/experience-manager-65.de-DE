---
title: Bearbeiten der Seiteneigenschaften
description: Definieren Sie die erforderlichen Eigenschaften für eine Seite in Adobe Experience Manager.
exl-id: 3cd9374f-6f16-40fb-97cf-5f9a750b8dd2
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
mini-toc-levels: 2
source-git-commit: d0515a6a3d08e181eada4a22e0d128305148e6ea
workflow-type: ht
source-wordcount: '2477'
ht-degree: 100%

---


# Bearbeiten der Seiteneigenschaften{#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. So können beispielsweise einige Seiten mit einer Live Copy verbunden sein, andere nicht, und die Informationen der Live Copy werden je nach Bedarf verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt.

### Allgemein {#basic}

#### Titel und Tags {#tile}

* **Titel** – Der Titel der Seite wird an verschiedenen Stellen angezeigt. 
   * Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.
   * Dies ist ein Pflichtfeld.
* **Tags** – Hier können Sie der Seite Tags hinzufügen oder Tags aus der Seite entfernen, indem Sie die Liste im Auswahlfeld aktualisieren.
   * Nachdem Sie ein Tag ausgewählt haben, wird es unterhalb des Auswahlfelds aufgelistet. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Sie können ein neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
      * Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
      * Das neue Tag wird mit einem kleinen Stern auf der rechten Seite angezeigt, was bedeutet, dass es sich um ein neues Tag handelt.
   * Mit dem Dropdown-Menü können Sie aus vorhandenen Tags auswählen.
   * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein „x“ angezeigt, mit dem Sie das Tag löschen können.
   * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags.](/help/sites-authoring/tags.md)
* **In der Navigation ausblenden** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Site ein- oder ausgeblendet werden soll.

#### Branding {#branding}

Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

* **Überschreiben**: Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
   * Der Wert wird von allen untergeordneten Seiten geerbt, es sei denn, deren Werte zum **Überschreiben** sind ebenfalls festgelegt.
* **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
   * Der Wert wird nach einem Pipe-Zeichen an den Seitentitel angehängt, z. B. `Cycling Tuscany | Always ready for the WKND`

#### Weitere Titel und Beschreibungen {#more}

* **Seitentitel** – Ein Titel zur Verwendung auf der Seite
   * Wird normalerweise von Titelkomponenten verwendet
   * Wenn dies leer gelassen wird, wird der **Titel** verwendet.
* **Navigationstitel** – Sie können einen eigenen Titel für die Navigation angeben (z. B. wenn Sie einen kürzeren Titel wünschen). 
   * Wenn dies leer gelassen wird, wird der **Titel** verwendet.
* **Untertitel** – Ein Untertitel zur Verwendung auf der Seite
* **Beschreibung** – Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

#### Einschaltzeit/Ausschaltzeit {#on-time}

Die Einschaltzeit/Ausschaltzeit für eine Seite ist eine praktische Methode, um bereits veröffentlichte Inhalte vorübergehend auszublenden. Der Inhalt bleibt auf der Veröffentlichungsinstanz, wenn sie deaktiviert ist. Durch Deaktivieren einer Seite wird die Veröffentlichung des Inhalts nicht rückgängig gemacht.

* **Einschaltzeit**: Zeitpunkt (Datum und Uhrzeit), zu dem die veröffentlichte Seite in der Publishing-Umgebung sichtbar (gerendert) wird. Die Seite muss entweder manuell oder durch vorkonfigurierte automatische Replikation veröffentlicht werden.

   * Wenn sie bereits [veröffentlicht](/help/sites-authoring/publishing-pages.md) wurde, ist diese Seite in der Veröffentlichungsinstanz verfügbar, ruht jedoch (ausgeblendet), bis sie zum angegebenen Zeitpunkt gerendert wird.
   * Wenn die Seite nicht veröffentlicht und [für die automatische Replikation konfiguriert](/help/sites-deploying/replication.md) ist, wird sie automatisch veröffentlicht und dann zum festgelegten Zeitpunkt gerendert.
   * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replikation konfiguriert ist, wird sie nicht automatisch veröffentlicht. Daher wird ein 404-Fehler angezeigt, wenn versucht wird, auf die Seite zuzugreifen.

* **Ausschaltzeit**: Ähnlich wie und häufig in Kombination mit der **Einschaltzeit** wird hier der Zeitpunkt festgelegt, zu dem die Veröffentlichungsumgebung auf der Veröffentlichungsseite ausgeblendet wird.

Lassen Sie diese Felder (**Einschaltzeit** und **Ausschaltzeit**) für Seiten, die Sie sofort veröffentlichen und verfügbar haben möchten und die in der Veröffentlichungsumgebung verfügbar sein sollen, leer, bis sie deaktiviert werden (der Normalfall).

>[!NOTE]
>Wenn entweder die **Einschaltzeit** oder die **Ausschaltzeit** in der Vergangenheit liegt und die automatische Replikation konfiguriert ist, wird die entsprechende Aktion sofort ausgelöst.

>[!TIP]
>
>Einschaltzeiten/Ausschaltzeiten gelten ausschließlich für bereits veröffentlichte Inhalte (entweder manuell oder über automatische Replikation). Aus diesem Grund werden Veröffentlichungs-Workflows, wie die zur Genehmigung von Inhalten, nicht durch Einschaltzeiten/Ausschaltzeiten ausgelöst, und Einschaltzeiten/Ausschaltzeiten wirken sich nicht auf den Veröffentlichungsstatus der Seite aus. Aus diesem Grund sind Einschaltzeiten/Ausschaltzeiten am besten geeignet, um bereits genehmigte und veröffentlichte Inhalte vorübergehend anzuzeigen/auszublenden.
>
>Wenn Sie neue Inhalte mit allen zugehörigen Workflows veröffentlichen oder Inhalte vollständig von Ihrer Site entfernen (Veröffentlichung rückgängig machen) möchten, sollten Sie die [Verwaltung Ihrer Veröffentlichung](/help/sites-authoring/publishing-pages.md#manage-publication) in Erwägung ziehen.

#### Vanity-URL {#vanity-url}

Ermöglicht die Eingabe einer Vanity-URL für diese Seite, sodass Sie eine kürzere bzw. aussagekräftigere URL verwenden können.

Wenn z. B. die Vanity-URL `welcome` auf die Seite gesetzt wird, die durch den Pfad `/v1.0/startpage` für die Website `http://example.com,` identifiziert wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`.

>[!CAUTION]
>
>Vanity-URLs:
>
>* Sie müssen eindeutig sein.
>* unterstützen keine Regex-Muster.
>* sollten nicht auf eine vorhandene Seite eingestellt sein.

Konfigurieren Sie den Dispatcher, um den Zugriff auf Vanity-URLs zu aktivieren. Weitere Einzelheiten finden Sie unter [Aktivieren des Zugriffs auf Vanity-URLs](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#enabling-access-to-vanity-urls-vanity-urls).

* **Hinzufügen** – Tippen oder klicken Sie, um eine Vanity-URL hinzuzufügen.
* **Entfernen** – Tippen oder klicken Sie, um eine Vanity-URL zu entfernen.
  **Vanity-URL umleiten** – Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll oder ob eine Umleitung zur tatsächlichen URL der Seite erfolgen soll.

### Erweitert {#advanced}

#### Einstellungen {#settings}

* **Sprache** – Die Seitensprache
* **Sprachstamm** – Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.
* **Umleiten** – Gibt die Seite an, zu der diese Seite automatisch umgeleitet werden soll.
* **Design** – Gibt das [Design](/help/sites-developing/designer.md) an, das für diese Seite verwendet werden soll.
* **Alias** – Gibt einen Alias an, der für diese Seite verwendet werden soll.
   * Beispiel: Wenn Sie einen Alias `private` für die Seite `/content/wknd/us/en/magazine/members-only` definieren, kann auf diese Seite über `/content/wknd/us/en/magazine/private` zugegriffen werden.
   * Durch die Erstellung eines Alias wird die Eigenschaft `sling:alias`, die sich nur auf die Ressource und nicht auf den Repository-Pfad auswirkt, auf dem Seitenknoten festgelegt.
   * Seiten, auf die im Editor über Aliasnamen zugegriffen wird, können nicht veröffentlicht werden. [Veröffentlichungsoptionen](/help/sites-authoring/publishing-pages.md) im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.
   * Weitere Informationen finden Sie in [Lokalisierte Seitennamen](/help/managing/seo-and-url-management.md#localized-page-names) unter „Best Practices für SEO- und URL-Verwaltung“.

#### Konfiguration {#configuration}

* **Vererbt von &lt;*Pfad*>** – Aktivieren/Deaktivieren Sie die Vererbung der **Cloud-Konfiguration** für die Seite.
* **Cloud-Konfiguration** – Der Pfad zur Konfiguration

#### Vorlageneinstellungen {#templates}

* **Erlaubte Vorlagen**: [Definiert die Liste der Vorlagen, die innerhalb dieses Unterzweigs verfügbar sind](/help/sites-authoring/templates.md#allowingatemplate)

#### Authentifizierungspflicht {#authentication}

* **Aktivieren** – Aktivieren (oder deaktivieren) Sie die Verwendung der Authentifizierung, damit Sie auf die Seite zugreifen können.
* **Anmeldeseite** - Die für die Anmeldung zu verwendende Seite

>[!NOTE]
>
>Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](/help/sites-authoring/editing-page-properties.md#permissions)** definiert.

>[!CAUTION]
>
>Auf der Registerkarte **[Berechtigungen](#permissions)** können Sie CUG-Konfigurationen abhängig vom Vorhandensein des Mixins `granite:AuthenticationRequired` konfigurieren. Wenn Seitenberechtigungen mit veralteten CUG-Konfigurationen konfiguriert werden, die auf dem Vorhandensein der Eigenschaft `cq:cugEnabled` basieren, wird unter **Authentifizierungspflicht** eine Warnmeldung angezeigt und die Option ist nicht bearbeitbar, ebenso wenig wie die [Berechtigungen](/help/sites-authoring/editing-page-properties.md#permissions).
>
>
>In diesem Fall müssen die CUG-Berechtigungen in der [klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) bearbeitet werden.

#### Export {#export}

* **Konfiguration** – Gibt eine Exportkonfiguration an

#### SEO {#seo}

* **Kanonische URL** – Wird zum Überschreiben der kanonischen URL der Seite verwendet
   * Wenn Sie das Feld leer lassen, ist die URL der Seite ihre kanonische URL.
* **Robots-Tags** – Verwenden Sie das Dropdown-Menü zum Auswählen der Robots-Tags, um das Verhalten der Suchmaschinen-Crawler zu steuern.
   * Einige Optionen stehen im Konflikt miteinander, wobei in diesem Fall die Option mit größerer Berechtigung Vorrang hat.
* **Sitemap generieren** – Wenn ausgewählt, wird eine `sitemap.xml` für diese Seite und ihre Unterseiten generiert.

### Bilder {#images}

#### Vorgestelltes Bild {#featured-image}

In diesem Abschnitt wird das anzuzeigende Bild ausgewählt und konfiguriert. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

* **Bild** – Sie können ein Asset **auswählen** oder nach einer hochzuladenden Datei suchen und dann das ausgewählte **bearbeiten** oder **löschen**.
* **Alternativtext** – Ein Text, der die Bedeutung und/oder Funktion des Bildes wiedergibt; wird häufig von Bildschirmlesehilfen verwendet.
* **Vererben – aus dem DAM-Asset stammender Wert** – Wenn diese Option aktiviert ist, wird der Alternativtext mit dem Wert der `dc:description`-Metadaten in DAM befüllt.

#### Miniaturansicht {#thumbnail}

In diesem Abschnitt wird die Miniatur für die Seite ausgewählt und konfiguriert. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

* **Vorschau generieren** – Eine Vorschau der Seite wird erstellt, die Sie als Miniatur verwenden möchten.
* **Bild hochladen** – Ein Bild wird hochgeladen, das Sie als Miniatur verwenden möchten.
* **Bild auswählen** – Ein vorhandenes Asset wird ausgewählt, das Sie als Miniatur verwendet möchten.
* **Zurück zur letzten Version** – Diese Option wird verfügbar, nachdem Sie die Miniatur geändert haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

### Cloud Services {#cloud-services}

* **Cloud-Service-Konfigurationen** - Es wird festgelegt, welche Konfiguration für Cloud-Services für die Seite verwendet werden soll.
* **Vererbt von** – Für Live Copies und Sprachkopien werden Cloud-Konfigurationen standardmäßig von der Blueprint vererbt.
   * Zum Überschreiben der Vererbung deaktivieren

### Personalisierung {#personalization}

#### ContextHub-Konfigurationen {#contexthub}

* **Vererbt von** – ContextHub-Konfigurationen werden standardmäßig von der übergeordneten Seite vererbt.
   * Deaktivieren Sie diese Option, um die Vererbung zu überschreiben.
* **ContextHub-Pfad** – Die [ContextHub-Konfiguration](/help/sites-developing/ch-configuring.md) wird ausgewählt.
* **Segmentpfad** – Der [Segmentpfad](/help/sites-administering/segmentation.md) wird ausgewählt.

#### Konfiguration für Targeting {#targeting}

Wählen Sie eine [Marke, um einen Bereich für das Targeting anzugeben.](/help/sites-authoring/target-adobe-campaign.md)

>[!NOTE]
>Für diese Option muss das Benutzerkonto der `Target Adminstrators`-Gruppe angehören.

### Berechtigungen {#permissions}

Verwenden Sie die Registerkarte **Berechtigungen**, um festzulegen, welche Benutzenden, Gruppen oder [geschlossenen Benutzergruppen (Closed User Groups, CUGs)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html?lang=de) auf die Seite zugreifen und/oder sie ändern können.

* [Berechtigungen hinzufügen](/help/sites-administering/user-group-ac-admin.md)
* [Geschlossene Benutzergruppe bearbeiten](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)
* [Effektive Berechtigungen](/help/sites-administering/user-group-ac-admin.md) anzeigen 

>[!CAUTION]
>
>Auf der Registerkarte **Berechtigungen** können Sie CUG-Konfigurationen abhängig vom Vorhandensein des Mixins `granite:AuthenticationRequired` konfigurieren. Wenn Seitenberechtigungen unter Verwendung veralteter CUG-Konfigurationen konfiguriert werden, die auf dem Vorhandensein der Eigenschaft `cq:cugEnabled` basieren, wird eine Warnmeldung angezeigt, und die CUG-Berechtigungen können nicht bearbeitet werden, ebenso wenig wie die Authentifizierungspflicht auf der Registerkarte [Erweitert](/help/sites-authoring/editing-page-properties.md#advanced).
>
>
>In diesem Fall müssen die CUG-Berechtigungen in der [klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) bearbeitet werden.

>[!NOTE]
>
>Die Registerkarte „Berechtigungen“ gestattet es nicht, leere CUG-Gruppen zu erstellen, was allerdings nützlich sein kann, um allen Benutzenden den Zugriff zu verwehren. Hierfür muss der CRX Explorer verwendet werden. Weitere Informationen finden Sie im Dokument [Verwaltung von Benutzenden, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

### Blueprint {#blueprint}

Diese Registerkarte ist nur für Seiten sichtbar, die als Blueprints dienen. Blueprints dienen als Grundlage für Live Copys und sind Teil des [Multi-Site-Managements](/help/sites-administering/msm.md).

* **Rollout** – Ein Rollout von Blueprint-Inhalten an die Live Copies wird gestartet.
* **Live Copy-Übersicht** – Ein Fenster zum Durchsuchen der Live Copy-Seitenstruktur wird geöffnet.
* **Aktuelle Live Copies** – Eine Liste von Seiten, die auf der ausgewählten Blueprint-Seite basieren (das heißt, Live Copies dieser Seite sind).
* **Rollout-Konfiguration** – Die Rollout-Konfiguration für die Seite wird definiert.

### Live Copy {#live-copy}

Diese Registerkarte ist nur für Seiten sichtbar, die als Live Copys konfiguriert sind. Wie [Blueprints](#blueprint) sind Live Copys Teil des [Multi-Site-Managements.](/help/sites-administering/msm.md)

* **Synchronisieren** – Live Copy wird mit Blueprint synchronisiert; lokale Änderungen werden beibehalten.
* **Zurücksetzen** – Die Live Copy wird auf den Status der Blueprint zurückgesetzt; lokale Änderungen werden entfernt.
* **Aussetzen** – Die Live Copy wird von weiteren Änderungen beim Rollout ausgesetzt.
* **Trennen** – Die Live Copy wird von der Blueprint getrennt.

#### Quelle {#source}

* Zeigt den Pfad der Blueprint für diese Live Copy an

#### Status {#status}

* Listet den aktuellen Live Copy-Status der Seite auf

#### Konfiguration {#live-copy-config}

* **Live Copy-Vererbung** – Wenn diese Option aktiviert ist, gilt die Live Copy-Konfiguration für alle untergeordneten Elemente.
* **Rollout-Konfigurationen aus übergeordnetem Element übernehmen** – Wenn diese Option aktiviert ist, wird die Rollout-Konfiguration von der übergeordneten Seite übernommen.
* **Rollout-Konfiguration auswählen**: Legt fest, unter welchen Umständen Änderungen aus der Blueprint übernommen werden, und ist nur verfügbar, wenn **Rollout-Konfigurationen von übergeordneter Seite erben** nicht aktiviert ist.
* **Liste der ausgeschlossenen Pfade**

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-1}

Sie können Seiteneigenschaften definieren:

* In der **Sites**-Konsole:

   * [Erstellen einer neuen Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page) (eine Untergruppe der Eigenschaften)

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

1. Speichern Sie dann Ihre Aktualisierungen mit **Speichern** und klicken Sie danach auf **Schließen**, um zur Konsole zurückzukehren.

### Beim Bearbeiten einer Seite {#when-editing-a-page}

Beim Bearbeiten einer Seite können Sie mithilfe von **Seiteninformationen** die Seiteneigenschaften definieren:

1. Öffnen Sie die Seite, für die Sie Eigenschaften bearbeiten möchten.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Auswahlmenü zu öffnen:

   ![screen_shot_2018-03-22at095740](assets/screen_shot_2018-03-22at095740.png)

1. Wählen Sie **Eigenschaften öffnen** aus. Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Eigenschaften – geordnet nach der jeweiligen Registerkarte – bearbeiten können. Die folgenden Schaltflächen stehen rechts in der Symbolleiste zur Verfügung:

   * **Abbrechen**
   * **Speichern und schließen**

1. Mit der Schaltfläche **Speichern und schließen** können Sie Änderungen speichern.

### In der Sites-Konsole (mehrere Seiten) {#from-the-sites-console-multiple-pages}

In der **Sites-Konsole** können Sie mehrere Seiten auswählen und dann die Seiteneigenschaften mithilfe der **Ansichtseigenschaften** anzeigen und/oder bearbeiten. Dies wird als Massenbearbeitung von Seiteneigenschaften bezeichnet.

>[!NOTE]
>
>Die Massenbearbeitung von Eigenschaften ist auch für Assets verfügbar. Sie ist ähnlich, unterscheidet sich aber in einigen Punkten. Weitere Informationen dazu finden Sie unter [Bearbeiten von Eigenschaften für mehrere Assets](/help/assets/metadata.md).
>
>Es gibt auch den [Bulk Editor](/help/sites-administering/bulk-editor.md). Mit diesem Editor können Sie mithilfe von GQL (Google Query Language) auf mehreren Seiten nach Inhalten suchen und die Inhalte anschließend direkt im Bulk Editor bearbeiten, bevor Sie die Änderungen an den Ursprungsseiten speichern.

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

Nach dem Start der Massenbearbeitung können Sie Folgendes tun:

* **Anzeigen**

  Wenn Sie Seiteneigenschaften für mehrere Seiten anzeigen, sehen Sie Folgendes:

   * eine Liste der betroffenen Seiten

      * Bei Bedarf können Sie Seiten auswählen oder ihre Auswahl aufheben

   * Registerkarten

      * Wie beim Anzeigen von Eigenschaften für eine einzelne Seite werden die Eigenschaften unter Registerkarten angeordnet.

   * Eine Untergruppe von Eigenschaften

      * Eigenschaften, die auf allen ausgewählten Seiten verfügbar sind und explizit als für die Massenbearbeitung verfügbar definiert wurden, sind sichtbar.
      * Wenn Sie die Seitenauswahl auf eine Seite reduzieren, sind alle Eigenschaften sichtbar.

   * Gemeinsame Eigenschaften mit einem gemeinsamen Wert

      * Nur Eigenschaften mit einem gemeinsamen Wert werden im Ansichtsmodus angezeigt.
      * Wenn es sich um ein mehrwertiges Feld handelt (z. B. Tags), werden die Werte nur angezeigt, wenn *alle* übereinstimmen. Wenn nur einige übereinstimmen, werden sie nur bei der Bearbeitung angezeigt.

  Wenn keine Eigenschaften mit einem gemeinsamen Wert vorhanden sind, wird eine Meldung angezeigt.

* **Bearbeiten**

  Beim Bearbeiten der Seiteneigenschaften für mehrere Seiten:

   * Sie können die Werte in den verfügbaren Feldern aktualisieren.

      * Die neuen Werte werden auf alle gewählten Seiten angewendet, wenn Sie **Fertig** wählen.
      * Wenn es sich um ein mehrwertiges Feld handelt (z. B. Tags), können Sie entweder einen neuen Wert anhängen oder einen gemeinsamen Wert entfernen.

   * Felder, die häufig vorkommen, aber auf den verschiedenen Seiten unterschiedliche Werte haben, werden durch einen speziellen Wert angezeigt, beispielsweise `<Mixed Entries>`.

>[!NOTE]
>
>Die Seitenkomponente kann so konfiguriert werden, dass die für die Massenbearbeitung verfügbaren Felder angegeben werden. Informationen dazu finden Sie unter [Konfigurieren der Seite für Massenbearbeitung von Seiteneigenschaften](/help/sites-developing/bulk-editing.md).
