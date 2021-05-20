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
role: Administrator
exl-id: 19b5765e-50bc-4fed-8af5-f6bb464516c8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 78%

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

![recommended-topology](assets/recommended-topology.png)

## Systemanforderungen {#system-requirements}

Bevor Sie mit der Installation und Konfiguration der Datenerfassungsfunktion von AEM Forms beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. Installieren Sie für Windows-Benutzer die AEM-Instanz im erweiterten Modus. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens zwei[ AEM-Instanzen (eine Autor- und Veröffentlichungsinstanz),](/help/sites-deploying/deploy.md) um AEM Forms-Datenerfassungsfunktionen auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt über das Internet oder ein internes Netzwerk veröffentlicht.

* Speicheranforderungen werden erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Die Replikation und die umgekehrte Replikation für die Autor- und die Veröffentlichungsinstanz werden festgelegt. Weitere Details finden Sie unter [Replikation](/help/sites-deploying/replication.md).
* Für UNIX-basierte Systeme:

   * Installieren Sie die folgenden 32-Bit-Pakete aus dem Installationsmedium:

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
>* Erstellen Sie die Symlinks libcurl.so, libcrypto.so und libssl.so , die auf die neueste Version der Bibliotheken libcurl, libcrypto und libssl verweisen.

>



* Installieren Sie das folgende 64-Bit-Paket vom Installationsmedium:

   * libicu

## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält AEM bildet Datenerfassung und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads suchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem, wählen Sie **[!UICONTROL Endbenutzer-Lizenzbedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.
1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen ServiceEvent REGISTERED und ServiceEvent UNREGISTERED nicht mehr in der  `[AEM-Installation-Directory]/crx-quickstart/logs/error.log` Datei angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen.  

### (Nur Windows) Automatische Installation von Visual Studio-Redistributables {#automatic-installation-visual-studio-redistributables}

Wenn Sie eine AEM-Instanz im erhöhten Modus installieren, werden die fehlenden Visual Studio-Redistributables während der Installation des AEM Forms Add-On-Pakets automatisch installiert.

Um zu prüfen, ob die Redistributables von Visual Studio automatisch installiert sind, öffnen Sie die Datei `error.log` im Verzeichnis `/crx-repository/logs/` . Die Protokolle enthalten die folgende Meldung:

`Redist <service name> already installed on system, will not attempt re-installation`

Wenn die Redistributables nicht installiert werden können, enthalten die Protokolle die folgende Meldung:

`Current user does not have elevated privileges, aborting installation of redist <service name>`

Um das Problem zu beheben, starten Sie den AEM-Server neu, installieren Sie AEM im erhöhten Modus und installieren Sie dann das Add-On-Paket für AEM Forms.

Wenn die Berechtigungsprüfung fehlschlägt, enthalten die Protokolle die folgende Meldung:

`Privilege escalation check failed with error: <error message>`

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher, Forms Portal, Adobe Sign, Adobe Analytics und Adobe Target.

### Obligatorisch Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die Datei `[AEM installation directory]\crx-quickstart\conf\sling.properties` zur Bearbeitung.

   Wenn Sie `[AEM installation directory]\crx-quickstart\bin\start.bat` zum Starten von AEM verwendet haben, bearbeiten Sie die sling.properties-Datei unter `[AEM_root]\crx-quickstart\`.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritte 1-4 für alle Autor- und Veröffentlichungsinstanzen.

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen aus, um das Paket zur Zulassungsliste hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. Die Standardeinstellung ist `https://'[server]:[port]'/system/console/configMgr`.
1. Suchen Sie nach **com.adobe.cq.deserfw.impl.DeserializationFirewallImpl.name** und öffnen Sie die Konfiguration.
1. Fügen Sie das Paket **sun.util.calendar** zum Feld **Zulassungsliste** hinzu. Klicken Sie auf **Speichern**.
1. Wiederholen Sie Schritte 1-3 für alle Autor- und Veröffentlichungsinstanzen.

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Konfiguration des Dispatchers {#configure-dispatcher}

Der Dispatcher ist das Tool zum Zwischenspeichern und/oder Lastenausgleich von Adobe Experience Manager, das in Verbindung mit einem Webserver der Unternehmensklasse verwendet werden kann. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. Die Standard-URL des Konfigurationsmanagers lautet `https://[server]:[port_number]/system/console/configMgr`. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist &quot;https://[server]:[port]&quot;.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zu AEM Konfigurationsmanager der Web-Konsole unter https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Klicken Sie auf **Konfiguration für adaptive Formulare und interaktiver Kommunikationswebkanal**, um die Konfigurationswerte zu bearbeiten. Geben Sie im Dialogfeld &quot;Konfigurationswerte bearbeiten&quot;die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **Anzahl adaptiver Forms** zwischenspeichern kann. Der Standardwert ist 100. Klicken Sie auf **Speichern**.

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
* [Erstellen Sie Ihr erstes PDF Formular](http://www.adobe.com/go/learn_aemforms_designer_quick_start_65_de)
* [Einführung in HTML5-Formulare](/help/forms/using/introduction.md)
