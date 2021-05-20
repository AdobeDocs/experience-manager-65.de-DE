---
title: Erstellen einer SCF-Sandbox
seo-title: Erstellen einer SCF-Sandbox
description: Dieses Tutorial richtet sich in erster Linie an Entwickler, die neu bei AEM sind und an der Verwendung von SCF-Komponenten interessiert sind.  Er führt durch die Erstellung einer SCF-Sandbox-Site.
seo-description: Dieses Tutorial richtet sich in erster Linie an Entwickler, die neu bei AEM sind und an der Verwendung von SCF-Komponenten interessiert sind.  Er führt durch die Erstellung einer SCF-Sandbox-Site.
uuid: ee52e670-e1e6-4bcd-9548-c963142e6704
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e1b5c25d-cbdd-421c-b81a-feb6039610a3
exl-id: 89858814-6625-4a56-8359-cc1eca402816
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---

# Erstellen einer SCF-Sandbox {#create-an-scf-sandbox}


Ab AEM 6.1 Communities ist es am einfachsten, eine Sandbox schnell zu erstellen, eine Community-Site zu erstellen. Siehe [Erste Schritte mit AEM Communities](getting-started.md).

Ein weiteres nützliches Tool für Entwickler ist das [Handbuch zu Community-Komponenten](components-guide.md), das die Erforschung und schnelle Prototypisierung von Communities-Komponenten und -Funktionen ermöglicht.

Die Erstellung einer Website kann nützlich sein, um die Struktur einer AEM Website zu verstehen, die Communities-Funktionen enthalten kann, und gleichzeitig einfache Seiten bereitzustellen, auf denen Sie die Arbeit mit dem [Social Component Framework (SCF)](scf.md) untersuchen können.

Dieses Tutorial richtet sich in erster Linie an Entwickler, die neu bei AEM sind und an der Verwendung von SCF-Komponenten interessiert sind. Er führt durch die Erstellung einer SCF-Sandbox-Site, ähnlich dem Tutorial für [So erstellen Sie eine vollständig vorgestellte Internet-Website](../../help/sites-developing/website.md) , die sich auf Site-Strukturen wie Navigation, Logo, Suche, Symbolleiste und Auflistung untergeordneter Seiten konzentriert.

Die Entwicklung erfolgt auf einer Autoreninstanz, während das Experimentieren mit der Site auf einer Veröffentlichungsinstanz am besten ist.

Die Schritte in diesem Tutorial sind:

* [Einrichten der Website-Struktur](setup-website.md)
* [Erste Sandbox-Anwendung](initial-app.md)
* [Anfänglicher Sandbox-Inhalt](initial-content.md)
* [Entwickeln von Sandbox-Anwendungen](develop-app.md)
* [Clientlibs hinzufügen](add-clientlibs.md)
* [Entwickeln von Sandbox-Inhalten](develop-content.md)

>[!CAUTION]
>
>In diesem Tutorial wird keine Community-Site mit den Funktionen erstellt, die mit der [Communities Sites Console](sites-console.md) erstellt wurden. In diesem Tutorial wird beispielsweise nicht beschrieben, wie Anmelden, Selbstregistrierung, [Anmeldung in sozialen Netzwerken](social-login.md), Nachrichten, Profile usw. eingerichtet werden.
>
>Wenn eine einfache Community-Site bevorzugt wird, folgen Sie dem Tutorial [Erstellen einer Beispielseite](create-sample-page.md) .

## Voraussetzungen {#prerequisites}

In diesem Tutorial wird davon ausgegangen, dass eine AEM Autoren- und eine AEM Veröffentlichungsinstanz installiert sind, die über die [neueste Version](deploy-communities.md#latest-releases) von Communities verfügt.

Im Folgenden finden Sie einige hilfreiche Links für Entwickler, die mit der AEM-Plattform neu sind:

* [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started): für die Bereitstellung AEM Instanzen.

   * [Grundlagen](../../help/sites-developing/the-basics.md): für Entwickler von Websites und Funktionen.
   * [Erste Schritte für Autoren](../../help/sites-authoring/first-steps.md): für die Bearbeitung von Seiteninhalten.

## Verwenden der CRXDE Lite-Entwicklungsumgebung {#using-crxde-lite-development-environment}

AEM Entwickler verbringen einen Großteil ihrer Zeit in der Entwicklungsumgebung [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) in einer Autoreninstanz. CRXDE Lite bietet einen weniger eingeschränkten Zugriff auf das CRX-Repository. Klassische UI-Tools und Touch-optimierte UI-Konsolen bieten einen strukturierteren Zugriff auf bestimmte Bereiche des CRX-Repositorys.

Nach der Anmeldung mit Administratorrechten gibt es verschiedene Möglichkeiten, auf die CRXDE Lite zuzugreifen:

1. Wählen Sie in der globalen Navigation die Option Navigation **[!UICONTROL Tools > CRXDE Lite]** aus.

   ![crxde-lite](assets/tools-crxde.png)

2. Scrollen Sie auf der Begrüßungsseite [Klassische Benutzeroberfläche](http://localhost:4502/welcome.html) nach unten und klicken Sie im rechten Bereich auf **[!UICONTROL CRXDE Lite]**.

   ![classic-ui-crxde](assets/classic-ui-crxde.png)

3. Gehen Sie direkt zu `CRXDE Lite`: `<server>:<port>/crx/de`

   Beispiel für eine lokale Autoreninstanz: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

Um mit CRXDE Lite zu arbeiten, müssen Sie sich mit Entwickler- oder Administratorrechten anmelden. Für die standardmäßige localhost-Instanz können Sie sich mit

* `username: admin`
* `password: admin`


**Beachten Sie,** dass bei dieser Anmeldung ein Timeout auftritt und Sie sich regelmäßig mit dem Pulldown am rechten Ende der Symbolleiste von CRXDe Lite erneut anmelden müssen.

Wenn Sie nicht angemeldet sind, können Sie nicht im JCR-Repository navigieren oder Bearbeitungs-/Speichervorgänge durchführen.

***Im Zweifelsfall melden Sie sich erneut an!***

![relogin](assets/relogin.png)
