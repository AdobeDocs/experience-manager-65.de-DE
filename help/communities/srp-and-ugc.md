---
title: Grundlagen zu SRP und UGC
description: Übersicht über den Speicher-Ressourcenanbieter und den benutzergenerierten Inhalt
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8279684f-23dd-4234-bf01-fd2ce74bcb4e
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Grundlagen zu SRP und UGC {#srp-and-ugc-essentials}

## Einführung {#introduction}

Wenn Sie nicht mit dem Speicher-Ressourcenanbieter (SRP) und dessen Beziehung zu benutzergenerierten Inhalten (UGC) vertraut sind, besuchen Sie [Community-Inhaltsspeicherung](working-with-srp.md) und [Übersicht über den Speicheranbieter](srp.md).

Dieser Abschnitt der Dokumentation enthält einige wichtige Informationen zu SRP und UGC.

## StorageResourceProvider-API {#storageresourceprovider-api}

Die SocialResourceProvider-API (SRP-API) ist eine Erweiterung verschiedener Sling Resource Provider-APIs. Es enthält Unterstützung für Paginierung und atomare Inkrementierung (nützlich für Tally und Scoring).

Abfragen sind für SCF-Komponenten erforderlich, da eine Sortierung nach Datum, Nützlichkeit, Anzahl der Stimmen usw. erforderlich ist. Alle SRP-Optionen verfügen über flexible Abfragemechanismen, die nicht auf Bucketing angewiesen sind.

Der SRP-Speicherort enthält den Komponentenpfad. Die SRP-API sollte immer für den Zugriff auf UGC verwendet werden, da der Stammpfad von der ausgewählten SRP-Option abhängt, z. B. ASRP, MSRP oder JSRP.

Die SRP-API ist keine abstrakte Klasse, sondern eine Schnittstelle. Eine benutzerdefinierte Implementierung sollte nicht so einfach durchgeführt werden, da die Vorteile künftiger Verbesserungen bei internen Implementierungen bei der Aktualisierung auf eine neue Version verpasst werden.

Die Mittel zur Verwendung der SRP-API werden über bereitgestellte Dienstprogramme bereitgestellt, z. B. über die im Paket SocialResourceUtilities vorhandenen.

Bei der Aktualisierung von AEM 6.0 oder früher muss UGC für alle SRP migriert werden, für die ein Open Source-Tool verfügbar ist. Siehe [Upgrade auf AEM Communities 6.3](upgrade.md).

>[!NOTE]
>
>Bisher wurden Dienstprogramme für den Zugriff auf UGC im Paket SocialUtils gefunden, das nicht mehr existiert.
>
>Weitere Informationen zu Ersatzprogrammen finden Sie unter [SocialUtils-Refaktorierung](socialutils.md).

## Dienstprogrammmethode für den Zugriff auf UGC {#utility-method-to-access-ugc}

Verwenden Sie zum Zugreifen auf UGC eine Methode aus dem Paket SocialResourceUtilities , die einen Pfad zurückgibt, der für den Zugriff auf UGC über SRP geeignet ist, und die veraltete Methode im Paket SocialUtils ersetzt.

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

Weitere SocialUtils-Ersetzungen finden Sie unter [SocialUtils-Refaktorierung](socialutils.md).

Informationen zu Richtlinien für die Kodierung finden Sie unter [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>Der Pfad resourceToUGCStoragePath() gibt Folgendes zurück: *not* geeignet für [ACL-Prüfung](srp.md#for-access-control-acls).

## Dienstprogrammmethode für den Zugriff auf ACLs {#utility-method-to-access-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Mithilfe der SRP-API führen alle SRP-Optionen vor allen CRUD-Vorgängen dieselbe Prüfung der Shadow-Position durch.

Um ACLs zu überprüfen, verwenden Sie eine Methode, die einen Pfad zurückgibt, der zum Überprüfen der auf die UGC der Ressource angewendeten Berechtigungen geeignet ist.

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
>Der von resourceToACLPath() zurückgegebene Pfad lautet *not* geeignet für [Zugriff auf die Benutzerkontensteuerung](#utility-method-to-access-acls) selbst.

## UGC-bezogene Speicherorte {#ugc-related-storage-locations}

Die folgenden Beschreibungen des Speicherorts können bei der Entwicklung mit JSRP oder MSRP hilfreich sein. Es gibt derzeit keine Benutzeroberfläche für den Zugriff auf UGC, die in ASRP gespeichert ist, wie dies für JSRP ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) und MSRP (MongoDB-Tools).

**Komponentenstandort**

Wenn ein Mitglied in der Veröffentlichungsumgebung in die benutzergenerierte Inhaltsbibliothek gelangt, interagiert es mit einer Komponente als Teil einer AEM Site.

Ein Beispiel für eine solche Komponente ist die [Kommentarkomponente](http://localhost:4502/content/community-components/en/comments.html) , die in der [Handbuch zu Community-Komponenten](components-guide.md) Site. Der Pfad zum Kommentarknoten im lokalen Repository lautet:

* Komponentenpfad = `/content/community-components/en/comments/jcr:content/content/includable/comments`

**Position des Shadow-Knotens**

Die Erstellung von benutzergenerierten Inhalten erzeugt auch eine [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) auf die die erforderlichen ACLs angewendet werden. Der Pfad zum entsprechenden Shadow-Knoten im lokalen Repository ist das Ergebnis der Vorgabe des Shadow-Knoten-Stammpfads zum Komponentenpfad:

* Stammverzeichnis = `/content/usergenerated`
* Kommentar-Shadow-Knoten = `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

**UGC-Speicherort**

Die UGC wird an keinem dieser Speicherorte erstellt und sollte nur über eine [Dienstprogrammmethode](#utility-method-to-access-ugc) , der die SRP-API aufruft.

* Stammverzeichnis = `/content/usergenerated/asi/srp-choice`
* UGC-Knoten für JSRP = `/content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/includable/comments/srzd-let_it_be_`

*Beachten Sie* für JSRP wird der UGC-Knoten *only* in der AEM-Instanz (Autor oder Veröffentlichungsinstanz) vorhanden sein, in der sie eingegeben wurde. Bei Eingabe in eine Veröffentlichungsinstanz ist eine Moderation in der Moderationskonsole auf der Autoreninstanz nicht möglich.

## Verwandte Informationen {#related-information}

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Kodierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
