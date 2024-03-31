---
title: Ändern des Zeichensatzes
description: Sie können den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert werden soll. Erfahren Sie, wie Sie den Zeichensatz ändern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 9ff75d98-54ad-425d-912f-d5a7501bf564
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 100%

---

# Ändern des Zeichensatzes {#change-the-character-set}

Sie können den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert werden soll.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Services > Ausgabe]**.
1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung ist von den Parametern `TransformationFormat` und `PrintFormat` abhängig, die über die API festgelegt werden. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen kodierten Wert ein.

   Wenn `TransformationFormat` den Wert „PDF“ oder „PDF/A“ oder wenn `PrintFormat` den Wert „PCL“, „PostScript“, „Zebra label“, „IPL“, „DPL“, „TPCL“, „GenericColorPCL“ oder „GenericPSLevel3“ hat, werden nur bestimmte Zeichensätze unterstützt.

   Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist ISO-8859-1.

1. Klicken Sie auf **[!UICONTROL Speichern]**.
