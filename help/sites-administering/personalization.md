---
title: 'Personalisierung '
seo-title: 'Personalisierung '
description: Erfahren Sie mehr über die Personalisierung in AEM.
seo-description: Erfahren Sie mehr über die Personalisierung in AEM.
uuid: 5790a3e0-f0ec-4785-b915-330a10dea30c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 03ebc494-8baa-4741-b8de-dac5ace743c8
translation-type: tm+mt
source-git-commit: ffded9c4c08c68db59d05b341166bed92e741e1e
workflow-type: tm+mt
source-wordcount: '1693'
ht-degree: 73%

---


# Personalisierung  {#personalization}

## Was ist Personalisierung? {#what-is-personalization}

Heute steht eine immer größere Menge an Inhalten zur Verfügung – sei es auf Websites im Internet, im Extranet oder im Intranet.

Personalisierung konzentriert sich darauf, dem Benutzer eine maßgeschneiderte Umgebung bereitzustellen, in der dynamische Inhalte angezeigt werden, die entsprechend den spezifischen Anforderungen ausgewählt werden – sei es auf Grundlage vordefinierter Profile, der Benutzerauswahl oder des interaktiven Benutzerverhaltens.

Personalisierung umfasst drei Hauptelemente:

### Benutzer {#users}

* Sie haben Profile, sowohl einzeln als auch gruppiert. Diese Profile enthalten Merkmale (wie Tätigkeitsbeschreibung, Standort, Interessen), die zur Personalisierung der angezeigten Inhalte verwendet werden können.
* Ergreifen Sie Maßnahmen. Diese können analysiert und mit Verhaltensregeln abgeglichen werden, um die angezeigten Inhalte benutzerspezifisch anzupassen.

### Inhalt {#content}

* Ist es, was der Benutzer sehen möchte. Bevorzugt sollten dies Inhalte sein, die für die Erfüllung der Aufgaben des Benutzers interessant und nützlich sind.
* Kann kategorisiert werden und damit für Benutzer gemäß vordefinierten Regeln zur Verfügung gestellt werden.muss dynamisch sein; mit anderen Worten, der Inhalt
* Muss irgendwie vom Benutzer abhängig sein - wenn jeder Benutzer denselben Inhalt sehen würde, wäre die Personalisierung überflüssig.

### Regeln {#rules}

* Definieren Sie, wie die Personalisierung tatsächlich abläuft - welche Inhalte der Benutzer sehen kann und wann.

Es gibt zwei Arten von Personalisierung:

#### Explizit {#explicit}

* Benutzerspezifische Anpassung: Hierbei wählt der Benutzer aus einer Reihe von Inhaltsquellen aus.

#### Implizit {#implicit}

* Regelbasiert: Geschäftsführer legen basierend auf bestimmten Profilen und/oder Verhaltensweisen bestimmte Regeln für Aktionen fest.
* Einfaches Filtern: Die Auswahlen werden basierend auf vordefinierten Profilen auf Benutzer- und/oder Gruppenebene vorgenommen.
* Kollaboratives Filtern/Empfehlungsfiltern: Das Benutzerverhalten wird unter Einhaltung vordefinierter Regeln registriert. Diese Regeln basieren auf dem Verhalten, das bei Personen mit ähnlichen Interessen beobachtet wurde. Die erfassten Informationen werden dazu verwendet, die angezeigten Informationen benutzerspezifisch anzupassen – vor allem in Form von Empfehlungen.

## Wie und wann kann die Personalisierung verwendet werden? {#how-and-when-can-personalization-be-used}

Die Personalisierung kann in vielen Fällen verwendet werden, wie zum Beispiel:

### Intranet-Seiten {#intranet-pages}

* Inhalte können basierend auf dem Standort, der Abteilung und/oder der Rolle eines Benutzers angeboten werden - bereits in einem internen Netzwerk definiert.
* Je nach der verfügbaren Auswahl hat der Benutzer noch weitere Auswahlmöglichkeiten.

### Spezifische, eingeschränkte Zielgruppe-Benutzergruppen - Extranets {#extranets}

* Benutzer benötigen Anmeldedaten zur Autorisierung. Dies wird mit einem Profil verknüpft, das die erforderlichen Informationen für die Personalisierung bereitstellt – wie zum Beispiel den Standort, die Beziehung zum Produkt, die Nutzungsgeschichte, Budgetierungsverpflichtungen usw. 
* Solche Instanzen können auch standortübergreifend genutzt werden, wie zum Beispiel in den folgenden Fällen:
* Unternehmen, die Websites für einen hochgradig spezialisierten Bereich ihres Markts bereitstellen, zum Beispiel Pharmaunternehmen, die Ärzten eine spezialisierte Website bereitstellen.
* Unternehmen, die Websites bereitstellen, mit denen ihre Kunden aktuelle Konto- und Rechnungsinformationen anzeigen können, so zum Beispiel Telekommunikationsanbieter.

### Vertriebs- und Vertriebs-Website {#sales-site}

* Verkaufs- und Vertriebswebsites wie Amazon können ein Benutzerprofil mit der Kauf- und Suchhistorie des Benutzers kombinieren, um Empfehlungen dazu auszusprechen, was den Benutzer als Nächstes interessieren könnte.

### Websites suchen {#search-site}

* Viele große Suchmaschinenwebsites verfügen über leistungsstarke Analysetools, die das Benutzerverhalten, die eingegebenen Suchbegriffe und die tatsächlich besuchten Websites aufzeichnen. Auf diese Weise können Sie die bereitgestellten Inhalte anpassen, insbesondere was die Anzeige von Anzeigen betrifft.

### Stärken der Personalisierung und zu berücksichtigende Punkte {#strengths-of-personalization-and-points-to-consider}

Personalisierung sollte aus folgenden Gründen eingesetzt werden:

* Der Benutzer profitiert von einer komfortablen, fokussierten Website.
* Personalisierung kann für die automatische Übertragung des Zugriffs auf die neueste Version der Inhalte verwendet werden.
* Den Benutzern stehen Social-Collaboration-Funktionen zur Verfügung, über die sie miteinander kommunizieren können, da sie anhand ihrer Profile identifiziert werden können.
* Einem Benutzer können die benötigten Inhalte für die Ausführung einer bestimmten Aufgabe bereitgestellt werden. Innerhalb des Intranets eines Unternehmens kann dies ein wertvolles Tool zur Verbreitung von Informationen sein.
* Einem Benutzer können die benötigten/gewünschten Inhalte bereitgestellt werden, sodass der Zeitaufwand für Suchvorgänge verringert wird.
* Der Anbieter der Inhalte kann nach spezifischen Benutzerkategorien steuern, welche Inhalte angezeigt werden.
* Es können Regeln für die Bereitstellung von Inhalten auf Grundlage der Kombination sowohl von Benutzereigenschaften als auch -verhaltensweisen festgelegt werden. Dies stellt einen ausgeklügelten Mechanismus für die Personalisierung des Weberlebnisses bereit.

Berücksichtigen Sie beim Einsetzen von Personalisierung Folgendes:

#### Leistung {#performance}

* Natürlich haben die zusätzlichen Analysen und Bewertungen Auswirkungen auf die Leistung. Dennoch sind die eingesetzten Methoden äußerst anspruchsvoll und können optimiert werden, um negative Auswirkungen zu minimieren.

#### Autorisierung {#authorization}

* Personalisierung erfordert einen Anmeldemechanismus, da die Website den Benutzer identifizieren muss.

#### Caching {#caching}

* Die Zwischenspeicherung ist ein Aspekt, den der Benutzer in Bezug auf Leistung und Genauigkeit sehen wird - wie schnell liefert die Website personalisierte Inhalte und ist sie immer aktuell.
* Die Speicherung im Cache ist eine wichtige Überlegung für die Konfiguration der Personalisierung und es ist ein gewisser Zeitaufwand erforderlich, um sicherzustellen, dass die richtige Implementierung verwendet wird.

>[!TIP]
>
>Die Auswirkungen der Personalisierung auf die Leistung und damit verbundene Themen zum Zwischenspeichern werden im Dokument [Leistungsoptimierung.](/help/sites-deploying/configuring-performance.md)

#### Genauigkeit der Regeln {#accuracy}

* Die Personalisierung, die durch die Rückverfolgung des Benutzerverhaltens oder durch die Festlegung von Regeln auf Grundlage des Benutzerprofils umgesetzt wird, muss genau und logisch erfolgen.
* Es gibt für Benutzer nichts Frustrierenderes, als nur aufgrund der ungenauen Logik einer Regel Inhalte aufgezwungen oder vorenthalten zu bekommen.
* Deshalb müssen Regeln gut durchdacht sein - mit den Anforderungen des Benutzers im Vordergrund. Dies kann sehr mühsam sein und darf nicht unterschätzt werden. Die Festlegung der geschäftlichen Regeln ist häufig aufwendiger als die technischen Maßnahmen bei der Implementierung der Personalisierung.

#### Verwenden von {#when-to-use}

* Wie viele Funktionen im Internet ist auch Personalisierung mit Vorsicht einzusetzen. Ist Ihr Einsatz wirklich von Vorteil für den Benutzer? Dies sollte immer die erste Überlegung sein. Darüber hinaus sollte ergründet werden, ob das gewünschte Ziel mit einer anderen Methode mit geringerem Aufwand erreicht werden kann. Personalisierung kann das Risiko eingehen, eine Funktion zu sein, die Benutzer einmal konfigurieren (um zu sehen, wie sie funktioniert) und nur einmal - da sie ihnen keine echten Vorteile bringt.
* Personalisierung ist nur dann sinnvoll, wenn der Inhalt dynamisch ist - abhängig vom Benutzer in irgendeiner Weise. Werden allen Benutzern dieselben Inhalte angezeigt, ist die Personalisierung redundant.

#### Vertraulichkeit {#confidentiality}

* Viele Benutzer machen sich Sorgen um Datenschutz und -sicherheit. Insbesondere gilt dies für Daten, die bei der Rückverfolgung ihres Verhaltens beim Surfen im Internet abgerufen werden.

## Personalisierung und Zugriff  {#personalization-and-access}

Personalisierung sollte separat von der Zugriffssteuerung betrachtet werden, allerdings gibt es einen Zusammenhang zwischen beidem.

Personalisierung selbst sorgt für keinerlei Form der Zugriffssteuerung. Es handelt sich um eine einfache Methode der Steuerung dessen, was der Benutzer sieht, und hält den Benutzer nicht davon ab, auf andere Inhalte zuzugreifen. Wie bei jeder Art von Inhalten müssen die korrekten Zugriffssteuerungen bereits zugewiesen sein.

Allerdings kann die Zugangskontrolle verwendet werden, um eine Art der Personalisierung zu entwickeln. Wenn Sie einem Benutzer den Zugriff auf Inhalte gewähren oder untersagen, hat dies unvermeidlich Auswirkungen auf die Auswahl der Inhalte, die zur Verfügung stehen – wodurch das Weberlebnis der Benutzer personalisiert wird.

## Verfügbare Komponenten für die Personalisierung  {#components-available-for-personalization}

Mit AEM werden verschiedene Komponenten für die Personalisierung bereitgestellt. Manche ermöglichen es den Benutzern, sich anzumelden und ihre Profile zu bearbeiten, andere (wie My Gadgets) dagegen ermöglichen den Benutzern die Konfiguration einer bestimmten Seite:

| Titel im Sidekick | Zweck |
|---|---|
| Geprüftes Kennwort-Feld | Fordert zur Eingabe des Kennworts und Bestätigung des Kennworts auf. |
| Kombinierte Anmeldung | Ermöglicht dem Benutzer, sich entweder bei einem vorhandenen Konto anzumelden oder sich für ein neues Konto zu registrieren. |
| Forms-Adressfeld | Ein komplexes Feld, das die Eingabe einer internationalen Adresse ermöglicht. |
| Forms Begin | Beginn einer Formulardefinition |
| Forms Captcha | Ein Feld, das aus einem automatisch aktualisierten alphanumerischen Wort besteht. Die Captcha-Komponente schützt Websites vor Bots.  |
| Forms-Kontrollkästchengruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Kontrollkästchen vorangestellt sind. Benutzer können mehrere Kontrollkästchen auswählen. |
| Forms Dropdown-Liste | Mehrere Elemente, die als Dropdown-Liste angeordnet sind. Der Schalter für die Mehrfachauswahl gibt an, ob mehrere Elemente aus der Liste ausgewählt werden können. |
| Forms End | Beendet die Formulardefinition. |
| Forms-Datei-Upload | Ein Upload-Element, mit dem der Benutzer eine Datei zum Server hochladen kann. |
| Ausgeblendetes Forms-Feld | Dieses Feld wird dem Benutzer nicht angezeigt. Mit ihm kann ein Wert zum Client und zurück zum Server übertragen werden. Für dieses Feld gelten keine Beschränkungen. |
| Forms-Bildschaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, die als Bild dargestellt wird. |
| Forms-Kennwortfeld | Identisch mit einem Textfeld, doch nur eine Zeile ist zulässig und die Texteingabe des Benutzers ist im Feld nicht sichtbar. |
| Forms Radio Group | Mehrere Elemente, die als Liste angeordnet sind und denen Optionsschalter vorangestellt sind. Benutzer dürfen nur einen Optionsschalter auswählen. |
| Forms-Senden-Schaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, wobei der Titel als Text auf der Schaltfläche dargestellt wird. |
| Forms-Textfeld | Ein Textfeld, in das Benutzer Informationen eingeben können. |
| Meine Gadgets | Ermöglicht Ihnen, eine Auswahl verfügbarer Geräte einzuschließen. |
| Profil-Avatar-Foto | Ermöglicht die Eingabe eines Avatar-Fotos. |
| Profil – Genauer Name | Eingabe von Namendetails, einschließlich Elemente wie Titel, zweiter Vorname und Suffix, falls erforderlich. |
| Profil - Anzeigename | Anzuzeigender Name. |
| Profil - E-Mail | Eingabe einer E-Mail-Adresse. |
| Profil-Geschlecht | Ermöglicht die Eingabe des Geschlechts.  |
| Profil Primär Telefonnummer | Ermöglicht die Eingabe einer Telefonnummer.  |
| Profil - Primäre URL | Ermöglicht die Eingabe einer URL. |
| Profil General Text, Eigenschaft | Profileigenschaften. |
| Anmelden | Ermöglicht Ihnen, bei der Anmeldung einen Benutzernamen und ein Kennwort zu senden. |
| Abmelden | Gibt den derzeit angemeldeten Benutzer an und gibt einen Link zum Abmelden an. |
| Tag-Cloud | Eine Tag-Cloud, um eine grafisch dargestellte Auswahl von Tags innerhalb Ihrer Website anzuzeigen |
| Teaser | Ein Inhaltselement (normalerweise ein Bild), das auf einer Hauptseite angezeigt wird, um Benutzer zum Zugriff auf den zugrunde liegenden Inhalt zu &quot;verleiten&quot;. |

## Personalisierung und Community-Inhalte {#personalization-and-community-content}

Community-Funktionen wie Blogs, Foren und Kalender generieren Community-Inhalte, die gemeinhin als benutzergenerierte Inhalte bezeichnet werden. Wurden benutzergenerierte Inhalte in eine aus mehreren AEM-Instanzen bestehende Veröffentlichungsumgebung eingegeben (eine [Veröffentlichungsfarm](/help/communities/topologies.md)), war hierbei eines der größten Probleme die instanzenübergreifende Synchronisierung der benutzergenerierten Inhalte.

Mit der Erweiterung [AEM Communities 6.1](/help/communities/overview.md) wird dieses Problem mit einem [gemeinsamen Speicher für UGC](/help/communities/working-with-srp.md) behoben. Bezüglich der Personalisierung beinhaltet Communities [Social Login](/help/communities/social-login.md) - die Möglichkeit, Site-Besuchern die Möglichkeit zu geben, sich bei Facebook und Twitter anzumelden.

Ohne Communities-Erweiterung gibt es verschiedene Methoden, das Problem der Konsistenz des benutzergenerierten Inhalts anzugehen:

* Mehrere Instanzen im Veröffentlichungsmodus bei Bedarf synchronisieren
* Senden Sie das UGC von der Veröffentlichungsinstanz an die Autorendatei, von der aus es ähnlich wie beim Veröffentlichen von Seiteninhalten veröffentlicht werden kann.

Die Methode, die verwendet wird, um die Konsistenz des benutzergenerierten Inhalts über mehrere Veröffentlichungsinstanzen hinweg zu erzielen, sollte sorgfältig gestaltet und auf ihre Leistung und Konsistenz hin überprüft werden.
