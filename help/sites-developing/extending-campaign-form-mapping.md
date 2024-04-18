---
title: Erstellen benutzerdefinierter Formularzuordnungen
description: Bei der Erstellung einer benutzerdefinierten Tabelle in Adobe Campaign ist es u. U. ratsam, in AEM ein Formular zu erstellen, das dieser benutzerdefinierten Tabelle zugeordnet wird.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: bce6c586-9962-4217-82cb-c837e479abc0
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 100%

---

# Erstellen benutzerdefinierter Formularzuordnungen{#creating-custom-form-mappings}

Bei der Erstellung einer benutzerdefinierten Tabelle in Adobe Campaign ist es u. U. ratsam, in AEM ein Formular zu erstellen, das dieser benutzerdefinierten Tabelle zugeordnet wird.

In diesem Dokument wird beschrieben, wie Sie benutzerdefinierte Formularzuordnungen erstellen. Indem Sie die Schritte in diesem Dokument abschließen, stellen Sie Ihren Benutzenden eine Ereignisseite zur Verfügung, auf der sie sich selbst für anstehende Ereignisse registrieren können. Diese Benutzenden kontaktieren Sie dann nachfolgend via Adobe Campaign.

## Voraussetzungen {#prerequisites}

Sie müssen Folgendes installiert haben:

* Adobe Experience Manager
* Adobe Campaign Classic

Weitere Informationen finden Sie unter [Integrieren von AEM mit Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md).

## Erstellen benutzerdefinierter Formularzuordnungen {#creating-custom-form-mappings-2}

Zur Erstellung benutzerdefinierter Formularzuordnungen führen Sie die folgenden Schritte aus, die in den nachstehenden Abschnitten genauer beschrieben werden:

1. Erstellen Sie eine benutzerdefinierte Tabelle.
1. Erweitern Sie die **Seed**-Tabelle.
1. Erstellen Sie eine benutzerdefinierte Zuordnung.
1. Erstellen Sie eine auf der benutzerdefinierten Zuordnung basierende Bereitstellung.
1. Erstellen Sie das Formular in AEM, das die erstellte Bereitstellung verwendet.
1. Übermitteln Sie das Formular, um es zu testen.

### Erstellen der benutzerdefinierten Tabelle in Adobe Campaign {#creating-the-custom-table-in-adobe-campaign}

Erstellen Sie zunächst eine benutzerdefinierte Tabelle in Adobe Campaign. In diesem Beispiel verwenden wir die folgende Definition zur Erstellung einer Ereignistabelle:

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

Führen Sie nach der Erstellung der Ereignistabelle den **Assistenten zur Aktualisierung der Datenbankstruktur** aus, um die Tabelle zu erstellen.

### Erweitern der Seed-Tabelle {#extending-the-seed-table}

Wählen Sie in Adobe Campaign die Option **Hinzufügen** aus, um eine Erweiterung für die Tabelle der **Seed-Adressen (nms)** hinzuzufügen.

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

Führen Sie danach den **Assistenten zur Aktualisierung der Datenbank** aus, um die Änderungen zu übernehmen.

### Erstellen eines benutzerdefinierten Zielgruppen-Mappings {#creating-custom-target-mapping}

Gehen Sie unter **Administration/Kampagnenverwaltung** zu **Zielgruppen-Mappings** und fügen Sie ein neues **Zielgruppen-Mapping** hinzu.

>[!NOTE]
>
>Verwenden Sie einen aussagekräftigen **internen Namen**.

![chlimage_1-195](assets/chlimage_1-195.png)

### Erstellen einer benutzerdefinierten Versandvorlage {#creating-a-custom-delivery-template}

In diesem Schritt fügen Sie eine Versandvorlage hinzu, die das erstellte **Zielgruppen-Mapping** verwendet.

Navigieren Sie unter **Ressourcen/Vorlagen** zur Versandvorlage und duplizieren Sie den bestehenden AEM-Versand. Wenn Sie auf **An** klicken, wählen Sie das **Zielgruppen-Mapping** für „Ereignis erstellen“ aus.

![chlimage_1-196](assets/chlimage_1-196.png)

### Erstellen des Formulars in AEM {#building-the-form-in-aem}

Vergewissern Sie sich, dass Sie in AEM unter **Seiteneigenschaften** einen Cloud-Service konfiguriert haben.

Wählen Sie dann auf der Registerkarte **Adobe Campaign** den Versand aus, der im Schritt [Erstellen einer benutzerdefinierten Versandvorlage](#creating-a-custom-delivery-template) erstellt wurde.

![chlimage_1-197](assets/chlimage_1-197.png)

Geben Sie bei der Konfiguration der Felder eindeutige Elementnamen für die Formularfelder an.

Nach der Konfiguration der Felder müssen Sie die Zuordnung manuell ändern.

Wechseln Sie in CRXDE Lite zum Knoten **jcr:content** der Seite und legen Sie als Wert von **acMapping** den internen Namen des **Zielgruppen-Mappings** fest.

![chlimage_1-198](assets/chlimage_1-198.png)

Aktivieren Sie bei der Konfiguration des Formulars das Kontrollkästchen „Erstellen, wenn nicht vorhanden“.

![chlimage_1-199](assets/chlimage_1-199.png)

### Übermitteln des Formulars {#submitting-the-form}

Sie können das Formular nun übermitteln, um in Adobe Campaign zu überprüfen, ob die Werte gespeichert wurden.

![chlimage_1-200](assets/chlimage_1-200.png)

## Fehlerbehebung {#troubleshooting}

**&quot;Invalid type for value &#39;02/02/2015&#39; from element &#39;@eventdate&#39; (document of type &#39;Event ([adb:event])&#39;)&quot;**

Beim Übermitteln des Formulars wird dieser Fehler in der Datei **error.log** von AEM protokolliert.

Dies ist auf ein ungültiges Format für das Datumsfeld zurückzuführen. Die Lösung besteht darin, einen Wert im Format **JJJJ-MM-TT** anzugeben.
