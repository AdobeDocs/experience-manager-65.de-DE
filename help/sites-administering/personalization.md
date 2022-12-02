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
ht-degree: 100%

---

# Personalisierung  {#personalization}

## Was ist Personalisierung? {#what-is-personalization}

Heute steht eine immer größere Menge an Inhalten zur Verfügung – sei es auf Websites im Internet, im Extranet oder im Intranet.

Personalisierung konzentriert sich darauf, dem Benutzer eine maßgeschneiderte Umgebung bereitzustellen, in der dynamische Inhalte angezeigt werden, die entsprechend den spezifischen Anforderungen ausgewählt werden – sei es auf Grundlage vordefinierter Profile, der Benutzerauswahl oder des interaktiven Benutzerverhaltens.

Personalisierung umfasst drei Hauptelemente:

### Benutzer {#users}

* Verfügen über Einzel- und Gruppenprofile. Diese Profile enthalten Merkmale (wie Tätigkeitsbeschreibung, Standort, Interessen), die zur Personalisierung der angezeigten Inhalte verwendet werden können.
* Ergreifen Maßnahmen. Diese können analysiert und mit Verhaltensregeln abgeglichen werden, um die angezeigten Inhalte benutzerspezifisch anzupassen.

### Inhalt {#content}

* Ist das, was der Benutzer sehen möchte. Bevorzugt sollten dies Inhalte sein, die für die Erfüllung der Aufgaben des Benutzers interessant und nützlich sind.
* Kann kategorisiert werden und daher Benutzern gemäß vordefinierten Regeln zur Verfügung gestellt werden.
* Muss dynamisch sein.

Anders ausgedrückt: Die Inhalte müssen in gewisser Weise vom Benutzer abhängig sein. Wenn jeder Benutzer dieselben Inhalte sieht, ist die Personalisierung redundant.

### Regeln {#rules}

* Legen fest, wie die Personalisierung tatsächlich vor sich geht, sowie welche Inhalte der Benutzer sehen kann und wann.

Es gibt zwei Arten von Personalisierung:

#### Explizit {#explicit}

* Benutzerspezifische Anpassung: Hierbei wählt der Benutzer aus einer Reihe von Inhaltsquellen aus.

#### Implizit {#implicit}

* Regelbasiert: Geschäftsführer legen basierend auf bestimmten Profilen und/oder Verhaltensweisen bestimmte Regeln für Aktionen fest.
* Einfaches Filtern: Die Auswahlen werden basierend auf vordefinierten Profilen auf Benutzer- und/oder Gruppenebene vorgenommen.
* Kollaboratives Filtern/Empfehlungsfiltern: Das Benutzerverhalten wird unter Einhaltung vordefinierter Regeln registriert. Diese Regeln basieren auf dem Verhalten, das bei Personen mit ähnlichen Interessen beobachtet wurde. Die erfassten Informationen werden dazu verwendet, die angezeigten Informationen benutzerspezifisch anzupassen – vor allem in Form von Empfehlungen.

## Wie und wann kann die Personalisierung verwendet werden? {#how-and-when-can-personalization-be-used}

Die Personalisierung kann in vielen Fällen verwendet werden, wie zum Beispiel:

### Intranetseiten {#intranet-pages}

* Inhalte können basierend auf dem Standort, der Abteilung und/oder der Rolle eines Benutzers angeboten werden, die bereits in einem internen Netzwerk festgelegt ist.
* Je nach der verfügbaren Auswahl hat der Benutzer noch weitere Auswahlmöglichkeiten.

### Spezifische begrenzte Zielbenutzergruppen – Extranets {#extranets}

* Benutzer benötigen Anmeldedaten zur Autorisierung. Dies wird mit einem Profil verknüpft, das die erforderlichen Informationen für die Personalisierung bereitstellt – wie zum Beispiel den Standort, die Beziehung zum Produkt, die Nutzungsgeschichte, Budgetierungsverpflichtungen usw. 
* Solche Instanzen können auch standortübergreifend genutzt werden, wie zum Beispiel in den folgenden Fällen:
* Unternehmen, die Websites für einen hochgradig spezialisierten Bereich ihres Markts bereitstellen, zum Beispiel Pharmaunternehmen, die Ärzten eine spezialisierte Website bereitstellen.
* Unternehmen, die Websites bereitstellen, mit denen ihre Kunden aktuelle Konto- und Rechnungsinformationen anzeigen können, so zum Beispiel Telekommunikationsanbieter.

### Verkaufs- und Vertriebs-Website {#sales-site}

* Verkaufs- und Vertriebswebsites wie Amazon können ein Benutzerprofil mit der Kauf- und Suchhistorie des Benutzers kombinieren, um Empfehlungen dazu auszusprechen, was den Benutzer als Nächstes interessieren könnte.

### Such-Websites {#search-site}

* Viele große Suchmaschinenwebsites verfügen über leistungsstarke Analyse-Tools, die das Benutzerverhalten, die eingegebenen Suchbegriffe und die tatsächlich besuchten Websites aufzeichnen. Dies wird dann für die benutzerdefinierte Anpassung der bereitgestellten Inhalte verwendet – vor allem im Hinblick auf die Anzeige von Werbung.

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

* Die Speicherung im Cache ist ein Aspekt, der sich für den Benutzer im Zusammenhang mit Leistung und Genauigkeit bemerkbar macht: Wie schnell stellt die Website personalisierte Inhalte bereit? Und sind diese immer aktuell?
* Die Speicherung im Cache ist eine wichtige Überlegung für die Konfiguration der Personalisierung und es ist ein gewisser Zeitaufwand erforderlich, um sicherzustellen, dass die richtige Implementierung verwendet wird.

>[!TIP]
>
>Die Auswirkungen der Personalisierung auf die Leistung und damit zusammenhängende Themen zum Zwischenspeichern werden im Dokument [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) näher erläutert.

#### Genauigkeit der Regeln {#accuracy}

* Die Personalisierung, die durch die Rückverfolgung des Benutzerverhaltens oder durch die Festlegung von Regeln auf Grundlage des Benutzerprofils umgesetzt wird, muss genau und logisch erfolgen.
* Es gibt für Benutzer nichts Frustrierenderes, als nur aufgrund der ungenauen Logik einer Regel Inhalte aufgezwungen oder vorenthalten zu bekommen.
* Daher müssen die Regeln gut durchdacht sein. Die Anforderungen des Benutzers müssen dabei immer im Vordergrund stehen. Dies kann sehr mühsam sein und darf nicht unterschätzt werden. Die Festlegung der geschäftlichen Regeln ist häufig aufwendiger als die technischen Maßnahmen bei der Implementierung der Personalisierung.

#### Wann ist sie einzusetzen? {#when-to-use}

* Wie viele Funktionen im Internet ist auch Personalisierung mit Vorsicht einzusetzen. Ist Ihr Einsatz wirklich von Vorteil für den Benutzer? Dies sollte immer die erste Überlegung sein. Darüber hinaus sollte ergründet werden, ob das gewünschte Ziel mit einer anderen Methode mit geringerem Aufwand erreicht werden kann. Mit der Personalisierung ist das Risiko verbunden, dass die Benutzer die Funktion nur ein einziges Mal konfigurieren (um zu sehen, wie sie funktioniert), da sie ihnen keine echten Vorteile verschafft.
* Personalisierung ist nur von Bedeutung, wenn der Inhalt dynamisch und gewissermaßen vom Benutzer abhängig ist. Werden allen Benutzern dieselben Inhalte angezeigt, ist die Personalisierung redundant.

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
| Kombinierte Anmeldung und Registrierung | Ermöglicht dem Benutzer, sich entweder bei einem vorhandenen Konto anzumelden oder sich für ein neues Konto zu registrieren. |
| Formular-Adressfeld | Ein komplexes Feld, das die Eingabe einer internationalen Adresse ermöglicht. |
| Formular-Beginn | Startet eine Formulardefinition |
| Formular-Captcha | Ein Feld, das aus einem automatisch aktualisierten alphanumerischen Wort besteht. Die Captcha-Komponente schützt Websites vor Bots.  |
| Formular-Kontrollkästchengruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Kontrollkästchen vorangestellt sind. Benutzer können mehrere Kontrollkästchen auswählen. |
| Formular-Dropdownliste | Mehrere Elemente, die als Dropdown-Liste angeordnet sind. Der Schalter für die Mehrfachauswahl gibt an, ob mehrere Elemente aus der Liste ausgewählt werden können. |
| Formular-Ende | Beendet die Formulardefinition |
| Formular-Datei-Upload | Ein Upload-Element, mit dem der Benutzer eine Datei zum Server hochladen kann. |
| Ausgeblendetes Formular-Feld | Dieses Feld wird dem Benutzer nicht angezeigt. Mit ihm kann ein Wert zum Client und zurück zum Server übertragen werden. Für dieses Feld gelten keine Beschränkungen. |
| Formular-Bildschaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, die als Bild dargestellt wird. |
| Formular-Kennwortfeld | Identisch mit einem Textfeld, doch nur eine Zeile ist zulässig und die Texteingabe des Benutzers ist im Feld nicht sichtbar. |
| Formular-Optionsfeldgruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Optionsschalter vorangestellt sind. Benutzer dürfen nur einen Optionsschalter auswählen. |
| Formular-Senden-Schaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, wobei der Titel als Text auf der Schaltfläche dargestellt wird. |
| Formular-Textfeld | Ein Textfeld, in das Benutzer Informationen eingeben können. |
| Meine Gadgets | Ermöglicht die Auswahl eines der verfügbaren Gadgets. |
| Profil – Avatar-Foto | Ermöglicht die Eingabe eines Avatar-Fotos. |
| Profil – Genauer Name | Eingabe von Namendetails, einschließlich Elemente wie Titel, zweiter Vorname und Suffix, falls erforderlich. |
| Profil – Anzeigename | Anzuzeigender Name. |
| Profil – E-Mail-Adresse | Eingabe einer E-Mail-Adresse. |
| Profil – Geschlecht | Ermöglicht die Eingabe des Geschlechts.  |
| Profil – Primäre Telefonnummer | Ermöglicht die Eingabe einer Telefonnummer.  |
| Profil – Primäre URL | Ermöglicht die Eingabe einer URL. |
| Profil – Allgemeine Texteigenschaft | Profil – Eigenschaften. |
| Anmelden | Ermöglicht die Eingabe eines Benutzernamens und eines Kennworts bei der Anmeldung. |
| Abmelden | Gibt den derzeit angemeldeten Benutzer an und stellt einen Link zum Abmelden zur Verfügung. |
| Tag-Cloud | Eine Tag-Cloud zeigt eine grafisch dargestellte Auswahl der Tags auf Ihrer Website |
| Teaser | Ein auf einer Hauptseite angezeigtes Stück Inhalt (für gewöhnlich ein Bild), das Benutzer zum Zugriff auf den darunterliegenden Inhalt „überreden“ soll. |

## Personalisierung und Community-Inhalte {#personalization-and-community-content}

Community-Funktionen wie Blogs, Foren und Kalender generieren Community-Inhalte, die gemeinhin als benutzergenerierte Inhalte bezeichnet werden. Wurden benutzergenerierte Inhalte in eine aus mehreren AEM-Instanzen bestehende Veröffentlichungsumgebung eingegeben (eine [Veröffentlichungsfarm](/help/communities/topologies.md)), war hierbei eines der größten Probleme die instanzenübergreifende Synchronisierung der benutzergenerierten Inhalte.

Mit der Erweiterung [AEM Communities 6.1](/help/communities/overview.md) wird dieses Problem durch einen [gemeinsamen Speicher für benutzergenerierten Inhalt (UGC, User Generated Content)](/help/communities/working-with-srp.md) gelöst. Im Hinblick auf die Personalisierung umfasst Communities die [Anmeldung bei sozialen Netzwerken](/help/communities/social-login.md) – die Möglichkeit, den Besuchern der Seite die Anmeldung über Facebook und Twitter zu ermöglichen.

Ohne Communities-Erweiterung gibt es verschiedene Methoden, das Problem der Konsistenz des benutzergenerierten Inhalts anzugehen:

* Synchronisierung der verschiedenen Veröffentlichungsinstanzen, falls erforderlich
* Senden des UGC von der Veröffentlichungsinstanz an die Autorenumgebung, von wo aus dieser auf eine ähnliche Weise wie Seiteninhalte veröffentlicht werden kann

Die Methode, die verwendet wird, um die Konsistenz des benutzergenerierten Inhalts über mehrere Veröffentlichungsinstanzen hinweg zu erzielen, sollte sorgfältig gestaltet und auf ihre Leistung und Konsistenz hin überprüft werden.
