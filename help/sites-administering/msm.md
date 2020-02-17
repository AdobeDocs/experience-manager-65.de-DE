---
title: '"Wiederverwenden von Inhalten: Multi Site Manager und Live Copy"'
seo-title: '"Wiederverwenden von Inhalten: Multi Site Manager und Live Copy"'
description: Erfahren Sie mehr über die Wiederverwendung von Inhalten mit Live Copies und dem Multi Site Manager.
seo-description: Erfahren Sie mehr über die Wiederverwendung von Inhalten mit Live Copies und dem Multi Site Manager.
uuid: 9f955226-8fc9-4357-b90c-c6896b0dc4b4
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c21debc3-ecf4-4aa9-ab5a-18ddd5cf2fff
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Wiederverwenden von Inhalten: Multi Site Manager und Live Copy{#reusing-content-multi-site-manager-and-live-copy}

Multi Site Manager (MSM) ermöglicht Ihnen die Verwendung derselben Website-Inhalte an mehreren Standorten. MSM verwendet seine Live Copy-Funktion, um Folgendes zu erreichen:

* Mit MSM können Sie:

   * Erstellen von Inhalten einmal und dann
   * in andere Bereiche derselben Site oder anderer Sites kopieren und wiederverwenden ([Live Copies](#live-copies)).

* MSM behält dann die (Live-)Beziehungen zwischen Ihren Quellinhalten und deren Live Copies bei, sodass:

   * Die Quelle und die Live Copies synchronisiert werden, wenn Sie Änderungen an den Quellinhalten vornehmen (um diese Änderungen auch auf die Live Copies anzuwenden).
   * Sie Anpassungen am Inhalt der Live Copies vornehmen können, indem Sie die Live-Beziehung zu einzelnen Unterseiten und/oder Komponenten trennen. Hierdurch werden Änderungen an der Quelle nicht mehr auf die Live Copy angewendet.

Die entsprechenden Themen werden auf dieser Seite sowie auf den folgenden Seiten behandelt:

* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [Konsole „Live Copy-Übersicht“](/help/sites-administering/msm-livecopy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](/help/sites-administering/msm-sync.md)
* [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md)
* [Best Practices für MSM](/help/sites-administering/msm-best-practices.md)

## Mögliche Szenarien {#possible-scenarios}

Es gibt viele Nutzungsszenarien für MSM und Live Copies. Einige der Szenarien umfassen Folgendes:

* **Multinational – Globale zu lokalen Unternehmen**

   Ein typisches, von MSM unterstütztes Nutzungsszenario ist die Wiederverwendung von Inhalten auf verschiedenen multinationalen Sites in derselben Sprache. Dies ermöglicht die Wiederverwendung der Kerninhalte und lässt gleichzeitig Abweichungen für verschiedene Länder zu.

   So wurde zum Beispiel der englische Abschnitt der We.Retail-Referenzsite für Kunden in den USA erstellt. Die meisten Inhalte auf dieser Site können auch für andere We.Retail-Websites verwendet werden, die sich an englischsprachige Kunden aus verschiedenen Ländern und Kulturkreisen richten. Der Kerninhalt bleibt auf allen Sites gleich, wobei regionale Anpassungen vorgenommen werden können.

   Die folgende Struktur kann für Sites in den Vereinigten Staaten, Großbritannien, Kanada und Australien verwendet werden:

   ```xml
   /content
       |- we.retail
           |- language-masters
               |- en
       |- we.retail
           |- us
               |- en
       |- we.retail
           |- gb
               |- en
       |- we.retail
           |- ca
               |- en
       |- we.retail
           |- au
               |- en
   ```

   >[!NOTE]
   >
   >MSM übersetzt die Inhalte nicht. Er wird zur Erstellung der erforderlichen Struktur und zur Bereitstellung von Inhalten verwendet.
   >
   >
   >See [Translating Content for Multilingual Sites](/help/sites-administering/translation.md) if you want to extend such an example.

* **National – Zentrale zu Zweigstellen**

   Alternativ dazu möchte ein Unternehmen mit einem Händlernetzwerk vielleicht separate Websites für seine einzelnen Verkaufsvertretungen, von denen jede eine Variante der von der Zentrale bereitgestellten Haupt-Site darstellt. Dies kann für ein einziges Unternehmen mit mehreren regionalen Niederlassungen oder für ein landesweites Franchisesystem mit einem zentralen Franchisegeber und mehreren lokalen Franchisenehmern eingesetzt werden.

   Die Zentrale kann die Kerninformationen bereitstellen und die regionalen Standorte können lokale Informationen wie Kontaktdetails, Geschäftszeiten und Veranstaltungen ergänzen.

   ```xml
   /content
       |- head-office-Berlin
       |- branch-Hamburg
       |- branch-Stuttgart
       |- branch-Munich
       |- branch-Frankfurt
   ```

* **Mehrere Versionen**

   Oder Sie können MSM zur Erstellung verschiedener Versionen eines spezifischen Unterzweigs verwenden, wie zum Beispiel einer Support-Unterwebsite mit Details zu den verschiedenen Versionen eines bestimmten Produkts. Die Basisinformationen bleiben hier gleich und nur die aktualisierten Merkmale müssen geändert werden:

   ```xml
   /content
       |- support
           |- product X
               |- v5.0
               |- v4.0
               |- v3.0
               |- v2.0
               |- v1.0
   ```

   >[!NOTE]
   >
   >Bei einem solchen Szenario stellt sich immer die Frage, ob eine direkte Kopie erstellt oder ob Live Copies verwendet werden sollen:
   >
   >Hierbei muss abgewogen werden:
   >
   >  * welcher Anteil des Kerninhalts über die diversen Versionen hinweg aktualisiert werden muss
   >
   >und
   >
   >  * welcher Anteil der einzelnen Kopien angepasst werden muss


## MSM über die Benutzeroberfläche {#msm-from-the-ui}

MSM ist in der Benutzeroberfläche mit verschiedenen Optionen aus der entsprechenden Konsole direkt zugänglich. Um eine Einführung bereitzustellen, werden im Folgenden die Hauptstandorte aufgeführt:

* **Website erstellen** (**Sites**)

   * MSM hilft Ihnen bei der Verwaltung mehrerer Websites mit gemeinsamen Inhalten. Websites werden für internationale Zielgruppen oft so bereitgestellt, dass die meisten Inhalte für alle Länder gleich sind und eine Teilmenge der Inhalte sich speziell auf die einzelnen Länder bezieht. MSM ermöglicht Ihnen die [Erstellung von Live Copies, die automatisch eine oder mehrere Websites basierend auf Ihrer Quell-Site aktualisieren](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Dies hilft Ihnen auch dabei, eine gemeinsame Basisstruktur zu erzwingen, die gemeinsamen Inhalte auf mehreren Sites zu nutzen, ein gemeinsames Erscheinungsbild zu erreichen und die Maßnahmen auf die Verwaltung der Inhalte zu konzentrieren, die sich auf den verschiedenen Sites tatsächlich unterscheiden.
   * Für die Angabe der Quelle ist eine vordefinierte Blueprint-Konfigurationen erforderlich.
   * Es wird eine Live Copy der (vordefinierten) Quelle erstellt.
   * Stellt dem Benutzer eine **Rollout**-Schaltfläche bereit.

* **Live Copy erstellen** (**Sites**)

   * MSM ermöglicht Ihnen die [Erstellung einer (einmaligen) Ad-hoc-Live Copy der einzelnen Seite oder des Unterzweigs einer Website](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page), wie zum Beispiel das Duplizieren eines Unterzweigs zur Bereitstellung von Informationen zu einer neuen/aktualisierten Version eines Produkts.
   * Erstellt eine Ad-hoc-Live Copy (keine Blueprint-Konfiguration erforderlich).
   * Kann verwendet werden, um (sofort) eine Live Copy einer beliebigen Seite/eines beliebigen Zweigs zu erstellen.
   * Requires **Synchronize** (does not provide the **Rollout** button).

* **Eigenschaften anzeigen** (**Sites**)

   * Where appropriate, this option helps you [monitor your live copy](/help/sites-administering/msm-livecopy.md#monitoring-your-live-copy) by providing information on the related **Live Cop** y or **Blueprint**.

* **Verweise** (**Sites**)

   * The [References](/help/sites-authoring/basic-handling.md#references) rail provides information about **Live Copies** together with access to appropriate actions.

* **Live Copy-Übersicht** (**Sites**)

   * Diese Konsole ermöglicht Ihnen die [Ansicht und Verwaltung Ihres Blueprints und dessen Live Copies](/help/sites-administering/msm-livecopy-overview.md).

* **Blueprints** (**Tools** – **Sites**)

   * Diese Konsole ermöglicht Ihnen die [Erstellung und Verwaltung Ihrer Blueprint-Konfigurationen](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

>[!NOTE]
>
>Aspekte der MSM-Funktion werden in verschiedenen anderen AEM-Funktionen eingesetzt (wie zum Beispiel Starts, Katalog). In diesen Fällen wird die Live Copy von dieser Funktion verwaltet.

### Verwendete Bedingungen {#terms-used}

Als Einführung stellt die folgende Tabelle einen Überblick über die wichtigsten MSM-Begriffe bereit. Diese werden in den folgenden Abschnitten und auf den folgenden Seiten noch detaillierter erläutert:

<table>
 <tbody>
  <tr>
   <td><strong>Term</strong></td>
   <td><strong>Definition</strong></td>
   <td><strong>Weitere Einzelheiten</strong></td>
  </tr>
  <tr>
   <td><strong>Quelle</strong></td>
   <td>Die Originalseiten.</td>
   <td>Synonym für Blueprints- und/oder Blueprint-Seiten.</td>
  </tr>
  <tr>
   <td><strong>Live Copy</strong></td>
   <td>Die Kopie (der Quelle), die durch Synchronisierungsaktionen gemäß den Rollout-Konfigurationen verwaltet wird. </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Live Copy-Konfiguration</strong></td>
   <td>Definition der Konfigurationsdetails für eine Live-Kopie.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Live-Beziehung</strong><br /> </td>
   <td>Wirksame Definition der Vererbung für eine bestimmte Ressource; die Verbindung(en) zwischen der Quelle und den Live-Kopien.<br /> </td>
   <td>Stellt sicher, dass Änderungen an der Quelle mit der Live-Kopie synchronisiert werden können.</td>
  </tr>
  <tr>
   <td><strong>Blaupause</strong></td>
   <td>Synonym mit Quelle.</td>
   <td>Kann durch eine Blueprint-Konfiguration definiert werden.</td>
  </tr>
  <tr>
   <td><strong>Blueprint-Konfiguration</strong></td>
   <td>Vordefinierte Konfiguration zur Angabe eines Quellpfads.</td>
   <td>Wenn in einer Blueprint-Konfiguration auf eine Blueprint-Seite verwiesen wird, steht der Befehl "Rollout"zur Verfügung.</td>
  </tr>
  <tr>
   <td><strong>Synchronisierung</strong></td>
   <td>Der allgemeine Begriff für die Synchronisierung von Inhalten zwischen der Quelle und den Live-Kopien (sowohl durch <strong>Rollout</strong> als auch durch <strong>Synchronisieren</strong>).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rollout</strong><br /> </td>
   <td>Synchronisiert von der Quelle zur Livecopy.<br /> Kann von einem Autor (auf einer Blueprint-Seite) oder von einem Systemereignis (wie in der Rollout-Konfiguration definiert) ausgelöst werden.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rollout-Konfiguration</strong></td>
   <td>Regeln, die bestimmen, welche Eigenschaften synchronisiert werden, wie und wann.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Synchronisieren</strong></td>
   <td>Eine manuelle Anforderung der Synchronisierung, die von den Livecopy-Seiten erfolgt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Vererbung</strong></td>
   <td>Eine Live Copy-Seite/Komponente erbt Inhalt von ihrer Quellseite/Komponente, wenn eine Synchronisierung stattfindet.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Aussetzen</strong></td>
   <td>Entfernt vorübergehend die Live-Beziehung zwischen einer Live-Kopie und der zugehörigen Blueprint-Seite.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Trennen</strong></td>
   <td>Entfernt dauerhaft die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Zurücksetzen</strong></td>
   <td><p>Setzen Sie eine Live Copy-Seite zurück, um:</p>
    <ul>
     <li>alle abgebrochenen Vererbungsvorgänge zu entfernen und<br /> </li>
     <li>die Seite in denselben Status wie die Quellseite zurückzuversetzen.</li>
    </ul> <p>Eine Rücksetzung wirkt sich auf alle von Ihnen durchgeführten Änderungen an den Seiteneigenschaften, am Absatzsystem und an den Komponenten aus.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Langsam</strong></td>
   <td>Eine Live-Kopie einer einzelnen Seite.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Tief</strong></td>
   <td>Eine Live-Kopie einer Seite mit ihren untergeordneten Seiten.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>See [Overview of the Java API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) for the object names.

## Live Copies {#live-copies}

Eine MSM-Live Copy ist eine Kopie von spezifischem Site-Inhalt, zu dem eine Live-Beziehung mit der Originalquelle gepflegt wird.

* Die Live Copy übernimmt Inhalte aus ihrer Quelle.
* Die Synchronisierung führt die tatsächliche Übertragung von Inhalten durch, wenn Änderungen an der Quelle vorgenommen werden.
* Eine Live Copy kann als eines der Folgenden betrachtet werden:

   * Flach: eine einzelne Seite
   * Tief: die Seite mit ihren untergeordneten Seiten

* Synchronisierungsregeln, die als Rollout-Konfigurationen bezeichnet werden, bestimmen, welche Eigenschaften synchronisiert werden und wann die Synchronisierung durchgeführt wird.

In the previous example, `/content/we-retail/language-masters/en` is the global master site in English. Zur Wiederverwendung des Inhalts dieser Site werden MSM-Live Copies erstellt:

* The content below `/content/we-retail/language-masters/en` is the source.

* Der unten stehende Inhalt `/content/we-retail/language-masters/en` wird unter die Knoten `/content/we-retail/us/en/`, `/content/we-retail/gb/en`, `/content/we-retail/ca/en`und `/content/we-retail/au/en` kopiert. Dies sind die Live Copies.

* Authors make changes to pages below `/content/we-retail/language-masters/en`.
* Nach der Auslösung synchronisiert MSM diese Änderungen mit den Live Copies.

### Live Copies – Komposition {#live-copies-composition}

>[!NOTE]
>
>Die Diagramme und Beschreibungen in diesem Abschnitt stellen Momentaufnahmen der potenziellen Live Copies dar. Sie erheben keinen Anspruch auf Vollständigkeit, stellen jedoch einen Überblick bereit, um bestimmte Merkmale hervorzuheben.

Bei der erstmaligen Erstellung einer Live Copy werden die ausgewählten Quellseiten 1:1 in der Live Copy wiedergegeben. Danach können neue Ressourcen (Seiten und/oder Absätze) auch direkt innerhalb der Live Copy erstellt werden. Daher ist es hilfreich, sich dieser Varianten und ihrer Auswirkung auf die Synchronisierung bewusst zu sein. Mögliche Kompositionen umfassen:

* [Live Copy mit Live Copy-fremden Seiten](#live-copy-with-non-live-copy-pages)
* [Verschachtelte Live Copies](#nested-live-copies)

Die grundlegende Form einer Live Copy verfügt über:

* Live Copy-Seiten, die die ausgewählten Quellseiten 1:1 wiedergeben
* Eine Konfigurationsdefinition
* Eine zu jeder Ressource festgelegte Live-Beziehung:

   * Verknüpft die Live Copy-Ressource mit ihrem Blueprint/ihrer Quelle
   * Werden bei der Realisierung von Vererbung und Rollout verwendet.

* Changes can be [synchronized](/help/sites-administering/msm-livecopy.md#synchronizing-your-live-copy) according to requirements.

![chlimage_1-367](assets/chlimage_1-367.png)

#### Live Copy mit Live Copy-fremden Seiten {#live-copy-with-non-live-copy-pages}

Wenn Sie in AEM eine Live Copy erstellen, können Sie den Live Copy-Zweig sehen und durch diesen navigieren und normale AEM-Funktionen auf dem Live Copy-Zweig verwenden. This means that you (or a process) can create new resources (pages and/or paragraphs) inside the live copy branch (e.g. `myCanadaOnlyProduct`).

* Solche Ressourcen verfügen über keine Live-Beziehung zu Quell-/Blueprint-Seiten und werden nicht synchronisiert.
* Es können Szenarien auftreten, die MSM als Spezialfälle behandelt. Ein Beispiel hierfür wäre, wenn Sie (oder ein Prozess) eine Seite mit der gleichen Position und dem gleichen Namen sowohl in der Quelle/dem Blueprint als auch in den Live Copy-Zweigen erstellen. For such situations see [MSM Rollout Conflicts](/help/sites-administering/msm-rollout-conflicts.md) for more information.

![chlimage_1-368](assets/chlimage_1-368.png)

#### Verschachtelte Live Copies {#nested-live-copies}

When you (or a process) create a [new page within an existing live copy](#live-copy-with-non-live-copy-pages) this new page can also be set up as a live copy of a different blueprint. Dies wird als verschachtelte Live Copy bezeichnet. Hier wird das Verhalten der zweiten (inneren) Live Copy durch die zweite (äußere) Live Copy auf folgende Weise beeinflusst:

* Ein tiefes Rollout, das für die Live Copy der obersten Ebene ausgelöst wurde, kann in einer verschachtelten Live Copy fortgeführt werden (zum Beispiel bei übereinstimmendem Auslöser).
* Alle Links zwischen den Quellen werden innerhalb der Live Copies neu geschrieben.

   Es werden zum Beispiel Links vom zweiten auf den ersten Blueprint neu als Links von der zweiten/verschachtelten Live Copy auf die erste Live Copy geschrieben.

![chlimage_1-369](assets/chlimage_1-369.png)

>[!NOTE]
>
>Wenn Sie eine Seite innerhalb des Live Copy-Zweigs verschieben/neu benennen, wird dies (intern) als verschachtelte Live Copy behandelt, um AEM die Rückverfolgung der Beziehungen zu ermöglichen.

#### Gestapelte Live Copies {#stacked-live-copies}

Eine Live Copy wird als gestapelte Live Copy bezeichnet, wenn sie als untergeordnetes Element einer flachen Live Copy erstellt wird. Sie verhält sich auf gleiche Weise wie eine [verschachtelte Live Copy](#nested-live-copies).

### Quelle, Blueprints und Blueprint-Konfigurationen {#source-blueprints-and-blueprint-configurations}

Jede Seite eines Zweigs von Seiten kann als Quelle einer Live Copy verwendet werden.

MSM ermöglicht Ihnen allerdings die Definition einer Blueprint-Konfiguration, die einen Quellpfad angibt. Die Vorteile einer Blueprint-Konfiguration sind, dass sie:

* Allow the author to use the **Rollout** option on a blueprint - to (explicitly) push modifications to live copies that inherit from this blueprint.
* Allow the author to use **Create Site**; this allows the user to easily select languages and configure the structure of the live copy.
* Sie definiert eine standardmäßige Rollout-Konfiguration für Live Copies, die über eine Beziehung mit dem Blueprint verfügen.

Bei der Quelle einer Live Copy kann es sich entweder um reguläre Seiten handeln oder um Seiten, die von einer Blueprint-Konfiguration abgedeckt sind. Beide Nutzungsszenarien sind möglich.

Die Quelle bildet den Blueprint für die Live Copy. Der Blueprint wird durch eine der folgenden Maßnahmen definiert:

* [Erstellen einer Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration)

   Die Konfiguration definiert (im Voraus) die Seiten, die zum Erstellen der Live-Kopie verwendet werden sollen.

* [Erstellen einer Live-Kopie einer Seite](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   Die zum Erstellen der Live-Kopie verwendeten Seiten (die Quellseiten) sind die Musterseiten.

   Die Quellseite kann von einer Blueprint-Konfiguration referenziert werden oder nicht.

### Rollout und Synchronisieren {#rollout-and-synchronize}

Ein Rollout ist die zentrale MSM-Aktion, die Live Copies mit ihrer Quelle synchronisiert. Sie können Rollouts manuell ausführen oder sie werden automatisch durchgeführt:

* Es kann eine [Rollout-Konfiguration](#rollout-configurations) definiert werden, sodass spezifische [Ereignisse](/help/sites-administering/msm-sync.md#rollout-triggers) eine automatische Ausführung eines Rollouts bewirken können.
* Beim Bearbeiten einer Blueprint-Seite können Sie den [Rollout](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint)-Befehl verwenden, um Änderungen auf die Live Copy zu pushen.

   **Der Rollout**-Befehl ist auf einer Blueprint-Seite verfügbar, die von einer Blueprint-Konfiguration referenziert wird.

   ![chlimage_1-370](assets/chlimage_1-370.png)

* Beim Bearbeiten einer Live Copy-Seite können Sie den Befehl [Synchronisieren](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) verwenden, um Änderungen aus der Quelle in die Live Copy zu ziehen.

   Der Befehl **Synchronisieren** ist auf der Live Copy-Seite immer verfügbar (unabhängig davon, ob die Quelle/Blueprint-Seite von einer Blueprint-Konfiguration abgedeckt ist).

   ![chlimage_1-371](assets/chlimage_1-371.png)

### Rollout-Konfigurationen {#rollout-configurations}

Eine Rollout-Konfiguration definiert, wann und wie eine Live Copy mit dem Quellinhalt synchronisiert wird. Eine Rollout-Konfiguration besteht aus einem Auslöser und einer oder mehr Synchronisierungsaktionen:

* **Auslöser**

   Ein Auslöser ist ein Ereignis, das die Live-Aktionssynchronisierung bewirkt, wie zum Beispiel die Aktivierung einer Quellseite. MSM definiert die Auslöser, die Sie verwenden können.

* **Synchronisierungsaktionen**

   Synchronisierungsaktionen werden mit der Live Copy ausgeführt, um diese mit der Quelle zu synchronisieren. Beispielaktionen kopieren Inhalte, ordnen untergeordnete Knoten an und aktivieren die Live Copy-Seite. MSM stellt eine Reihe von Synchronisierungsaktionen bereit.

   >[!NOTE]
   >
   >Sie können mithilfe der Java API benutzerdefinierte Aktionen für Ihre Instanz erstellen.

Rollout-Konfigurationen können wiederverwendet werden, sodass mehr als eine Live Copy dieselbe Rollout-Konfiguration verwenden kann. Mehrere [Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations) sind in einer Standardinstallation enthalten.

### Rollout-Konflikte {#rollout-conflicts}

Rollouts können kompliziert werden, vor allem wenn Autoren sowohl Inhalte in der Quelle als auch in der Live Copy bearbeiten. Es ist also hilfreich zu wissen, wie AEM [Konflikte handhabt, die während des Rollouts auftreten können](/help/sites-administering/msm-rollout-conflicts.md).

### Aussetzen und Abbrechen der Vererbung und Synchronisierung {#suspending-and-cancelling-inheritance-and-synchronization}

Jede Seite und Komponente in einer Live Copy ist über eine Live-Beziehung mit ihrer Quellseite und Komponente verknüpft. Die Live-Beziehung konfiguriert die Synchronisierung des Live Copy-Inhalts der Quelle.

Sie können die Live Copy-Vererbung für eine Live Copy-Seite **aussetzen**, damit Sie Seiteneigenschaften und Komponenten ändern können. Wenn Sie die Vererbung aussetzen, werden die Seiteneigenschaften und Komponenten nicht mehr mit der Quelle synchronisiert.

Bei der Bearbeitung einer einzelnen Seite können Autoren zu einer Komponente die **Vererbung abbrechen**. Wird die Vererbung abgebrochen, wird die Live-Beziehung unterbrochen und die Synchronisierung tritt bei dieser Komponente nicht auf. Das Abbrechen der Vererbung und Synchronisierung ist nützlich, wenn Unterabschnitte des Inhalts angepasst werden müssen.

### Trennen von Live Copies {#detaching-a-live-copy}

Sie können auch [eine Live Copy von ihrem Blueprint trennen](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy), um alle Verbindungen zu entfernen.

>[!CAUTION]
>
>Die Trennaktion ist dauerhaft und kann nicht rückgängig gemacht werden.

Beim Trennen wird die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite dauerhaft entfernt. Alle MSM-bezogenen Eigenschaften werden aus der Live Copy entfernt und die Live Copy-Seiten werden zu einer eigenständigen Kopie.

>[!NOTE]
>
>Die vollständigen Details, einschließlich der damit verbundenen Auswirkungen auf Unterseiten und übergeordnete Seiten, finden Sie unter [Trennen von Live Copies](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy).

## Standardschritte zur Verwendung von MSM {#standard-steps-for-using-msm}

Die folgenden Schritte beschreiben die standardmäßige Vorgehensweise für die Verwendung von MSM zur Wiederverwendung von Inhalten und zur Synchronisierung von Änderungen an den Live Copies.

1. Entwickeln Sie die Inhalte Der Quell-Site.
1. Legen Sie die zu verwendende Rollout-Konfiguration fest.

   1. MSM [installs several rollout configurations](/help/sites-administering/msm-sync.md#installed-rollout-configurations) that can satisfy a number of use cases.
   1. Sie können bei Bedarf optional eine [Rollout-Konfiguration erstellen](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration).

1. Legen Sie fest, wo Sie die [zu verwendenden Rollout-Konfigurationen angeben](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) müssen und nehmen Sie bei Bedarf eine Konfiguration vor.
1. If required, [create a blueprint configuration](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration) that identifies the source content of the live copy.
1. [Erstellen Sie eine Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy).
1. Nehmen Sie bei Bedarf Änderungen am Quellinhalt vor. Sie sollten den normalen, von Ihrer Organisation etablierten Inhaltsprüfungs- und Genehmigungsprozess anwenden.
1. [Führen Sie](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) den Blueprint aus oder [synchronisieren Sie die Live-Kopie](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) mit den Änderungen.

## Anpassen von MSM {#customizing-msm}

MSM stellt Tools bereit, sodass Ihre Implementierung sich an die außergewöhnlichen Komplexitäten anpassen kann, die bei der Freigabe von Inhalten auftreten können:

* **Benutzerdefinierte Rollout-Konfigurationen**
   [Erstellen Sie eine Rollout-Konfiguration](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) , wenn die installierten Rollout-Konfigurationen Ihre Anforderungen nicht erfüllen. Sie können jeden verfügbaren Rollout-Auslöser und jede verfügbare Synchronisierungsaktion verwenden.

* **Benutzerdefinierte Synchronisierungsaktionen**
   [Erstellen Sie eine benutzerdefinierte Synchronisierungsaktion](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) , wenn die installierten Aktionen Ihre spezifischen Anwendungsanforderungen nicht erfüllen. MSM stellt eine Java-API für die Erstellung einer benutzerdefinierten Synchronisierungsaktion bereit.

## Best Practices {#best-practices}

Die Seite [Best Practices für MSM](/help/sites-administering/msm-best-practices.md) enthält wichtige Informationen zur Implementierung.
