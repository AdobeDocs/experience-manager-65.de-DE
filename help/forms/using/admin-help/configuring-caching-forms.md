---
title: Konfigurieren der Zwischenspeicherung für Forms
description: Erfahren Sie, wie Sie Cache-Einstellungen konfigurieren und wie Sie Überlegungen zum Cluster für Caches durchführen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6b57d00e-5ba0-41ee-8497-49ecfec5b9ed
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1611'
ht-degree: 26%

---

# Konfigurieren der Zwischenspeicherung für Forms{#configuring-caching-for-forms}

Der Forms-Dienst nimmt Formularentwürfe vor, die in Designer erstellt wurden, und rendert sie in verschiedenen Formaten.

Die Forms-Seite in Administration Console enthält Einstellungen, die steuern, wie der Forms-Dienst Elemente zwischenspeichert. Sie können diese Einstellungen anpassen, um die Leistung des Forms-Dienstes zu optimieren.

Der Forms-Dienst speichert die folgenden Elemente zwischen:

* **Formularentwürfe:** Der Forms-Dienst speichert Formularentwürfe zwischen, die von dem Repository oder von HTTP-Quellen abgerufen werden. Diese Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.
* **Fragmente und Bilder:** Der Forms-Dienst kann in Formularentwürfen verwendete Fragmente und Bilder zwischenspeichern. Wenn der Forms-Dienst diese Objekte zwischenspeichert, wird die Leistung verbessert, da die Fragmente und Bilder nur bei der ersten Anforderung vom Repository gelesen werden.
* **Formulare:** Der Forms-Dienst speichert die wiedergegebenen Formulare zwischen. Diese Art der Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst dasselbe Formular in nachfolgenden Anfragen nicht auflösen und wiedergeben muss.

Forms speichert den Cache an zwei Speicherorten:

* **im Speicher:** Elemente werden für einen schnellen Zugriff im Speicher gespeichert. Der Arbeitsspeichercache hat eine begrenzte Größe und wird beim Neustart des Servers gelöscht.
* **auf der Festplatte:** Elemente werden im Dateisystem des Servers gespeichert. Der Datenträgercache verfügt über eine größere Kapazität als der Arbeitsspeichercache und wird beim Neustart des Servers beibehalten. Der Speicherort des Datenträgercache hängt von Ihrem Anwendungsserver ab. Informationen zum Ändern des Speicherorts des Datenträgercache finden Sie unter [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).

## Festlegen des Cache-Modus {#specifying-the-cache-mode}

Forms unterstützt zwei Modi der Zwischenspeicherung:

* unbedingter
* Verwenden des Cacheprüfpunkts

Wenn Sie zwischen den Cache-Modi wechseln, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

Die Cacheprüfpunkt-Zeit wird automatisch zurückgesetzt, wenn Sie zwischen den Modi wechseln.

### Unbedingte Zwischenspeicherung verwenden {#using-unconditional-caching}

In diesem Modus validiert der Forms-Dienst, wenn er eine Anforderung erhält, die erforderlichen Ressourcen (Formularentwurf und alle zugehörigen Assets wie Fragmente und Bilder). Der Forms-Dienst vergleicht den Zeitstempel der Ressourcen im Repository mit dem Zeitstempel der Ressourcen im Cache. Wenn die Ressource im Cache älter ist, wird sie vom Forms-Dienst aktualisiert.

Dieser Cache-Modus garantiert die Verwendung der neuesten Ressourcen. Die Leistung ist jedoch beeinträchtigt, da der Forms-Dienst die zwischengespeicherten Elemente bei jeder Anfrage gegen das Repository validiert. Dieser Cache-Modus eignet sich für Entwicklungs- und Staging-Umgebungen, in denen Ressourcen häufig aktualisiert werden und die Leistung kein Hauptproblem darstellt.

**Unbedingtes Caching angeben**

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Wählen Sie unter Forms Cache Control Settings die Option Unbedingter Zugriff und klicken Sie auf Save.

### Cacheprüfpunkt verwenden {#use-the-cache-check-point}

In diesem Modus überprüft der Forms-Dienst das Repository nur dann auf neuere Versionen von Ressourcen, wenn der Zeitstempel der zwischengespeicherten Ressource älter als die Cacheprüfpunkt-Zeit ist. Die letzte Cacheprüfpunkt-Zeit wird auf der Forms-Seite in Administration Console angezeigt.

Verwenden Sie diesen Cache-Modus in Produktionsumgebungen mit hoher Leistung, in denen die Leistung bedenklich ist und Änderungen an Ressourcen selten auftreten. Sie können die Cacheprüfpunkt-Zeit zurücksetzen, wenn Sie Änderungen an den Repository-Ressourcen bereitstellen möchten.

**Verwendung eines Cacheprüfpunkts festlegen**

1. Klicken Sie in Administration Console auf Dienste > Forms.
1. Wählen Sie unter &quot;Einstellungen für die Forms-Cache-Steuerung&quot;die Option Nur, wenn die letzte Validierung vor der Cacheprüfpunkt-Zeit durchgeführt wurde, und klicken Sie auf Speichern.

**Cache-Checkpoint zurücksetzen**

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Klicken Sie unter &quot;Forms Cache Control Settings&quot;auf Cache Check Point.

**Zurücksetzen des Cache-Inhalts**

Sie können den Inhalt des Caches jederzeit löschen. Nach dem Zurücksetzen des Caches ist die erste Anforderung für jedes Formular langsamer, da der Forms-Dienst eine vollständige Wiedergabe durchführt und neue Cache-Inhalte erstellt.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Klicken Sie unter &quot;Forms Cache Control Settings&quot;auf Cache zurücksetzen.

## Cache-Einstellungen konfigurieren {#configuring-cache-settings}

Sie können Einstellungen angeben, die Forms für die Zwischenspeicherung verwendet, um die Leistung Ihrer AEM Forms-Umgebung zu optimieren.

Um auf diese Einstellungen zuzugreifen, klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms&quot;.

>[!NOTE]
>
>Die Datenträgeranforderungen für den Cache sollten mit dem Repository übereinstimmen.

### Globale Cache-Einstellungen festlegen {#specifying-global-cache-settings}

Die Einstellungen in der **Globale Cache-Einstellungen** -Bereich wirkt sich auf alle Arten von Caches aus. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

**Max. Größe des Dokuments im Cache (KB):** Die maximale Größe (in Kilobyte) eines Formularentwurfs oder einer anderen Ressource, die in einem Arbeitsspeicher-Cache gespeichert werden kann. Dies ist eine globale Einstellung, die für alle speicherinternen Caches gilt. Wenn eine Ressource größer als dieser Wert ist, wird sie nicht im Speicher zwischengespeichert. Der Standardwert ist 1024 KB. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Formularwiedergabe mit aktiviertem Zwischenspeicher:** Diese Option ist standardmäßig aktiviert. Das bedeutet, dass die wiedergegebenen Formulare für spätere Abrufe zwischengespeichert werden. Diese Einstellung verbessert die Leistung, da der Forms-Dienst ein bestimmtes Formular nur einmal wiedergeben muss und dann die zwischengespeicherte Version verwendet. Diese Option funktioniert mit der Cache-Eigenschaft des Formularentwurfs. Informationen zum Konfigurieren dieses Wertes im Formularentwurf finden Sie in der Designer-Hilfe.

### Formularentwürfe zwischenspeichern {#caching-form-designs}

Wenn der Forms-Dienst eine Wiedergabeanforderung erhält, ruft er den Formularentwurf aus dem Repository ab und speichert ihn zwischen. Diese Zwischenspeicherung verbessert die Leistung, da der Forms-Service für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.

Der Forms-Dienst speichert Formularentwürfe immer auf dem Datenträger zwischen. Wenn Formularentwürfe auf dem Server gespeichert werden, werden diese Dateien als Datenträgercache betrachtet. Der Forms-Dienst speichert außerdem Formularentwürfe im Arbeitsspeicher zwischen, entsprechend der Einstellung in der **Im Speicher-Vorlagencache** Bereich. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

**Vorlagenkonfigurations-Cache-Größe:** Die maximale Anzahl von Vorlagenkonfigurationsobjekten, die im Arbeitsspeicher beibehalten werden sollen. Der Standardwert ist 100. Es wird empfohlen, diesen Wert größer oder gleich dem Wert der Vorlagencache-Größe festzulegen. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Vorlagen-Cache-Größe:** Die maximale Anzahl von Vorlageninhaltobjekten, die im Arbeitsspeicher behalten werden sollen. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist dieses Kontrollkästchen aktiviert. Das bedeutet, dass die Formularvorlagen im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht aktiviert ist, werden Formularvorlagen nur auf der Festplatte zwischengespeichert.

### Wiedergegebene Formulare zwischenspeichern {#caching-rendered-forms}

Der Forms-Dienst speichert wiedergegebene Formulare zwischen, sodass dasselbe Formular in nachfolgenden Anfragen nicht aufgelöst und wiedergegeben werden muss. Die wiedergegebenen Formulare werden sowohl auf dem Datenträger als auch im Arbeitsspeicher zwischengespeichert.

Diese Einstellungen befinden sich im **Im Arbeitsspeicherwiedergabe-Cache** Bereich. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

**Cache-Größe:** Gibt die maximale Anzahl wiedergegebener Formulare an, die sich im Arbeitsspeicher-Cache befinden können. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist diese Option aktiviert. Das bedeutet, dass die wiedergegebenen Formulare im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht ausgewählt ist, werden die wiedergegebenen Formulare nur auf dem Datenträger zwischengespeichert.

### Fragmente und Bilder zwischenspeichern {#caching-fragments-and-images}

Der Forms-Dienst speichert Fragmente und Bilder zwischen, die in Formularentwürfen auf dem Datenträger verwendet werden. Dies verbessert die Leistung, da die Fragmente und Bilder nur bei der ersten Anforderung aus dem Repository gelesen werden. Bei nachfolgenden Anfragen liest der Forms-Dienst dann Fragmente und Bilder aus dem Datenträgercache. Fragmente und Bilder werden nur auf dem Datenträger zwischengespeichert, nicht aber im Speicher.

Sie können die folgenden Einstellungen verwenden, um das Zwischenspeichern von Fragmenten und Bildern auf der Festplatte zu steuern. Diese Einstellungen befinden sich im **Cacheeinstellungen für Vorlagenressourcen** Bereich:

**Ressourcenzwischenspeicherung** Wählen Sie eine der folgenden Optionen aus der Liste aus:

**Aktiviert für Fragmente und Bilder:** Der Forms-Service speichert Fragmente und Bilder zwischen. Dies ist die Standardoption.

**Aktiviert für Fragmente:** Der Forms-Service speichert Fragmente, jedoch keine Bilder zwischen.

**Deaktiviert:** Der Forms-Service speichert weder Fragmente noch Bilder zwischen.

**Bereinigungsintervall (Sekunden):** Gibt an, wie oft der Forms-Service alte ungültige Cache-Dateien entfernen soll. Der Forms-Dienst entfernt keine gültigen Cache-Dateien. Wenn Sie das Bereinigungsintervall ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind. Der Standardwert ist 600 Sekunden.

## Clustering-Überlegungen für Caches {#clustering-considerations-for-caches}

In einer Clusterumgebung verwaltet jeder Knoten seinen eigenen Arbeitsspeicher- und Datenträgercache. Der Cache-Inhalt auf jedem Knoten hängt davon ab, welche Formulare auf diesem Knoten wiedergegeben wurden.

Der Speicherort des Caches muss auf jedem Knoten des Clusters identisch sein (derselbe Datenträger und Pfad). Platzieren Sie den Cache nicht auf dem freigegebenen Speicher.

Wenn Sie die Forms-Seite in Administration Console verwenden, um die Cache-Einstellungen für einen bestimmten Knoten zu ändern, werden die Cache-Einstellungen auf anderen Knoten aktualisiert, wenn eine Anforderung an diesen Knoten gesendet wird. Dieses Verhalten gilt auch für die Schaltfläche &quot;Cache zurücksetzen&quot;. Wenn Sie für einen Knoten auf die Schaltfläche Cache zurücksetzen klicken, wird der Cache sofort aus diesem Knoten entfernt. Der Cache auf anderen Knoten wird gelöscht, wenn eine Anfrage an diesen Knoten gesendet wird.
