---
title: Angeben der einzubettenden Schriftarten
description: Erfahren Sie, wie Sie Schriftarten angeben, die in ein adaptives Formular eingebettet werden sollen. Sie können angeben, welche Schriften in Formulare eingebettet oder nie eingebettet werden sollen, die vom Forms-Dienst erstellt werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 02c28b2c-0cab-4431-9fab-fa332c96e092
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 100%

---

# Angeben der einzubettenden Schriftarten{#specify-fonts-to-embed}

Sie können angeben, welche Schriftarten immer oder nie in Formulare eingebettet werden sollen, die von der Ausgabe verwendet werden. Das Einbetten von Schriften erhöht die Dateigröße von Formularen. Betten Sie ungewöhnliche Schriftarten ein, die Benutzende eher selten installiert haben, während gängige Schriften, die vermutlich installiert sind, nicht eingebettet werden sollten.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Output angegeben haben, setzt die Option „Schrift einbetten“ in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Angeben von Dateispeicherorten für die Ausgabe](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Geben Sie unter „Schrifteinbettungseinstellungen“ in das Feld „Schriftarten immer einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in dem erzeugten Formular eingebettet, wenn sie in dem Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, aktiviert ist.  In diesem Fall werden alle Schriftarten, die in der PDF-Datei verwendet werden, immer eingebettet.
1. Geben Sie in das Feld „Schriften nie einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die nicht in Formulare eingebettet werden sollen. Die hier von Ihnen angegebenen Schriftarten werden nicht in der PDF-Datei eingebettet, selbst wenn sie in der generierten PDF-Datei verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schriftart einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, deaktiviert ist.  In diesem Fall wird keine der Schriftarten, die in der PDF-Datei verwendet werden, eingebettet.
1. Klicken Sie auf „Speichern“.
