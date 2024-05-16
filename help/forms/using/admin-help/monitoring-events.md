---
title: Überwachen von Ereignissen
description: Wenn die Auditing-Funktion aktiviert ist, können Sie mithilfe von Document Security bestimmte Ereignistypen überwachen. Mithilfe von Document Security können Sie die Ereignisliste einfach durchsuchen und sortieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 078b9ad1-16e2-40f4-92dc-e4093c0bb6ac
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '958'
ht-degree: 100%

---

# Überwachen von Ereignissen {#monitoring-events}

Wenn die Auditing-Funktion aktiviert ist, können Sie mithilfe von Document Security bestimmte Ereignistypen überwachen. Die Ereignisse, die Sie sehen können, hängen von Ihrer Rolle ab:

**Benutzer:** Sind in der Lage, geprüfte Ereignisse für ihre richtliniengeschützten Dokumente sowie andere geschützte Dokumente, die sie erhalten und verwenden, anzuzeigen.

**Richtliniensatzkoordinatoren:** Sind in der Lage, geprüfte Ereignisse, einschließlich Dokument- und Richtlinienereignissen, für Dokumente anzuzeigen, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

**Administratoren:** Sind in der Lage, geprüfte Ereignisse im Zusammenhang mit allen richtliniengeschützten Dokumenten und Benutzern anzuzeigen. Admins können auch andere Arten von Ereignissen verfolgen, darunter Benutzer-, Dokument-, Richtlinien- und System-Ereignisse.

>[!NOTE]
>
>Ereignisse, die an einer Kopie eines richtliniengeschützten Dokuments ausgeführt werden, werden auch als Ereignisse am ursprünglichen geschützten Dokument verfolgt.

(Siehe [Ereignis-Auditing-Optionen](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).)

Ein fehlgeschlagenes Ereignis wird aufgezeichnet, wenn nicht autorisierte Benutzende versuchen, ein Dokument anzuzeigen oder sich mit einem falschen Benutzernamen oder Kennwort anzumelden.

>[!NOTE]
>
>Fehlgeschlagene anonyme Zugriffsereignisse für Dokumente können protokolliert werden, wenn eine Richtlinie bearbeitet wird, um den anonymen Zugriff zu entfernen. Wenn autorisierte Empfängerinnen oder Empfänger versuchen, auf ein Dokument zuzugreifen, das durch die bearbeitete Richtlinie geschützt ist, wird zwar weiterhin ein anonymer Zugriff versucht, der Versuch schlägt jedoch fehl.

Wenn eine Richtlinie den anonymen Benutzerzugriff zulässt, die Admins den anonymen Zugriff jedoch später aus Gründen der Dokumentensicherheit deaktivieren, schlägt der anonyme Zugriff für mit der Richtlinie geschützte Dokumente fehl und das Ereignis wird nicht protokolliert.

## Aktivieren des Ereignis-Auditings {#enable-event-auditing}

Damit ein Ereignis-Auditing stattfinden kann, müssen die folgenden Einrichtungsanforderungen erfüllt sein:

* Die Auditing-Funktion für den Server muss vom System oder durch Admins aktiviert werden.

  (Siehe [Konfigurieren von Ereignis-Auditing- und Datenschutzeinstellungen](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).)

* Für die Richtlinie, die Sie zum Schutz des Dokuments verwenden, muss das Auditing aktiviert sein. (Siehe [Erstellen und Bearbeiten von Richtlinien](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Suchen nach einem Ereignis {#search-for-an-event}

Sie können die Ereignisliste durchsuchen und ausführlichere Beschreibungen zu Ereignissen anzeigen. Die ausführlichen Beschreibungen enthalten Informationen wie die Ereignis-ID, Beschreibung, IP-Adresse, Organisation, betroffene Benutzende, Datum und Uhrzeit des Ereignisses, abgelehnte Aktivitäten und Offline-Ereignisse (wenn Benutzende versuchen, ein Dokument zu verwenden, ohne mit der Dokumentensicherheit verbunden zu sein).

Sie können auf der Seite „Ereignisse“ nach Ereignissen suchen, indem Sie eine Kombination aus Ereignissuchkriterien und den Daten verwenden, an denen die Ereignisse auftraten. Die Ereignisse, nach denen Sie suchen können, hängen von Ihrer Rolle ab:

**Benutzer:** Sind in der Lage, geprüfte Ereignisse für ihre richtliniengeschützten Dokumente sowie andere geschützte Dokumente, die sie erhalten und verwenden, anzuzeigen. Die folgenden Suchoptionen sind verfügbar:

**Ereignisse, die mich 
betreffen:** Benutzer können nach Ereignissen für die richtliniengeschützten Dokumente suchen, die sie erstellt oder empfangen haben. Wenn ein Benutzer beispielsweise ein Dokument öffnet, anzeigt oder druckt, das von einer anderen Person geschützt wurde, werden dem Benutzer diese Ereignisse nur für dieses Dokument angezeigt.

**Ereignisse, die meine Dokumente betreffen:** Benutzer können alle Ereignisse finden, die im Zusammenhang mit ihren eigenen richtliniengeschützten Dokumenten stehen. Der Benutzer sieht die Ereignisse, die von allen Personen generiert wurden, die Umgang mit seinen Dokumenten hatten.

**Richtliniensatzkoordinatoren:** Sind in der Lage, geprüfte Ereignisse, einschließlich Dokument- und Richtlinienereignissen, für Dokumente anzuzeigen, die von Richtlinien in ihren Richtliniensätzen geschützt werden. Die folgenden Optionen stehen zur Auswahl:  

**Dokumentereignisse,
wenn ich Richtliniensatzkoordinator bin:** Richtliniensatzkoordinatoren mit der Berechtigung zum Anzeigen von Ereignissen können Ereignisse finden, die Dokumente betreffen, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

**Richtlinienereignisse, wenn ich Richtliniensatzkoordinator bin:** Richtliniensatzkoordinatoren mit der Berechtigung zum Anzeigen von Ereignissen können Ereignisse finden, die mit Richtlinien in ihren Richtliniensätzen in Zusammenhang stehen.

**Administratoren:** Sind in der Lage, geprüfte Ereignisse im Zusammenhang mit allen richtliniengeschützten Dokumenten und Benutzern anzuzeigen. Admins können darüber hinaus andere Typen nachverfolgen.  Außerdem können Admins die Ereignissuche je nach Benutzertyp weiter unterteilen:

**Bekannte Benutzer:** Benutzer, die in den Quellordnern gefunden werden können oder als externe Benutzer registriert sind.

**Anonyme Benutzer:** Benutzer, die auf ein Dokument zugreifen, das durch eine Richtlinie geschützt ist, die den anonymen Zugriff erlaubt.

**Systembenutzer:** Vom Server ausgelöste Ereignisse, z. B. eine Ordnersynchronisierung.

1. Klicken Sie auf der Document Security-Seite auf „Ereignisse“.
1. Wählen Sie in der Liste „Suchen“ die gewünschten Suchkriterien aus.  Abhängig von der Auswahl in der Liste „Suchen“ wird eine zweite Liste mit weiteren Suchkriterien angezeigt.  Geben Sie, falls möglich, in das Textfeld die Suchkriterien ein.

   Weitere Einzelheiten zu bestimmten Ereignistypen finden Sie unter [Ereignis-Auditing-Optionen](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

1. Wählen Sie in der Liste „Benutzer“ den Benutzertyp aus, der das Ereignis verursacht hat.

   * Wenn Sie „Bekannter Benutzer“ auswählen, wird ein zweites Suchfeld angezeigt, in das Sie den Benutzernamen und die E-Mail-Adresse der Person eingeben müssen.
   * Wenn Sie diese Angaben nicht kennen, klicken Sie auf das Adressbuchsymbol, um den Benutzer anhand des Benutzernamens oder der E-Mail-Adresse zu suchen.

1. Wählen Sie in der Liste „Datum“ eine Datumsbereichsoption aus. Wenn Sie „Eigene Daten“ auswählen, werden Felder eingeblendet, in die Sie das Datum im Format TT.MM.JJJJ eingeben, oder Sie können über die Datumsauswahl den Datumsbereich angeben:

   * Klicken Sie auf den Kalender, um die Datumsauswahl zu öffnen.
   * Bestimmen Sie mithilfe der Pfeilschaltflächen ein Jahr und einen Monat.
   * Klicken Sie auf dem Kalender auf einen Monatstag.
   * Klicken Sie auf „OK“, um die Datumsauswahl zu schließen.

1. Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus.
1. Klicken Sie auf „Suchen“.

   Fehlgeschlagene Ereignisse werden in der Liste mit dem Symbol „Verweigert“ gekennzeichnet.

1. Um Details zu einem Ereignis anzuzeigen, klicken Sie auf die Beschreibung des Ereignisses in der Liste.

## Sortieren der Ereignisliste {#sort-the-event-list}

Sie können die Ereignisliste nach Spaltenüberschrift sortieren, um Ereignisse leichter zu finden. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an, ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

1. Klicken Sie auf die gewünschte Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie nochmals auf die Spaltenüberschrift.
