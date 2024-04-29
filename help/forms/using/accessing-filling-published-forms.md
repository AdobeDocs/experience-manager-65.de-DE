---
title: Öffnen und Ausfüllen veröffentlichter Formulare
description: Das Formularportal bietet Web-Entwicklerinnen und Web-Entwicklern Komponenten zum Erstellen und Anpassen von Formularportalen für Websites, die mit Adobe Experience Manager (AEM) erstellt wurden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: aedf890c-a2f1-412f-8897-2492ffab335a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '935'
ht-degree: 100%

---

# Öffnen und Ausfüllen veröffentlichter Formulare{#accessing-and-filling-published-forms}

In einer formularzentrierten Portal-Bereitstellung sind die Formularentwicklung und die Portalentwicklung zwei unterschiedliche Aktivitäten. Während Personen, die für das Formular-Design zuständig sind, Formulare in einem Repository entwerfen und speichern, erstellen Web-Entwicklerinnen und Web-Entwickler eine Web-Anwendung, um Formulare aufzulisten und Übermittlungen zu verarbeiten. Formulare werden dann in die Web-Stufe kopiert, da keine Kommunikation zwischen dem Formular-Repository und der Web-Anwendung besteht.

Dies führt häufig zu Problemen beim Verwalten der Einrichtung und zu Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, ersetzt die Person, die für das Formular-Design zuständig ist, das Formular auf der Web-Ebene, ändert die Web-Anwendung und stellt das Formular erneut auf der öffentlichen Website bereit. Die Neuverteilung der Web-Anwendung kann eine gewisse Server-Ausfallzeit verursachen. Da es sich bei der Server-Ausfallzeit um eine geplante Aktivität handelt, können die Änderungen nicht sofort auf die öffentliche Website übertragen werden.

Forms Portal reduziert den Verwaltungsaufwand und Produktionsverzögerungen. Es bietet Web-Entwicklerinnen und Web-Entwicklern Komponenten zum Erstellen und Anpassen von Formularportalen für Websites, die mit Adobe Experience Manager (AEM) erstellt wurden.

Weitere Informationen über das Formularportal und dessen Funktionen finden Sie unter [Einführung in die Veröffentlichung von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md).

## Erste Schritte mit dem Formularportal {#getting-started-with-forms-portal}

Navigieren Sie zur veröffentlichten Formularportalseite. Weitere Informationen zum Erstellen einer Formularportalseite finden Sie unter [Erstellen einer Formularportalseite](../../forms/using/creating-form-portal-page.md).

Die Komponente „Suche und Auflister“ des Formularportals zeigt die in der Veröffentlichungsinstanz des AEM-Servers verfügbaren Formulare. Diese Liste enthält alle Formulare oder die im Filter definierten Formulare zum Zeitpunkt der Erstellung der Formularportalseite. Eine Formularportalseite ist ähnlich der in der folgenden Abbildung gezeigten:

![Beispiel einer Formularportalseite ](assets/forms-portal-page.png)

Beispiel einer Formularportalseite

### Suche und Auflister {#search-and-lister}

Die Komponente „Suche und Auflister“ ermöglicht das Hinzufügen der folgenden Funktion zu Ihrem Formularportal:

* Auflisten von Formularen in der Bereich-, Karten- oder Rasteransicht, die direkt verfügbar sind. Es werden auch benutzerdefinierte templatesList-Formulare aus bestimmten Ordnern in Forms Manager unterstützt.
* Geben Sie an, wie Formulare gerendert werden: HTML5, PDF oder beides.
* Geben Sie an, wie PDF- und XFA-Formulare gerendert werden: HTML5, PDF oder beides. Nicht-XFA-Formulare wie HTML5.
* Aktivieren Sie die Suche nach Formularen anhand von Kriterien wie zum Beispiel Formulareigenschaften, Metadaten und Tags.
* Senden von Formulardaten an ein Servlet.
* Verwenden Sie benutzerdefinierte Style Sheets (CSS), um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.

Sie können auf der Formularportalseite mithilfe der folgenden Optionen nach Formularen suchen:

* Volltextsuche
* Erweiterte Suche

Mit der Volltextsuche können Sie Formulare anhand der angegebenen Suchbegriffe suchen und auflisten.

![Dialogfeld für die erweiterte Suche](assets/search-panel.png)

Dialogfeld für die erweiterte Suche

Mit der erweiterten Suche können Sie Formulare basierend auf angegebenen Formulareigenschaften suchen. Dies liefert ein genaueres Ergebnis als die Volltextsuche. Die erweiterte Suche umfasst die Suche anhand von Tags, Eigenschaften (wie Autorin bzw. Autor, Beschreibung und Titel), Änderungsdatum und Volltext.

Der Auflister zeigt Formulare anhand der Suchparameter an. Jedes Formular im Suchergebnis wird mit einem Symbol angezeigt, das mit dem entsprechenden Formular verlinkt ist. Sie können auf das Symbol klicken, um das zugehörige Formular zu öffnen und damit zu arbeiten.

### Ausfüllen eines Formulars {#filling-a-form}

![Beispiel für ein adaptives Formular](assets/filling_a_form.png)

Beispiel für ein adaptives Formular

Der Zugriff auf die Formulare ist über den Link möglich, der in der Komponente „Suche und Auflister“ der Seite neben dem Formular zur Verfügung steht.

Jedes Formular enthält Hilfsinformationen, mit denen Benutzende das Formular ausfüllen können.

#### Entwürfe und Übermittlungen {#drafts-and-submission}

Benutzende können optional einen Entwurf eines Formulars speichern, indem sie auf **Speichern** klicken. Dadurch können die Benutzenden über einen bestimmten Zeitraum an einem Formular arbeiten, bevor sie das Formular übermitteln.

Die im Formular eingetragenen Daten (einschließlich Anlagen) werden als Entwurf auf dem Server gespeichert. Der Entwurf eines Formulars kann beliebig oft gespeichert werden. Das gespeicherte Formular wird auf der Registerkarte „Formular“ der Komponente „Entwürfe und Übermittlungen“ der Seite angezeigt.

Nach dem Ausfüllen des Formulars versenden Benutzer die Formulare, indem sie auf dem Formular auf die Schaltfläche „Übermitteln“ klicken. Die übermittelten Formulare werden auf der Registerkarte „Übermittelte Formulare“ der Komponente „Entwürfe und Übermittlungen“ der Seite angezeigt.

>[!NOTE]
>
>Übermittelte Formulare werden nur dann auf der Registerkarte „Übermittelte Formulare“ angezeigt, wenn die Übermittlungsaktion für das adaptive Formular als Forms Portal-Übermittlungsaktion konfiguriert ist. Weitere Informationen zu Sendeaktionen finden Sie unter [Konfigurieren der Sendeaktion](../../forms/using/configuring-submit-actions.md).

![Komponente „Drafts and Submissions“](assets/draft-submission.png)

Komponente „Entwürfe und Sendungen“

## Erstellen eines neuen Formulars mit bereits übermittelten Formulardaten {#start-a-new-form-using-submitted-form-data}

Es gibt bestimmte Formulare, die Sie ausfüllen und oft übermitteln müssen. So wird beispielsweise jedes Jahr das Formular zur Abgabe einer Steuererklärung übermittelt. Dabei ändern sich zwar einige Angaben von Jahr zu Jahr, andere wie zur Person oder zur Familie jedoch nicht. Sie müssen jedoch das gesamte Formular von Grund auf neu ausfüllen.

AEM Forms trägt zu einem optimierten Benutzererlebnis beim Ausfüllen von Formularen bei und reduziert dafür benötigte Zeit erheblich. Endbenutzende können für ein neues Formular die Daten von einem früher übermittelten Formular verwenden. Diese Funktionalität ist in der Komponente [Entwürfe und Übermittlungen](../../forms/using/draft-submission-component.md) integriert. Wenn Sie die Komponente „Entwürfe und Übermittlungen“ zu Ihrer Formularportalseite hinzufügen und veröffentlichen, finden Endbenutzende eine Option auf den Registerkarten „Übermittelte Formulare“ und „Formularentwürfe“. Mit dieser Option können Sie ein neues Formular mit Daten aus einem übermittelten Formular erstellen. Die folgende Abbildung verdeutlicht diese Option.

![start-a-new-form](assets/start-a-new-form.png)

Wenn Sie auf die Schaltfläche klicken, um ein neues Formular zu initiieren, wird ein neues Formular mit Daten aus dem entsprechenden übermittelten Formular geöffnet. Jetzt können Sie die Informationen überprüfen und bei Bedarf aktualisieren und das Formular übermitteln.
