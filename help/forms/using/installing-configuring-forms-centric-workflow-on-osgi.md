---
title: Installieren und Konfigurieren des formularzentrierten Workflows auf OSGi
seo-title: Installieren und Konfigurieren des formularzentrierten Workflows auf OSGi
description: Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen.
seo-description: Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen.
uuid: 1ceae822-215a-4b83-a562-4609a09c3a54
topic-tags: installing
discoiquuid: de292a19-07db-4ed3-b13a-7a2f1cd9e0dd
docset: aem65
translation-type: tm+mt
source-git-commit: a18a018181a779b9f48ef3e39c26410a1bc4919b
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 54%

---


# Installieren und Konfigurieren des formularzentrierten Workflows auf OSGi{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Einführung {#introduction}

Unternehmen erfassen und verarbeiten Daten aus mehreren Formularen, Back-End-Systemen und anderen Datenquellen. Die Datenverarbeitung umfasst Überprüfungs- und Genehmigungsverfahren, sich wiederholende Aufgaben und die Datenarchivierung. Betrachten Sie beispielsweise ein Formular und konvertieren Sie es in ein PDF-Dokument. Bei manueller Ausführung können sich die sich wiederholenden Aufgaben sehr viel Zeit und Ressourcen kosten.

Sie können den [formularorientierten Arbeitsablauf auf OSGi](../../forms/using/aem-forms-workflow.md) verwenden, um schnell adaptive formularbasierte Workflows zu erstellen. Diese Workflows unterstützen Sie bei der Automatisierung von Review- und Genehmigungs-Workflows, Workflows und anderen wiederholten Aufgaben. Diese Workflows helfen auch bei der Verarbeitung von Dokumenten (Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen, um den Zugriff auf Dokumente zu beschränken, Barcode-Formulare zu dekodieren und vieles mehr) und bei der Verwendung des Adobe Signatur-Workflows mit Formularen und Dokumenten.

Nach der Einrichtung können diese Workflows manuell ausgelöst werden, um einen definierten Prozess abzuschließen oder programmgesteuert auszuführen, wenn Benutzer ein Formular oder eine interaktive Kommunikation senden. Die Funktion ist im AEM Forms Add-On-Paket enthalten.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse. Der formularorientierte Arbeitsablauf auf OSGi ist nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](introduction-aem-forms.md).

>[!NOTE]
>
>Mit formularzentrierten Workflows in OSGi können Sie schnell Workflows für verschiedene Aufgaben auf dem OSGi-Stapel erstellen und bereitstellen, ohne die komplette Prozessverwaltungsfunktion auf dem JEE-Stapel zu installieren. Weitere Informationen zu den Unterschieden und Ähnlichkeiten in den Funktionen finden Sie in einem [Vergleich](capabilities-osgi-jee-workflows.md) der formularzentrierten AEM Workflows auf OSGi und Process Management on JEE.
>
>Nach dem Vergleich finden Sie unter Installieren oder Aktualisieren von AEM Forms auf JEE [](/help/forms/home.md) ausführliche Informationen zum Installieren und Konfigurieren von JEE-Stack und zu den Process Management-Funktionen, wenn Sie die Process Management-Funktion auf JEE-Stack installieren.

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur mindestens ein AEM Author oder eine Verarbeitungsinstanz (Produktionsautor), um den formularzentrierten Workflow mit OSGi-Funktionen auszuführen. A processing instance is a [hardened AEM Author](/help/forms/using/hardening-securing-aem-forms-environment.md) instance. Führen Sie kein tatsächliches Authoring wie das Erstellen von Workflows oder adaptiven Formularen im Produktionsautor durch.

Die folgende Topologie ist eine indikative Topologie zum Ausführen von AEM Forms Interactive Communications, Correspondence Management, AEM Forms-Datenerfassung und Forms-Centric-Workflow für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommendations-topology](assets/recommended-topology.png)

AEM Forms Forms-zentrierter Arbeitsablauf auf OSGi führt die Benutzeroberfläche zur Erstellung von AEM Inbox- und AEM Workflow-Modellen auf den Autoreninstanzen von AEM Forms aus.

## Systemanforderungen {#system-requirements}

>[!NOTE]
>
>Gehen Sie zum Abschnitt [Nächste Schritte](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) des Dokuments, wenn Sie bereits AEM Forms auf OSGi installiert haben, wie im Artikel [Installations- und Konfigurationsfunktionen](../../forms/using/installing-configuring-aem-forms-osgi.md) beschrieben.

Bevor Sie mit der Installation und Konfiguration des formularzentrierten Workflows auf OSGi beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM-Instanz (Autor oder Verarbeitung), um einen formularzentrierten Workflow unter OSGi auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Verarbeitung:** Eine Verarbeitungsinstanz ist eine [extrasichere Instanz von AEM Autor](/help/forms/using/hardening-securing-aem-forms-environment.md). Sie können eine Autoreninstanz einrichten und nach der Installation absichern.

   * **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt über das Internet oder ein internes Netzwerk veröffentlicht.

* Speicheranforderungen werden erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie die folgenden-Pakete aus den Installationsmedien des jeweiligen Betriebssystems.

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

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält einen formularzentrierten Arbeitsablauf auf OSGi und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Open [Software Distribution](https://experience.adobe.com/downloads). Sie benötigen eine Adobe ID, um sich bei der Softwareverteilung anzumelden.
1. Tippen Sie auf **[!UICONTROL Adobe Experience Manager]** , der im Kopfzeilenmenü verfügbar ist.
1. In the **[!UICONTROL Filters]** section:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** .
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können die Ergebnisse auch mit der Option **[!UICONTROL Downloads]** suchen filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie &quot;Endbenutzer-Lizenzbedingungen **[!UICONTROL akzeptieren&quot;]** und klicken Sie auf &quot; **[!UICONTROL Herunterladen]**&quot;.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf Paket **[!UICONTROL hochladen]** , um das Paket hochzuladen.
1. Select the package and click **[!UICONTROL Install]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie, bevor Sie den AEM Forms-Server beenden, bis die Meldungen &quot;ServiceEvent REGISTERED&quot;und &quot;ServiceEvent UNREGISTERED&quot;in der Datei &quot; [AEM-Installationsverzeichnis]/crx-quickstart/logs/error.log&quot;nicht mehr angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen.  

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

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
1. Wiederholen Sie Schritten 1-4 für alle Autor- und Veröffentlichungsinstanzen.  

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie die folgenden Schritte für alle Instanzen im Autoren- und Veröffentlichungsmodus aus, um das Paket der Zulassungsliste &quot;&quot;hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. The default URL is https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Suchen und öffnen Sie die **Deserialisierungs-Firewallkonfiguration**.
1. Add the **sun.util.calendar** package to the **allowlist** field. Klicken Sie auf Speichern.
1. Wiederholen Sie Schritten 1-3 für alle Autor- und Veröffentlichungsinstanzen.  

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher·ist ein·Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Durch Anwendung von AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. The Default URL of the configuration manager is https://&#39;server&#39;:[port_number]/system/console/configMgr. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. The format of the entry is `https://'[server]:[port]'`.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Go to AEM web console configuration manager at `https://'[server]:[port]'/system/console/configMgr`.
1. Click **Adaptive Form Configuration Service** to edit its configuration values. In the edit configuration values dialog, specify the maximum number of forms or documents an instance of the AEM Forms server can cache in the **Number of Adaptive Forms** field. Der Standardwert ist 100.       Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Adobe Sign konfigurieren {#configure-adobe-sign}

Adobe Sign aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In a typical Adobe Sign and Forms-centric workflow on OSGi scenario, a user fills an adaptive form to **apply for a service**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger. Wenn ein Benutzer das Antragsformular ausfüllt, sendet und unterzeichnet, wird ein Genehmigungsvorgang gestartet. Der Dienstleister prüft die Anwendung in AEM Inbox und verwendet Adobe Sign, um die Anwendung elektronisch zu signieren. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, [integrieren Sie Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung des formularzentrierten Arbeitsablaufs auf OSGi-Funktionen konfiguriert. Die folgenden Schritte zur Nutzung der Funktion sind nun die folgenden:

* [Verwenden des formularzentrierten Workflows auf OSGi](../../forms/using/aem-forms-workflow.md)
* [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md)
* [Nachbearbeitung von Briefen und interaktiver Kommunikation](../../forms/using/submit-letter-topostprocess.md)

