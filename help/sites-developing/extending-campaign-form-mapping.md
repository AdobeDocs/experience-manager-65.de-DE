---
title: Erstellen benutzerdefinierter Formularzuordnungen
seo-title: Creating Custom Form Mappings
description: Wenn Sie eine benutzerdefinierte Tabelle in Adobe Campaign erstellen, möchten Sie möglicherweise ein Formular in erstellen, das AEM dieser benutzerdefinierten Tabelle zugeordnet ist
seo-description: When you create a custom table in Adobe Campaign, you may want to build a form in AEM that maps to that custom table
uuid: f3bde513-6edb-4eb6-9048-40045ee08c4a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d5dac1db-2dde-4b75-a31b-e057b447f6e2
exl-id: bce6c586-9962-4217-82cb-c837e479abc0
source-git-commit: 1807919078996b1cf1cbd1f2d90c3b14cb660e2c
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 15%

---

# Erstellen benutzerdefinierter Formularzuordnungen{#creating-custom-form-mappings}

Wenn Sie eine benutzerdefinierte Tabelle in Adobe Campaign erstellen, möchten Sie möglicherweise ein Formular in erstellen, das AEM dieser benutzerdefinierten Tabelle zugeordnet ist.

In diesem Dokument wird beschrieben, wie Sie benutzerdefinierte Formularzuordnungen erstellen. Wenn Sie die Schritte in diesem Dokument ausführen, stellen Sie Ihren Benutzern eine Ereignisseite zur Verfügung, auf der sie sich für ein bevorstehendes Ereignis registrieren können. Anschließend können Sie diese Benutzer über Adobe Campaign nachverfolgen.

## Voraussetzungen {#prerequisites}

Sie müssen Folgendes installiert haben:

* Adobe Experience Manager
* Adobe Campaign Classic

Weitere Informationen finden Sie unter [Integrieren von AEM mit Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md).

## Erstellen benutzerdefinierter Formularzuordnungen {#creating-custom-form-mappings-2}

Um benutzerdefinierte Formularzuordnungen zu erstellen, müssen Sie die folgenden allgemeinen Schritte ausführen, die in den folgenden Abschnitten ausführlich beschrieben werden:

1. Erstellen Sie eine benutzerdefinierte Tabelle.
1. Erweitern Sie die **Saatgut** Tabelle.
1. Erstellen Sie eine benutzerdefinierte Zuordnung.
1. Erstellen Sie einen Versand basierend auf dem benutzerdefinierten Mapping.
1. Erstellen Sie das Formular in AEM, das den erstellten Versand verwendet.
1. Senden Sie das Formular, um es zu testen.

### Erstellen einer benutzerdefinierten Tabelle in Adobe Campaign {#creating-the-custom-table-in-adobe-campaign}

Erstellen Sie zunächst eine benutzerdefinierte Tabelle in Adobe Campaign. In diesem Beispiel verwenden wir die folgende Definition zur Erstellung einer Ereignistabelle:

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

Nachdem Sie die Ereignistabelle erstellt haben, führen Sie die **Assistent zur Aktualisierung der Datenbankstruktur** , um die Tabelle zu erstellen.

### Erweitern der Testtabelle {#extending-the-seed-table}

Tippen/klicken Sie in Adobe Campaign auf **Hinzufügen** , um eine neue Erweiterung der **Testadressen (nms)** Tabelle.

![chlimage_1-194](assets/chlimage_1-194.png)

Verwenden Sie nun die Felder der **Ereignistabelle** zur Erweiterung der **Seed**-Tabelle:

```xml
<element label="Event" name="custom_cus_event">
 <attribute name="eventname" template="cus:event:event/@eventname"/>
 <attribute name="eventdate" template="cus:event:event/@eventdate"/>
 <attribute name="email" template="cus:event:event/@email"/>
 <attribute name="seats" template="cus:event:event/@seats"/>
 </element>
```

Führen Sie danach **Datenbankassistent aktualisieren** , um die Änderungen anzuwenden.

### Erstellen einer benutzerdefinierten Zielzuordnung {#creating-custom-target-mapping}

In **Administration/Kampagnenverwaltung** t, gehen Sie zu **Zielzuordnungen** und fügen Sie einen neuen T hinzu **Zielzuordnung.**

>[!NOTE]
>
>Stellen Sie sicher, dass Sie einen aussagekräftigen Namen für **Interner Name**.

![chlimage_1-195](assets/chlimage_1-195.png)

### Erstellen einer benutzerdefinierten Versandvorlage {#creating-a-custom-delivery-template}

In diesem Schritt fügen Sie eine Versandvorlage hinzu, die die **Zielgruppen-Mapping**.

In **Ressourcen/Vorlagen**, navigieren Sie zur Versandvorlage und duplizieren Sie den bestehenden AEM. Wenn Sie auf **nach**, wählen Sie das Erstellungsereignis aus **Zielgruppen-Mapping**.

![chlimage_1-196](assets/chlimage_1-196.png)

### Erstellen des Formulars in AEM {#building-the-form-in-aem}

Stellen Sie AEM sicher, dass Sie einen Cloud Service in **Seiteneigenschaften**.

Dann in der **Adobe Campaign** Wählen Sie im Tab den in erstellten Versand aus. [Erstellen einer benutzerdefinierten Versandvorlage](#creating-a-custom-delivery-template).

![chlimage_1-197](assets/chlimage_1-197.png)

Stellen Sie beim Konfigurieren der Felder sicher, dass Sie eindeutige Elementnamen für die Formularfelder angeben.

Nachdem die Felder konfiguriert wurden, müssen Sie die Zuordnung manuell ändern.

Wechseln Sie in CRXDE-lite zum **jcr:content** (der Seite) und ändern Sie die **acMapping** zum internen Namen der **Zielgruppen-Mapping**.

![chlimage_1-198](assets/chlimage_1-198.png)

Aktivieren Sie bei der Konfiguration des Formulars das Kontrollkästchen „Erstellen, wenn nicht vorhanden“.

![chlimage_1-199](assets/chlimage_1-199.png)

### Formular übermitteln {#submitting-the-form}

Jetzt können Sie das Formular senden und auf der Adobe Campaign-Seite überprüfen, ob die Werte gespeichert werden.

![chlimage_1-200](assets/chlimage_1-200.png)

## Fehlerbehebung {#troubleshooting}

**&quot;Ungültiger Typ für den Wert &#39;02/02/2015&#39; aus Element &#39;@eventdate&#39; (Dokument des Typs &#39;Ereignis ([adb:event])&#39;)&quot;**

Beim Senden des Formulars wird dieser Fehler im **error.log** in AEM.

Dies liegt an einem ungültigen Format für das Datumsfeld. Die Lösung besteht darin, **yyyy-mm-dd** als Wert.
