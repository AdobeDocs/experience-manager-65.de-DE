---
title: Konfigurieren der Zwischenspeicherung für die Ausgabe
description: Der Output-Dienst speichert Formularentwürfe, Fragmente und Bilder zwischen. Erfahren Sie, wie Sie die Zwischenspeicherung für die Ausgabe konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1015f5c9-6ab8-4656-a5c8-40f82b9938b9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1442'
ht-degree: 100%

---

# Konfigurieren der Zwischenspeicherung für die Ausgabe  {#configuring-caching-for-output}

Der Output-Dienst führt XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammen, um einen Dokumentausgabe-Stream in einer Vielzahl von Formaten zu erstellen.

Die Output-Seite in der Administrationskonsole enthält Einstellungen, die steuern, wie der Output-Dienst Elemente zwischenspeichert. Sie können diese Einstellungen anpassen, um die Leistung des Output-Dienstes zu optimieren.

Der Output-Dienst führt für die folgenden Elemente eine Zwischenspeicherung aus:

* **Formularentwürfe:** Der Output-Dienst speichert Formularentwürfe zwischen, die von dem Repository oder von HTTP-Quellen abgerufen werden. Diese Zwischenspeicherung verbessert die Leistung, da der Output-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.
* **Fragmente und Bilder:** Der Output-Dienst kann in Formularentwürfen verwendete Fragmente und Bilder zwischenspeichern. Wenn der Output-Dienst diese Objekte zwischenspeichert, wird die Leistung verbessert, da die Fragmente und Bilder nur bei der ersten Anfrage vom Repository gelesen werden.

Output speichert den Cache an zwei Orten:

* **Im Arbeitsspeicher:** Elemente werden zwecks Schnellzugriffs im Arbeitsspeicher gespeichert. Der Arbeitsspeicher-Cache hat eine begrenzte Größe und wird beim Neustart des Servers gelöscht.
* **Auf einem Datenträger:** Elemente werden auf dem Dateisystem des Servers gespeichert. Der Datenträger-Cache verfügt über eine größere Kapazität als der Arbeitsspeicher-Cache und wird beim Neustart des Servers beibehalten. Der Speicherort des Datenträger-Cache hängt von Ihrem Anwendungs-Server ab. Weitere Informationen zum Ändern des Speicherorts des Datenträger-Caches finden Sie unter [Angeben der Dateispeicherorte für die Ausgabe](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

## Angeben des Cache-Modus {#specifying-the-cache-mode}

Output unterstützt zwei Modi für die Zwischenspeicherung:

* unbedingt
* unter Verwendung des Cache-Prüfpunkts

Wenn Sie zwischen den Cache-Modi wechseln, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench oder folgen Sie den Anweisungen unter [Starten oder Beenden von Diensten, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

Die Cache-Prüfpunkt-Zeit wird automatisch zurückgesetzt, wenn Sie zwischen den Modi wechseln.

### Verwendung von unbedingter Zwischenspeicherung {#using-unconditional-caching}

In diesem Modus überprüft der Output-Dienst die erforderlichen Ressourcen (Formularentwurf und andere zugehörige Assets wie Fragmente und Bilder), wenn er eine Anfrage erhält. Der Output-Dienst vergleicht den Zeitstempel der Ressourcen im Repository mit dem Zeitstempel der Ressourcen im Cache. Ist die Ressource im Cache älter, führt der Output-Dienst eine Aktualisierung durch.

Dieser Cache-Modus garantiert die Verwendung der neuesten Ressourcen. Jedoch hat dies Auswirkungen auf die Leistung, da der Output-Dienst die zwischengespeicherten Elemente bei jeder Anfrage mit dem Repository abgleicht. Dieser Cache-Modus eignet sich für Entwicklungs- und Staging-Umgebungen, in denen Ressourcen häufig aktualisiert werden und die Leistung kein Hauptproblem darstellt.

**Angeben von unbedingter Zwischenspeicherung**

1. Klicken Sie in der Administration-Console auf „Services“ > „Ausgabe“.
1. Wählen Sie unter „Einstellungen für die Ausgabe-Cache-Steuerung“ die Option „Bedingungslos“ aus und klicken Sie auf „Speichern“.

### Verwenden des Cache-Prüfpunkts {#use-the-cache-check-point}

In diesem Modus überprüft der Output-Dienst das Repository nur dann auf eine neuere Version der Ressourcen, wenn der Zeitstempel der zwischengespeicherten Ressourcen vor der Cache-Prüfpunktzeit liegt. Die letzte Cache-Prüfpunktzeit wird auf der Output-Seite in der Administrationskonsole angezeigt.

Verwenden Sie diesen Cache-Modus in leistungsintensiven Produktionsumgebungen, die Leistung wichtig ist und Änderungen an den Ressourcen nicht häufig vorkommen. Sie können die Cache-Prüfpunkt-Zeit zurücksetzen, wenn Sie Änderungen an den Repository-Ressourcen implementieren möchten.

**Festlegen der Verwendung eines Cache-Prüfpunkts**

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Ausgabe“.
1. Aktivieren Sie unter „Einstellungen für die Ausgabe-Cache-Steuerung“ die Option „Nur wenn die letzte Validierung vor der Cache-Prüfpunktzeit ausgeführt wurde“ und klicken Sie auf „Speichern“.

**Zurücksetzen des Cache-Prüfpunkts**

1. Klicken Sie in der Administration-Console auf „Services“ > „Ausgabe“.
1. Klicken Sie unter „Einstellungen für die Ausgabe-Cache-Steuerung“ auf die Option „Cache-Prüfpunkt“.

### Zurücksetzen des Cache-Inhalts {#reset-the-cache-contents}

Sie können den Inhalt des Cache jederzeit löschen. Nach dem Zurücksetzen des Caches ist die erste Anfrage für jedes Formular langsamer, da der Output-Dienst einen vollständigen Render-Vorgang ausführt und neue Inhalte für den Cache erstellt.

1. Klicken Sie in der Administration-Console auf „Services“ > „Ausgabe“.
1. Klicken Sie unter „Einstellungen für die Ausgabecache-Steuerung“ auf die Option „Cache zurücksetzen“.

## Konfigurieren der Cache-Einstellungen {#configuring-cache-settings}

Sie können Eigenschaften festlegen, die von der Ausgabe für das Cashing verwendet werden und die die Leistung der AEM Forms-Umgebung optimieren können.

Klicken Sie zum Zugreifen auf diese Einstellungen in der Administrationskonsole auf „Dienste“ > „Ausgabe“.

>[!NOTE]
>
>Die Datenträgeranforderungen für den Cache sollten mit dem Repository übereinstimmen.

### Festlegen von globalen Cache-Einstellungen {#specifying-global-cache-settings}

Die Einstellungen im Bereich **Globale Cache-Einstellungen** wirken sich auf alle Cache-Typen aus. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Ausgabe-Service neu, damit die Änderung wirksam wird.  Verwenden Sie zum Neustart dieses Dienstes entweder Workbench oder folgen Sie den Anweisungen unter [Starten oder Beenden von Diensten, denen AEM Forms-Module zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules). 

**Max. Größe des Dokuments im Cache (KB):** Die maximale Größe (in Kilobyte) eines Formularentwurfs oder einer anderen Ressource, die in einem Arbeitsspeicher-Cache gespeichert werden kann. Dies ist eine globale Einstellung, die für alle Arbeitsspeicher-Caches gilt. Wenn die Ressource größer als dieser Wert ist, wird sie nicht im Arbeitsspeicher zwischengespeichert.  Der Standardwert ist 1024 KB. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Formularwiedergabe mit aktiviertem Zwischenspeicher**: Diese Option ist standardmäßig ausgewählt. Das bedeutet, dass die wiedergegebenen Formulare für spätere Abrufe zwischengespeichert werden. Diese Einstellung hat wenig Auswirkungen auf die Leistung des Ausgabe-Service, da keine nicht-interaktiven Dokumente zwischengespeichert werden.  Diese Option hat eine Auswirkung, wenn Sie den Ausgabe-Service für nicht interaktive Dokumente verwenden, die auf dem Client wiedergegeben werden.

### Zwischenspeichern von Formularentwürfen {#caching-form-designs}

Wenn der Ausgabe-Service eine Wiedergabeanforderung erhält, werden die Formularentwürfe aus dem Repository oder aus einer HTTP-Quelle abgerufen und zwischengespeichert.  Diese Zwischenspeicherung verbessert die Leistung, da der Ausgabe-Service für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.

Der Ausgabe-Service speichert Formularentwürfe immer auf dem Datenträger zwischen.  Wenn Formularentwürfe auf dem Server gespeichert werden, werden diese Dateien als Datenträger-Cache betrachtet. Der Ausgabe-Service speichert außerdem Formularentwürfe im Arbeitsspeicher zwischen, gemäß der Einstellung im Bereich **Arbeitsspeicher-Cache für Vorlagenkonfiguration**. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Ausgabe-Service neu, damit die Änderung wirksam wird.  Verwenden Sie zum Neustart dieses Dienstes entweder Workbench oder folgen Sie den Anweisungen unter [Starten oder Beenden von Diensten, denen AEM Forms-Module zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Vorlagenkonfigurations-Cache-Größe:** Die maximale Anzahl von Vorlagenkonfigurationsobjekten, die im Arbeitsspeicher beibehalten werden sollen. Der Standardwert ist 100. Es wird empfohlen, diesen Wert größer oder gleich dem Wert der Vorlagen-Cache-Größe festzulegen. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Vorlagen-Cache-Größe:** Die maximale Anzahl von Vorlageninhaltobjekten, die im Arbeitsspeicher behalten werden sollen. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert:** Standardmäßig ist dieses Kontrollkästchen aktiviert. Das bedeutet, dass die Formularvorlagen im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht aktiviert ist, werden Formularvorlagen nur auf der Festplatte zwischengespeichert.

### Zwischenspeichern von Fragmenten und Bildern {#caching-fragments-and-images}

Der Ausgabe-Service speichert Fragmente und Bilder, die in Formularentwürfen auf dem Datenträger verwendet werden, zwischen.  Dadurch wird die Leistung verbessert, weil die Fragmente und Bilder nur bei der ersten Anforderung aus dem Repository gelesen werden. Bei nachfolgenden Anforderungen liest der Ausgabe-Service anschließend die Fragmente und Bilder vom Datenträgercache.  Fragmente und Bilder werden nur auf dem Datenträger zwischengespeichert und nicht im Arbeitsspeicher.

Sie können die folgenden Einstellungen verwenden, um die Zwischenspeicherung von Fragmenten und Bildern auf dem Datenträger zu steuern. Diese Einstellungen befinden sich im Bereich **Cache-Einstellungen für Vorlagenressourcen**:

**Ressourcenzwischenspeicherung** Wählen Sie eine der folgenden Optionen aus der Liste aus:

**Aktiviert für Fragmente und Bilder**: Der Ausgabe-Service speichert Fragmente und Bilder zwischen. Dies ist die Standardoption.

**Aktiviert für Fragmente**: Der Ausgabe-Service speichert Fragmente zwischen, jedoch keine Bilder.

**Deaktiviert**: Der Ausgabe-Service speichert weder Fragmente noch Bilder zwischen.

**Bereinigungsintervall (Sekunden)**: Gibt an, wie oft der Ausgabe-Service alte, ungültige Cache-Dateien entfernen soll. Der Ausgabe-Service entfernt keine gültigen Cache-Dateien.  Wenn Sie das Bereinigungsintervall ändern, starten Sie den Ausgabe-Service neu, damit die Änderung wirksam wird.  Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind.

## Clustering-Überlegungen zum Zwischenspeicher {#clustering-considerations-for-caches}

In einer Cluster-Umgebung verwaltet jeder Knoten seinen eigenen Arbeitsspeicher- und Datenträger-Cache. Der Inhalt des Zwischenspeichers auf jedem Knoten hängt davon ab, welche Formulare auf diesem Knoten wiedergegeben wurden.

Der Speicherort des Zwischenspeichers muss auf jedem Knoten des Clusters identisch sein (derselbe Datenträger und Pfad). Legen Sie den Zwischenspeicher nicht auf einem freigegebenen Speicher an.

Wenn Sie die Seite „Ausgabe“ in der Administrationskonsole verwenden, um die Cache-Einstellungen für einen bestimmten Knoten zu ändern, werden die Cache-Einstellungen bei einer Anforderung an diesen Knoten auch auf anderen Knoten aktualisiert. Dieses Verhalten gilt auch für die Schaltfläche „Cache zurücksetzen“. Wenn Sie auf die Schaltfläche „Cache zurücksetzen“ für einen Knoten klicken, wird der Zwischenspeicher sofort von diesem Knoten gelöscht. Der Zwischenspeicher auf anderen Knoten wird bei einer Anfrage an diesen Knoten gelöscht.
