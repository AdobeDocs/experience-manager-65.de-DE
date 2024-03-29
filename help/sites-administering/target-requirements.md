---
title: Voraussetzungen für das Integrieren mit Adobe Target
description: Erfahren Sie mehr über die Voraussetzungen für die Integration mit Adobe Target.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 30813c44-51ac-4e6e-8ee6-4e8baacb1ff9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 56%

---

# Voraussetzungen für das Integrieren mit Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als Teil der [Integration von AEM und Adobe Target](/help/sites-administering/target.md) müssen Sie sich bei Adobe Target registrieren, den Replikationsagenten konfigurieren und Aktivitätseinstellungen auf dem Veröffentlichungsknoten sichern.

## Registrieren bei Adobe Target {#registering-with-adobe-target}

Zur Integration von AEM in Adobe Target benötigen Sie ein gültiges Adobe Target-Konto. Dieses Konto muss mindestens über die Berechtigungsstufe einer **Genehmigenden Person** verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Sie benötigen den Clientcode sowie Ihren Adobe Target-Anmeldenamen und Ihr Kennwort, um eine Verbindung AEM Adobe Target herzustellen.

Der Clientcode identifiziert das Adobe Target-Kundenkonto beim Aufrufen des Adobe Target-Servers.

>[!NOTE]
>
>Ihr Konto muss auch vom Target-Team aktiviert werden, um die Integration verwenden zu können.
>
>Ist dies nicht der Fall, kontaktieren Sie [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html?lang=de).

## Aktivieren des Target-Replikationsagenten {#enabling-the-target-replication-agent}

Auf der Autoreninstanz muss der Test-and-Target-[Replikationsagent](/help/sites-deploying/replication.md) aktiviert werden. Dieser Replikationsagent ist standardmäßig deaktiviert, wenn Sie bei der Installation von AEM den Ausführungsmodus [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) verwendet haben. Weitere Informationen zum Schützen der Produktionsumgebung finden Sie im Abschnitt [Sicherheitscheckliste](/help/sites-administering/security-checklist.md).

1. Klicken Sie auf der AEM Homepage auf **Instrumente** > **Implementierung** > **Replikation**.
1. Klicks **Agenten für Autor**.
1. Klicken Sie auf **Test und Target (Test und Ziel)** Replikationsagent und klicken Sie dann auf **Bearbeiten**.
1. Wählen Sie die Option Aktiviert aus und klicken Sie auf **OK**.

   >[!NOTE]
   >
   >Bei der Konfiguration des Test &amp; Target-Replikationsagenten wird auf der Registerkarte **Transport** für den URI standardmäßig **tnt:///** festgelegt. Ersetzen Sie den URI nicht durch **https://admin.testandtarget.omniture.com**.
   >
   >Wenn Sie versuchen, die Verbindung mit **tnt:///**, gibt ein Fehler aus. Dieses Verhalten wird erwartet, da dieser URI nur für die interne Verwendung vorgesehen ist. Verwenden Sie nicht mit **Verbindung testen**.

## Sichern des Aktivitätseinstellungsknotens {#securing-the-activity-settings-node}

Sie müssen den Aktivitätseinstellungsknoten **cq:ActivitySettings** auf der Publishing-Instanz sichern, sodass dieser für normale Benutzende nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Service zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.

Die **cq:ActivitySettings** -Knoten ist in CRXDE Lite verfügbar unter `/content/campaigns/*nameofbrand*`* *unter dem Aktivitätsknoten jcr:content ;* *Beispiel: `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dieser Knoten wird nur erstellt, wenn Sie eine Komponente als Ziel angeben.

Der Knoten **cq:ActivitySettings** unter dem Aktivitätsknoten jcr:content wird von folgenden ACLs geschützt:

* Alle für alle verweigern
* Zulassen von jcr:read,rep:write für &quot;target-activity-authors&quot;(der Autor ist standardmäßig Mitglied dieser Gruppe)
* Allow jcr:read,rep:write für &quot;targetservice&quot;

Diese Einstellungen stellen sicher, dass normale Benutzer keinen Zugriff auf die Knoteneigenschaften haben. Verwenden Sie dieselben ACLs für Autor und Veröffentlichung. Weitere Informationen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

## Konfigurieren des AEM-Link-Externalizer {#configuring-the-aem-link-externalizer}

Beim Bearbeiten einer Aktivität in Adobe Target verweist die URL auf **localhost**, außer Sie ändern die URL auf dem AEM-Autorenknoten. Sie können den AEM-Link-Externalizer konfigurieren, wenn der exportierte Inhalt auf eine bestimmte *Veröffentlichungs*-Domain verweisen soll.

>[!NOTE]
>
>Siehe auch [Hinzufügen der Cloud-Konfiguration](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

Konfigurieren Sie den AEM-Externalizer wie folgt:

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Externalisieren von URLs](/help/sites-developing/externalizer.md).

1. Navigieren Sie zur OSGi-Web-Konsole unter **https://&lt;server>:&lt;port>/system/console/configMgr**.
1. Suchen Sie nach **Day CQ Link Externalizer** und geben Sie die Domain des Autorenknotens an.

   ![Day CQ Link Externalizer ](assets/aem-externalizer-01.png)
