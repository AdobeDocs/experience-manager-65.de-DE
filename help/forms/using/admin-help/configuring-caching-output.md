---
title: Konfigurieren der Zwischenspeicherung für die Ausgabe
description: Der Output-Dienst speichert die Formularentwürfe, Fragmente und Bilder zwischen. Erfahren Sie, wie Sie die Zwischenspeicherung für die Ausgabe konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1015f5c9-6ab8-4656-a5c8-40f82b9938b9
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1442'
ht-degree: 22%

---

# Konfigurieren der Zwischenspeicherung für die Ausgabe  {#configuring-caching-for-output}

Der Output-Dienst führt XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammen, um einen Dokumentausgabestream in verschiedenen Formaten zu erstellen.

Die Output-Seite in Administration Console enthält Einstellungen, die steuern, wie der Output-Dienst Elemente zwischenspeichert. Sie können diese Einstellungen anpassen, um die Leistung des Output-Dienstes zu optimieren.

Der Output-Dienst speichert die folgenden Elemente zwischen:

* **Formularentwürfe:** Der Output-Dienst speichert Formularentwürfe zwischen, die von dem Repository oder von HTTP-Quellen abgerufen werden. Diese Zwischenspeicherung verbessert die Leistung, da der Output-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.
* **Fragmente und Bilder:** Der Output-Dienst kann in Formularentwürfen verwendete Fragmente und Bilder zwischenspeichern. Wenn der Output-Dienst diese Objekte zwischenspeichert, wird die Leistung verbessert, da die Fragmente und Bilder nur bei der ersten Anforderung aus dem Repository gelesen werden.

Output speichert den Cache an zwei Speicherorten:

* **im Speicher:** Elemente werden für einen schnellen Zugriff im Speicher gespeichert. Der Arbeitsspeichercache hat eine begrenzte Größe und wird beim Neustart des Servers gelöscht.
* **auf der Festplatte:** Elemente werden im Dateisystem des Servers gespeichert. Der Datenträgercache verfügt über eine größere Kapazität als der Arbeitsspeichercache und wird beim Neustart des Servers beibehalten. Der Speicherort des Datenträgercache hängt von Ihrem Anwendungsserver ab. Informationen zum Ändern des Speicherorts des Datenträgercache finden Sie unter [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

## Festlegen des Cache-Modus {#specifying-the-cache-mode}

Output unterstützt zwei Modi der Zwischenspeicherung:

* unbedingter
* Verwenden des Cacheprüfpunkts

Wenn Sie zwischen den Cache-Modi wechseln, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

Die Cacheprüfpunkt-Zeit wird automatisch zurückgesetzt, wenn Sie zwischen den Modi wechseln.

### Unbedingte Zwischenspeicherung verwenden {#using-unconditional-caching}

Wenn der Output-Dienst in diesem Modus eine Anforderung erhält, validiert er die erforderlichen Ressourcen (Formularentwurf und alle zugehörigen Assets wie Fragmente und Bilder). Der Output-Dienst vergleicht den Zeitstempel der Ressourcen im Repository mit dem Zeitstempel der Ressourcen im Cache. Wenn die Ressource im Cache älter ist, aktualisiert der Output-Dienst sie.

Dieser Cache-Modus garantiert die Verwendung der neuesten Ressourcen. Die Leistung ist jedoch beeinträchtigt, da der Output-Dienst die zwischengespeicherten Elemente bei jeder Anfrage gegen das Repository validiert. Dieser Cache-Modus eignet sich für Entwicklungs- und Staging-Umgebungen, in denen Ressourcen häufig aktualisiert werden und die Leistung kein Hauptproblem darstellt.

**Unbedingtes Caching angeben**

1. Klicken Sie in der Administration-Console auf „Services“ > „Ausgabe“.
1. Wählen Sie unter &quot;Einstellungen für Output Cache Control&quot;die Option Unbedingter Zugriff und klicken Sie auf Speichern.

### Cacheprüfpunkt verwenden {#use-the-cache-check-point}

In diesem Modus überprüft der Output-Dienst das Repository nur dann auf neuere Versionen von Ressourcen, wenn der Zeitstempel der zwischengespeicherten Ressource älter als die Cacheprüfpunkt-Zeit ist. Die letzte Cacheprüfpunkt-Zeit wird auf der Seite &quot;Ausgabe&quot;in Administration Console angezeigt.

Verwenden Sie diesen Cache-Modus in Produktionsumgebungen mit hoher Leistung, in denen die Leistung bedenklich ist und Änderungen an Ressourcen selten auftreten. Sie können die Cacheprüfpunkt-Zeit zurücksetzen, wenn Sie Änderungen an den Repository-Ressourcen bereitstellen möchten.

**Verwendung eines Cacheprüfpunkts festlegen**

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Output&quot;.
1. Wählen Sie unter &quot;Einstellungen für die Ausgabe-Cache-Steuerung&quot;die Option Nur, wenn die letzte Validierung vor der Cacheprüfpunkt-Zeit durchgeführt wurde, und klicken Sie auf Speichern.

**Cache-Checkpoint zurücksetzen**

1. Klicken Sie in der Administration-Console auf „Services“ > „Ausgabe“.
1. Klicken Sie unter &quot;Output Cache Control Settings&quot;auf Cache Check Point.

### Zurücksetzen des Cache-Inhalts {#reset-the-cache-contents}

Sie können den Inhalt des Caches jederzeit löschen. Nach dem Zurücksetzen des Caches ist die erste Anforderung für jedes Formular langsamer, da der Output-Dienst eine vollständige Wiedergabe durchführt und neue Cache-Inhalte erstellt.

1. Klicken Sie in der Administration-Console auf „Services“ > „Ausgabe“.
1. Klicken Sie unter &quot;Einstellungen der Output Cache Control&quot;auf Cache zurücksetzen.

## Cache-Einstellungen konfigurieren {#configuring-cache-settings}

Sie können Einstellungen angeben, die Output für die Zwischenspeicherung verwendet, um die Leistung Ihrer AEM Forms-Umgebung zu optimieren.

Um auf diese Einstellungen zuzugreifen, klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Output&quot;.

>[!NOTE]
>
>Die Datenträgeranforderungen für den Cache sollten mit dem Repository übereinstimmen.

### Globale Cache-Einstellungen festlegen {#specifying-global-cache-settings}

Die Einstellungen in der **Globale Cache-Einstellungen** -Bereich wirkt sich auf alle Arten von Caches aus. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

**Max. Größe des Dokuments im Cache (KB):** Die maximale Größe (in Kilobyte) eines Formularentwurfs oder einer anderen Ressource, die in einem Arbeitsspeicher-Cache gespeichert werden kann. Dies ist eine globale Einstellung, die für alle speicherinternen Caches gilt. Wenn die Ressource größer als dieser Wert ist, wird sie nicht im Speicher zwischengespeichert. Der Standardwert ist 1024 KB. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Formularwiedergabe mit aktiviertem Zwischenspeicher**: Diese Option ist standardmäßig ausgewählt. Das bedeutet, dass die wiedergegebenen Formulare für spätere Abrufe zwischengespeichert werden. Diese Einstellung hat geringe Auswirkungen auf die Leistung des Output-Dienstes, da nicht interaktive Dokumente nicht zwischengespeichert werden. Diese Option wirkt sich nicht aus, wenn Sie den Output-Dienst für nicht interaktive Dokumente verwenden, die auf dem Client wiedergegeben werden.

### Formularentwürfe zwischenspeichern {#caching-form-designs}

Wenn der Output-Dienst eine Wiedergabeanforderung erhält, ruft er den Formularentwurf aus dem Repository oder aus einer HTTP-Quelle ab und speichert ihn zwischen. Diese Zwischenspeicherung verbessert die Leistung, da der Ausgabe-Service für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.

Der Output-Dienst speichert Formularentwürfe immer auf dem Datenträger zwischen. Wenn Formularentwürfe auf dem Server gespeichert werden, werden diese Dateien als Datenträgercache betrachtet. Der Output-Dienst speichert außerdem Formularentwürfe im Arbeitsspeicher zwischen, entsprechend der Einstellung in der **Im Speicher-Vorlagencache** Bereich. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Um diesen Dienst neu zu starten, verwenden Sie entweder Workbench oder lesen Sie [Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) für Anweisungen.

**Vorlagenkonfigurations-Cache-Größe:** Die maximale Anzahl von Vorlagenkonfigurationsobjekten, die im Arbeitsspeicher beibehalten werden sollen. Der Standardwert ist 100. Es wird empfohlen, diesen Wert größer oder gleich dem Wert der Vorlagencache-Größe festzulegen. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Vorlagen-Cache-Größe:** Die maximale Anzahl von Vorlageninhaltobjekten, die im Arbeitsspeicher behalten werden sollen. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist dieses Kontrollkästchen aktiviert. Das bedeutet, dass die Formularvorlagen im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht aktiviert ist, werden Formularvorlagen nur auf der Festplatte zwischengespeichert.

### Fragmente und Bilder zwischenspeichern {#caching-fragments-and-images}

Der Output-Dienst speichert Fragmente und Bilder zwischen, die in Formularentwürfen auf dem Datenträger verwendet werden. Dies verbessert die Leistung, da die Fragmente und Bilder nur bei der ersten Anforderung aus dem Repository gelesen werden. Bei nachfolgenden Anforderungen liest der Output-Dienst dann Fragmente und Bilder aus dem Datenträgercache. Fragmente und Bilder werden nur auf dem Datenträger zwischengespeichert, nicht aber im Speicher.

Sie können die folgenden Einstellungen verwenden, um das Zwischenspeichern von Fragmenten und Bildern auf der Festplatte zu steuern. Diese Einstellungen befinden sich im **Cacheeinstellungen für Vorlagenressourcen** Bereich:

**Ressourcenzwischenspeicherung** Wählen Sie eine der folgenden Optionen aus der Liste aus:

**Aktiviert für Fragmente und Bilder**: Der Ausgabe-Service speichert Fragmente und Bilder zwischen. Dies ist die Standardoption.

**Aktiviert für Fragmente**: Der Ausgabe-Service speichert Fragmente zwischen, jedoch keine Bilder.

**Deaktiviert**: Der Ausgabe-Service speichert weder Fragmente noch Bilder zwischen.

**Bereinigungsintervall (Sekunden)**: Gibt an, wie oft der Ausgabe-Service alte, ungültige Cache-Dateien entfernen soll. Der Output-Dienst entfernt keine gültigen Cache-Dateien. Wenn Sie das Bereinigungsintervall ändern, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind.

## Clustering-Überlegungen für Caches {#clustering-considerations-for-caches}

In einer Clusterumgebung verwaltet jeder Knoten seinen eigenen Arbeitsspeicher- und Datenträgercache. Der Cache-Inhalt auf jedem Knoten hängt davon ab, welche Formulare auf diesem Knoten wiedergegeben wurden.

Der Speicherort des Caches muss auf jedem Knoten des Clusters identisch sein (derselbe Datenträger und Pfad). Platzieren Sie den Cache nicht auf dem freigegebenen Speicher.

Wenn Sie die Output-Seite in Administration Console verwenden, um die Cache-Einstellungen für einen bestimmten Knoten zu ändern, werden die Cache-Einstellungen auf anderen Knoten aktualisiert, wenn eine Anforderung an diesen Knoten gesendet wird. Dieses Verhalten gilt auch für die Schaltfläche &quot;Cache zurücksetzen&quot;. Wenn Sie für einen Knoten auf die Schaltfläche Cache zurücksetzen klicken, wird der Cache sofort aus diesem Knoten entfernt. Der Cache auf anderen Knoten wird gelöscht, wenn eine Anfrage an diesen Knoten gesendet wird.
