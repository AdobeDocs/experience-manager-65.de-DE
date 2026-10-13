---
title: Konfigurieren einer zertifikatbasierten Authentifizierung
description: Importieren Sie eine Zertifizierungsstelle (ZS) in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung zur zertifikatbasierten Authentifizierung.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 9cbea8c8-4d42-446b-b98d-c090709624d7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 88%
---
# Konfigurieren einer zertifikatbasierten Authentifizierung {#configuring-certificate-based-authentication}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Die Benutzerverwaltung führt die Authentifizierung in der Regel mithilfe eines Benutzernamens und Kennworts durch. Die Benutzerverwaltung unterstützt auch die zertifikatbasierte Authentifizierung, die Sie zum Authentifizieren von Benutzenden über Acrobat oder zum programmgesteuerten Authentifizieren von Benutzenden verwenden können. Weitere Informationen zum programmgesteuerten Authentifizieren von Benutzenden finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).

Zur zertifikatbasierten Authentifizierung importieren Sie eine Zertifizierungsstelle (CA), der Sie vertrauen, in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung.

## Importieren des CA-Zertifikats {#import-the-ca-certificate}

Wählen Sie beim Importieren des Zertifikats die Optionen „Trust für Zertifikatauthentifizierung“ und „Trust für Identität“ sowie weitere erforderliche Optionen aus. Weitere Informationen zum Importieren von Zertifikaten finden Sie unter [Verwalten von Zertifikaten](/help/forms/using/admin-help/certificates.md#managing-certificates).

## Konfigurieren der Zertifikatzuordnung {#configuring-certificate-mapping}

Um die zertifikatbasierte Authentifizierung für Benutzende zu aktivieren, erstellen Sie eine Zertifikatzuordnung. Eine *Zertifikatzuordnung* definiert eine Zuordnung zwischen den Attributen eines Zertifikats und den Attributen von Benutzern in einer Domain. Sie können derselben Domain mehr als ein Zertifikat zuordnen.

Wenn Sie ein Zertifikat testen, lädt die Benutzerverwaltung die Zertifikatüberprüfungen, um sicherzustellen, dass das Zertifikat die folgenden Voraussetzungen erfüllt:

* Das Zertifikat ist gültig.
* Die von Ihnen angegebene herausgebende Stelle kann das Zertifikat überprüfen.
* Das Zertifikat enthält das für die Zuordnung erforderliche Attribut.
* Die von Ihnen angegebene Zuordnung ordnet das Zertifikat nur einer Person in der AEM Forms-Datenbank zu. Sowohl aktuelle als auch veraltete (gelöschte) Benutzende werden überprüft, um zu bestimmen, ob sie den Zuordnungskriterien entsprechen. Daher schlägt der Zertifikattest fehl, wenn mehr als eine Person, einschließlich veralteter Benutzender, über den entsprechenden Attributwert verfügen.

>[!NOTE]
>
>Sie können eine vorhandene Zertifikatzuordnung nicht bearbeiten.

**Hinzufügen einer Zertifikatzuordnung**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Zertifikatzuordnung“.
1. Klicken Sie auf „Neue Zertifikatzuordnung“ und wählen Sie in der Liste „Für Herausgeber“ den in der Trust Store-Verwaltung konfigurierten Zertifikatalias aus.
1. Weisen Sie eines der Zertifikatattribute einem Benutzerattribut zu. Sie können beispielsweise den allgemeinen Namen des Zertifikats der Anmelde-ID der Person zuordnen.

   Wenn sich der Inhalt des Attributs im Zertifikat von dem Inhalt des Benutzerattributs in der Benutzerverwaltungsdatenbank unterscheidet, können Sie einen regulären Java-Ausdruck (Java Regular Expression, Regex) verwenden, um die beiden Attribute abzustimmen. Wenn beispielsweise die allgemeinen Namen der Zertifikate Namen wie *Alex Pink (Authentifizierung)* und *Alex Pink (Signierung)* sind und der allgemeine Name in der User Management-Datenbank *Alex Pink* lautet, verwenden Sie einen Regex, um den erforderlichen Teil des Zertifikatattributs zu extrahieren (in diesem Beispiel *Alex Pink*.) Der von Ihnen angegebene reguläre Ausdruck muss der Java-Regex-Spezifikation entsprechen.

   Sie können den Ausdruck transformieren, indem Sie im Feld „Benutzerdefinierte Reihenfolge“ die Reihenfolge der Gruppen angeben. Die benutzerdefinierte Reihenfolge wird mit der Methode `java.util.regex.Matcher.replaceAll()` verwendet. Das Verhalten entspricht dem Verhalten der Methode, und die Eingabezeichenfolge (die benutzerdefinierte Reihenfolge) muss entsprechend angegeben werden.

   Um den regulären Ausdruck zu testen, geben Sie einen Wert in das Feld „Testparameter“ ein und klicken Sie auf „Testen“.

   Sie können folgende Zeichen in dem regulären Ausdruck verwenden:

   * . (alle Zeichen)
   * &ast; (0 oder mehr Vorkommen)
   * () (die Gruppe in Klammern angeben)
   * \ (wird verwendet, um aus einem Regex-Zeichen ein reguläres Zeichen zu machen)
   * $n (wird verwendet, um auf die n-te Gruppe zu verweisen)

   Beispiele regulärer Ausdrücke:

   * So extrahieren Sie „Alex Pink“ aus „Alex Pink (Authentifizierung)“:

     **Regex:** (.&ast;) \(Authentifizierung\)

   * So extrahieren Sie „Alex Pink“ aus „Alex (Authentifizierung) Pink“:

     **Regex:** (.&ast;)\(Authentication\) (.&ast;)

   * So extrahieren Sie „Pink Alex“ aus „Alex (Authentifizierung) Pink“:

     **Regex:** (.&ast;)\(Authentication\) (.&ast;)

     Benutzerdefinierte Reihenfolge: $2 $1 (zweite Gruppe zurückgeben, verkettet mit der ersten Gruppe, erfasst durch Leerzeichen)

   * So extrahieren Sie &quot;apink@sampleorg.com&quot; aus „smtp:apink@sampleorg.com“

     **Regex:** smtp:(.&ast;)

   Weitere Informationen zur Verwendung regulärer Ausdrücke finden Sie im [Java-Tutorial zu regulären Ausdrücken](https://java.sun.com/docs/books/tutorial/essential/regex/).

1. Wählen Sie im Feld „Für Domain“ die Domain des Benutzers aus.
1. Um diese Konfiguration zu testen, klicken Sie auf „Durchsuchen“ und laden Sie ein Beispielbenutzerzertifikat hoch. Klicken Sie dann auf „Zertifikat testen“. Ist die Konfiguration korrekt, klicken Sie auf „OK“.

**Bearbeiten einer vorhandenen Zertifikatzuordnung**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“.
1. Klicken Sie auf „Zertifikatzuordnung“.
1. Wählen Sie die zu bearbeitende Zertifikatzuordnung aus und bearbeiten Sie die zugehörige Konfiguration. Sie können den regulären Ausdruck und die benutzerdefinierte Reihenfolge aktualisieren.
1. Um die Änderungen zu testen, klicken Sie auf „Durchsuchen“ und laden Sie ein Beispielzertifikat hoch. Klicken Sie dann auf „Zertifikat testen“ und anschließend auf „OK“

**Löschen einer Zertifikatzuordnung**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Zertifikatzuordnung“.
1. Aktivieren Sie das Kontrollkästchen der zu löschenden Zertifikatzuordnung. Klicken Sie dann auf „Löschen“ und anschließend auf „OK“.
