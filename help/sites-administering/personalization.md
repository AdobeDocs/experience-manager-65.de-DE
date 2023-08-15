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
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 58%

---

# Personalisierung  {#personalization}

## Was ist Personalisierung? {#what-is-personalization}

Heute stehen immer mehr Inhalte zur Verfügung, sei es im Internet, im Extranet oder im Intranet.

Personalisierung konzentriert sich darauf, Benutzern eine maßgeschneiderte Umgebung mit dynamischen Inhalten bereitzustellen, die entsprechend ihren spezifischen Anforderungen ausgewählt werden. Dies kann anhand von vordefinierten Profilen, der Benutzerauswahl oder dem interaktiven Benutzerverhalten geschehen.

Die Personalisierung umfasst drei Hauptelemente:

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

* Regelbasiert: Geschäftsführer definieren spezifische Regeln für Aktionen, die auf bestimmten Profilen und/oder Verhaltensweisen basieren.
* Einfache Filterung: Die Auswahl erfolgt auf Basis vordefinierter Profile auf Benutzer- und/oder Gruppenebene.
* Kollaboratives Filtern/Empfehlungsfiltern: Das Benutzerverhalten wird unter Einhaltung vordefinierter Regeln registriert. Diese Regeln basieren auf dem Verhalten gleich gesinnter Personen. Die gesammelten Informationen werden verwendet, um die dem Benutzer angezeigten Informationen anzupassen, insbesondere in Form von Empfehlungen.

## Wie und wann kann die Personalisierung verwendet werden? {#how-and-when-can-personalization-be-used}

Die Personalisierung kann in vielen Fällen verwendet werden, wie zum Beispiel:

### Intranetseiten {#intranet-pages}

* Inhalte können basierend auf dem Standort, der Abteilung und/oder der Rolle eines Benutzers angeboten werden, die bereits in einem internen Netzwerk festgelegt ist.
* Je nach der verfügbaren Auswahl hat der Benutzer noch weitere Auswahlmöglichkeiten.

### Spezifische begrenzte Zielbenutzergruppen – Extranets {#extranets}

* Benutzer benötigen zur Autorisierung einen Login. Dieser wird mit einem Profil verknüpft, das für die Personalisierung erforderliche Informationen bereitstellt, möglicherweise Details wie Standort, Beziehung zum Produkt, Nutzungsverlauf, Budgetierungsaufgaben usw.
* Solche Instanzen können sich auf Websites erstrecken, z. B.:
* Unternehmen, die Websites für einen hochspezialisierten Bereich ihres Marktes bereitstellen, z. B. ein Pharmaunternehmen, das eine spezialisierte Website für Ärzte bereitstellt.
* Unternehmen, die Websites bereitstellen, mit denen ihre Kunden aktuelle Konto- und Rechnungsinformationen anzeigen können, so zum Beispiel Telekommunikationsanbieter.

### Verkaufs- und Vertriebs-Website {#sales-site}

* Verkaufs- und Vertriebswebsites wie Amazon können ein Benutzerprofil mit der Kauf- und Suchhistorie des Benutzers kombinieren, um Empfehlungen dazu auszusprechen, was den Benutzer als Nächstes interessieren könnte.

### Such-Websites {#search-site}

* Viele große Suchmaschinenwebsites verfügen über leistungsstarke Analyse-Tools, die das Benutzerverhalten, die eingegebenen Suchbegriffe und die tatsächlich besuchten Websites aufzeichnen. Dies wird dann für die benutzerdefinierte Anpassung der bereitgestellten Inhalte verwendet – vor allem im Hinblick auf die Anzeige von Werbung.

### Stärken der Personalisierung und zu berücksichtigende Punkte {#strengths-of-personalization-and-points-to-consider}

Personalisierung sollte aus folgenden Gründen eingesetzt werden:

* Ein Benutzer kann eine bequeme, fokussierte Website erleben.
* Mit der Personalisierung kann der Zugriff automatisch auf die neueste Version des Inhalts erweitert werden.
* Benutzer können über Social Collaboration-Funktionen miteinander kommunizieren, da sie anhand ihrer Profile identifiziert werden können.
* Ein Benutzer kann den Inhalt erhalten, den er zur Erfüllung einer bestimmten Aufgabe benötigt. Innerhalb des Intranets eines Unternehmens kann dies ein unschätzbares Instrument zur Verbreitung von Informationen sein.
* Ein Benutzer kann mit den benötigten/gewünschten Inhalten versorgt werden, wodurch die Zeit für die Durchführung von Suchvorgängen verkürzt wird.
* Der Inhaltsanbieter kann den Inhalt steuern, der für bestimmte Benutzergruppen angezeigt werden soll.
* Regeln können definiert werden, um Inhalte basierend auf Kombinationen aus Benutzermerkmalen und -verhalten bereitzustellen. Dies bietet einen ausgereiften Mechanismus zur Personalisierung ihres Web-Erlebnisses.

Berücksichtigen Sie beim Einsetzen von Personalisierung Folgendes:

#### Leistung {#performance}

* Natürlich hat die zusätzliche Analyse und Auswertung Auswirkungen auf die Leistung. Die verwendeten Methoden sind jedoch hoch entwickelt und können optimiert werden, um die Auswirkungen zu minimieren.

#### Autorisierung {#authorization}

* Personalisierung erfordert einen Anmeldemechanismus, da die Website den Benutzer identifizieren muss.

#### Caching {#caching}

* Die Speicherung im Cache ist ein Aspekt, der sich für den Benutzer im Zusammenhang mit Leistung und Genauigkeit bemerkbar macht: Wie schnell stellt die Website personalisierte Inhalte bereit? Und sind diese immer aktuell?
* Die Speicherung im Cache ist eine wichtige Überlegung für die Konfiguration der Personalisierung und es ist ein gewisser Zeitaufwand erforderlich, um sicherzustellen, dass die richtige Implementierung verwendet wird.

>[!TIP]
>
>Die Auswirkungen der Personalisierung auf die Leistung und damit zusammenhängende Themen zum Zwischenspeichern werden im Dokument [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) näher erläutert.

#### Genauigkeit der Regeln {#accuracy}

* Die Personalisierung, die durch die Verfolgung des Benutzerverhaltens oder durch die Festlegung von Regeln auf der Grundlage des Benutzerprofils durchgeführt wird, muss akkurat und logisch sein.
* Es gibt nichts Frustrierenderes für den Benutzer, als dass ihm Inhalte aufgrund der ungenauen Logik einer Regel aufgezwungen oder verweigert werden.
* Daher müssen die Regeln gut durchdacht sein. Die Anforderungen des Benutzers müssen dabei immer im Vordergrund stehen. Dies kann sehr mühsam sein und darf nicht unterschätzt werden. Die Festlegung der geschäftlichen Regeln ist häufig aufwendiger als die technischen Maßnahmen bei der Implementierung der Personalisierung.

#### Wann ist sie einzusetzen? {#when-to-use}

* Wie bei vielen Funktionen im Internet sollte die Personalisierung mit Vorsicht verwendet werden. Wird die Nutzung wirklich dem Benutzer zugute kommen? sollte immer die erste Überlegung sein - oder ob das gewünschte Ziel mit weniger Aufwand durch eine andere Methode erreicht werden kann. Mit der Personalisierung ist das Risiko verbunden, dass die Benutzer die Funktion nur ein einziges Mal konfigurieren (um zu sehen, wie sie funktioniert), da sie ihnen keine echten Vorteile verschafft.
* Personalisierung ist nur von Bedeutung, wenn der Inhalt dynamisch und gewissermaßen vom Benutzer abhängig ist. Werden allen Benutzern dieselben Inhalte angezeigt, ist die Personalisierung redundant.

#### Vertraulichkeit {#confidentiality}

* Viele Benutzer machen sich Sorgen um Datenschutz und Sicherheit. Insbesondere bezüglich der Daten, die beim Tracking ihres Verhaltens beim Surfen im Internet abgerufen werden.

## Personalisierung und Zugriff {#personalization-and-access}

Personalisierung sollte getrennt von der Zugriffskontrolle betrachtet werden, sie stehen jedoch in Wechselbeziehung zueinander.

Die Personalisierung selbst erzeugt keine Form der Zugriffssteuerung. Es handelt sich lediglich um eine Methode zur Steuerung dessen, was der Benutzer sieht. Es schränkt den Benutzer nicht vom Zugriff auf andere Inhalte ein, und wie bei allen Inhalten müssen ihm bereits die richtigen Zugriffssteuerungen zugewiesen sein.

Die Zugriffskontrolle kann jedoch verwendet werden, um eine Form der Personalisierung zu erstellen. Wenn Sie einem Benutzer den Zugriff auf Inhalte erlauben oder verweigern, wirkt sich dies unweigerlich auf die Auswahl der verfügbaren Inhalte aus - und personalisiert so sein Web-Erlebnis.

## Für die Personalisierung verfügbare Komponenten {#components-available-for-personalization}

Zur Personalisierung stehen verschiedene Komponenten mit AEM zur Verfügung. Einige ermöglichen es Benutzern, sich anzumelden und ihre Profile zu bearbeiten, andere (wie My Gadgets) ermöglichen es Benutzern, eine bestimmte Seite zu konfigurieren:

| Titel im Sidekick | Zweck |
|---|---|
| Geprüftes Kennwort-Feld | Fordert zur Eingabe des Kennworts und Bestätigung des Kennworts auf. |
| Kombinierte Anmeldung und Registrierung | Ermöglicht dem Benutzer, sich entweder bei einem vorhandenen Konto anzumelden oder sich für ein neues Konto zu registrieren. |
| Formular-Adressfeld | Ein komplexes Feld, das die Eingabe einer internationalen Adresse ermöglicht. |
| Formular-Beginn | Startet eine Formulardefinition |
| Formular-Captcha | Ein Feld, das aus einem automatisch aktualisierten alphanumerischen Wort besteht. Die Captcha-Komponente schützt Websites vor Bots. |
| Formular-Kontrollkästchengruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Kontrollkästchen vorangestellt sind. Benutzer können mehrere Kontrollkästchen auswählen. |
| Formular-Dropdownliste | Mehrere Elemente, die als Dropdown-Liste angeordnet sind. Der Schalter für die Mehrfachauswahl gibt an, ob mehrere Elemente aus der Liste ausgewählt werden können. |
| Formular-Ende | Beendet die Formulardefinition |
| Formular-Datei-Upload | Ein Upload-Element, mit dem der Benutzer eine Datei zum Server hochladen kann. |
| Ausgeblendetes Formular-Feld | Dieses Feld wird dem Benutzer nicht angezeigt. Sie kann verwendet werden, um einen Wert an den Client und zurück an den Server zu übertragen. Dieses Feld sollte keine Einschränkungen aufweisen. |
| Formular-Bildschaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, die als Bild dargestellt wird. |
| Formular-Kennwortfeld | Identisch mit einem Textfeld, doch nur eine Zeile ist zulässig und die Texteingabe des Benutzers ist im Feld nicht sichtbar. |
| Formular-Optionsfeldgruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Optionsschalter vorangestellt sind. Benutzer dürfen nur ein Optionsfeld auswählen. |
| Formular-Senden-Schaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, wobei der Titel als Text auf der Schaltfläche dargestellt wird. |
| Formular-Textfeld | Ein Textfeld, in das Benutzer Informationen eingeben können. |
| Meine Gadgets | Hier können Sie eine Auswahl an verfügbaren Gadgets einbeziehen. |
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

Community-Funktionen wie Blogs, Foren und Kalender führen zur Erstellung von Community-Inhalten, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden. Wurden benutzergenerierte Inhalte in eine aus mehreren AEM-Instanzen bestehende Veröffentlichungsumgebung eingegeben (eine [Veröffentlichungsfarm](/help/communities/topologies.md)), war hierbei eines der größten Probleme die instanzenübergreifende Synchronisierung der benutzergenerierten Inhalte.

Mit der Erweiterung [AEM Communities 6.1](/help/communities/overview.md) wird dieses Problem durch einen [gemeinsamen Speicher für benutzergenerierten Inhalt (UGC, User Generated Content)](/help/communities/working-with-srp.md) gelöst. Im Hinblick auf die Personalisierung umfasst Communities die [Anmeldung bei sozialen Netzwerken](/help/communities/social-login.md) – die Möglichkeit, den Besuchern der Seite die Anmeldung über Facebook und Twitter zu ermöglichen.

Ohne Communities-Erweiterung gibt es verschiedene Methoden, das Problem der Konsistenz des benutzergenerierten Inhalts anzugehen:

* Synchronisierung der verschiedenen Veröffentlichungsinstanzen, falls erforderlich
* Senden des UGC von der Veröffentlichungsinstanz an die Autorenumgebung, von wo aus dieser auf eine ähnliche Weise wie Seiteninhalte veröffentlicht werden kann

Die Methode, die verwendet wird, um die Konsistenz des benutzergenerierten Inhalts über mehrere Veröffentlichungsinstanzen hinweg zu erzielen, sollte sorgfältig gestaltet und auf ihre Leistung und Konsistenz hin überprüft werden.
