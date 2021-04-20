---
title: Ereignisse überwachen
seo-title: Ereignisse überwachen
description: Wenn die Prüffunktion aktiviert ist, können Sie mithilfe von Document Security bestimmte Arten von Ereignissen überwachen. Sie können die Ereignisliste mithilfe der Document Security mühelos durchsuchen und sortieren.
seo-description: Wenn die Prüffunktion aktiviert ist, können Sie mithilfe von Document Security bestimmte Arten von Ereignissen überwachen. Sie können die Ereignisliste mithilfe der Document Security mühelos durchsuchen und sortieren.
uuid: 22add6ff-536d-4cb9-8eac-b72cad5c3ecf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 379957bf-0634-4182-b269-1b010da4c90f
feature: Document Security
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 74%

---


# Ereignisse überwachen {#monitoring-events}

Wenn die Prüffunktion aktiviert ist, können Sie mithilfe von Document Security bestimmte Arten von Ereignissen überwachen. Die Ereignisse, die Sie anzeigen können, hängen von Ihrer Rolle ab:

**Benutzer:** Kann Ansicht geprüfte Ereignis für ihre richtliniengeschützten Dokumente und für alle geschützten Dokumente, die sie empfangen und verwenden, prüfen.

**Richtliniensatzkoordinatoren:** Kann Ansicht geprüfte Ereignis, einschließlich Dokument- und Richtliniensatzvorgaben, für Dokumente prüfen, die durch Richtlinien aus ihren Richtliniensätzen geschützt sind.

**Administratoren:** Kann Ansicht geprüfte Ereignis prüfen, die sich auf alle richtliniengeschützten Dokumente und Benutzer beziehen. Administratoren können darüber hinaus andere Ereignistypen nachverfolgen, z. B. Benutzer-, Dokument-, Richtlinien- und Systemereignisse.

>[!NOTE]
>
>Ereignisse, die für eine Kopie eines richtliniengeschützten Dokuments erfolgen, werden ebenso nachverfolgt wie Ereignisse für das ursprünglich geschützte Dokument.

(Siehe [Ereignisprüfungsoptionen](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).)

Ein fehlgeschlagenes Ereignis wird aufgezeichnet, wenn ein nicht autorisierter Benutzer versucht, ein Dokument anzuzeigen oder sich mit einem falschen Benutzernamen und Kennwort anzumelden.

>[!NOTE]
>
>Fehlgeschlagene anonyme Zugriffsereignisse werden ggf. protokolliert, wenn eine Richtlinie so bearbeitet wird, dass der anonyme Zugriff entfernt wird. Wenn ein autorisierter Empfänger versucht, auf ein Dokument zuzugreifen, das von der bearbeiteten Richtlinie geschützt wird, wird der anonyme Zugriff zunächst weiter versucht, schlägt jedoch fehl.

Wenn eine Richtlinie den anonymen Benutzerzugriff erlaubt, doch der Administrator später den anonymen Zugriff für Document Security deaktiviert, schlägt der anonyme Zugriff auf durch mit der Richtlinie geschützte Dokumente fehl, ohne dass dieses Ereignis protokolliert wird.

## Ereignisprüfung aktivieren {#enable-event-auditing}

Es folgen die Schritte, die für die Aktivierung der Ereignisprüfung erfolgen müssen:

* Der Systemadministrator bzw. Administrator muss die Prüffunktion für den Server aktivieren.

   (Siehe [Ereignisprüfungs- und Datenschutzeinstellungen konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).)

* Für die Richtlinie, die dem Schutz des Dokuments dient, muss die Prüffunktion aktiviert sein. (Siehe [Richtlinien erstellen und bearbeiten](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Nach einem Ereignis suchen  {#search-for-an-event}

Sie können die Ereignisliste durchsuchen und detaillierte Beschreibungen von Ereignissen anzeigen. Dazu zählen Informationen wie die Ereignis-ID, Beschreibung und IP-Adresse, das Unternehmen, die betroffenen Benutzer, Datum und Uhrzeit des Ereignisses, verweigerte Aktivitäten und Offline-Ereignisse (wenn Benutzer versuchen, ein Dokument zu nutzen, ohne mit Document Security verbunden zu sein).

Auf der Seite „Ereignisse“ können Sie über eine Kombination aus Ereignissuchkriterien und Datumsangaben nach Ereignissen suchen. Die Ereignisse, nach denen Sie suchen können, hängen von Ihrer Rolle ab:

**Benutzer:** Kann Ansicht geprüfte Ereignis für ihre richtliniengeschützten Dokumente und für alle geschützten Dokumente, die sie empfangen und verwenden, prüfen. Die folgenden Suchoptionen sind verfügbar:

**Ereignis, die mit mir in Verbindung stehen:** Benutzer können Ereignis für jedes richtliniengeschützte Dokument finden, das sie erstellt oder empfangen haben. Wenn ein Benutzer beispielsweise ein Dokument öffnet, anzeigt oder druckt, das von einer anderen Person geschützt wurde, werden dem Benutzer diese Ereignisse nur für dieses Dokument angezeigt.

**Ereignisse im Zusammenhang mit meinen Dokumenten:** Benutzer können alle Ereignis finden, die mit ihren eigenen richtliniengeschützten Dokumenten in Verbindung stehen. Der Benutzer sieht die Ereignisse, die von allen Personen generiert wurden, die Umgang mit seinen Dokumenten hatten.

**Richtliniensatzkoordinatoren:** Kann Ansicht geprüfte Ereignis, einschließlich Dokument- und Richtliniensatzvorgaben, für Dokumente prüfen, die durch Richtlinien aus ihren Richtliniensätzen geschützt sind. Die folgenden Optionen stehen zur Auswahl:  

**Dokument-Ereignis, bei denen ich Richtliniensatzkoordinator bin:** Richtliniensatzkoordinatoren mit der Berechtigung zum Ereignis von Ansichten können Ereignis im Zusammenhang mit Dokumenten finden, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

**Richtliniensatzkoordinator:** Richtliniensatzkoordinatoren, die über die Berechtigung für Ansichten-Ereignisse verfügen, können aus ihren Richtliniensätzen Ereignis im Zusammenhang mit Richtlinien finden.

**Administratoren:** Kann Ansicht geprüfte Ereignis prüfen, die sich auf alle richtliniengeschützten Dokumente und Benutzer beziehen. Administratoren können darüber hinaus andere Typen nachverfolgen. Administratoren können außerdem Ereignissuchen gemäß dem Benutzertyp unterteilen:

**Bekannte Benutzer:** Benutzer befinden sich in den Quellordnern oder sind als externe Benutzer registriert.

**Anonyme Benutzer:** Unbekannte Nutzer, die auf ein Dokument zugreifen, das durch eine Richtlinie geschützt ist, die den anonymen Zugriff zulässt.

**Systembenutzer:vom** Server initiierte Ereignis, z. B. eine Ordnersynchronisierung.

1. Klicken Sie auf der Document Security-Seite auf „Ereignisse“.
1. Wählen Sie in der Liste „Suchen“ die gewünschten Suchkriterien aus. Abhängig von der Auswahl in der Liste „Suchen“ wird eine zweite Liste mit weiteren Suchkriterien angezeigt. Geben Sie, falls möglich, in das Textfeld die Suchkriterien ein.

   Weitere Einzelheiten zu bestimmten Ereignistypen finden Sie unter [Ereignisprüfungsoptionen](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

1. Wählen Sie in der Liste „Benutzer“ den Benutzertyp aus, der das Ereignis verursacht hat.

   * Wenn Sie „Bekannter Benutzer“ auswählen, wird ein zweites Suchfeld angezeigt, in das Sie den Benutzernamen und die E-Mail-Adresse des Benutzers eingeben müssen.
   * Wenn Sie diese Angaben nicht kennen, klicken Sie auf das Adressbuchsymbol , um den Benutzer anhand des Benutzernamens oder der E-Mail-Adresse zu suchen.

1. Wählen Sie in der Liste „Datum“ eine Datumsbereichsoption aus. Wenn Sie „Eigene Daten“ auswählen, werden Felder eingeblendet, in die Sie das Datum im Format TTMMJJJJ eingeben, oder Sie können über die Datumsauswahl den Datumsbereich angeben:

   * Klicken Sie auf den Kalender, um die Datumsauswahl zu öffnen.
   * Bestimmen Sie über die Pfeilschaltflächen ein Jahr und einen Monat.
   * Klicken Sie auf dem Kalender auf einen Monatstag.
   * Klicken Sie auf „OK“, um die Datumsauswahl zu schließen.

1. Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus.
1. Klicken Sie auf &quot;Suchen &quot;.

   Fehlgeschlagene Ereignisse werden in der Liste mit dem Symbol „Verweigert“ gekennzeichnet.

1. Um Details zu einem Ereignis anzuzeigen, klicken Sie auf die Beschreibung des Ereignisses in der Liste.

## Die Ereignisliste sortieren  {#sort-the-event-list}

Sie können die Ereignisliste nach Spaltenüberschrift sortieren, um Ereignisse leichter zu finden. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an. Ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

1. Klicken Sie auf die gewünschte Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie nochmals auf die Spaltenüberschrift.

