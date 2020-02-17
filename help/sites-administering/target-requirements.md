---
title: Voraussetzungen für die Integration mit Adobe Target
seo-title: Voraussetzungen für die Integration mit Adobe Target
description: Hier finden Sie alle Informationen über die Voraussetzungen für die Integration mit Adobe Target.
seo-description: Hier finden Sie alle Informationen über die Voraussetzungen für die Integration mit Adobe Target.
uuid: 55d87a96-5fe7-4f7e-93c1-fdf7fbb7c971
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: ae4a6e97-c0d7-472d-a25f-b89b1abf4df3
docset: aem65
translation-type: tm+mt
source-git-commit: 4b965d8f7814816126601f6366c1ba313e404538

---


# Voraussetzungen für die Integration mit Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als Teil der [Integration von AEM und Adobe Target](/help/sites-administering/target.md) müssen Sie sich bei Adobe Target registrieren, den Replikationsagenten konfigurieren und Aktivitätseinstellungen auf dem Veröffentlichungsknoten sichern.

## Registrieren bei Adobe Target {#registering-with-adobe-target}

Zur Integration von AEM mit Adobe Target müssen Sie über ein gültiges Adobe Target-Konto verfügen. This account must have **approver** level permissions at a minimum. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Dieser Clientcode und Ihre Adobe Target-Anmeldedaten sind erforderlich, um eine Verbindung zwischen AEM und Adobe Target herzustellen.

Der Clientcode identifiziert beim Aufrufen des Adobe Target-Servers das Adobe Target-Kundenkonto.

>[!NOTE]
>
>Ihr Konto muss auch vom Target-Team aktiviert werden, damit die Integration genutzt werden kann.
>
>
>If it is not the case, please contact [Adobe Target Customer Care](https://marketing.adobe.com/resources/help/en_US/target/target/r_problem.html).

## Aktivieren des Target-Replikationsagenten {#enabling-the-target-replication-agent}

The Test and Target [replication agent](/help/sites-deploying/replication.md) must be enabled on the author instance. Note that this replication agent is not enabled by default if you used the [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) run mode for installing AEM. Weitere Informationen zum Speichern Ihrer Produktionsumgebung finden Sie in der [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).

1. Klicken oder tippen Sie auf der AEM-Homepage auf **Tools** > **Bereitstellung** > **Replikation**.
1. Klicken oder tippen Sie auf **Agenten für Autor**.
1. Klicken oder tippen Sie auf den **Test &amp; Target**-Replikationsagenten und dann auf **Bearbeiten**.
1. Wählen Sie die Option „Aktiviert“ aus und klicken oder tippen Sie auf **OK**.

   >[!NOTE]
   >
   >Bei der Konfiguration des Test &amp; Target-Replikationsagenten wird auf der Registerkarte **Transport** für den URI standardmäßig **tnt:///** festgelegt. Do not replace this URI with **https://admin.testandtarget.omniture.com**.
   >
   >Beim Testen der Verbindung mit **tnt:///** wird ein Fehler ausgegeben. This is expected behavior as this URI is for internal use only and should not be used with **Test Connection**.

## Sichern des Aktivitätseinstellungsknotens {#securing-the-activity-settings-node}

Sie müssen den Aktivitätseinstellungsknoten **cq:ActivitySettings** auf der Veröffentlichungsinstanz sichern, sodass dieser für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Dienst zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.

**Der Knoten** cq:ActivitySettings`/content/campaigns/*nameofbrand*` ist in CRXDE lite unter *** unter dem Aktivitätenknoten jcr:content verfügbar. *zum Beispiel `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dieser Knoten wird nur erstellt, wenn Sie eine Komponente als Ziel angeben.

The **cq:ActivitySettings** node under the activity&#39;s jcr:content is protected by the following ACLs:

* Alles für jeden verweigern
* „jcr:read,rep:write“ für „target-activity-authors“ zulassen („author“ ist standardmäßig ein Mitglied dieser Gruppe)
* „jcr:read,rep:write“ für „targetservice“ zulassen

Diese Einstellungen gewährleisten, dass normale Benutzer keinen Zugriff auf die Knoteneigenschaften haben. Verwenden Sie dieselben ACLs für „author“ und „publish“. See [User Administration and Security](/help/sites-administering/security.md) for more information.

## Configuring the AEM Link Externalizer {#configuring-the-aem-link-externalizer}

Beim Bearbeiten einer Aktivität in Adobe Target verweist die URL auf **localhost**, außer Sie ändern die URL auf dem AEM-Autorenknoten. Sie können den AEM Link Externalizer konfigurieren, wenn der exportierte Inhalt auf eine bestimmte *Veröffentlichungsdomäne* verweisen soll.

>[!NOTE]
>
>Siehe auch Cloud-Konfiguration [hinzufügen](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

Konfigurieren Sie den AEM-Externalizer wie folgt:

>[!NOTE]
>
>For more details see [Externalizing URLs](/help/sites-developing/externalizer.md).

1. Navigate to the OSGi web console at **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Suchen Sie nach **Day CQ Link Externalizer** und geben Sie die Domäne des Autorenknotens an.

   ![chlimage_1-120](assets/aem-externalizer-01.png)

