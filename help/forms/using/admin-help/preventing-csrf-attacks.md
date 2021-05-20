---
title: CSRF-Angriffe verhindern
seo-title: CSRF-Angriffe verhindern
description: Erfahren Sie, wie Sie Angriffe Cross-site request forgery (CSRF) verhindern und Benutzerdaten vor Beschädigung schützen.
seo-description: Erfahren Sie, wie Sie Angriffe Cross-site request forgery (CSRF) verhindern und Benutzerdaten vor Beschädigung schützen.
uuid: f3553826-f5eb-40ea-aeb7-90e4ad30598c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a3cbffb7-c1d1-47c2-bcfd-70f1e2d81ac9
exl-id: e17fc114-eba5-4e1b-8e70-ad6af7008018
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 81%

---

# CSRF-Angriffe verhindern {#preventing-csrf-attacks}

## Funktionsweise von CSRF-Angriffen {#how-csrf-attacks-work}

Cross-Site Request Forgery (CSRF) ist eine Website-Schwachstelle, bei der ein gültiger Browser des Benutzers für das Senden einer böswillige Anforderung, möglicherweise über einen iFrame, verwendet wird. Da der Browser Cookies auf Domänenbasis sendet, wenn der Benutzer derzeit bei einer Anwendung angemeldet ist, sind die Daten des Benutzers möglicherweise gefährdet.

Angenommen, Sie sind in einem Browser bei Administration Console angemeldet. Sie erhalten eine E-Mail mit einem Link. Sie klicken auf den Link, der eine neue Registerkarte im Browser öffnet. Die von Ihnen geöffnete Seite enthält einen ausgeblendeten iFrame, der eine böswillige Anforderung beim Formularserver mithilfe der Cookies aus Ihrer authentifizierten AEM Forms-Sitzung erzeugt. Da User Management einen gültigen Cookie erhält, wird die Anforderung übergegeben.

## CSRF-verwandte Begriffe {#csrf-related-terms}

**Referrer:** Die Adresse der Quellseite, von der aus eine Anforderung stammt. Eine Webseite auf „site1.com“ enthält beispielsweise einen Link zu „site2.com“. Beim Klicken auf den Link, wird eine Anforderung an „site2.com“ gesendet. Die Referenz dieser Anforderung ist „site1.com“, da die Anforderung von einer Seite stammt, deren Quelle „site1.com“ ist.

**Auf die Zulassungsliste gesetzt URIs:** URIs identifizieren Ressourcen auf dem Formularserver, die angefordert werden, z. B. /adminui oder /contentspace. Einige Ressourcen ermöglichen einer Anforderung möglicherweise, von einer externen Site aus auf die Anwendung zuzugreifen. Diese Ressourcen werden als auf die Zulassungsliste gesetzt URIs betrachtet. Der Formularserver führt nie eine Referrer-Prüfung von auf die Zulassungsliste gesetzt URIs durch.

**Null-Referrer:** Wenn Sie ein neues Browser-Fenster oder eine neue Registerkarte öffnen, eine Adresse eingeben und die Eingabetaste drücken, ist der Referrer null. Die Anforderung ist neu und stammt nicht aus einer übergeordneten Webseite, daher gibt es keine Referenz für die Anforderung. Der Forms kann eine Null-Referenz aus folgenden Quellen erhalten:

* Anforderungen, die auf SOAP- oder REST-Endpunkten von Acrobat durchgeführt werden
* Beliebige Desktop-Clients, die eine HTTP-Anforderung an auf einem SOAP- oder REST-Endpunkt von AEM Forms durchführen
* Wenn ein neues Browserfenster geöffnet wird und die URL für die Anmeldeseite einer AEM Forms-Webanwendung eingegeben wird

Lassen Sie eine Null-Referenz auf SOAP- und REST-Endpunkten zu. Lassen Sie außerdem eine Null-Referenz auf allen URI-Anmeldeseiten, wie „/adminui“ und „/contentspace“, und den entsprechenden zugeordneten Ressourcen zu. Beispielsweise ist das zugeordnete Servlet für „/contentspace“ „/contentspace/faces/jsp/login.jsp“, was eine Null-Referenzausnahme darstellt. Diese Ausnahme ist nur erforderlich, wenn Sie GET-Filterung für die Webanwendung aktivieren. Die Anwendungen können angeben, ob Null-Referenzen zulässig sind. Siehe &quot;Schutz vor Cross-Site Request Forgery-Angriffen&quot;in [Härtung und Sicherheit für AEM Formulare](https://help.adobe.com/en_US/livecycle/11.0/HardeningSecurity/index.html).

**Zulässige Referrer - Ausnahme:** Zulässige Referrer - Ausnahme ist eine Unterliste der Liste zulässiger Referrer, von der aus Anfragen blockiert werden. Zulässige Referenzauausnahmen beziehen sich insbesondere auf eine Webanwendung. Wenn eine Untergruppe der zulässigen Referrer nicht zum Aufrufen einer bestimmten Webanwendung berechtigt sein soll, können Sie die Referenzen über &quot;Zulässige Referrer - Ausnahmen&quot;in Blockierungslisten aufrufen. Zulässige Referenzausnahmen werden in der Datei „web.xml“ für Ihre Anwendung angegeben. (Siehe den Abschnitt zum Schutz vor Cross-Site Request Forgery-Angriffen in „Härtung und Sicherheit für AEM Forms on Hilfe und Tutorials.)

## Funktionsweise von zulässigen Referenzen {#how-allowed-referers-work}

AEM Forms bietet Referenzfilterung, die CSRF-Angriffe verhindern kann. Im Folgenden wird die Funktionsweise der Referenzfilterung beschrieben:

1. Der Formularserver prüft die für den Aufruf verwendete HTTP-Methode:

   * Bei POST prüft der Formularserver den Referrer-Header.
   * Bei GET umgeht der Formularserver die Referrer-Prüfung, es sei denn, CSRF_CHECK_GETS ist auf „true“ festgelegt. In diesem Fall wird der Referrer-Header überprüft. CSRF_CHECK_GETS wird in der Datei „web.xml“ für Ihre Anwendung angegeben. (Siehe den Abschnitt zum Schutz vor Cross-Site Request Forgery-Angriffen[ in der Unix-Systembibliothek](https://help.adobe.com/en_US/livecycle/11.0/HardeningSecurity/index.html).) und Sicherheit

1. Der Formularserver prüft, ob der angeforderte URI auf die Zulassungsliste gesetzt ist:

   * Wenn der URI auf die Zulassungsliste gesetzt ist, übergibt der Server die Anforderung.
   * Wenn der angeforderte URI nicht auf die Zulassungsliste gesetzt wird, ruft der Server den Referrer der Anfrage ab.

1. Wenn es eine Referenz in der Anforderung gibt, überprüft der Server, ob es sich um eine zugelassene Referenz handelt. Wenn sie zulässig ist, sucht der Server nach einer Referenzausnahme:

   * Wenn sie eine Ausnahme ist, wird die Anforderung blockiert.
   * Wenn sie keine Ausnahme ist, wird die Anforderung übergeben.

1. Wenn es keine Referenz in der Anforderung gibt, überprüft der Server, ob eine Null-Referenz zulässig ist.

   * Wenn eine Null-Referenz zulässig ist, wird die Anforderung übergeben.
   * Wenn eine Null-Referenz nicht zulässig ist, überprüft der Server, ob der angeforderte URI eine Ausnahme für die Null-Referenz ist, und bearbeitet die Anfrage entsprechend.

## Zulässige Referenzen konfigurieren  {#configure-allowed-referers}

Wenn Sie Configuration Manager ausführen, werden der Standardhost und die IP-Adresse oder der Formularserver der Liste für zulässige Referenzen hinzugefügt. Sie können diese Liste in Administration Console bearbeiten.

1. Klicken Sie in Administration Console auf Einstellungen > User Management > Konfiguration > URLs für zulässige Referenzen konfigurieren. Die Liste für zulässige Referenzen wird unten auf der Seite angezeigt.
1. Hinzufügen einer zulässigen Referenz:

   * Geben Sie einen Hostnamen oder eine IP-Adresse in das Feld „Zulässige Referenzen“ ein. Um mehr als eine zulässige Referenz gleichzeitig hinzuzufügen, geben Sie jeden Hostnamen oder jede IP-Adresse in eine neue Zeile ein.
   * Geben Sie im Feld „HTTP-Anschluss“ und „HTTPS-Anschluss“ an, welche Anschlüsse Sie für HTTP, HTTPS oder beide zulassen möchten. Wenn Sie diese Felder leer lassen, werden die Standardanschlüsse (Anschluss 80 für HTTP und Anschluss 443 für HTTPS) verwendet. Wenn Sie den Wert `0` (null) in die Felder eingeben, werden alle Anschlüsse auf diesem Server aktiviert. Sie können außerdem eine bestimmte Anschlussnummer eingeben, damit nur dieser Anschluss aktiviert wird.
   * Klicken Sie auf Hinzufügen.

1. Um Einträge aus der Liste für zulässige Referenzen zu entfernen, wählen Sie das Element aus der Liste aus und klicken auf „Löschen“.

   Wenn die Liste für zulässige Referenzen leer ist, funktionieren die CSRF-Funktionen nicht mher und das System wird unsicher.

1. Nachdem Sie die Liste für zulässige Referenzen geändert haben, starten Sie den AEM Forms-Server neu.
