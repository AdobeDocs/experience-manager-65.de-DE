---
title: Informationen zur Verwendung der Berechtigung überprüfen
seo-title: Informationen zur Verwendung der Berechtigung überprüfen
description: Erfahren Sie, wie Sie die Informationen zur Verwendung der Berechtigung überprüfen.
seo-description: Erfahren Sie, wie Sie die Informationen zur Verwendung der Berechtigung überprüfen.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: a8e16cf8-f3c8-48ce-87da-2f0de0b10a6e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 93%

---

# Informationen zur Verwendung der Berechtigung überprüfen {#review-credential-use-information}

Die Berechtigung enthält Informationen zu ihrem vorgesehenen Zweck, auf die über die Acrobat Reader DC Extensions-Webanwendung für Endbenutzer zugegriffen werden kann. Anhand dieser Informationen können Sie den Typ der installierten Berechtigung (entweder Test oder Produktion) und die Gültigkeitsdauer bestimmen.

1. Öffnen Sie einen Webbrowser und geben Sie diese URL ein:

   http://localhost:port/ReaderExtensions (wobei *port* die Anschlussnummer Ihres Anwendungsservers ist)

1. Melden Sie sich mit dem standardmäßigen Benutzernamen und Kennwort an:

   Benutzername: administrator

   Kennwort: password

   >[!NOTE]
   >
   >Sie benötigen Administrator- oder Hauptbenutzerberechtigungen, um sich mit dem standardmäßigen Benutzernamen und Kennwort anmelden zu können. Um anderen Benutzern den Zugriff auf Acrobat Reader DC Extensions zu erlauben, erstellen Sie die Benutzerkonten in User Management und weisen Sie ihnen die Rolle „Acrobat Reader DC Extensions-Webanwendung“ zu.

1. Wählen Sie den Berechtigungsalias in der Liste „Berechtigung auswählen“ aus und überprüfen Sie die Informationen in den Feldern „Ablaufdatum“ und „Hinweis zur bestimmungsgemäßen Verwendung“.

>[!NOTE]
>
>Das Ablaufdatum finden Sie auch in Administration Console auf der Seite „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“ unter „Ablaufdatum“.
