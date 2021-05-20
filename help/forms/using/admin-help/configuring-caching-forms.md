---
title: Zwischenspeicherung für Forms konfigurieren
seo-title: Zwischenspeicherung für Forms konfigurieren
description: Erfahren Sie, wie Sie Cacheeinstellungen konfigurieren und wie Sie Überlegungen zum Cache gruppieren.
seo-description: Erfahren Sie, wie Sie Cacheeinstellungen konfigurieren und wie Sie Überlegungen zum Cache gruppieren.
uuid: 70f36191-4163-410b-991a-e1481488aea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8a07dddf-1281-45ac-a55e-4333b860a261
exl-id: 6b57d00e-5ba0-41ee-8497-49ecfec5b9ed
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 88%

---

# Zwischenspeicherung für Forms konfigurieren{#configuring-caching-for-forms}

Der Forms-Dienst nimmt Formularentwürfe, die in Designer erstellt wurden, und gibt sie in verschiedenen Formaten wieder.

Die Forms-Seite in der Administration Console enthält Einstellungen, die steuern, wie der Forms-Dienst Elemente zwischenspeichert. Sie können diese Einstellungen anpassen, um die Leistung des Forms-Dienstes zu optimieren.

Der Forms-Dienst führt für die folgenden Elemente eine Zwischenspeicherung aus:

* **Formularentwürfe:** Der Forms-Dienst speichert Formularentwürfe zwischen, die von dem Repository oder von HTTP-Quellen abgerufen werden. Diese Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.
* **Fragmente und Bilder:** Der Forms-Dienst kann in Formularentwürfen verwendete Fragmente und Bilder zwischenspeichern. Wenn der Forms-Dienst diese Objekte zwischenspeichert, wird die Leistung verbessert, da die Fragmente und Bilder nur bei der ersten Anforderung vom Repository gelesen werden.
* **Formulare:** Der Forms-Dienst speichert die wiedergegebenen Formulare zwischen. Diese Art der Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst dasselbe Formular in nachfolgenden Anforderungen nicht auflösen und wiedergeben muss.

Forms speichert den Zwischenspeicher an zwei Speicherorten:

* **Im Arbeitsspeicher:** Elemente werden für schnellen Zugriff im Arbeitsspeicher gespeichert. Der Arbeitsspeichercache verfügt über eine begrenzte Größe und wir beim Neustart des Servers gelöscht.
* **Auf einem Datenträger:** Elemente werden im Dateisystem des Servers gespeichert. Der Datenträgercache verfügt über eine größere Kapazität als der Arbeitsspeichercache und er wird beim Neustart des Servers beibehalten. Der Speicherort des Datenträgercache hängt von Ihrem Anwendungsserver ab. Weitere Informationen zum Ändern des Speicherorts des Datenträger-Caches finden Sie unter [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).

## Cachemodus angeben {#specifying-the-cache-mode}

Forms unterstützt zwei Modi für die Zwischenspeicherung:

* nicht konditional
* unter Verwendung des Cacheprüfpunkts

Wenn Sie zwischen den Cachemodi wechseln, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

Die Cacheprüfpunkt-Zeit wird beim Wechsel zwischen den Modi automatisch zurückgesetzt.

### Nicht konditionale Zwischenspeicherung verwenden  {#using-unconditional-caching}

In diesem Modus überprüft der Forms-Dienst die erforderlichen Ressourcen (Formularentwurf und andere zugehörige Elemente wie Fragmente und Bilder), wenn er eine Anforderung erhält. Der Forms-Dienst vergleicht den Zeitstempel der Ressourcen im Repository mit dem Zeitstempel der Ressourcen im Cache. Ist die Ressource im Cache älter, wird dieser vom Forms-Dienst aktualisiert.

Dieser Cache-Modus gewährleistet, dass die neuesten Ressourcen verwendet werden. Jedoch hat dies Auswirkungen auf die Leistung, da der Forms-Dienst die zwischengespeicherten Elemente bei jeder Anforderung gegen das Repository überprüft. Dieser Cache-Modus ist für Entwicklungs- und Testumgebungen geeignet, in denen Ressourcen häufig aktualisiert werden und die Leistung nicht am wichtigsten ist.

**Nicht konditionale Zwischenspeicherung angeben**

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Wählen Sie unter „Einstellungen für die Forms-Cache-Steuerung“ die Option „Bedingungslos“ aus und klicken Sie auf „Speichern“.

### Den Cacheprüfpunkt verwenden  {#use-the-cache-check-point}

In diesem Modus überprüft der Forms-Dienst das Repository nur dann auf eine neuere Version der Ressourcen, wenn der Zeitstempel der zwischengespeicherten Ressourcen vor der Cacheprüfpunkt-Zeit liegt. Die letzte Cacheprüfpunkt-Zeit wird auf der Forms-Seite in Administration Console angezeigt.

Verwenden Sie diesen Cache-Modus in Produktionsumgebungen mit hoher Leistung, in denen Änderungen an den Ressourcen nicht häufig vorkommen und in denen die Leistung wichtig ist. Sie können die Cacheprüfpunkt-Zeit zurücksetzen, wenn Sie Änderungen an den Repository-Ressourcen bereitstellen möchten.

**Die Verwendung einer Cacheprüfpunkt-Zeit angeben**

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Aktivieren Sie unter „Einstellungen für die Forms-Cache-Steuerung“ die Option „Nur, wenn die letzte Validierung vor der Cacheprüfpunkt-Zeit ausgeführt wurde“ und klicken Sie auf „Speichern“.

**Die Cacheprüfpunkt-Zeit zurücksetzen**

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Klicken Sie unter „Einstellungen für die Forms-Cache-Steuerung“ auf die Option „Cacheprüfpunkt“.

**Den Inhalt des Zwischenspeichers zurücksetzen**

Sie können den Inhalt des Zwischenspeichers jederzeit löschen. Nach dem Zurücksetzen des Zwischenspeichers ist die erste Anforderung für jedes Formular langsamer, da der Forms-Dienst eine vollständige Wiedergabe ausführt und neue Inhalte für den Zwischenspeicher erstellt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Klicken Sie unter „Einstellungen für die Formularcache-Steuerung“ auf die Option „Cache zurücksetzen“.

## Cache-Einstellungen konfigurieren  {#configuring-cache-settings}

Sie können Eigenschaften festlegen, die von Forms für die Zwischenspeicherung verwendet werden und die die Leistung der AEM Forms-Umgebung optimieren können.

Klicken Sie zum Zugreifen auf diese Einstellungen in Administration Console auf „Dienste“ > „Forms“.

>[!NOTE]
>
>Die Datenträgeranforderungen für den Cache müssen denen für das Repository entsprechen.

### Globale Cache-Einstellungen angeben  {#specifying-global-cache-settings}

Die Einstellungen im Bereich **Globale Cache-Einstellungen** wirken sich auf alle Cache-Typen aus. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Maximale Größe des Cache-Dokuments (KB):**  Die maximale Größe (in Kilobytes) eines Formularentwurfs oder einer anderen Ressource, die in einem beliebigen Arbeitsspeichercache gespeichert werden kann. Dies ist eine globale Einstellung, die für alle Arbeitsspeichercaches gilt. Wenn eine Ressource größer als dieser Wert ist, wird sie nicht im Arbeitsspeicher zwischengespeichert. Der Standardwert ist 1024 KB. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Formular-Rendering-Cache aktiviert:** Standardmäßig ist diese Option aktiviert. Das bedeutet, dass die wiedergegebenen Formulare für den nachfolgenden Abruf zwischengespeichert werden. Diese Einstellung verbessert die Leistung, da der Forms-Dienst nur einmal ein bestimmtes Formular wiedergeben muss und danach wird die zwischengespeicherte Version verwendet. Diese Option nutzt die Cache-Eigenschaft des Formularentwurfs. Informationen zum Konfigurieren dieses Wertes im Formularentwurf finden Sie in der Designer-Hilfe.

### Formularentwürfe zwischenspeichern {#caching-form-designs}

Wenn der Forms-Dienst eine Wiedergabeanforderung erhält, werden die Formularentwürfe aus dem Repository abgerufen und zwischengespeichert. Diese Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.

Der Forms-Dienst speichert Formularentwürfe immer auf dem Datenträger zwischen. Wenn Formularentwürfe auf dem Server gespeichert werden, werden diese Dateien als Datenträgercache bezeichnet. Der Forms-Dienst speichert außerdem Formularentwürfe im Arbeitsspeicher zwischen, gemäß der Einstellung im Bereich **Arbeitsspeichercache für Vorlagenkonfiguration**. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Cachegröße für Vorlagenkonfiguration:** Die maximale Anzahl von Vorlagenkonfigurationsobjekten, die im Speicher beibehalten werden sollen. Der Standardwert ist 100. Es wird empfohlen, diesen Wert größer gleich dem Wert für die Vorlagencache-Größe festzulegen. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Vorlagencache-Größe:** Die maximale Anzahl von Vorlageninhaltsobjekten, die im Speicher beibehalten werden sollen. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist dieses Kontrollkästchen aktiviert, d. h. Formularvorlagen werden im Arbeitsspeicher zwischengespeichert. Wenn diese Option nicht ausgewählt ist, werden die Formularvorlagen nur auf dem Datenträger zwischengespeichert.

### Wiedergegebene Formulare zwischenspeichern  {#caching-rendered-forms}

Der Forms-Dienst speichert wiedergegebene Formulare zwischen, damit dasselbe Formular in nachfolgenden Anforderungen nicht aufgelöst und wiedergegeben werden muss. Wiedergegebene Formulare werden auf dem Datenträger und im Arbeitsspeicher zwischengespeichert.

Diese Einstellungen befinden sich im Bereich **Arbeitsspeichercache für Formularwiedergabe**. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Cachegröße:** Gibt die maximale Anzahl der wiedergegebenen Formulare an, die sich im Arbeitsspeichercache befinden können. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist diese Option ausgewählt, d. h. die wiedergegebenen Formulare werden im Arbeitsspeicher zwischengespeichert. Wenn diese Option nicht ausgewählt ist, werden die wiedergegebenen Formulare nur auf dem Datenträger zwischengespeichert.

### Fragmente und Bilder zwischenspeichern  {#caching-fragments-and-images}

Der Forms-Dienst speichert Fragmente und Bilder zwischen, die in Formularentwürfen auf dem Datenträger verwendet werden. Dies verbessert die Leistung, da die Fragmente und Bilder nur bei der ersten Anforderung vom Repository gelesen werden. Bei nachfolgenden Anforderungen liest der Forms-Dienst anschließend die Fragmente und Bilder vom Datenträgercache. Fragmente und Bilder werden nur auf dem Datenträger zwischengespeichert und nicht im Arbeitsspeicher.

Sie können die folgenden Einstellungen verwenden, um die Zwischenspeicherung von Fragmenten und Bildern auf dem Datenträger zu steuern. Diese Einstellungen befinden sich im Bereich **Cacheeinstellungen für Vorlagenressourcen**:

**Resource** CachingWählen Sie eine der folgenden Optionen aus der Liste aus:

**Aktiviert für Fragmente und Bilder:** Der Forms-Dienst speichert Fragmente und Bilder zwischen. Dies ist die Standardoption.

**Aktiviert für Fragmente:**  Der Forms-Dienst speichert Fragmente, jedoch keine Bilder zwischen.

**Deaktiviert:** Der Forms-Dienst speichert keine Fragmente oder Bilder zwischen.

**Bereinigungsintervall (Sekunden):** Gibt an, wie oft der Forms-Dienst alte ungültige Cachedateien entfernt. Der Forms-Dienst entfernt keine gültigen Cachedateien. Wenn Sie das Bereinigungsintervall ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind. Der Standardwert ist 600 Sekunden.

## Clustering-Überlegungen zum Zwischenspeicher {#clustering-considerations-for-caches}

In einer Clusterumgebung verwaltet jeder Knoten seinen eigenen Arbeitsspeicher- und Datenträgercache. Der Inhalt des Zwischenspeichers auf jedem Knoten hängt davon ab, welche Formulare auf diesem Knoten wiedergegeben wurden.

Der Speicherort des Zwischenspeichers muss auf jedem Knoten des Clusters identisch sein (derselbe Datenträger und Pfad). Legen Sie den Zwischenspeicher nicht auf einem freigegebenen Speicher ab.

Wenn Sie die Forms-Seite in der Administration Console verwenden, um die Cache-Einstellungen für einen bestimmten Knoten zu ändern, werden die Cache-Einstellungen bei einer Anforderung an diesen Knoten auch auf anderen Knoten aktualisiert. Dieses Verhalten gilt auch für die Schaltfläche „Cache zurücksetzen“. Wenn Sie auf die Schaltfläche „Cache zurücksetzen“ für einen Knoten klicken, wird der Zwischenspeicher sofort von diesem Knoten gelöscht. Der Zwischenspeicher auf anderen Knoten wird bei einer Anforderung an diesen Knoten gelöscht.
