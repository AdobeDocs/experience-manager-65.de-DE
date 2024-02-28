---
title: Installieren und Konfigurieren von interaktiven Kommunikationen
description: Installieren und konfigurieren Sie interaktive Kommunikationen in AEM Forms, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommens-Kits zu erstellen.
topic-tags: installing
docset: aem65
role: Admin
exl-id: 37fcfad9-2f84-4f0c-aed8-e4a5a3303a06
source-git-commit: d195ac80ee59439bab5b1219a2c1f16e93e3d22b
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 95%

---

# Installieren und konfigurieren Sie Interaktive Kommunikationen{#install-and-configure-interactive-communications}

## Einführung {#introduction}

Mit AEM Form lässt sich die Generierung, Zusammenstellung, Verwaltung und Lieferung von sicheren und interaktiven Dokumenten wie Geschäftskorrespondenzen, Dokumenten, Kontoauszügen, Mitteilungen über finanzielle Leistungen, Marketing-Mails, Rechnungen und Willkommenspaketen zentralisieren. Diese Funktion wird als interaktive Kommunikation bezeichnet. Die Funktion ist im Add-on-Paket zu AEM Forms enthalten. Das Add-On-Paket wird auf einer Authoring- oder Publishing-Instanz von AEM bereitgestellt.

Sie können die Funktion der interaktiven Kommunikation verwenden, um Kommunikation in mehreren Formaten zu erstellen. Zum Beispiel Web und PDF. Sie können die interaktive Kommunikation mit AEM Workflow integrieren, um die zusammengesetzte Kommunikation zu verarbeiten und sie den Kundinnen und Kunden über den Kanal ihrer Wahl zu liefern. Beispielsweise, indem Sie eine Kommunikation per E-Mail an die Endnutzerin oder den Endnutzer senden.

Wenn Sie ein Upgrade von einer früheren Version durchführen und bereits in die Korrespondenzverwaltung investiert haben, können Sie das [Kompatibilitätspaket](../../forms/using/installing-configuring-intreactive-communication-correspondence-management.md#install-compatibility-package) installieren, um die Korrespondenzverwaltung weiterhin zu verwenden. Informationen zu den Unterschieden zwischen interaktiver Kommunikation und Korrespondenzverwaltung finden Sie unter [Übersicht über interaktive Kommunikation](/help/forms/using/interactive-communications-overview.md#interactive-communications-vs-correspondence-management).

AEM Forms ist eine leistungsstarke Plattform der Unternehmensklasse. Interaktive Kommunikation ist nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](../../forms/using/introduction-aem-forms.md).

## Bereitstellungstopologie {#deployment-topology}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur mindestens eine AEM-Authoring- und Verarbeitungsinstanz, um die Funktion „Interaktive Kommunikation“ zu nutzen. Die folgende Topologie ist eine indikative Topologie für die Nutzung der interaktiven Kommunikation in AEM Forms, Correspondence Management, AEM Forms-Datenerfassung und formularzentrierten Workflows für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommended-topology](assets/recommended-topology.png)

Interaktive Kommunikationen in AEM Forms führen Administrations-, Authoring- und Agentenbenutzeroberflächen auf den Authoring-Instanzen von AEM Forms aus. Die Publishing-Instanzen hosten die endgültige Version der interaktiven Kommunikation, die für Endnutzende nutzbar ist.

## Systemanforderungen {#system-requirements}

Bevor Sie mit der Installation und Konfiguration interaktiver Kommunikations- und Korrespondenzverwaltungsfunktionen von AEM Forms beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM Instanz läuft. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM-Instanz (Autor oder Verarbeitung), um die interaktiven Kommunikations- und Korrespondenzverwaltungsfunktionen von AEM Forms ausführen zu können:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Verarbeitung:** Eine Verarbeitungsinstanz ist eine [extrasichere AEM-Authoring-Instanz](/help/forms/using/hardening-securing-aem-forms-environment.md). Nach der Installation können Sie eine Autoreninstanz festlegen und absichern.

   * **Veröffentlichung**: Eine AEM-Instanz, die die veröffentlichten Inhalte über das Internet oder ein internes Netzwerk öffentlich zugänglich macht.

* Es gibt gewisse Arbeitsspeicheranforderungen. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft® Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Zusätzliche Anforderungen für UNIX-basierte Systeme: Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie die folgenden Pakete über die Installationsmedien des jeweiligen Betriebssystems.

<table>
 <tbody>
  <tr>
   <td>expat</td>
   <td>libxcb</td>
   <td>freetype</td>
   <td>libXau</td>
  </tr>
  <tr>
   <td>libSM</td>
   <td>zlib</td>
   <td>libICE</td>
   <td>libuuid</td>
  </tr>
  <tr>
   <td>glibc</td>
   <td>libXext</td>
   <td><p>nss-softokn-freebl</p> </td>
   <td>fontconfig</td>
  </tr>
  <tr>
   <td>libX11</td>
   <td>libXrender</td>
   <td>libXrandr</td>
   <td>libXinerama</td>
  </tr>
 </tbody>
</table>

## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält Funktionen für AEM Forms, darunter für interaktive Kommunikation, Korrespondenz-Management und weitere. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Auswählen **[!UICONTROL Adobe Experience Manager]** im Kopfzeilenmenü verfügbar.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen aus und wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und wählen Sie **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „[AEM-Installation-Directory]/crx-quickstart/logs/error.log“ angezeigt werden und das Protokoll stabil ist.

   >[!NOTE]
   >
   > Es wird empfohlen, den Befehl &quot;Strg + C&quot;zu verwenden, um das SDK neu zu starten. Das Neustart des AEM SDK mithilfe alternativer Methoden, z. B. das Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM Entwicklungsumgebung führen.

1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen.

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

Einige der Konfigurationen von AEM Forms sind obligatorisch und andere optional. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

### Obligatorische Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die Datei „[AEM-Installationsverzeichnis]\crx-quickstart\conf\sling.properties“ zur Bearbeitung.

   Wenn Sie „[AEM-Installation-Directory]\crx-quickstart\bin\start.bat“ zum Starten von AEM verwendet haben, bearbeiten Sie die Datei „sling.properties“ unter [AEM_root]\crx-quickstart\.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritten 1-4 für alle Autor- und Veröffentlichungsinstanzen.

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie auf allen Autoren- und Veröffentlichungsinstanzen folgende Schritte aus, um das Paket zur Zulassungsliste hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. Die Standard-URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Suchen und öffnen Sie die **Deserialisierungs-Firewallkonfiguration**.
1. Fügen Sie das Paket **sun.util.calendar** zum Feld **Zulassungsliste** hinzu. Klicken Sie auf Speichern.
1. Wiederholen Sie Schritten 1-3 für alle Autor- und Veröffentlichungsinstanzen.

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Installieren des Kompatibilitäts-Pakets {#install-compatibility-package}

Interaktive Kommunikation ist der Standard und empfohlene Ansatz, um Kundenkommunikation in AEM 6.5 Forms zu erstellen. Wenn Sie ein Upgrade oder eine Migration von einer früheren Version durchgeführt haben und weiterhin Briefe (Correspondence Management) verwenden möchten, installieren Sie das [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-65/forms/upgrade-aem-forms/aem-forms-osgi-upgrade/compatibility-package.html?lang=de).

Mit dem AEMFD-Kompatibilitätspaket können Sie die folgenden Assets aus AEM 6.4 Forms, AEM 6.3 Forms und AEM 6.2 Forms in AEM 6.5 Forms verwenden:

* Dokumentfragmente
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

#### Konfiguration des Dispatchers {#configure-dispatcher}

Der Dispatcher ist das Werkzeug für das Caching und/oder den Lastenausgleich von Adobe Experience Manager, das in Verbindung mit einem Webserver der Enterprise-Klasse verwendet werden kann. Wenn Sie [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“ zum Bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie ihm den folgenden Filter hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Detaillierte Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de).

1. So konfigurieren Sie den Referrer-Filterdienst:

   Melden Sie sich beim Apache Felix Configuration Manager als Admin an. Die Standard-URL von Configuration Manager lautet https://&#39;server&#39;:[port_number]/system/console/configMgr. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Host-Namen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist https://&#39;[Server]:[Port]&#39;.

#### Integrieren mit Adobe Target {#integrate-adobe-target}

Ihre Kunden werden interaktive Kommunikation wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kundschaft ist dies ein frustrierendes Erlebnis, und für Ihr Unternehmen kann es zusätzlichen Support-Aufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konvertierungsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. AEM Forms ist der Schlüssel zu diesem Problem.

AEM Forms kann mit Adobe Target, einer Adobe Experience Cloud-Lösung, integriert werden, um Kundinnen und Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Um Adobe Target zur Personalisierung einer interaktiven Kommunikation zu verwenden, [integrieren Sie Adobe Target in AEM Forms](../../forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

#### Konfigurieren der SSL-Kommunikation für das Formulardatenmodell  {#configure-ssl-communcation-for-form-data-model}

Sie können für das Formulardatenmodell die SSL-Kommunikation aktivieren. Um die SSL-Kommunikation für das Formulardatenmodell zu aktivieren, fügen Sie vor dem Starten einer AEM Forms-Instanz Zertifikate zum Java™ Trust Store aller Instanzen hinzu. Sie können den folgenden Befehl ausführen, um die Zertifikate hinzuzufügen:

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung konfiguriert, in der Funktionen für interaktive Kommunikation und Korrespondenz-Management verwendet werden können. Die nächsten Schritte zur Verwendung der Funktionen, sind Folgende:

* [Überblick über Correspondence Management](/help/forms/using/interactive-communications-overview.md)

* [Interaktive Kommunikation erstellen](../../forms/using/create-interactive-communication.md)

* [Erstellen eines Correspondence Management-Briefs](../../forms/using/create-letter.md)
