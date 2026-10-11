---
title: Überprüfen der Informationen zur Verwendung von Anmeldedaten
description: Erfahren Sie, wie Sie die Informationen zur Verwendung von Anmeldedaten überprüfen. Auf die Informationen zur Verwendung von Anmeldedaten, die ihre Verwendung beschreiben, kann über die Acrobat Reader-Erweiterung zugegriffen werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a8e16cf8-f3c8-48ce-87da-2f0de0b10a6e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 94%
---
# Überprüfen der Informationen zur Verwendung von Anmeldedaten {#review-credential-use-information}

Die Anmeldedaten enthalten Informationen zur Beschreibung der vorgesehenen Verwendung, auf die über die Acrobat Reader DC-Erweiterungen-Web-Anwendung für Endbenutzende zugegriffen werden kann. Anhand dieser Informationen können Sie den Typ der installierten Anmeldedaten (entweder Test oder Produktion) und die Gültigkeitsdauer bestimmen.

1. Öffnen Sie einen Webbrowser und geben Sie diese URL ein:

   http://localhost:port/ReaderExtensions (wobei *port* die Port-Nummer Ihres Anwendungsservers ist)

1. Melden Sie sich mit dem standardmäßigen Benutzernamen und Kennwort an:

   Benutzername: administrator

   Kennwort: password

   >[!NOTE]
   >
   >Sie benötigen Administrator- oder Hauptbenutzer-Berechtigungen, um sich mit dem standardmäßigen Benutzernamen und Kennwort anmelden zu können. Um anderen Benutzenden den Zugriff auf Acrobat Reader DC-Erweiterungen zu erlauben, erstellen Sie die Benutzerkonten in User Management und weisen Sie ihnen die Rolle „Acrobat Reader DC-Erweiterungen-Web-Anwendung“ zu.

1. Wählen Sie den Anmeldedaten-Alias in der Liste „Anmeldedaten auswählen“ aus und überprüfen Sie die Informationen in den Feldern „Ablaufdatum“ und „Hinweis zur bestimmungsgemäßen Verwendung“.

>[!NOTE]
>
>Das Ablaufdatum der Anmeldedaten finden Sie auch in der Administrationskonsole auf der Seite „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Anmeldedaten“ unter „Ablaufdatum“.
