---
title: Angeben der einzubettenden Schriftarten
description: Erfahren Sie, wie Sie Schriftarten angeben, die in ein adaptives Formular eingebettet werden sollen. Sie können angeben, welche Schriftarten in Formulare eingebettet werden oder nie in Formulare eingebettet werden, die der Forms-Dienst generiert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 02c28b2c-0cab-4431-9fab-fa332c96e092
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 22%

---

# Angeben der einzubettenden Schriftarten{#specify-fonts-to-embed}

Sie können angeben, welche Schriftarten immer oder nie in die von Output verwendeten Formulare eingebettet werden. Das Einbetten von Schriftarten erhöht die Dateigröße der Formulare. Betten Sie ungewöhnliche Schriftarten ein, die Benutzer wahrscheinlich nicht auf ihren Systemen haben, und betten Sie keine gängigen Schriftarten ein, die sie installiert haben.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für die Ausgabe angegeben haben, setzt die Option &quot;Schrift einbetten&quot;in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Geben Sie unter „Schrifteinbettungseinstellungen“ in das Feld „Schriftarten immer einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in das generierte Formular eingebettet, wenn sie im Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei aktiviert wurde, die an den Dienst übergeben wird. In diesem Fall werden alle im PDF verwendeten Schriftarten immer eingebettet.
1. Geben Sie in das Feld „Schriften nie einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die nicht in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nicht in die PDF eingebettet, selbst wenn sie auf der generierten PDF verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei, die an den Dienst übergeben wird, deaktiviert wurde. In diesem Fall wird keine der im PDF verwendeten Schriftarten eingebettet.
1. Klicken Sie auf „Speichern“.
