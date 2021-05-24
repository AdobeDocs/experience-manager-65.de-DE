---
title: Testen der Benutzeroberfläche
seo-title: Testen der Benutzeroberfläche
description: AEM stellt ein Framework bereit, mit dem Sie das Testen Ihrer AEM-Benutzeroberfläche automatisieren können.
seo-description: AEM stellt ein Framework bereit, mit dem Sie das Testen Ihrer AEM-Benutzeroberfläche automatisieren können.
uuid: 408a60b5-cba9-4c9f-abd3-5c1fb5be1c50
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components, testing
discoiquuid: 938100ad-94f9-408a-819d-72657dc115f7
docset: aem65
exl-id: 2d28cee6-31b0-4288-bad3-4d2ecad7b626
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 73%

---

# Testen der Benutzeroberfläche{#testing-your-ui}

>[!NOTE]
>
>Ab AEM 6.5 wird das UI-Test-Framework hobbes.js nicht mehr unterstützt. Adobe plant keine weiteren Verbesserungen und empfiehlt Kunden die Verwendung der Selenium-Automatisierung.
>
>Siehe [Veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md).

AEM stellt ein Framework bereit, mit dem Sie das Testen Ihrer AEM-Benutzeroberfläche automatisieren können. Mit diesem Framework können Sie Tests der Benutzeroberfläche direkt in einem Webbrowser schreiben und ausführen. Das Framework stellt eine JavaScript-API zum Erstellen von Tests bereit.

Das AEM-Test-Framework verwendet Hobbes.js, eine in JavaScript geschriebene Testbibliothek. Das Hobbes.js-Framework wurde für AEM-Tests als Teil des Entwicklungsprozesses entwickelt. Das Framework steht jetzt zur allgemeinen Verwendung zum Testen Ihrer AEM-Anwendungen zur Verfügung.

>[!NOTE]
>
>Ausführliche Informationen zur API finden Sie in der Dokumentation zu Hobbes.js [Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/test-api/index.html) .

## Die Struktur von Tests {#structure-of-tests}

Wenn Sie automatisierte Tests in AEM verwenden, sollten Sie die folgenden Begriffe kennen:

| Aktion | Eine **Aktion** ist eine bestimmte Aktivität auf einer Webseite, z. B. das Klicken auf einen Link oder eine Schaltfläche. |
|---|---|
| Testfall | Ein **Testfall** ist eine bestimmte Situation, die aus einer oder mehreren **Aktionen** bestehen kann. |
| Testsuite | Eine **Test Suite** ist eine Gruppe verwandter **Testfälle**, die gemeinsam einen bestimmten Anwendungsfall testen. |

## Ausführen von Tests {#executing-tests}

### Anzeigen von Test-Suites {#viewing-test-suites}

Öffnen Sie die Testen-Konsole, um die registrierten Test-Suites anzuzeigen. Das Test-Feld enthält eine Liste der Test-Suites samt ihrer Testfälle.

Navigieren Sie über **Globale Navigation > Tools > Vorgänge > Testen** zur Tools-Konsole.

![chlimage_1-63](assets/chlimage_1-63.png)

Wenn Sie die Konsole öffnen, werden die Test-Suites links aufgeführt, zusammen mit der Option, sie alle nacheinander auszuführen. Der Bereich rechts mit einem Hintergrund im Schachbrettmuster ist ein Platzhalter. Hier werden Seiteninhalte bei der Testausführung angezeigt.

![chlimage_1-64](assets/chlimage_1-64.png)

### Ausführen einer einzelnen Test-Suite {#running-a-single-test-suite}

Test-Suites können einzeln ausgeführt werden. Wenn Sie eine Test-Suite ausführen, ändert sich die Seite, während die Testfälle und ihre Aktion ausgeführt werden, und die Ergebnisse werden nach dem Abschluss des Tests angezeigt. Symbole zeigen die Ergebnisse an.

Das Häkchen-Symbol kennzeichnet einen erfolgreichen Test:

![](do-not-localize/chlimage_1-2.png)

Das X-Symbol steht für einen gescheiterten Test:

![](do-not-localize/chlimage_1-3.png)

So führen Sie eine Test-Suite aus:

1. Klicken oder tippen Sie im Testfeld auf den Namen des Testfalls, den Sie ausführen möchten, um die Details zu den Aktionen anzuzeigen.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Klicken oder tippen Sie auf die Schaltfläche **Test ausführen**.

   ![](do-not-localize/chlimage_1-4.png)

1. Der Platzhalter wird durch Seiteninhalte ersetzt, wenn der Test ausgeführt wird.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Um die Ergebnisse des Testfalls anzuzeigen, tippen oder klicken Sie auf die Beschreibung, um das Feld **Ergebnis** zu öffnen. Wenn Sie im Feld **Ergebnis** auf den Namen des Testfalls tippen oder klicken, werden alle Details angezeigt.

   ![chlimage_1-67](assets/chlimage_1-67.png)

### Ausführen mehrerer Tests {#running-multiple-tests}

Test-Suites werden nacheinander in der Reihenfolge ausgeführt, in der sie in der Konsole erscheinen. Sie können einen Test aufschlüsseln, um detaillierte Ergebnisse einzusehen.

![chlimage_1-68](assets/chlimage_1-68.png)

1. Tippen oder klicken Sie im Testfeld auf die Schaltfläche **Alle Tests ausführen** oder auf die Schaltfläche **Tests ausführen** unter dem Titel der Test-Suite, die Sie ausführen möchten.

   ![](do-not-localize/chlimage_1-5.png)

1. Um die Ergebnisse jedes Testfalls anzuzeigen, tippen oder klicken Sie auf den Titel des Testfalls. Durch Tippen oder Klicken auf den Namen Ihres Tests im Bedienfeld **Ergebnis** werden alle Details angezeigt.

   ![chlimage_1-69](assets/chlimage_1-69.png)

## Erstellen und Verwenden einer einfachen Test-Suite {#creating-and-using-a-simple-test-suite}

Das folgende Verfahren führt Sie durch die Erstellung und Ausführung einer Test Suite mit [We.Retail-Inhalt](/help/sites-developing/we-retail.md). Sie können den Test jedoch einfach ändern, um eine andere Webseite zu verwenden.

Vollständige Informationen zum Erstellen eigener Test-Suites finden Sie in der [Dokumentation zur Hobbes.js-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/test-api/index.html).

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
   >**Nur in AEM Forms**
   >
   >
   >Um adaptive Formulare zu testen, fügen Sie die folgenden Werte den Kategorien (categories) und Abhängigkeiten (dependencies) hinzu. Beispiel:
   >
   >
   >**categories**:  `granite.testing.hobbes.tests, granite.testing.hobbes.af.commons`
   >
   >
   >**dependencies**:  `granite.testing.hobbes.testrunner, granite.testing.hobbes.af`

1. Klicken Sie auf **Alle speichern**.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `myFirstTest` und klicken Sie auf **Erstellen > Datei erstellen**. Nennen Sie die Datei `js.txt` und klicken Sie auf **OK**.
1. Geben Sie in der Datei `js.txt` den folgenden Text ein:

   ```
   #base=.
   myTestSuite.js
   ```

1. Klicken Sie auf **Alle speichern** und schließen Sie dann die Datei `js.txt`.
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
