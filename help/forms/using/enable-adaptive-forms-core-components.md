---
title: Aktivieren der Kernkomponenten für adaptive Formulare in AEM 6.5 Forms
description: Schrittweise Anleitung zur Aktivierung der Kernkomponenten für adaptive Formulare in einer AEM 6.5 Forms-Umgebung
keywords: Kernkomponenten aktivieren, Kernkomponenten für adaptive Formulare, Kernkomponenten in 6.5, Kernkomponenten für adaptive Formulare in AEM 6.5, AF-Kernkomponenten in AEM 6.5, AEM 6.5 Forms-Kernkomponenten
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms, Core Components
exl-id: 6585ea71-6242-47d3-bc59-6f603cf507b6
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '968'
ht-degree: 100%

---

# Aktivieren der Kernkomponenten für adaptive Formulare in AEM 6.5 Forms {#enable-adaptive-forms-core-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

Durch Aktivieren der Kernkomponenten für adaptive Formulare können Sie mit der Erstellung, Veröffentlichung und Bereitstellung von [auf Kernkomponenten basierenden adaptiven Formularen](create-an-adaptive-form-core-components.md) und [adaptiven Headless-Formularen](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) aus Ihrer AEM 6.5 Forms-Umgebung beginnen.

Um Kernkomponenten für adaptive Formulare in Ihrer AEM 6.5 Forms-Umgebung zu aktivieren, richten Sie ein auf [AEM Archetyp 41 oder höher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) basierendes Projekt ein und stellen Sie es (mit aktivierten Formularoptionen) für all Ihre Autoren- und Veröffentlichungsinstanzen bereit.

Dieser Artikel enthält detaillierte Anweisungen zum Einrichten und Bereitstellen von einem auf AEM Archetyp 41 oder höher basierenden Projekt in der AEM 6.5 Forms-Umgebung, um die Kernkomponenten für adaptive Formulare zu aktivieren. In der nachstehenden Liste finden Sie für **AEM 6.5** kompatible Versionen zur Aktivierung der Kernkomponenten für Formulare:

## Voraussetzungen {#prerequisites}

Vor der Aktivierung von Kernkomponenten für adaptive Formulare in der AEM 6.5 Forms-Umgebung:

* [Nehmen Sie ein Upgrade auf AEM 6.5 Forms Service Pack 16 (6.5.16.0) oder höher vor](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de).

* Installieren Sie die neueste Version von [Apache Maven](https://maven.apache.org/download.cgi).

* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft Visual Studio Code.

## Erstellen Sie ein auf dem neuesten AEM Archetyp basierendes Projekt und stellen Sie es bereit

So erstellen Sie ein auf AEM Archetyp 41 oder [höher](https://github.com/adobe/aem-project-archetype) basierendes Projekt und stellen es für alle Authoring- und Publishing-Instanzen bereit:

1. Melden Sie sich bei Ihrem Computer an, hosten Sie Ihre AEM 6.5 Forms-Instanz und führen Sie sie als Administrator aus.
1. Öffnen Sie die Eingabeaufforderung oder das Terminal und führen Sie den folgenden Befehl aus, um ein AEM Archetyp-Projekt zu erstellen (mit aktivierten Formularoptionen):

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

   * Ändern Sie nicht den Wert der Eigenschaft `aemVersion` von `6.5.15.0` auf einen anderen Wert.

   * Legen Sie die Eigenschaft `archetypeVersion` auf `41` oder höher fest. Die neueste Version finden Sie im Abschnitt „Systemanforderungen“ in der Dokumentation zum [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype).

   * Aktualisieren Sie den Befehl, um die spezifischen Werte für Ihre Umgebung widerzuspiegeln, einschließlich `appTitle`, `appId` und `groupId`. Legen Sie außerdem den Wert der Eigenschaft `includeFormsenrollment` auf `y` fest. Wenn Sie Forms Portal verwenden, legen Sie die Option `includeExamples=y` fest, um die Kernkomponenten von Forms Portal in Ihr Projekt aufzunehmen.


1. (Nur für Projekte, die auf dem Archetyp Version 41 basieren) Nachdem das AEM-Archetyp-Projekt erstellt wurde, aktivieren Sie Designs für auf Kernkomponenten basierende adaptive Formulare. So aktivieren Sie Designs:

   1. Öffnen Sie den [AEM-Archetyp-Projektordner]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html zur Bearbeitung:

   1. Fügen Sie in Zeile 21 den folgenden Code hinzu:

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![Fügen Sie den oben genannten Code in Zeile 21 hinzu](/help/forms/using/assets/code-to-enable-themes.png)

   1. Speichern und schließen Sie die Datei.

1. Aktualisieren Sie das Projekt, um die neueste Version der Forms-Kernkomponenten einzuschließen:

   1. Öffnen Sie den [AEM-Archetyp-Projektordner]/pom.xml zur Bearbeitung.
   1. Legen Sie die Version von `core.forms.components.version` und `core.forms.components.af.version` auf die [aktuelle Version der Kernkomponenten für Formulare](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/version#aem-as-form-version-history) fest und stellen Sie sicher, dass beide dieselbe Version haben wie die in der Tabelle angegebenen **Kernkomponenten für Formulare**. Legen Sie die Version von `core.wcm.components.version` gemäß der [WCM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/versions.html?lang=de) fest.

      >[!WARNING]
      >
      >* Wenn Sie ein Archetyp-Projekt mit Version 45 erstellen, setzt `[AEM Archetype Project Folder]/pom.xml` zunächst die Version der Formular-Kernkomponenten auf 1.1.28. Aktualisieren Sie vor dem Erstellen oder Bereitstellen des Archetyp-Projekts die Version der Formular-Kernkomponenten auf 1.1.26. Die neueste Version finden Sie im [Versionsverlauf von AEM 6.5 Forms](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/version#aem-as-form-version-history).

      >[!NOTE]
      >
      >* Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs für Übermitteln, Vorausfüllen und andere Funktionen auf der Dispatcher-Ebene in die Zulassungsliste eintragen.

   1. Speichern und schließen Sie die Datei.


1. Nachdem das AEM-Archetyp-Projekt erfolgreich erstellt wurde, erstellen Sie das Bereitstellungspaket für Ihre Umgebung. Erstellen des Pakets:

   1. Navigieren Sie zum Stammverzeichnis Ihres AEM-Archetyp-Projekts.

   1. Führen Sie den folgenden Befehl aus, um das AEM-Archetyp-Projekt für Ihre Umgebung zu erstellen:

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](/help/forms/using/assets/corecomponent-build-successful.png)


   Nachdem das AEM-Archetyp-Projekt erfolgreich erstellt wurde, wird ein AEM-Paket generiert. Sie finden das Paket im [AEM-Archetyp-Projektordner]\all\target\[appid].all-[version].zip

1. Verwenden Sie den [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) zur Bereitstellung des Pakets [AEM-Archetyp-Projektordner]\all\target\[appid].all-[version].zip auf allen Authoring- und Publishing-Instanzen.

>[!NOTE]
>
>
>
> * Falls Sie Schwierigkeiten haben, den Anmeldedialog auf einer Veröffentlichungsinstanz aufzurufen, um das Paket über den Package Manager zu installieren, versuchen Sie, sich über die URL `http://[Publish Server URL]:[PORT]/system/console` anzumelden. Auf diese Weise können Sie auf die Anmeldeseite bei der Veröffentlichungsinstanz zugreifen, sodass Sie mit dem Installationsprozess fortfahren können.
> * Löschen oder verwerfen Sie das Archetyp-Projekt nicht, nachdem Sie es in Ihrer Umgebung bereitgestellt haben. Das Archetyp-Projekt ist erforderlich, um Ihrer Umgebung benutzerdefinierte und neue Kernkomponenten-Designs für adaptive Formulare hinzuzufügen.

Die Kernkomponenten sind für Ihre Umgebung aktiviert. Eine leere, auf Kernkomponenten basierende Vorlage für ein adaptives Formular und ein Canvas 3.0-Design werden in Ihrer Umgebung bereitgestellt, sodass Sie [auf Kernkomponenten basierende adaptive Formulare erstellen können](create-an-adaptive-form-core-components.md).

## Häufig gestellte Fragen

### Was sind Kernkomponenten?

Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web-Content-Management-Komponenten (WCM) für AEM, um die Entwicklungszeit zu verkürzen und die Wartungskosten Ihrer Websites zu senken.

### Welche Funktionen werden durch die Aktivierung der Kernkomponenten hinzugefügt?


Wenn die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert sind, werden Ihrer Umgebung eine leere, auf Kernkomponenten basierende Vorlage für adaptive Formulare und ein Canvas 3.0-Design hinzugefügt. Nachdem Sie die Kernkomponenten der adaptiven Formulare für Ihre Umgebung aktiviert haben, können Sie Folgendes tun:

* Erstellen Sie adaptive Formulare auf Grundlage der Kernkomponenten.
* Erstellen Sie Vorlagen für adaptive Formulare auf Grundlage der Kernkomponenten.
* Erstellen Sie benutzerdefinierte Vorlagen-Designs für adaptive Formulare auf Grundlage der Kernkomponenten.
* Stellen Sie JSON-Darstellungen adaptiver Formulare auf Grundlage der Kernkomponenten für Kanäle wie Mobile, Web, native Apps und Dienste bereit, die eine Headless-Darstellung des Formulars erfordern.

## Wie geht es weiter

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Erstellen von Designs für auf Kernkomponenten basierende adaptive Formulare](create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Erstellen einer Vorlage für auf Kernkomponenten basierende adaptive Formulare](template-editor.md)
