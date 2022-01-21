---
title: Arbeiten mit selektiver Veröffentlichung in Dynamic Media
description: Sie können Assets auf Ordnerebene in Adobe Experience Manager oder Dynamic Media veröffentlichen oder deren Veröffentlichung rückgängig machen. Sie können entweder Veröffentlichung verwalten oder Quick Publish verwenden, anstatt sich ausschließlich auf die Dynamic Media-Konfiguration zu verlassen, deren Einstellungen für alle Ordner in Ihrer Dynamic Media-Instanz gelten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: cd025e9d-6fb1-436c-9e78-795f2daaf345
feature: Publishing
source-git-commit: 664e22cc4c6acd74f285a4ec1a0dbd7d301240b7
workflow-type: tm+mt
source-wordcount: '3000'
ht-degree: 80%

---

# Konfigurieren von selektiver Veröffentlichung auf Ordnerebene in Dynamic Media {#selective-publish-configure-folder}

Sie können Assets auf Ordnerebene in Adobe Experience Manager oder Dynamic Media veröffentlichen oder deren Veröffentlichung rückgängig machen. Sie können entweder **[!UICONTROL Veröffentlichung verwalten]** oder **[!UICONTROL Quick Publish]** anstatt sich ausschließlich auf die **[!UICONTROL Dynamic Media-Konfiguration]** deren Einstellungen für alle Ordner in Ihrer Dynamic Media-Instanz global sind.

Beispielsweise können Sie mit selektiver Veröffentlichung Assets für Produkte bearbeiten, die noch nicht live sind. In einem solchen Fall kann ein Marketing-Team auf Bilder mit smartem Zuschnitt und dynamische Ausgabedarstellungen zugreifen, die mit Dynamic Media synchronisiert werden. Auf diese Weise können Marketing-Experten Werbematerialien erstellen, ohne diese Assets für die globale Bereitstellung in Dynamic Media veröffentlichen zu müssen.

>[!IMPORTANT]
>
>Selektive Veröffentlichung ist nur im Modus Dynamic Media - Scene7 verfügbar.

>[!NOTE]
>
>Beim *Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus der Assets gelöscht. Wenn Sie Assets in oder aus Ordnern *verschieben*, deren Ordnereigenschaft auf **[!UICONTROL Selektive Veröffentlichung]** festgelegt ist, wird der Veröffentlichungsstatus dieser Assets jedoch beibehalten.

Falls Sie sich später entscheiden, die Einstellungen für **[!UICONTROL Selektive Veröffentlichung]** in einem Ordner zu ändern, wirken sich diese Änderungen nur auf neue Assets aus, die Sie ab diesem Zeitpunkt in den Ordner hochladen. Der Veröffentlichungsstatus vorhandener Assets im Ordner bleibt unverändert, bis Sie ihn im Dialogfeld **[!UICONTROL Quick Publish]** oder **[!UICONTROL Veröffentlichung verwalten]** manuell ändern.

Die Option **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf der Ordnerebene ist standardmäßig immer auf den Wert eingestellt, der sich in der Einstellung **[!UICONTROL Assets veröffentlichen]** in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** befindet. Folgende Schritte in diesem Thema zeigen Ihnen jedoch, wie Sie diesen Standardwert auf der Ordnerebene manuell ändern können (wie in den folgenden Schritten beschrieben), um den Wert für die **[!UICONTROL Dynamic Media-Konfiguration]** zu überschreiben.

Unabhängig davon, ob Sie sich auf einen der folgenden Punkte verlassen:

* **[!UICONTROL Veröffentlichen von Assets]** Wert festgelegt in **[!UICONTROL Dynamic Media-Konfiguration]**.
* **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** -Wert, der in den Eigenschaften auf Ordnerebene festgelegt ist.

Sie können **[!UICONTROL Sofort]**, **[!UICONTROL Bei Aktivierung]** oder **[!UICONTROL Selektive Veröffentlichung]**. Sie können beispielsweise die **[!UICONTROL Veröffentlichen von Assets]** -Wert in **[!UICONTROL Dynamic Media-Konfiguration]** nach **[!UICONTROL Bei Aktivierung]**, aber legen Sie die **[!UICONTROL Dynamic Media Publish]** -Moduswert auf Ordnerebene in **[!UICONTROL Selektive Veröffentlichung]** und umgekehrt.

Nachdem Sie selektive Veröffentlichung in einem Ordner konfiguriert haben, haben Sie folgende Möglichkeiten:

* [Veröffentlichen Sie Assets selektiv für Dynamic Media oder Experience Manager mit „Veröffentlichung verwalten“.](#selective-publish-manage-publication)
* [Heben Sie die Veröffentlichung von Assets in Dynamic Media oder Experience Manager mithilfe von „Veröffentlichung verwalten“ auf.](#selective-unpublish-manage-publication)
* [Veröffentlichen Sie Assets in Dynamic Media oder Experience Manager mithilfe von „Quick Publish“.](#quick-publish-aem-dm)
* [Veröffentlichen Sie Assets mithilfe von Suchergebnissen selektiv bzw. heben Sie die Veröffentlichung auf.](#selective-publish-unpublish-search-results)

**So konfigurieren Sie eine selektive Veröffentlichung auf der Ordnerebene in Dynamic Media:**

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen. Wählen Sie auf der linken Seite das Navigationssymbol (direkt über dem Werkzeugsymbol) aus und wählen Sie dann **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Führen Sie einen der folgenden Schritte aus:
   * Eigenschaften eines vorhandenen Ordners bearbeiten – Navigieren Sie in der **[!UICONTROL Kartenansicht]**, der **[!UICONTROL Spaltenansicht]** oder der **[!UICONTROL Listenansicht]** zu einem Ordner, dessen Eigenschaften Sie bearbeiten möchten. Wählen Sie den Ordner aus und wählen Sie dann in der Symbolleiste **[!UICONTROL Eigenschaften]**.
   * Eigenschaften eines neuen Ordners bearbeiten - in **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** Wählen Sie rechts oben auf der Seite die Option **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner]**. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** einen Titel für den Ordner ein (erforderlich) und klicken Sie dann auf **[!UICONTROL Erstellen]**. Wählen Sie den Ordner aus und wählen Sie dann in der Symbolleiste **[!UICONTROL Eigenschaften]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Synchronisationsmodus]** eine der folgenden Optionen aus:

   | Synchronisationsmodus | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Übernommen]** | Kein expliziter Synchronisationswert für den Ordner. Stattdessen übernimmt der Ordner den Synchronisationswert von einem seiner Vorgängerordner oder den Standardmodus, der in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** festgelegt ist. festgelegt ist. Der detaillierte Status für **[!UICONTROL übernommene]** Daten wird als QuickInfo angezeigt. |
   | **[!UICONTROL Alles in diesem Unterbaum des Ordners mit Dynamic Media synchronisieren]** | Damit das Veröffentlichen in Dynamic Media erfolgreich ist, müssen Assets mit Dynamic Media synchronisiert werden. Wenn Sie diese Option wählen, werden alle Assets in diesem Unterbaum bei der Synchronisation mit Dynamic Media einbezogen. Die ordnerspezifischen Einstellungen setzen die Standardeinstellung in der **[!UICONTROL Dynamic Media-Konfiguration]** außer Kraft. |
   | **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Synchronisation mit Dynamic Media ausschließen]** | Schließen Sie alle Assets in diesem Unterbaum von der Synchronisation mit Dynamic Media aus. |

   ![Selektive Veröffentlichung auf Ordnerebene](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** eine Option aus. Beachten Sie, dass bei der Option **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** standardmäßig immer der in der **[!UICONTROL Dynamic Media-Konfiguration]** festgelegte Wert verwendet wird. Sie können diesen Standardwert für die **[!UICONTROL Dynamic Media-Konfiguration]** jedoch manuell überschreiben, indem Sie eine der folgenden Optionen nutzen.

   >[!IMPORTANT]
   >
   >Beachten Sie, dass unabhängig von der ausgewählten Option für den Veröffentlichungsmodus für Dynamic Media alle Aktualisierungen, die Sie später an einem *bereits* veröffentlichten Asset vornehmen, sofort ohne weitere Benutzeraktion veröffentlicht werden.
   >
   >Wenn ein veröffentlichtes Video aktualisiert wird, muss es erneut veröffentlicht werden, um Änderungen beim Versand widerzuspiegeln.

   | Option für Veröffentlichungsmodus für Dynamic Media | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Sofort]** | Wenn Assets in diesen Ordner hochgeladen werden, erfasst das System die Assets in Experience Manager und stellt die URL/den Einbettungs-Link sofort bereit. Diese Option ist nur an Experience Manager-Veröffentlichungen gebunden; es ist kein Benutzereingriff erforderlich, wenn Assets veröffentlicht werden sollen.<br>Diese Option ist *nicht* verfügbar, wenn Sie im vorherigen Schritt die Option **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Synchronisation mit Dynamic Media ausschließen]** im **[!UICONTROL Synchronisationsmodus]** ausgewählt haben. |
   | **[!UICONTROL Bei Aktivierung]** | Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie ein Asset zuerst explizit veröffentlichen, bevor eine URL/ein Einbettungs-Link bereitgestellt wird. Diese Option ist nur an Experience Manager-Veröffentlichungen gebunden.<br>Diese Option ist *nicht* verfügbar, wenn Sie im vorherigen Schritt die Option **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Synchronisation mit Dynamic Media ausschließen]** im **[!UICONTROL Synchronisationsmodus]** ausgewählt haben. |
   | **[!UICONTROL Selektive Veröffentlichung]** | Assets werden für die Bereitstellung im öffentlich zugänglichen Bereich je nach Wahl entweder in Experience Manager oder Dynamic Media veröffentlicht. Beide Veröffentlichungsmethoden schließen sich gegenseitig aus. Das heißt, Sie können Assets in DMS7 veröffentlichen, damit Sie Funktionen wie smartes Zuschneiden oder dynamische Ausgabedarstellungen verwenden können. Oder Sie können Assets ausschließlich in Experience Manager zur sicheren Vorschau veröffentlichen. Diese Assets werden *nicht* in DMS7 veröffentlicht, um sie im öffentlich zugänglichen Bereich bereitzustellen. Diese Option ist nicht verfügbar, wenn Sie im vorherigen Schritt die Option **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Synchronisation mit Dynamic Media ausschließen]** im **[!UICONTROL Synchronisationsmodus]** ausgewählt haben. |

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern und schließen]** und dann auf **[!UICONTROL OK]**, um zu Experience Manager Assets zurückzukehren.

## Assets mithilfe von &quot;Veröffentlichung verwalten&quot;selektiv in Dynamic Media oder Experience Manager veröffentlichen{#selective-publish-manage-publication}

Bevor Sie **[!UICONTROL Veröffentlichung verwalten]** Um Assets selektiv in Dynamic Media oder Experience Manager zu veröffentlichen, stellen Sie sicher, dass Sie eine der folgenden Einstellungen festgelegt haben:

* Die **[!UICONTROL Veröffentlichen von Assets]** Option in **[!UICONTROL Dynamic Media-Konfiguration]** nach **[!UICONTROL Selektive Veröffentlichung]**
* Selektive Veröffentlichung auf Ordnerebene konfiguriert.

Siehe [Erstellen einer Dynamic Media-Konfiguration](#configuring-dynamic-media-cloud-services) oder [Konfigurieren von selektiver Veröffentlichung auf Ordnerebene in Dynamic Media](#selective-publish-configure-folder)

>[!IMPORTANT]
>
>Selektive Veröffentlichung ist nur im Modus Dynamic Media - Scene7 verfügbar.

>[!NOTE]
>
>Beim *Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus der Assets gelöscht. Wenn Sie Assets in oder aus Ordnern *verschieben*, deren Ordnereigenschaft auf **[!UICONTROL Selektive Veröffentlichung]** festgelegt ist, wird der Veröffentlichungsstatus dieser Assets jedoch beibehalten.

**So veröffentlichen Sie Assets mit &quot;Veröffentlichung verwalten&quot;selektiv in Dynamic Media oder Experience Manager:**

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen. Wählen Sie auf der linken Seite das Navigationssymbol (direkt über dem Werkzeugsymbol) aus und wählen Sie dann **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie **[!UICONTROL Listenansicht]**, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners leichter überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie **[!UICONTROL Listenansicht]**, damit Sie den Veröffentlichungsstatus eines bestimmten Assets leichter überprüfen können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Veröffentlichung verwalten]** nicht in der Symbolleiste angezeigt wird, klicken Sie stattdessen auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** unter **[!UICONTROL Aktion]** den gewünschten Aktivierungstyp aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichen]** (in Experience Manager) | Wählen Sie diese Option aus, damit Sie Assets für eine sichere Vorschau in Experience Manager veröffentlichen können. |
   | **[!UICONTROL In Dynamic Media veröffentlichen]** | Wählen Sie diese Option aus, damit Sie Assets in Dynamic Media veröffentlichen können, um sie öffentlich bereitzustellen, oder damit Sie Funktionen wie smartes Zuschneiden oder dynamische Ausgabedarstellungen verwenden können.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt ist. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Veröffentlichung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Assets sofort zu veröffentlichen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Assets an einem bestimmten Datum zu einer bestimmten Uhrzeit zu veröffentlichen. |

1. Klicken Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten]** auf **[!UICONTROL Weiter]**.
1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:

   * Wählen Sie bei Bedarf ein oder mehrere Assets aus, die Sie aus der Veröffentlichung entfernen möchten.
   * Wählen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL In Dynamic Media veröffentlichen]** aus.
1. Klicken Sie auf **[!UICONTROL OK]**.

### Selektives Aufheben der Veröffentlichung von Assets in Dynamic Media oder Experience Manager mithilfe von „Veröffentlichung verwalten“ {#selective-unpublish-manage-publication}

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen. Wählen Sie auf der linken Seite das Navigationssymbol (direkt über dem Werkzeugsymbol) aus und wählen Sie dann **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, für dessen Assets Sie die Veröffentlichung aufheben möchten. Wählen Sie den Ordner aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie **[!UICONTROL Listenansicht]**, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners leichter überprüfen können.
   * Navigieren Sie zu einem Ordner, für dessen Assets Sie die Veröffentlichung aufheben möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie **[!UICONTROL Listenansicht]**, damit Sie den Veröffentlichungsstatus eines bestimmten Assets leichter überprüfen können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Veröffentlichung verwalten]** nicht in der Symbolleiste angezeigt wird, klicken Sie stattdessen auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** unter **[!UICONTROL Aktion]** die gewünschte Art der Deaktivierung aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichung aufheben]** (aus Experience Manager) | Wählen Sie diese Option aus, wenn Sie die Veröffentlichung von Assets in Experience Manager rückgängig machen möchten. |
   | **[!UICONTROL Veröffentlichung in Dynamic Media aufheben]** | Wählen Sie diese Option aus, wenn Sie die Veröffentlichung von Assets in Dynamic Media rückgängig machen möchten.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt ist. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Deaktivierung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Veröffentlichung der Assets sofort aufzuheben. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Veröffentlichung der Assets an einem bestimmten Datum zu einer bestimmten Uhrzeit aufzuheben. |

1. Klicken Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten]** auf **[!UICONTROL Weiter]**.
1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, deren Veröffentlichung Sie aufheben möchten.
   * Wählen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** **[!UICONTROL Veröffentlichung aufheben]** oder **[!UICONTROL Veröffentlichung in Dynamic Media rückgängig machen]** aus.
1. Klicken Sie auf **[!UICONTROL OK]**.

## Veröffentlichen von Assets in Dynamic Media oder Experience Manager mithilfe von „Quick Publish“ {#quick-publish-aem-dm}

Für einfache Asset-Aktivierungen können Sie **[!UICONTROL Quick Publish]** verwenden. Mit der Funktion **[!UICONTROL Quick Publish]** werden die ausgewählten Assets ohne weitere Benutzerinteraktion sofort veröffentlicht. Aufgrund dieser Aktion werden alle nicht veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

>[!NOTE]
>
>Um Assets in Dynamic Media oder Experience Manager mit **[!UICONTROL Quick Publish]** veröffentlichen zu können, stellen Sie sicher, dass die Option **[!UICONTROL Selektive Veröffentlichung]** entweder in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** oder den Ordnereigenschaften des ausgewählten Ordners aktiviert ist.

**So veröffentlichen Sie Assets in Dynamic Media oder Experience Manager mithilfe von „Quick Publish“:**

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen. Wählen Sie links auf der Seite das Navigationssymbol (direkt über dem Werkzeugsymbol) aus und klicken Sie dann rechts auf der Seite auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Quick Publish]**. Verwenden Sie **[!UICONTROL Listenansicht]**, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners leichter überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus. Verwenden Sie **[!UICONTROL Listenansicht]**, damit Sie den Veröffentlichungsstatus eines bestimmten Assets leichter überprüfen können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Quick Publish]** nicht in der Symbolleiste angezeigt wird, klicken Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Quick Publish]**.

      ![„Quick Publish“ auf der Ordnerebene in Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Wählen Sie aus dem Listenmenü **[!UICONTROL Quick Publish]** eine der folgenden Optionen aus.

   | Option „Quick Publish“ | Funktion |
   | --- | --- | 
   | In Experience Manager veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in Experience Manager. |
   | In Brand Portal veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in **[!UICONTROL Brand Portal]**.<br>Diese Option ist nur verfügbar, wenn **[!UICONTROL Brand Portal]** bereits für Ihre Experience Manager Assets-Instanz konfiguriert wurde. |
   | In Dynamic Media veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in Dynamic Media.<br>Ein Asset muss mit Dynamic Media synchronisiert werden. Stellen Sie bei Bedarf sicher, dass der **[!UICONTROL Synchronisationsmodus]** in den Eigenschaften eines Ordners schon auf **[!UICONTROL Alles in diesem Unterbaum des Ordners mit Dynamic Media synchronisieren]** gesetzt ist. |

1. Klicken Sie auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Schließen]**.

## Selektive Veröffentlichung oder Aufheben der Veröffentlichung von Assets mithilfe von Suchergebnissen {#selective-publish-unpublish-search-results}

In den Suchergebnissen können Assets aus allen Asset-Ordnern angezeigt werden, die unterschiedliche Veröffentlichungseinstellungen für Dynamic Media haben. Wenn Sie mehrere Assets aus den Suchergebnissen auswählen und jedes Asset unterschiedliche Veröffentlichungsmoduseinstellungen in Dynamic Media hat, können Sie Trigger **[!UICONTROL Veröffentlichung verwalten]** in der Symbolleiste zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung.

Siehe auch [Suchen von Assets in Experience Manager](/help/assets/search-assets.md).

**So veröffentlichen Sie Assets selektiv mithilfe von Suchergebnissen oder heben die Veröffentlichung auf:**

1. Klicken Sie in Experience Manager links oben auf der Seite auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen. Wählen Sie auf der linken Seite der Seite das Navigationssymbol (direkt über dem Werkzeugsymbol) aus und wählen Sie dann **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Klicken Sie in der Symbolleiste rechts oben auf der Seite auf das Suchsymbol (Lupe).
1. Geben Sie im Textfeld **[!UICONTROL Zu suchender Typ]** ein Keyword ein und drücken Sie dann die **[!UICONTROL Eingabetaste]**.
1. Klicken Sie oben rechts auf der Seite auf das Symbol **[!UICONTROL Listenansicht]**.
1. Klicken Sie oben links auf das Symbol **[!UICONTROL Filter]**.

   ![Listenansicht und Filter in Suchergebnissen](/help/assets/assets-dm/select-publish-search-result.png)

1. Erweitern Sie im linken Bereich den **[!UICONTROL Status]** und dann das Suchprädikat für **[!UICONTROL Dynamic Media]**.
1. Verwenden Sie die Kontrollkästchen **[!UICONTROL Veröffentlicht]** und **[!UICONTROL Veröffentlichung aufgehoben]**, um die Suchergebnisse je nach Veröffentlichungsstatus der Dynamic Media-Assets weiter zu verfeinern.
Optional können Sie diese Kontrollkästchen zusammen mit dem Suchprädikat **[!UICONTROL Veröffentlichen]** verwenden, um die Suchergebnisse von **[!UICONTROL veröffentlichten]** und **[!UICONTROL nicht mehr veröffentlichten]** Experience Manager-Assets zu verfeinern.
1. Führen Sie einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie veröffentlichen oder deren Veröffentlichung Sie aufheben möchten.
   * Klicken Sie in der rechten oberen Ecke der Seite **[!UICONTROL Suchergebnisse]** auf **[!UICONTROL Alle auswählen]**.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Wählen Sie das Symbol mit den Auslassungspunkten in der Symbolleiste aus, damit Sie **[!UICONTROL Veröffentlichung verwalten]**.
1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** die gewünschte Aktion aus.

   | Ausgewählte Aktion | Einstellung für die Veröffentlichung von Assets in der Dynamic Media-Konfiguration | Asset-Status |
   | --- | --- | --- |
   | Veröffentlichen | Sofort oder bei Aktivierung | In Experience Manager und Dynamic Media veröffentlicht. |
   | Veröffentlichen | Selektive Veröffentlichung | Nur in Experience Manager veröffentlicht. |
   | Veröffentlichung aufheben | Sofort oder bei Aktivierung | Veröffentlichung in Experience Manager und Dynamic Media aufgehoben. |
   | Veröffentlichung aufheben | Selektive Veröffentlichung | Veröffentlichung nur in Experience Manager aufgehoben. |
   | In Dynamic Media veröffentlichen | Sofort oder bei Aktivierung | Nicht in Experience Manager oder Dynamic Media oder in beiden veröffentlicht. |
   | In Dynamic Media veröffentlichen | Selektive Veröffentlichung | Nur in Dynamic Media veröffentlicht. |
   | Veröffentlichung in Dynamic Media aufheben | Sofort oder bei Aktivierung | Veröffentlichung in Experience Manager, Dynamic Media oder in beiden nicht aufgehoben. |
   | Veröffentlichung in Dynamic Media aufheben | Selektive Veröffentlichung | Veröffentlichung nur in Dynamic Media aufgehoben. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Deaktivierung fest.

   | Ausgewählter Zeitplan | Ergebnis |
   | --- | --- |
   | Jetzt | Die ausgewählte Aktion wird sofort ausgeführt. |
   | Später | Die ausgewählte Aktion wird am ausgewählten Datum zur ausgewählten Uhrzeit ausgeführt. |

1. Klicken Sie in der rechten oberen Ecke der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** auf **[!UICONTROL Weiter]**.
1. (Optional) Überprüfen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten - Umfang]** in der Tabelle die Spalte **[!UICONTROL Ziel veröffentlichen]**, um die ausgewählten Assets anzuzeigen.

   | Einstellung für die Veröffentlichung von Assets in der Dynamic Media-Konfiguration | Ausgewählte Aktion | Ziel veröffentlichen |
   | --- | --- | --- |
   | Sofort oder <br>bei Aktivierung | Veröffentlichen | Experience Manager und Dynamic Media |
   | Sofort oder <br>bei Aktivierung | In Dynamic Media veröffentlichen | Kein |
   | Selektive Veröffentlichung | Veröffentlichen | Experience Manager |
   | Selektive Veröffentlichung | In Dynamic Media veröffentlichen | Dynamic Media |
   | Sofort oder <br>bei Aktivierung | Veröffentlichung aufheben | Experience Manager und Dynamic Media |
   | Sofort oder <br>bei Aktivierung | Veröffentlichung in Dynamic Media aufheben | Kein |
   | Selektive Veröffentlichung | Veröffentlichung aufheben | Experience Manager |
   | Selektive Veröffentlichung | Veröffentlichung in Dynamic Media aufheben | Dynamic Media |

1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie aus der Veröffentlichung oder dem Aufheben der Veröffentlichung entfernen möchten.
   * Wählen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Veröffentlichung aufheben]** aus, um die Aktion zu starten.
1. Klicken Sie auf **[!UICONTROL OK]**.

## Überprüfen des Veröffentlichungsstatus eines Assets {#check-publish-status-of-asset}

Sie können in Experience Manager die **[!UICONTROL Zeitleiste]** mit der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** verwenden, um den Veröffentlichungsstatus eines Assets rasch zu ermitteln.

**So prüfen Sie den Veröffentlichungsstatus eines Assets:**

1. Klicken Sie in Experience Manager links oben auf der Seite auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen. Wählen Sie auf der linken Seite der Seite das Navigationssymbol (direkt über dem Werkzeugsymbol) aus und wählen Sie dann **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Öffnen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** (im Screenshot unten ist die **[!UICONTROL Listenansicht]** dargestellt) einen Ordner, der Assets enthält, die Sie veröffentlicht haben oder deren Veröffentlichung Sie aufgehoben haben.
1. Wählen Sie ein Asset aus, damit es mit einem Häkchen angezeigt wird. Siehe als Beispiel den Screenshot unten.
1. Wählen Sie links oben auf der Seite aus dem Dropdown-Menü die Option **[!UICONTROL Zeitleiste]** Der Bereich **[!UICONTROL Status]** links zeigt den Veröffentlichungsstatus des ausgewählten Assets an.
Wenn Sie die **[!UICONTROL Listenansicht]** verwenden, wird eine zusätzliche Spalte für den Veröffentlichungsstatus in **[!UICONTROL Dynamic Media]** angezeigt.
   * In einem Ordner, der für die Synchronisation mit Dynamic Media konfiguriert wurde, wird die Spalte **[!UICONTROL Dynamic Media]** standardmäßig angezeigt.
   * In einem Ordner, der *nicht* für die Synchronisation mit Dynamic Media konfiguriert wurde, wird die Spalte „Dynamic Media“ nicht angezeigt.
      ![Listenansicht und Zeitleistensegment](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Fehlerbehebung bei der selektiven Veröffentlichung {#selective-publish-troubleshoot}

Bei Assets, die nicht mit Dynamic Media synchronisiert werden, bei denen jedoch eine Veröffentlichungsaktion für Dynamic Media ausgelöst wird, kommt es zu folgender Fehlermeldung und Lösung:

![Fehler bei der selektiven Veröffentlichung](/help/assets/assets-dm/selective-publish-error.png)
