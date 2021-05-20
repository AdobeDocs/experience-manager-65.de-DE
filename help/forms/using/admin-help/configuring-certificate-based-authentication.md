---
title: Zertifikatbasierte Authentifizierung konfigurieren
seo-title: Zertifikatbasierte Authentifizierung konfigurieren
description: Importieren Sie eine Zertifizierungsstelle (Certificate Authority, CA) in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung für zertifikatbasierte Authentifizierung.
seo-description: Importieren Sie eine Zertifizierungsstelle (Certificate Authority, CA) in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung für zertifikatbasierte Authentifizierung.
uuid: 9802a969-6d29-4b80-a4ed-06eb6e66e046
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d958ae65-3008-4d68-9e11-4346e149827f
exl-id: 9cbea8c8-4d42-446b-b98d-c090709624d7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 94%

---

# Zertifikatbasierte Authentifizierung konfigurieren {#configuring-certificate-based-authentication}

User Management führt in der Regel die Authentifizierung mithilfe eines Benutzernamens und eines Kennworts aus. User Management unterstützt auch die zertifikatbasierte Authentifizierung, die Sie zum Authentifizieren von Benutzern über Acrobat oder zum programmgesteuerten Authentifizieren von Benutzern verwenden können. Ausführliche Informationen zum programmgesteuerten Authentifizieren von Benutzern finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).

Zum Verwenden der zertifikatbasierten Authentifizierung importieren Sie eine Zertifizierungsstelle (Certificate Authority, CA), der Sie vertrauen, in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung.

## CA-Zertifikat importieren {#import-the-ca-certificate}

Wählen Sie beim Importieren des Zertifikats die Optionen „Trust für Zertifikatauthentifizierung“ und „Trust für Identität“ sowie weitere erforderliche Optionen aus. Einzelheiten zum Importieren von Zertifikaten finden Sie unter [Zertifikate verwalten](/help/forms/using/admin-help/certificates.md#managing-certificates).

## Zertifikatzuordnung konfigurieren  {#configuring-certificate-mapping}

Um die zertifikatbasierte Authentifizierung für Benutzer zu aktivieren, erstellen Sie eine Zertifikatzuordnung. Eine *Zertifikatzuordnung* definiert eine Zuordnung zwischen den Attributen eines Zertifikats und den Attributen von Benutzern in einer Domäne. Sie können derselben Domäne mehr als ein Zertifikat zuordnen.

Wenn Sie ein Zertifikat testen, lädt User Management die Zertifikatüberprüfungen, um sicherzustellen, dass das Zertifikat die folgenden Voraussetzungen erfüllt:

* Das Zertifikat ist gültig.
* Der von Ihnen angegebene Herausgeber kann das Zertifikat überprüfen.
* Das Zertifikat enthält das für die Zuordnung erforderliche Attribut.
* Die von Ihnen angegebene Zuordnung ordnet das Zertifikat nur einem Benutzer in der AEM Forms-Datenbank zu. Sowohl aktuelle als auch veraltete (gelöschte) Benutzer werden überprüft, um zu bestimmen, ob sie den Zuordnungskriterien entsprechen. Daher schlägt der Zertifikattest fehl, wenn mehr als ein Benutzer, einschließlich veralteter Benutzer, über den entsprechenden Attributwert verfügen.

>[!NOTE]
>
>Sie können eine vorhandene Zertifikatzuordnung nicht bearbeiten.

**Zertifikatzuordnung hinzufügen**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Zertifikatzuordnung“.
1. Klicken Sie auf „Neue Zertifikatzuordnung“ und wählen Sie in der Liste „Für Herausgeber“ den in der Trust Store-Verwaltung konfigurierten Zertifikatalias aus.
1. Weisen Sie eines der Zertifikatattribute einem Benutzerattribut zu. Sie können beispielsweise den allgemeinen Namen des Zertifikats der Anmelde-ID des Benutzers zuordnen.

   Wenn sich der Inhalt des Attributs im Zertifikat von dem Inhalt des Benutzerattributs in der User Management-Datenbank unterscheidet, können Sie einen regulären Java-Ausdruck (Java Regular Expression, regex) verwenden, der mit den beiden Attributen übereinstimmen soll. Wenn beispielsweise die allgemeinen Namen der Zertifikate in etwa *Alex Pink (Authentifizierung)* und *Alex Pink (Signieren)* lauten und der allgemeine Name in der User Management-Datenbank *Alex Pink* lautet, sollten Sie einen Regex verwenden, um den erforderlichen Teil des Zertifikatattributs (in diesem Beispiel *Alex Pink* zu extrahieren.) Der von Ihnen angegebene reguläre Ausdruck muss mit der Java-Regex-Spezifikation übereinstimmen.

   Sie können den Ausdruck transformieren, indem Sie im Feld „Benutzerdefinierte Reihenfolge“ die Reihenfolge der Gruppen angeben. Die benutzerdefinierte Reihenfolge wird mit der `java.util.regex.Matcher.replaceAll()`-Methode verwendet. Das Verhalten entspricht dem Verhalten der Methode und die Eingabezeichenfolge (die benutzerdefinierte Reihenfolge) muss entsprechend angegeben werden.

   Um den Regex zu testen, geben Sie einen Wert in das Feld „Parameter testen“ ein und klicken Sie auf „Testen“.

   Sie können folgende Zeichen in dem Regex verwenden:

   * . (alle Zeichen)
   * &amp;ast; (0 oder mehr Vorkommen)
   * () (Geben Sie die Gruppe in Klammern an)
   * \ (Wird verwendet, um ein Regex-Zeichen durch ein reguläres Zeichen zu ersetzen)
   * $n (Wird verwendet, um auf die n-te Gruppe zu verweisen)

   Beispiele regulärer Ausdrücke:

   * So extrahieren Sie „Alex Pink“ aus „Alex Pink (Authentifizierung)“

      **Regex:** (.&amp;ast;) \(Authentifizierung\)

   * So extrahieren Sie „Alex Pink“ aus „Alex (Authentifizierung) Pink“

      **Regex:** (.&amp;ast;)\(Authentifizierung\) (.&amp;ast;)

   * So extrahieren Sie „Pink Alex“ aus „Alex (Authentifizierung) Pink“

      **Regex:** (.&amp;ast;)\(Authentifizierung\) (.&amp;ast;)

      Benutzerdefinierte Reihenfolge: 2 $1 (zweite Gruppe zurückgeben, verkettet mit der ersten Gruppe, erfasst durch Leerzeichen)

   * So extrahieren Sie „apink@sampleorg.com“ aus „smtp:apink@sampleorg.com“

      **Regex:** smtp:(.&amp;ast;)
   Einzelheiten zur Verwendung regulärer Ausdrücke finden Sie im [Java-Tutorium zu regulären Ausdrücken](https://java.sun.com/docs/books/tutorial/essential/regex/).

1. Wählen Sie im Feld „Für Domäne“ die Domäne des Benutzers aus.
1. Um diese Konfiguration zu testen, klicken Sie auf „Durchsuchen“, um ein Beispielbenutzerzertifikat hochzuladen, und klicken dann auf „Zertifikat testen“. Wenn die Konfiguration ordnungsgemäß ist, klicken Sie auf „OK“.

**Vorhandene Zertifikatzuordnung bearbeiten**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“.
1. Klicken Sie auf „Zertifikatzuordnung“.
1. Wählen Sie die zu bearbeitende Zertifikatzuordnung aus und bearbeiten Sie deren Konfiguration. Sie können den regulären Ausdruck und die benutzerdefinierte Reihenfolge aktualisieren.
1. Um die Änderungen zu testen, klicken Sie auf „Durchsuchen“, um ein Beispielzertifikat hochzuladen, klicken Sie dann auf „Zertifikat testen“ und anschließend auf „OK“.

**Zertifikatzuordnung löschen**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Zertifikatzuordnung“.
1. Aktivieren Sie das Kontrollkästchen der zu löschenden Zertifikatzuordnung und klicken Sie auf „Löschen“ und anschließend auf „OK“.
