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
translation-type: tm+mt
source-git-commit: 0a7c243589b410a671674b85d27fad158fe96b2a

---


# Aktualisierung auf AEM 6.5 Forms auf OSGi {#upgrade-to-aem-forms-osgi}

Sie können direkt von AEM 6.3 Forms und AEM 6.4 Forms auf AEM 6.5 Forms aktualisieren.

Direct upgrade path from **AEM 6.0 Forms, AEM 6.1 Forms**, and **AEM 6.2 Forms** to AEM 6.5 Forms is not available. Perform an intermediate [upgrade to AEM 6.2 Forms](https://helpx.adobe.com/experience-manager/6-2/forms/using/upgrade.html), [upgrade to AEM 6.3 Forms](https://helpx.adobe.com/experience-manager/6-3/forms/using/upgrade.html), or [upgrade to AEM 6.4 Forms](/help/forms/using/upgrade.md) and then upgrade from AEM 6.3 Forms, or AEM 6.4 Forms to AEM 6.5 Forms.

Führen Sie die folgenden Schritte aus, um von AEM 6.3 Forms oder AEM 6.4 Forms auf AEM 6.5 Forms zu aktualisieren:

1. Aktualisieren Sie die bestehende AEM-Instanz auf AEM 6.5. Dies umfasst die folgenden Schritte:

   1. Installieren Sie das aktuelle Service Pack und Patches für AEM 6.3 Forms bzw. AEM 6.4 Forms. Weitere Informationen finden Sie unter [AEM Sustenance Hub](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).
   1. Bereiten Sie die Quellinstanz für die Aktualisierung vor. Ausführliche Anweisungen finden Sie im Artikel [Aktualisieren auf AEM 6.5](/help/sites-deploying/upgrade.md).
   1. Laden Sie [AEM 6.5 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software) herunter.
   1. **(Nur Unix/Linux-basierte Installationen)** Wenn Sie UNIX oder Linux als Betriebssystem verwenden, öffnen Sie das Terminalfenster, um zu dem Ordner mit „crx-quickstart“ zu navigieren, und führen Sie den folgenden Befehl aus:

      `chmod -R 755 ../crx-quickstart`

   1. Upgrade your AEM instance to AEM 6.3. For step by step instructions, see [Upgrading to AEM 6.5](/help/sites-deploying/upgrade.md).

      Bevor Sie mit den nächsten Schritten fortfahren, warten Sie, bis die Nachrichten ServiceEvent REGISTERED und ServiceEvent UNREGISTERED ServiceEvent nicht mehr in der Datei &lt;crx-repository>/error.log angezeigt werden.

      >[!NOTE]
      >
      >Sobald der Server ausgeführt wird, bleiben einige AEM Forms-Pakete im Installationsstatus. Die Anzahl von Paketen kann für jede Installation variieren. Sie können den Zustand dieser Pakete ignorieren. The bundles are listed at https://[server]:[port]/system/console/.

1. Installieren des AEM Forms-Add-on-Pakets. Dies umfasst die folgenden Schritte:

   1. Melden Sie sich beim AEM-Server als Administrator an und öffnen Sie Package Share. The default URL of the package share is `https://[server]:[port]/crx/packageshare`.
   1. Suchen Sie in Package Share nach **Add-On-Pakete für AEM 6.5 Forms** und klicken Sie auf das Paket für Ihr Betriebssystem und dann auf **Herunterladen**. Lesen und akzeptieren Sie die Lizenzvereinbarung und klicken Sie auf **OK**. Der Download wird gestartet. Nachdem der Download abgeschlossen ist, wird das Wort **Heruntergeladen** neben dem Paket angezeigt.

      Alternately, you can also use the hyperlinks listed in [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) to manually download a package.

   1. Nachdem der Download abgeschlossen ist, klicken Sie auf **Heruntergeladen**. Sie werden zum Paketmanager weitergeleitet. Suchen Sie im Paketmanager das heruntergeladene Paket und klicken Sie auf **Installieren**.

      Wenn Sie das Paket manuell über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) angegeben ist, öffnen Sie AEM Package Manager, klicken Sie auf **Paket hochladen**, wählen Sie das heruntergeladene Paket aus und klicken Sie auf „Hochladen“. Nachdem Sie das Paket hochgeladen haben, klicken Sie auf den Paketnamen und dann auf **Installieren.**

      >[!NOTE]
      >
      >Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „&lt;crx-Repository>/error.log“ angezeigt werden und das Protokoll stabil ist. Beachten Sie zudem, dass einige Pakete im installierten Zustand verbleiben können. Sie können den Status dieser Pakete ignorieren.

   1. Starten Sie die AEM-Instanz neu.

1. Führen Sie auf die Installation folgenden Aufgaben durch.

   * **Migrationsdienstprogramm ausführen**

      Das Migrationsdienstprogramm macht die adaptiven Formulare und Correspondence Management-Assets aus früheren Versionen kompatibel mit AEM 6.5 Forms. Sie können das Dienstprogramm von AEM Package Share herunterladen. Informationen in Einzelschritten zur Konfiguration und Verwendung des Migrationsdienstprogramms finden Sie in der Dokumentation zum [Migrationsdienstprogramm](../../forms/using/migration-utility.md).

      Wenn Sie [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) mit der Datenbank verwenden und von einer früheren Version aktualisieren, führen Sie nach der Aktualisierung die folgenden SQL-Abfragen aus:

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Nur bei Aktualisierung von AEM 6.2 Forms oder früheren Versionen) Adobe Sign neu konfigurieren**

      Wenn Adobe Sign in der vorherigen Version von AEM Forms konfiguriert war, müssen Sie Adobe Sign über die AEM-Cloud-Services erneut konfigurieren. Weitere Informationen finden Sie unter [Adobe-Zeichen mit AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Unterstützung für jQuery**

      In AEM 6.5 Forms wird die Version von jQuery auf 3.2.1 aktualisiert und die jQuery UI-Version auf 1.12.1 aktualisiert. AEM Form verwendet JQuery im **Modus &quot;Kein Konflikt&quot;** . Wenn Sie also eine andere jQuery-Version verwenden, werden während der Aktualisierung keine Probleme angezeigt. Wenn Sie jedoch auf AEM 6.5 Forms aktualisieren:

      * Stellen Sie sicher, dass Ihre benutzerdefinierten Komponenten, falls vorhanden, mit unterstützten jQuery-Versionen kompatibel sind.
      * Entfernen Sie nicht unterstützte APIs aus den benutzerdefinierten Komponenten. Eine Liste der entfernten APIs finden Sie im [Aktualisierungshandbuch](https://jquery.com/upgrade-guide/3.0/) . Beispielsweise wird die Unterstützung für die APIs load(), .unload() und .error() entfernt. Verwenden Sie die Methode .on() anstelle der oben genannten APIs. Ändern Sie beispielsweise $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).
   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Analysen und Berichte neu**

      In AEM 6.4 Forms stehen keine Traffic-Variablen für Quelle und Erfolgsereignis für Impressionen zur Verfügung. Wenn Sie von AEM 6.2 Forms oder vorherigen Versionen aktualisieren, sendet AEM Forms daher keine Daten mehr an den Adobe Analytics-Server und es stehen keine Analyseberichte für adaptive Formulare zur Verfügung. Darüber hinaus werden mit AEM 6.4 Forms Traffic-Variablen für die Version der Formularanalyse und das Erfolgsereignis mit Angabe der Dauer der Aktivität in einem Feld eingeführt. Konfigurieren Sie daher die Analysen und Berichte erneut für Ihre AEM Forms-Umgebung. Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analyse und Berichten](../../forms/using/configure-analytics-forms-documents.md).


1. Vergewissern Sie sich, dass der Server erfolgreich aktualisiert und alle Daten migriert wurden und dass der Server einwandfrei funktioniert.

   * **Überprüfen Sie den Status der Pakete:** Stellen Sie sicher, dass alle Pakete sich im aktiven Status befinden.
   * **Überprüfen Sie Replikation und Rückwärtsreplikation:** Veröffentlichen Sie einige migrierte Formulare, füllen Sie sie aus und übermitteln Sie sie. Überprüfen Sie auch die gesendeten Daten.
   * **Überprüfen Sie den Zugriff auf die Administrator- und Benutzeroberflächen:** Melden Sie sich über ein Administratorkonto bei der AEM-Instanz an und überprüfen Sie, ob Sie Zugriff auf die folgenden URLs haben:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`
   >[!NOTE]
   In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Wenn Sie von 6.3 Forms auf AEM 6.5 Forms aktualisieren, verwenden Sie die geänderten Pfade zur Anpassung, die Sie neu erstellen. Sie finden die vollständige Liste der geänderten Pfade unter [Forms Repository-Restrukturierung in AEM](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md).

