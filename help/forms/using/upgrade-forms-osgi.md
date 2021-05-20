---
title: Aktualisierung auf AEM 6.5 Forms
seo-title: Aktualisierung auf AEM 6.5 Forms
description: Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren.
seo-description: Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Administrator
exl-id: 1e39455e-f588-42a2-91f5-daefcfed82a0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 69%

---

# Aktualisierung auf AEM 6.5 Forms auf OSGi {#upgrade-to-aem-forms-osgi}

Sie können direkt von AEM 6.3 Forms und AEM 6.4 Forms auf AEM 6.5 Forms aktualisieren.

Der direkte Aktualisierungspfad von **AEM 6.0 Forms, AEM 6.1 Forms** und **AEM 6.2 Forms** ist nicht AEM 6.5 Forms verfügbar. Führen Sie ein Zwischenupgrade von [auf AEM 6.2 Forms](https://helpx.adobe.com/de/experience-manager/6-2/forms/using/upgrade.html), [Upgrade auf AEM 6.3 Forms](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/upgrade.html) oder [Upgrade auf AEM 6.4 Forms](/help/forms/using/upgrade.md) durch und aktualisieren Sie dann von AEM 6.3 Forms oder AEM 6.4 Forms auf AEM 6.5.

Führen Sie die folgenden Schritte aus, um von AEM 6.3 Forms oder AEM 6.4 Forms auf AEM 6.5 Forms zu aktualisieren:

1. Aktualisieren Sie die bestehende AEM-Instanz auf AEM 6.5. Dies umfasst die folgenden Schritte:

   1. Installieren Sie das aktuelle Service Pack und Patches für AEM 6.3 Forms bzw. AEM 6.4 Forms. Weitere Informationen finden Sie unter [AEM Sustenance Hub](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).
   1. Bereiten Sie die Quellinstanz für die Aktualisierung vor. Ausführliche Anweisungen finden Sie im Artikel [Aktualisieren auf AEM 6.5](/help/sites-deploying/upgrade.md).
   1. Laden Sie [AEM 6.5 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software) herunter.
   1. **(Nur Unix/Linux-basierte Installationen)** Wenn Sie UNIX oder Linux als Betriebssystem verwenden, öffnen Sie das Terminalfenster, um zu dem Ordner mit „crx-quickstart“ zu navigieren, und führen Sie den folgenden Befehl aus:

      `chmod -R 755 ../crx-quickstart`

   1. Aktualisieren Sie Ihre AEM-Instanz auf AEM 6.3. Eine schrittweise Anleitung finden Sie unter [Aktualisieren auf AEM 6.5](/help/sites-deploying/upgrade.md).

      Bevor Sie mit den nächsten Schritten fortfahren, warten Sie, bis die Nachrichten ServiceEvent REGISTERED und ServiceEvent UNREGISTERED ServiceEvent nicht mehr in der Datei &lt;crx-repository>/error.log angezeigt werden.

      >[!NOTE]
      >
      >Sobald der Server ausgeführt wird, bleiben einige AEM Forms-Pakete im Installationsstatus. Die Anzahl von Paketen kann für jede Installation variieren. Sie können den Zustand dieser Pakete ignorieren. Die Bundles sind unter https://&#39;[server]:[port]&#39;/system/console/ aufgeführt.

1. Installieren des AEM Forms-Add-on-Pakets. Dies umfasst die folgenden Schritte:

   1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
   1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
   1. Im Abschnitt **[!UICONTROL Filter]**:
      1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
      1. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads suchen]** verwenden, um die Ergebnisse zu filtern.
   1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem, wählen Sie **[!UICONTROL Endbenutzer-Lizenzbedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
   1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
   1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

      Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

      >[!NOTE]
      >
      >Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „&lt;crx-Repository>/error.log“ angezeigt werden und das Protokoll stabil ist. Beachten Sie zudem, dass einige Pakete im installierten Zustand verbleiben können. Sie können den Status dieser Pakete ignorieren.

1. Starten Sie die AEM-Instanz neu.

1. Führen Sie auf die Installation folgenden Aufgaben durch.

   * **Migrationsdienstprogramm ausführen**

      Das Migrationsdienstprogramm macht die adaptiven Formulare und Correspondence Management-Assets aus früheren Versionen kompatibel mit AEM 6.5 Forms. Sie können das Dienstprogramm von AEM Software Distribution herunterladen. Informationen in Einzelschritten zur Konfiguration und Verwendung des Migrationsdienstprogramms finden Sie in der Dokumentation zum [Migrationsdienstprogramm](../../forms/using/migration-utility.md).

      Wenn Sie [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) mit der Datenbank verwenden und von einer früheren Version aktualisieren, führen Sie nach der Aktualisierung die folgenden SQL-Abfragen aus:

      ```sql
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```sql
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Nur bei Aktualisierung von AEM 6.2 Forms oder früheren Versionen) Konfigurieren Sie Adobe Sign neu**

      Wenn Adobe Sign in der vorherigen Version von AEM Forms konfiguriert war, müssen Sie Adobe Sign über die AEM-Cloud-Services erneut konfigurieren. Weitere Informationen finden Sie unter [Adobe-Zeichen mit AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Unterstützung für jQuery**

      In AEM 6.5 Forms wird die jQuery-Version auf 3.2.1 aktualisiert und die jQuery-UI-Version wird auf 1.12.1 aktualisiert. AEM Form verwendet JQuery im Modus **noConflict** . Wenn Sie also eine andere jQuery-Version verwenden, werden bei der Durchführung eines Upgrades keine Probleme angezeigt. Wenn Sie jedoch auf AEM 6.5 Forms aktualisieren:

      * Stellen Sie sicher, dass Ihre benutzerdefinierten Komponenten, falls vorhanden, mit unterstützten jQuery-Versionen kompatibel sind.
      * Entfernen Sie nicht unterstützte APIs aus den benutzerdefinierten Komponenten. Eine Liste der entfernten APIs finden Sie im [Upgrade-Handbuch](https://jquery.com/upgrade-guide/3.0/) . Beispielsweise wird die Unterstützung für die APIs load(), .unload() und .error() entfernt. Verwenden Sie die Methode .on() anstelle der oben genannten APIs. Ändern Sie beispielsweise $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).
   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Analysen und Berichte neu**

      In AEM 6.4 Forms stehen keine Traffic-Variablen für Quelle und Erfolgsereignis für Impressionen zur Verfügung. Wenn Sie von AEM 6.2 Forms oder vorherigen Versionen aktualisieren, sendet AEM Forms daher keine Daten mehr an den Adobe Analytics-Server und es stehen keine Analyseberichte für adaptive Formulare zur Verfügung. Darüber hinaus werden mit AEM 6.4 Forms Traffic-Variablen für die Version der Formularanalyse und das Erfolgsereignis mit Angabe der Dauer der Aktivität in einem Feld eingeführt. Konfigurieren Sie daher die Analysen und Berichte erneut für Ihre AEM Forms-Umgebung. Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analyse und Berichten](../../forms/using/configure-analytics-forms-documents.md).


1. Vergewissern Sie sich, dass der Server erfolgreich aktualisiert und alle Daten migriert wurden und dass der Server einwandfrei funktioniert.

   * **Überprüfen Sie den Status der Pakete:** Stellen Sie sicher, dass alle Pakete sich im aktiven Status befinden.
   * **Überprüfen Sie Replikation und Rückwärtsreplikation:** Veröffentlichen Sie einige migrierte Formulare, füllen Sie sie aus und übermitteln Sie sie. Überprüfen Sie auch die gesendeten Daten.
   * **Überprüfen Sie den Zugriff auf die Administrator- und Benutzeroberflächen:** Melden Sie sich über ein Administratorkonto bei der AEM-Instanz an und überprüfen Sie, ob Sie Zugriff auf die folgenden URLs haben:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Wenn Sie von 6.3 Forms auf AEM 6.5 Forms aktualisieren, verwenden Sie die geänderten Pfade zur Anpassung, die Sie neu erstellen. Sie finden die vollständige Liste der geänderten Pfade unter [Forms Repository-Restrukturierung in AEM](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md).
