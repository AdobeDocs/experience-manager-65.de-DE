---
title: Erstellen einer benutzerdefinierten adaptiven Formularvorlage
description: In diesem Artikel wird beschrieben, wie Sie benutzerdefinierte adaptive Formularvorlagen erstellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 35b50573-0be8-469d-a1ac-f51b9aaa5fef
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 100%

---

# Erstellen einer benutzerdefinierten adaptiven Formularvorlage{#creating-a-custom-adaptive-form-template}

>[!NOTE]
>
>AEM Forms hat dynamische Vorlagen eingeführt. Mit dem AEM Sites-Vorlageneditor können Sie [dynamische Vorlagen erstellen oder bearbeiten](../../forms/using/template-editor.md). Bei den im folgenden Artikel genannten Vorlagen handelt es sich um statische Vorlagen. Diese sind bei einer Standardinstallation nicht verfügbar. [Kompatibilitätspaket installieren](../../forms/using/compatibility-package.md), um diese Vorlagen in Ihrer Umgebung zu erhalten.

## Voraussetzungen {#prerequisites}

* Grundlagen zu den [Seitenvorlagen](/help/sites-authoring/templates.md) und zum [Authoring adaptiver Formulare](https://helpx.adobe.com/de/aem-forms/6-1/introduction-forms-authoring.html?lang=de-DE)

* Grundlagen zu den [Client-seitigen Bibliotheken](/help/sites-developing/clientlibs.md) in AEM

## Adaptive Formularvorlage {#adaptive-form-template}

Eine adaptive Formularvorlage ist eine spezielle AEM-Seitenvorlage mit bestimmten Eigenschaften und einer vorgegebenen Inhaltsstruktur, aus der ein adaptives Formular erstellt wird. Die Vorlage hat vorkonfigurierte Layouts, Stile und eine einfache, bereits vorgegebene Inhaltsstruktur.

Änderungen an der Inhaltsstruktur einer Formularvorlage werden nicht in das aus der Vorlage erstellte Formular übernommen.

## Adaptive Standardformularvorlagen {#default-adaptive-form-templates}

Ein AEM-Schnellstart bietet die folgenden adaptiven Formularvorlagen:

* Vorlage für eine Umfrage: Ermöglicht die Erstellung eines einseitigen adaptiven Formulars mithilfe eines responsiven Layouts mit mehreren vorkonfigurierten Spalten. Das Layout passt sich automatisch an die jeweilige Bildschirmgröße an.
* Einfache Registrierungsvorlage: Ermöglicht die Erstellung eines mehrere Schritte erfordernden adaptiven Formulars mithilfe eines Assistenten-Layouts. In diesem Layout können Sie für jeden Schritt einen Terminierungsausdruck festlegen, der vor dem Übergang zum nächsten Schritt überprüft wird.
* Registrierungsvorlage mit Registerkarten: Ermöglicht die Erstellung eines aus mehreren Registerkarten bestehenden adaptiven Formulars mithilfe eines Layouts, in dem sich links Registerkarten befinden, über die die Register in beliebiger Reihenfolge aufgerufen werden können.
* Erweiterte Registrierungsvorlage: Ermöglicht die Erstellung eines Formulars mit mehreren Registerkarten und Assistenten. Es wird ein Layout verwendet, bei dem sich die Registerkarten links befinden. Dabei können die Registerkarten in beliebiger Reihenfolge aufgerufen werden. Es werden Adobe Document Cloud eSign-Dienste zum Signieren und zur Prüfung verwendet.
* Leere Vorlage: Ermöglicht die Erstellung eines Formulars ohne Kopf- und Fußzeile sowie ohne Anfangsinhalt. Sie können Komponenten wie Textfelder, Schaltflächen und Bilder hinzufügen. Mit der leeren Vorlage können Sie ein Formular erstellen, das Sie [in AEM Site-Seiten einbetten](/help/forms/using/embed-adaptive-form-aem-sites.md) können.

Außerdem ist für diese Vorlagen die Eigenschaft `sling:resourceType` auf die entsprechende Seitenkomponente gesetzt. Die Seitenkomponente rendert die CQ-Seite mit dem Container des adaptiven Formulars, der seinerseits das adaptive Formular rendert.

Die folgende Tabelle zeigt die Zuordnung zwischen Vorlagen und Seitenkomponenten:

<table>
 <tbody>
  <tr>
   <td><p><strong>Vorlage</strong></p> </td>
   <td><p><strong>Seitenkomponente </strong></p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/af/templates/surveyTemplate</p> </td>
   <td><p>/libs/fd/af/components/page/survey</p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/af/templates/simpleEnrollmentTemplate</p> </td>
   <td><p>/libs/fd/af/components/page/base</p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/af/templates/tabbedEnrollmentTemplate</p> </td>
   <td><p>/libs/fd/af/components/page/tabbedenrollment</p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/afaddon/templates/advancedEnrollmentTemplate</p> </td>
   <td><p>/libs/fd/afaddon/components/page/advancedenrollment</p> </td>
  </tr>
 </tbody>
</table>

## Erstellen einer adaptiven Formularvorlage mithilfe des Vorlageneditors {#creating-an-adaptive-form-template-using-template-editor}

Sie können die Struktur und den anfänglichen Inhalt eines adaptiven Formulars unter Verwendung des Vorlagen-Editors angeben. Beispiel: Sie möchten, dass alle Formularautorinnen und Formularautoren in einem Registrierungsformular Textfelder, Navigationsschaltflächen und eine Schaltfläche zum Senden verwenden. Sie können eine Vorlage erstellen, die Autorinnen und Autoren verwenden können, damit ihr Formular konsistent mit anderen Registrierungsformularen ist. Mit dem AEM-Vorlageneditor haben Sie folgende Möglichkeiten:

* Kopf- und Fußzeilenkomponenten eines Formulars in der Strukturebene hinzufügen.
* Den anfänglichen Inhalt für das Formular angeben.
* Legen Sie ein Design fest.
* Geben Sie Aktionen wie Senden, Zurücksetzen und Navigation fest.

Weitere Informationen finden Sie unter [Vorlagen-Editor](../../forms/using/template-editor.md).

## Erstellen einer adaptiven Formularvorlage aus CRXDE {#creating-an-adaptive-form-template-from-crxde}

Anstatt die verfügbaren Vorlagen zu verwenden, können Sie auch eine Vorlage erstellen und diese für die Erstellung adaptiver Formulare verwenden. Benutzerdefinierte Vorlagen basieren auf verschiedenen Seitenkomponenten, die Container für adaptive Formulare und Seitenelemente wie Kopf- und Fußzeilen referenzieren.

Diese Komponenten können Sie aus der Basisseitenkomponente Ihrer Website erstellen. Alternativ können Sie auch die Seitenkomponente des adaptiven Formulars erweitern, das in den mitgelieferten Vorlagen verwendet wird.

Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Vorlage wie die Vorlage „simpleEnrollmentTemplate“ zu erstellen.

1. Navigieren Sie auf Ihrer Authoring-Instanz zu CRXDE Lite.

1. Erstellen Sie im Verzeichnis „/apps“ die Ordnerstruktur für Ihre Anwendung. Lautet der Anwendungsname beispielsweise „mycompany“, so erstellen Sie einen Ordner mit diesem Namen. In der Regel enthält das Anwendungsverzeichnis die Ordner „components“, „configuration“, „templates“, „src“ und „installation“. Für dieses Beispiel reicht es aus, wenn Sie die Ordner „components“, „configuration“ und „templates“ erstellen.

1. Navigieren Sie zum Ordner „/libs/fd/af/templates“.
1. Kopieren Sie den Knoten `simpleEnrollmentTemplate`.
1. Navigieren Sie zum Ordner „/apps/mycompany/templates“. Klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Einfügen]**.
1. Benennen Sie bei Bedarf den kopierten Vorlagenknoten um. Nennen Sie ihn zum Beispiel „enrollment-template“. 

1. Navigieren Sie zu „/apps/mycompany/templates/enrollment-template“.

1. Ändern Sie die Eigenschaften `jcr:title` und `jcr:description` für den Knoten `jcr:content`, um die Vorlage von der kopierten Vorlage zu unterscheiden.

1. Der Knoten `jcr:content` der geänderten Vorlage enthält die Komponenten `guideContainer` und `guideformtitle`. Der Container `guideContainer` enthält das adaptive Formular. Die Komponente `guideformtitle` zeigt den Anwendungsnamen, die Beschreibung und ähnliche Details an.

   Statt der Komponente `guideformtitle` können Sie eine benutzerdefinierte Komponente oder die Komponente `parsys` einfügen. Entfernen Sie zum Beispiel `guideformtitle` und fügen Sie eine benutzerdefinierte Komponente oder den Komponentenknoten `parsys` hinzu. Vergewissern Sie sich, dass die Eigenschaft `sling:resourceType` der Komponente auf die Komponente verweist und das Gleiche auch in der Datei `component.jsp` der Seite definiert ist.

1. Navigieren Sie zu „/apps/mycompany/templates/enrollment-template/jcr:content“. 

1. Öffnen Sie die Registerkarte **[!UICONTROL Eigenschaften]** und setzen Sie die Eigenschaft `cq:designPath` auf „/etc/designs/mycompany“. 

1. Erstellen Sie nun für den Typ `cq:Page` den Knoten „/etc/designs/mycompany“. 

## Erstellen einer adaptiven Formularseitenkomponente {#create-an-adaptive-form-page-component}

Die benutzerdefinierte Vorlage hat den gleichen Stil wie die Standardvorlage, da die Vorlage auf die Seitenkomponente „/libs/fd/af/components/page/base“ verweist. Der Komponentenverweis befindet sich in der Eigenschaft `sling:resourceType` unter dem Knoten „/apps/mycompany/templates/enrollment-template/jcr:content“. Da es sich bei der Basis um eine Kernproduktkomponente handelt, sollten Sie diese Komponente nicht ändern.

1. Navigieren Sie zum Knoten /apps/mycompany/templates/enrollment-template/jcr:content und setzen Sie die Eigenschaft `sling:resourceType` auf „/apps/mycompany/components/page/enrollmentpage“.
1. Kopieren Sie den Knoten „/libs/fd/af/components/page/base“ in den Ordner „/apps/mycompany/components/page“. 

1. Benennen Sie die kopierte Komponente in `enrollmentpage` um.

1. **(Nur bei bereits vorhandener Inhaltsseite)** Führen Sie die folgenden Schritte (a-d) aus, wenn die Komponente `contentpage` bereits für Ihre Website vorhanden ist. Wenn die Komponente `contentpage` noch nicht für Ihre Website vorhanden ist, können Sie die Eigenschaft `resourceSuperType` so einstellen, dass sie auf die vorkonfigurierte Basisseite verweist.

   1. Setzen Sie die Eigenschaft `sling:resourceSuperType` für den Knoten `enrollmentpage` auf „mycompany/components/page/contentpage“. Die Komponente `contentpage` ist die Basisseitenkomponente Ihrer Site. Sie kann durch andere Seitenkomponenten erweitert werden. Entfernen Sie Skriptdateien unter `enrollmentpage`, außer `head.jsp`, `content.jsp` und `library.jsp`. Die Komponente `sling:resourceSuperType`, in diesem Fall `contentpage`, enthält alle diese Skripte. Kopf- und Fußzeile sowie Navigationsleiste werden aus der Komponente `contentpage` übernommen.

   1. Öffnen Sie die Datei `head.jsp`.

      Die JSP-Datei enthält die Zeile `<cq.include script="library.jsp"/>`.

      Die Datei `library.jsp` enthält die Client-Bibliothek `guide.theme.simpleEnrollment`, die wiederum den Stil für das adaptive Formular enthält.

      Die Seitenkomponente `enrollmentpage` enthält eine exklusive `head.jsp`-Datei, durch die die `head.jsp`-Datei der Komponente `contentpage` überschrieben wird.

   1. Binden Sie alle Skripte in der Datei `head.jsp` für die Komponente `contentpage` in die Datei `head.jsp` für die Komponente `enrollmentpage` ein.
   1. Dem Skript `content.jsp` können Sie weiteren Seiteninhalt oder Verweise auf andere Komponenten hinzufügen, die beim Rendern einer Seite wiedergegeben werden. Beispiel: Wenn Sie die benutzerdefinierte Komponente `applicationformheader` hinzufügen, fügen Sie der Komponente den folgenden Verweis in der JSP-Datei hinzu:

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      Die benutzerdefinierte Komponente müssen Sie ebenso einfügen, wenn Sie der Vorlagenknotenstruktur eine `parsys`-Komponente hinzufügen.

## Erstellen einer Client-Bibliothek für adaptive Formulare {#creating-an-adaptive-form-client-library}

Die `head.jsp`-Datei der Komponente `enrollmentpage` der neuen Vorlage enthält eine Client-Bibliothek namens `guide.theme.simpleEnrollment`. Die Standardvorlage verwendet ebenfalls diese Client-Bibliothek. Ändern Sie den Stil in der neuen Vorlage mit einer der folgenden Methoden:

* Definieren Sie ein benutzerdefiniertes Design, durch das Sie das Standarddesign`guide.theme.simpleEnrollment` ersetzen. 
* Definieren Sie unter „/etc/designs/mycompany“ eine neue Client-Bibliothek. Schließen Sie die Client-Bibliothek nach dem Eintrag des Standard-Designs in der JSP-Seite ein. Binden Sie alle überschriebenen Stile und zusätzlichen JavaScript-Dateien in dieser Client-Bibliothek ein.

>[!NOTE]
>
>Mit Design wird eine Client-Bibliothek bezeichnet, die in einer zum Rendern eines adaptiven Formulars verwendeten Seitenkomponente enthalten ist. Die Client-Bibliothek wirkt sich in erster Linie auf das Erscheinungsbild des adaptiven Formulars aus.
