---
title: Konfigurieren der Zwischenspeicherung für Forms
description: Erfahren Sie, wie Sie Cache-Einstellungen konfigurieren und wie Sie Überlegungen zum Cache gruppieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6b57d00e-5ba0-41ee-8497-49ecfec5b9ed
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1611'
ht-degree: 100%

---

# Konfigurieren der Zwischenspeicherung für Forms{#configuring-caching-for-forms}

Der Forms-Dienst nimmt Formularentwürfe, die in Designer erstellt wurden, und gibt sie in verschiedenen Formaten wieder.

Die Forms-Seite in der Administrationskonsole enthält Einstellungen, die steuern, wie der Forms-Dienst Elemente zwischenspeichert. Sie können diese Einstellungen anpassen, um die Leistung des Forms-Dienstes zu optimieren.

Der Forms-Dienst speichert die folgenden Elemente zwischen:

* **Formularentwürfe:** Der Forms-Dienst speichert Formularentwürfe zwischen, die von dem Repository oder von HTTP-Quellen abgerufen werden. Diese Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.
* **Fragmente und Bilder:** Der Forms-Dienst kann in Formularentwürfen verwendete Fragmente und Bilder zwischenspeichern. Wenn der Forms-Dienst diese Objekte zwischenspeichert, wird die Leistung verbessert, da die Fragmente und Bilder nur bei der ersten Anforderung vom Repository gelesen werden.
* **Formulare:** Der Forms-Dienst speichert die wiedergegebenen Formulare zwischen. Diese Art der Zwischenspeicherung verbessert die Leistung, da der Forms-Dienst dasselbe Formular in nachfolgenden Anforderungen nicht auflösen und wiedergeben muss.

Forms speichert den Zwischenspeicher an zwei Speicherorten:

* **Im Arbeitsspeicher:** Elemente werden für schnellen Zugriff im Arbeitsspeicher gespeichert. Der Arbeitsspeicher-Cache hat eine begrenzte Größe und wird beim Neustart des Servers gelöscht.
* **Auf einem Datenträger:** Elemente werden auf dem Dateisystem des Servers gespeichert. Der Datenträger-Cache verfügt über eine größere Kapazität als der Arbeitsspeicher-Cache und wird beim Neustart des Servers beibehalten. Der Speicherort des Datenträger-Cache hängt von Ihrem Anwendungs-Server ab. Informationen zum Ändern des Speicherorts des Datenträger-Cache finden Sie unter [Konfigurieren von Speicherorten für Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).

## Angeben des Cache-Modus {#specifying-the-cache-mode}

Forms unterstützt zwei Modi der Zwischenspeicherung:

* unbedingt
* unter Verwendung des Cache-Prüfpunkts

Wenn Sie zwischen den Cache-Modi wechseln, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

Die Cache-Prüfpunkt-Zeit wird automatisch zurückgesetzt, wenn Sie zwischen den Modi wechseln.

### Verwendung von unbedingter Zwischenspeicherung {#using-unconditional-caching}

In diesem Modus überprüft der Forms-Dienst die erforderlichen Ressourcen (Formularentwurf und andere zugehörige Elemente wie Fragmente und Bilder), wenn er eine Anforderung erhält. Der Forms-Dienst vergleicht den Zeitstempel der Ressourcen im Repository mit dem Zeitstempel der Ressourcen im Cache. Wenn die Ressource im Cache älter ist, wird sie vom Forms-Dienst aktualisiert.

Dieser Cache-Modus garantiert die Verwendung der neuesten Ressourcen. Die Leistung ist jedoch beeinträchtigt, da der Forms-Dienst bei jeder Anfrage die zwischengespeicherten Elemente gegen das Repository validiert. Dieser Cache-Modus eignet sich für Entwicklungs- und Staging-Umgebungen, in denen Ressourcen häufig aktualisiert werden und die Leistung kein Hauptproblem darstellt.

**Angeben von unbedingter Zwischenspeicherung**

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Wählen Sie unter „Einstellungen für die Forms-Cache-Steuerung“ die Option „Unbedingt“ aus und klicken Sie auf „Speichern“.

### Verwenden des Cache-Prüfpunkts {#use-the-cache-check-point}

In diesem Modus überprüft der Forms-Dienst das Repository nur dann auf eine neuere Version der Ressourcen, wenn der Zeitstempel der zwischengespeicherten Ressourcen vor der Zeit des Cache-Prüfpunkts liegt. Die letzte Cache-Prüfpunkt-Zeit wird auf der Forms-Seite in der Administrationskonsole angezeigt.

Verwenden Sie diesen Cache-Modus in leistungsintensiven Produktionsumgebungen, die Leistung wichtig ist und Änderungen an den Ressourcen nicht häufig vorkommen. Sie können die Cache-Prüfpunkt-Zeit zurücksetzen, wenn Sie Änderungen an den Repository-Ressourcen implementieren möchten.

**Festlegen der Verwendung eines Cache-Prüfpunkts**

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms“.
1. Aktivieren Sie in den Einstellungen für die Forms-Cache-Steuerung die Option „Nur wenn die letzte Validierung vor der Cache-Prüfpunkt-Zeit ausgeführt wurde“ und klicken Sie auf „Speichern“.

**Zurücksetzen des Cache-Prüfpunkts**

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Klicken Sie in den Einstellungen für die Forms-Cache-Steuerung auf die Option „Cache-Prüfpunkt“.

**Zurücksetzen des Cache-Inhalts**

Sie können den Inhalt des Cache jederzeit löschen. Nach dem Zurücksetzen des Cache ist die erste Anfrage für jedes Formular langsamer, da der Forms-Dienst eine vollständige Wiedergabe ausführt und neue Inhalte für den Zwischenspeicher erstellt.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Klicken Sie in den Einstellungen für die Forms-Cache-Steuerung auf die Option „Cache zurücksetzen“.

## Konfigurieren der Cache-Einstellungen {#configuring-cache-settings}

Sie können Eigenschaften festlegen, die von Forms für die Zwischenspeicherung verwendet werden und die die Leistung der AEM Forms-Umgebung optimieren können.

Klicken Sie zum Zugreifen auf diese Einstellungen in der Administrationskonsole auf „Dienste“ > „Forms“.

>[!NOTE]
>
>Die Datenträgeranforderungen für den Cache sollten mit dem Repository übereinstimmen.

### Festlegen von globalen Cache-Einstellungen {#specifying-global-cache-settings}

Die Einstellungen im Bereich **Globale Cache-Einstellungen** wirken sich auf alle Cache-Typen aus. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Max. Größe des Dokuments im Cache (KB):** Die maximale Größe (in Kilobyte) eines Formularentwurfs oder einer anderen Ressource, die in einem Arbeitsspeicher-Cache gespeichert werden kann. Dies ist eine globale Einstellung, die für alle Arbeitsspeicher-Caches gilt. Wenn eine Ressource größer als dieser Wert ist, wird sie nicht im Arbeitsspeicher zwischengespeichert. Der Standardwert ist 1024 KB. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Formularwiedergabe mit aktiviertem Zwischenspeicher:** Diese Option ist standardmäßig aktiviert. Das bedeutet, dass die wiedergegebenen Formulare für spätere Abrufe zwischengespeichert werden. Diese Einstellung verbessert die Leistung, da der Forms-Dienst ein bestimmtes Formular nur einmal wiedergeben muss und dann die zwischengespeicherte Version verwendet. Diese Option funktioniert mit der Cache-Eigenschaft des Formularentwurfs. Informationen zum Konfigurieren dieses Wertes im Formularentwurf finden Sie in der Designer-Hilfe.

### Zwischenspeichern von Formularentwürfen {#caching-form-designs}

Wenn der Forms-Dienst eine Render-Anfrage erhält, ruft er den Formularentwurf aus dem Repository ab und speichert ihn zwischen. Diese Zwischenspeicherung verbessert die Leistung, da der Forms-Service für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.

Der Forms-Dienst speichert Formularentwürfe immer auf einem Datenträger zwischen. Wenn Formularentwürfe auf dem Server gespeichert werden, werden diese Dateien als Datenträger-Cache betrachtet. Der Forms-Dienst speichert außerdem Formularentwürfe im Arbeitsspeicher zwischen, entsprechend der Einstellung im Bereich **Arbeitsspeicher-Vorlagen-Cache**. Wenn Sie eine dieser Einstellungen ändern, müssen Sie den Forms-Dienst neu starten, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench oder folgen Sie den Anweisungen unter [Starten oder Beenden von Diensten, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Vorlagenkonfigurations-Cache-Größe:** Die maximale Anzahl von Vorlagenkonfigurationsobjekten, die im Arbeitsspeicher beibehalten werden sollen. Der Standardwert ist 100. Es wird empfohlen, diesen Wert größer oder gleich dem Wert der Vorlagen-Cache-Größe festzulegen. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Vorlagen-Cache-Größe:** Die maximale Anzahl von Vorlageninhaltobjekten, die im Arbeitsspeicher behalten werden sollen. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist dieses Kontrollkästchen aktiviert. Das bedeutet, dass die Formularvorlagen im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht aktiviert ist, werden Formularvorlagen nur auf der Festplatte zwischengespeichert.

### Zwischenspeichern von wiedergegebenen Formularen {#caching-rendered-forms}

Der Forms-Dienst speichert wiedergegebene Formulare zwischen, sodass dasselbe Formular in nachfolgenden Anfragen nicht aufgelöst und wiedergegeben werden muss. Die wiedergegebenen Formulare werden sowohl auf einem Datenträger als auch im Arbeitsspeicher zwischengespeichert.

Diese Einstellungen befinden sich im Bereich **Arbeitspeicher-Formularwiedergabe-Cache**. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Forms-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench oder folgen Sie den Anweisungen unter [Starten oder Beenden von Diensten, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Cache-Größe:** Gibt die maximale Anzahl wiedergegebener Formulare an, die sich im Arbeitsspeicher-Cache befinden können. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist diese Option aktiviert. Das bedeutet, dass die wiedergegebenen Formulare im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht ausgewählt ist, werden die wiedergegebenen Formulare nur auf dem Datenträger zwischengespeichert.

### Zwischenspeichern von Fragmenten und Bildern {#caching-fragments-and-images}

Der Forms-Dienst speichert Fragmente und Bilder zwischen, die in Formularentwürfen auf dem Datenträger verwendet werden. Dadurch wird die Leistung verbessert, weil die Fragmente und Bilder nur bei der ersten Anforderung aus dem Repository gelesen werden. Bei nachfolgenden Anforderungen liest der Forms-Dienst anschließend die Fragmente und Bilder aus dem Datenträgercache. Fragmente und Bilder werden nur auf dem Datenträger zwischengespeichert und nicht im Arbeitsspeicher.

Sie können die folgenden Einstellungen verwenden, um die Zwischenspeicherung von Fragmenten und Bildern auf dem Datenträger zu steuern. Diese Einstellungen befinden sich im Bereich **Cache-Einstellungen für Vorlagenressourcen**:

**Ressourcenzwischenspeicherung** Wählen Sie eine der folgenden Optionen aus der Liste aus:

**Aktiviert für Fragmente und Bilder:** Der Forms-Service speichert Fragmente und Bilder zwischen. Dies ist die Standardoption.

**Aktiviert für Fragmente:** Der Forms-Service speichert Fragmente, jedoch keine Bilder zwischen.

**Deaktiviert:** Der Forms-Service speichert weder Fragmente noch Bilder zwischen.

**Bereinigungsintervall (Sekunden):** Gibt an, wie oft der Forms-Service alte ungültige Cache-Dateien entfernen soll. Der Forms-Dienst entfernt keine gültigen Cache-Dateien. Wenn Sie das Bereinigungsintervall ändern, müssen Sie den Forms-Dienst neu starten, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind. Der Standardwert ist 600 Sekunden.

## Clustering-Überlegungen zum Zwischenspeicher {#clustering-considerations-for-caches}

In einer Cluster-Umgebung verwaltet jeder Knoten seinen eigenen Arbeitsspeicher- und Datenträger-Cache. Der Inhalt des Zwischenspeichers auf jedem Knoten hängt davon ab, welche Formulare auf diesem Knoten wiedergegeben wurden.

Der Speicherort des Zwischenspeichers muss auf jedem Knoten des Clusters identisch sein (derselbe Datenträger und Pfad). Legen Sie den Zwischenspeicher nicht auf einem freigegebenen Speicher an.

Wenn Sie die Forms-Seite in der Administrationskonsole verwenden, um die Cache-Einstellungen für einen bestimmten Knoten zu ändern, werden die Cache-Einstellungen bei einer Anfrage an diesen Knoten auch auf anderen Knoten aktualisiert. Dieses Verhalten gilt auch für die Schaltfläche „Cache zurücksetzen“. Wenn Sie auf die Schaltfläche „Cache zurücksetzen“ für einen Knoten klicken, wird der Zwischenspeicher sofort von diesem Knoten gelöscht. Der Zwischenspeicher auf anderen Knoten wird bei einer Anfrage an diesen Knoten gelöscht.
