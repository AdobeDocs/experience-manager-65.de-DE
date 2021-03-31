---
title: Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen
description: Erfahren Sie, wie Sie mit der Funktion für mehrere Mandanten Inhalte im CRX-Repository basierend auf der Kundenorganisation trennen können, um nicht autorisierten Zugriff zu verhindern.
contentOwner: AG
role: Architekt, Administrator, Leiter
feature: Sammlungen
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 3%

---


# Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Funktion für mehrere Mandanten können Sie Inhalte in CRX basierend auf dem Organisations-Präfix und der Organisations-ID trennen, um den Inhalt vor unbefugtem Zugriff durch Benutzer anderer Organisationen zu schützen.

[!DNL Adobe Experience Manager Assets] speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Präfix und die Organisations-ID identifiziert
die im traditionellen Speicherort enthalten ist, an dem verschiedene Asset-Typen in CRX gespeichert werden.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo` erstellen, speichert [!DNL Experience Manager] assets den Ordner traditionell unter `../content/dam/Demo`. Bei aktivierter Multi-Mandate können Sie die Daten jetzt unter `../content/dam/<organization prefix>/<organization id>Demo` speichern

Wenn Sie beispielsweise für [!DNL Adobe Marketing Cloud]-Benutzer von [!DNL Assets] (On-Demand), die dem `aodpremium`-Unternehmen zugewiesen sind, den Pfad für `../content/dam/<mac>/<aodpremium>Demo` mit der Funktion für mehrere Mandanten konfigurieren, können Sie den Pfad zum Trennen ihres Inhalts konfigurieren. In diesem Beispiel ist `mac` das Organisations-Präfix und `aodpremium` die Organisations-ID.

Dieser qualifizierte Pfad wird basierend auf der Organisation und ID des Benutzers in der [!DNL Assets]-Schnittstelle und verschiedenen Assistenten angezeigt, einschließlich der Assistenten zum Verschieben und Snippet-Erstellen, um die Segregation zu erzwingen.

Mit der Funktion &quot;Mehrere Mandanten&quot;können Sie die folgenden Assets und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite Hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
