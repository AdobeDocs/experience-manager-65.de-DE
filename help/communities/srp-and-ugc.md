---
title: SRP und UGC Essentials
seo-title: SRP und UGC Essentials
description: Übersicht über Speicherressourcenanbieter und vom Benutzer erstellte Inhalte
seo-description: Übersicht über Speicherressourcenanbieter und vom Benutzer erstellte Inhalte
uuid: a4ee8725-f554-4fcf-ac1e-34878d6c02f8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0763f236-5648-49e9-8a24-dbc8f4c77ee3
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# SRP und UGC Essentials {#srp-and-ugc-essentials}

## Einführung {#introduction}

Wenn Sie mit dem Speicherressourcenanbieter (SRP) und seiner Beziehung zu benutzergenerierten Inhalten (UGC) nicht vertraut sind, besuchen Sie die [Community Content Storage](working-with-srp.md) - und [Storage Resource Provider-Übersicht](srp.md).

Dieser Abschnitt der Dokumentation enthält einige wichtige Informationen zu SRP und UGC.

## StorageResourceProvider-API {#storageresourceprovider-api}

Die SocialResourceProvider-API (SRP-API) ist eine Erweiterung verschiedener Sling Resource Provider-APIs. Es umfasst Unterstützung für Paginierung und atomare Inkrementierung (nützlich für Tally und Scoring).

Abfragen sind für SCF-Komponenten erforderlich, da eine Sortierung nach Datum, Hilfsbereitschaft, Anzahl der Stimmen usw. erforderlich ist. Alle SRP-Optionen verfügen über flexible Abfragemechanismen, die sich nicht auf das Bucketing verlassen.

Der SRP-Speicherort enthält den Komponentenpfad. Die SRP-API sollte immer für den Zugriff auf UGC verwendet werden, da der Stammpfad von der ausgewählten SRP-Option wie ASRP, MSRP oder JSRP abhängt.

Die SRP-API ist keine abstrakte Klasse, sondern eine Schnittstelle. Eine benutzerdefinierte Implementierung sollte nicht so leicht durchgeführt werden, da die Vorteile künftiger Verbesserungen an internen Implementierungen bei der Aktualisierung auf eine neue Version verpasst würden.

Die Mittel zur Verwendung der SRP-API werden über bereitgestellte Hilfsprogramme bereitgestellt, z. B. im Paket SocialResourceUtilities.

Beim Aktualisieren von AEM 6.0 oder früher müssen Sie UGC für alle SRP migrieren, für die ein Open-Source-Tool verfügbar ist. See [Upgrading to AEM Communities 6.3](upgrade.md).

>[!NOTE]
>
>Bisher wurden Hilfsprogramme für den Zugriff auf UGC im Paket SocialUtils gefunden, das nicht mehr existiert.
>
>Ersatzdienstprogramme finden Sie unter [SocialUtils Refactoring](socialutils.md).

## Dienstprogrammmethode für den Zugriff auf UGC {#utility-method-to-access-ugc}

Um auf UGC zuzugreifen, verwenden Sie eine Methode aus dem SocialResourceUtilities-Paket, die einen Pfad zurückgibt, der für den Zugriff auf UGC über SRP geeignet ist, und die veraltete Methode ersetzt, die im SocialUtils-Paket gefunden wird.

Im Folgenden finden Sie ein minimales Beispiel für die Verwendung der Methode resourceToUGCStoragePath() in einem Servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String ugcPath = socialResourceUtilities.resourceToUGCStoragePath(request.getResource());
  // rest of servlet
}
```

Weitere SocialUtils-Ersetzungen finden Sie unter [SocialUtils-Umgestaltung](socialutils.md).

Richtlinien zum Kodieren finden Sie unter [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>Der Pfad resourceToUGCStoragePath() gibt *nicht *geeignet für die [ACL-Überprüfung](srp.md#for-access-control-acls)zurück.

## Dienstprogrammmethode für den Zugriff auf ACLs {#utility-method-to-access-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Überprüfung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Bei Verwendung der SRP-API werden alle SRP-Optionen vor allen CRUD-Vorgängen an der Position des Schattens überprüft.

Um ACLs zu überprüfen, verwenden Sie eine Methode, die einen Pfad zurückgibt, der geeignet ist, die Berechtigungen zu überprüfen, die auf das UGC der Ressource angewendet wurden.

Im Folgenden finden Sie ein einfaches Beispiel für die Verwendung der Methode resourceToACLPath() in einem Servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String aclPath = socialResourceUtilities.resourceToACLPath(request.getResource());
  // rest of servlet
}
```

>[!CAUTION]
>
>Der von resourceToACLPath() zurückgegebene Pfad ist *nicht *geeignet für den [Zugriff auf die UGC](#utility-method-to-access-acls) selbst.

## UGC-bezogene Speicherorte {#ugc-related-storage-locations}

Die folgenden Beschreibungen des Speicherorts können bei der Entwicklung mit JSRP oder MSRP hilfreich sein. Es gibt derzeit keine Benutzeroberfläche für den Zugriff auf UGC, die in ASRP gespeichert ist, wie es für JSRP ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) und MSRP (MongoDB-Werkzeuge) gibt.

**Komponentenposition**

Wenn ein Mitglied in der Veröffentlichungsumgebung in das UGC gelangt, interagiert es mit einer Komponente als Teil einer AEM-Site.

Ein Beispiel für eine solche Komponente ist die [Kommentarkomponente](http://localhost:4502/content/community-components/en/comments.html) , die auf der Website &quot; [Community-Komponenten-Handbuch](components-guide.md) &quot;vorhanden ist. Der Pfad zum Kommentarknoten im lokalen Repository lautet:

* Komponentenpfad = */content/community-components/de/comments/jcr:content/content/einschließlich/comments*

**Speicherort des Schatten-Knotens**

Bei der Erstellung von UGC wird auch ein [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) erstellt, auf den die erforderlichen ACLs angewendet werden. Der Pfad zum entsprechenden Shadow-Knoten im lokalen Repository ist das Ergebnis, wenn der Shadow-Knoten-Stammpfad dem Komponentenpfad vorangestellt wird:

* Stammpfad = /content/usergenerated
* Kommentarschattenknoten = /content/usergenerated/content/community-components/de/comments/jcr:content/content/einschließlich/comments

**UGC-Speicherort**

Die UGC wird an keinem dieser Orte erstellt und sollte nur mit einer [Dienstprogrammmethode](#utility-method-to-access-ugc) aufgerufen werden, die die SRP-API aufruft.

* Stammpfad = /content/usergenerated/asi/srp-choice
* UGC-Knoten für JSRP = /content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/einschließlich/comments/srzd-let_it_be_

*Beachten Sie*, dass der UGC-Knoten für JSRP *nur* auf der AEM-Instanz vorhanden ist (entweder Autor oder Veröffentlichung), auf der er eingegeben wurde. Bei der Eingabe in eine Veröffentlichungsinstanz ist eine Moderation in der Moderationskonsole beim Autor nicht möglich.

## Verwandte Informationen {#related-information}

* [Übersicht über](srp.md) den Speicherressourcen-Provider - Einführung und Übersicht über die Repository-Nutzung
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Richtlinien zum Kodieren
* [SocialUtils Refactoring](socialutils.md) - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

