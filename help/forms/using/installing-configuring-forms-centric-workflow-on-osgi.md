---
title: Installieren und Konfigurieren des Forms-zentrierten Workflows auf OSGi
seo-title: Installieren und Konfigurieren des Forms-zentrierten Workflows auf OSGi
description: Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen.
seo-description: Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen.
uuid: 1ceae822-215a-4b83-a562-4609a09c3a54
topic-tags: installing
discoiquuid: de292a19-07db-4ed3-b13a-7a2f1cd9e0dd
docset: aem65
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1643'
ht-degree: 58%

---


# Installieren und Konfigurieren des Forms-zentrierten Workflows auf OSGi{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Einführung {#introduction}

Unternehmen erfassen und verarbeiten Daten aus mehreren Formularen, Back-End-Systemen und anderen Datenquellen. Die Datenverarbeitung umfasst Überprüfungs- und Genehmigungsverfahren, sich wiederholende Aufgaben und die Datenarchivierung. Betrachten Sie beispielsweise ein Formular und konvertieren Sie es in ein PDF-Dokument. Bei manueller Ausführung können sich die sich wiederholenden Aufgaben sehr viel Zeit und Ressourcen kosten.

Sie können den [Forms-orientierten Arbeitsablauf unter OSGi](../../forms/using/aem-forms-workflow.md) verwenden, um schnell adaptive formularbasierte Workflows zu erstellen. Diese Workflows unterstützen Sie bei der Automatisierung von Review- und Genehmigungs-Workflows, Workflows und anderen wiederholten Aufgaben. Diese Workflows helfen auch bei der Verarbeitung von Dokumenten (Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Unterschriften zur Beschränkung des Zugriffs auf Dokumente, Dekodieren von mit Strichcode versehenen Formularen usw.) und bei der Verwendung des Adobe Sign-Unterschriftsarbeitsablaufs mit Formularen und Dokumenten.

Nach der Einrichtung können diese Workflows manuell ausgelöst werden, um einen definierten Prozess abzuschließen oder programmgesteuert auszuführen, wenn Benutzer ein Formular oder eine interaktive Kommunikation senden. Die Funktion ist im AEM Forms Add-On-Paket enthalten.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse. Forms-zentrierter Arbeitsablauf auf OSGi ist nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](introduction-aem-forms.md).

>[!NOTE]
>
>Mit formularzentrierten Workflows in OSGi können Sie schnell Workflows für verschiedene Aufgaben auf dem OSGi-Stapel erstellen und bereitstellen, ohne die komplette Prozessverwaltungsfunktion auf dem JEE-Stapel zu installieren. Informationen zu den Unterschieden und Ähnlichkeiten in den Funktionen finden Sie in einem [Vergleich](capabilities-osgi-jee-workflows.md) der Forms-zentrierten AEM auf OSGi und Process Management on JEE.
>
>Nach dem Vergleich finden Sie unter [Installieren oder Aktualisieren von AEM Forms on JEE](/help/forms/home.md) ausführliche Informationen zum Installieren und Konfigurieren des JEE-Stapels und zu den Process Management-Funktionen, wenn Sie sich dafür entscheiden, die Process Management-Funktion auf dem JEE-Stapel zu installieren.

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur mindestens eine AEM Author- oder Verarbeitungsinstanz (Produktionsautor), um den Forms-zentrierten Workflow mit OSGi-Funktionen auszuführen. Eine Verarbeitungsinstanz ist eine [harrierte AEM-Autoreninstanz](/help/forms/using/hardening-securing-aem-forms-environment.md). Führen Sie kein tatsächliches Authoring wie das Erstellen von Workflows oder adaptiven Formularen im Produktionsautor durch.

Die folgende Topologie ist eine indikative Topologie zum Ausführen von AEM Forms Interactive Communications, Correspondence Management, AEM Forms-Datenerfassung und Forms-Centric-Workflow für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommendations-topology](assets/recommended-topology.png)

AEM Forms Forms-zentrierter Arbeitsablauf auf OSGi wird AEM Benutzeroberfläche für die Erstellung des Inbox- und AEM Workflow-Modells auf den Autoreninstanzen von AEM Forms ausgeführt.

## Systemanforderungen {#system-requirements}

>[!NOTE]
>
>Gehen Sie zum Abschnitt [Nächste Schritte](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) des Dokuments, wenn Sie AEM Forms bereits auf OSGi installiert haben, wie im Artikel [Möglichkeiten zur Installation und Konfiguration der Datenerfassung](../../forms/using/installing-configuring-aem-forms-osgi.md) beschrieben.

Bevor Sie mit der Installation und Konfiguration des Forms-zentrierten Workflows auf OSGi beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM Instanz (Autor oder Verarbeitung), um einen Forms-zentrierten Workflow unter OSGi auszuführen:

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

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält einen Forms-zentrierten Arbeitsablauf für OSGi und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können die Ergebnisse auch mit der Option **[!UICONTROL Downloads suchen]** filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie **[!UICONTROL EULA-Begriffe akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms Releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Bevor Sie den AEM Forms-Server beenden, warten Sie, bis die Meldungen &quot;ServiceEvent REGISTERED&quot;und &quot;ServiceEvent UNREGISTERED&quot;nicht mehr in der Datei &quot; [AEM-Installation-Directory]/crx-quickstart/logs/error.log&quot;angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen.  

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

### Obligatorisch Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die Datei [AEM Installationsordner]\crx-quickstart\conf\sling.properties zur Bearbeitung.

   Wenn Sie [AEM Installationsordner]\crx-quickstart\bin\start.bat zum Beginn AEM, bearbeiten Sie die Datei &quot;sling.properties&quot;unter [AEM_root]\crx-quickstart\.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritten 1-4 für alle Autor- und Veröffentlichungsinstanzen.  

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie die folgenden Schritte für alle Instanzen im Autoren- und Veröffentlichungsmodus aus, um das Paket der Zulassungsliste &quot;&quot;hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. Die Standard-URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Suchen und öffnen Sie die **Deserialisierungs-Firewallkonfiguration**.
1. hinzufügen Sie das Paket **sun.util.calendar** in das Feld **Zulassungsliste**. Klicken Sie auf Speichern.
1. Wiederholen Sie Schritten 1-3 für alle Autor- und Veröffentlichungsinstanzen.  

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher·ist ein·Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Durch Anwendung von AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. Die Standard-URL des Configuration Managers lautet https://&#39;server&#39;:[port_number]/system/console/configMgr. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist `https://'[server]:[port]'`.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Gehen Sie zu AEM Web Console Configuration Manager unter `https://'[server]:[port]'/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiver Kommunikationswebkanal]**, um die Konfigurationswerte zu bearbeiten. Geben Sie im Dialogfeld &quot;Konfigurationswerte bearbeiten&quot;die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **Anzahl der adaptiven Forms** zwischenspeichern kann. Der Standardwert ist 100. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Adobe Sign konfigurieren {#configure-adobe-sign}

Adobe Sign aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In einem typischen Adobe Sign- und Forms-zentrierten Arbeitsablauf für OSGi füllt ein Benutzer ein adaptives Formular aus, um **einen Dienst** anzufordern. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger. Wenn ein Benutzer das Antragsformular ausfüllt, sendet und unterzeichnet, wird ein Genehmigungsvorgang gestartet. Der Dienstleister prüft den Antrag in AEM Inbox und verwendet Adobe Sign, um den Antrag elektronisch zu unterzeichnen. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, [integrieren Sie Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung des Forms-zentrierten Arbeitsablaufs auf OSGi-Funktionen konfiguriert. Die folgenden Schritte zur Nutzung der Funktion sind nun die folgenden:

* [Forms-zentrierter Workflow unter OSGi](../../forms/using/aem-forms-workflow.md)
* [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md)
* [Nachbearbeitung von Briefen und interaktiver Kommunikation](../../forms/using/submit-letter-topostprocess.md)

