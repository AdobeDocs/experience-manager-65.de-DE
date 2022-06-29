---
title: Zwischenspeicherung für Output konfigurieren
seo-title: Configuring caching for Output
description: Der Ausgabe-Dienst speichert Formulardesigns, -fragmente und Bilder. Erfahren Sie, wie Sie die Zwischenspeicherung für die Ausgabe konfigurieren.
seo-description: The Output service caches the form designs, fragments and images. Learn how to configure the caching for output.
uuid: 00bffeb5-c9c4-4a46-98b5-e14ec9f4514e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e5398abd-f62c-485d-9f4b-a316c0de2b6b
exl-id: 1015f5c9-6ab8-4656-a5c8-40f82b9938b9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1440'
ht-degree: 100%

---

# Zwischenspeicherung für Output konfigurieren  {#configuring-caching-for-output}

Der Output-Dienst führt XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammen, um einen Dokumentausgabestream in einer Vielzahl von Formaten zu erstellen.

Die Output-Seite in Administration Console enthält Einstellungen, die steuern, wie der Output-Dienst Elemente zwischenspeichert. Sie können diese Einstellungen anpassen, um die Leistung des Output-Dienstes zu optimieren.

Der Output-Dienst führt für die folgenden Elemente eine Zwischenspeicherung aus:

* **Formularentwürfe:** Der Output-Dienst speichert Formularentwürfe zwischen, die von dem Repository oder von HTTP-Quellen abgerufen werden. Diese Zwischenspeicherung verbessert die Leistung, da der Output-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.
* **Fragmente und Bilder:** Der Output-Dienst kann in Formularentwürfen verwendete Fragmente und Bilder zwischenspeichern. Wenn der Output-Dienst diese Objekte zwischenspeichert, wird die Leistung verbessert, da die Fragmente und Bilder nur bei der ersten Anforderung vom Repository gelesen werden.

Output speichert den Zwischenspeicher an zwei Speicherorten:

* **Im Arbeitsspeicher:** Elemente werden für schnellen Zugriff im Arbeitsspeicher gespeichert. Der Arbeitsspeichercache verfügt über eine begrenzte Größe und wir beim Neustart des Servers gelöscht.
* **Auf einem Datenträger:** Elemente werden im Dateisystem des Servers gespeichert. Der Datenträgercache verfügt über eine größere Kapazität als der Arbeitsspeichercache und er wird beim Neustart des Servers beibehalten. Der Speicherort des Datenträgercache hängt von Ihrem Anwendungsserver ab. Weitere Informationen zum Ändern des Speicherorts des Datenträger-Caches finden Sie unter [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

## Cachemodus angeben {#specifying-the-cache-mode}

Output unterstützt zwei Modi für die Zwischenspeicherung:

* nicht konditional
* unter Verwendung des Cacheprüfpunkts

Wenn Sie zwischen den Cachemodi wechseln, starten Sie den Output -Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

Die Cacheprüfpunkt-Zeit wird beim Wechsel zwischen den Modi automatisch zurückgesetzt.

### Nicht konditionale Zwischenspeicherung verwenden {#using-unconditional-caching}

In diesem Modus überprüft der Output-Dienst die erforderlichen Ressourcen (Formularentwurf und andere zugehörige Elemente wie Fragmente und Bilder), wenn er eine Anforderung erhält. Der Output-Dienst vergleicht den Zeitstempel der Ressourcen im Repository mit dem Zeitstempel der Ressourcen im Cache. Ist die Ressource im Cache älter, wird dieser vom Output-Dienst aktualisiert.

Dieser Cache-Modus gewährleistet, dass die neuesten Ressourcen verwendet werden. Jedoch hat dies Auswirkungen auf die Leistung, da der Output-Dienst die zwischengespeicherten Elemente bei jeder Anforderung gegen das Repository überprüft. Dieser Cache-Modus ist für Entwicklungs- und Testumgebungen geeignet, in denen Ressourcen häufig aktualisiert werden und die Leistung nicht am wichtigsten ist.

**Nicht konditionale Zwischenspeicherung angeben**

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Wählen Sie unter „Einstellungen für die Ausgabecache-Steuerung“ die Option „Bedingungslos“ aus und klicken Sie auf „Speichern“.

### Den Cacheprüfpunkt verwenden {#use-the-cache-check-point}

In diesem Modus überprüft der Output-Dienst das Repository nur dann auf eine neuere Version der Ressourcen, wenn der Zeitstempel der zwischengespeicherten Ressourcen vor der Cacheprüfpunkt-Zeit liegt. Die letzte Cacheprüfpunkt-Zeit wird auf der Output-Seite in Administration Console angezeigt.

Verwenden Sie diesen Cache-Modus in Produktionsumgebungen mit hoher Leistung, in denen Änderungen an den Ressourcen nicht häufig vorkommen und in denen die Leistung wichtig ist. Sie können die Cacheprüfpunkt-Zeit zurücksetzen, wenn Sie Änderungen an den Repository-Ressourcen bereitstellen möchten.

**Die Verwendung einer Cacheprüfpunkt-Zeit angeben**

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Aktivieren Sie unter „Einstellungen für die Ausgabecache-Steuerung“ die Option „Nur, wenn die letzte Validierung vor der Cacheprüfpunkt-Zeit ausgeführt wurde“ und klicken Sie auf „Speichern“.

**Die Cacheprüfpunkt-Zeit zurücksetzen**

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Klicken Sie unter „Einstellungen für die Ausgabecache-Steuerung“ auf die Option „Cacheprüfpunkt“.

### Den Inhalt des Zwischenspeichers zurücksetzen {#reset-the-cache-contents}

Sie können den Inhalt des Zwischenspeichers jederzeit löschen. Nach dem Zurücksetzen des Zwischenspeichers ist die erste Anforderung für jedes Formular langsamer, da der Output-Dienst eine vollständige Wiedergabe ausführt und neue Inhalte für den Zwischenspeicher erstellt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Klicken Sie unter „Einstellungen für die Ausgabecache-Steuerung“ auf die Option „Cache zurücksetzen“.

## Cache-Einstellungen konfigurieren {#configuring-cache-settings}

Sie können Eigenschaften festlegen, die von Output für die Zwischenspeicherung verwendet werden und die die Leistung der AEM Forms-Umgebung optimieren können.

Klicken Sie zum Zugreifen auf diese Einstellungen in Administration Console auf „Dienste“ > „Output“.

>[!NOTE]
>
>Die Datenträgeranforderungen für den Cache müssen denen für das Repository entsprechen.

### Globale Cache-Einstellungen angeben {#specifying-global-cache-settings}

Die Einstellungen im Bereich **Globale Cache-Einstellungen** wirken sich auf alle Cache-Typen aus. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Max. Größe des Dokuments im Cache (KB)**: Die maximale Größe eines Formularentwurfs oder einer anderen Ressource in Kilobyte, die in einem speicherinternen Cache gespeichert werden kann. Dies ist eine globale Einstellung, die für alle Arbeitsspeichercaches gilt. Wenn die Ressource größer als dieser Wert ist, wird sie nicht im Arbeitsspeicher zwischengespeichert. Der Standardwert ist 1024 KB. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Formularwiedergabe mit aktiviertem Zwischenspeicher**: Diese Option ist standardmäßig ausgewählt. Das bedeutet, dass die wiedergegebenen Formulare für spätere Abrufe zwischengespeichert werden. Diese Einstellung hat wenig Auswirkungen auf die Leistung des Output-Dienstes, da keine nicht-interaktiven Dokumente zwischengespeichert werden. Diese Option hat eine Auswirkung, wenn Sie den Output-Dienst für nicht interaktive Dokumente, die auf dem Client wiedergegeben werden, verwenden.

### Formularentwürfe zwischenspeichern {#caching-form-designs}

Wenn der Output-Dienst eine Wiedergabeanforderung erhält, werden die Formularentwürfe aus dem Repository oder aus einer HTTP-Quelle abgerufen und zwischengespeichert. Diese Zwischenspeicherung verbessert die Leistung, da der Output-Dienst für folgende Wiedergabeanforderungen die Formularentwürfe aus dem Zwischenspeicher und nicht aus dem Repository abruft.

Der Output-Dienst speichert Formularentwürfe immer auf dem Datenträger zwischen. Wenn Formularentwürfe auf dem Server gespeichert werden, werden diese Dateien als Datenträgercache bezeichnet. Der Output-Dienst speichert außerdem Formularentwürfe im Arbeitsspeicher zwischen, gemäß der Einstellung im Bereich **Arbeitsspeichercache für Vorlagenkonfiguration**. Wenn Sie eine dieser Einstellungen ändern, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter [Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules).

**Vorlagenkonfigurations-Cache-Größe**: Die maximale Anzahl von Vorlagenkonfigurationsobjekten, die im Speicher beibehalten werden sollen. Der Standardwert ist 100. Es wird empfohlen, diesen Wert größer gleich dem Wert für die Vorlagencache-Größe festzulegen. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Vorlagen-Cache-Größe**: Die maximale Anzahl von Vorlageninhaltobjekten, die im Arbeitsspeicher behalten werden sollen. Der Standardwert ist 100. Diese Einstellung hat keine Auswirkungen auf den Datenträgercache.

**Aktiviert**: Standardmäßig ist dieses Kontrollkästchen aktiviert. Das bedeutet, dass die Formularvorlagen im Arbeitsspeicher zwischengespeichert werden. Wenn diese Option nicht ausgewählt ist, werden die Formularvorlagen nur auf dem Datenträger zwischengespeichert.

### Fragmente und Bilder zwischenspeichern {#caching-fragments-and-images}

Der Output-Dienst speichert Fragmente und Bilder, die in Formularentwürfen auf dem Datenträger verwendet werden, zwischen. Dies verbessert die Leistung, da die Fragmente und Bilder nur bei der ersten Anforderung vom Repository gelesen werden. Bei nachfolgenden Anforderungen liest der Output-Dienst anschließend die Fragmente und Bilder vom Datenträgercache. Fragmente und Bilder werden nur auf dem Datenträger zwischengespeichert und nicht im Arbeitsspeicher.

Sie können die folgenden Einstellungen verwenden, um die Zwischenspeicherung von Fragmenten und Bildern auf dem Datenträger zu steuern. Diese Einstellungen befinden sich im Bereich **Cacheeinstellungen für Vorlagenressourcen**:

**Ressourcenzwischenspeicherung** Wählen Sie eine der folgenden Optionen aus der Liste aus:

**Aktiviert für Fragmente und Bilder**: Der Ausgabe-Service speichert Fragmente und Bilder zwischen. Dies ist die Standardoption.

**Aktiviert für Fragmente**: Der Ausgabe-Service speichert Fragmente zwischen, jedoch keine Bilder.

**Deaktiviert**: Der Ausgabe-Service speichert weder Fragmente noch Bilder zwischen.

**Bereinigungsintervall (Sekunden)**: Gibt an, wie oft der Ausgabe-Service alte, ungültige Cache-Dateien entfernen soll. Der Output-Dienst entfernt keine gültigen Cachedateien. Wenn Sie das Bereinigungsintervall ändern, starten Sie den Output-Dienst neu, damit die Änderung wirksam wird. Verwenden Sie zum Neustart dieses Dienstes entweder Workbench, oder folgen Sie den Anweisungen unter Dienste starten oder beenden, die AEM Forms-Modulen zugeordnet sind.

## Clustering-Überlegungen zum Zwischenspeicher {#clustering-considerations-for-caches}

In einer Clusterumgebung verwaltet jeder Knoten seinen eigenen Arbeitsspeicher- und Datenträgercache. Der Inhalt des Zwischenspeichers auf jedem Knoten hängt davon ab, welche Formulare auf diesem Knoten wiedergegeben wurden.

Der Speicherort des Zwischenspeichers muss auf jedem Knoten des Clusters identisch sein (derselbe Datenträger und Pfad). Legen Sie den Zwischenspeicher nicht auf einem freigegebenen Speicher ab.

Wenn Sie die Output-Seite in Administration Console verwenden, um die Cache-Einstellungen für einen bestimmten Knoten zu ändern, werden die Cache-Einstellungen bei einer Anforderung an diesen Knoten auch auf anderen Knoten aktualisiert. Dieses Verhalten gilt auch für die Schaltfläche „Cache zurücksetzen“. Wenn Sie auf die Schaltfläche „Cache zurücksetzen“ für einen Knoten klicken, wird der Zwischenspeicher sofort von diesem Knoten gelöscht. Der Zwischenspeicher auf anderen Knoten wird bei einer Anforderung an diesen Knoten gelöscht.
