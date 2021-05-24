---
title: Integrieren mit Adobe Campaign Standard
seo-title: Integrieren mit Adobe Campaign Standard
description: Integrieren mit Adobe Campaign Standard
seo-description: Integrieren mit Adobe Campaign Standard.
uuid: ef31339e-d925-499c-b8fb-c00ad01e38ad
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 5c0fec99-7b1e-45d6-a115-e498d288e9e1
exl-id: caa43d80-1f38-46fc-a8b9-9485c235c0ca
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 69%

---

# Integrieren mit Adobe Campaign Standard{#integrating-with-adobe-campaign-standard}

>[!NOTE]
>
>In dieser Dokumentation wird beschrieben, wie Sie AEM mit Adobe Campaign Standard, der abonnementbasierten Lösung, integrieren. Wenn Sie Adobe Campaign 6.1 verwenden, finden Sie die entsprechenden Anweisungen in [Integrieren mit Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md).

Adobe Campaign ermöglicht die Verwaltung von Inhalten und Formularen für die Übermittlung per E-Mail direkt in Adobe Experience Manager.

Damit Sie beide Lösungen gleichzeitig verwenden können, müssen Sie sie zunächst miteinander verknüpfen. Dies umfasst Konfigurationsschritte in Adobe Campaign und Adobe Experience Manager. Diese Schritte werden in diesem Dokument detailliert beschrieben.

Die Arbeit mit Adobe Campaign in AEM bietet die Möglichkeit, über Adobe Campaign E-Mails und Formulare zu versenden. Dies wird beschrieben in [Arbeiten mit Adobe Campaign](/help/sites-authoring/campaign.md).

Des Weiteren sind unter Umständen die folgenden Themen relevant, wenn Sie AEM mit [Adobe Campaign](https://docs.campaign.adobe.com/doc/standard/de/home.html) integrieren:

* [Best Practices für E-Mail-Vorlagen](/help/sites-administering/best-practices-for-email-templates.md)
* [Fehlerbehebung bei der Adobe Campaign-Integration](/help/sites-administering/troubleshooting-campaignintegration.md)

Hinsichtlich der Erweiterung einer Adobe Campaign-Integration sind folgende Seiten empfehlenswert:

* [Erstellen benutzerspezifischer Erweiterungen](/help/sites-developing/extending-campaign-extensions.md)
* [Erstellen benutzerdefinierter Formularzuordnungen](/help/sites-developing/extending-campaign-form-mapping.md)

## Konfigurieren von Adobe Campaign {#configuring-adobe-campaign}

Die Konfiguration von Adobe Campaign umfasst Folgendes:

1. Konfiguration des Benutzers **aemserver**
1. Erstellung eines dedizierten externen Kontos
1. Überprüfung der Option „AEMResourceTypeFilter“
1. Erstellung einer dedizierten Bereitstellungsvorlage

>[!NOTE]
>
>Um diese Vorgänge auszuführen, müssen Sie in Adobe Campaign über die Rolle **administration** verfügen.

### Voraussetzungen {#prerequisites}

Stellen Sie im Voraus sicher, dass Sie über die folgenden Elemente verfügen:

* [Eine AEM-Autoreninstanz](/help/sites-deploying/deploy.md#getting-started)
* [Eine AEM-Veröffentlichungsinstanz](/help/sites-deploying/deploy.md#author-and-publish-installs)
* [Eine Adobe Campaign-Instanz](https://docs.adobe.com/content/docs/de/campaign/ACS.html)

>[!CAUTION]
>
>Vorgänge, die im Abschnitt [Konfigurieren von Adobe Campaign](#configuring-adobe-campaign) und [Konfigurieren von Adobe Experience Manager](#configuring-adobe-experience-manager) beschrieben werden, sind erforderlich, damit die Integrationsfunktionen zwischen AEM und Adobe Campaign ordnungsgemäß funktionieren.

### Konfigurieren des Benutzers „aemserver“{#configuring-the-aemserver-user}

Der Benutzer **aemserver** muss in Adobe Campaign konfiguriert werden. **aemserver** ist ein technischer Benutzer, der verwendet wird, um den AEM-Server mit Adobe Campaign zu verbinden.

Gehen Sie zu **Administration** > **Benutzer &amp; Sicherheit** > **Benutzer** und wählen Sie den Benutzer **aemserver** aus. Klicken Sie darauf, um die Benutzereinstellungen zu öffnen.

* Sie müssen für diesen Benutzer ein Kennwort festlegen. Dies kann nicht über die Benutzeroberfläche erledigt werden. Diese Konfiguration muss von einem technischen Administrator in REST erledigt werden.
* Sie können diesem Benutzer bestimmte Rollen zuweisen, z. B. **deliveryPrepare**, mit denen der Benutzer Sendungen erstellen und bearbeiten kann.

### Konfigurieren eines externen Adobe Experience Manager-Kontos {#configuring-an-adobe-experience-manager-external-account}

Sie müssen ein externes Konto konfigurieren, das es Ihnen ermöglicht, Adobe Campaign mit Ihrer AEM-Instanz zu verknüpfen.

>[!NOTE]
>
>Stellen Sie in AEM sicher, dass Sie das Kennwort für den Benutzer „campaign-remote“ festlegen. Sie müssen dieses Kennwort festlegen, um Adobe Campaign mit AEM zu verknüpfen. Melden Sie sich als Administrator an und wählen Sie an der Benutzeradministrationskonsole den Benutzer „campaign-remote“. Klicken Sie dann auf **Kennwort festlegen**.

Konfigurieren Sie ein externes AEM-Konto wie folgt:

1. Gehen Sie zu **Administration** > **Anwendungskonfiguration** > **Externe Konten**.

   ![chlimage_1-124](assets/chlimage_1-124a.png)

1. Wählen Sie das standardmäßige externe Konto **aemInstance** aus oder erstellen Sie ein neues Konto, indem Sie auf die Schaltfläche **Erstellen** klicken.
1. Wählen Sie **Adobe Experience Manager** i im Feld **Typ** aus und geben Sie die Zugriffsparameter ein, die für Ihre AEM Authoring-Instanz verwendet werden: Server-Adresse, Kontoname und Kennwort.

   >[!NOTE]
   >
   >Hängen Sie an die URL keinen abschließenden Schrägstrich **/** an, sonst funktioniert die Verknüpfung nicht.

1. Vergewissern Sie sich, dass das Kontrollkästchen **Aktiviert** aktiviert ist, und klicken Sie dann auf **Speichern**, um Ihre Änderungen zu speichern.

### Überprüfen der Option „AEMResourceTypeFilter“{#verifying-the-aemresourcetypefilter-option}

Die Option **AEMResourceTypeFilter** wird verwendet, um AEM Ressourcentypen zu filtern, die in Adobe Campaign verwendet werden können. Dies ermöglicht Adobe Campaign das Abrufen von AEM-Inhalten, die speziell für die ausschließliche Verwendung in Adobe Campaign entwickelt wurden.

Diese Option ist vorkonfiguriert. Falls Sie an dieser Option Änderungen vornehmen, funktioniert die Integration unter Umständen nicht.

Überprüfen Sie wie folgt, ob die Option **AEMResourceTypeFilter** konfiguriert ist:

1. Wechseln Sie zu **Administration** > **Anwendungseinstellungen** > **Optionen**.
1. In der Liste können Sie sicherstellen, dass die Option **AEMResourceTypeFilter** aufgeführt ist und dass die Pfade korrekt sind.

### Erstellen einer AEM-spezifischen E-Mail-Bereitstellungsvorlage {#creating-an-aem-specific-email-delivery-template}

Die AEM-Funktion ist in den E-Mail-Vorlagen von Adobe Campaign standardmäßig deaktiviert. Sie haben die Möglichkeit, eine neue E-Mail-Bereitstellungsvorlage für die Erstellung von E-Mails mit AEM-Inhalten zu konfigurieren.

Erstellen Sie AEM-spezifische E-Mail-Bereitstellungsvorlagen wie folgt:

1. Wechseln Sie zu **Ressourcen** > **Vorlagen** > **Bereitstellungsvorlagen**.
1. **Aktivieren Sie** die Auswahl, indem Sie in der Aktionsleiste auf das Häkchen klicken und die vorhandene  **Standard-E-Mail-** Standardvorlage auswählen. Duplizieren Sie sie dann, indem Sie auf das  **** Kopiersymbol klicken und auf  **Bestätigen** klicken.
1. Deaktivieren Sie den Auswahlmodus, indem Sie auf die Vorlage **x** klicken, die neu erstellte Vorlage **Kopie der Standard-E-Mail (mail)** öffnen und dann **Eigenschaften bearbeiten** in der Aktionsleiste des Vorlagen-Dashboards auswählen.

   Sie können die **Beschriftung** der Vorlage ändern.

1. Legen Sie im Abschnitt **Inhalt** der Eigenschaften **Adobe Experience Manager** als **Inhaltsquelle** fest. Wählen Sie dann das zuvor erstellte externe Konto aus und klicken Sie auf **Bestätigen**.

   Speichern Sie Ihre Änderungen, indem Sie auf **Bestätigen** und anschließend auf **Speichern** klicken.

   Für die aus dieser Vorlage erstellten E-Mail-Bereitstellungen ist die AEM-Inhaltsfunktion aktiviert.

   ![chlimage_1-125](assets/chlimage_1-125a.png)

## Konfigurieren von Adobe Experience Manager {#configuring-adobe-experience-manager}

Zum Konfigurieren von AEM müssen Sie folgende Schritte ausführen:

* die Replikation zwischen Instanzen konfigurieren
* AEM mit Adobe Campaign verknüpfen
* den Externalizer konfigurieren

### Konfigurieren der Replikation zwischen AEM-Instanzen  {#configuring-replication-between-aem-instances}

Inhalte, die in der AEM-Autoreninstanz erstellt werden, werden zunächst an die Veröffentlichungsinstanz übermittelt. Diese Veröffentlichungsinstanz übermittelt die Inhalte dann an Adobe Campaign. Der Replikationsagent muss deshalb so konfiguriert werden, dass er aus der AEM-Autoreninstanz in die AEM-Veröffentlichungsinstanz repliziert.

>[!NOTE]
>
>Möchten Sie nicht die Replikations-URL sondern stattdessen die öffentlich zugängliche URL verwenden, so haben Sie die Möglichkeit, die **Öffentliche URL** in der folgenden Konfigurationseinstellung in OSGi festzulegen (**Tools** > **Web-Konsole** > **OSGi-Konfiguration > AEM-Kampagnenintegration – Konfiguration**):
**Öffentliche URL:** com.day.cq.mcm.campaign.impl.IntegrationConfigImpl#aem.mcm.campaign.publicUrl

Dieser Schritt ist auch erforderlich, um bestimmte Autoreninstanzkonfigurationen in die Veröffentlichungsinstanz zu replizieren.

So konfigurieren Sie die Replikation zwischen AEM-Instanzen:

1. Wählen Sie in der Autoreninstanz **AEM Logo** **Tools** > **Bereitstellung** > **Replikation** > **Agenten für Autor** und klicken Sie dann auf **Standardagent**.

   ![chlimage_1-126](assets/chlimage_1-126a.png)

   >[!NOTE]
   Verwenden Sie nach Möglichkeit nicht localhost (eine lokale Kopie von AEM), wenn Sie die Integration mit Adobe Campaign konfigurieren, außer die Veröffentlichungs- und Autoreninstanz befinden sich auf demselben Computer.

1. Klicken Sie auf **Bearbeiten** und wählen Sie dann die Registerkarte **Transport** aus.
1. Konfigurieren Sie den URI, indem Sie **localhost** durch die IP-Adresse oder die Adresse der AEM-Veröffentlichungsinstanz ersetzen.

   ![chlimage_1-127](assets/chlimage_1-127a.png)

### Verknüpfen von AEM mit Adobe Campaign {#connecting-aem-to-adobe-campaign}

Bevor Sie AEM und Adobe Campaign zusammen verwenden können, müssen Sie die beiden Lösungen verknüpfen, damit sie miteinander kommunizieren können.

1. Stellen Sie eine Verbindung mit Ihrer AEM-Autoreninstanz her.
1. Wählen Sie **Tools** > **Vorgänge** > **Cloud** > **Cloud Services** und dann **Jetzt** im Adobe Campaign-Bereich konfigurieren.

   ![chlimage_1-128](assets/chlimage_1-128a.png)

1. Erstellen Sie eine neue Konfiguration, indem Sie einen **Titel** eingeben und auf **Erstellen** klicken oder die vorhandene Konfiguration auswählen, die Sie mit Ihrer Adobe Campaign-Instanz verknüpfen möchten.
1. Passen Sie die Konfiguration so an, dass sie den Parametern Ihrer Adobe Campaign-Instanz entspricht.

   * **Benutzername**:  **aemserver**, der Adobe Campaign AEM Integrationspaket-Benutzer, der zur Herstellung der Verbindung zwischen den beiden Lösungen verwendet wurde.
   * **Kennwort**: Das Adobe Campaign-Kennwort des aemserver-Operators. Unter Umständen müssen Sie das Kennwort für diesen Operator direkt in Adobe Campaign erneut angeben.
   * **API-Endpunkt**: URL der Adobe Campaign-Instanz.

1. Wählen Sie **Verbindung zu Adobe Campaign** und klicken Sie auf **OK**.

   ![chlimage_1-129](assets/chlimage_1-129a.png)

   >[!NOTE]
   Nachdem Sie [die E-Mail erstellt und veröffentlicht haben](/help/sites-authoring/campaign.md), müssen Sie die Konfiguration auf der Veröffentlichungsinstanz erneut veröffentlichen.

   ![chlimage_1-130](assets/chlimage_1-130a.png)

>[!NOTE]
Prüfen Sie Folgendes, falls die Verbindung nicht hergestellt werden kann:
* Möglicherweise tritt ein Zertifikatfehler auf, wenn Sie eine sichere Verbindung (https) mit einer Adobe Campaign-Instanz herstellen. Sie müssen das Adobe Campaign-Instanzzertifikat der Datei &quot;cacerts&quot;Ihres JDK hinzufügen.
* Weitere Informationen finden Sie in [Fehlerbehebung bei der AEM/Adobe Campaign-Integration](/help/sites-administering/troubleshooting-campaignintegration.md).



### Konfigurieren des Externalizers  {#configuring-the-externalizer}

Sie müssen [den Externalizer](/help/sites-developing/externalizer.md) in AEM auf der Autoreninstanz konfigurieren. Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade in externe, absolute URLs umzuwandeln. Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs.

Allgemeine Anweisungen finden Sie unter [Konfigurieren des Externalizers](/help/sites-developing/externalizer.md). Stellen Sie für die Adobe Campaign-Integration sicher, dass Sie den Veröffentlichungsserver unter `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl` nicht auf `localhost:4503`, sondern auf einen Server konfigurieren, der über die Adobe Campaign-Konsole erreichbar ist.

Wenn er auf `localhost:4503` oder einen anderen Server, den Adobe Campaign nicht erreichen kann, verweist, werden Ihre Bilder auf der Adobe Campaign-Konsole nicht angezeigt.

![chlimage_1-131](assets/chlimage_1-131a.png)
