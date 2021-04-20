---
title: Arbeiten mit selektiver Veröffentlichung in Dynamic Media
description: Informationen zum Arbeiten mit selektiver Veröffentlichung in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner, Administrator
exl-id: cd025e9d-6fb1-436c-9e78-795f2daaf345
feature: Publishing
translation-type: tm+mt
source-git-commit: 9134130f349c6c7a06ad9658a87f78a86b7dbf9c
workflow-type: tm+mt
source-wordcount: '2935'
ht-degree: 98%

---

# Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media {#selective-publish-configure-folder}

Sie können Assets in AEM oder Dynamic Media auf der Ordnerebene veröffentlichen bzw. die Veröffentlichung rückgängig machen, indem Sie entweder **[!UICONTROL Veröffentlichung verwalten]** oder **[!UICONTROL Quick Publish]** nutzen, anstatt sich ausschließlich auf die **[!UICONTROL Dynamic Media-Konfiguration]** zu verlassen, deren Einstellungen für alle Ordner in Ihrer Dynamic Media-Instanz global sind.

Beispielsweise können Sie mit selektiver Veröffentlichung Assets für Produkte bearbeiten, die noch nicht live sind. In einem solchen Fall kann ein Marketing-Team auf Bilder mit smartem Zuschnitt und dynamische Ausgabedarstellungen zugreifen, die mit Dynamic Media synchronisiert werden. Auf diese Weise können Marketing-Experten Werbematerialien erstellen, ohne diese Assets für die weltweite Bereitstellung in Dynamic Media veröffentlichen zu müssen.

>[!IMPORTANT]
>
>Selektive Veröffentlichung ist nur im Dynamic Media-Scene7-Modus verfügbar.

>[!NOTE]
>
>Beim *Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus der Assets gelöscht. Wenn Sie Assets in oder aus Ordnern *verschieben*, deren Ordnereigenschaft auf **[!UICONTROL Selektive Veröffentlichung]** festgelegt ist, wird der Veröffentlichungsstatus dieser Assets jedoch beibehalten.

Falls Sie sich später entscheiden, die Einstellungen für **[!UICONTROL Selektive Veröffentlichung]** in einem Ordner zu ändern, wirken sich diese Änderungen nur auf neue Assets aus, die Sie ab diesem Zeitpunkt in den Ordner hochladen. Der Veröffentlichungsstatus vorhandener Assets im Ordner bleibt unverändert, bis Sie ihn im Dialogfeld **[!UICONTROL Quick Publish]** oder **[!UICONTROL Veröffentlichung verwalten]** manuell ändern.

Die Option **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf der Ordnerebene ist standardmäßig immer auf den Wert eingestellt, der in der Einstellung **[!UICONTROL Assets veröffentlichen]** in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** enthalten ist. Folgende Schritte in diesem Thema zeigen Ihnen jedoch, wie Sie diesen Standardwert auf der Ordnerebene manuell ändern können (wie in den folgenden Schritten beschrieben), um den Wert für die **[!UICONTROL Dynamic Media-Konfiguration]** zu überschreiben.

Unabhängig davon, ob Sie sich auf den Wertesatz **[!UICONTROL Assets veröffentlichen]**, der in **[!UICONTROL Dynamic Media-Konfiguration]** festgelegt ist, oder den in den Eigenschaften der Ordnerebene festgelegten Wertesatz **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** verlassen, können Sie zwischen **[!UICONTROL Sofort]**, **[!UICONTROL Bei Aktivierung]** und **[!UICONTROL Selektive Veröffentlichung]** wählen. Sie können beispielsweise den Wert **[!UICONTROL Assets veröffentlichen]** in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** auf **[!UICONTROL Bei Aktivierung]** setzen, den Wert für den **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf der Ordnerebene aber auf **[!UICONTROL Selektive Veröffentlichung]** setzen und umgekehrt usw.

Nachdem Sie selektive Veröffentlichung in einem Ordner konfiguriert haben, haben Sie folgende Möglichkeiten:

* [Veröffentlichen Sie Assets selektiv für Dynamic Media oder AEM mit „Veröffentlichung verwalten“.](#selective-publish-manage-publication)
* [Machen Sie die Veröffentlichung von Assets in Dynamic Media oder AEM mithilfe von „Veröffentlichung verwalten“ rückgängig.](#selective-unpublish-manage-publication)
* [Veröffentlichen Sie Assets in Dynamic Media oder AEM mithilfe von „Quick Publish“.](#quick-publish-aem-dm)
* [Veröffentlichen Sie Assets mithilfe von Suchergebnissen selektiv bzw. machen Sie die Veröffentlichung rückgängig.](#selective-publish-unpublish-search-results)

**So konfigurieren Sie eine selektive Veröffentlichung auf der Ordnerebene in Dynamic Media**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie einen der folgenden Schritte aus:
   * Eigenschaften eines vorhandenen Ordners bearbeiten – Navigieren Sie in der **[!UICONTROL Kartenansicht]**, der **[!UICONTROL Spaltenansicht]** oder der **[!UICONTROL Listenansicht]** zu einem Ordner, dessen Eigenschaften Sie bearbeiten möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
   * Eigenschaften eines neuen Ordners bearbeiten – Tippen Sie in der **[!UICONTROL Kartenansicht]**, der **[!UICONTROL Spaltenansicht]** oder der **[!UICONTROL Listenansicht]** oben rechts auf der Seite auf **[!UICONTROL Erstellen > Ordner]**. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** einen Titel für den Ordner ein (erforderlich) und tippen Sie dann auf **[!UICONTROL Erstellen]**. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Synchronisationsmodus]** eine der folgenden Optionen aus:

   | Synchronisationsmodus | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Übernommen]** | Kein expliziter Synchronisationswert für den Ordner. Stattdessen übernimmt der Ordner den Synchronisationswert von einem seiner Vorgängerordner oder den Standardmodus, der in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** festgelegt ist. Der detaillierte Status für **[!UICONTROL übernommene]** Daten wird als QuickInfo angezeigt. |
   | **[!UICONTROL Alles in diesem Unterbaum des Ordners mit Dynamic Media synchronisieren]** | Damit das Veröffentlichen in Dynamic Media erfolgreich ist, müssen Assets mit Dynamic Media synchronisiert werden. Wenn Sie diese Option wählen, werden alle Assets in diesem Unterbaum bei der Synchronisation mit Dynamic Media einbezogen. Die ordnerspezifischen Einstellungen setzen die Standardeinstellung in der **[!UICONTROL Dynamic Media-Konfiguration]** außer Kraft. |
   | **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Dynamic Media-Synchronisation ausschließen]** | Schließen Sie alle Assets in diesem Unterbaum von der Synchronisation mit Dynamic Media aus. |

   ![Selektive Veröffentlichung auf Ordnerebene](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** eine Option aus. Beachten Sie, dass bei der Option **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** standardmäßig immer der in der **[!UICONTROL Dynamic Media-Konfiguration]** festgelegte Wert verwendet wird. Sie können diesen Standardwert für die **[!UICONTROL Dynamic Media-Konfiguration]** jedoch manuell überschreiben, indem Sie eine der folgenden Optionen nutzen.

   >[!IMPORTANT]
   >
   >Beachten Sie, dass unabhängig von der ausgewählten Option für den Veröffentlichungsmodus für Dynamic Media alle Aktualisierungen, die Sie später an einem *bereits* veröffentlichten Asset vornehmen, sofort ohne weitere Benutzeraktion veröffentlicht werden.

   | Option für Veröffentlichungsmodus für Dynamic Media | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Sofort]** | Wenn Assets in diesen Ordner hochgeladen werden, erfasst das System die Assets in AEM und stellt die URL/den Einbettungs-Link sofort bereit. Diese Option ist nur an AEM-Veröffentlichungen gebunden; es ist kein Benutzereingriff erforderlich, wenn Assets veröffentlicht werden sollen.<br>Diese Option ist *nicht* verfügbar, wenn Sie im vorherigen Schritt die Option **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Dynamic Media-Synchronisation ausschließen]** im **[!UICONTROL Synchronisationsmodus]** aktiviert haben. |
   | **[!UICONTROL Bei Aktivierung]** | Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie ein Asset zuerst explizit veröffentlichen, bevor eine URL/ein Einbettungs-Link bereitgestellt wird. Diese Option ist nur an AEM-Veröffentlichungen gebunden.<br>Diese Option ist *nicht* verfügbar, wenn Sie im vorherigen Schritt die Option **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Dynamic Media-Synchronisation ausschließen]** im **[!UICONTROL Synchronisationsmodus]** aktiviert haben. |
   | **[!UICONTROL Selektive Veröffentlichung]** | Assets werden für die Bereitstellung im öffentlich zugänglichen Bereich je nach Wahl entweder in AEM oder Dynamic Media veröffentlicht. Beide Veröffentlichungsmethoden schließen sich gegenseitig aus.  Das heißt, Sie können Assets in DMS7 veröffentlichen, damit Sie Funktionen wie smartes Zuschneiden oder dynamische Ausgabedarstellungen verwenden können. Oder Sie können Assets ausschließlich in AEM zur sicheren Vorschau veröffentlichen. Diese Assets werden *nicht* in DMS7 veröffentlicht, um sie öffentlich bereitzustellen. Diese Option ist nicht verfügbar, wenn Sie im vorherigen Schritt die Option **[!UICONTROL Alles in diesem Unterbaum des Ordners von der Dynamic Media-Synchronisation ausschließen]** im **[!UICONTROL Synchronisationsmodus]** aktiviert haben. |

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern und schließen]** und dann auf **[!UICONTROL OK]**, um zu AEM Assets zurückzukehren.

## Assets mithilfe von &quot;Veröffentlichung verwalten{#selective-publish-manage-publication}&quot;selektiv auf Dynamic Media oder AEM veröffentlichen

Bevor Sie **[!UICONTROL Veröffentlichung verwalten]** verwenden können, um Assets in Dynamic Media oder AEM selektiv zu veröffentlichen, müssen Sie sicherstellen, dass Sie die Option **[!UICONTROL Assets veröffentlichen]** in **[!UICONTROL Dynamic Media-Konfiguration]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt oder auf der Ordnerebene selektive Veröffentlichung konfiguriert haben.

Siehe [Erstellen einer Dynamic Media-Konfiguration](#configuring-dynamic-media-cloud-services) oder [Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media](#selective-publish-configure-folder).

>[!IMPORTANT]
>
>Selektive Veröffentlichung ist nur im Dynamic Media-Scene7-Modus verfügbar.

>[!NOTE]
>
>Beim *Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus der Assets gelöscht. Wenn Sie Assets in oder aus Ordnern *verschieben*, deren Ordnereigenschaft auf **[!UICONTROL Selektive Veröffentlichung]** festgelegt ist, wird der Veröffentlichungsstatus dieser Assets jedoch beibehalten.

**So veröffentlichen Sie Assets selektiv unter Dynamic Media oder AEM mit &quot;Veröffentlichung verwalten&quot;**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Es ist ggf. hilfreich, die **[!UICONTROL Listenansicht]** zu verwenden, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners leichter erkennen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Es ist ggf. hilfreich, die **[!UICONTROL Listenansicht]** zu verwenden, um den Veröffentlichungsstatus eines bestimmten Assets leichter erkennen zu können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Veröffentlichung verwalten]** nicht in der Symbolleiste angezeigt wird, tippen Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** unter **[!UICONTROL Aktion]** den gewünschten Aktivierungstyp aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichen]** (in AEM) | Wählen Sie diese Option, um Assets in AEM für eine sichere Vorschau zu veröffentlichen. |
   | **[!UICONTROL In Dynamic Media veröffentlichen]** | Wählen Sie diese Option, um Assets für die Bereitstellung im öffentlich zugänglichen Bereich in Dynamic Media zu veröffentlichen oder um Funktionen wie smartes Zuschneiden oder dynamische Ausgabedarstellungen zu verwenden.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt ist. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Veröffentlichung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Assets sofort zu veröffentlichen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Assets an einem bestimmten Datum zu einer bestimmten Uhrzeit zu veröffentlichen. |

1. Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten]** auf **[!UICONTROL Weiter]**.
1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:

   * Wählen Sie bei Bedarf ein oder mehrere Assets aus, die Sie aus der Veröffentlichung entfernen möchten.
   * Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL In Dynamic Media veröffentlichen]**.
1. Tippen Sie auf **[!UICONTROL OK]**.

### Rückgängigmachen der Veröffentlichung von Assets in Dynamic Media oder AEM mithilfe von „Veröffentlichung verwalten“ {#selective-unpublish-manage-publication}

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, für dessen Assets Sie die Veröffentlichung rückgängig machen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Es ist ggf. hilfreich, die **[!UICONTROL Listenansicht]** zu verwenden, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners leichter erkennen können.
   * Navigieren Sie zu einem Ordner, für dessen Assets Sie die Veröffentlichung rückgängig machen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Es ist ggf. hilfreich, die **[!UICONTROL Listenansicht]** zu verwenden, um den Veröffentlichungsstatus eines bestimmten Assets leichter erkennen zu können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Veröffentlichung verwalten]** nicht in der Symbolleiste angezeigt wird, tippen Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** unter **[!UICONTROL Aktion]** die gewünschte Art der Deaktivierung aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichung rückgängig machen]** (in AEM) | Wählen Sie diese Option, um eine Veröffentlichung von Assets in AEM rückgängig zu machen. |
   | **[!UICONTROL Veröffentlichung in Dynamic Media rückgängig machen]** | Wählen Sie diese Option, um eine Veröffentlichung von Assets in Dynamic Media rückgängig zu machen.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt ist. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Deaktivierung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Veröffentlichung der Assets sofort rückgängig zu machen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Veröffentlichung der Assets an einem bestimmten Datum zu einer bestimmten Uhrzeit rückgängig zu machen. |

1. Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten]** auf **[!UICONTROL Weiter]**.
1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, deren Veröffentlichung Sie rückgängig machen möchten.
   * Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** auf **[!UICONTROL Veröffentlichung rückgängig machen]** oder **[!UICONTROL Veröffentlichung in Dynamic Media rückgängig machen]**.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Veröffentlichen von Assets in Dynamic Media oder AEM mithilfe von „Quick Publish“ {#quick-publish-aem-dm}

Für einfache Asset-Aktivierungen können Sie **[!UICONTROL Quick Publish]** verwenden. Mit der Funktion **[!UICONTROL Quick Publish]** werden die ausgewählten Assets ohne weitere Benutzerinteraktion sofort veröffentlicht. Aus diesem Grund werden alle nicht-veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

>[!NOTE]
>
>Um Assets in Dynamic Media oder AEM mit **[!UICONTROL Quick Publish]** veröffentlichen zu können, stellen Sie sicher, dass die Option **[!UICONTROL Selektive Veröffentlichung]** entweder in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** oder den Ordnereigenschaften des ausgewählten Ordners aktiviert ist.

**So veröffentlichen Sie Assets in Dynamic Media oder AEM mit „Quick Publish“**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie links auf der Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann rechts auf der Seite auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Quick Publish]**. Es ist ggf. hilfreich, die **[!UICONTROL Listenansicht]** zu verwenden, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners leichter erkennen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Quick Publish]**. Es ist ggf. hilfreich, die **[!UICONTROL Listenansicht]** zu verwenden, um den Veröffentlichungsstatus eines bestimmten Assets leichter erkennen zu können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Quick Publish]** nicht in der Symbolleiste angezeigt wird, tippen Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Quick Publish]**.

      ![„Quick Publish“ auf der Ordnerebene in Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Wählen Sie aus dem Listenmenü **[!UICONTROL Quick Publish]** eine der folgenden Optionen aus.

   | Option „Quick Publish“ | Funktion |
   | --- | --- | 
   | In AEM veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in AEM. |
   | In Brand Portal veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in **[!UICONTROL Brand Portal.]**<br>Diese Option ist nur verfügbar, wenn**[!UICONTROL  Brand Portal ]**bereits für Ihre AEM Assets-Instanz konfiguriert wurde. |
   | In Dynamic Media veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in Dynamic Media.<br>Ein Asset muss bereits mit Dynamic Media synchronisiert worden sein. Stellen Sie bei Bedarf sicher, dass der **[!UICONTROL Synchronisationsmodus]** in den Eigenschaften eines Ordners schon auf **[!UICONTROL Alles in diesem Unterbaum des Ordners mit Dynamic Media synchronisieren]** gesetzt ist. |

1. Tippen Sie auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Schließen.]**

## Selektive Veröffentlichung oder Rückgängigmachen der Veröffentlichung von Assets mithilfe von Suchergebnissen {#selective-publish-unpublish-search-results}

In den Suchergebnissen können Assets aus allen Asset-Ordnern angezeigt werden, die unterschiedliche Veröffentlichungseinstellungen für Dynamic Media haben. Wenn Sie ein oder mehrere Assets aus den Suchergebnissen ausgewählt haben und die Assets unterschiedliche Einstellungen für den Veröffentlichungsmodus für Dynamic Media aufweisen, können Sie über die Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** auslösen, um die Veröffentlichung vorzunehmen oder rückgängig zu machen.

Siehe auch [Suchen nach Assets in AEM](/help/assets/search-assets.md).

**So veröffentlichen Sie Assets selektiv mithilfe von Suchergebnissen oder machen die Veröffentlichung rückgängig**

1. Tippen Sie in AEM links oben auf der Seite auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der Seite links auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Tippen Sie in der Symbolleiste rechts oben auf der Seite auf das Suchsymbol (Lupe).
1. Geben Sie im Textfeld **[!UICONTROL Zu suchender Typ]** ein Keyword ein und drücken Sie dann die **[!UICONTROL Eingabetaste]**.
1. Tippen Sie oben rechts auf der Seite auf das Symbol **[!UICONTROL Listenansicht]**.
1. Tippen Sie oben links auf das Symbol **[!UICONTROL Filter]**.

   ![Listenansicht und Filter in Suchergebnissen](/help/assets/assets-dm/select-publish-search-result.png)

1. Erweitern Sie im linken Bereich den **[!UICONTROL Status]** und dann das Suchprädikat für **[!UICONTROL Dynamic Media]**.
1. Verwenden Sie die Kontrollkästchen **[!UICONTROL Veröffentlicht]** und **[!UICONTROL Veröffentlichung rückgängig gemacht]**, um die Suchergebnisse je nach Veröffentlichungsstatus der Dynamic Media-Assets weiter zu verfeinern.
Optional können Sie diese Kontrollkästchen zusammen mit dem Suchprädikat **[!UICONTROL Veröffentlichen]** verwenden, um die Suchergebnisse von **[!UICONTROL veröffentlichten]** und **[!UICONTROL rückgängig gemachten]** AEM-Assets zu verfeinern.
1. Führen Sie einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie veröffentlichen oder deren Veröffentlichung Sie rückgängig machen möchten.
   * Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Suchergebnisse]** auf **[!UICONTROL Alle auswählen]**.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Möglicherweise müssen Sie in der Symbolleiste auf das Symbol mit den Auslassungszeichen tippen, um die Option **[!UICONTROL Veröffentlichung verwalten]** anzuzeigen.
1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** die gewünschte Aktion aus.

   | Ausgewählte Aktion | Einstellung für die Veröffentlichung von Assets in der Dynamic Media-Konfiguration | Asset-Status |
   | --- | --- | --- |
   | Veröffentlichen | Sofort oder bei Aktivierung | Veröffentlicht in AEM und Dynamic Media. |
   | Veröffentlichen | Selektive Veröffentlichung | Nur in AEM veröffentlicht. |
   | Veröffentlichung rückgängig machen | Sofort oder bei Aktivierung | Veröffentlichung in AEM und Dynamic Media rückgängig gemacht. |
   | Veröffentlichung rückgängig machen | Selektive Veröffentlichung | Veröffentlichung nur in AEM rückgängig gemacht. |
   | In Dynamic Media veröffentlichen | Sofort oder bei Aktivierung | Nicht in AEM, Dynamic Media oder beidem veröffentlicht. |
   | In Dynamic Media veröffentlichen | Selektive Veröffentlichung | Nur in Dynamic Media veröffentlicht. |
   | Veröffentlichung in Dynamic Media rückgängig machen | Sofort oder bei Aktivierung | Veröffentlichung in AEM, Dynamic Media oder beidem nicht rückgängig gemacht. |
   | Veröffentlichung in Dynamic Media rückgängig machen | Selektive Veröffentlichung | Veröffentlichung nur in Dynamic Media rückgängig gemacht. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Deaktivierung fest.

   | Ausgewählter Zeitplan | Ergebnis |
   | --- | --- |
   | Jetzt | Die ausgewählte Aktion wird sofort ausgeführt. |
   | Später | Die ausgewählte Aktion wird am ausgewählten Datum zur ausgewählten Uhrzeit ausgeführt. |

1. Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** auf **[!UICONTROL Weiter]**.
1. (Optional) Überprüfen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten - Umfang]** in der Tabelle die Spalte **[!UICONTROL Ziel veröffentlichen]**, um die ausgewählten Assets anzuzeigen.

   | Einstellung für die Veröffentlichung von Assets in der Dynamic Media-Konfiguration | Ausgewählte Aktion | Ziel veröffentlichen |
   | --- | --- | --- |
   | Sofort oder <br>bei Aktivierung | Veröffentlichen | AEM und Dynamic Media |
   | Sofort oder <br>bei Aktivierung | In Dynamic Media veröffentlichen | Kein |
   | Selektive Veröffentlichung | Veröffentlichen | AEM |
   | Selektive Veröffentlichung | In Dynamic Media veröffentlichen | Dynamic Media |
   | Sofort oder <br>bei Aktivierung | Veröffentlichung rückgängig machen | AEM und Dynamic Media |
   | Sofort oder <br>bei Aktivierung | Veröffentlichung in Dynamic Media rückgängig machen | Kein |
   | Selektive Veröffentlichung | Veröffentlichung rückgängig machen | AEM |
   | Selektive Veröffentlichung | Veröffentlichung in Dynamic Media rückgängig machen | Dynamic Media |

1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie aus der Veröffentlichung oder dem Rückgängigmachen der Veröffentlichung entfernen möchten.
   * Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Veröffentlichung rückgängig machen]**, um die Aktion zu starten.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Überprüfen des Veröffentlichungsstatus eines Assets {#check-publish-status-of-asset}

Sie können in AEM die **[!UICONTROL Zeitleistensegment]** mit der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** verwenden, um den Veröffentlichungsstatus eines Assets rasch zu ermitteln.

**So prüfen Sie den Veröffentlichungsstatus eines Assets**

1. Tippen Sie in AEM links oben auf der Seite auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der Seite links auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Öffnen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** (im Screenshot unten ist die **[!UICONTROL Listenansicht]** dargestellt) einen Ordner, der Assets enthält, die Sie veröffentlicht haben oder deren Veröffentlichung Sie rückgängig gemacht haben.
1. Wählen Sie ein Asset aus, damit es mit einem Häkchen angezeigt wird. Siehe als Beispiel den Screenshot unten.
1. Wählen Sie links oben auf der Seite aus dem Dropdown-Menü die Option **[!UICONTROL Zeitleistensegment]**. Der Bereich **[!UICONTROL Status]** links zeigt den Veröffentlichungsstatus des ausgewählten Assets an.
Wenn Sie die **[!UICONTROL Listenansicht]** verwenden, wird eine zusätzliche Spalte für den Veröffentlichungsstatus in **[!UICONTROL Dynamic Media]** angezeigt.
   * In einem Ordner, der für die Synchronisation mit Dynamic Media konfiguriert wurde, wird die Spalte **[!UICONTROL Dynamic Media]** standardmäßig angezeigt.
   * In einem Ordner, der *nicht* für die Synchronisation mit Dynamic Media konfiguriert wurde, wird die Dynamic Media-Spalte nicht angezeigt.
      ![Listenansicht und Zeitleistensegment](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Fehlerbehebung bei der selektiven Veröffentlichung {#selective-publish-troubleshoot}

Bei Assets, die nicht mit Dynamic Media synchronisiert werden, bei denen jedoch eine Veröffentlichungsaktion für Dynamic Media ausgelöst wird, kommt es zu folgender Fehlermeldung und Lösung:

![Fehler bei der selektiven Veröffentlichung](/help/assets/assets-dm/selective-publish-error.png)
