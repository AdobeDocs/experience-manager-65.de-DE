---
title: Erstellen einer SCF-Sandbox
seo-title: Erstellen einer SCF-Sandbox
description: Dieses Tutorial richtet sich vor allem an Entwickler, die neu bei AEM sind und an SCF-Komponenten interessiert sind.  Es durchläuft die Erstellung einer SCF Sandbox-Site
seo-description: Dieses Tutorial richtet sich vor allem an Entwickler, die neu bei AEM sind und an SCF-Komponenten interessiert sind.  Es durchläuft die Erstellung einer SCF Sandbox-Site
uuid: ee52e670-e1e6-4bcd-9548-c963142e6704
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e1b5c25d-cbdd-421c-b81a-feb6039610a3
translation-type: tm+mt
source-git-commit: 548e19b0fc76ede8685ea938ed871fbdc8c3858f
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---



# Erstellen einer SCF-Sandbox {#create-an-scf-sandbox}


Ab AEM 6.1 Communities ist es am einfachsten, eine Sandbox schnell zu erstellen, eine Community-Site zu erstellen. Siehe [Erste Schritte mit AEM Communities](getting-started.md).

Ein weiteres nützliches Tool für Entwickler ist der [Community Components guide](components-guide.md), der die Erforschung und schnelle Prototypisierung von Communities-Komponenten und -Funktionen ermöglicht.

Die Erstellung einer Website kann nützlich sein, um die Struktur einer AEM Website zu verstehen, die Community-Funktionen enthalten kann, und gleichzeitig einfache Seiten bereitzustellen, auf denen die Arbeit mit dem [Social-Komponenten-Framework (SCF)](scf.md) erforscht werden kann.

Dieses Tutorial richtet sich vor allem an Entwickler, die neu bei AEM sind und an SCF-Komponenten interessiert sind. Es führt durch die Erstellung einer SCF Sandbox-Site, ähnlich dem Tutorial für [Wie eine vollständig ausgestattete Internet-Website](../../help/sites-developing/website.md) erstellt wird, das sich auf Site-Strukturen wie Navigation, Logo, Suche, Symbolleiste und Auflistung untergeordneter Seiten konzentriert.

Die Entwicklung erfolgt in einer Autoreninstanz, während das Experimentieren mit der Site am besten in einer Veröffentlichungsinstanz erfolgt.

Die Schritte in diesem Lernprogramm sind:

* [Website-Struktur einrichten](setup-website.md)
* [Anfänglicher Sandbox-Antrag](initial-app.md)
* [Anfänglicher Sandbox-Inhalt](initial-content.md)
* [Sandbox-Anwendung entwickeln](develop-app.md)
* [hinzufügen Clientlibs](add-clientlibs.md)
* [Entwicklung von Sandbox-Inhalten](develop-content.md)

>[!CAUTION]
>
>In diesem Lernprogramm wird keine Community-Site mit den Funktionen erstellt, die mit der Konsole [Communities Sites](sites-console.md) erstellt wurden. In diesem Lernprogramm wird beispielsweise nicht beschrieben, wie Sie Anmeldung, Selbstregistrierung, [Social-Anmeldung](social-login.md), Messaging, Profile usw. einrichten.
>
>Wenn eine einfache Community-Site bevorzugt wird, folgen Sie dem Lernprogramm [Beispielseite erstellen](create-sample-page.md).

## Voraussetzungen {#prerequisites}

In diesem Lernprogramm wird davon ausgegangen, dass ein AEM Autor und eine AEM Veröffentlichungsinstanz installiert sind, für die das [letzte Release](deploy-communities.md#latest-releases) von Communities installiert ist.

Im Folgenden finden Sie einige hilfreiche Links für Entwickler, die neu auf die AEM Plattform zugreifen:

* [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started): zum Bereitstellen AEM Instanzen.

   * [Grundlagen](../../help/sites-developing/the-basics.md): für Entwickler von Websites und Funktionen.
   * [Erste Schritte für Autoren](../../help/sites-authoring/first-steps.md): zum Authoring von Seiteninhalten.

## Verwenden der CRXDE Lite Development Umgebung {#using-crxde-lite-development-environment}

AEM Entwickler verbringen einen Großteil ihrer Zeit in der [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)-Entwicklungs-Umgebung auf einer Autoreninstanz. CRXDE Lite bietet einen weniger eingeschränkten Zugriff auf das CRX-Repository. Klassische UI-Werkzeuge und touchfähige UI-Konsolen bieten strukturierteren Zugriff auf bestimmte Teile des CRX-Repositorys.

Nach der Anmeldung mit Administratorrechten gibt es verschiedene Möglichkeiten, auf die CRXDE Lite zuzugreifen:

1. Wählen Sie in der globalen Navigation die Option Navigation **[!UICONTROL Tools > CRXDE Lite]**.

   ![crxde-lite](assets/tools-crxde.png)

2. Blättern Sie auf der Begrüßungsseite [klassische Benutzeroberfläche](http://localhost:4502/welcome.html) nach unten und klicken Sie im rechten Bereich auf **[!UICONTROL CRXDE Lite]**.

   ![classic-ui-crxde](assets/classic-ui-crxde.png)

3. Gehen Sie direkt zu `CRXDE Lite`: `<server>:<port>/crx/de`

   Beispiel für eine lokale Autorinstanz: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

Um mit CRXDE Lite arbeiten zu können, müssen Sie sich mit Entwickler- oder Administratorberechtigungen anmelden. Bei der standardmäßigen localhost-Instanz können Sie sich mit

* `username: admin`
* `password: admin`


**Denken Sie** daran, dass bei dieser Anmeldung ein Timeout eintritt und Sie sich regelmäßig erneut anmelden müssen. Verwenden Sie dazu den Pulldown am rechten Ende der Werkzeugleiste von CRXDe Lite.

Wenn Sie nicht angemeldet sind, können Sie weder im JCR-Repository navigieren noch Bearbeitungs-/Speichervorgänge durchführen.

***Im Zweifelsfall melden Sie sich erneut an!***

![relogin](assets/relogin.png)
