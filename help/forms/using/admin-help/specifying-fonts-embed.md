---
title: Einzubettende Schriften angeben
seo-title: Einzubettende Schriften angeben
description: Hier erfahren Sie, wie Sie Schriftarten angeben, die Sie einbetten möchten.
seo-description: Hier erfahren Sie, wie Sie Schriftarten angeben, die Sie einbetten möchten.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: b2cbf5f3-ee13-47bf-bf7f-f6a1884cee66
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 80%

---

# Einzubettende Schriften angeben {#specifying-fonts-to-embed}

Sie können angeben, welche Schriften immer oder nie in Formulare eingebettet werden sollen, die vom Forms-Dienst erstellt werden. Das Einbetten von Schriften erhöht die Dateigröße von Formularen. Betten Sie ungewöhnliche Schriftarten ein, die die Benutzer nur selten auf ihren Systemen haben. Betten Sie keine allgemeinen Schriftarten ein, die sie normalerweise installiert haben.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Forms angegeben haben, setzt die Option „Schrift einbetten“ in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste > Forms]**.
1. Geben Sie unter **[!UICONTROL Einstellungen für die Schrifteinbettung]** im Feld **[!UICONTROL Schriftarten immer einbetten]** die Namen der Schriftarten ein, die mit den Formularen eingebettet werden sollen, getrennt durch Kommas. Die von Ihnen angegebenen Schriften werden nur in dem erzeugten Formular eingebettet, wenn sie in dem Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, aktiviert ist, da in diesem Fall alle Schriften, die in der PDF-Datei verwendet werden, immer eingebettet werden.
1. Geben Sie in das Feld **[!UICONTROL Schriften nie einbetten]** die Namen der Schriften ein, die nicht in Formulare eingebettet werden sollen (durch Kommas getrennt). Die von Ihnen angegebenen Schriften werden nicht in der PDF-Datei eingebettet, selbst wenn sie in der generierten PDF-Datei verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, deaktiviert ist, da in diesem Fall keine der Schriften, die in der PDF-Datei verwendet werden, eingebettet wird.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
