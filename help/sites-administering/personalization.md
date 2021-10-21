---
title: Personalisierung
seo-title: Personalization
description: Erfahren Sie mehr über die Personalisierung in AEM.
seo-description: Learn about personalization in AEM.
uuid: 5790a3e0-f0ec-4785-b915-330a10dea30c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 03ebc494-8baa-4741-b8de-dac5ace743c8
exl-id: 3a550a33-b54b-4217-b9a6-b5a7971276ee
source-git-commit: d6b595b6b5477b5cad662e219f1abd483491897f
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 72%

---

# Personalisierung {#personalization}

## Was ist Personalisierung? {#what-is-personalization}

Heute steht eine immer größere Menge an Inhalten zur Verfügung – sei es auf Websites im Internet, im Extranet oder im Intranet.

Personalisierung konzentriert sich darauf, dem Benutzer eine maßgeschneiderte Umgebung bereitzustellen, in der dynamische Inhalte angezeigt werden, die entsprechend den spezifischen Anforderungen ausgewählt werden – sei es auf Grundlage vordefinierter Profile, der Benutzerauswahl oder des interaktiven Benutzerverhaltens.

Personalisierung umfasst drei Hauptelemente:

### Benutzer {#users}

* Sie haben sowohl einzelne Profile als auch Profile aus der Gruppe. Diese Profile enthalten Merkmale (wie Tätigkeitsbeschreibung, Standort, Interessen), die zur Personalisierung der angezeigten Inhalte verwendet werden können.
* Ergreifen Sie Maßnahmen. Diese können analysiert und mit Verhaltensregeln abgeglichen werden, um die angezeigten Inhalte benutzerspezifisch anzupassen.

### Inhalt {#content}

* Ist es, was der Benutzer sehen möchte. Der Inhalt, der für sie interessant ist und sie zur Erfüllung ihrer Aufgaben verwendet.
* Kann kategorisiert werden und daher Benutzern gemäß vordefinierten Regeln zur Verfügung gestellt werden.
* Muss dynamisch sein.

Anders ausgedrückt: Der Inhalt muss in gewisser Weise vom Benutzer abhängig sein. Wenn jeder Benutzer denselben Inhalt sieht, ist die Personalisierung redundant.

### Regeln {#rules}

* Definieren Sie, wie die Personalisierung tatsächlich erfolgt - welcher Inhalt dem Benutzer angezeigt werden kann und wann.

Es gibt zwei Arten von Personalisierung:

#### Explizit {#explicit}

* Benutzerspezifische Anpassung: Hierbei wählt der Benutzer aus einer Reihe von Inhaltsquellen aus.

#### Implizit {#implicit}

* Regelbasiert: Geschäftsführer legen basierend auf bestimmten Profilen und/oder Verhaltensweisen bestimmte Regeln für Aktionen fest.
* Einfaches Filtern: Die Auswahlen werden basierend auf vordefinierten Profilen auf Benutzer- und/oder Gruppenebene vorgenommen.
* Kollaboratives Filtern/Empfehlungsfiltern: Das Benutzerverhalten wird unter Einhaltung vordefinierter Regeln registriert. Diese Regeln basieren auf dem Verhalten, das bei Personen mit ähnlichen Interessen beobachtet wurde. Die erfassten Informationen werden dazu verwendet, die angezeigten Informationen benutzerspezifisch anzupassen – vor allem in Form von Empfehlungen.

## Wie und wann kann Personalisierung verwendet werden? {#how-and-when-can-personalization-be-used}

Die Personalisierung kann in vielen Fällen verwendet werden, wie zum Beispiel:

### Intranet-Seiten {#intranet-pages}

* Inhalte können basierend auf dem Standort, der Abteilung und/oder der Rolle eines Benutzers bereitgestellt werden, der bereits in einem internen Netzwerk definiert ist.
* Je nach der verfügbaren Auswahl hat der Benutzer noch weitere Auswahlmöglichkeiten.

### Spezifische, eingeschränkte Target-Benutzergruppen - Extranets {#extranets}

* Benutzer benötigen Anmeldedaten zur Autorisierung. Dies wird mit einem Profil verknüpft, das die erforderlichen Informationen für die Personalisierung bereitstellt – wie zum Beispiel den Standort, die Beziehung zum Produkt, die Nutzungsgeschichte, Budgetierungsverpflichtungen usw. 
* Solche Instanzen können auch standortübergreifend genutzt werden, wie zum Beispiel in den folgenden Fällen:
* Unternehmen, die Websites für einen hochgradig spezialisierten Bereich ihres Markts bereitstellen, zum Beispiel Pharmaunternehmen, die Ärzten eine spezialisierte Website bereitstellen.
* Unternehmen, die Websites bereitstellen, mit denen ihre Kunden aktuelle Konto- und Rechnungsinformationen anzeigen können, so zum Beispiel Telekommunikationsanbieter.

### Verkaufs- und Vertriebswebsite {#sales-site}

* Verkaufs- und Vertriebswebsites wie Amazon können ein Benutzerprofil mit der Kauf- und Suchhistorie des Benutzers kombinieren, um Empfehlungen dazu auszusprechen, was den Benutzer als Nächstes interessieren könnte.

### Websites durchsuchen {#search-site}

* Viele große Suchmaschinenwebsites verfügen über leistungsstarke Analysetools, die das Benutzerverhalten, die eingegebenen Suchbegriffe und die tatsächlich besuchten Websites aufzeichnen. Dies wird dann verwendet, um den bereitgestellten Inhalt anzupassen, insbesondere im Hinblick auf die Anzeige von Werbung.

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

* Das Caching ist ein Aspekt, den der Benutzer hinsichtlich Leistung und Genauigkeit sehen wird. Wie schnell liefert die Website personalisierte Inhalte und ist immer aktuell.
* Die Speicherung im Cache ist eine wichtige Überlegung für die Konfiguration der Personalisierung und es ist ein gewisser Zeitaufwand erforderlich, um sicherzustellen, dass die richtige Implementierung verwendet wird.

>[!TIP]
>
>Die Auswirkungen der Personalisierung auf die Leistung und damit zusammenhängende Themen zum Zwischenspeichern werden im Dokument näher erläutert. [Leistungsoptimierung.](/help/sites-deploying/configuring-performance.md)

#### Genauigkeit der Regeln {#accuracy}

* Die Personalisierung, die durch die Rückverfolgung des Benutzerverhaltens oder durch die Festlegung von Regeln auf Grundlage des Benutzerprofils umgesetzt wird, muss genau und logisch erfolgen.
* Es gibt für Benutzer nichts Frustrierenderes, als nur aufgrund der ungenauen Logik einer Regel Inhalte aufgezwungen oder vorenthalten zu bekommen.
* Daher müssen Regeln gut durchdacht sein - mit den Anforderungen des Benutzers im Vordergrund. Dies kann sehr mühsam sein und darf nicht unterschätzt werden. Die Festlegung der geschäftlichen Regeln ist häufig aufwendiger als die technischen Maßnahmen bei der Implementierung der Personalisierung.

#### Verwendungsbereiche {#when-to-use}

* Wie viele Funktionen im Internet ist auch Personalisierung mit Vorsicht einzusetzen. Ist Ihr Einsatz wirklich von Vorteil für den Benutzer? Dies sollte immer die erste Überlegung sein. Darüber hinaus sollte ergründet werden, ob das gewünschte Ziel mit einer anderen Methode mit geringerem Aufwand erreicht werden kann. Bei der Personalisierung besteht die Gefahr, dass sie nur einmal von Benutzern konfiguriert wird (um zu sehen, wie sie funktionieren) und nur einmal - da sie keine echten Vorteile bringt.
* Personalisierung ist nur dann sinnvoll, wenn der Inhalt dynamisch ist - abhängig vom Benutzer in irgendeiner Weise. Werden allen Benutzern dieselben Inhalte angezeigt, ist die Personalisierung redundant.

#### Vertraulichkeit {#confidentiality}

* Viele Benutzer machen sich Sorgen um Datenschutz und -sicherheit. Insbesondere gilt dies für Daten, die bei der Rückverfolgung ihres Verhaltens beim Surfen im Internet abgerufen werden.

## Personalisierung und Zugriff {#personalization-and-access}

Personalisierung sollte separat von der Zugriffssteuerung betrachtet werden, allerdings gibt es einen Zusammenhang zwischen beidem.

Personalisierung selbst sorgt für keinerlei Form der Zugriffssteuerung. Es handelt sich um eine einfache Methode der Steuerung dessen, was der Benutzer sieht, und hält den Benutzer nicht davon ab, auf andere Inhalte zuzugreifen. Wie bei jeder Art von Inhalten müssen die korrekten Zugriffssteuerungen bereits zugewiesen sein.

Allerdings kann die Zugangskontrolle verwendet werden, um eine Art der Personalisierung zu entwickeln. Wenn Sie einem Benutzer den Zugriff auf Inhalte gewähren oder untersagen, hat dies unvermeidlich Auswirkungen auf die Auswahl der Inhalte, die zur Verfügung stehen – wodurch das Weberlebnis der Benutzer personalisiert wird.

## Verfügbare Komponenten für die Personalisierung {#components-available-for-personalization}

Mit AEM werden verschiedene Komponenten für die Personalisierung bereitgestellt. Manche ermöglichen es den Benutzern, sich anzumelden und ihre Profile zu bearbeiten, andere (wie My Gadgets) dagegen ermöglichen den Benutzern die Konfiguration einer bestimmten Seite:

| Titel im Sidekick | Zweck |
|---|---|
| Geprüftes Kennwort-Feld | Fordert zur Eingabe des Kennworts und Bestätigung des Kennworts auf. |
| Kombinierte Anmeldung | Ermöglicht dem Benutzer, sich entweder bei einem vorhandenen Konto anzumelden oder sich für ein neues Konto zu registrieren. |
| Forms-Adressfeld | Ein komplexes Feld, das die Eingabe einer internationalen Adresse ermöglicht. |
| Forms Begin | Startet eine Formulardefinition |
| Forms Captcha | Ein Feld, das aus einem automatisch aktualisierten alphanumerischen Wort besteht. Die Captcha-Komponente schützt Websites vor Bots.  |
| Forms-Kontrollkästchengruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Kontrollkästchen vorangestellt sind. Benutzer können mehrere Kontrollkästchen auswählen. |
| Forms-Dropdownliste | Mehrere Elemente, die als Dropdown-Liste angeordnet sind. Der Schalter für die Mehrfachauswahl gibt an, ob mehrere Elemente aus der Liste ausgewählt werden können. |
| Forms End | Beendet die Formulardefinition. |
| Forms-Datei-Upload | Ein Upload-Element, mit dem der Benutzer eine Datei zum Server hochladen kann. |
| Ausgeblendetes Forms-Feld | Dieses Feld wird dem Benutzer nicht angezeigt. Mit ihm kann ein Wert zum Client und zurück zum Server übertragen werden. Für dieses Feld gelten keine Beschränkungen. |
| Forms-Bildschaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, die als Bild dargestellt wird. |
| Forms-Kennwortfeld | Identisch mit einem Textfeld, doch nur eine Zeile ist zulässig und die Texteingabe des Benutzers ist im Feld nicht sichtbar. |
| Forms-Optionsfeldgruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Optionsschalter vorangestellt sind. Benutzer dürfen nur einen Optionsschalter auswählen. |
| Forms-Senden-Schaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, wobei der Titel als Text auf der Schaltfläche dargestellt wird. |
| Forms-Textfeld | Ein Textfeld, in das Benutzer Informationen eingeben können. |
| Meine Gadgets | Ermöglicht die Auswahl eines der verfügbaren Gadgets. |
| Profil-Avatar-Foto | Ermöglicht die Eingabe eines Avatar-Fotos. |
| Profil – Genauer Name | Eingabe von Namendetails, einschließlich Elemente wie Titel, zweiter Vorname und Suffix, falls erforderlich. |
| Profil - Anzeigename | Anzuzeigender Name. |
| Profil - E-Mail | Eingabe einer E-Mail-Adresse. |
| Profil-Geschlecht | Ermöglicht die Eingabe des Geschlechts.  |
| Profil - Primäre Telefonnummer | Ermöglicht die Eingabe einer Telefonnummer.  |
| Profil - Primäre URL | Ermöglicht die Eingabe einer URL. |
| Allgemeine Texteigenschaft für Profil | Profileigenschaften. |
| Anmelden | Ermöglicht die Eingabe eines Benutzernamens und eines Kennworts bei der Anmeldung. |
| Abmelden | Gibt den derzeit angemeldeten Benutzer an und gibt einen Link zum Abmelden. |
| Tag-Cloud | Tag-Cloud, um eine grafisch dargestellte Auswahl von Tags auf Ihrer Website anzuzeigen |
| Teaser | Ein Inhaltselement (normalerweise ein Bild), das auf einer Hauptseite angezeigt wird, um Benutzer zum Zugriff auf den zugrunde liegenden Inhalt zu &quot;ermuntern&quot;. |

## Personalisierung und Community-Inhalte {#personalization-and-community-content}

Community-Funktionen wie Blogs, Foren und Kalender generieren Community-Inhalte, die gemeinhin als benutzergenerierte Inhalte bezeichnet werden. Wurden benutzergenerierte Inhalte in eine aus mehreren AEM-Instanzen bestehende Veröffentlichungsumgebung eingegeben (eine [Veröffentlichungsfarm](/help/communities/topologies.md)), war hierbei eines der größten Probleme die instanzenübergreifende Synchronisierung der benutzergenerierten Inhalte.

Mit [AEM Communities 6.1](/help/communities/overview.md) -Erweiterung verwenden, wird dieses Problem durch die Verwendung einer [gemeinsamer Speicher für benutzergenerierte Inhalte](/help/communities/working-with-srp.md). Im Hinblick auf die Personalisierung schließt Communities [Anmeldung über soziale Netzwerke](/help/communities/social-login.md) - die Möglichkeit, Site-Besuchern die Möglichkeit zu geben, sich bei Facebook und Twitter anzumelden.

Ohne Communities-Erweiterung gibt es verschiedene Methoden, das Problem der Konsistenz des benutzergenerierten Inhalts anzugehen:

* Synchronisieren Sie bei Bedarf mehrere Veröffentlichungsinstanzen.
* Senden Sie die Benutzerkontensteuerung von der Veröffentlichungsinstanz an die Autorenumgebung, von der aus sie ähnlich wie Seiteninhalte veröffentlicht werden kann.

Die Methode, die verwendet wird, um die Konsistenz des benutzergenerierten Inhalts über mehrere Veröffentlichungsinstanzen hinweg zu erzielen, sollte sorgfältig gestaltet und auf ihre Leistung und Konsistenz hin überprüft werden.
