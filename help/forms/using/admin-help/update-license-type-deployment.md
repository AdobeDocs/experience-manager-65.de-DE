---
title: Lizenztyp für die Bereitstellung aktualisieren
seo-title: Lizenztyp für die Bereitstellung aktualisieren
description: Aktualisieren Sie den Lizenztyp für die Bereitstellung, indem Sie die Seite „Lizenz ändern“ in der Administration Console verwenden.
seo-description: Aktualisieren Sie den Lizenztyp für die Bereitstellung, indem Sie die Seite „Lizenz ändern“ in der Administration Console verwenden.
uuid: 0152635e-2c00-4944-b9b6-64b368589a91
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e4f31377-ccc9-4986-a3bf-ef2e83d12448
exl-id: 6b975aa1-9270-4098-9af5-c5cc67cb7b5d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# Lizenztyp für die Bereitstellung aktualisieren {#update-the-license-type-for-the-deployment}

Als Teil des Installationsprozesses von AEM Forms haben Sie mithilfe von Configuration Manager die erforderlichen AEM Forms-Module konfiguriert und bereitgestellt. Diese Module sind standardmäßig mit einer Testlizenz für 60 Tage konfiguriert. Verwenden Sie die Seite „Lizenz ändern“ in Administration Console, um den Lizenztyp für die Bereitstellung zu ändern. Die zurzeit bereitgestellten Module werden auf der Seite „Lizenz ändern“ angezeigt.

Auf der Seite „Lizenz ändern“ werden Informationen über Ihre Lizenz angezeigt:

* Der aktuelle Lizenztyp;
* Datum und Uhrzeit der letzten Aktualisierung der Lizenz;
* Benutzer, der die letzte Aktualisierung ausgeführt hat;
* Der aktuelle Status der Lizenz;
* Das Datum, an dem AEM Forms installiert wurde;
* Das Ablaufdatum der aktuellen Lizenz.

>[!NOTE]
>
>Die Änderung der Lizenz wird auf alle bereitgestellten Module angewendet. Bevor Sie den Lizenztyp ändern, heben Sie die Bereitstellung aller nicht lizenzierten Module auf. Wählen Sie nicht den Lizenztyp „Produktion“ aus, wenn die Liste bereitgestellter Module andere Module enthält als die, die Sie von Adobe erworben haben.

## Aktualisieren des Lizenztyps {#update-the-license-type}

1. Klicken Sie in Administration Console auf „Lizenzieren“.
1. Lesen Sie den AEM Forms-Endbenutzerlizenzvertrag, wählen Sie, wenn Sie zustimmen, „Ich akzeptiere die Bedingungen der Lizenzvereinbarung“ und klicken Sie auf „Weiter“.
1. Wählen Sie auf der Seite „Lizenz ändern“ einen Lizenztyp aus:

   * **EVAL:** Testlizenz für 60 Tage
   * **DEV:** Permanente Entwicklungslizenz
   * **NFR:** 2-Jahres-Testlizenz
   * **IDEV:** 1-Jahres-Abonnement für das Adobe Developer Program
   * **Production:** Permanente Lizenz

1. Wählen Sie die Option „Ja, Lizenzänderung ist für alle bereitgestellten Module gültig“ aus.
1. Klicken Sie auf „Lizenzänderung bestätigen“. In einer Meldung wird angezeigt, dass die Lizenz erfolgreich aktualisiert wurde.
