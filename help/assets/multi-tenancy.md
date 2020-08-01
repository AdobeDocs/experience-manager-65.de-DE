---
title: Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen
description: Erfahren Sie, wie Sie mit der Funktion für mehrere Mandanten Inhalte im CRX-Repository basierend auf der Kundenorganisation trennen können, um nicht autorisierten Zugriff zu verhindern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# Multi-tenancy for Collections, snippets, and snippet templates {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Funktion für mehrere Mandanten können Sie Inhalte in CRX basierend auf dem Organisations-Präfix und der Organisations-ID trennen, um den Inhalt vor unbefugtem Zugriff durch Benutzer anderer Organisationen zu schützen.

[!DNL Adobe Experience Manager Assets] speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Organisations-Präfix und die Organisations-ID identifiziert, die im traditionellen Speicherort enthalten sind, an dem verschiedene Asset-Typen in CRX gespeichert werden.

Wenn Sie z. B. einen Ordner mit dem Namen `Demo`erstellen, speichert assets normalerweise den Ordner in [!DNL Experience Manager] Assets `../content/dam/Demo`. Bei aktivierter Multi-Mandate können Sie die Daten jetzt unter `../content/dam/<organization prefix>/<organization id>Demo`

For example, if for [!DNL Adobe Marketing Cloud] users of [!DNL Assets] (on demand) that are assigned to the `aodpremium` organization, you can use the multi-tenancy feature to configure `../content/dam/<mac>/<aodpremium>Demo` path to segregate their content. In diesem Beispiel `mac` ist das Organisations-Präfix und `aodpremium` die Organisations-ID.

Based on the user&#39;s organization and ID, this qualified path is displayed in the [!DNL Assets] interface and various wizards, including the Move and Snippet creation wizards to enforce segregation.

Mit der Funktion &quot;Mehrere Mandanten&quot;können Sie die folgenden Assets und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite Hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
