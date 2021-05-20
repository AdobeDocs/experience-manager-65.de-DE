---
title: Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen
description: Erfahren Sie, wie Sie mit der Multi-Tenancy-Funktion Inhalte im CRX-Repository basierend auf der Kundenorganisation trennen können, um nicht autorisierten Zugriff zu verhindern.
contentOwner: AG
role: Architect, Administrator, Leader
feature: Sammlungen
exl-id: f95560c9-f1b9-4e86-94a7-70347d268d8f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 3%

---

# Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX basierend auf dem Organisations-Präfix und der Organisations-ID trennen, um den Inhalt vor unbefugtem Zugriff durch Benutzer anderer Organisationen zu schützen.

[!DNL Adobe Experience Manager Assets] speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Präfix und die Organisations-ID identifiziert
, die am herkömmlichen Speicherort enthalten ist, an dem verschiedene Asset-Typen in CRX gespeichert sind.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo` erstellen, speichert [!DNL Experience Manager]-Assets den Ordner traditionell unter `../content/dam/Demo`. Bei aktivierter Multi-Tenancy können Sie die Daten jetzt unter `../content/dam/<organization prefix>/<organization id>Demo` speichern.

Wenn Sie beispielsweise für [!DNL Adobe Marketing Cloud] Benutzer von [!DNL Assets] (On-Demand), die der `aodpremium`-Organisation zugewiesen sind, können Sie mit der Multi-Tenancy-Funktion den Pfad `../content/dam/<mac>/<aodpremium>Demo` konfigurieren, um ihren Inhalt zu trennen. In diesem Beispiel ist `mac` das Organisationspräfix und `aodpremium` die Organisations-ID.

Basierend auf der Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der [!DNL Assets]-Benutzeroberfläche und in verschiedenen Assistenten angezeigt, einschließlich der Assistenten zum Verschieben und Erstellen von Snippets , um die Segmentierung zu erzwingen.

Mit der Multi-Tenancy-Funktion können Sie die folgenden Assettypen und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
