---
title: Benutzerdefinierte Sonderzeichen in Correspondence Management
seo-title: Benutzerdefinierte Sonderzeichen in Correspondence Management
description: Erfahren Sie, wie Sie benutzerdefinierte Sonderzeichen in Correspondence Management hinzufügen.
seo-description: Erfahren Sie, wie Sie benutzerdefinierte Sonderzeichen in Correspondence Management hinzufügen.
uuid: a1890f6d-8e0c-471f-a9bd-861acf1f17e6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 9f26565c-a7ba-4e9e-bf77-a95eb8e351f2
docset: aem65
feature: Korrespondenzverwaltung
exl-id: 3e978c3e-12f2-4dc6-801d-8ab4c5df6700
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 69%

---

# Benutzerdefinierte Sonderzeichen in Correspondence Management{#custom-special-characters-in-correspondence-management}

## Überblick {#overview}

Correspondence Management umfasst einen integrierten Standard-Support für 210 Sonderzeichen, die Sie mühelos in Briefen einfügen können.

Sie können beispielsweise die folgenden Sonderzeichen einfügen:

* Währungssymbole wie €,¥ und £
* Mathematische Symbole wie, Ö, % und ^
* Satzzeichen als ‟ und&quot;

Sie können Sonderzeichen in Briefe einfügen:

* Im [Texteditor](/help/forms/using/document-fragments.md#createtext)
* In einem [bearbeitbaren Inline-Modul in einer Korrespondenz](../../forms/using/create-correspondence.md#managecontent)

![specialcharaktersinlinemodul](assets/specialcharactersinlinemodule.png)

Der Administrator kann Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen. In diesem Artikel finden Sie Anweisungen dazu, wie Sie Unterstützung für zusätzliche benutzerdefinierte Sonderzeichen hinzufügen können.

## Hinzufügen oder Ändern von Unterstützung für benutzerdefinierte Sonderzeichen in Correspondence Management {#creatingfolderstructure}

Führen Sie die folgenden Schritte aus, um Unterstützung für benutzerdefinierte Sonderzeichen hinzuzufügen:

1. Gehen Sie zu `https://'[server]:[port]'/[ContextPath]/crx/de` und melden Sie sich als Administrator an.
1. Erstellen Sie im Apps-Ordner einen Ordner mit dem Namen **[!UICONTROL specialcharacters]** mit einem ähnlichen Pfad/einer ähnlichen Struktur wie der Ordner für Sonderzeichen (im Ordner textEditorConfig unter libs):

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **specialcharacters** im folgenden Pfad und wählen Sie **Überlagerungsknoten** aus:

      `/libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:**  /libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen:** Überprüft

      >[!NOTE]
      >
      >Nehmen Sie keine Änderungen in der Verzweigung /libs vor. Alle Änderungen, die Sie vornehmen, gehen möglicherweise verloren, da diese Verzweigung sich ändern kann, wenn Sie:
      >
      >
      >
      >    * Ihre Instanz aktualisieren
      >    * Ein Hotfix anwenden
      >    * Ein Feature Pack installieren


   1. Klicken Sie auf **OK** und dann auf **Alle speichern**. Der Ordner &quot;Sonderzeichen&quot;wird im angegebenen Pfad erstellt.

      Nach dem Erstellen des Überlagerungsknotens, überprüfen Sie die Knotenstrukturtags. Jeder Knoten, der in /Apps mit der Überlagerung erstellt wurde, sollte dieselbe Klasse und dieselben Eigenschaften haben, wie es in /libs für diesen Knoten definiert ist. Wenn eine Eigenschaft oder ein Tag in der Knotenstruktur unter /Apps fehlt, synchronisieren sie die Tags mit dem entsprechenden Knoten in /libs.



1. Stellen Sie sicher, dass der Knoten **[!UICONTROL textEditorConfig]** folgende Eigenschaften und Werte aufweist:

   | Name | Typ | Wert |
   |---|---|---|
   | cmConfigurationType | Zeichenfolge | cmTextEditorConfiguration |
   | cssPath | Zeichenfolge | /libs/fd/cm/ma/gui/components/admin/createasset/textcontrol/clientlibs/textcontrol |

1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL specialcharacters]** im folgenden Pfad und wählen Sie **Erstellen > Untergeordneter Knoten** und klicken Sie dann auf **Alle speichern**:

   /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters/&lt;YourChildNode>

1. Aktualisieren Sie den Texteditor\Benutzeroberfläche „Korrespondenz erstellen“. Der Knoten, den Sie hinzugefügt haben, ist der letzte in der Liste der Sonderzeichen in der Benutzeroberfläche.
1. Klicken Sie auf **Alle speichern**.
1. Nehmen Sie die Änderungen in den Sonderzeichen wie gewünscht vor:

<table>
 <tbody>
  <tr>
   <td><strong>To...</strong></td>
   <td><strong>Führen Sie nun die folgenden Schritte durch</strong></td>
  </tr>
  <tr>
   <td>Fügen Sie ein benutzerdefiniertes Sonderzeichen hinzu</td>
   <td>
    <ol>
     <li>Fügen Sie einen untergeordneten Knoten unter "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"mit obligatorischen Eigenschaften hinzu.</li>
     <li>Klicken Sie auf Alle speichern</li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Aktualisieren Sie die Eigenschaften der vorhandenen Sonderzeichen</td>
   <td>
    <ol>
     <li>Überlagern den Knoten, der aktualisiert werden soll, wie oben erläutert und überprüfen Sie Tags und Klassen.</li>
     <li>Ändern Sie alle Werte wie Beschriftung, Wert, endValue und multipleCaption. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Ausblenden von Sonderzeichen</td>
   <td>
    <ol>
     <li>Überlagern Sie den Knoten, der unter "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"ausgeblendet werden soll.</li>
     <li>Fügen Sie die Eigenschaft sling:hideResource (Boolesch) zum Knoten (unter Apps) hinzu, der ausgeblendet werden soll. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Ausblenden mehrerer Sonderzeichen</td>
   <td>
    <ol>
     <li>Fügen Sie die Eigenschaft "sling:hideChildren (String oder String[])"zu "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"hinzu. </li>
     <li>Fügen Sie Knotennamen (Sonderzeichen, die ausgeblendet werden sollen) als Werte für die Eigenschaft „sling:hideChildren“ hinzu. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.<br />  </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Sonderzeichen anordnen</td>
   <td>
    <ol>
     <li>Fügen Sie einen untergeordneten Knoten unter "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"mit obligatorischen Eigenschaften hinzu. </li>
     <li>Fügen Sie die Eigenschaft „sling:orderBefore (String)“ zum neu erstellten untergeordneten Knoten hinzu. </li>
     <li>Fügen Sie den Knotennamen als Wert vor dem neu hinzugefügten Sonderzeichen hinzu, das angezeigt werden soll. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>
