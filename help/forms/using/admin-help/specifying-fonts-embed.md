---
title: Angeben der einzubettenden Schriften
description: Erfahren Sie, wie Sie Schriftarten angeben, die in ein adaptives Formular eingebettet werden sollen. Sie können angeben, welche Schriftarten in Formulare eingebettet werden oder nie in Formulare eingebettet werden, die der Forms-Dienst generiert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b2cbf5f3-ee13-47bf-bf7f-f6a1884cee66
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 22%

---

# Angeben der einzubettenden Schriften {#specifying-fonts-to-embed}

Sie können angeben, welche Schriftarten immer oder nie in die Formulare eingebettet werden, die der Forms-Dienst generiert. Das Einbetten von Schriftarten erhöht die Dateigröße der Formulare. Betten Sie ungewöhnliche Schriftarten ein, die Benutzer selten auf ihren Systemen haben. Betten Sie keine gängigen Schriftarten ein, die sie normalerweise installiert haben.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Forms angegeben haben, setzt die Option &quot;Schrift einbetten&quot;in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Services > Forms]**.
1. Geben Sie unter **[!UICONTROL Schrifteinbettungseinstellungen]** in das Feld **[!UICONTROL Schriftarten immer einbetten]** die Namen der Schriftarten ein (durch Kommas getrennt), die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in das generierte Formular eingebettet, wenn sie im Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei aktiviert wurde, die an den Dienst übergeben wird, da in diesem Fall alle Schriften, die auf dem PDF verwendet werden, immer eingebettet werden.
1. Geben Sie in das Feld **[!UICONTROL Schriften nie einbetten]** die Namen der Schriftarten ein (durch Kommas getrennt), die nicht in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nicht in die PDF eingebettet, selbst wenn sie auf der generierten PDF verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei, die an den Dienst übergeben wird, deaktiviert wurde, da in diesem Fall keine der im PDF verwendeten Schriften eingebettet ist.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
