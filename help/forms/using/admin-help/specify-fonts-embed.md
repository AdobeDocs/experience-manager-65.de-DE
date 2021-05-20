---
title: Einzubettende Schriften angeben
seo-title: Einzubettende Schriften angeben
description: Hier erfahren Sie, wie Sie Schriftarten angeben, die Sie einbetten möchten.
seo-description: Hier erfahren Sie, wie Sie Schriftarten angeben, die Sie einbetten möchten.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: 02c28b2c-0cab-4431-9fab-fa332c96e092
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 100%

---

# Einzubettende Schriften angeben{#specify-fonts-to-embed}

Sie können angeben, welche Schriften immer oder nie in Formulare eingebettet werden sollen, die von Output verwendet werden. Das Einbetten von Schriften erhöht die Dateigröße von Formularen. Betten Sie ungewöhnliche Schriften ein, die Benutzer eher selten installiert haben, während gängige Schriften, die der Benutzer vermutlich installiert hat, nicht eingebettet werden sollten.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Output angegeben haben, setzt die Option „Schrift einbetten“ in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Geben Sie unter „Schrifteinbettungseinstellungen“ in das Feld „Schriften immer einbetten“ die Namen der Schriften ein (durch Kommas getrennt), die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriften werden nur in dem erzeugten Formular eingebettet, wenn sie in dem Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, aktiviert ist. In diesem Fall werden alle Schriften, die in der PDF-Datei verwendet werden, immer eingebettet.
1. Geben Sie in das Feld „Schriften nie einbetten“ die Namen der Schriften ein (durch Kommas getrennt), die nicht in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriften werden nicht in der PDF-Datei eingebettet, selbst wenn sie in der generierten PDF-Datei verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, deaktiviert ist. In diesem Fall wird keine der Schriften, die in der PDF-Datei verwendet werden, eingebettet.
1. Klicken Sie auf Speichern.
