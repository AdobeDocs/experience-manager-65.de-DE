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
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 2%

---


# Testen von mobilen Apps{#testing-mobile-apps}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Angesichts der breiten Palette von Geräten auf dem Markt und von Geräten, die veröffentlicht werden, ist das Testen Ihrer Apps äußerst wichtig geworden. Dies ist ein Bereich, in dem Funktionen und Benutzerfreundlichkeit zu niedrigen Reviews in einem App Store führen können, aber ein Fehler kann dazu führen, dass Ihre App deinstalliert wird. Bei Ihren Testplänen und der Qualitätssicherung muss sorgfältig darauf geachtet werden. Der folgende Link behandelt viele Themen, die allgemein behandelt werden müssen, wie z.B. die Identifizierung Ihrer Umgebung, die Definition von Testfällen, Testtypen, Annahmen, Kundenbeteiligung usw. Darüber hinaus werden Tools zur Unterstützung des Testens besprochen. Interne Tools wie [Hobbes](/help/sites-developing/hobbes.md) können beim webbasierten Testen der Benutzeroberfläche helfen. [Die ](/help/sites-developing/tough-day.md) Tage können Ihre Instanzen mit einer simulierten Last bedienen. Wenn Ihre Test-Umgebung bereits Erfahrung mit Drittanbieter-Tools wie Selen hat, können auch diese verwendet werden.

Bei der Entwicklung einer mobilen App gibt es viele neue Probleme, die speziell für Geräte gelten, die zusammen mit denen herkömmlicher Tests behandelt werden müssen.

* Funktionen - Werden alle Anforderungen von Ihrer App erfüllt?
* Benutzerfreundlichkeit - Ist die App benutzerfreundlich und wird sie von Ihrem Kunden verstanden?
* Leistung - Was passiert bei einer Spitze der Nutzung? Sind die App-Elemente wie Blättern und Karusselle schnell und lassen sich nicht vom Erlebnis ablenken?
* Fehler oder Unterbrechungen: Was passiert, wenn während der Ausführung der App ein eingehender Aufruf oder eine eingehende Benachrichtigung erfolgt? Was passiert, wenn ein Netzwerkausfall vorliegt oder der Netzschalter ausgeschaltet ist?
* Installation und Updates - Wie wird die Installation durchgeführt? Wie werden Updates herausgegeben?
* Technisch - Verbraucht Ihre App zu viel Strom von einem Gerät?
* lokale Anpassung - Werden alle Bereiche in Ihrer App übersetzt?
* Zertifizierung - Wurde Ihre App zertifiziert? Können Kunden darauf vertrauen, dass alle datenschutzrechtlichen Anforderungen eingehalten werden?

Diese Fragen sollten während Ihres automatisierten und manuellen Tests beantwortet werden.

## Automatisierte Tests {#automated-testing}

Es sollte ein gewisses Maß an automatisiertem Test durchgeführt werden, um die verschiedenen Bildschirmgrößen, Speicherbeschränkungen, Eingabemethoden und Betriebssysteme abzudecken. Sie deckt nicht nur viele der Testfälle ab, sondern kann auch Regressionstests beschleunigen, wenn neue Funktionen oder Geräte eingeführt werden. Im Idealfall sollten Ihre Automatisierungstools die Duplizierung reduzieren oder einschränken. Verwenden Sie Tools oder Frameworks, damit Ihr Testaufwand für alle Plattformen gilt. Die folgende Tabelle zeigt eine vereinfachte Struktur einer Testing-Umgebung für webbasierte UI-Tests und mobile App-Tests. Die linke Seite des Diagramms zeigt eine Reihe von Selenium-Knoten mit Browsern. SeleniumGrid kann allgemeine webbasierte UI-Tests an einem dieser Knoten auswerten. Der Selenium-Hub kann auch eine Verbindung zu Appium herstellen, um plattformübergreifende App-Tests durchzuführen. Es werden nur Simulatoren angezeigt, Sie können aber adb für Android- und Xcode-Hilfsprogramme für iOS-Geräte einbinden. Links finden Sie weiter unten in diesem Dokument, wo Sie spezifische Informationen zu den genannten Tools finden.

![chlimage_1](assets/chlimage_1.jpeg)

## Manuelle Tests {#manual-testing}

Zusätzlich zu automatisierten Tests sollte Ihre App einen manuellen Testzyklus durchlaufen. Kunden, die die App auf einem echten Gerät ausführen, können nicht durch ein Skript dupliziert werden. Auch hier haben Sie viele Möglichkeiten. Sie können eine Plattform wie HockeyApp verwenden, um zu definieren, wer Zugriff hat und Feedback zu sammeln. Oder Sie können den gesamten Prozess an einen Dienst wie UTest, ElusiveStars oder Test auslagern. Wenn Sie eine Gruppe interner Tester haben, aber keine unterschiedlichen Geräte haben, gibt es Cloud-Dienste, bei denen Sie manuelle Tests auf ihren Gerätepools durchführen können. Ein solcher Dienst, der dies bietet, ist SauceLabs. Sie können Apps auch remote für PhoneGap Enterprise erstellen und auf lokalen Geräten installieren, um Akzeptanztests oder Demos durchzuführen. Die neuesten Funktionen und Dokumentation finden Sie auf der Website [PhoneGap](https://phonegap.com/). Unabhängig vom Ansatz sollten manuelle Prüfungen durchgeführt werden.

* eine große Zielgruppe von Tester getroffen hat,
* Testen mit einem großen Pool von Geräten (im Idealfall echte Geräte, aber Simulatoren/Emulatoren, wenn keine echten Geräte verfügbar sind),
* informatives Feedback geben:

   * Absturzberichte,
   * Analyse/Verfolgung,
   * Benutzerfreundlichkeit,
   * besondere Aufmerksamkeit,
   * Leistung,
   * Daten-/Stromverbrauch usw.

## Tools {#tools}

Zum Testen von mobilen Apps stehen eine breite Palette von Tools zur Verfügung. Die Auswahl der zu verwendenden hängt von Ihrer spezifischen Situation ab: Funktionen, Preis, Support, Abdeckung usw. Im Folgenden werden einige der verfügbaren Tools und Dienste kurz beschrieben.

**Selenium**

* Framework, das eine API für Testskripte enthält, um WebDriver zu steuern und verschiedene Browser zu steuern.
* Sie können dies zusammen mit Appium zum Testen auf realen Geräten verwenden.
* SeleniumGrid leitet Tests zum parallelen Testen über Knoten hinweg.
* Selenium IDE hilft, die Schreibweise von Testfällen zu reduzieren.

Weitere Informationen finden Sie unter [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**Testdroid**

* Ein Cloud-basierter Testdienst mit kontinuierlichen Integrationshaken und echten Gerätetests.
* Enthält einen App-Crawler, der die Gerätekompatibilität prüft, Protokolle analysiert, Ansichten durchläuft, Screenshots aufnimmt und die Leistung überwacht.

Weitere Informationen finden Sie unter [https://testdroid.com/](https://testdroid.com/).

**Appium**

* Appium ist ein beliebtes plattformübergreifendes Framework zur Automatisierung von mobilen Tests.
* Zusätzlich ist ein Inspektor mit Aufzeichnungsfähigkeiten ausgestattet, um Testfälle zu codieren.

Weitere Informationen finden Sie unter [https://appium.io/](https://appium.io/).

**SauceLabs**

* SauceLabs bietet Cloud-basierte Tests und ist mit kontinuierlicher Integration integriert.
* Tests werden automatisch in der Cloud-Umgebung ausgeführt oder Sie können ein bestimmtes Gerät oder eine bestimmte Plattform Beginn und manuelle Tests durchführen, um Probleme zu debuggen.

Weitere Informationen finden Sie unter [https://saucelabs.com/](https://saucelabs.com/).

**AppTestNow**

* Ein Outsourcing-Dienst, der Ihre mobilen Apps testen wird.
* Umfasst einen großen Pool von Geräten und Angebot mit einer Vielzahl von Testtypen: Leistung, Qualität, Funktionalität, Zertifizierung, lokale Anpassung, Datenverbrauch usw.

Weitere Informationen finden Sie unter [https://www.apptestnow.com](https://www.apptestnow.com/).

**HockeyApp**

* HockeyApp wird unter den manuellen Test fallen, bei dem die mobile App an einen persönlichen App Store gesendet wird, in dem die Tester sie herunterladen und ausprobieren können.

Weitere Informationen finden Sie unter [https://hockeyapp.net/features/](https://hockeyapp.net/features/).

**Jenkins**

* Obwohl Jenkins kein Testwerkzeug ist, ist es ein kontinuierliches Integrationsframework, das das Rückgrat für automatisierte Tests bietet. Zur Erweiterung der Funktionalität stehen zahlreiche Drittanbieter-Plugins zur Verfügung. Ein Beispiel: Das SeleniumGrid-Plugin bietet eine Benutzeroberfläche zur Verwaltung des Selenium-Hub und der Selenium-Knoten.

Weitere Informationen finden Sie unter [https://jenkins-ci.org/](https://jenkins-ci.org/) und [https://wiki.jenkins-ci.org/display/JENKINS/Plugins](https://wiki.jenkins-ci.org/display/JENKINS/Plugins).
