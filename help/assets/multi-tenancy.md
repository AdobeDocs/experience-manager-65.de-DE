---
title: Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen
description: Erfahren Sie, wie Sie mit der Funktion für mehrere Mandanten Inhalte im CRX-Repository basierend auf der Kundenorganisation trennen können, um nicht autorisierten Zugriff zu verhindern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 3%

---


# Multi-tenancy for Collections, snippets, and snippet templates {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Funktion für mehrere Mandanten können Sie Inhalte in CRX basierend auf dem Organisations-Präfix und der Organisations-ID trennen, um den Inhalt vor unbefugtem Zugriff durch Benutzer anderer Organisationen zu schützen.

Adobe Experience Manager Assets speichert Daten für jedes Unternehmen in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Organisations-Präfix und die Organisations-ID identifiziert, die im traditionellen Speicherort enthalten sind, an dem verschiedene Asset-Typen in CRX gespeichert werden.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo`erstellen, speichert Experience Manager-Assets den Ordner üblicherweise unter `../content/dam/Demo`. Bei aktivierter Multi-Mandate können Sie die Daten jetzt unter `../content/dam/<organization prefix>/<organization id>Demo`

For example, if for [!DNL Adobe Marketing Cloud] users of Assets (on demand) that are assigned to the `aodpremium` organization, you can use the multi-tenancy feature to configure `../content/dam/<mac>/<aodpremium>Demo` path to segregate their content. In diesem Beispiel `mac` ist das Organisations-Präfix und `aodpremium` die Organisations-ID.

Dieser qualifizierte Pfad wird basierend auf der Organisation und der ID des Benutzers in der Assets-Oberfläche und in verschiedenen Assistenten angezeigt, einschließlich der Assistenten zum Erstellen von Verschieben und Segmenten, um die Segregation zu erzwingen.

Mit der Funktion &quot;Mehrere Mandanten&quot;können Sie die folgenden Assets und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite Hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
