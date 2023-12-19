---
title: Personalisierung
description: Erfahren Sie mehr über die Personalisierung in Adobe Experience Manager, um dem Benutzer eine maßgeschneiderte Umgebung mit dynamischen Inhalten bereitzustellen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 3a550a33-b54b-4217-b9a6-b5a7971276ee
source-git-commit: 941e5d7574d31622f50e50e717c21cd2eba2e602
workflow-type: tm+mt
source-wordcount: '1697'
ht-degree: 92%

---

# Personalisierung  {#personalization}

## Was ist Personalisierung? {#what-is-personalization}

Heutzutage stehen immer mehr Inhalte zur Verfügung – auf Websites im Internet, im Extranet oder im Intranet.

Personalisierung konzentriert sich darauf, Benutzenden eine maßgeschneiderte Umgebung mit dynamischen Inhalten bereitzustellen, die entsprechend ihren spezifischen Anforderungen ausgewählt werden. Dies kann anhand von vordefinierten Profilen, der Benutzerauswahl oder dem interaktiven Benutzerverhalten geschehen.

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

* Regelbasiert: Geschäftsführerinnen und Geschäftsführer definieren spezifische Regeln für Aktionen, die auf bestimmten Profilen und/oder Verhaltensweisen basieren.
* Einfache Filterung: Die Auswahl erfolgt auf Basis vordefinierter Profile auf Benutzer- und/oder Gruppenebene.
* Kollaboratives Filtern/Empfehlungsfiltern: Das Benutzerverhalten wird unter Einhaltung vordefinierter Regeln registriert. Diese Regeln basieren auf dem Verhalten, das bei Personen mit ähnlichen Interessen beobachtet wurde. Die erfassten Informationen werden verwendet, um die den Benutzenden angezeigten Informationen anzupassen, insbesondere in Form von Empfehlungen.

## Wie und wann kann die Personalisierung verwendet werden? {#how-and-when-can-personalization-be-used}

Die Personalisierung kann in vielen Fällen verwendet werden, wie zum Beispiel:

### Intranetseiten {#intranet-pages}

* Inhalte können basierend auf dem Standort, der Abteilung und/oder der Rolle eines Benutzers angeboten werden, die bereits in einem internen Netzwerk festgelegt ist.
* Je nach der verfügbaren Auswahl hat der Benutzer noch weitere Auswahlmöglichkeiten.

### Spezifische begrenzte Zielbenutzergruppen – Extranets {#extranets}

* Benutzer benötigen zur Autorisierung einen Login. Dieser wird mit einem Profil verknüpft, das für die Personalisierung erforderliche Informationen bereitstellt, möglicherweise Details wie Standort, Beziehung zum Produkt, Nutzungsverlauf, Budgetierungsverpflichtungen usw.
* Solche Instanzen können sich über Sites erstrecken wie etwa:
* Unternehmen, die Websites für einen hoch spezialisierten Bereich ihres Marktes anbieten, z. B. ein Pharmaunternehmen, das eine spezielle Website für Ärztinnen und Ärzte bereitstellt.
* Unternehmen, die Websites bereitstellen, die es ihren Kunden ermöglichen, aktuelle Konto- und Rechnungsinformationen anzuzeigen, wie beispielsweise Telefonanbieter.

### Verkaufs- und Vertriebs-Website {#sales-site}

* Verkaufs- und Vertriebswebsites wie Amazon können ein Benutzerprofil mit der Kauf- und Suchhistorie des Benutzers kombinieren, um Empfehlungen dazu auszusprechen, was den Benutzer als Nächstes interessieren könnte.

### Such-Websites {#search-site}

* Viele große Suchmaschinenwebsites verfügen über leistungsstarke Analyse-Tools, die das Benutzerverhalten, die eingegebenen Suchbegriffe und die tatsächlich besuchten Websites aufzeichnen. Dies wird dann für die benutzerdefinierte Anpassung der bereitgestellten Inhalte verwendet – vor allem im Hinblick auf die Anzeige von Werbung.

### Stärken der Personalisierung und zu berücksichtigende Punkte {#strengths-of-personalization-and-points-to-consider}

Personalisierung sollte aus folgenden Gründen eingesetzt werden:

* Benutzende profitieren von einer bequemen, fokussierten Website.
* Personalisierung kann für die automatische Übertragung des Zugriffs auf die neueste Version der Inhalte genutzt werden.
* Benutzende können über Social-Collaboration-Funktionen miteinander kommunizieren, da sie anhand ihrer Profile identifiziert werden können.
* Einer Benutzerin oder einem Benutzer können die benötigten Inhalte für die Ausführung einer bestimmten Aufgabe bereitgestellt werden. Innerhalb des Intranets eines Unternehmens kann dies ein wertvolles Instrument zur Verbreitung von Informationen sein.
* Benutzende können mit den benötigten/gewünschten Inhalten versorgt werden, sodass der Zeitaufwand für Suchvorgänge verringert wird.
* Menschen, die Inhalte anbieten, können den Inhalt steuern, der für bestimmte Gruppen von Benutzenden angezeigt werden soll.
* Es können Regeln definiert werden, um Inhalte anhand von Kombinationen aus Merkmalen und Verhalten von Benutzenden bereitzustellen. Dies stellt einen ausgeklügelten Mechanismus für die Personalisierung ihres Web-Erlebnisses bereit.

Berücksichtigen Sie beim Einsetzen von Personalisierung Folgendes:

#### Leistung {#performance}

* Natürlich hat die zusätzliche Analyse und Auswertung Auswirkungen auf die Leistung. Die eingesetzten Methoden sind äußerst anspruchsvoll, können jedoch optimiert werden, um negative Auswirkungen zu minimieren.

#### Autorisierung {#authorization}

* Personalisierung erfordert einen Anmeldemechanismus, da die Website den Benutzer identifizieren muss.

#### Caching {#caching}

* Die Speicherung im Cache ist ein Aspekt, der sich für den Benutzer im Zusammenhang mit Leistung und Genauigkeit bemerkbar macht: Wie schnell stellt die Website personalisierte Inhalte bereit? Und sind diese immer aktuell?
* Die Speicherung im Cache ist eine wichtige Überlegung für die Konfiguration der Personalisierung und es ist ein gewisser Zeitaufwand erforderlich, um sicherzustellen, dass die richtige Implementierung verwendet wird.

>[!TIP]
>
>Die Auswirkungen der Personalisierung auf die Leistung und damit zusammenhängende Themen zum Zwischenspeichern werden im Dokument [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) näher erläutert.

#### Genauigkeit der Regeln {#accuracy}

* Die Personalisierung, die durch Tracking des Benutzerverhaltens oder durch Festlegung von Regeln auf Grundlage des Benutzerprofils durchgeführt wird, muss akkurat und logisch sein.
* Es gibt nichts Frustrierenderes für Benutzende, als dass ihnen aufgrund der ungenauen Logik einer Regel Inhalte aufgezwungen oder verweigert werden.
* Daher müssen die Regeln gut durchdacht sein. Die Anforderungen des Benutzers müssen dabei immer im Vordergrund stehen. Dies kann viel Aufwand erfordern und ist nicht zu unterschätzen. Die Definition der Geschäftsregeln übersteigt oft den technischen Aufwand bei der Implementierung der Personalisierung.

#### Wann ist sie einzusetzen? {#when-to-use}

* Wie bei vielen Funktionen im Internet sollte die Personalisierung mit Vorsicht verwendet werden. Ist ihr Einsatz wirklich von Vorteil für die Benutzenden? Dies sollte immer die erste Überlegung sein. Darüber hinaus sollte ergründet werden, ob das gewünschte Ziel vielleicht mit weniger Aufwand durch eine andere Methode erreicht werden kann. Mit der Personalisierung ist das Risiko verbunden, dass die Benutzer die Funktion nur ein einziges Mal konfigurieren (um zu sehen, wie sie funktioniert), da sie ihnen keine echten Vorteile verschafft.
* Personalisierung ist nur von Bedeutung, wenn der Inhalt dynamisch und gewissermaßen vom Benutzer abhängig ist. Werden allen Benutzern dieselben Inhalte angezeigt, ist die Personalisierung redundant.

#### Vertraulichkeit {#confidentiality}

* Viele Benutzende machen sich Sorgen um Datenschutz und -sicherheit. Insbesondere gilt dies für Daten, die beim Tracking ihres Verhaltens beim Surfen im Internet abgerufen werden.

## Personalisierung und Zugriff {#personalization-and-access}

Personalisierung sollte separat von der Zugriffssteuerung betrachtet werden, allerdings gibt es einen Zusammenhang zwischen beidem.

Die Personalisierung selbst sorgt für keinerlei Form von Zugriffssteuerung. Es handelt sich lediglich um eine Methode zur Steuerung dessen, was Benutzende sehen, und hält sie nicht vom Zugriff auf andere Inhalte ab. Wie bei allen Inhalten müssen die richtigen Zugriffssteuerungen bereits zugewiesen sein.

Allerdings kann die Zugangssteuerung verwendet werden, um eine Art von Personalisierung herzustellen. Wenn Sie Benutzenden den Zugriff auf Inhalte erlauben bzw. verweigern, wirkt sich dies unweigerlich auf die Auswahl der verfügbaren Inhalte aus – und personalisiert so das Web-Erlebnis für sie.

## Verfügbare Komponenten für die Personalisierung {#components-available-for-personalization}

Mit AEM werden verschiedene Komponenten für die Personalisierung bereitgestellt. Einige ermöglichen es Benutzenden, sich anzumelden und ihre Profile zu bearbeiten; durch andere (wie „Meine Gadgets“) können Benutzende eine bestimmte Seite konfigurieren:

| Titel im Sidekick | Zweck |
|---|---|
| Geprüftes Kennwort-Feld | Fordert zur Eingabe des Kennworts und Bestätigung des Kennworts auf. |
| Kombinierte Anmeldung und Registrierung | Ermöglicht dem Benutzer, sich entweder bei einem vorhandenen Konto anzumelden oder sich für ein neues Konto zu registrieren. |
| Formular-Adressfeld | Ein komplexes Feld, das die Eingabe einer internationalen Adresse ermöglicht. |
| Formular-Beginn | Startet eine Formulardefinition |
| Formular-Captcha | Ein Feld, das aus einem automatisch aktualisierten, alphanumerischen Wort besteht.  Die Captcha-Komponente schützt Websites vor Bots. |
| Formular-Kontrollkästchengruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Kontrollkästchen vorangestellt sind. Benutzende können mehrere Kontrollkästchen auswählen. |
| Formular-Dropdownliste | Mehrere Elemente, die als Dropdown-Liste angeordnet sind. Der Schalter für die Mehrfachauswahl gibt an, ob mehrere Elemente aus der Liste ausgewählt werden können. |
| Formular-Ende | Beendet die Formulardefinition |
| Formular-Datei-Upload | Ein Upload-Element, mit dem der Benutzer eine Datei zum Server hochladen kann. |
| Ausgeblendetes Formular-Feld | Dieses Feld wird der Benutzerin bzw. dem Benutzer nicht angezeigt. Es wird verwendet, um einen Wert an den Client und zurück zum Server zu übermitteln.  Für dieses Feld gelten keine Beschränkungen. |
| Formular-Bildschaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, die als Bild dargestellt wird. |
| Formular-Kennwortfeld | Identisch mit einem Textfeld, doch nur eine Zeile ist zulässig und die Texteingabe des Benutzers ist im Feld nicht sichtbar. |
| Formular-Optionsfeldgruppe | Mehrere Elemente, die als Liste angeordnet sind und denen Optionsschalter vorangestellt sind. Benutzende dürfen nur ein einziges Optionsfeld auswählen. |
| Formular-Senden-Schaltfläche | Eine zusätzliche Senden-Schaltfläche für das Formular, wobei der Titel als Text auf der Schaltfläche dargestellt wird. |
| Formular-Textfeld | Ein Textfeld, in das Benutzer Informationen eingeben können. |
| Meine Gadgets | Ermöglicht die Auswahl eines der verfügbaren Gadgets. |
| Profil – Avatar-Foto | Ermöglicht die Eingabe eines Avatar-Fotos. |
| Profil – Genauer Name | Eingabe von Namensdetails, einschließlich Elementen wie Titel, Vorname und Suffix, falls erforderlich. |
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

Mit Community-Funktionen wie Blogs, Foren und Kalendern werden Community-Inhalte erstellt, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden. Wurden benutzergenerierte Inhalte in eine aus mehreren AEM-Instanzen bestehende Veröffentlichungsumgebung eingegeben (eine [Veröffentlichungsfarm](/help/communities/topologies.md)), war hierbei eines der größten Probleme die instanzenübergreifende Synchronisierung der benutzergenerierten Inhalte.

Mit der Erweiterung [AEM Communities 6.1](/help/communities/overview.md) wird dieses Problem durch einen [gemeinsamen Speicher für benutzergenerierten Inhalt (UGC, User Generated Content)](/help/communities/working-with-srp.md) gelöst. Im Hinblick auf die Personalisierung umfasst Communities die [Anmeldung bei sozialen Netzwerken](/help/communities/social-login.md) – die Möglichkeit, den Besuchern der Seite die Anmeldung über Facebook und Twitter zu ermöglichen.

Ohne Communities-Erweiterung gibt es verschiedene Methoden, das Problem der Konsistenz des benutzergenerierten Inhalts anzugehen:

* Synchronisierung der verschiedenen Veröffentlichungsinstanzen, falls erforderlich
* Senden des UGC von der Veröffentlichungsinstanz an die Autorenumgebung, von wo aus dieser auf eine ähnliche Weise wie Seiteninhalte veröffentlicht werden kann

Die Methode, die verwendet wird, um UGC-Konsistenz in einer Veröffentlichungsumgebung aus mehreren Veröffentlichungsinstanzen zu erzielen, sollte sorgfältig konzipiert und auf Leistung und Konsistenz getestet werden.
