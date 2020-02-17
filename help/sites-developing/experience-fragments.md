---
title: Experience Fragments
seo-title: Experience Fragments
description: Erfahren Sie mehr zum Anpassen von Erlebnisfragmenten.
seo-description: Erfahren Sie mehr zum Anpassen von Erlebnisfragmenten.
uuid: fc9f7e59-bd7c-437a-8c63-de8559b5768d
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c02e713e-15f3-408b-879a-d5eb014aef02
docset: aem65
translation-type: tm+mt
source-git-commit: 25eff10d4be811774e7a25cebf7e0506acfd5b0b

---


# Experience Fragments{#experience-fragments}

## Grundlagen {#the-basics}

Ein [Experience Fragment](/help/sites-authoring/experience-fragments.md) ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können.

Ein Erlebnisfragment-Master und/oder eine Variante verwendet:

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

Da es keine gibt, wird `/libs/cq/experience-fragments/components/xfpage/xfpage.html` auf

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## Die Plain-HTML-Wiedergabe {#the-plain-html-rendition}

Using the `.plain.` selector in the URL, you can access the plain HTML rendition.

Diese ist über den Browser verfügbar, aber ihr Hauptzweck ist es, anderen Applikationen (beispielsweise Web-Applikationen von Drittanbietern oder benutzerdefinierten mobilen Implementierungen) den direkten Zugriff auf den Inhalt des Erlebnisfragments zu ermöglichen, und zwar allein über die URL.

Die Plain-HTML-Wiedergabe fügt den Protokoll-, Host- und Kontextpfad zu Pfaden hinzu, welche:

* des Typs: `src`, `href`oder `action`

* or end with: `-src`, or `-href`

Beispiel:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Links verweisen immer auf die Veröffentlichungsinstanz. Sie sind für die Nutzung durch Dritte bestimmt, sodass der Link immer von der Veröffentlichungsinstanz und nicht von der Autoreninstanz aufgerufen wird.

![xf-14](assets/xf-14.png)

Der Selektor für einfache Darstellung verwendet anstelle zusätzlicher Skripten einen Transformer. Der [Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wird als Transformator verwendet. Dies wird konfiguriert unter

* `/libs/experience-fragments/config/rewriter/experiencefragments`

## Social-Variationen {#social-variations}

Social-Varianten können in sozialen Medien (Text und Bild) veröffentlicht werden. In AEM können diese Social-Varianten Komponenten enthalten. zum Beispiel Textkomponenten, Bildkomponenten.

Das Bild und der Text für den Social-Beitrag können aus jedem Bildressourcentyp oder jedem Textressourcentyp in jeder Tiefe genommen werden (entweder im Baustein- oder Layout-Container).

Social-Varianten ermöglichen auch Bausteine und berücksichtigen sie bei Social-Aktionen (in der Veröffentlichungsumgebung).

Um den richtigen Text und das richtige Bild im Social Media-Netzwerk zu veröffentlichen, müssen einige Konventionen beachtet werden, wenn Sie eigene benutzerdefinierte Komponenten entwickeln.

Dazu müssen die folgenden Eigenschaften verwendet werden:

* So extrahieren Sie das Bild

   * `fileReference`
   * `fileName`

* So extrahieren Sie den Text

   * `text`

Komponenten, die diese Konvention nicht verwenden, werden nicht berücksichtigt.

## Vorlagen für Erlebnisfragmente {#templates-for-experience-fragments}

>[!CAUTION]
>
>***Für Erlebnisfragmente werden nur*** [bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) unterstützt.

Beim Entwickeln einer neuen Vorlage für Erlebnisfragmente folgen Sie den Standardverfahren für eine [bearbeitbare Vorlage](/help/sites-developing/page-templates-editable.md).

Um eine Erlebnisfragmentvorlage zu erstellen, die vom Assistenten **Erlebnisfragment** erstellt wird, müssen Sie einen der folgenden Regelsätze ausführen:

1. Beide:

   1. Der Ressourcentyp der Vorlage (der ursprüngliche Knoten) muss übernehmen von:
      `cq/experience-fragments/components/xfpage`

   1. Der Name der Vorlage muss beginnen mit:
      `experience-fragments`
Dadurch können Benutzer Erlebnisfragmente in /content/experience-fragments erstellen, da die `cq:allowedTemplates` Eigenschaft dieses Ordners alle Vorlagen enthält, deren Namen mit beginnen `experience-fragment`. Kunden können diese Eigenschaft aktualisieren, um ihr eigenes Benennungsschema oder ihre eigenen Vorlagenspeicherorte einzuschließen.

1. [Zulässige Vorlagen](/help/sites-authoring/experience-fragments.md#configure-allowed-templates-folder) können in der Experience Fragments-Konsole konfiguriert werden.
<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Komponenten für Erlebnisfragmente {#components-for-experience-fragments}

[Die Entwicklung von Komponenten](/help/sites-developing/components.md) für die Verwendung mit/in Erlebnisfragmenten erfolgt gemäß den Standardverfahren.

Die einzige zusätzliche Konfiguration besteht darin, sicherzustellen, dass die Komponenten in der Vorlage [zulässig sind. Dies wird mit der Content Policy](/help/sites-developing/page-templates-editable.md#content-policies)erreicht.

## Der Experience Fragment Link Rewriter Provider – HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM haben Sie die Möglichkeit, Erlebnisfragmente zu erstellen. Ein Experience Fragment:

* aus einer Gruppe von Komponenten und einem Layout besteht,
* kann unabhängig von einer AEM-Seite vorhanden sein.

Einer der Anwendungsfälle für solche Gruppen ist das Einbetten von Inhalten in Touchpoints von Drittanbietern, wie z. B. Adobe Target.

### Standardmäßige Linkumbenennung {#default-link-rewriting}

Mit der Funktion [In Target](/help/sites-administering/experience-fragments-target.md) exportieren können Sie:

* Erlebnisfragment erstellen,
* Komponenten hinzufügen,
* und exportieren Sie es dann als Adobe Target-Angebot entweder im HTML- oder JSON-Format.

Diese Funktion kann in einer Autoreninstanz von AEM[](/help/sites-administering/experience-fragments-target.md#Prerequisites)aktiviert werden. Es erfordert eine gültige Adobe Target-Konfiguration und Konfigurationen für den Link Externalizer.

Der Link-Externalisierer wird verwendet, um die richtigen URLs zu ermitteln, die beim Erstellen der HTML-Version des Target-Angebots erforderlich sind, das anschließend an Adobe Target gesendet wird. Dies ist erforderlich, da Adobe Target erfordert, dass alle Links im Target-HTML-Angebot öffentlich zugänglich sind. Dies bedeutet, dass alle Ressourcen, auf die die Links verweisen, und das Erlebnisfragment selbst veröffentlicht werden müssen, bevor sie verwendet werden können.

Wenn Sie ein Target-HTML-Angebot erstellen, wird eine Anforderung standardmäßig an eine benutzerdefinierte Sling-Auswahl in AEM gesendet. Dieser Selektor wird aufgerufen `.nocloudconfigs.html`. Wie der Name schon sagt, wird ein einfaches HTML-Rendering eines Erlebnisfragments erstellt, jedoch keine Cloud-Konfigurationen (was überflüssige Informationen sein würde).

Nachdem Sie die HTML-Seite generiert haben, nimmt die Sling Rewriter-Pipeline Änderungen an der Ausgabe vor:

1. Die Elemente `html`, `head`und `body` werden durch `div` Elemente ersetzt. Die Elemente `meta`, `noscript` und `title` werden entfernt (sie sind untergeordnete Elemente des ursprünglichen `head` Elements und werden nicht berücksichtigt, wenn dies durch das `div` -Element ersetzt wird).

   Dies geschieht, um sicherzustellen, dass das HTML-Target-Angebot in Target-Aktivitäten einbezogen werden kann.

1. AEM ändert alle internen Links im HTML-Code, sodass sie auf eine veröffentlichte Ressource verweisen.

   Um die zu ändernden Links zu bestimmen, folgt AEM für Attribute von HTML-Elementen:

   1. `src` Attribute
   1. `href` Attribute
   1. `*-src` Attribute (z. B. data-src, custom-src usw.)
   1. `*-href` Attribute (z. B. `data-href`, `custom-href`, `img-href`usw.)
   >[!NOTE]
   >
   >In den meisten Fällen handelt es sich bei den internen Links im HTML-Code um relative Links. Es kann jedoch vorkommen, dass benutzerdefinierte Komponenten vollständige URLs im HTML-Code bereitstellen. Standardmäßig ignoriert AEM diese vollständigen URLs und nimmt keine Änderungen vor.

   Die Links in diesen Attributen werden über den AEM Link Externalizer ausgeführt, `publishLink()` um die URL so neu zu erstellen, als wäre sie auf einer veröffentlichten Instanz und als solche öffentlich verfügbar.

Bei Verwendung einer vordefinierten Implementierung sollte der oben beschriebene Prozess ausreichen, um das Target-Angebot aus dem Erlebnisfragment zu generieren und es dann in Adobe Target zu exportieren. Es gibt jedoch einige Anwendungsfälle, die in diesem Prozess nicht berücksichtigt werden; Dazu gehören:

* Sling-Zuordnung nur für die Veröffentlichungsinstanz verfügbar
* Dispatcher-Umleitungen

Für diese Anwendungsfälle stellt AEM die Schnittstelle für den Link Rewriter Provider bereit.

### Benutzeroberfläche des Link Rewriter-Anbieters {#link-rewriter-provider-interface}

>[!NOTE]
>
>Diese Schnittstelle wurde in [AEM 6.5 SP1 (6.5.1.0)](/help/release-notes/sp-release-notes.md)eingeführt.

Für kompliziertere Fälle, die nicht vom [Standard](#default-link-rewriting)abgedeckt werden, bietet AEM die Link-Rewriter-Provider-Schnittstelle. Dies ist eine `ConsumerType` Schnittstelle, die Sie als Dienst in Ihre Pakete implementieren können. Es umgeht die Änderungen, die AEM an internen Links eines HTML-Angebots vornimmt, wie sie aus einem Erlebnisfragment gerendert werden. Diese Oberfläche ermöglicht es Ihnen, den Prozess des Umschreibens interner HTML-Links an Ihre geschäftlichen Anforderungen anzupassen.

Beispiele für Anwendungsfälle für die Implementierung dieser Schnittstelle als Dienst:

* Sling-Zuordnungen sind in den Veröffentlichungsinstanzen aktiviert, nicht jedoch in der Autoreninstanz
* Eine Dispatcher- oder ähnliche Technologie wird verwendet, um URLs intern umzuleiten
* Es gibt `sling:alias mechanisms` Ressourcen

>[!NOTE]
>
>Diese Schnittstelle verarbeitet nur die internen HTML-Links aus dem generierten Target-Angebot.

Die Benutzeroberfläche des Link-Rewriter-Providers ( `ExperienceFragmentLinkRewriterProvider`) lautet wie folgt:

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### Verwendung der Oberfläche des Link-Rewriter-Providers {#how-to-use-the-link-rewriter-provider-interface}

Um die Oberfläche zu verwenden, müssen Sie zunächst ein Bundle erstellen, das eine neue Dienstkomponente enthält, die die Schnittstelle für den Link Rewriter Provider implementiert.

Dieser Dienst wird verwendet, um die Umschreibung von Erlebnisfragment-Export in Target einzubinden, um Zugriff auf die verschiedenen Links zu erhalten.

Beispiel, `ComponentService`:

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

Damit der Dienst funktioniert, müssen jetzt drei Methoden innerhalb des Dienstes implementiert werden:

* ` [shouldRewrite](#shouldrewrite)`
* ` [rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* ` [getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

Sie müssen dem System angeben, ob die Links umgeschrieben werden müssen, wenn für eine bestimmte Erlebnisfragment-Variante ein Aufruf für &quot;In Target exportieren&quot;erfolgt. Implementieren Sie dazu die folgende Methode:

`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

Beispiel:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

Diese Methode erhält als Parameter die Erlebnisfragment-Variation, die das System Export in Target derzeit umschreibt.

Im obigen Beispiel möchten wir Folgendes umschreiben:

* Links vorhanden in `src`

* `href` Nur Attribute

* für ein bestimmtes Erlebnisfragment:
   `/content/experience-fragment/master`

Alle anderen Erlebnisfragmente, die das System &quot;In Target exportieren&quot;durchlaufen, werden ignoriert und nicht von den in diesem Dienst implementierten Änderungen betroffen.

#### rewriteLink {#rewritelink}

Für die Erlebnisfragment-Variante, die vom Umschreibungsprozess betroffen ist, wird der Dienst die Linkumschreibung bearbeiten. Bei jedem Auftreten eines Links im internen HTML-Code wird die folgende Methode aufgerufen:

`rewriteLink(String link, String tag, String attribute)`

Als Eingabe erhält die Methode die folgenden Parameter:

* `link`
Die `String` Darstellung des Links, der derzeit verarbeitet wird. Dies ist normalerweise eine relative URL, die auf die Ressource in der Autoreninstanz verweist.

* `tag`
Der Name des HTML-Elements, das derzeit verarbeitet wird.

* `attribute`
Der genaue Attributname.

Wenn beispielsweise das System &quot;Nach Target exportieren&quot;dieses Element derzeit verarbeitet, können Sie `CSSInclude` Folgendes definieren:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

Der Aufruf der `rewriteLink()` Methode erfolgt mithilfe der folgenden Parameter:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wenn Sie den Dienst erstellen, können Sie Entscheidungen basierend auf der angegebenen Eingabe treffen und dann den Link entsprechend umschreiben.

In unserem Beispiel möchten wir den `/etc.clientlibs` Teil der URL entfernen und die entsprechende externe Domäne hinzufügen. Um die Dinge einfach zu halten, werden wir bedenken, dass wir Zugriff auf einen Ressourcen-Resolver für Ihren Dienst haben, wie in `rewriteLinkExample2`folgenden:

>[!NOTE]
>
>Weitere Informationen zum Abrufen eines Ressourcenauflösers über einen Dienstbenutzer finden Sie unter [Dienstbenutzer in AEM](/help/sites-administering/security-service-users.md).

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>Wenn die oben beschriebene Methode zurückgegeben wird `null`, belässt das System &quot;In Target exportieren&quot;den Link wie gewünscht, einen relativen Link zu einer Ressource.

#### Prioritäten - getPriority {#priorities-getpriority}

Es ist nicht ungewöhnlich, mehrere Dienste zu benötigen, um verschiedene Arten von Erlebnisfragmenten zu berücksichtigen, oder sogar einen generischen Dienst zu haben, der das Externalisieren und Zuordnen aller Erlebnisfragmente verarbeitet. In diesen Fällen kann es zu Konflikten darüber kommen, welcher Dienst verwendet werden soll, sodass AEM die Möglichkeit bietet, **Prioritäten** für verschiedene Dienste festzulegen. Die Prioritäten werden nach folgendem Verfahren festgelegt:

* `getPriority()`

Diese Methode ermöglicht die Verwendung mehrerer Dienste, bei denen die `shouldRewrite()` Methode für dasselbe Erlebnisfragment &quot;true&quot;zurückgibt. Der Dienst, der die höchste Zahl aus seiner `getPriority()`Methode zurückgibt, ist der Dienst, der die Erlebnisfragment-Variation verarbeitet.

Beispielsweise können Sie eine `GenericLinkRewriterProvider` Methode verwenden, die die grundlegende Zuordnung für alle Erlebnisfragmente verarbeitet und wenn die `shouldRewrite()` Methode für alle Erlebnisfragmentvarianten `true` zurückgibt. Für mehrere spezifische Erlebnisfragmente ist möglicherweise eine besondere Behandlung erforderlich. In diesem Fall können Sie also eine Methode bereitstellen, `SpecificLinkRewriterProvider` für die die `shouldRewrite()` Methode nur für einige Erlebnisfragmentvarianten &quot;true&quot;zurückgibt. Um sicherzustellen, dass für die Verarbeitung dieser Erlebnisfragmentvarianten ausgewählt `SpecificLinkRewriterProvider` wird, muss in seiner `getPriority()` Methode eine höhere Zahl zurückgegeben werden als `GenericLinkRewriterProvider.`
