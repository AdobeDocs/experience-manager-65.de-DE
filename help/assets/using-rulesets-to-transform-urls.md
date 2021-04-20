---
title: Verwenden von Regelsätzen zum Konvertieren von URLs
description: In Dynamic Media haben Sie die Möglichkeit, Regelsätze anzuwenden, um URLs zu konvertieren. Regelsätze sind Anweisungen, die in einer Skriptsprache (beispielsweise JavaScript) abgefasst werden. Sie werten XML-Daten aus und führen bestimmte Aktionen durch, falls die Daten die festgelegten Bedingungen erfüllen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: Business Practitioner, Administrator,Developer
exl-id: b0ac587b-8592-4d37-9ce0-98a0859c367f
feature: Configuration,Rulesets
translation-type: tm+mt
source-git-commit: c9aec973faf4caef741961d92a6f258646aeddb7
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 98%

---

# Verwenden von Regelsätzen zum Konvertieren von URLs {#using-rulesets-to-transform-urls}

In Dynamic Media haben Sie die Möglichkeit, Regelsätze anzuwenden, um URLs zu konvertieren. Regelsätze sind Anweisungen, die in einer Skriptsprache (beispielsweise JavaScript) abgefasst werden. Sie werten XML-Daten aus und führen bestimmte Aktionen durch, falls die Daten die festgelegten Bedingungen erfüllen. Jede Regel besteht mindestens aus einer Bedingung und einer Aktion. Eine Regel vergleicht die XML-Daten mit den Bedingungen. Wenn eine Bedingung erfüllt ist, wird die entsprechende Aktion durchgeführt. Beispiele für Regelsätze:

* Hinzufügen eines Suffix vom MIME-Typ. Viele Services und Websites benötigen Bildsuffixe. So wird beispielsweise an eine URL das Suffix `.jpg` angefügt.
* Erstellen eines Ordnerpfads zur URL für SEO (Search Engine Optimization)-Zwecke

   Weitere Informationen finden Sie unter [Unterstützung von SEO durch Dynamic Media Classic](/help/assets/assets/s7_seo.pdf).

* Hinzufügen von Metadaten zur URL für SEO (Search Engine Optimization)

   Weitere Informationen finden Sie unter [Unterstützung von SEO durch Dynamic Media Classic](/help/assets/assets/s7_seo.pdf).

* Einstellen der Content-Disposition zum Auslösen eines Downloads
* Vereinfachen der URLs für Vorlagen zur Bildbearbeitung für die Personalisierung. Ändern Sie beispielsweise `rgb{XX,YY,ZZ}` in die RTF-fähige `\redXX\greenYY\blueZZ`

* Anfordern bestimmter zu kodierender Zeichen wie `$`, `{` und `}` und bestimmter für ImageServer zu dekodierender Zeichen. Facebook funktioniert beispielsweise nicht mit URLs, die Sonderzeichen enthalten.

   Siehe [Entfernen von Sonderzeichen aus URLs](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

Im Zusammenhang mit Dynamic Media können Websites, die ein XML-basiertes System zur Verwaltung von Asset-Informationen verwenden, XML-Dateien in Dynamic Media hochladen. Sie können eine dieser Dateien als Regelsatzdatei zur Vorverarbeitung für die Verarbeitung des Dynamic Media-Assets festlegen. Mit dieser Datei wird das Standard-URL-Protokollformat neu strukturiert und an die Geschäftslogik der in Dynamic Media integrierten Systeme angepasst. Sie geben eine XML-Datei an, die als Dateipfad für die Regeldefinitionen dienen soll.

>[!CAUTION]
>
>Verwenden Sie Regelsätze mit Vorsicht. Sie können verhindern, dass Dynamic Media-Inhalte auf Ihrer Website angezeigt werden.

Mit den als Beispiele verfügbaren Regelsätzen können Sie Ihren eigenen Regelsatz erstellen.
 Siehe [Regelsatzreferenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference.html?lang=de).

Stellen Sie wie bei allen Regelsatzerstellungen sicher, dass Ihre XML-Datei gültig ist, bevor Sie sie mit einem XML-Validator-Programm wie xmlvalid hochladen.
Siehe auch [Fehlerbehebung in Regelsätzen](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

Stellen Sie außerdem sicher, dass der Regelsatz zunächst in einer Staging-Umgebung getestet wurde, die sich nicht auf die Live-Produktionsumgebung auswirkt.
Für Produktions- und Testumgebungen sind in der Regel unterschiedliche Anmeldungen erforderlich.

Informationen zum Anmelden finden Sie unter dem [Adobe Dynamic Media Classic Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#sign-in-dmc-app).

<!-- OBSOLETE INFORMATION * **NA staging environment** login page: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA staging environment** login page: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC staging environment** login page: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/) -->

Siehe auch [Verwenden von „Asset“ anstelle von „is“-Bild in einem Regelsatz](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

**So stellen Sie XML-Regelsätze bereit:**

1. Melden Sie sich bei Ihrer [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#sign-in-dmc-app) an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Laden Sie Ihre Regelsatzdatei wie folgt hoch:

   * Klicken Sie in der Symbolleiste für globale Navigation auf **[!UICONTROL Hochladen]**.
   * Klicken Sie auf der Seite **[!UICONTROL Hochladen]** in der linken oberen Ecke auf **[!UICONTROL Durchsuchen]**.
   * Navigieren Sie im Dialogfeld **[!UICONTROL Öffnen]** zu Ihrer Regelsatzdatei (XML).
   * Wählen Sie die Datei aus und klicken Sie auf **[!UICONTROL Öffnen]**.
   * Wählen Sie rechts auf der Seite **[!UICONTROL Hochladen]** einen Zielordner für die Regelsatzdatei aus.
   * Stellen Sie am unteren Rand der Seite sicher, dass die Option **[!UICONTROL Nach Hochladen veröffentlichen]** aktiviert ist.
   * Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Upload starten]**.
   * Klicken Sie in der globalen Navigationsleiste auf **[!UICONTROL Aufträge]**, um den Status der Upload-Aufträge zu prüfen. Wenn in der Spalte **[!UICONTROL Status]** auf der Seite **[!UICONTROL Auftrag]** der Status „Hochladen abgeschlossen“ angezeigt wird, fahren Sie mit den nächsten Schritten fort.

1. Klicken Sie in der Navigationsleiste oben auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinrichtung > Image-Server]**.
1. Suchen Sie auf der Seite **[!UICONTROL Veröffentlichung zum Image-Server]** in der Gruppe **[!UICONTROL Katalogverwaltung]** den Pfad **[!UICONTROL Dateipfad für Regeldefinitionen]** und klicken Sie auf **[!UICONTROL Auswählen]**.
1. Klicken Sie auf der Seite **[!UICONTROL Regeldefinitionsdatei (XML) auswählen]** auf die Regelsatzdatei und dann in der rechten unteren Ecke der Seite auf **[!UICONTROL Auswählen]**.
1. Klicken Sie in der rechten unteren Ecke der Seite „Einstellungen“ auf **[!UICONTROL Schließen]**.
1. Führen Sie einen Auftrag zur Veröffentlichung des Image-Servers aus.

   Die Bedingungen des Regelsatzes werden auf die Anforderungen an die Live-Image-Server von Dynamic Media angewendet.

   Wenn Sie Änderungen an der Regelsatzdatei vornehmen, werden die Änderungen sofort angewendet, wenn Sie die aktualisierte Regelsatzdatei erneut hochladen oder veröffentlichen.
