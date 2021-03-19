---
title: Debuggings von HTML5-Formularen
seo-title: Debuggings von HTML5-Formularen
description: Das Dokument listet Schritte zur Behebung verschiedener bekannter Probleme auf.
seo-description: Das Dokument listet Schritte zur Behebung verschiedener bekannter Probleme auf.
uuid: df1835aa-6033-4ecb-97c8-4c3b7b96b943
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 5260d981-da40-40ab-834e-88e091840813
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 71%

---


# Debuggings von HTML5-Formularen {#debugging-html-forms}

Dieses Dokument umfasst mehrere Fehlerbehebungsszenarien. Für jedes Beispiel werden einige Schritte beschrieben, um das Problem zu beheben. Führen Sie diese Schritte aus und, falls das Problem weiterhin besteht, konfigurieren Sie die Protokollfunktion, um Protokolle zu erhalten und auf Fehler/Warnungen zu überprüfen. Weitere Informationen zur Protokollierung von HTML5-Formularen finden Sie unter [Erstellen von Protokollen für HTML5-Formulare](/help/forms/using/enable-logs.md).

## Problem: Wenn ich das Formular rendere, erscheint die Ausnahmeseite „org.apache.sling.api.SlingException“.{#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page}

Suchen Sie in den Ausnahmedetails nach dem Wort **verursacht von**.

Die wahrscheinliche Ursache ist, dass mindestens ein Parameter in der URL falsch ist.

Überprüfen Sie die folgenden Parameter:

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>template</td>
   <td>Dateiname der Vorlage</td>
  </tr>
  <tr>
   <td>contentRoot</td>
   <td>Der Pfad, wo sich Vorlage und zugeordnete Ressourcen befinden</td>
  </tr>
  <tr>
   <td>dataRef</td>
   <td>Absoluter Pfad der Datendatei, die mit der Vorlage zusammengeführt wird.<br /> Hinweis: Pfad definiert den absoluten Pfad der Datendatei.</td>
  </tr>
  <tr>
   <td>data</td>
   <td>UTF-8-kodierte Datenbyte, die mit der Vorlage zusammengeführt werden.</td>
  </tr>
 </tbody>
</table>

## Problem: Ein Formular kann nicht gerendert werden (eine Fehlermeldung wird angezeigt) {#problem-unable-to-render-form}

1. Stellen Sie sicher, dass die angegebenen Parameter korrekt sind. Detaillierte Informationen zu Parametern finden Sie unter [Render-Parameter](#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page).
1. Melden Sie sich bei CRX Package Manager an (unter https://&lt;server>:&lt;port>/crx/packmgr/index.jsp) und überprüfen Sie, ob die folgenden Pakete korrekt installiert wurden:

   * adobe-lc-forms-content-pkg-&lt;version>.zip
   * adobe-lc-forms-runtime-pkg-&lt;version>.zip

1. Melden Sie sich bei der CQ Web Console (Felix Console) unter https://&lt;server>:&lt;port>/system/console/bundles an.

    Stellen Sie sicher, dass der Status der folgenden Pakete „aktiv“ ist:

   * scala-lang.bundle [osgi]

   (com.adobe.livecyclescala-lang.bundle)

   * Adobe XFA Forms Renderer

   (com.adobe.livecycle.adobe-lc-forms-core)

   * Adobe XFA Forms LC Connector

   (com.adobe.livecycle.adobe-lc-forms-lc-connector)

## Problem: Formular rendert ohne Stile {#problem-form-renders-without-styles}

1. Rufen Sie im Browser **„Developer Tools“ auf**. Stellen Sie sicher, dass Profil.css verfügbar ist.
1. Wenn die Datei &quot;Profil.css&quot;nicht verfügbar ist, melden Sie sich bei CRX DE unter https://&lt;server>:&lt;port>/crx/de an.
1. Navigieren Sie in der Ordnerhierarchie auf der linken Seite zu /etc/clientlibs/fd/xfaforms/. Öffnen Sie die in den Ordnern aufgeführten css.txt-Dateien.

   * Profil
   * runtime
   * scrollnav
   * toolbar
   * xfalib

1. Überprüfen Sie, ob diese Dateien in den css.txt-Dateien in CRX DE Lite vorhanden sind unter /libs/fd/xfaforms/clientlibs/xfalib/css.

   ```css
   #base=css
   application.css
   dialog.css
   datepicker.css
   scribble.css
   listboxwidget.css
   ```

1. Wenn die erwähnten Dateien nicht vorhanden sind, installieren Sie das Paket „adobe-lc-forms-runtime-pkg-&lt;Version>.zip“ erneut.

### Problem: Unerwarteter Fehler gefunden {#problem-unexpected-error-encountered}

1. Fügen Sie in der Formular-URL den Parameter &quot;Abfrage&quot;debugClientLibs hinzu und setzen Sie den Wert auf &quot;true&quot;(z. B.: https://&lt;server>:&lt;port>/content/xfaforms/profiles/test.html?contentRoot=&lt;beliebiger Pfad>&amp;template=&lt;Name der xdp-Datei>&amp;log=1-a9-b9-c9&amp;debugClientLibs=true)
1. Im Desktop-Browser, z. B. Chrome, rufen Sie „Developer Tools“ -> „Console“ auf
1. Öffnen Sie die Protokolle, um den Fehlertyp zu identifizieren. Detaillierte Informationen zu Protokollen finden Sie unter [Protokolle für HTML5-Formulare](/help/forms/using/enable-logs.md).
1. Wechseln Sie zu „Developer Tools“ -> „Console“. Verwenden Sie die Stapelablaufverfolgung, um den Code zu finden, der den Fehler verursacht hat. Debuggen Sie den Fehler, um das Problem zu lösen.

   >[!NOTE]
   >
   >Bei einem Scripting-Fehler überprüfen Sie, ob das Problem beim Rendern des Formulars in PDF auch auftritt. Wenn ja, gibt es ein Problem in der Formular-Skriptlogik.

## Problem: Formular lässt sich nicht versenden {#problem-unable-to-submit-the-form}

1. Vergewissern Sie sich, dass Sie Zugriffsrechte auf den AEM-Server haben und mit dem Server verbunden sind.
1. Überprüfen Sie, ob der Parameter „submitUrl“ korrekt ist.
1. Aktivieren Sie die clientseitigen Protokolle, wie unter [Protokolle für die HTML5-Formulare](/help/forms/using/enable-logs.md) beschrieben, und verwenden Sie die Debugoption **1-a5-b5-c5**. Rendern Sie das Formular erneut und klicken Sie auf „Senden“. Öffnen Sie die Debug-Console im Browser und prüfen Sie, ob Fehler vorliegen.
1. Suchen Sie die Serverprotokolle, die erwähnt werden unter [Protokolle für die HTML5-Formulare](/help/forms/using/enable-logs.md). Prüfen Sie, ob in den Serverprotokollen während der Sendung ein Fehler verzeichnet wurde.

## Problem: Lokalisierte Fehlermeldungen werden nicht angezeigt  {#problem-localized-error-messages-do-not-display}

1. Rendern Sie das Formular mit dem zusätzlichem Abfrageparameter **debugClientLibs=true** im Desktop-Browser, wechseln Sie dann zu „Developer Tools -> Ressourcen“ und suchen Sie die Datei „I18N.css“.
1. Wenn die Datei nicht verfügbar ist, melden Sie sich bei CRX DE unter https://&lt;server>:&lt;port>/crx/de an.
1. In der Ordnerhierarchie auf der linken Seite navigieren Sie zu „/libs/fd/xfaforms/clientlibs/I18N“. Stellen Sie sicher, dass die folgenden Dateien und Ordner vorhanden sind:

   * Namespace.js
   * LogMessages.js
   * Ordner für Sprachen

1. Wenn eine der oben aufgeführten Dateien oder ein Ordner nicht vorhanden ist, installieren Sie das Paket **adobe-lc-forms-runtime-pkg-&lt;version>.zip** erneut.
1. Navigieren Sie zu dem Ordner, der denselben Namen wie das Gebietsschemas hat, und überprüfen Sie seinen Inhalt. Der Ordner muss die folgenden Dateien enthalten:

   * I18N.js
   * js.txt

1. Überprüfen Sie den Inhalt von js.txt und stellen Sie sicher, dass die folgenden Einträge vorhanden sind.

   ```javascript
   ../Namespace.js
   I18N.js
   ../LogMessages.js
   ```

## Problem: Bild wird nicht angezeigt  {#problem-image-not-showing-up}

1. Stellen Sie sicher, dass die URL des Bilds korrekt ist.
1. Überprüfen Sie, ob Ihr Browser diesen Bildtyp unterstützt.
1. Suchen Sie in den Ausnahmedetails nach dem Wort **verursacht von**.

   Die wahrscheinliche Ursache ist, dass mindestens ein Parameter in der URL falsch ist.

   Überprüfen Sie die folgenden Parameter:
Schritttext

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>template</td>
   <td>Dateiname der Vorlage</td>
  </tr>
  <tr>
   <td>contentRoot</td>
   <td>Der Pfad, wo sich Vorlage und zugeordnete Ressourcen befinden</td>
  </tr>
  <tr>
   <td>dataRef</td>
   <td>Absoluter Pfad der Datendatei, die mit der Vorlage zusammengeführt wird.<br /> Hinweis: Pfad definiert den absoluten Pfad der Datendatei.</td>
  </tr>
  <tr>
   <td>data</td>
   <td>UTF-8-kodierte Datenbyte, die mit der Vorlage zusammengeführt werden.</td>
  </tr>
 </tbody>
</table>

1. Rufen Sie im Desktop-Browser „Developer Tools“ -> „Ressourcen“ auf.

   Überprüfen Sie auf der linken Seite unter „Frames“, ob das Bild zu sehen ist.
