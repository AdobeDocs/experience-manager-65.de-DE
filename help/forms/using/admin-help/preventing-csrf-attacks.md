---
title: Verhindern von CSRF-Angriffen
description: Erfahren Sie, wie Sie Cross-Site Request Forgery(CSRF)-Angriffe verhindern und Benutzerdaten vor einem unbefugten Zugriff schützen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e17fc114-eba5-4e1b-8e70-ad6af7008018
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 97%

---

# Verhindern von CSRF-Angriffen {#preventing-csrf-attacks}

## Funktionsweise von CSRF-Angriffen {#how-csrf-attacks-work}

Cross-Site Request Forgery (CSRF) ist eine Website-Schwachstelle, bei der der Browser eines gültigen Benutzers verwendet wird, um eine böswillige Anfrage zu senden, möglicherweise über einen iFrame. Da der Browser Cookies auf Domain-Basis sendet, wenn die Benutzerin oder der Benutzer bei einer Anwendung angemeldet ist, sind die Benutzerdaten möglicherweise gefährdet.

Angenommen, Sie sind in einem Browser bei der Administrationskonsole angemeldet. Sie erhalten eine E-Mail-Nachricht mit einem Link. Sie klicken auf den Link, über den eine neue Registerkarte im Browser geöffnet wird. Die von Ihnen geöffnete Seite enthält einen ausgeblendeten iFrame, der eine böswillige Anfrage beim Formular-Server mithilfe des Cookies aus Ihrer authentifizierten AEM Forms-Sitzung erzeugt. Da die Benutzerverwaltung einen gültigen Cookie erhält, wird die Anfrage weitergegeben.

## CSRF-bezogene Begriffe {#csrf-related-terms}

**Referer:** Die Adresse der Quellseite, von der eine Anfrage kommt. Beispielsweise enthält eine Web-Seite unter site1.com einen Link zu site2.com. Durch Klicken auf den Link wird eine Anfrage an site2.com gesendet. Der Referrer dieser Anfrage ist site1.com, da die Anfrage von einer Seite mit site1.com als Quelle stammt.

**Auf die Zulassungsliste gesetzte URIs:** URIs identifizieren Ressourcen auf dem Formular-Server, die angefordert werden, z. B. „/adminui“ oder „/contentspace“. Einige Ressourcen ermöglichen einer Anforderung möglicherweise, von einer externen Site aus auf die Anwendung zuzugreifen. Diese Ressourcen gelten als auf die Zulassungsliste gesetzte URIs. Der Formular-Server führt keine Referrer-Überprüfungen für URIs durch, die sich auf der Zulassungsliste befinden.

**Null-Referrer:** Wenn Sie ein neues Browser-Fenster oder eine neue Registerkarte öffnen, dann eine Adresse eingeben und die Eingabetaste drücken, ist der Referrer null. Die Anfrage ist völlig neu und stammt nicht von einer übergeordneten Web-Seite. Daher gibt es keinen Referrer für die Anfrage. Der Formular-Server kann einen Null-Referrer von folgenden Quellen erhalten:

* Anfragen, die auf SOAP- oder REST-Endpunkten von Acrobat durchgeführt werden
* beliebige Desktop-Clients, die eine HTTP-Anfrage auf einem SOAP- oder REST-Endpunkt von AEM Forms durchführen
* beim Öffnen eines neuen Browser-Fensters und Eingeben der URL für die Anmeldeseite einer AEM Forms-Web-Anwendung

Lassen Sie einen Null-Referrer auf SOAP- und REST-Endpunkten zu. Lassen Sie außerdem einen Null-Referrer auf allen URI-Anmeldeseiten wie „/adminui“ und „/contentspace“ und den entsprechenden zugeordneten Ressourcen zu. Beispielsweise ist „/contentspace/faces/jsp/login.jsp“ das zugeordnete Servlet für „/contentspace“, was eine Null-Referrer-Ausnahme sein sollte. Diese Ausnahme ist nur erforderlich, wenn Sie die GET-Filterung für die Web-Anwendung aktivieren. In Ihren Anwendungen kann angegeben werden, ob Null-Referrer zulässig sind. Siehe „Schutz vor Cross-Site Request Forgery-Angriffen“ in [Härtung und Sicherheit für AEM Forms](https://help.adobe.com/de_DE/livecycle/11.0/HardeningSecurity/index.html).

**Zulässige Referrer-Ausnahme:** Dies ist eine Unterliste der Liste der zulässigen Referrer, von denen Anfragen blockiert werden. Zulässige Referrer-Ausnahmen sind spezifisch für eine Web-Anwendung. Wenn einer Untergruppe der zulässigen Referrer nicht erlaubt werden soll, eine bestimmte Web-Anwendung aufzurufen, können Sie die Referrer über die zulässigen Referrer-Ausnahmen auf eine Blockierungsliste setzen. Zulässige Referrer-Ausnahmen werden in der Datei „web.xml“ für Ihre Anwendung angegeben. (Siehe den Abschnitt zum Schutz vor Cross-Site Request Forgery-Angriffen in „Härtung und Sicherheit für AEM Forms“ auf der Seite „Hilfe und Tutorials“.)

## Funktionsweise zulässiger Referrer {#how-allowed-referers-work}

AEM Forms ermöglicht eine Referrer-Filterung, was CSRF-Angriffe verhindern kann. So funktioniert die Referrer-Filterung:

1. Der Formular-Server prüft die für den Aufruf verwendete HTTP-Methode:

   * Bei der POST-Methode prüft der Formular-Server den Referrer-Header.
   * Bei der GET-Methode umgeht der Formular-Server die Referrer-Prüfung, es sei denn, CSRF_CHECK_GETS ist auf „true“ gesetzt. In diesem Fall wird der Referrer-Header überprüft. CSRF_CHECK_GETS ist in der Datei web.xml für Ihre Anwendung festgelegt. (Siehe „Schutz vor Cross-Site Request Forgery-Angriffen“ im [Handbuch für Härtung und Sicherheit](https://help.adobe.com/de_DE/livecycle/11.0/HardeningSecurity/index.html)).

1. Der Formular-Server prüft, ob der angeforderte URI auf die Zulassungsliste gesetzt wurde:

   * Wenn der URI auf die Zulassungsliste gesetzt ist, übergibt der Server die Anforderung.
   * Wenn sich der angeforderte URI nicht auf der Zulassungsliste befindet, ruft der Server den Referrer der Anfrage ab.

1. Wenn in der Anfrage ein Referrer angegeben ist, prüft der Server, ob es sich um einen zulässigen Referrer handelt. Wenn der Referrer zulässig ist, prüft der Server, ob es sich um eine Referrer-Ausnahme handelt:

   * Wenn es sich um eine Ausnahme handelt, wird die Anfrage blockiert.
   * Wenn es sich nicht um eine Ausnahme handelt, wird die Anfrage übergeben.

1. Wenn in der Anfrage kein Referrer angegeben ist, prüft der Server, ob ein Null-Referrer zulässig ist.

   * Wenn ein Null-Referrer zulässig ist, wird die Anfrage übergeben.
   * Wenn ein Null-Referrer nicht zulässig ist, überprüft der Server, ob der angeforderte URI eine Ausnahme für den Null-Referrer ist, und bearbeitet die Anfrage entsprechend.

## Konfigurieren der zulässigen Referrer {#configure-allowed-referers}

Wenn Sie Configuration Manager ausführen, werden der Standardhost und die IP-Adresse oder der Formular-Server der Liste für zulässige Referrer hinzugefügt. Sie können diese Liste in der Administrationskonsole bearbeiten.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „URLs für zulässige Referrer konfigurieren“. Die Liste für zulässige Referrer wird unten auf der Seite angezeigt.
1. Hinzufügen eines zulässigen Referrers:

   * Geben Sie einen Hostnamen oder eine IP-Adresse in das Feld „Zulässige Referrer“ ein. Um mehr als einen zulässigen Referrer gleichzeitig hinzuzufügen, geben Sie jeden Hostnamen oder jede IP-Adresse in eine neue Zeile ein.
   * Geben Sie im Feld „HTTP-Port“ und „HTTPS-Port“ an, welche Ports Sie für HTTP, HTTPS oder beide zulassen möchten. Wenn Sie diese Felder leer lassen, werden die Standard-Ports (Port 80 für HTTP und Port 443 für HTTPS) verwendet. Wenn Sie den Wert `0` (null) in die Felder eingeben, werden alle Anschlüsse auf diesem Server aktiviert. Sie können außerdem eine bestimmte Port-Nummer eingeben, damit nur dieser Port aktiviert wird.
   * Klicken Sie auf Hinzufügen.

1. Um Einträge aus der Liste für zulässige Referrer zu entfernen, wählen Sie das Element aus der Liste aus und klicken auf „Löschen“.

   Wenn die Liste für zulässige Referrer leer ist, funktionieren die CSRF-Funktionen nicht mehr und das System wird unsicher.

1. Nachdem Sie die Liste für zulässige Referrer geändert haben, starten Sie den AEM Forms-Server neu.
