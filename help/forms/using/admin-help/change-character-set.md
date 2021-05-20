---
title: Den Zeichensatz ändern
seo-title: Den Zeichensatz ändern
description: Sie können den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird. Erfahren Sie, wie Sie den Zeichensatz ändern können.
seo-description: Sie können den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird. Erfahren Sie, wie Sie den Zeichensatz ändern können.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 9ff75d98-54ad-425d-912f-d5a7501bf564
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 96%

---

# Den Zeichensatz ändern {#change-the-character-set}

Sie können den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste > output]**.
1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung ist von den Parametern `TransformationFormat` und `PrintFormat` abhängig, die über die API festgelegt werden. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen kodierten Wert ein.

   Wenn `TransformationFormat` den Wert „PDF“ oder „PDF/A“ oder wenn `PrintFormat` den Wert „PCL“, „PostScript“, „Zebra label“, „IPL“, „DPL“, „TPCL“, „GenericColorPCL“ oder „GenericPSLevel3“ hat, werden nur bestimmte Zeichensätze unterstützt.

   Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist „ISO-8859-1“.

1. Klicken Sie auf **[!UICONTROL Speichern]**.
