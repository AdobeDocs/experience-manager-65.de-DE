---
title: Konfigurieren einer zertifikatbasierten Authentifizierung
description: Importieren Sie ein Zertifikat der Zertifizierungsstelle (Certificate Authority, CA) in den Trust Store und erstellen Sie eine Zertifikatzuordnung für die zertifikatbasierte Authentifizierung.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 9cbea8c8-4d42-446b-b98d-c090709624d7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 10%

---

# Konfigurieren einer zertifikatbasierten Authentifizierung {#configuring-certificate-based-authentication}

Die Benutzerverwaltung führt die Authentifizierung in der Regel mithilfe eines Benutzernamens und Kennworts durch. User Management unterstützt auch die zertifikatbasierte Authentifizierung, mit der Sie Benutzer über Acrobat authentifizieren oder Benutzer programmgesteuert authentifizieren können. Weitere Informationen zum programmgesteuerten Authentifizieren von Benutzern finden Sie unter [Programmieren mit AEM](https://www.adobe.com/go/learn_aemforms_programming_63_de).

Um die zertifikatbasierte Authentifizierung zu verwenden, importieren Sie ein Zertifikat der Zertifizierungsstelle (Certificate Authority, CA), dem Sie vertrauen, in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung.

## CA-Zertifikat importieren {#import-the-ca-certificate}

Wählen Sie beim Importieren des Zertifikats die Optionen Trust für Zertifikatauthentifizierung und Trust für Identität sowie alle anderen erforderlichen Optionen aus. Weitere Informationen zum Importieren von Zertifikaten finden Sie unter [Zertifikate verwalten](/help/forms/using/admin-help/certificates.md#managing-certificates).

## Zertifikatzuordnung konfigurieren {#configuring-certificate-mapping}

Um die zertifikatbasierte Authentifizierung für Benutzer zu aktivieren, erstellen Sie eine Zertifikatzuordnung. Eine *Zertifikatzuordnung* definiert eine Zuordnung zwischen den Attributen eines Zertifikats und den Attributen von Benutzern in einer Domain. Sie können derselben Domain mehr als ein Zertifikat zuordnen.

Beim Testen eines Zertifikats lädt User Management die Zertifikatprüfungen hoch, um sicherzustellen, dass es die folgenden Anforderungen erfüllt:

* Das Zertifikat ist gültig.
* Der von Ihnen angegebene Aussteller kann das Zertifikat überprüfen.
* Das Zertifikat enthält das für die Zuordnung erforderliche Attribut.
* Die von Ihnen angegebene Zuordnung ordnet das Zertifikat nur einem Benutzer in der AEM Formulardatenbank zu. Sowohl aktuelle als auch veraltete (gelöschte) Benutzer werden überprüft, um festzustellen, ob sie den Zuordnungskriterien entsprechen. Daher schlägt der Zertifikattest fehl, wenn mehr als ein Benutzer, einschließlich veralteter Benutzer, den Attributwert berücksichtigt.

>[!NOTE]
>
>Sie können eine vorhandene Zertifikatzuordnung nicht bearbeiten.

**Zertifikatzuordnung hinzufügen**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Zertifikatzuordnung&quot;.
1. Klicken Sie auf &quot;Neue Zertifikatzuordnung&quot;und wählen Sie in der Liste &quot;Für Aussteller&quot;den Zertifikatalias aus, der in der Trust Store-Verwaltung konfiguriert wurde.
1. Ordnen Sie eines der Attribute des Zertifikats dem -Attribut eines Benutzers zu. Sie können beispielsweise den allgemeinen Namen des Zertifikats der Anmelde-ID des Benutzers zuordnen.

   Wenn der Inhalt des Attributs im Zertifikat sich vom Inhalt des Benutzerattributs in der User Management-Datenbank unterscheidet, können Sie einen regulären Java-Ausdruck (Regex) verwenden, der mit den beiden Attributen übereinstimmt. Wenn die allgemeinen Namen der Zertifikate beispielsweise Namen wie *Alex Pink (Authentifizierung)* und *Alex Pink (Signing)* und der allgemeine Name in der User Management-Datenbank lautet *Alex Pink* verwenden Sie einen Regex, um den erforderlichen Teil des Zertifikatattributs zu extrahieren (in diesem Beispiel: *Alex Pink*. Der von Ihnen angegebene reguläre Ausdruck muss der Java-Regex-Spezifikation entsprechen.

   Sie können den Ausdruck transformieren, indem Sie die Reihenfolge der Gruppen im Feld &quot;Benutzerdefinierte Reihenfolge&quot;angeben. Die benutzerdefinierte Reihenfolge wird mit der Methode `java.util.regex.Matcher.replaceAll()` verwendet. Das angezeigte Verhalten entspricht dem Verhalten dieser Methode, und die Eingabezeichenfolge (die benutzerdefinierte Reihenfolge) muss entsprechend angegeben werden.

   Geben Sie zum Testen des Regex einen Wert in das Feld &quot;Testparameter&quot;ein und klicken Sie auf &quot;Testen&quot;.

   Sie können die folgenden Zeichen im Regex verwenden:

   * . (beliebiges Zeichen)
   * &amp;ast; (0 oder mehr Vorkommen)
   * () (geben Sie die Gruppe in Klammern an)
   * \ (wird verwendet, um ein Regex-Zeichen in ein reguläres Zeichen zu Escape durchzuführen)
   * $n (wird verwendet, um auf die n-te Gruppe zu verweisen)

   Beispiele für reguläre Ausdrücke:

   * So extrahieren Sie &quot;Alex Pink&quot;aus &quot;Alex Pink (Authentifizierung)&quot;

     **Regex:** (.&amp;ast;) \(Authentifizierung\)

   * So extrahieren Sie &quot;Alex Pink&quot;aus &quot;Alex (Authentifizierung) Pink&quot;

     **Regex:** (.&amp;ast;)\(Authentifizierung\) (.&amp;ast;)

   * So extrahieren Sie &quot;Pink Alex&quot;aus &quot;Alex (Authentication) Pink&quot;

     **Regex:** (.&amp;ast;)\(Authentifizierung\) (.&amp;ast;)

     Benutzerdefinierte Reihenfolge: 2 USD 1 (zweite Gruppe zurückgeben, mit der ersten Gruppe verkettet, die durch Leerzeichen erfasst wird)

   * So extrahieren Sie &quot;apink@sampleorg.com&quot;aus &quot;smtp:apink@sampleorg.com&quot;

     **Regex:** smtp:(.&amp;ast;)

   Weitere Informationen zur Verwendung regulärer Ausdrücke finden Sie unter [Java-Tutorial zu regulären Ausdrücken](https://java.sun.com/docs/books/tutorial/essential/regex/).

1. Wählen Sie im Feld „Für Domain“ die Domain des Benutzers aus.
1. Um diese Konfiguration zu testen, klicken Sie auf Durchsuchen , um ein Beispielbenutzerzertifikat hochzuladen, auf Zertifikat testen und, falls die Konfiguration korrekt ist, auf OK.

**Vorhandene Zertifikatzuordnung bearbeiten**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;.
1. Klicken Sie auf Zertifikatzuordnung.
1. Wählen Sie die Zertifikatzuordnung aus, um die Konfiguration zu bearbeiten und zu bearbeiten. Sie können den regulären Ausdruck und die benutzerdefinierte Reihenfolge aktualisieren.
1. Um Ihre Änderungen zu testen, klicken Sie auf &quot;Durchsuchen&quot;, um ein Beispielzertifikat hochzuladen, klicken auf &quot;Zertifikat testen&quot;und anschließend auf &quot;OK&quot;.

**Zertifikatzuordnung löschen**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Zertifikatzuordnung&quot;.
1. Aktivieren Sie das Kontrollkästchen für die zu löschende Zertifikatzuordnung und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.
