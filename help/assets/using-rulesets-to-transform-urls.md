---
title: Regelsätze zum Konvertieren von URLs
description: In Dynamic Media haben Sie die Möglichkeit, Regelsätze anzuwenden, um URLs zu konvertieren. Regelsätze sind Anweisungen, die in einer Skriptsprache (beispielsweise JavaScript) abgefasst werden. Sie werten XML-Daten aus und führen bestimmte Aktionen durch, falls die Daten die festgelegten Bedingungen erfüllen.
uuid: 9fed0c83-67b7-4483-a9b4-322e6a483449
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: abcff903-204b-4ab6-87d8-6f0ce63d7b41
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Verwenden von Regelsätzen zum Transformieren von URLs {#using-rulesets-to-transform-urls}

In Dynamic Media haben Sie die Möglichkeit, Regelsätze anzuwenden, um URLs zu konvertieren. Regelsätze sind Anweisungen, die in einer Skriptsprache (beispielsweise JavaScript) abgefasst werden. Sie werten XML-Daten aus und führen bestimmte Aktionen durch, falls die Daten die festgelegten Bedingungen erfüllen. Jede Regel besteht mindestens aus einer Bedingung und einer Aktion. Eine Regel vergleicht die XML-Daten mit den Bedingungen. Wenn eine Bedingung erfüllt ist, wird die entsprechende Aktion durchgeführt. Beispiele für Regelsätze:

* Hinzufügen eines Suffix vom MIME-Typ. Many services and websites require image suffixes, such as adding `.jpg` to a URL.
* Erstellen eines Ordnerpfads zur URL für SEO (Search Engine Optimization)-Zwecke

    Siehe [Unterstützung von SEO durch Adobe Scene7 Publishing System](/help/assets/assets/s7_seo.pdf)

* Hinzufügen von Metadaten zur URL für SEO (Search Engine Optimization)

    Siehe [Unterstützung von SEO durch Adobe Scene7 Publishing System](/help/assets/assets/s7_seo.pdf)

* Einstellen der Content-Disposition zum Auslösen eines Downloads
* Vereinfachen der URLs für Vorlagen zur Bildbearbeitung für die Personalisierung. So können Sie zum Beispiel `rgb{XX,YY,ZZ}` die RTF-fähige `\redXX\greenYY\blueZZ`

* Request certain characters to be encoded such as `$`, `{`, and `}`, and certain characters to be decoded toward ImageServer. Facebook funktioniert beispielsweise nicht mit URLs, die Sonderzeichen enthalten.

   Siehe [Entfernen von Sonderzeichen von URLs](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

Im Zusammenhang mit Dynamic Media können Websites, die ein XML-basiertes System zur Verwaltung von Asset-Informationen verwenden, XML-Dateien in Dynamic Media hochladen. Sie können eine dieser Dateien als Regelsatzdatei zur Vorverarbeitung für die Verarbeitung des Dynamic Media-Assets festlegen. Mit dieser Datei wird das Standard-URL-Protokollformat neu strukturiert und an die Geschäftslogik der in Dynamic Media integrierten Systeme angepasst. Sie geben eine XML-Datei an, die als Dateipfad für die Regeldefinitionen dienen soll.

>[!CAUTION]
>
>Gehen Sie bei der Verwendung von Regelsätzen vorsichtig vor; Sie können verhindern, dass Inhalte für dynamische Medien auf Ihrer Website angezeigt werden.

Mit den als Beispiele verfügbaren Regelsätzen können Sie Ihren eigenen Regelsatz erstellen.
 Siehe [ Regelsatzverweis](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/image_catalog/c_rule_set_reference.html). 

Stellen Sie wie bei allen Regelsatzerstellungen sicher, dass Ihre XML-Datei gültig ist, bevor Sie sie mit einem XML-Validator-Programm wie xmlvalid hochladen.
Siehe auch [Fehlerbehebung in Regelsätzen](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

Stellen Sie außerdem sicher, dass der Regelsatz zunächst in einer Staging-Umgebung getestet wurde, die sich nicht auf die Live-Produktionsumgebung auswirkt.
Für Produktions- und Testumgebungen sind in der Regel unterschiedliche Anmeldungen erforderlich.

* **NA-Anmeldeseite für die Staging-Umgebung** : [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **Anmeldeseite der** EMEA-Staging-Umgebung: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **Anmeldeseite der JAPAC-Staging-Umgebung** : [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/)

Siehe auch [Verwenden von „Asset“ statt „is“-Bild in Regelsatz](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

**So stellen Sie XML-Regelsätze bereit:** 

1. Melden Sie sich bei Ihrem Konto für Dynamic Media Classic an:

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Ihre Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Laden Sie Ihre Regelsatzdatei wie folgt hoch:

   * Klicken Sie in der Symbolleiste für globale Navigation auf **[!UICONTROL Hochladen]**.
   * On the **[!UICONTROL Upload]** page, near the upper-left corner, click **[!UICONTROL Browse]**.
   * In the **[!UICONTROL Open]** dialog box, browse to your rule set file (XML).
   * Wählen Sie die Datei aus und klicken Sie auf **[!UICONTROL Öffnen]**.
   * On the right side of the **[!UICONTROL Upload]** page, select a destination folder for the rule set file.
   * Stellen Sie am unteren Rand der Seite sicher, dass die Option **[!UICONTROL Nach Hochladen veröffentlichen]** aktiviert ist.
   * Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Upload starten]**.
   * Klicken Sie in der globalen Navigationsleiste auf **[!UICONTROL Aufträge]**, um den Status der Upload-Aufträge zu prüfen. When the **[!UICONTROL Status]** column on the **[!UICONTROL Job]** page says Upload Done, continue to the next steps.

1. Klicken Sie in der Navigationsleiste im oberen Teil der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinrichtung > Image-Server]**.
1. On the **[!UICONTROL Image Server Publish]** page, under the **[!UICONTROL Catalog Management]** group, locate **[!UICONTROL Rule Set Definition File Path]**, then click **[!UICONTROL Select]**.
1. On the **[!UICONTROL Select Rule Set Definition File (XML)]** page, browse to your rule set file, then in the lower-right corner of the page, click **[!UICONTROL Select]**.
1. Klicken Sie in der rechten unteren Ecke der Seite „Einstellungen“ auf **[!UICONTROL Schließen]**.
1. Führen Sie einen Auftrag zur Veröffentlichung des Image-Servers aus.

   Die Bedingungen des Regelsatzes werden auf die Anforderungen an die Live-Image-Server von Dynamic Media angewendet.

   Wenn Sie Änderungen an der Regelsatzdatei vornehmen, werden die Änderungen sofort angewendet, wenn Sie die aktualisierte Regelsatzdatei erneut hochladen oder veröffentlichen.

