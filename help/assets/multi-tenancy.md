---
title: Multi-Tenancy für Sammlungen, Snippets sowie Snippet-Vorlagen
description: Erfahren Sie, wie Sie mithilfe der Multi-Tenancy-Funktion Inhalte im CRX-Repository basierend auf der Kundenorganisation trennen können, um einen nicht autorisierten Zugriff zu verhindern.
contentOwner: AG
role: Architect, Admin, Leader
feature: Collections
exl-id: f95560c9-f1b9-4e86-94a7-70347d268d8f
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: ht
source-wordcount: '220'
ht-degree: 100%

---

# Multi-Tenancy für Sammlungen, Snippets sowie Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX auf Basis von Präfix und ID der Organisation trennen, um die Inhalte vor unberechtigtem Zugriff durch Anwender von anderen Unternehmen zu schützen.

[!DNL Adobe Experience Manager Assets] speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Organisationspräfix und die Organisations-ID angegeben, die am herkömmlichen Speicherort enthalten ist, in dem unterschiedliche Typen von Assets in CRX gespeichert werden.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo` erstellen, speichert [!DNL Experience Manager] Assets speichert den Ordner herkömmlicherweise unter `../content/dam/Demo`. Bei aktivierter Multi-Tenancy-Funktionen können Sie die Daten jetzt unter `../content/dam/<organization prefix>/<organization id>Demo` speichern.

Beispielsweise können Sie für [!DNL Adobe Marketing Cloud]-Benutzer von [!DNL Assets] (on Demand), die der `aodpremium`-Organisation zugewiesen sind, mit der Multi-Tenancy-Funktion den `../content/dam/<mac>/<aodpremium>Demo`-Pfad konfigurieren, um die Inhalte zu trennen. In diesem Beispiel ist `mac` das Organisations-Präfix und `aodpremium` ist Organisations-ID.

Auf Basis von Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der Benutzeroberfläche und in verschiedenen Assistenten von [!DNL Assets] angezeigt, darunter die Assistenten für Verschiebung und Snippet-Erstellung zur Durchsetzung der Trennung.

Mit der Multi-Tenancy-Funktion können Sie die folgenden Typen von Assets und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten „Seite hinzufügen/auswählen“)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
