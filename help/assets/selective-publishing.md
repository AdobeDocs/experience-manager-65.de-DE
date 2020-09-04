---
title: Arbeiten mit selektiver Veröffentlichung in dynamischen Medien
description: Informationen zum Arbeiten mit Selektiver Veröffentlichung in dynamischen Medien.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: 5e5108b943907e5286298552c724d2b33873503f
workflow-type: tm+mt
source-wordcount: '2934'
ht-degree: 6%

---


# Konfigurieren der selektiven Veröffentlichung auf Ordnerebene in dynamischen Medien {#selective-publish-configure-folder}

Sie können Assets auf Ordnerebene auf oder von AEM oder dynamischen Medien veröffentlichen oder die Veröffentlichung rückgängig machen, indem Sie entweder Veröffentlichung **** verwalten oder **[!UICONTROL Schnellveröffentlichung]** verwenden, anstatt sich ausschließlich auf die **[!UICONTROL dynamische Medienkonfiguration]** zu verlassen, deren Einstellungen für alle Ordner in Ihrer dynamischen Medieninstanz global sind.

Beispielsweise können Sie mit selektiver Veröffentlichung Assets für Produkte bearbeiten, die noch nicht live sind. In einem solchen Fall kann ein Marketingteam auf Bilder mit intelligenten Zuschnitten und dynamische Darstellungen zugreifen, die mit dynamischen Medien synchronisiert werden, um Werbematerialien zu erstellen, ohne diese Assets für den weltweiten Versand in dynamischen Medien veröffentlichen zu müssen.

>[!IMPORTANT]
>
>Selektive Veröffentlichung ist nur im Modus &quot;Dynamische Medien - Scene7&quot;verfügbar.

>[!NOTE]
>
>*Beim Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus dieser Assets gelöscht. Wenn Sie jedoch Assets in Ordner *verschieben* , deren Ordnereigenschaft auf &quot; **[!UICONTROL Selektive Veröffentlichung]**&quot;festgelegt ist, wird der Veröffentlichungsstatus dieser Assets beibehalten.

Wenn Sie sich später entscheiden, die Einstellungen für die **[!UICONTROL selektive Veröffentlichung]** in einem Ordner zu ändern, wirken sich diese Änderungen nur auf neue Assets aus, die Sie von diesem Zeitpunkt an in diesen Ordner hochladen. Der Veröffentlichungsstatus vorhandener Assets im Ordner bleibt unverändert, bis Sie sie manuell im Dialogfeld &quot; **[!UICONTROL Schnelle Veröffentlichung]** &quot;oder &quot;Veröffentlichung **[!UICONTROL verwalten]** &quot;ändern.

Die Option **[!UICONTROL Veröffentlichungsmodus]** für dynamische Medien auf Ordnerebene ist immer standardmäßig auf den Wert eingestellt, der in der Einstellung &quot;Elemente **[!UICONTROL veröffentlichen]** &quot;in Ihrer **[!UICONTROL dynamischen Medienkonfiguration]** enthalten ist. Die folgenden Schritte in diesem Thema zeigen Ihnen jedoch, wie Sie diesen Standardwert auf Ordnerebene (wie in den folgenden Schritten beschrieben) manuell ändern können, um den Wert für die **[!UICONTROL dynamische Medienkonfiguration]** zu überschreiben.

Unabhängig davon, ob Sie sich auf den Wert &quot;Assets **** veröffentlichen&quot;in den Eigenschaften für die **[!UICONTROL dynamische Medienkonfiguration]** oder &quot;Veröffentlichungsmodus für **[!UICONTROL dynamische Medien]** &quot;verlassen, können Sie **[!UICONTROL Sofort]**, **[!UICONTROL bei Aktivierung]****** oder beiSelektives Veröffentlichen auswählen. Sie können beispielsweise den Wert **[!UICONTROL &quot;Assets]** veröffentlichen&quot;in Ihrer **[!UICONTROL Konfiguration]** für dynamische Medien auf &quot; **[!UICONTROL Bei Aktivierung]**&quot;festlegen, den Wert für den Veröffentlichungsmodus **[!UICONTROL für]** dynamische Medien auf Ordnerebene jedoch auf &quot; **[!UICONTROL Selektive Veröffentlichung]**&quot;einstellen, umgekehrt usw.

Nachdem Sie die selektive Veröffentlichung in einem Ordner konfiguriert haben, haben Sie folgende Möglichkeiten:

* [Veröffentlichen Sie Assets selektiv für dynamische Medien oder AEM mit &quot;Veröffentlichung verwalten&quot;.](#selective-publish-manage-publication)
* [Rückgängigmachen der Veröffentlichung von Assets aus dynamischen Medien oder AEM mithilfe von &quot;Veröffentlichung verwalten&quot;.](#selective-unpublish-manage-publication)
* [Veröffentlichen von Assets in dynamischen Medien oder AEM mithilfe der Schnellveröffentlichung.](#quick-publish-aem-dm)
* [Assets können mithilfe von Suchergebnissen selektiv veröffentlicht oder die Veröffentlichung rückgängig gemacht werden.](#selective-publish-unpublish-search-results)

**So konfigurieren Sie eine selektive Veröffentlichung auf Ordnerebene in dynamischen Medien**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Extras-Symbol) und dann auf **[!UICONTROL Assets > Dateien.]**
1. Führen Sie einen der folgenden Schritte aus:
   * Bearbeiten Sie die Eigenschaften eines vorhandenen Ordners: Navigieren Sie in der **[!UICONTROL Kartenordner-Ansicht]**, der **[!UICONTROL SpaltenAnsicht]** oder der **[!UICONTROL Liste-Ansicht]** zu einem Ordner, dessen Eigenschaften Sie bearbeiten möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften.]**
   * Bearbeiten Sie die Eigenschaften eines neuen Ordners - In der **[!UICONTROL Kartenansicht, der Ansicht]** der **[!UICONTROL Spalte oder der Ansicht]** der **[!UICONTROL Liste]** oben rechts auf der Seite tippen Sie auf **[!UICONTROL Erstellen > Ordner.]** Geben Sie im Dialogfeld &quot;Ordner **[!UICONTROL erstellen]** &quot;einen Titel (erforderlich) für den Ordner ein und tippen Sie dann auf **[!UICONTROL Erstellen.]** Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften.]**

1. Wählen Sie in der Dropdown-Liste &quot; **[!UICONTROL Synchronisierungsmodus]** &quot;eine der folgenden Optionen aus:

   | Synchronisationsmodus | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Übernommen]** | No explicit sync value on the folder; instead, the folder inherits the sync value from one of its ancestor folders or the default mode set in your **[!UICONTROL Dynamic Media Configuration]**. The detailed status for **[!UICONTROL Inherited]** shows by way of a tool tip. |
   | **[!UICONTROL Alles in diesem Unterbaum des Ordners mit Dynamic Media synchronisieren]** | Damit das Veröffentlichen in dynamischen Medien erfolgreich ist, müssen Assets mit dynamischen Medien synchronisiert werden. Wenn Sie diese Option auswählen, werden alle Assets in dieser Unterstruktur zum Synchronisieren mit dynamischen Medien einbezogen. Die ordnerspezifischen Einstellungen setzen die Standardeinstellung in der **[!UICONTROL dynamischen Medienkonfiguration]** außer Kraft. |
   | **[!UICONTROL Alle Elemente in diesem Ordner-Unterbaum von der Synchronisierung mit dynamischen Medien ausschließen]** | Schließen Sie alle Assets in dieser Unterstruktur von der Synchronisierung mit dynamischen Medien aus. |

   ![Ordnerebene selektiv veröffentlichen](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Wählen Sie in der Dropdown-Liste &quot;Veröffentlichungsmodus für **[!UICONTROL dynamische Medien]** &quot;eine Option aus. Beachten Sie, dass bei der Option **[!UICONTROL Veröffentlichungsmodus]** für dynamische Medien immer der in der **[!UICONTROL Konfiguration]** für dynamische Medien festgelegte Wert verwendet wird. Sie können diesen Standardwert für die **[!UICONTROL dynamische Medienkonfiguration]** jedoch manuell überschreiben, indem Sie eine der folgenden Optionen verwenden.

   >[!IMPORTANT]
   >
   >Beachten Sie, dass unabhängig von der ausgewählten Option für den Veröffentlichungsmodus für dynamische Medien alle Aktualisierungen, die Sie später an einem Asset vornehmen, das *bereits* veröffentlicht wurde, sofort ohne weitere Benutzeraktionen veröffentlicht werden.

   | Option für den Veröffentlichungsmodus für dynamische Medien | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Sofort]** | Wenn Assets in diesen Ordner hochgeladen werden, lädt das System die Assets in AEM ein und stellt die URL/Einbettung sofort bereit. Diese Option ist nur an AEM Veröffentlichung gebunden und es ist kein Benutzereingriff erforderlich, um Assets zu veröffentlichen.<br>Diese Option ist *nicht* verfügbar, wenn Sie im vorherigen Schritt die Option Alles in diesem Ordner-Unterbaum von der Synchronisierung **[!UICONTROL der dynamischen Medien im]** Synchronisierungsmodus **** ausschließen aktiviert haben. |
   | **[!UICONTROL Bei Aktivierung]** | Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor ein URL-/Einbettungslink bereitgestellt wird. Diese Option ist nur an AEM Veröffentlichung gebunden.<br>Diese Option ist *nicht* verfügbar, wenn Sie im vorherigen Schritt die Option Alles in diesem Ordner-Unterbaum von der Synchronisierung **[!UICONTROL der dynamischen Medien im]** Synchronisierungsmodus **** ausschließen aktiviert haben. |
   | **[!UICONTROL Selektive Veröffentlichung]** | Assets werden für den Versand im öffentlichen Bereich entweder nach Ihrer Wahl AEM oder auf dynamische Medien veröffentlicht. Beide Veröffentlichungsmethoden schließen sich gegenseitig aus.  Das heißt, Sie können Assets in DMS7 veröffentlichen, damit Sie Funktionen wie Smart-Zuschneiden oder dynamische Darstellungen verwenden können. Or, you can publish assets exclusively to AEM for secure previewing; those same assets are *not* published to DMS7 for delivery in the public domain. Diese Option ist nicht verfügbar, wenn Sie im vorherigen Schritt die Option Alles in diesem Ordner-Unterbaum aus der Synchronisierung **[!UICONTROL der dynamischen Medien im]** Synchronisierungsmodus **** ausschließen aktiviert haben. |

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern &amp; Schließen]** und dann auf **[!UICONTROL OK]** , um zu AEM Assets zurückzukehren.

## Assets mithilfe von &quot;Veröffentlichung verwalten&quot;selektiv für dynamische Medien oder AEM veröffentlichen{#selective-publish-manage-publication}

Bevor Sie Veröffentlichungen **** verwalten verwenden können, um Assets selektiv für dynamische Medien zu veröffentlichen oder AEM, stellen Sie sicher, dass Sie die Option &quot;Assets **** veröffentlichen&quot;in der Konfiguration **** dynamischer Medien auf **[!UICONTROL Selektive Veröffentlichung]** eingestellt oder eine selektive Veröffentlichung auf Ordnerebene konfiguriert haben.

Siehe [Erstellen einer Konfiguration](#configuring-dynamic-media-cloud-services) für dynamische Medien oder [Konfigurieren der selektiven Veröffentlichung auf Ordnerebene in dynamischen Medien](#selective-publish-configure-folder)

>[!IMPORTANT]
>
>Selektive Veröffentlichung ist nur im Modus &quot;Dynamische Medien - Scene7&quot;verfügbar.

>[!NOTE]
>
>*Beim Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus dieser Assets gelöscht. Wenn Sie jedoch Assets in Ordner *verschieben* , deren Ordnereigenschaft auf &quot; **[!UICONTROL Selektive Veröffentlichung]**&quot;festgelegt ist, wird der Veröffentlichungsstatus dieser Assets beibehalten.

**So veröffentlichen Sie Assets selektiv für dynamische Medien oder AEM mit &quot;Veröffentlichung verwalten&quot;**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Extras-Symbol) und dann auf **[!UICONTROL Assets > Dateien.]**
1. Führen Sie in **[!UICONTROL Ansicht]**, **[!UICONTROL Spalte Ansicht]** oder Ansicht **[!UICONTROL Liste]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und tippen Sie dann auf der Symbolleiste auf Veröffentlichung **[!UICONTROL verwalten.]**  Es ist ggf. hilfreich, die Ansicht **[!UICONTROL der]** Liste zu verwenden, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners einfacher überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. On the toolbar, tap **[!UICONTROL Manage Publication]**. Es ist ggf. hilfreich, die Ansicht **[!UICONTROL der]** Liste zu verwenden, um den Veröffentlichungsstatus eines bestimmten Assets einfacher zu prüfen.

      >[!NOTE]
      >
      >Wenn Veröffentlichung **[!UICONTROL verwalten]** nicht in der Symbolleiste angezeigt wird, tippen Sie stattdessen auf die Auslassungsschaltfläche und wählen Sie im Menü &quot;Liste&quot;die Option &quot;Veröffentlichung **[!UICONTROL verwalten]** &quot;aus.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten - Optionen]** unter **[!UICONTROL Aktion]** den gewünschten Typ der Aktivierung aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichen]** (AEM) | Wählen Sie diese Option, um Assets für eine sichere Vorschau AEM zu veröffentlichen. |
   | **[!UICONTROL In Dynamic Media veröffentlichen]** | Wählen Sie diese Option, um Assets für den Versand in der öffentlichen Domäne auf dynamischen Medien zu veröffentlichen oder um Funktionen wie Smart-Zuschneiden oder dynamische Darstellungen zu verwenden.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der Veröffentlichungsmodus **[!UICONTROL für]** dynamische Medien auf **[!UICONTROL Selektive Veröffentlichung]** eingestellt ist. |

1. Legen Sie unter **[!UICONTROL Planen]** den Zeitpunkt der Veröffentlichung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Assets sofort zu veröffentlichen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Assets an einem bestimmten Datum und einer bestimmten Uhrzeit zu veröffentlichen. |

1. In the upper-right corner of the **[!UICONTROL Manage Publication]** page, tap **[!UICONTROL Next]**.
1. Führen Sie auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Scope]** &quot;einen der folgenden Schritte aus:
   * Wählen Sie bei Bedarf ein oder mehrere Assets aus, die Sie aus der Veröffentlichung entfernen möchten.
   * Tippen Sie in der rechten oberen Ecke der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Umfang]** &quot;auf **[!UICONTROL Veröffentlichen]** oder Auf dynamischen Medien **[!UICONTROL veröffentlichen.]**
1. Tippen Sie auf **[!UICONTROL OK]**.

### Rückgängigmachen der Veröffentlichung von Assets aus dynamischen Medien oder AEM mithilfe von &quot;Veröffentlichung verwalten&quot; {#selective-unpublish-manage-publication}

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Extras-Symbol) und dann auf **[!UICONTROL Assets > Dateien.]**
1. Führen Sie in **[!UICONTROL Ansicht]**, **[!UICONTROL Spalte Ansicht]** oder Ansicht **[!UICONTROL Liste]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie die Veröffentlichung rückgängig machen möchten. Wählen Sie den Ordner aus und tippen Sie dann auf der Symbolleiste auf Veröffentlichung **[!UICONTROL verwalten.]**  Es ist ggf. hilfreich, die Ansicht **[!UICONTROL der]** Liste zu verwenden, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners einfacher überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie die Veröffentlichung rückgängig machen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. On the toolbar, tap **[!UICONTROL Manage Publication]**. Es ist ggf. hilfreich, die Ansicht **[!UICONTROL der]** Liste zu verwenden, um den Veröffentlichungsstatus eines bestimmten Assets einfacher zu prüfen.

      >[!NOTE]
      >
      >Wenn Veröffentlichung **[!UICONTROL verwalten]** nicht in der Symbolleiste angezeigt wird, tippen Sie stattdessen auf die Auslassungsschaltfläche und wählen Sie im Menü &quot;Liste&quot;die Option &quot;Veröffentlichung **[!UICONTROL verwalten]** &quot;aus.

1. Wählen Sie auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Optionen]** &quot;unter &quot; **[!UICONTROL Aktion]**&quot;die gewünschte Art der Aktivierung aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichung rückgängig machen]** (von AEM) | Wählen Sie diese Option, um die Veröffentlichung von Assets aus AEM rückgängig zu machen. |
   | **[!UICONTROL Veröffentlichung von Dynamic Media rückgängig machen]** | Wählen Sie diese Option, um die Veröffentlichung von Assets aus dynamischen Medien rückgängig zu machen.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der Veröffentlichungsmodus **[!UICONTROL für]** dynamische Medien auf **[!UICONTROL Selektive Veröffentlichung]** eingestellt ist. |

1. Legen Sie unter **[!UICONTROL Planen]** den Zeitpunkt der Aktivierung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Veröffentlichung der Assets sofort rückgängig zu machen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Veröffentlichung der Assets an einem bestimmten Datum und einer bestimmten Uhrzeit rückgängig zu machen. |

1. In the upper-right corner of the **[!UICONTROL Manage Publication]** page, tap **[!UICONTROL Next]**.
1. Führen Sie auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Scope]** &quot;einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie aus der Rückgängigmachung der Veröffentlichung entfernen möchten.
   * Tippen Sie oben rechts auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Umfang]** &quot;auf **[!UICONTROL Veröffentlichung rückgängig machen]** oder Veröffentlichung aus dynamischen Medien **[!UICONTROL rückgängig machen]**.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Veröffentlichen von Assets in dynamischen Medien oder AEM mithilfe der Schnellveröffentlichung {#quick-publish-aem-dm}

Sie können die **[!UICONTROL Schnellveröffentlichung]** für einfache Asset-Aktivierungen verwenden. **[!UICONTROL Mit der Funktion &quot;Schnell veröffentlichen]** &quot;werden die ausgewählten Assets sofort ohne weitere Benutzerinteraktionen veröffentlicht. Aus diesem Grund werden alle nicht veröffentlichten Referenzen automatisch veröffentlicht.

>[!NOTE]
>
>Um Assets mit der **[!UICONTROL Schnellveröffentlichung]** für dynamische Medien oder AEM zu veröffentlichen, stellen Sie sicher, dass die Option &quot; **[!UICONTROL Selektive Veröffentlichung]** &quot;entweder in Ihrer **[!UICONTROL dynamischen Medienkonfiguration]** oder in den Ordnereigenschaften des ausgewählten Ordners aktiviert ist.

**So veröffentlichen Sie Assets mit dynamischen Medien oder AEM mit der Schnellveröffentlichung**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Extras-Symbol) und dann rechts auf der Seite auf **[!UICONTROL Assets > Dateien.]**
1. Führen Sie in **[!UICONTROL Ansicht]**, **[!UICONTROL Spalte Ansicht]** oder Ansicht **[!UICONTROL Liste]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Schnellveröffentlichung.]**  Es ist ggf. hilfreich, die Ansicht **[!UICONTROL der]** Liste zu verwenden, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners einfacher überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Quick Publish]**. Es ist ggf. hilfreich, die Ansicht **[!UICONTROL der]** Liste zu verwenden, um den Veröffentlichungsstatus eines bestimmten Assets einfacher zu prüfen.

      >[!NOTE]
      >
      >Wenn die **[!UICONTROL Schnellveröffentlichung]** nicht in der Symbolleiste angezeigt wird, tippen Sie stattdessen auf die Auslassungsschaltfläche und wählen Sie im Menü &quot;Liste&quot;die Option &quot; **[!UICONTROL Schnelle Veröffentlichung]** &quot;aus.

      ![Schnellveröffentlichung auf Ordnerebene für dynamische Medien](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Wählen Sie eine der folgenden Optionen aus der Liste im Menü &quot; **[!UICONTROL Schnelle Veröffentlichung]** &quot;aus.

   | Schnellveröffentlichungsoption | Funktion |
   | --- | --- | 
   | In AEM veröffentlichen | Veröffentlicht die ausgewählten Assets sofort auf AEM. |
   | Im Brand Portal veröffentlichen | Veröffentlicht die ausgewählten Assets sofort im **[!UICONTROL Markenportal]**.<br>Diese Option ist nur verfügbar, wenn Ihre AEM Assets-Instanz **[!UICONTROL Brand Portal]** bereits konfiguriert hat. |
   | In Dynamic Media veröffentlichen | Veröffentlicht die ausgewählten Assets sofort auf dynamischen Medien.<br>Ein Asset muss bereits mit dynamischen Medien synchronisiert werden. Stellen Sie bei Bedarf sicher, dass der **[!UICONTROL Synchronisierungsmodus]** in den Eigenschaften eines Ordners bereits auf &quot;Alles in diesem Unterbaum **[!UICONTROL synchronisieren&quot;eingestellt ist, um dynamisches Medium]** zu verwenden. |

1. Tippen Sie auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Schließen]**.

## Selektives Veröffentlichen oder Rückgängigmachen der Veröffentlichung von Assets mithilfe von Suchergebnissen {#selective-publish-unpublish-search-results}

In den Suchergebnissen können Assets aus Asset-Ordnern mit unterschiedlichen Veröffentlichungseinstellungen für dynamische Medien angezeigt werden. Wenn Sie ein oder mehrere Assets aus den Suchergebnissen ausgewählt haben und die Assets unterschiedliche Einstellungen für den Veröffentlichungsmodus für dynamische Medien haben, können Sie Veröffentlichungen **[!UICONTROL über die Symbolleiste]** verwalten auslösen, um die Veröffentlichung zu veröffentlichen oder die Veröffentlichung rückgängig zu machen.

Siehe auch [Suchen von Assets in AEM.](/help/assets/search-assets.md)

**So veröffentlichen Sie Assets selektiv mithilfe von Suchergebnissen oder machen die Veröffentlichung rückgängig**

1. Tippen Sie in AEM links oben auf der Seite auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Extras-Symbol) und dann auf **[!UICONTROL Assets > Dateien.]**
1. Tippen Sie in der Symbolleiste rechts oben auf das Suchsymbol (Lupe).
1. Geben Sie im Textfeld **[!UICONTROL Typ, nach dem gesucht]** werden soll, einen Suchbegriff ein und drücken Sie dann die **[!UICONTROL Eingabetaste]**.
1. Tippen Sie oben rechts auf der Seite auf das Symbol **[!UICONTROL Liste Ansicht]** .
1. Near the upper-left corner of the page, tap the **[!UICONTROL Filters]** icon.

   ![Ansicht und Filter der Liste in den Suchergebnissen](/help/assets/assets-dm/select-publish-search-result.png)

1. Erweitern Sie im linken Bereich **[!UICONTROL Status]** und dann die Suchvorhersage für **[!UICONTROL dynamische Medien]** .
1. Verwenden Sie die Kontrollkästchen &quot; **[!UICONTROL Veröffentlicht]** &quot;und &quot; **[!UICONTROL unveröffentlicht]** &quot;, um die Suchergebnisse je nach dem Status der Assets mit dynamischen Medien weiter zu verfeinern.
Optional können Sie diese Kontrollkästchen zusammen mit der Suchvorgabe **[!UICONTROL Veröffentlichen]** verwenden, um die Suchergebnisse von **[!UICONTROL Veröffentlicht]** - und **[!UICONTROL Nicht veröffentlicht]** -AEM-Assets zu verfeinern.
1. Führen Sie einen der folgenden Schritte aus:
   * Wählen Sie eines oder mehrere Assets aus, die Sie veröffentlichen oder die Veröffentlichung rückgängig machen möchten.
   * Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Suchergebnisse]** auf Alle **[!UICONTROL auswählen]**.
1. On the toolbar, tap **[!UICONTROL Manage Publication]**. Möglicherweise müssen Sie auf das Auslassungszeichen in der Symbolleiste tippen, um die **[!UICONTROL Option &quot;Veröffentlichung]** verwalten&quot;anzuzeigen.
1. Wählen Sie auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Optionen]** &quot;die gewünschte Aktion aus.

   | Ausgewählte Aktion | Einstellung &quot;Assets veröffentlichen&quot;in der Konfiguration für dynamische Medien | Assets sind |
   | --- | --- | --- |
   | Veröffentlichen   | Sofort oder auf Aktivierung | Veröffentlicht in AEM und dynamischen Medien. |
   | Veröffentlichen   | Selektive Veröffentlichung | Nur AEM veröffentlicht. |
   | Veröffentlichung rückgängig machen | Sofort oder auf Aktivierung | Veröffentlichung für AEM und dynamische Medien rückgängig gemacht. |
   | Veröffentlichung rückgängig machen | Selektive Veröffentlichung | Nur AEM Veröffentlichung rückgängig gemacht. |
   | In Dynamic Media veröffentlichen | Sofort oder auf Aktivierung | Nicht in AEM, in dynamischen Medien oder beidem veröffentlicht. |
   | In Dynamic Media veröffentlichen | Selektive Veröffentlichung | Nur für dynamische Medien veröffentlicht. |
   | Veröffentlichung von Dynamic Media rückgängig machen | Sofort oder auf Aktivierung | Veröffentlichung nicht rückgängig gemacht von AEM, Dynamic Media oder beidem. |
   | Veröffentlichung von Dynamic Media rückgängig machen | Selektive Veröffentlichung | Nur Veröffentlichung für dynamische Medien rückgängig gemacht. |

1. Legen Sie unter **[!UICONTROL Planen]** den Zeitpunkt der Aktivierung fest.

   | Ausgewählter Zeitplan | Ergebnis |
   | --- | --- |
   | Jetzt | Die ausgewählte Aktion wird sofort ausgeführt. |
   | Später | Die ausgewählte Aktion wird am ausgewählten Datum und zur ausgewählten Uhrzeit ausgeführt. |

1. Tippen Sie in der rechten oberen Ecke der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Optionen]** &quot;auf **[!UICONTROL Weiter]**.
1. (Optional) Überprüfen Sie auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Umfang]** &quot;die Spalte &quot;Zielgruppe **[!UICONTROL für]** Veröffentlichung&quot;für die ausgewählten Assets.

   | Einstellung &quot;Assets veröffentlichen&quot;in der Konfiguration für dynamische Medien | Ausgewählte Aktion | Ziel veröffentlichen |
   | --- | --- | --- |
   | Sofort oder <br>nach Aktivierung | Veröffentlichen   | AEM und dynamische Medien |
   | Sofort oder <br>nach Aktivierung | In Dynamic Media veröffentlichen | Keine |
   | Selektive Veröffentlichung | Veröffentlichen   | AEM |
   | Selektive Veröffentlichung | In Dynamic Media veröffentlichen | Dynamic Media |
   | Sofort oder <br>nach Aktivierung | Veröffentlichung rückgängig machen | AEM und dynamische Medien |
   | Sofort oder <br>nach Aktivierung | Veröffentlichung von Dynamic Media rückgängig machen | Keine |
   | Selektive Veröffentlichung | Veröffentlichung rückgängig machen | AEM |
   | Selektive Veröffentlichung | Veröffentlichung von Dynamic Media rückgängig machen | Dynamic Media |

1. Führen Sie auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Scope]** &quot;einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie aus der Veröffentlichung entfernen oder die Veröffentlichung rückgängig machen möchten.
   * Tippen Sie oben rechts auf der Seite &quot;Veröffentlichung **[!UICONTROL verwalten - Umfang]** &quot;auf **[!UICONTROL Veröffentlichen]** oder Veröffentlichung **[!UICONTROL rückgängig machen]** , um die Aktion zu starten.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Überprüfen des Veröffentlichungsstatus eines Assets {#check-publish-status-of-asset}

Sie können die **[!UICONTROL Zeitschiene]** mit der **[!UICONTROL KartenAnsicht]**, der **[!UICONTROL Spalten-Ansicht]** oder der Ansicht **[!UICONTROL der]** Liste in AEM verwenden, um den Veröffentlichungsstatus eines Assets schnell zu überprüfen.

**So prüfen Sie den Veröffentlichungsstatus eines Assets**

1. Tippen Sie in AEM links oben auf der Seite auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Extras-Symbol) und dann auf **[!UICONTROL Assets > Dateien.]**
1. Öffnen Sie in der Ansicht **[!UICONTROL &quot;]** Ansicht **[!UICONTROL der Karte&quot;, &quot;]** Spalte&quot; **[!UICONTROL oder &quot;]** Liste&quot;(Screenshot unten zeigt die Ansicht **[!UICONTROL der]** Liste) einen Ordner, der die veröffentlichten oder unveröffentlichten Assets enthält.
1. Wählen Sie ein Asset aus, damit es mit einem Häkchen angezeigt wird. Siehe Screenshot unten zum Beispiel.
1. Near the upper-left corner of the page, from the drop-down menu, select **[!UICONTROL Timeline]**. Der **[!UICONTROL Statusbereich]** im linken Bereich zeigt den Veröffentlichungsstatus des ausgewählten Assets an.
Wenn Sie die **[!UICONTROL Liste-Ansicht]** verwenden, wird eine zusätzliche Spalte für den Veröffentlichungsstatus **[!UICONTROL für dynamische Medien]** angezeigt.
   * In einem Ordner, der für die Synchronisierung mit dynamischen Medien konfiguriert ist, wird standardmäßig die Spalte &quot; **[!UICONTROL Dynamische Medien]** &quot;angezeigt.
   * In einem Ordner, der *nicht* für die Synchronisierung mit dynamischen Medien konfiguriert ist, wird die Spalte &quot;Dynamische Medien&quot;nicht angezeigt.
      ![Ansicht und Zeitschiene der Liste](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Fehlerbehebung bei selektiver Veröffentlichung {#selective-publish-troubleshoot}

Bei einem Asset, das nicht mit dynamischen Medien synchronisiert wird, bei dem jedoch eine Veröffentlichungsaktion für dynamische Medien ausgelöst wird, wird die folgende Fehlermeldung und Lösung angezeigt:

![Selektiver Veröffentlichungsfehler](/help/assets/assets-dm/selective-publish-error.png)

