---
title: Testen der Benutzeroberfläche
description: AEM bietet ein Framework für die Automatisierung von Tests für Ihre AEM-Benutzeroberfläche
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components, testing
docset: aem65
exl-id: 2d28cee6-31b0-4288-bad3-4d2ecad7b626
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 91%

---

# Testen der Benutzeroberfläche{#testing-your-ui}

>[!NOTE]
>
>Ab AEM 6.5 wird das Framework für Benutzeroberflächentests hobbes.js als veraltet gekennzeichnet. Adobe plant keine weiteren Verbesserungen und empfiehlt Kunden die Verwendung der Selenium-Automatisierung.
>
>Siehe [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md).

AEM bietet ein Framework für die Automatisierung von Tests für Ihre AEM-Benutzeroberfläche. Mit diesem Framework können Sie Tests der Benutzeroberfläche direkt in einem Webbrowser schreiben und ausführen. Das Framework umfasst eine JavaScript-API für das Erstellen von Tests.

Das AEM-Test-Framework nutzt Hobbes.js, eine Testbibliothek, die in JavaScript geschrieben wurde. Das Hobbes.js-Framework wurde für AEM-Tests als Teil des Entwicklungsprozesses entwickelt. Das Framework steht jetzt zur allgemeinen Verwendung zum Testen Ihrer AEM-Anwendungen zur Verfügung.

>[!NOTE]
>
>Detaillierte Angaben zur API finden Sie in der [Dokumentation](https://developer.adobe.com/experience-manager/reference-materials/6-5/test-api/index.html) zu Hobbes.js.

## Struktur von Tests {#structure-of-tests}

Bei der Verwendung automatisierter Tests in AEM ist es wichtig, die folgenden Begriffe zu verstehen:

| Aktion | Eine **Aktion** ist eine bestimmte Aktivität auf einer Web-Seite, z. B. das Klicken auf einen Link oder eine Schaltfläche. |
|---|---|
| Testfall | Ein **Testfall** ist eine bestimmte Situation, die aus einer oder mehreren **Aktionen** bestehen kann. |
| Testsuite | Eine **Test-Suite** ist eine Gruppe verwandter **Testfälle**, die zusammen einen bestimmten Anwendungsfall testen. |

## Ausführen von Tests {#executing-tests}

### Anzeigen von Test-Suites {#viewing-test-suites}

Öffnen Sie die Testkonsole, um die registrierten Test-Suites anzuzeigen. Das Testfeld enthält eine Liste von Test-Suites und deren Testfälle.

Navigieren Sie zur Tools-Konsole über **Globale Navigation > Tools > Vorgänge > Tests**.

![chlimage_1-63](assets/chlimage_1-63.png)

Beim Öffnen der Konsole werden die Test-Suites auf der linken Seite aufgeführt, zusammen mit der Option, sie alle nacheinander auszuführen. Der rechts angezeigte Bereich mit einem gecheckten Hintergrund ist ein Platzhalter für die Anzeige des Seiteninhalts während der Testausführung.

![chlimage_1-64](assets/chlimage_1-64.png)

### Ausführen einer einzelnen Test-Suite {#running-a-single-test-suite}

Testsuiten können einzeln ausgeführt werden. Wenn Sie eine Test-Suite ausführen, ändert sich die Seite, während die Testfälle und ihre Aktionen ausgeführt werden. Die Ergebnisse werden nach Abschluss des Tests angezeigt. Die Ergebnisse werden durch Symbole gekennzeichnet.

Das Häkchen-Symbol kennzeichnet einen erfolgreichen Test: 

![Häkchensymbol.](do-not-localize/chlimage_1-2.png)

Eine X-Symbol zeigt einen fehlgeschlagenen Test an:

![Symbol „Fehlgeschlagener Test“, gekennzeichnet durch ein X in einem Kreis.](do-not-localize/chlimage_1-3.png)

So führen Sie eine Test-Suite aus:

1. Klicken Sie im Bereich Tests auf den Namen des Testfalls, den Sie ausführen möchten, um die Details der Aktionen zu erweitern.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Klicken Sie auf **Test ausführen**.

   ![Ein Bild der Schaltfläche „Tests ausführen“, gekennzeichnet durch einen nach rechts zeigenden Zeiger in einem Kreis.](do-not-localize/chlimage_1-4.png)

1. Der Platzhalter wird durch Seiteninhalte ersetzt, wenn der Test ausgeführt wird.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Um die Ergebnisse des Testfalls anzuzeigen, tippen oder klicken Sie auf die Beschreibung, um das Bedienfeld **Ergebnis** zu öffnen. Wenn Sie im Bedienfeld **Ergebnis** auf den Namen des Testfalls tippen oder klicken, werden alle Details angezeigt.

   ![chlimage_1-67](assets/chlimage_1-67.png)

### Ausführen mehrerer Tests {#running-multiple-tests}

Test-Suites werden nacheinander in der Reihenfolge ausgeführt, in der sie in der Konsole angezeigt werden. Sie können einen Drilldown durchführen, um die detaillierten Ergebnisse anzuzeigen.

![chlimage_1-68](assets/chlimage_1-68.png)

1. Klicken Sie im Bereich &quot;Tests&quot;auf die **Alle Tests ausführen** oder **Ausführen von Tests** unter dem Titel der Test-Suite, die Sie ausführen möchten.

   ![Ein Bild der Schaltfläche „Alle Tests ausführen“ und der Schaltfläche „Tests ausführen“, gekennzeichnet durch einen nach rechts zeigenden Zeiger in einem Kreis.](do-not-localize/chlimage_1-5.png)

1. Um die Ergebnisse jedes Testfalls anzuzeigen, tippen oder klicken Sie auf den Titel des Testfalls. Wenn Sie im Bedienfeld **Ergebnis** auf den Namen des Tests klicken, werden alle Details angezeigt.

   ![chlimage_1-69](assets/chlimage_1-69.png)

## Erstellen und Verwenden einer einfachen Test-Suite {#creating-and-using-a-simple-test-suite}

Die folgenden Schritte erläutern die Erstellung und Ausführung einer Test-Suite mit [We.Retail-Inhalten](/help/sites-developing/we-retail.md). Sie können den Test jedoch auch einfach für eine andere Web-Seite anpassen.

Vollständige Informationen zum Erstellen eigener Test-Suites finden Sie in der [Dokumentation zur Hobbes.js-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/test-api/index.html).

1. Öffnen Sie CRXDE Lite. ([https://localhost:4502/crx/de](https://localhost:4502/crx/de))
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/etc/clientlibs` und klicken Sie auf **Erstellen > Ordner erstellen**. Geben Sie als Namen `myTests` ein und klicken Sie auf **OK**.
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/etc/clientlibs/myTests` und klicken Sie auf **Erstellen > Knoten erstellen**. Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie dann auf **OK**:

   * Name: `myFirstTest`
   * Typ: `cq:ClientLibraryFolder`

1. Fügen Sie dem Knoten „myFirstTest“ die folgenden Eigenschaften hinzu:

   | Name | Typ | Wert |
   |---|---|---|
   | `categories` | Zeichenfolge[] | `granite.testing.hobbes.tests` |
   | `dependencies` | Zeichenfolge[] | `granite.testing.hobbes.testrunner` |

   >[!NOTE]
   >
   >**Nur AEM Forms**
   >
   >
   >Fügen Sie den Kategorien und Abhängigkeiten die folgenden Werte hinzu, um adaptive Formulare zu testen. Beispiel:
   >
   >
   >**categories:**: `granite.testing.hobbes.tests, granite.testing.hobbes.af.commons`
   >
   >
   >**dependencies**: `granite.testing.hobbes.testrunner, granite.testing.hobbes.af`

1. Klicken Sie auf **Alle speichern**.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `myFirstTest` und klicken Sie auf **Erstellen > Datei erstellen**. Nennen Sie die Datei `js.txt` und klicken Sie auf **OK**.
1. Geben Sie in der Datei `js.txt` den folgenden Text ein:

   ```
   #base=.
   myTestSuite.js
   ```

1. Klicken Sie auf **Alle speichern** und schließen Sie dann die Datei `js.txt`
1. Klicken Sie mit der rechten Maustaste auf den Knoten `myFirstTest` und klicken Sie auf **Erstellen > Datei erstellen**. Nennen Sie die Datei `myTestSuite.js` und klicken Sie auf **OK**.
1. Kopieren Sie den folgenden Code in die Datei `myTestSuite.js` und speichern Sie die Datei anschließend:

   ```
   new hobs.TestSuite("Experience Content Test Suite", {path:"/etc/clientlibs/myTests/myFirstTest/myTestSuite.js"})
      .addTestCase(new hobs.TestCase("Navigate to Experience Content")
         .navigateTo("/content/we-retail/us/en/experience/arctic-surfing-in-lofoten.html")
      )
      .addTestCase(new hobs.TestCase("Hover Over Topnav")
         .mouseover("li.visible-xs")
      )
      .addTestCase(new hobs.TestCase("Click Topnav Link")
         .click("li.active a")
   );
   ```

1. Navigieren Sie zur **Testkonsole**, um die Test-Suite zu testen.
