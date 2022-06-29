---
title: Installieren und Konfigurieren eines formularzentrierten Workflows unter OSGi
seo-title: Installing and Configuring Forms-centric workflow on OSGi
description: Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen.
seo-description: Install and configure AEM Forms Interactive Communications to create business correspondences, documents, statements, benefit notices, marketing mails, bills, and welcome kits.
uuid: 1ceae822-215a-4b83-a562-4609a09c3a54
topic-tags: installing
discoiquuid: de292a19-07db-4ed3-b13a-7a2f1cd9e0dd
docset: aem65
role: Admin
exl-id: 4b24a38a-c1f0-4c81-bb3a-39ce2c4892b1
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: ht
source-wordcount: '1614'
ht-degree: 100%

---

# Installieren und Konfigurieren eines formularzentrierten Workflows unter OSGi{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Einführung {#introduction}

Unternehmen erfassen und verarbeiten Daten aus mehreren Formularen, Back-End-Systemen und anderen Datenquellen. Zur Datenverarbeitung gehören Überprüfungs- und Validierungsverfahren, sich wiederholende Aufgaben und die Datenarchivierung. Zum Beispiel wird ein Formular überprüft und in ein PDF-Dokument konvertiert. Wenn die sich wiederholenden Aufgaben manuell durchgeführt werden, kann dies viel Zeit und Ressourcen in Anspruch nehmen.

Sie können [formularzentrierte Workflows unter OSGi](../../forms/using/aem-forms-workflow.md) verwenden, um schnell adaptive formularbasierte Workflows zu erstellen. Diese Workflows können Ihnen dabei helfen, Prüfungs- und Genehmigungs-Workflows, Geschäftsprozess-Workflows und andere sich wiederholende Aufgaben zu automatisieren. Diese Workflows helfen auch bei der Verarbeitung von Dokumenten (Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen, um den Zugriff auf-Dokumente zu beschränken, Decodieren von Barcode-Formularen und mehr) sowie bei der Verwendung des Signatur-Workflows von Adobe Sign mit Formularen und Dokumenten.

Wenn diese Workflows einmal eingerichtet sind, können sie manuell ausgelöst werden, um einen definierten Prozess abzuschließen, oder sie können programmgesteuert ausgeführt werden, wenn Benutzer ein Formular oder eine interaktive Kommunikation übermitteln. Die Funktion ist im AEM Forms Add-On-Paket enthalten.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse. Formularzentrierte Workflows unter OSGi sind nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](introduction-aem-forms.md).

>[!NOTE]
>
>Mit formularzentrierten Workflows in OSGi können Sie schnell Workflows für verschiedene Aufgaben auf dem OSGi-Stapel erstellen und bereitstellen, ohne die komplette Prozessverwaltungsfunktion auf dem JEE-Stapel zu installieren. In diesem [Vergleich](capabilities-osgi-jee-workflows.md) der formularbasierten AEM-Workflows unter OSGi mit dem Process Management auf JEE erfahren Sie mehr über die Unterschiede und Gemeinsamkeiten der Funktionen.
>
>Wenn Sie sich nach dem Vergleich für die Installation der Process Management-Funktionen auf dem JEE-Stapel entscheiden, finden Sie unter [Installieren oder Aktualisieren von AEM Forms auf JEE](/help/forms/home.md) detaillierte Informationen zum Installieren und Konfigurieren des JEE-Stapels und der Process Management-Funktionen.

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen minimal nur eine AEM-Autoren- oder -Verarbeitungsinstanz (Produktionsautor), um die Funktionalität des formularzentrierten Workflows unter OSGi auszuführen. Eine Verarbeitungsinstanz ist eine [extrasichere AEM-Autoreninstanz](/help/forms/using/hardening-securing-aem-forms-environment.md). Führen Sie auf dem Produktionsautor kein tatsächliches Authoring durch, wie das Erstellen von Workflows oder adaptiven Formularen.

Die folgende Topologie ist eine indikative Topologie zum Ausführen von AEM Forms Interactive Communications, Correspondence Management, AEM Forms-Datenerfassung und Forms-Centric-Workflow für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommended-topology](assets/recommended-topology.png)

Ein formularzentrierter AEM Forms-Workflow unter OSGi führt den AEM-Posteingang und die Benutzeroberfläche zur Erstellung von AEM-Workflow-Modellen auf den Autoreninstanzen von AEM Forms aus.

## Systemanforderungen {#system-requirements}

>[!NOTE]
>
>Springen Sie zum Abschnitt [Weitere Schritte](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) des Dokuments, wenn Sie AEM Forms unter OSGi bereits so installiert haben, wie im Artikel [Installieren und Konfigurieren von Datenerfassungsfunktionen](../../forms/using/installing-configuring-aem-forms-osgi.md) beschrieben.

Bevor Sie mit der Installation und Konfiguration eines formularzentrierten Workflows unter OSGi beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM Instanz (Autor oder Verarbeitung), um einen formularzentrierten Workflow unter OSGi auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Verarbeitung:** Eine Verarbeitungsinstanz ist eine [extrasichere Instanz von AEM Autor](/help/forms/using/hardening-securing-aem-forms-environment.md). Nach der Installation können Sie eine Autoreninstanz festlegen und absichern. 

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

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält einen formularzentrierten Workflow unter OSGi und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „[AEM-Installationsverzeichnis]/crx-quickstart/logs/error.log“ angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen. 

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

### Obligatorisch Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die Datei „[AEM-Installationsverzeichnis]\crx-quickstart\conf\sling.properties“ zur Bearbeitung.

   Wenn Sie AEM mit „[AEM-Installationsverzeichnis]\crx-quickstart\bin\start.bat“ gestartet haben, bearbeiten Sie die Datei „sling.properties“ unter [AEM_root]\crx-quickstart\.

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

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher ist ein Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Durch Anwendung von AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. Die Standard-URL von Configuration Manager lautet https://&#39;server&#39;:[port_number]/system/console/configMgr. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist `https://'[server]:[port]'`.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://'[server]:[port]'/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten. Geben Sie im Feld **Anzahl adaptiver Formulare** des Dialogfelds „Konfigurationswerte bearbeiten“ die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers zwischenspeichern kann. Der Standardwert ist 100. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Adobe Sign konfigurieren {#configure-adobe-sign}

Adobe Sign aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit Adobe Sign und einem formularzentrierten Workflow unter OSGi füllt ein Benutzer ein adaptives Formular aus, um **einen Service zu beantragen**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt, übermittelt und signiert, wird ein Genehmigungs-/Zurückweisungs-Workflow gestartet. Der Dienstleister prüft den Antrag im AEM Posteingang und verwendet Adobe Sign, um den Antrag elektronisch zu signieren. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, [integrieren Sie Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung der Funktionen eines formularzentrierten Workflows unter OSGi konfiguriert. Die nächsten Schritte zur Verwendung der Funktionen, sind Folgende:

* [Verwenden eines formularzentrierten Workflows unter OSGi](../../forms/using/aem-forms-workflow.md)
* [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md)
* [Nachbearbeitung von Briefen und interaktiver Kommunikation](../../forms/using/submit-letter-topostprocess.md)
