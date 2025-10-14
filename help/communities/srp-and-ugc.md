---
title: SRP und UGC Essentials
description: Speicherressourcenanbieter und Übersicht über benutzergenerierte Inhalte
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8279684f-23dd-4234-bf01-fd2ce74bcb4e
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# SRP und UGC Essentials {#srp-and-ugc-essentials}

## Einführung {#introduction}

Wenn Sie mit dem Speicherressourcenanbieter (SRP) und seiner Beziehung zu benutzergenerierten Inhalten (User-Generated Content, UGC) nicht vertraut sind, besuchen Sie [Community-](working-with-srp.md)) und [Speicherressourcenanbieter - Übersicht](srp.md).

Dieser Abschnitt der Dokumentation enthält einige wichtige Informationen zu SRP und UGC.

## StorageResourceProvider-API {#storageresourceprovider-api}

Die SocialResourceProvider-API (SRP-API) ist eine Erweiterung verschiedener Sling Resource Provider-APIs. Es unterstützt Paginierung und atomare Inkremente (nützlich für Tally und Scoring).

Abfragen sind für SCF-Komponenten erforderlich, da nach Datum, Nützlichkeit, Anzahl der Stimmen usw. sortiert werden muss. Alle SRP-Optionen verfügen über flexible Abfragemechanismen, die nicht auf Bucketing angewiesen sind.

Der SRP-Speicherort enthält den Komponentenpfad. Die SRP-API sollte immer für den Zugriff auf benutzergenerierten Inhalt verwendet werden, da der Stammpfad von der ausgewählten SRP-Option abhängt, z. B. ASRP, MSRP oder JSRP.

Die SRP-API ist keine abstrakte Klasse, sondern eine Schnittstelle. Eine benutzerdefinierte Implementierung sollte nicht auf die leichte Schulter genommen werden, da die Vorteile künftiger Verbesserungen bei internen Implementierungen beim Upgrade auf eine neue Version ausbleiben würden.

Die Mittel für die Verwendung der SRP-API werden durch Dienstprogramme bereitgestellt, wie z. B. die im SocialResourceUtilities-Paket enthaltenen.

Beim Upgrade von AEM 6.0 oder früher ist es erforderlich, UGC für alle SRPs zu migrieren, für die ein Open Source-Tool verfügbar ist. Siehe [Aktualisieren auf AEM Communities 6.3](upgrade.md).

>[!NOTE]
>
>Früher wurden Dienstprogramme für den Zugriff auf UGC im SocialUtils-Paket gefunden, das nicht mehr existiert.
>
>Informationen zu Ersatzdienstprogrammen finden Sie unter [SocialUtils-Refaktorierung](socialutils.md).

## Dienstprogramm-Methode für den Zugriff auf benutzergenerierten Inhalt {#utility-method-to-access-ugc}

Um auf den UGC zuzugreifen, verwenden Sie eine Methode aus dem SocialResourceUtilities-Paket, die einen Pfad zurückgibt, der für den Zugriff auf den UGC aus SRP geeignet ist, und die veraltete Methode im SocialUtils-Paket ersetzt.

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

Weitere Ersetzungen für SocialUtils finden Sie unter [SocialUtils-Umgestaltung](socialutils.md).

Kodierungsrichtlinien finden Sie unter [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>Der von resourceToUGCStoragePath() zurückgegebene Pfad ist *nicht* geeignet für [ACL-Überprüfung](srp.md#for-access-control-acls).

## Dienstprogramm-Methode für den Zugriff auf ACLs {#utility-method-to-access-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Schattenknoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Mithilfe der SRP-API führen alle SRP-Optionen vor allen CRUD-Vorgängen dieselbe Prüfung des Shadow-Speicherorts durch.

Verwenden Sie zum Überprüfen von ACLs eine -Methode, die einen Pfad zurückgibt, der zum Überprüfen der auf den UGC der Ressource angewendeten Berechtigungen geeignet ist.

Im Folgenden finden Sie ein einfaches Beispiel für die Verwendung der resourceToACLPath()-Methode in einem Servlet:

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
>Der von resourceToACLPath() zurückgegebene Pfad ist *nicht* geeignet für den [Zugriff auf den UGC](#utility-method-to-access-acls).

## UGC-bezogene Speicherorte {#ugc-related-storage-locations}

Die folgenden Beschreibungen des Speicherorts können bei der Entwicklung mit JSRP oder MSRP hilfreich sein. Derzeit gibt es keine Benutzeroberfläche für den Zugriff auf in ASRP gespeicherte benutzergenerierte Inhalte, wie z. B. für JSRP ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) und MSRP (MongoDB-Tools).

**Speicherort der Komponente**

Wenn ein Mitglied in der Veröffentlichungsumgebung in den benutzergenerierten Inhalt eingibt, interagiert es mit einer Komponente als Teil einer AEM-Site.

Ein Beispiel für eine solche Komponente ist die Komponente [Kommentare](http://localhost:4502/content/community-components/en/comments.html) die auf der Website [Community-Komponentenhandbuch](components-guide.md) vorhanden ist. Der Pfad zum Kommentarknoten im lokalen Repository lautet:

* Komponentenpfad = `/content/community-components/en/comments/jcr:content/content/includable/comments`

**Speicherort des Schattenknotens**

Beim Erstellen von benutzergenerierten Inhalten wird auch ein [Shadow-Knoten](srp.md#about-shadow-nodes-in-jcr) erstellt, auf den die erforderlichen ACLs angewendet werden. Der Pfad zum entsprechenden Shadow-Knoten im lokalen Repository resultiert aus der Voranstellung des Shadow-Knoten-Stammpfads im Komponentenpfad:

* Stammverzeichnis = `/content/usergenerated`
* Schattenknoten des Kommentars = `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

**UGC-Speicherort**

Der UGC wird an keinem dieser Orte erstellt und sollte nur über eine -Dienstprogrammmethode aufgerufen werden[&#x200B; die &#x200B;](#utility-method-to-access-ugc)-API aufruft.

* Stammverzeichnis = `/content/usergenerated/asi/srp-choice`
* UGC-Knoten für JSRP = `/content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/includable/comments/srzd-let_it_be_`

*Achtung* Bei JSRP ist der UGC-Knoten *nur* in der AEM-Instanz (Author oder Publish) vorhanden, in der er eingegeben wurde. Bei Eingabe in einer Veröffentlichungsinstanz ist die Moderation über die Moderationskonsole in der Autoreninstanz nicht möglich.

## Ergänzende Informationen {#related-information}

* [Speicherressourcenanbieter - Übersicht](srp.md) - Einführung und Repository-Nutzung - Übersicht.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
