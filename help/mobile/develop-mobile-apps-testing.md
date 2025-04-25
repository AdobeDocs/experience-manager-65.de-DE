---
title: Mobile Apps testen
description: Erfahren Sie, wie Sie Ihre Mobile Apps mithilfe verschiedener Tools automatisieren oder manuell testen können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing
content-type: reference
exl-id: e10e1904-7016-4eb0-9408-36297285f378
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 1%

---

# Mobile Apps testen{#testing-mobile-apps}

{{ue-over-mobile}}

Angesichts der breiten Palette von Geräten auf dem Markt und Geräten, die veröffentlicht werden, ist das Testen Ihrer Apps zwingend erforderlich geworden. Dies ist ein Bereich, in dem Funktionalität und Benutzerfreundlichkeit in einem App-Store niedrige Bewertungen erhalten können, aber ein einziger Fehler kann dazu führen, dass Ihre App deinstalliert wird. Bei Ihren Testplänen und der Qualitätssicherung muss sorgfältig darauf geachtet werden. Unter dem folgenden Link werden viele der Themen behandelt, die im Allgemeinen behandelt werden müssen, z. B. die Identifizierung Ihrer Umgebung, die Definition von Testfällen, Arten von Tests, Annahmen und die Beteiligung von Kunden. Außerdem werden Tools erläutert, die bei den Tests helfen können. Interne Tools wie [Hobbes](/help/sites-developing/hobbes.md) können bei Web-basierten Benutzeroberflächentests hilfreich sein. [Tough Day](/help/sites-developing/tough-day.md) kann Ihre Instanzen mit einer simulierten Last belasten. Wenn Ihre Testumgebung bereits über Erfahrung mit Tools von Drittanbietern wie Selenium verfügt, können auch diese verwendet werden.

Bei der Entwicklung einer Mobile App gibt es viele neue Probleme, die speziell für Geräte gelten und die neben denen des herkömmlichen Testens angegangen werden müssen.

* Funktionell - Werden alle Anforderungen von Ihrer App erfüllt?
* Benutzerfreundlichkeit - Ist die App einfach zu verwenden und von Ihren Kunden zu verstehen?
* Leistung - Was passiert bei einer Auslastungsspitze? Sind die App-Elemente wie Wischen und Karussells schnell und beeinträchtigen das Erlebnis nicht?
* Fehler oder Interrupts - Was passiert, wenn während der Ausführung Ihrer App ein eingehender Aufruf oder eine Benachrichtigung erfolgt? Was passiert, wenn das Netzwerk ausfällt oder ausgeschaltet wird?
* Installation und Updates - Wie sieht das Installationserlebnis aus? Wie werden Updates herausgegeben?
* Technisch - Verbraucht Ihre App zu viel Strom von einem Gerät?
* Lokalisierung : Werden alle Bereiche der App übersetzt?
* Zertifizierung - Wurde Ihre App zertifiziert? Können sich Kunden darauf verlassen, dass alle Datenschutzbestimmungen eingehalten werden?

Diese Fragen sollten während der automatisierten und manuellen Tests beantwortet werden.

## Automatisierte Tests {#automated-testing}

Es sollte ein gewisser Grad an automatisierten Tests durchgeführt werden, um die verschiedenen Bildschirmgrößen, Speicherbeschränkungen, Eingabemethoden und Betriebssysteme abzudecken. Sie deckt nicht nur viele der Testfälle ab, sondern kann auch Regressionstests beschleunigen, wenn neue Funktionen oder Geräte eingeführt werden. Idealerweise sollten Ihre Automatisierungstools Doppelarbeit reduzieren oder begrenzen. Verwenden Sie Tools oder Frameworks, damit Ihr Testaufwand für alle Plattformen gilt. Das folgende Diagramm zeigt eine vereinfachte Struktur einer Testumgebung für Web-basierte Benutzeroberflächentests und Mobile-App-Tests. Auf der linken Seite des Diagramms wird eine Reihe von Selenium-Knoten mit Browsern angezeigt. SeleniumGrid kann allgemeine, webbasierte Benutzeroberflächentests für jeden dieser Knoten erstellen. Der Selenium-Hub kann auch mit Appium verbunden werden, um plattformübergreifende App-Tests durchzuführen. Es werden nur Simulatoren angezeigt, Sie können jedoch auch die Dienstprogramme adb für Android™ und Xcode für iOS-Geräte einbinden. Links werden später in diesem Dokument bereitgestellt, wo Sie spezifische Details zu den genannten Tools finden können.

![chlimage_1](assets/chlimage_1.jpeg)

## Manuelle Tests {#manual-testing}

Zusätzlich zu automatisierten Tests sollte Ihre App einen Zyklus manueller Tests durchlaufen. Kunden, die die App auf einem echten Gerät ausführen, können nicht durch ein Skript dupliziert werden. Auch hier haben Sie viele Möglichkeiten. Sie können eine Plattform wie HockeyApp verwenden, um festzulegen, wer Zugriff hat, und Feedback einholen. Oder Sie können den gesamten Prozess an einen Service wie UTest, ElusiveStars oder Testin auslagern. Wenn Sie eine Gruppe interner Tester haben, aber keine Vielzahl von Geräten haben, gibt es Cloud-Services, mit denen Sie manuelle Tests an ihrem Gerätepool durchführen können. Ein solcher Dienst, der dies bereitstellt, ist SauceLabs. Sie können Apps auch remote für PhoneGap Enterprise erstellen und auf lokalen Geräten installieren, um Akzeptanztests oder Demos durchzuführen. Auf der PhoneGap (`https://phonegap.com/`)-Website finden Sie die neuesten Funktionen und die Dokumentation. Unabhängig vom Ansatz sollten manuelle Tests Folgendes bewirken:

* eine große Zahl von Testern getroffen hat,
* Testen gegen einen großen Pool von Geräten (im Idealfall echte Geräte, aber Simulatoren/Emulatoren, wenn keine echten Geräte verfügbar sind),
* Geben Sie informatives Feedback:

   * Absturzberichte,
   * Analyse/Tracking,
   * Verwendbarkeit,
   * Schwerpunkte,
   * Leistung,
   * Daten-/Stromverbrauch usw.

## Tools {#tools}

Zum Testen mobiler Apps steht eine breite Palette von Tools zur Verfügung. Die Auswahl der zu verwendenden sollte sich nach Ihrer spezifischen Situation richten: Funktionen, Preis, Support, Abdeckung usw. Im Folgenden finden Sie eine kurze Beschreibung einiger der verfügbaren Tools und Services.

**Selenium**

* Framework, das eine API für Testskripte enthält, um WebDriver zu befüllen und verschiedene Browser zu steuern.
* Sie können dies mit Appium zum Testen auf echten Geräten verwenden.
* SeleniumGrid leitet Tests für parallele Tests über Knoten.
* Selenium IDE hilft, das Schreiben von Testfällen zu reduzieren.

Weitere Informationen finden Sie unter [https://www.selenium.dev/](https://www.selenium.dev/).

**Testdroid**

* Ein Cloud-basierter Test-Service mit kontinuierlichen Integrations-Hooks und echten Gerätetests.
* Dazu gehört ein App Crawler, der die Gerätekompatibilität überprüft, Protokolle analysiert, Ansichten durchläuft, Screenshots erstellt und die Leistung überwacht.

https://testdroid.com/ Weitere Informationen finden Sie unter [&#128279;](https://testdroid.com/).

**Appium**

* Appium ist ein beliebtes plattformübergreifendes Framework zur Automatisierung von Tests für Mobilgeräte.
* Außerdem ist ein Inspektor mit Aufzeichnungsfunktionen enthalten, um Testfälle zu codieren.

https://appium.io/ Weitere Informationen finden Sie unter [&#128279;](https://appium.io/).

**SauceLabs**

* SauceLabs bietet Cloud-basierte Tests und lässt sich mit kontinuierlicher Integration integrieren.
* Tests werden automatisch in der Cloud-Umgebung ausgeführt oder Sie können ein bestimmtes Gerät oder eine bestimmte Plattform starten und manuelle Tests durchführen, um Probleme zu debuggen.

https://saucelabs.com/ Weitere Informationen finden Sie unter [&#128279;](https://saucelabs.com/).

<!-- **AppTestNow**

* An outsourcing service that tests your mobile apps.
* Included is a large pool of devices and offers a wide range of types of testing: performance, quality, functional, certification, localization, data consumption, and so on.

For more information, see [https://apptestnow.com/](https://apptestnow.com/). -->

**HockeyApp**

* HockeyApp fällt unter die manuellen Tests, bei denen die Mobile App in einen persönlichen App-Store verschoben wird, wo Tester sie herunterladen und ausprobieren können.

https://hockeyapp.net/features/ Weitere Informationen finden Sie unter [&#128279;](https://hockeyapp.net/features/).

**Jenkins**

* Obwohl es sich nicht um ein Test-Tool handelt, ist Jenkins ein kontinuierliches Integrations-Framework, das das Rückgrat für automatisierte Tests bereitstellt. Es stehen zahlreiche Plug-ins von Drittanbietern zur Verfügung, um die Funktionalität zu erweitern. Beispielsweise stellt das SeleniumGrid-Plug-in eine Benutzeroberfläche bereit, die bei der Verwaltung des Selenium-Hub und der -Knoten hilft.

https://www.jenkins.io/ Weitere Informationen finden Sie unter [&#128279;](https://www.jenkins.io/) und [https://plugins.jenkins.io/](https://plugins.jenkins.io/).
