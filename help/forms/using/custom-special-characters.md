---
title: Benutzerdefinierte Sonderzeichen in Correspondence Management
description: Erfahren Sie, wie Sie benutzerdefinierte Sonderzeichen in Correspondence Management hinzufügen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: 3e978c3e-12f2-4dc6-801d-8ab4c5df6700
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 40%

---

# Benutzerdefinierte Sonderzeichen in Correspondence Management{#custom-special-characters-in-correspondence-management}

## Übersicht {#overview}

Correspondence Management bietet standardmäßig Unterstützung für 210 Sonderzeichen, die Sie problemlos in Briefe einfügen können.

Sie können beispielsweise die folgenden Sonderzeichen einfügen:

* Währungssymbole wie €,￥ und £
* Mathematische Symbole wie ∑, √, ∂ und ^
* Interpunktionssymbole wie „ und “

Sie können Sonderzeichen in Briefe einfügen:

* Im [Texteditor](/help/forms/using/document-fragments.md#createtext)
* In einem [editierbaren Inline-Modul in einer Korrespondenz](../../forms/using/create-correspondence.md#managecontent)

![specialcharactersinlinemodul](assets/specialcharactersinlinemodule.png)

Der Administrator kann Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen. Dieser Artikel enthält Anweisungen dazu, wie Sie Unterstützung für zusätzliche benutzerdefinierte Sonderzeichen hinzufügen können.

## Unterstützung für benutzerdefinierte Sonderzeichen in Correspondence Management hinzufügen oder ändern {#creatingfolderstructure}

Führen Sie die folgenden Schritte aus, um Unterstützung für benutzerdefinierte Sonderzeichen hinzuzufügen:

1. Wechseln Sie zu `https://'[server]:[port]'/[ContextPath]/crx/de` und melden Sie sich als Administrator an.
1. Erstellen Sie im Ordner &quot;apps&quot;einen Ordner mit dem Namen **[!UICONTROL Sonderzeichen]** mit einem ähnlichen Pfad/einer ähnlichen Struktur zum Ordner &quot;Sonderzeichen&quot;(im Ordner textEditorConfig unter libs):

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **specialcharacters** unter dem folgenden Pfad und wählen Sie **Überlagerungsknoten**:

      `/libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen**: Kontrollkästchen aktiviert

      >[!NOTE]
      >
      >Ändern Sie nicht die Verzweigung /libs . Alle Änderungen, die Sie vornehmen, können verloren gehen, da sich diese Verzweigung ändern kann, wenn Sie:
      >
      >
      >
      >    * Aktualisierung Ihrer Instanz
      >    * Hotfix anwenden
      >    * Feature Pack installieren
      >
      >

   1. Klicken Sie auf **OK** und dann auf **Alle speichern**. Der Ordner „specialcharacters“ wird in dem angegebenen Pfad erstellt.

      Überprüfen Sie nach dem Erstellen der Überlagerung die Knotenstruktur-Tags. Jeder Knoten, der mit der Überlagerung in /apps erstellt wurde, sollte dieselbe Klasse und dieselben Eigenschaften wie in /libs für diesen Knoten haben. Wenn eine Eigenschaft oder ein Tag in der Knotenstruktur unter /apps fehlt, synchronisieren Sie die Tags mit dem entsprechenden Knoten in /libs.

1. Stellen Sie sicher, dass **[!UICONTROL textEditorConfig]** -Knoten weist die folgenden Eigenschaften und Werte auf:

   | Name | Typ | Wert |
   |---|---|---|
   | cmConfigurationType | Zeichenfolge | cmTextEditorConfiguration |
   | cssPath | Zeichenfolge | /libs/fd/cm/ma/gui/components/admin/createasset/textcontrol/clientlibs/textcontrol |

1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL specialcharacters]** unter dem folgenden Pfad und wählen Sie **Erstellen > Untergeordneter Knoten** und klicken Sie dann auf **Alle speichern**:

   /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters/&lt;yourchildnode>

1. Aktualisieren Sie die Seite Texteditor/Benutzeroberfläche &quot;Korrespondenz erstellen&quot;. Der Knoten, den Sie hinzugefügt haben, ist der letzte in der Liste der Sonderzeichen in der Benutzeroberfläche.
1. Klicken Sie auf **Alle speichern**.
1. Änderungen an den Sonderzeichen nach Bedarf:

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
     <li>Fügen Sie einen untergeordneten Knoten unter „/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters“ mit obligatorischen Eigenschaften hinzu.</li>
     <li>Klicken Sie auf Alle speichern</li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche "Korrespondenz erstellen", damit Sie die Änderungen sehen können.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Eigenschaften eines vorhandenen Sonderzeichens aktualisieren</td>
   <td>
    <ol>
     <li>Überlagern Sie den Knoten, der wie oben beschrieben aktualisiert werden soll, und überprüfen Sie Tags und Klassen.</li>
     <li>Ändern Sie beliebige Werte wie Beschriftung, Wert, endValue und multipleCaption. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche "Korrespondenz erstellen", damit Sie die Änderungen sehen können.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Sonderzeichen ausblenden</td>
   <td>
    <ol>
     <li>Überlagern Sie den Knoten, der unter „/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters“ ausgeblendet werden soll</li>
     <li>Fügen Sie die Eigenschaft sling:hideResource (boolesch) zum Knoten (unter Apps) hinzu, der ausgeblendet werden soll. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche "Korrespondenz erstellen", damit Sie die Änderungen sehen können.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Ausblenden mehrerer Sonderzeichen</td>
   <td>
    <ol>
     <li>Fügen Sie die Eigenschaft „sling:hideChildren (String or String[])“ zu „/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters” hinzu. </li>
     <li>Fügen Sie Knotennamen (Sonderzeichen, die ausgeblendet werden sollen) als Werte für die Eigenschaft "sling:hideChildren"hinzu. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche "Korrespondenz erstellen", damit Sie die Änderungen sehen können.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Sonderzeichen anordnen</td>
   <td>
    <ol>
     <li>Fügen Sie einen untergeordneten Knoten unter „/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters“ mit obligatorischen Eigenschaften hinzu. </li>
     <li>Fügen Sie die Eigenschaft "sling:orderBefore (String)"zum neu erstellten untergeordneten Knoten hinzu. </li>
     <li>Fügen Sie den Knotennamen als Wert hinzu, vor dem das neu hinzugefügte Sonderzeichen angezeigt werden soll. </li>
     <li>Klicken Sie auf Alle speichern. </li>
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche "Korrespondenz erstellen", damit Sie die Änderungen sehen können.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>
