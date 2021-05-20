---
title: Testen von mobilen Apps
seo-title: Testen von mobilen Apps
description: Testen von mobilen Apps
seo-description: 'null'
uuid: 3b402d34-5cab-4280-b8b9-88ad9f8fc5e4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing
content-type: reference
discoiquuid: 5a98e1bd-f5c1-4f2f-ac02-dbd005dc1de7
exl-id: e10e1904-7016-4eb0-9408-36297285f378
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 2%

---

# Testen von mobilen Apps{#testing-mobile-apps}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Angesichts der breiten Palette von Geräten auf dem Markt und Geräten, die veröffentlicht werden, ist das Testen Ihrer Apps sehr wichtig geworden. In diesem Bereich können Funktionalität und Benutzerfreundlichkeit niedrige Bewertungen in einem Appstore generieren, aber ein einzelner Fehler kann dazu führen, dass Ihre App deinstalliert wird. Bei Ihren Testplänen und der Qualitätssicherung muss besondere Aufmerksamkeit geschenkt werden. Der folgende Link behandelt viele Themen, die allgemein angesprochen werden müssen, z. B. die Identifizierung Ihrer Umgebung, die Definition von Testfällen, Arten von Tests, Annahmen, Kundenbeteiligung usw. Außerdem werden Tools erläutert, die bei den Tests helfen. Interne Tools wie [Hobbes](/help/sites-developing/hobbes.md) können beim webbasierten Testen der Benutzeroberfläche helfen. [Tough ](/help/sites-developing/tough-day.md) Daycan belastet Ihre Instanzen mit einer simulierten Belastung. Wenn Ihre Testumgebung bereits über Erfahrung mit Drittanbieter-Tools wie Selenium verfügt, können auch diese verwendet werden.

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

Ein gewisser Grad automatisierter Tests sollte durchgeführt werden, um die verschiedenen Bildschirmgrößen, Speicherbeschränkungen, Eingabemethoden und Betriebssysteme abzudecken. Sie deckt nicht nur einen Großteil der Testfälle ab, sondern kann Regressionstests beschleunigen, wenn neue Funktionen oder Geräte eingeführt werden. Idealerweise sollten Ihre Automatisierungstools Doppelarbeit reduzieren oder begrenzen. Verwenden Sie Tools oder Frameworks, damit Ihre Testbemühungen auf allen Plattformen gelten. Die folgende Tabelle zeigt eine vereinfachte Struktur einer Testumgebung für webbasierte Benutzeroberflächentests und Tests mobiler Apps. Die linke Seite des Diagramms zeigt eine Reihe von Selenium-Knoten mit Browsern an. SeleniumGrid kann allgemeine, webbasierte UI-Tests für jeden dieser Knoten auswerten. Der Selenium-Hub kann für plattformübergreifende App-Tests auch eine Verbindung zu Appium herstellen. Es werden nur Simulatoren angezeigt, Sie können aber adb für Android- und Xcode-Dienstprogramme für iOS-Geräte integrieren. Links finden Sie weiter unten in diesem Dokument, in dem Sie spezifische Details zu den erwähnten Tools finden.

![chlimage_1](assets/chlimage_1.jpeg)

## Manuelle Tests {#manual-testing}

Zusätzlich zu automatisierten Tests sollte Ihre App einen manuellen Testzyklus durchlaufen. Kunden, die die App auf einem echten Gerät ausführen, können nicht durch ein Skript dupliziert werden. Auch hier haben Sie viele Möglichkeiten. Sie können eine Plattform wie HockeyApp verwenden, um festzulegen, wer Zugriff hat und Feedback erfassen kann. Oder Sie können den gesamten Prozess an einen Dienst wie UTest, ElusiveStars oder Test auslagern. Wenn Sie über eine Gruppe interner Tester verfügen, aber nicht über verschiedene Geräte verfügen, gibt es Cloud-Services, mit denen Sie manuelle Tests an ihrem Gerätesool durchführen können. Ein solcher Dienst, der dies bereitstellt, ist SauceLabs. Sie können Apps auch remote für PhoneGap Enterprise erstellen und auf lokalen Geräten installieren, um Akzeptanztests oder Demos durchzuführen. Die neuesten Funktionen und Dokumentationen finden Sie auf der Website [PhoneGap](https://phonegap.com/) . Unabhängig vom Ansatz sollten manuelle Prüfungen durchgeführt werden.

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

Zum Testen von mobilen Apps stehen zahlreiche Tools zur Verfügung. Die Auswahl der zu verwendenden Optionen hängt von Ihrer spezifischen Situation ab: Funktionen, Preis, Support, Abdeckung usw. Im Folgenden finden Sie eine kleine Beschreibung einiger der verfügbaren Tools und Dienste.

**Selenium**

* Framework, das eine API für Testskripte enthält, um WebDriver zuzuführen und verschiedene Browser zu steuern.
* Sie können dies zusammen mit Appium zum Testen auf echten Geräten verwenden.
* SeleniumGrid leitet Tests zum parallelen Testen über Knoten hinweg.
* Selenium IDE hilft, das Schreiben von Testfällen zu reduzieren.

Weitere Informationen finden Sie unter [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**Testdroid**

* Ein Cloud-basierter Testdienst mit kontinuierlichen Integrationshaken und echten Gerätetests.
* Enthält einen App-Crawler, der die Gerätekompatibilität überprüft, Protokolle analysiert, Ansichten durchsucht, Screenshots erstellt und die Leistung überwacht.

Weitere Informationen finden Sie unter [https://testdroid.com/](https://testdroid.com/).

**Appium**

* Appium ist ein beliebtes plattformübergreifendes Framework zur Automatisierung mobiler Tests.
* Darüber hinaus ist ein Inspektor mit Datensatzfähigkeiten ausgestattet, um Code-Testfälle zu unterstützen.

Weitere Informationen finden Sie unter [https://appium.io/](https://appium.io/).

**SauceLabs**

* SauceLabs bietet Cloud-basierte Tests und ist mit kontinuierlicher Integration integriert.
* Tests werden automatisch in der Cloud-Umgebung ausgeführt. Alternativ können Sie ein bestimmtes Gerät oder eine bestimmte Plattform starten und manuelle Tests durchführen, um Probleme zu beheben.

Weitere Informationen finden Sie unter [https://saucelabs.com/](https://saucelabs.com/).

**AppTestNow**

* Ein Outsourcing-Service, der Ihre mobilen Apps testet.
* Umfasst einen großen Pool von Geräten und bietet eine breite Palette von Testtypen: Leistung, Qualität, Funktionalität, Zertifizierung, Lokalisierung, Datennutzung usw.

Weitere Informationen finden Sie unter [https://www.apptestnow.com](https://www.apptestnow.com/).

**HockeyApp**

* HockeyApp fällt unter den manuellen Test, bei dem die mobile App an einen persönlichen Appstore gesendet wird, in dem Tester sie herunterladen und ausprobieren können.

Weitere Informationen finden Sie unter [https://hockeyapp.net/features/](https://hockeyapp.net/features/).

**Jenkins**

* Obwohl es sich nicht um ein Testwerkzeug handelt, ist Jenkins ein kontinuierliches Integrations-Framework, das das Rückgrat für automatisierte Tests bildet. Es sind zahlreiche Drittanbieter-Plug-ins verfügbar, um die Funktionalität zu erweitern. Ein Beispiel: Das SeleniumGrid-Plug-in bietet eine Benutzeroberfläche zur Verwaltung des Selenium-Hub und der Selenium-Knoten.

Weitere Informationen finden Sie unter [https://jenkins-ci.org/](https://jenkins-ci.org/) und [https://wiki.jenkins-ci.org/display/JENKINS/Plugins](https://wiki.jenkins-ci.org/display/JENKINS/Plugins).
