---
title: Installieren und konfigurieren Sie Datenerfassungsfunktionen
seo-title: Installieren und konfigurieren Sie Datenerfassungsfunktionen
description: Installieren und konfigurieren Sie adaptive Formulare, PDF-Formulare und HTML5-Formulare. Konfigurieren Sie Adobe Analytics und Adobe Target für adaptive Formulare, um die Verwendung von Formularen und Zielbenutzern anhand ihres Profils zu analysieren.
seo-description: Installieren und konfigurieren Sie adaptive Formulare, PDF-Formulare und HTML5-Formulare. Konfigurieren Sie Adobe Analytics und Adobe Target für adaptive Formulare, um die Verwendung von Formularen und Zielbenutzern anhand ihres Profils zu analysieren.
uuid: 5d49032a-4dea-4f21-9dad-a7a30c5872ea
topic-tags: installing
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dfc473eb-6091-4f5d-a5a0-789972c513a9
docset: aem65
translation-type: tm+mt
source-git-commit: 5831c173114a5a6f741e0721b55d85a583e52f78

---


# Installieren und konfigurieren Sie Datenerfassungsfunktionen{#install-and-configure-data-capture-capabilities}

## Einführung {#introduction}

AEM Forms bietet eine Reihe von Formularen, um Daten vom Endbenutzer zu erhalten: adaptive Formulare, HTML5-Formulare und PDF-Formulare. Darüber hinaus bietet es Tools zum Auflisten aller verfügbaren Formulare auf einer Webseite, Analysieren der Verwendung von Formularen und Targeting von Benutzern anhand ihres Profils. Diese Funktionen sind im Add-On-Paket für AEM Forms enthalten. Das Add-On-Paket wird auf einer Autor- oder Veröffentlichungsinstanz von AEM bereitgestellt.

**Adaptive Formulare:** Diese Formulare ändern Aussehen aufgrund der Bildschirmgröße des Geräts, sind ansprechend und interaktiv. Adaptive Formulare können auch mit Adobe Analytics, Adobe Sign und Adobe Target integriert werden. Es ermöglichte Ihnen, basierend auf der Demografie und anderen Funktionen, personalisierte Formulare und prozessorientierte Benutzererfahrungen bereitzustellen. Sie können außerdem adaptive Formulare mit Adobe Sign integrieren.

**PDF-Formulare** eignen sich für pixelgenaues Drucken und digitale Informationserfassung in einem PDF-Dokument. Im digitalen Avatar können Sie Adobe Acrobat oder Acrobat Reader verwenden, um diese Formulare zu füllen. Sie können diese Formulare auf Ihrer Website hosten oder das Formularportal verwenden, um diese Formulare auf einer AEM-Site aufzulisten. Sie können diese Formulare auch als Anhang an andere senden. Diese Formulare eignen sich am besten für Desktopumgebungen.

**HTML5-Forms** sind die browserfreundliche Version von PDF-Formularen. HTML5-Forms eignen sich für Umgebungen, in denen PDF-Plug-Ins nicht unterstützt werden. HTML5-Forms ermöglichen das Anzeigen von Formularen auf mobilen Geräten und Desktop-Browsern, auf denen XFA-basierte PDF nicht unterstützt werden. Diese Formulare sind für Tablets und Desktops am besten geeignet.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse und die Datenerfassung (adaptive Formulare, PDF-Formulare und HTML5-Formulare) ist nur eine der Möglichkeiten von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur ein Minimum einer AEM Autor- oder Veröffentlichungsinstanz, um AEM Forms-Datenerfassungsfunktionen auszuführen. Die folgende Topologie wird zum Ausführen von AEM Forms-Datenerfassungsfunktionen von AEM Forms empfohlen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommendations-topology](assets/recommended-topology.png)

## Systemanforderungen {#system-requirements}

Bevor Sie mit der Installation und Konfiguration der Datenerfassungsfunktion von AEM Forms beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens zwei[ AEM-Instanzen (eine Autor- und Veröffentlichungsinstanz),](/help/sites-deploying/deploy.md) um AEM Forms-Datenerfassungsfunktionen auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt über das Internet oder ein internes Netzwerk veröffentlicht.

* Speicheranforderungen werden erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Die Replikation und die umgekehrte Replikation für die Autor- und die Veröffentlichungsinstanz werden festgelegt. Weitere Details finden Sie unter [Replikation](/help/sites-deploying/replication.md).
* Bei UNIX-basierten Systemen:

   * Installieren Sie die folgenden 32-Bit-Pakete vom Installationsmedium:

<table>
 <tbody>
  <tr>
   <td>expat</td>
   <td>fontconfig</td>
   <td>freetype</td>
   <td>glibc</td>
  </tr>
  <tr>
   <td>libcurl</td>
   <td>libICE</td>
   <td>libicu</td>
   <td>libSM</td>
  </tr>
  <tr>
   <td>libuuid</td>
   <td>libX11</td>
   <td><p>libXau</p> </td>
   <td>libxcb</td>
  </tr>
  <tr>
   <td>libXext</td>
   <td>libXinerama</td>
   <td>libXrandr</td>
   <td>libXrender</td>
  </tr>
  <tr>
   <td>nss-softokn-freebl</td>
   <td>OpenSSL</td>
   <td>zlib</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Wenn OpenSSL bereits auf dem Server installiert ist, aktualisieren Sie es auf die neueste Version.
>* Erstellen Sie die Symlinks libcurl.so, libcrypto.so und libssl.so, die auf die neueste Version der Bibliotheken libcurl, libcrypto und libssl verweisen.
>



* Installieren Sie das folgende 64-Bit-Paket vom Installationsmedium:

   * libicu

## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält AEM bildet Datenerfassung und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Melden Sie sich beim [AEM-Server](https://localhost:4502) als Administrator an und öffnen Sie [Package Share](https://localhost:4502/crx/packageshare). Zum Anmelden bei der Paketfreigabe benötigen Sie eine Adobe ID.
1. Suchen Sie in [AEM Package Share](https://localhost:4502/crx/packageshare/login.html) nach **Add-On-Pakete für AEM 6.5 Forms** und klicken Sie auf das Paket, das auf Ihr Betriebssystem zutrifft, und dann auf **Herunterladen**. Lesen und akzeptieren Sie die Lizenzvereinbarung und klicken Sie auf **OK**. Der Download wird gestartet. Nachdem der Download abgeschlossen ist, wird das Wort **Heruntergeladen** neben dem Paket angezeigt.

   Sie können auch die Versionsnummer verwenden, um nach einem Add-On-Paket zu suchen. Die Versionsnummer für das neueste Paket finden Sie im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

1. Nachdem der Download abgeschlossen ist, klicken Sie auf **Heruntergeladen**. Sie werden zum Paketmanager weitergeleitet. Suchen Sie im Paketmanager das heruntergeladene Paket und klicken Sie auf **Installieren**.

   Wenn Sie das Paket manuell über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) angegeben ist, melden Sie sich beim Paketmanager an, klicken Sie auf **Paket hochladen**, wählen Sie das heruntergeladene Paket aus und klicken Sie auf „Hochladen“. Nachdem Sie das Paket hochgeladen haben, klicken Sie auf den Paketnamen und dann auf **Installieren.**

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Bevor Sie den AEM Forms-Server beenden, warten Sie, bis die Nachrichten &quot;ServiceEvent REGISTERED&quot;und &quot;ServiceEvent UNREGISTERED&quot;in der `[AEM-Installation-Directory]/crx-quickstart/logs/error.log` Datei nicht mehr angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-4 für alle Autor- und Veröffentlichungsinstanzen.  

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher, Forms Portal, Adobe Sign, Adobe Analytics und Adobe Target.

### Obligatorisch Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Open the [AEM installation directory]\crx-quickstart\conf\sling.properties file for editing.

   If you used [AEM installation directory]\crx-quickstart\bin\start.bat to start AEM, then edit the sling.properties located at [AEM_root]\crx-quickstart\.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritte 1-4 für alle Autor- und Veröffentlichungsinstanzen.

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie die folgenden Schritte auf allen Autor- und Veröffentlichungsinstanzen aus, um das Paket auf die Whitelist zu setzen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. The default URL is `https://[server]:[port]/system/console/configMgr`.
1. Suchen Sie nach **com.adobe.cq.deserfw.impl.DeserializationFirewallImpl.name** und öffnen Sie die Konfiguration.
1. Fügen Sie das Paket **sun.util.calendar** zum Feld **Whitelist** hinzu. Klicken Sie auf **Speichern**.
1. Wiederholen Sie Schritte 1-3 für alle Autor- und Veröffentlichungsinstanzen.

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher·ist ein·Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Durch Anwendung von AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. The Default URL of the configuration manager is https://[server]:[port_number]/system/console/configMgr. In the **Configurations **menu, select the **Apache Sling Referrer Filter** option. Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. The format of the entry is https://[server]:[port].

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Go to AEM web console configuration manager at https://[server]:[port]/system/console/configMgr.
1. Klicken Sie auf **Konfiguration für adaptive Formulare und interaktiver Kommunikationswebkanal**, um die Konfigurationswerte zu bearbeiten. In the edit configuration values dialog, specify the maximum number of forms or documents an instance of the AEM Forms server can cache in the **Number of Adaptive Forms** field. Der Standardwert ist 100. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Konfigurieren Sie die SSL-Kommunikation für das Formulardatenmodell {#configure-ssl-communcation-for-form-data-model}

Sie können die SSL-Kommunikation für das Formulardatenmodell aktivieren. Um die SSL-Kommunikation für das Formulardatenmodell zu aktivieren, fügen Sie vor dem Starten einer AEM Forms-Instanz Zertifikate zum Java Trust Store aller Instanzen hinzu. Sie können den folgenden Befehl ausführen, um die Zertifikate hinzuzufügen: &quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Adobe Sign konfigurieren {#configure-adobe-sign}

Adobe Sign aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In einem typischen Szenario mit Adobe Sign und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine **Dienstleistung zu beantragen**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstanbieter gesendet. Dienstanbieter prüft den Antrag und markiert ihn mit Adobe Sign als genehmigt. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, [integrieren Sie Adobe Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Konfigurieren Sie Analytics {#configure-adobe-analytics}

AEM Forms ermöglicht die Integration in Adobe Analytics, sodass Sie Leistungsmetriken für Ihre veröffentlichten Formulare und Dokumente erfassen und verfolgen können. Ziel dieser Analyse ist es, informierte, auf Daten basierende Entscheidungen zu erforderlichen Formularänderungen treffen zu können, durch die Formulare oder Dokumente benutzerfreundlicher werden.

Adobe Analytics mit AEM Forms finden Sie unter [Konfigurieren von Analytics und Berichte](/help/forms/using/configure-analytics-forms-documents.md).

#### Integrieren von Adobe Target {#integrate-adobe-target}

Ihre Kunden werden ein Formular wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kunden ist dies ein frustrierendes Erlebnis. Für Ihr Unternehmen kann es zusätzlichen Supportaufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konvertierungsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. Mit AEM forms erhalten Sie das entscheidende Werkzeug.

AEM forms kann mit der Adobe Marketing Cloud-Lösung Adobe Target integriert werden, um den Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Um Adobe Target für A/B-Tests für adaptive Formulare zu verwenden, [integrieren Sie Adobe Target in AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung der AEM Forms-Datenerfassungsfunktionen konfiguriert. Die nächsten Schritte zur Verwendung der Funktionen, sind Folgende:

* [Erstellen Sie Ihr erstes adaptives Formular](/help/forms/using/create-your-first-adaptive-form.md)
* [Erstellen Sie Ihr erstes PDF Formular](http://www.adobe.com/go/learn_aemforms_designer_quick_start_65)
* [Einführung in HTML5-Formulare](/help/forms/using/introduction.md)

