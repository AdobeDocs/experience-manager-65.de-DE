---
title: Installieren und Konfigurieren eines formularzentrierten Workflows unter OSGi
description: Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen.
topic-tags: installing
docset: aem65
role: Admin, User, Developer
exl-id: 4b24a38a-c1f0-4c81-bb3a-39ce2c4892b1
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1624'
ht-degree: 100%

---

# Installieren und Konfigurieren eines formularzentrierten Workflows unter OSGi{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Einführung {#introduction}

Unternehmen erfassen und verarbeiten Daten aus mehreren Formularen, Back-End-Systemen und anderen Datenquellen. Zur Datenverarbeitung gehören Überprüfungs- und Validierungsverfahren, sich wiederholende Aufgaben und die Datenarchivierung. Zum Beispiel wird ein Formular überprüft und in ein PDF-Dokument konvertiert. Wenn die sich wiederholenden Aufgaben manuell durchgeführt werden, kann dies viel Zeit und zahlreiche Ressourcen in Anspruch nehmen.

Sie können [formularzentrierte Workflows unter OSGi](../../forms/using/aem-forms-workflow.md) verwenden, um schnell adaptive formularbasierte Workflows zu erstellen. Diese Workflows können Ihnen dabei helfen, Prüfungs- und Genehmigungs-Workflows, Geschäftsprozess-Workflows und andere sich wiederholende Aufgaben zu automatisieren. Diese Workflows helfen auch bei der Verarbeitung von Dokumenten (Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen, um den Zugriff auf-Dokumente zu beschränken, Decodieren von Barcode-Formularen und mehr) sowie bei der Verwendung des Signatur-Workflows von Adobe Sign mit Formularen und Dokumenten.

Wenn diese Workflows einmal eingerichtet sind, können sie manuell ausgelöst werden, um einen definierten Prozess abzuschließen, oder sie können programmgesteuert ausgeführt werden, wenn Benutzer ein Formular oder eine interaktive Kommunikation übermitteln. Die Funktion ist im AEM Forms Add-On-Paket enthalten.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse. Formularzentrierte Workflows unter OSGi sind nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](introduction-aem-forms.md).

>[!NOTE]
>
>Mit formularzentrierten Workflows in OSGi können Sie schnell Workflows für verschiedene Aufgaben auf dem OSGi-Stapel erstellen und bereitstellen, ohne die komplette Prozessverwaltungsfunktion auf dem JEE-Stapel zu installieren. In diesem [Vergleich](capabilities-osgi-jee-workflows.md) der formularbasierten AEM-Workflows unter OSGi mit dem Process Management auf JEE erfahren Sie mehr über die Unterschiede und Gemeinsamkeiten der Funktionen.
>
>Wenn Sie sich nach dem Vergleich für die Installation der Process Management-Funktionen auf dem JEE-Stapel entscheiden, finden Sie unter [Installieren oder Aktualisieren von AEM Forms auf JEE](/help/forms/using/introduction-aem-forms.md) detaillierte Informationen zum Installieren und Konfigurieren des JEE-Stapels und der Process Management-Funktionen.

## Bereitstellungstopologie {#deployment-topology}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen minimal nur eine AEM-Autoren- oder -Verarbeitungsinstanz (Produktionsautor), um die Funktionalität des formularzentrierten Workflows unter OSGi auszuführen. Eine Verarbeitungsinstanz ist eine [extrasichere AEM-Autoreninstanz](/help/forms/using/hardening-securing-aem-forms-environment.md). Führen Sie auf dem Produktionsautor kein tatsächliches Authoring durch, wie das Erstellen von Workflows oder adaptiven Formularen.

Die folgende Topologie ist eine indikative Topologie für die Nutzung der interaktiven Kommunikation in AEM Forms, Correspondence Management, AEM Forms-Datenerfassung und formularzentrierten Workflows für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommended-topology](assets/recommended-topology.png)

Ein formularzentrierter AEM Forms-Workflow unter OSGi führt den AEM-Posteingang und die Benutzeroberfläche zur Erstellung von AEM-Workflow-Modellen auf den Autoreninstanzen von AEM Forms aus.

## Systemanforderungen {#system-requirements}

>[!NOTE]
>
>Springen Sie zum Abschnitt [Weitere Schritte](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) des Dokuments, wenn Sie AEM Forms unter OSGi bereits so installiert haben, wie im Artikel [Installieren und Konfigurieren von Datenerfassungsfunktionen](../../forms/using/installing-configuring-aem-forms-osgi.md) beschrieben.

Bevor Sie mit der Installation und Konfiguration eines formularzentrierten Workflows unter OSGi beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM Instanz läuft. In der AEM-Terminologie bezeichnet eine „Instanz“ eine Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM Instanz (Autor oder Verarbeitung), um einen formularzentrierten Workflow unter OSGi auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Verarbeitung:** Eine Verarbeitungsinstanz ist eine [extrasichere AEM-Authoring-Instanz](/help/forms/using/hardening-securing-aem-forms-environment.md). Nach der Installation können Sie eine Autoreninstanz festlegen und absichern.

   * **Veröffentlichung**: Eine AEM-Instanz, die die veröffentlichten Inhalte über das Internet oder ein internes Netzwerk öffentlich zugänglich macht.

* Es gibt gewisse Arbeitsspeicheranforderungen. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
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

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält einen formularzentrierten Workflow unter OSGi und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „[AEM-Installationsverzeichnis]/crx-quickstart/logs/error.log“ angezeigt werden und das Protokoll stabil ist.

   >[!NOTE]
   >
   > Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen.

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

Einige der Konfigurationen von AEM Forms sind obligatorisch und andere optional. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

### Obligatorische Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

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

Dispatcher ist ein Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Mit AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“ zum Bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie ihm den folgenden Filter hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Detaillierte Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. So konfigurieren Sie den Referrer-Filterdienst:

   Melden Sie sich beim Apache Felix Configuration Manager als Admin an. Die Standard-URL von Configuration Manager lautet https://&#39;server&#39;:[port_number]/system/console/configMgr. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist `https://'[server]:[port]'`.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Mechanismus zur Verkürzung von Datenzugriffszeiten, zur Verringerung von Latenzzeiten und zur Verbesserung der Ein-/Ausgabegeschwindigkeit (I/O). Der Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Er trägt dazu bei, die für die Darstellung eines adaptiven Formulars erforderliche Zeit zu verkürzen.

* Wenn Sie den Cache für adaptive Formulare verwenden, verwenden Sie den [AEM Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars zwischenzuspeichern.
* Halten Sie beim Entwickeln benutzerdefinierter Komponenten den Cache für adaptive Formulare auf dem für die Entwicklung verwendeten Server deaktiviert.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://'[server]:[port]'/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten. Geben Sie im Dialogfeld „Konfigurationswerte bearbeiten“ die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **Anzahl adaptiver Formulare** zwischenspeichern kann. Der Standardwert ist 100. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert im Feld „Anzahl adaptiver Formulare“ auf **0** fest. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Konfigurieren von Adobe Sign {#configure-adobe-sign}

Adobe Sign ermöglicht Workflows für die elektronische Signatur für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit Adobe Sign und einem formularzentrierten Workflow unter OSGi füllt ein Benutzer ein adaptives Formular aus, um **einen Service zu beantragen**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt, übermittelt und signiert, wird ein Genehmigungs-/Zurückweisungs-Workflow gestartet. Der Dienstleister prüft den Antrag im AEM Posteingang und verwendet Adobe Sign, um den Antrag elektronisch zu signieren. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, [integrieren Sie Adobe Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung der Funktionen eines formularzentrierten Workflows unter OSGi konfiguriert. Die nächsten Schritte zur Verwendung der Funktionen, sind Folgende:

* [Verwenden eines formularzentrierten Workflows unter OSGi](../../forms/using/aem-forms-workflow.md)
* [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md)
* [Nachbearbeitung von Briefen und interaktiver Kommunikation](../../forms/using/submit-letter-topostprocess.md)
