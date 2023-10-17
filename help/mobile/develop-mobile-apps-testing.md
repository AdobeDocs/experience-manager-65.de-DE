---
title: Testen von mobilen Apps
description: Hier erfahren Sie, wie Sie Ihre mobilen Apps mit verschiedenen Tools automatisieren oder manuell testen können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing
content-type: reference
exl-id: e10e1904-7016-4eb0-9408-36297285f378
source-git-commit: 06a6d4e0ba2aeaefcfb238233dd98e8bbd6731da
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 1%

---

# Testen von mobilen Apps{#testing-mobile-apps}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Angesichts der breiten Palette von Geräten auf dem Markt und Geräten, die veröffentlicht werden, ist das Testen Ihrer Apps unerlässlich geworden. In diesem Bereich können Funktionalität und Benutzerfreundlichkeit niedrige Bewertungen in einem Appstore generieren, aber ein einzelner Fehler kann dazu führen, dass Ihre App deinstalliert wird. Bei Ihren Testplänen und der Qualitätssicherung muss besondere Aufmerksamkeit geschenkt werden. Der folgende Link behandelt viele Themen, die allgemein angesprochen werden müssen, wie z. B. die Identifizierung Ihrer Umgebung, die Definition von Testfällen, Arten von Tests, Annahmen und die Einbeziehung von Kunden. Außerdem werden Tools erläutert, die bei den Tests helfen. Interne Tools wie [Hobbes](/help/sites-developing/hobbes.md), kann beim webbasierten UI-Test helfen. [Tough Day](/help/sites-developing/tough-day.md) Sie können Ihre Instanzen mit einer simulierten Last unter Stress stellen. Wenn Ihre Testumgebung bereits über Erfahrung mit Drittanbieter-Tools wie Selenium verfügt, können auch diese verwendet werden.

Bei der Entwicklung einer mobilen App gibt es viele neue Probleme, die speziell für Geräte gelten, die zusammen mit herkömmlichen Tests angesprochen werden müssen.

* Funktion - Werden alle Anforderungen von Ihrer App erfüllt?
* Benutzerfreundlichkeit - Ist die App von Ihrem Kunden einfach zu verwenden und zu verstehen?
* Leistung - Was passiert während einer Spitze bei der Verwendung? Sind die App-Elemente, wie Wischen und Karussells, schnell und beeinträchtigen Sie nicht das Erlebnis?
* Fehler oder Unterbrechungen - Was passiert, wenn während der Ausführung der App ein eingehender Aufruf oder eine eingehende Benachrichtigung erfolgt? Was passiert, wenn das Netzwerk ausfällt oder ausgeschaltet ist?
* Installation und Updates - Wie funktioniert die Installation? Wie werden Aktualisierungen veröffentlicht?
* Technisch - Verbraucht Ihre App zu viel Strom von einem Gerät?
* Lokalisierung - Sind alle Bereiche in Ihrer App übersetzt?
* Zertifizierung - Wurde Ihre App zertifiziert? Können Kunden darauf vertrauen, dass alle gesetzlichen Datenschutzbestimmungen eingehalten werden?

Diese Fragen sollten während der automatisierten und manuellen Tests beantwortet werden.

## Automatisierte Tests {#automated-testing}

Ein gewisser Grad automatisierter Tests sollte durchgeführt werden, um die verschiedenen Bildschirmgrößen, Speicherbeschränkungen, Eingabemethoden und Betriebssysteme abzudecken. Sie deckt nicht nur viele der Testfälle ab, sondern kann auch Regressionstests beschleunigen, wenn neue Funktionen oder Geräte eingeführt werden. Idealerweise sollten Ihre Automatisierungstools Doppelarbeit reduzieren oder begrenzen. Verwenden Sie Tools oder Frameworks, damit Ihre Testbemühungen auf allen Plattformen gelten. Die folgende Tabelle zeigt eine vereinfachte Struktur einer Testumgebung für webbasierte Benutzeroberflächentests und Tests mobiler Apps. Die linke Seite des Diagramms zeigt eine Reihe von Selenium-Knoten mit Browsern an. SeleniumGrid kann allgemeine, webbasierte UI-Tests für jeden dieser Knoten auswerten. Der Selenium-Hub kann für plattformübergreifende App-Tests auch eine Verbindung zu Appium herstellen. Es werden nur Simulatoren angezeigt, Sie können aber adb für Android™- und Xcode-Dienstprogramme für iOS-Geräte integrieren. Links finden Sie weiter unten in diesem Dokument, in dem Sie spezifische Details zu den erwähnten Tools finden.

![chlimage_1](assets/chlimage_1.jpeg)

## Manuelle Prüfung {#manual-testing}

Zusätzlich zu automatisierten Tests sollte Ihre App einen manuellen Testzyklus durchlaufen. Kunden, die die App auf einem echten Gerät ausführen, können nicht durch ein Skript dupliziert werden. Auch hier haben Sie viele Möglichkeiten. Sie können eine Plattform wie HockeyApp verwenden, um festzulegen, wer Zugriff hat und Feedback erfassen kann. Oder Sie können den gesamten Prozess an einen Dienst wie UTest, ElusiveStars oder Test auslagern. Wenn Sie über eine Gruppe interner Tester verfügen, aber nicht über verschiedene Geräte verfügen, gibt es Cloud-Services, mit denen Sie manuelle Tests an ihrem Gerätesool durchführen können. Ein solcher Dienst, der dies bereitstellt, ist SauceLabs. Sie können Apps auch remote für PhoneGap Enterprise erstellen und auf lokalen Geräten installieren, um Akzeptanztests oder Demos durchzuführen. Siehe PhoneGap (`https://phonegap.com/`) auf der Website mit den neuesten Funktionen und Dokumentation. Unabhängig vom Ansatz sollten manuelle Tests Folgendes tun:

* eine große Zielgruppe von Tester erreichen,
* Testen Sie mit einem großen Pool von Geräten (idealerweise echte Geräte, Simulatoren/Emulatoren jedoch, wenn keine echten Geräte verfügbar sind).
* Feedback geben:

   * Absturzberichte,
   * Analyse/Tracking,
   * Benutzerfreundlichkeit,
   * besondere Aufmerksamkeit,
   * Leistung,
   * Daten-/Stromverbrauch usw.

## Tools {#tools}

Zum Testen von mobilen Apps stehen zahlreiche Tools zur Verfügung. Die Auswahl der zu verwendenden sollte auf Ihrer spezifischen Situation basieren: Funktionen, Preis, Support, Abdeckung usw. Im Folgenden finden Sie eine kleine Beschreibung einiger der verfügbaren Tools und Dienste.

**Selenium**

* Framework, das eine API für Testskripte enthält, um WebDriver zuzuführen und verschiedene Browser zu steuern.
* Sie können dies mit Appium zum Testen auf echten Geräten verwenden.
* SeleniumGrid leitet Tests zum parallelen Testen über Knoten hinweg.
* Selenium IDE hilft, das Schreiben von Testfällen zu reduzieren.

Weitere Informationen finden Sie unter [https://www.selenium.dev/](https://www.selenium.dev/).

**Testdroid**

* Ein Cloud-basierter Testdienst mit kontinuierlichen Integrationshaken und echten Gerätetests.
* Dazu gehört ein App-Crawler, der die Gerätekompatibilität überprüft, Protokolle analysiert, Ansichten durchsucht, Screenshots erstellt und die Leistung überwacht.

Weitere Informationen finden Sie unter [https://testdroid.com/](https://testdroid.com/).

**Appium**

* Appium ist ein beliebtes plattformübergreifendes Framework zur Automatisierung mobiler Tests.
* Außerdem verfügt ein Inspektor über Datensatzfähigkeiten zur Unterstützung von Code-Testfällen.

Weitere Informationen finden Sie unter [https://appium.io/](https://appium.io/).

**SauceLabs**

* SauceLabs bietet Cloud-basierte Tests und ist mit kontinuierlicher Integration integriert.
* Tests werden automatisch in der Cloud-Umgebung ausgeführt. Alternativ können Sie ein bestimmtes Gerät oder eine bestimmte Plattform starten und manuelle Tests durchführen, um Probleme zu beheben.

Weitere Informationen finden Sie unter [https://saucelabs.com/](https://saucelabs.com/).

**AppTestNow**

* Ein Outsourcing-Dienst, der Ihre mobilen Apps testet.
* Es umfasst einen großen Pool von Geräten und bietet eine breite Palette von Testtypen: Leistung, Qualität, Funktionalität, Zertifizierung, Lokalisierung, Datenverbrauch usw.

Weitere Informationen finden Sie unter [https://apptestnow.com/](https://apptestnow.com/).

**HockeyApp**

* HockeyApp fällt unter den manuellen Test, bei dem die mobile App an einen persönlichen Appstore gesendet wird, in dem Tester sie herunterladen und ausprobieren können.

Weitere Informationen finden Sie unter [https://hockeyapp.net/features/](https://hockeyapp.net/features/).

**Jenkins**

* Obwohl es sich nicht um ein Testwerkzeug handelt, ist Jenkins ein kontinuierliches Integrations-Framework, das das Rückgrat für automatisierte Tests bildet. Zur Erweiterung der Funktionalität stehen zahlreiche Drittanbieter-Plug-ins zur Verfügung. Ein Beispiel: Das SeleniumGrid-Plug-in bietet eine Benutzeroberfläche zur Verwaltung des Selenium-Hub und der Selenium-Knoten.

Weitere Informationen finden Sie unter [https://www.jenkins.io/](https://www.jenkins.io/) und [https://plugins.jenkins.io/](https://plugins.jenkins.io/).
