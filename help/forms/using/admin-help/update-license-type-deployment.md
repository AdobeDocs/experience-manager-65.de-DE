---
title: Aktualisieren des Lizenztyps für die Bereitstellung
description: Aktualisieren Sie den Lizenztyp für die Bereitstellung mithilfe der Seite Lizenz ändern in Administration Console.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6b975aa1-9270-4098-9af5-c5cc67cb7b5d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 16%

---

# Aktualisieren des Lizenztyps für die Bereitstellung {#update-the-license-type-for-the-deployment}

Als Teil des Installationsprozesses von AEM Forms haben Sie mithilfe von Configuration Manager die erforderlichen AEM Forms-Module konfiguriert und bereitgestellt. Standardmäßig sind diese Module mit einer Testlizenz für 60 Tage konfiguriert. Auf der Seite &quot;Lizenz ändern&quot;in Administration Console können Sie den Lizenztyp für die Bereitstellung ändern. Die derzeit bereitgestellten Module werden auf der Seite Lizenz ändern angezeigt.

Auf der Seite Lizenz ändern werden Informationen zu Ihrer Lizenz angezeigt:

* Der aktuelle Lizenztyp
* Datum und Uhrzeit der letzten Aktualisierung der Lizenz
* Wer das letzte Update durchgeführt hat
* Der aktuelle Status der Lizenz
* Das Datum der Installation AEM Formulare
* Das Datum, an dem die aktuelle Lizenz abläuft

>[!NOTE]
>
>Die Lizenzänderung gilt für alle bereitgestellten Module. Bevor Sie den Lizenztyp ändern, heben Sie die Bereitstellung aller Module auf, die nicht lizenziert sind. Wählen Sie nicht den Lizenztyp Produktion aus, wenn die Liste der bereitgestellten Module andere Module enthält als die, die Sie von Adobe erworben haben.

## Lizenztyp aktualisieren {#update-the-license-type}

1. Klicken Sie in Administration Console auf &quot;Lizenzierung&quot;.
1. Lesen Sie die Lizenzvereinbarung für Endbenutzer in AEM Formularen, wählen Sie Ich akzeptiere , wenn Sie mit den Bedingungen der Vereinbarung einverstanden sind, und klicken Sie auf Weiter.
1. Wählen Sie auf der Seite Lizenz ändern einen Lizenztyp aus:

   * **EVAL:** Testlizenz für 60 Tage
   * **DEV:** Permanente Entwicklungslizenz
   * **NFR:** 2-Jahres-Evaluierungslizenz
   * **IDEV:** 1-Jahres-Abo für das Adobe Developer-Programm
   * **Production:** Permanente Lizenz

1. Wählen Sie Ja, Lizenzänderung ist für alle bereitgestellten Module gültig.
1. Klicken Sie auf Lizenzänderung bestätigen . Es wird eine Meldung angezeigt, die besagt, dass die Lizenz erfolgreich aktualisiert wurde.
