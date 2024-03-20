---
title: Überprüfen der Informationen zur Verwendung von Anmeldedaten
description: Erfahren Sie, wie Sie die Informationen zur Nutzung der Berechtigung überprüfen. Auf die Informationen zur Verwendung der Berechtigung, die deren Verwendung beschreibt, kann über die Acrobat Reader-Erweiterung zugegriffen werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a8e16cf8-f3c8-48ce-87da-2f0de0b10a6e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 9%

---

# Überprüfen der Informationen zur Verwendung von Anmeldedaten {#review-credential-use-information}

Die Berechtigung enthält Informationen zur Beschreibung der vorgesehenen Verwendung, auf die über die Acrobat Reader DC Extensions-Webanwendung für Endbenutzer zugegriffen werden kann. Mithilfe dieser Informationen können Sie den Typ der installierten Berechtigung (entweder Test oder Produktion) und deren Gültigkeitsdaten bestimmen.

1. Öffnen Sie einen Webbrowser und geben Sie diese URL ein:

   http://localhost:port/ReaderExtensions (wobei *port* die Port-Nummer Ihres Programm-Servers ist)

1. Melden Sie sich mit dem Standardbenutzernamen und -kennwort an:

   Benutzername: administrator

   Kennwort: password

   >[!NOTE]
   >
   >Sie müssen über Administrator- oder Superuser-Berechtigungen verfügen, um sich mit dem Standardbenutzernamen und -kennwort anzumelden. Um anderen Benutzern den Zugriff auf Acrobat Reader DC-Erweiterungen zu ermöglichen, erstellen Sie die Benutzerkonten in User Management und weisen Sie den Benutzern die Rolle Acrobat Reader DC Extensions-Webanwendung zu.

1. Wählen Sie den Berechtigungsalias aus der Liste &quot;Berechtigung auswählen&quot;aus und überprüfen Sie die Informationen in den Abschnitten &quot;Ablaufdatum&quot;und &quot;Hinweis zur vorgesehenen Verwendung&quot;.

>[!NOTE]
>
>Das Ablaufdatum der Berechtigung ist auch auf der Seite Einstellungen > Trust Store-Verwaltung > Lokale Berechtigungen in Administration Console unter &quot;Ablaufdatum&quot;verfügbar.
