---
title: Angeben der einzubettenden Schriften
description: Erfahren Sie, wie Sie Schriftarten angeben, die in ein adaptives Formular eingebettet werden sollen. Sie können angeben, welche Schriften in Formulare eingebettet oder nie eingebettet werden sollen, die vom Forms-Dienst erstellt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b2cbf5f3-ee13-47bf-bf7f-f6a1884cee66
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---

# Angeben der einzubettenden Schriften {#specifying-fonts-to-embed}

Sie können angeben, welche Schriften immer oder nie in die Formulare eingebettet werden sollen, die vom Forms-Dienst erstellt werden. Das Einbetten von Schriften erhöht die Dateigröße von Formularen. Betten Sie ungewöhnliche Schriftarten ein, die Benutzende nur selten auf ihren Systemen haben. Betten Sie keine allgemeinen Schriftarten ein, die bei Benutzende normalerweise installiert sind.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Formulare angegeben haben, setzt die Option „Schrift einbetten“ in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Konfigurieren von Speicherorten für Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Services > Forms]**.
1. Geben Sie unter **[!UICONTROL Schrifteinbettungseinstellungen]** in das Feld **[!UICONTROL Schriftarten immer einbetten]** die Namen der Schriftarten ein (durch Kommas getrennt), die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in dem erzeugten Formular eingebettet, wenn sie in dem Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei aktiviert ist, die an den Dienst übermittelt wird, da in diesem Fall alle in der PDF-Datei verwendeten Schriftarten immer eingebettet werden.
1. Geben Sie in das Feld **[!UICONTROL Schriften nie einbetten]** die Namen der Schriftarten ein (durch Kommas getrennt), die nicht in Formulare eingebettet werden sollen. Die hier von Ihnen angegebenen Schriftarten werden nicht in der PDF-Datei eingebettet, selbst wenn sie in der generierten PDF-Datei verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei deaktiviert ist, die an den Dienst übermittelt wird, da in diesem Fall keine der in der PDF-Datei verwendeten Schriftarten eingebettet wird.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
