---
title: Verhindern von CSRF-Angriffen
description: Erfahren Sie, wie Sie CSRF-Angriffe (Cross-Site Request Forgery) verhindern und Benutzerdaten vor Beschädigung schützen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e17fc114-eba5-4e1b-8e70-ad6af7008018
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 16%

---

# Verhindern von CSRF-Angriffen {#preventing-csrf-attacks}

## Funktionsweise von CSRF-Angriffen {#how-csrf-attacks-work}

Cross-Site Request Forgery (CSRF) ist eine Website-Schwachstelle, bei der der Browser eines gültigen Benutzers verwendet wird, um eine böswillige Anfrage zu senden, möglicherweise über einen iFrame. Da der Browser Cookies auf Domänenbasis sendet, sind die Benutzerdaten möglicherweise beeinträchtigt, wenn der Benutzer in einer Anwendung angemeldet ist.

Angenommen, Sie sind in einem Browser bei Administration Console angemeldet. Sie erhalten eine E-Mail-Nachricht mit einem Link. Klicken Sie auf den Link, um eine neue Registerkarte in Ihrem Browser zu öffnen. Die von Ihnen geöffnete Seite enthält einen ausgeblendeten iFrame, der mithilfe des Cookies aus Ihrer authentifizierten AEM Forms-Sitzung eine böswillige Anforderung an den Forms-Server sendet. Da User Management ein gültiges Cookie erhält, wird die Anfrage übergeben.

## CSRF-bezogene Begriffe {#csrf-related-terms}

**Referer:** Die Adresse der Quellseite, von der eine Anfrage kommt. Beispielsweise enthält eine Webseite unter site1.com einen Link zu site2.com. Durch Klicken auf den Link wird eine Anfrage an site2.com gesendet. Der Referrer dieser Anfrage ist site1.com , da die Anfrage von einer Seite stammt, deren Quelle site1.com lautet.

**Auf die Zulassungsliste gesetzt URIs:** URIs identifizieren Ressourcen auf dem Forms-Server, die angefordert werden, z. B. /adminui oder /contentspace. Einige Ressourcen ermöglichen einer Anforderung möglicherweise, von einer externen Site aus auf die Anwendung zuzugreifen. Diese Ressourcen gelten als auf die Zulassungsliste gesetzte URIs. Der Forms-Server führt keine Referrer-Prüfung aus den auf die Zulassungsliste gesetzt URIs durch.

**Null-Referenz:** Wenn Sie ein neues Browser-Fenster oder eine neue Registerkarte öffnen, geben Sie eine Adresse ein und drücken Sie die Eingabetaste. Der Referrer ist null. Die Anfrage ist völlig neu und stammt nicht von einer übergeordneten Webseite. Daher gibt es keinen Referrer für die Anfrage. Der Forms-Server kann einen Nullreferrer von erhalten:

* Anforderungen an SOAP- oder REST-Endpunkte von Acrobat
* alle Desktop-Clients, die HTTP-Anforderungen an einen SOAP- oder REST-Endpunkt AEM Formulars senden
* wenn ein neues Browser-Fenster geöffnet und die URL für die Anmeldeseite AEM Forms-Webanwendung eingegeben wird

Lassen Sie einen Nullverweis für SOAP- und REST-Endpunkte zu. Lassen Sie außerdem einen Null-Referrer auf allen URI-Anmeldeseiten wie /adminui und /contentspace und den entsprechenden zugeordneten Ressourcen zu. Beispielsweise ist das zugeordnete Servlet für /contentspace /contentspace/faces/jsp/login.jsp, was eine Null-Referrer-Ausnahme sein sollte. Diese Ausnahme ist nur erforderlich, wenn Sie die Filterung von GET für Ihre Webanwendung aktivieren. Ihre Anwendungen können angeben, ob Null-Referrer zugelassen werden sollen. Siehe „Schutz vor Cross-Site Request Forgery-Angriffen“ in [Härtung und Sicherheit für AEM Forms](https://help.adobe.com/de_DE/livecycle/11.0/HardeningSecurity/index.html).

**Zulässige Referrer - Ausnahme:** &quot;Zulässige Referrer - Ausnahme&quot;ist eine Unterliste der Liste zulässiger Referrer, von der aus Anfragen blockiert werden. Zulässige Referenzauausnahmen beziehen sich insbesondere auf eine Webanwendung. Wenn es einer Untergruppe der zulässigen Referrer nicht gestattet sein sollte, eine bestimmte Webanwendung aufzurufen, können Sie die Referrer mithilfe von &quot;Zulässige Referrer - Ausnahmen&quot;in Blockierungsliste setzen. Zulässige Referrer Ausnahmen werden in der Datei web.xml für Ihre Anwendung angegeben. (Siehe den Abschnitt zum Schutz vor Cross-Site Request Forgery-Angriffen in „Härtung und Sicherheit für AEM Forms“ auf der Seite „Hilfe und Tutorials“.)

## Funktionsweise zulässiger Referrer {#how-allowed-referers-work}

AEM Forms bietet Filter für Referrer, die CSRF-Angriffe verhindern können. So funktioniert die Filterung von Referrern:

1. Der Forms-Server überprüft die für den Aufruf verwendete HTTP-Methode:

   * Wenn es sich um eine POST handelt, führt der Forms-Server die Header-Prüfung des Referrers durch.
   * Wenn es sich um GET handelt, umgeht der Forms-Server die Referrer-Prüfung, es sei denn, CSRF_CHECK_GETS ist auf &quot;true&quot;festgelegt. In diesem Fall wird der Referrer-Header überprüft. CSRF_CHECK_GETS ist in der Datei web.xml für Ihre Anwendung festgelegt. (Siehe „Schutz vor Cross-Site Request Forgery-Angriffen“ im [Handbuch für Härtung und Sicherheit](https://help.adobe.com/de_DE/livecycle/11.0/HardeningSecurity/index.html)).

1. Der Forms-Server prüft, ob der angeforderte URI auf die Zulassungsliste gesetzt ist:

   * Wenn der URI auf die Zulassungsliste gesetzt ist, übergibt der Server die Anforderung.
   * Wenn der angeforderte URI nicht auf die Zulassungsliste gesetzt wird, ruft der Server den Referrer der Anfrage ab.

1. Wenn die Anforderung einen Referrer enthält, prüft der Server, ob es sich um einen zulässigen Referrer handelt. Wenn dies zulässig ist, sucht der Server nach einer Referrer-Ausnahme:

   * Wenn es sich um eine Ausnahme handelt, wird die Anfrage blockiert.
   * Wenn es sich nicht um eine Ausnahme handelt, wird die Anfrage übergeben.

1. Wenn in der Anfrage kein Referrer enthalten ist, prüft der Server, ob ein Null-Referrer zulässig ist.

   * Wenn eine Null-Referenz zulässig ist, wird die Anfrage übergeben.
   * Wenn ein Null-Referrer nicht zulässig ist, prüft der Server, ob der angeforderte URI eine Ausnahme für Null-Referrer ist, und verarbeitet die Anfrage entsprechend.

## Zulässige Referrer konfigurieren {#configure-allowed-referers}

Wenn Sie Configuration Manager ausführen, werden der Standardhost und die IP-Adresse oder der Forms-Server der Liste &quot;Zulässige Referrer&quot;hinzugefügt. Sie können diese Liste in Administration Console bearbeiten.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;URLs für zulässige Referrer konfigurieren&quot;. Die Liste &quot;Zulässige verweisende Stelle&quot;wird unten auf der Seite angezeigt.
1. Hinzufügen einer zulässigen verweisenden Stelle:

   * Geben Sie einen Hostnamen oder eine IP-Adresse in das Feld &quot;Zulässige Referrer&quot;ein. Um mehrere zulässige Referrer gleichzeitig hinzuzufügen, geben Sie jeden Hostnamen oder jede IP-Adresse in eine neue Zeile ein.
   * Geben Sie in den Feldern &quot;HTTP-Anschluss&quot;und &quot;HTTPS-Anschluss&quot;an, welche Ports für HTTP, HTTPS oder beide zulässig sein sollen. Wenn Sie diese Felder leer lassen, werden die Standardanschlüsse (Port 80 für HTTP und Port 443 für HTTPS) verwendet. Wenn Sie den Wert `0` (null) in die Felder eingeben, werden alle Anschlüsse auf diesem Server aktiviert. Sie können auch eine bestimmte Portnummer eingeben, um nur diesen Port zu aktivieren.
   * Klicken Sie auf Hinzufügen.

1. Um den Eintrag aus der Liste &quot;Zulässige verweisende Stelle&quot;zu entfernen, wählen Sie das Element aus der Liste aus und klicken Sie auf &quot;Löschen&quot;.

   Wenn die Liste der zulässigen Referrer leer ist, funktioniert die CSRF-Funktion nicht mehr und das System wird unsicher.

1. Nachdem Sie die Liste der zulässigen Referrer geändert haben, starten Sie den AEM Forms-Server neu.
