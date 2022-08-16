---
title: Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen
description: Erfahren Sie, wie Sie mit der Multi-Tenancy-Funktion Inhalte im CRX-Repository basierend auf der Kundenorganisation trennen können, um nicht autorisierten Zugriff zu verhindern.
contentOwner: AG
role: Architect, Admin, Leader
feature: Collections
exl-id: f95560c9-f1b9-4e86-94a7-70347d268d8f
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---

# Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX basierend auf dem Organisations-Präfix und der Organisations-ID trennen, um den Inhalt vor unbefugtem Zugriff durch Benutzer anderer Organisationen zu schützen.

[!DNL Adobe Experience Manager Assets] speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Organisations-Präfix und die Organisations-ID identifiziert, die am herkömmlichen Speicherort enthalten sind, an dem verschiedene Asset-Typen in CRX gespeichert sind.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo`, [!DNL Experience Manager] -Assets speichert den Ordner herkömmlicherweise unter `../content/dam/Demo`. Bei aktivierter Multi-Tenancy können Sie die Daten jetzt unter `../content/dam/<organization prefix>/<organization id>Demo`

Beispiel: Wenn für [!DNL Adobe Marketing Cloud] Benutzer von [!DNL Assets] (On-Demand), die der `aodpremium` -Organisation, können Sie die Multi-Tenancy-Funktion verwenden, um `../content/dam/<mac>/<aodpremium>Demo` Pfad, um ihren Inhalt zu trennen. In diesem Beispiel `mac` ist das Organisations-Präfix und `aodpremium` ist die Organisations-ID.

Basierend auf der Organisation und ID des Benutzers wird dieser qualifizierte Pfad im [!DNL Assets] -Benutzeroberfläche und verschiedenen Assistenten, einschließlich der Assistenten zum Verschieben und Erstellen von Segmenten, um die Segmentierung zu erzwingen.

Mit der Multi-Tenancy-Funktion können Sie die folgenden Assettypen und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
