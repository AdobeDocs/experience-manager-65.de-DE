---
title: Wie aktivieren Sie die adaptiven Forms-Kernkomponenten in AEM 6.5 Forms?
seo-title: How to enable Adaptive Forms Core Components on AEM 6.5 Forms?
description: Schrittweise Anleitung zur Aktivierung der adaptiven Forms-Kernkomponenten in einer AEM 6.5 Forms-Umgebung.
seo-description: Step-by-Step guide to help you enable Adaptive Forms Core Components on an AEM 6.5 Forms environment.
keywords: Kernkomponenten aktivieren, Kernkomponenten Adaptive Forms, Kernkomponenten in 6.5, adaptive Forms-Kernkomponenten in AEM 6.5, AF-Kernkomponenten in AEM 6.5, AEM 6.5 Forms-Kernkomponenten
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
source-git-commit: 3bc61e56d2fcd9f32c37a7ea04b0ffc6728bfc56
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 9%

---


# Aktivieren der adaptiven Forms-Kernkomponenten in AEM 6.5 Forms {#enable-adaptive-forms-core-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

**Gilt für:** ✅ Kernkomponenten für adaptive Formulare ❎ Foundation-Komponenten für adaptive Formulare.

Durch die Aktivierung der adaptiven Forms-Kernkomponenten können Sie mit der Erstellung, Veröffentlichung und Bereitstellung von [Auf Kernkomponenten basierende adaptive Forms](create-an-adaptive-form-core-components.md) und [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) aus Ihrer AEM 6.5 Forms-Umgebung.

Um HAdaptive Forms-Kernkomponenten in Ihrer AEM 6.5 Forms-Umgebung zu aktivieren, richten Sie eine [AEM Archetyp 41 oder höher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) Basiertes Projekt (mit aktivierten Formularoptionen) auf allen Autoren- und Veröffentlichungsinstanzen.

Dieser Artikel enthält detaillierte Anweisungen zum Einrichten und Bereitstellen AEM Archetyp 41 oder höher-basierten Projekts auf Ihrer AEM 6.5 Forms-Umgebung, um die adaptiven Forms-Kernkomponenten zu aktivieren.


## Voraussetzungen {#prerequisites}

Vor der Aktivierung der adaptiven Forms-Kernkomponenten in einer AEM 6.5 Forms-Umgebung:

* [Upgrade auf AEM 6.5 Forms Service Pack 16 (6.5.16.0) oder höher](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html).

* Installieren Sie die neueste Version von [Apache Maven](https://maven.apache.org/download.cgi).

* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft Visual Studio Code.

## Erstellen und Bereitstellen des neuesten AEM Archetyp-basierten Projekts

So erstellen Sie einen AEM Archetyp 41 oder [later](https://github.com/adobe/aem-project-archetype) Basiertes Projekt erstellen und für alle Autoren- und Veröffentlichungsinstanzen bereitstellen:

1. Melden Sie sich bei Ihrem Computer an, hosten Sie Ihre AEM 6.5 Forms-Instanz und führen Sie sie als Administrator aus.
1. Öffnen Sie die Eingabeaufforderung oder das Terminal und führen Sie den folgenden Befehl aus, um AEM Archetyp-Projekt zu erstellen (mit aktivierten Formularoptionen):

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.15" 
   ```

   * Linux oder Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.15" 
   ```

   Beachten Sie beim Ausführen des oben genannten Befehls die folgenden Punkte:

   * Ändern Sie den Wert der `aemVersion` Eigenschaft aus `6.5.15.0` auf alles andere.

   * Legen Sie die `archetypeVersion` Eigenschaft auf `41` oder höher. Die neueste Version finden Sie im Abschnitt zu den Systemanforderungen unter [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) Dokumentation.

   * Aktualisieren Sie den Befehl, um die spezifischen Werte für Ihre Umgebung widerzuspiegeln, einschließlich der `appTitle`, `appId`, und `groupId`. Legen Sie außerdem den Wert der  `includeFormsenrollment` Eigenschaft auf `y`. Wenn Sie Forms Portal verwenden, legen Sie die `includeExamples=y` , um die Kernkomponenten von Forms Portal in Ihr Projekt aufzunehmen.


1. (Nur für Projekte, die auf Archetyp Version 41 basieren) Nachdem das AEM Archetyp-Projekt erstellt wurde, aktivieren Sie Designs für auf Kernkomponenten basierende adaptive Forms. So aktivieren Sie Designs:

   1. Öffnen Sie die [AEM Archetyp-Projektordner]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html zur Bearbeitung:

   1. Fügen Sie in Zeile 21 den folgenden Code hinzu:

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![Fügen Sie oben genannten Code in Zeile 21 hinzu.](/help/forms/using/assets/code-to-enable-themes.png)

   1. Speichern und schließen Sie die Datei.

1. Aktualisieren Sie das Projekt, um die neueste Version der Forms-Kernkomponenten einzuschließen:

   1. Öffnen Sie die [AEM Archetyp-Projektordner]/pom.xml zur Bearbeitung.
   1. Version von festlegen `core.forms.components.version` und `core.forms.components.af.version` nach [Aktuelle Forms-Kernkomponenten](https://github.com/adobe/aem-core-forms-components/tree/release/650) -Version.

   1. Speichern und schließen Sie die Datei.


1. Nachdem das AEM Archetyp-Projekt erfolgreich erstellt wurde, erstellen Sie das Bereitstellungspaket für Ihre Umgebung. Erstellen des Pakets:

   1. Navigieren Sie zum Stammverzeichnis Ihres AEM Archetypprojekts.

   1. Führen Sie den folgenden Befehl aus, um das AEM Archetyp-Projekt für Ihre Umgebung zu erstellen:

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](/help/forms/using/assets/corecomponent-build-successful.png)


   Nachdem das AEM Archetyp-Projekt erfolgreich erstellt wurde, wird ein AEM-Paket generiert. Sie finden das Paket unter [AEM Archetyp-Projektordner]\all\target\[appid].all-[version].zip

1. Verwenden Sie die [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) zur Bereitstellung der [AEM Archetyp-Projektordner]\all\target\[appid].all-[version]ZIP-Paket auf allen Autoren- und Veröffentlichungsinstanzen.

>[!NOTE]
>
>
>
> * Falls Sie auf Schwierigkeiten beim Zugriff auf das Anmeldedialogfeld auf einer Veröffentlichungsinstanz stoßen, versuchen Sie, das Paket über Package Manager zu installieren, indem Sie die URL verwenden: `http://[Publish Server URL]:[PORT]/system/console` , um sich anzumelden. Auf diese Weise können Sie auf die Anmeldeseite in einer Veröffentlichungsinstanz zugreifen und mit dem Installationsprozess fortfahren.
> * Löschen oder verwerfen Sie das Archetyp-Projekt nicht, nachdem Sie es in Ihrer Umgebung bereitgestellt haben. Das Archetyp-Projekt ist erforderlich, um Ihrer Umgebung benutzerdefinierte und neue Kernkomponenten-Designs für adaptive Forms hinzuzufügen.

Die Kernkomponenten sind für Ihre Umgebung aktiviert. Eine leere, auf Kernkomponenten basierende Vorlage für adaptives Formular und ein Canvas 3.0-Design werden in Ihrer Umgebung bereitgestellt, sodass Sie [Erstellen von Kernkomponenten-basierten adaptiven Forms](create-an-adaptive-form-core-components.md).

## Häufig gestellte Fragen

### Was sind Kernkomponenten?

Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web Content Management (WCM)-Komponenten, mit denen AEM die Entwicklungszeit verkürzen und die Wartungskosten Ihrer Websites reduzieren können.

### Welche Funktionen wurden zur Aktivierung von Kernkomponenten hinzugefügt?


Wenn die adaptiven Forms-Kernkomponenten für Ihre Umgebung aktiviert sind, werden Ihrer Umgebung eine leere, auf Kernkomponenten basierende Vorlage für adaptive Formulare und ein Canvas 3.0-Design hinzugefügt. Nachdem Sie die adaptiven Forms-Kernkomponenten für Ihre Umgebung aktiviert haben, können Sie Folgendes tun:

* Erstellen Sie auf Kernkomponenten basierende adaptive Forms.
* Erstellen Sie auf Kernkomponenten basierende Vorlagen für adaptive Formulare.
* Erstellen Sie benutzerdefinierte Designs für auf Kernkomponenten basierende Vorlagen für adaptive Formulare.
* Bereitstellung der JSON-Darstellungen des auf Kernkomponenten basierenden adaptiven Formulars in Kanälen wie Mobilgeräten, Web, nativen Apps und Diensten, die die Headless-Darstellung eines Formulars erfordern.

## Wie geht es weiter

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Erstellen von Designs für auf Kernkomponenten basierende adaptive Forms](create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Erstellen einer Vorlage für auf Kernkomponenten basierende adaptive Forms](template-editor.md)