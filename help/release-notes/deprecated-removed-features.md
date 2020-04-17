---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.5.
uuid: 81d9a064-e712-4eff-bd3b-6e15513a5435
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: e8e2e01b-0117-48c3-86d8-609d29a147be
docset: aem65
translation-type: tm+mt
source-git-commit: 4be5286858b255a30983b5987ac54c4e71dd4f2f

---


# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von AEM-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Die Funktionen sind zwar nicht mehr unterstützt, aber sie werden nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die in AEM 6.5 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, deren Entfernung in einer zukünftigen Version geplant ist, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderungen ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

<table>
 <tbody>
  <tr>
   <td><b>Bereich</b></td>
   <td><b>Funktion</b></td>
   <td><b>Ersatz</b></td>
  </tr>
  <tr>
   <td>Creative Cloud-Integration</td>
   <td><p><a href="/help/assets/aem-cc-folder-sharing-best-practices.md">Die Freigabe</a> von AEM für Creative Cloud-Ordner wurde in AEM 6.2 eingeführt, um kreativen Benutzern Zugriff auf Assets aus AEM zu geben, sodass sie diese in CC-Anwendungen öffnen und neue Dateien hochladen oder Änderungen in AEM speichern können. Eine neue Funktion der Creative Cloud-Anwendung, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus.</p> <p>Adobe plant keine weiteren Verbesserungen an der Integration der Ordnerfreigabe aus AEM in Creative Cloud. Obwohl die Funktion in AEM enthalten ist, wird Kunden ausdrücklich der Einsatz von Ersatzlösungen empfohlen.</p> </td>
   <td>Kunden wird empfohlen, auf neue Creative Cloud-Integrationsfunktionen wie Adobe Asset Link oder AEM Desktop-App zu wechseln. Weitere Informationen finden Sie unter <a href="/help/assets/aem-cc-integration-best-practices.md">Best Practices für die Integration von AEM und Creative Cloud</a>.</td>
  </tr>
  <tr>
   <td>Assets </td>
   <td>
    <ol>
     <li>AssetDownloadServlet ist bei den Veröffentlichungsinstanzen standardmäßig deaktiviert. Weitere Informationen finden Sie unter <a href="/help/sites-administering/security-checklist.md">Checkliste für die AEM-Sicherheit</a>.</li>
     <li>Wenn ein Benutzer nicht über ausreichende Berechtigungen (Lesen und Schreiben) für /content/dam/collections verfügt, kann er keine Sammlung erstellen.</li>
    </ol> </td>
   <td>
    <ol>
     <li>Konfiguration, wie unter <a href="/help/sites-administering/security-checklist.md">Checkliste für die AEM-Sicherheit</a> beschrieben.</li>
     <li>Einhaltung der Zugangssteuerungseinrichtung für den Benutzer und Sicherstellung entsprechender Berechtigungen.<br />  </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Adobe Search &amp; Promote</td>
   <td><p>Die Integration mit Adobe Search &amp; Promote ist veraltet.</p> <p>Adobe plant keine weiteren Verbesserungen an der Search &amp; Promote-Integration. Beachten Sie, dass die Search &amp; Promote-Integration zwar veraltet ist, aber weiterhin umfassend unterstützt wird.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>DTM Tag Manager</td>
   <td>Die Integration in DTM (Dynamic Tag Manager) ist als veraltet gekennzeichnet.</td>
   <td>Steigen Sie auf Adobe Experience Platform als Tagmanager um.</td>
  </tr>
  <tr>
   <td>Adobe Target</td>
   <td>Durch das Hinzufügen der Möglichkeit in AEM 6.5, dass AEM über die Adobe I/O-basierte Adobe Target Standard-API (Rest-API) eine Verbindung zum Adobe Target-Service herstellt, ist die Methode unter Verwendung der Target Classic-API (AML) veraltet.</td>
   <td><a href="https://helpx.adobe.com/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html">Konfigurieren Sie die Integration so, dass die neue API verwendet werden kann.</a></td>
  </tr>
  <tr>
   <td>Adobe Target</td>
   <td>Die Verwendung der mbox.js-basierten Integration mit Adobe Target ist in AEM als veraltet gekennzeichnet.</td>
   <td>Stellen Sie auf at.js 1.x um.</td>
  </tr>
  <tr>
   <td>Commerce</td>
   <td><p><a href="https://github.com/adobe/commerce-cif-api" target="_blank">CIF REST</a> wurde 2018 als eine Reihe von Mikrodiensten bereitgestellt, um Integrationen zwischen AEM und Commerce-Engines zu ermöglichen.</p> <p>Nach der Übernahme von Magento Mitte 2018 hat Adobe aus zwei Gründen beschlossen, seinen Ansatz zu ändern: </p> <p><strong>1.</strong> Magento verfügt über einen eigenen Satz Commerce-APIs (REST und GraphQL) und es ist keine gute Praxis, zwei APIs zu verwalten </p> <p><strong>2.</strong> Die Markttrends deuten darauf hin, dass Kunden sich auf GraphQL zubewegen, weil es eine effizientere Art ist, Daten abzufragen. Im Jahr 2019 hat Adobe das neue Commerce Integration Framework unter Verwendung der GraphQL APIs von Magento als Quelle der Wahrheit veröffentlicht.</p> <p>Adobe plant keine weiteren Investitionen in CIF REST. Kunden wird dringend empfohlen, die Ersatzlösung zu verwenden.</p> </td>
   <td><p>Für AEM-Magento-Integrationen wechseln Sie zu <a href="https://github.com/adobe/aem-cif-project-archetype" target="_blank">AEM CIF-Archetyp</a>und <a href="https://github.com/adobe/aem-core-cif-components" target="_blank">AEM CIF-Hauptkomponenten</a></p> <p>Weitere Informationen finden Sie unter <a href="https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md" target="_blank">AEM- und Magento-Integration mit Commerce Integration Framework</a> .</p> <p>Die Unterstützung für Integration von Drittanbietern (außer Magento) in den neuen Ansatz ist auf unserem Plan.</p> </td>
  </tr>
  <tr>
   <td>Komponenten (AEM Sites)</td>
   <td><p>Adobe plant keine weiteren Verbesserungen an den meisten Foundation-Komponenten, die in /libs/foundation/components gespeichert sind.</p> <p>Suchen Sie im Komponentenordner nach den Eigenschaften <strong>cq:deprecated</strong> und <strong>cq:deprecatedReason</strong>.</p> <p>In AEM 6.5 sind die Foundation-Komponenten enthalten, und Kunden, die von früheren Versionen aktualisieren, können diese weiterhin wie bisher verwenden. Darüber hinaus werden die Foundation-Komponenten weiterhin vollständig unterstützt, während sie nicht mehr unterstützt werden. </p> </td>
   <td>Kunden wird empfohlen, für künftige Projekte die Kernkomponenten zu verwenden. Existing sites can remain as is or use the <a href="https://github.com/adobe/aem-modernize-tools">AEM Modernize Tools Suite</a> to refactor the site to use Core Components.</td>
  </tr>
  <tr>
   <td>Komponenten (AEM Sites)</td>
   <td>Design-Importtool-Komponenten (/libs/wcm/designimporter/components) sind seit 6.5 als veraltet gekennzeichnet. Adobe plant keine weiteren Verbesserungen an dieser Implementierung des Design-Importtools.</td>
   <td>Adobe plant für künftige Versionen eine alternative Implementierung des Nutzungsszenarios.</td>
  </tr>
  <tr>
   <td>Komponenten (AEM Forms)</td>
   <td><p>Mit dem Unterschriftsschritt können Benutzer ein adaptives Formular überprüfen und unterschreiben. In früheren Versionen konnte der Unterschriftsschritt sowohl die Komponenten "Adobe Sign"als auch "Scribble Signature"als Unterschriftsfelder verwenden. In AEM 6.5 Forms wird das Signaturerlebnis für Scribble-Signaturen des Signatur-Schritts nicht mehr unterstützt.</p> </td>
   <td>
    <ul>
     <li>Wenn Sie eine Neuinstallation durchgeführt haben:
      <ul>
       <li>Verwenden Sie das Adobe Sign-basierte Signaturerlebnis in einem Signaturschritt in einem adaptiven Formular.</li>
       <li>Verwenden Sie die eigenständige Scribble-Signatur-Komponente in einem adaptiven Formular, in einer interaktiven Kommunikation und in HTML5-Formularen.</li>
      </ul> </li>
     <li>Wenn Sie von einer früheren Version auf AEM 6.5 Forms aktualisiert haben:<br />
      <ul>
       <li>Verwenden Sie weiterhin die Scribble-Signatur-basierte Signatur-Erfahrung von Signature Step mit Formularen, die die Funktion bereits verwenden.<br /> </li>
       <li>Verwenden Sie die eigenständige Scribble-Signatur-Komponente oder die Adobe Sign-basierte Signaturerfahrung in einem Signaturschritt, wenn Sie ein neues Formular erstellen. </li>
      </ul> </li>
    </ul> <p> </p> <p> </p> </td>
  </tr>
  <tr>
   <td>Foundation</td>
   <td><p>Granite-Abladeframework</p> <p>Adobe plant keine weiteren Verbesserungen am Abladeframework, der in Version 5.6.1 zur Externalisierung der Asset-Verarbeitung eingeführt wurde. </p> </td>
   <td>Adobe arbeitet an einem cloudnativen Abladeframework der nächsten Generation.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>Hobbes.js</p> <p>Adobe plant keine weiteren Verbesserungen am Testframework für die Benutzeroberfläche von hobbes.js.</p> </td>
   <td>Adobe empfiehlt Kunden, Selenium-Automatisierung zu verwenden.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>jQuery UI-Client-Bibliothek</p> <p>Adobe plant keine weitere Pflege und Aktualisierung der jQuery UI-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird.</p> </td>
   <td>Adobe empfiehlt Kunden, die noch jQuery-Benutzeroberfläche benötigen, damit ihr Code in ihre Projektcodebasis eingefügt werden kann.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>jQuery Animation-Client-Bibliothek (granite.jquery.animation)</p> <p>Adobe plant keine weitere Pflege und Aktualisierung der jQuery Animation-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird.</p> </td>
   <td>Adobe empfiehlt Kunden, die noch jQuery Animations benötigen, um den Code in ihre Projektcodebasis einzufügen.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>Handlebars-Client-Bibliothek</p> <p>Adobe plant keine weitere Pflege und Aktualisierung der Handlebars-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird.</p> </td>
   <td>Adobe empfiehlt Kunden, die für ihren Code weiterhin Handlebars benötigen, um ihn in ihre Projektcodebasis einzufügen.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>Lawnchair-Client-Bibliothek</p> <p>Adobe plant keine weitere Pflege und Aktualisierung der Lawnchair-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird.</p> </td>
   <td>Adobe empfiehlt Kunden, die weiterhin einen Lawnchair benötigen, damit ihr Code in ihre Projektcodebasis eingefügt werden kann.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>Granite.Sling.js-Client-Bibliothek</p> <p>Adobe plant keine weitere Pflege und Aktualisierung der Granite.Sling.js-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird.</p> </td>
   <td>Adobe empfiehlt Kunden, die sich auf die Fähigkeit der Bibliothek verlassen, ihren Code umzugestalten und nicht mehr zu verwenden.</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td>Verwendung von YUI zum Komprimieren/Minimieren der JavaScript-Client-Bibliotheken: Adobe plant keine weitere Aktualisierung der YUI-Bibliothek. Bis zu AEM 6.4 wurde JavaScript standardmäßig mit der Option zum Wechsel zu Google Closure Compiler (GCC) minimiert. Ab AEM 6.5 ist GCC der Standard.</td>
   <td>Adobe empfiehlt Kunden, die auf AEM 6.5 aktualisieren, um zur Implementierung auf GCC zu wechseln</td>
  </tr>
  <tr>
   <td>Entwickler</td>
   <td><p>Dialog-Editor für klassische UI in CRXDE Lite.</p> <p>Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Forms</td>
   <td><p>AEM Forms-Integration mit AEM Mobile&lt; wird nicht mehr unterstützt </p> </td>
   <td>Kein Ersatz vorhanden. </td>
  </tr>
 </tbody>
</table>

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die aus AEM 6.5 entfernt wurden. Frühere Versionen hatten diese Funktionen als veraltet markiert.

| Bereich | Funktion | Ersatz |
|--- |--- |--- |
| Analytics-Aktivität-Map | Die Version der Aktivität Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Verwenden Sie das [ActivityMap-Plugin, das von Adobe Analytics bereitgestellt wird](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html). |
| Integrationen | Die ExactTarget-Integration wurde aus der Standardverteilung (QuickStart) entfernt und ist nicht mehr verfügbar. | Kein Ersatz vorhanden. |
| Integrationen | Die Salesforce Force-API-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist jetzt ein zusätzliches, über PackageShare zu installierendes Paket. | Die Funktion ist weiterhin verfügbar. |
| Formulare | Die Unterstützung für den Adobe Central Migration Bridge-Service wurde eingestellt, da Adobe Central nicht länger unterstützt wird. | Kein Ersatz vorhanden. |
| Forms | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Kein Ersatz vorhanden. |
| Forms | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Kein Ersatz vorhanden. |
| Forms | Eine Single-Hop-Aktualisierung von LiveCycle ES4 SP1 auf AEM 6.5 Forms on JEE ist nicht verfügbar. | Siehe [verfügbare Aktualisierungspfade](../forms/using/upgrade.md) in der Dokumentation zur AEM Forms-Aktualisierung. |
| Entwickler | Firebug Lite wurde aus der Standardverteilung (Quickstart) entfernt. | Verwenden Sie die im Browser integrierten Entwicklerkonsolen. |
| Entwickler | Remove `customJavaScriptPath` support in HTML Client Library Manager. | Kein Ersatz vorhanden. |
| Assets  | Die Funktion zum Abladen von Assets wurde in AEM 6.5 entfernt | Kein Ersatz vorhanden. |
| Cache | `system/console/slingjsp` entfernt wurde, ist in AEM 6.5 nicht mehr verfügbar. | Klassen und Leichter Cache werden unter dem Apache Sling Commons FileSystem ClassLoader Bundle gespeichert. Sie können die Bundle-Nummer in der AEM Web Console überprüfen und den Cache-Ordner direkt aus dem Dateisystem entfernen (`crx-quickstart/launchpad/felix/bundle<ID>`). |

## Vorankündigung für die nächste Version {#pre-announcement-for-next-release}

Dieser Abschnitt wird verwendet, um Änderungen in der zukünftigen Version vorab bekannt zu geben, bei denen es sich nicht um veraltete Funktionen handelt, die aber Auswirkungen für Kunden haben. Diese werden für Planungszwecke bereitgestellt.

| Bereich | Funktion | Mitteilung |
|--- |--- |--- |
| Foundation | UI-Framework | Adobe plant, die Coral UI 2-Komponenten im Jahr 2019 als veraltet zu kennzeichnen. Coral UI 3 wurde mit AEM 6.2 eingeführt und AEM 6.5 basiert vollständig auf Coral 3. Adobe empfiehlt Kunden und Partnern, die benutzerdefinierte UIs mit Coral 2 erstellt haben, ihre UIs für Coral 3 neu zu strukturieren. Adobe stellt ein Tool zur Konvertierung von Coral 2-Dialogfeldern in Coral 3 bereit. [Klicken Sie hier, um mehr zu erfahren.](/help/sites-developing/dialog-conversion.md) |
