---
title: Was ist Document Security?
description: Erfahren Sie, wie Sie mit Document Security vordefinierte Vertraulichkeitseinstellungen mühelos erstellen, speichern und auf Dokumente anwenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Document Security
exl-id: 0cdc9ee3-0172-43be-9b62-ed768534c074
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '3219'
ht-degree: 100%

---

# Informationen zur Dokumentensicherheit {#about-document-security}

Document Security stellt sicher, dass nur autorisierte Benutzerinnen und Benutzer Ihre Dokumente verwenden können. Mithilfe von Document Security können Sie Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher verteilen. Unterstützte Dateiformate:

* Adobe PDF-Dateien
* Microsoft® Word-, Excel- und PowerPoint-Dateien

Weitere Informationen zum Schutz unterstützter Dokumenttypen durch Richtlinien finden Sie unter [Zusätzliche Informationen zu Document Security](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-security/document-security-offerings.html?lang=de).

Mit Document Security können Sie vordefinierte Vertraulichkeitseinstellungen einfach erstellen, speichern und auf Ihre Dokumente anwenden. Um zu verhindern, dass Informationen über Ihren Einflussbereich hinaus verbreitet werden, können Sie auch überwachen und kontrollieren, wie die Empfängerinnen und Empfänger Ihre Dokumente verwenden, nachdem Sie sie verteilt haben.

Sie können Dokumente mithilfe von Richtlinien schützen. Eine *Richtlinie* ist eine Sammlung von Informationen, die Vertraulichkeitseinstellungen und eine Liste autorisierter Personen umfasst. Die Vertraulichkeitseinstellungen, die Sie in einer Richtlinie angeben, bestimmen, wie ein Dokument, auf das Sie die Richtlinie anwenden, genutzt werden darf. Sie können beispielsweise angeben, ob Empfängerinnen und Empfänger Text drucken oder kopieren, Text bearbeiten oder geschützten Dokumenten Signaturen und Kommentare hinzufügen können.

Benutzerinnen und Benutzer von Document Security erstellen Richtlinien über die Endbenutzer-Web-Seiten. Admins verwenden die Document Security-Web-Seiten, um Richtliniensätze mit gemeinsam genutzten Richtlinien zu erstellen, die für alle autorisierten Benutzerinnen und Benutzer verfügbar sind.

Richtlinien werden zwar in Document Security gespeichert, werden jedoch von Ihnen über Ihre Client-Anwendung auf Dokumente angewendet. Wie Richtlinien auf PDF-Dokumente angewendet werden, wird ausführlich in der *Acrobat-Hilfe* beschrieben. Das Anwenden von Richtlinien durch andere Anwendungen wie Microsoft® Office wird in der *Acrobat Reader DC Extensions-Hilfe* zur jeweiligen Anwendung behandelt.

Wenn Sie eine Richtlinie auf ein Dokument anwenden, schützen die in der Richtlinie angegebenen Vertraulichkeitseinstellungen die Informationen, die das Dokument enthält. Die Vertraulichkeitseinstellungen schützen auch alle Dateien (Text, Audio oder Video) innerhalb eines PDF-Dokuments. Sie können das richtliniengeschützte Dokument an Empfängerinnen und Empfänger verteilen, die durch die Richtlinie autorisiert sind.

**Zugriffskontrolle und Auditing von Dokumenten**

Durch das Schützen eines Dokuments mit einer Richtlinie behalten Sie die Kontrolle über das Dokument, auch nachdem es verteilt wurde. Sie können das Dokument überwachen, die Richtlinie ändern, Benutzende daran hindern, weiterhin auf das Dokument zuzugreifen, und die Richtlinie wechseln, die auf das Dokument angewendet wird.

Über Document Security können Sie richtliniengeschützte Dokumente überwachen und Ereignisse nachverfolgen, z. B. wenn eine autorisierte oder nicht autorisierte Person versucht, das Dokument zu öffnen.

**Komponenten**

Document Security besteht aus einem Server und einer Benutzeroberfläche:

**Server:** Der Server ist die zentrale Komponente, über die Document Security Transaktionen wie z. B. die Authentifizierung von Benutzern, die Richtlinienverwaltung in Echtzeit und das Durchsetzen der Vertraulichkeit ausführt. Der Server stellt außerdem ein zentrales Repository für Richtlinien, Auditdatensätze und andere zugehörige Informationen bereit.

**Web-Seiten:** Die Benutzeroberfläche, auf der Sie Richtlinien erstellen, richtliniengeschützte Dokumente verwalten und Ereignisse im Zusammenhang mit richtliniengeschützten Dokumenten überwachen. Admins können auch globale Optionen wie Benutzerauthentifizierung, Auditing und Messaging für eingeladene Benutzende konfigurieren und Konten eingeladener Benutzender verwalten.

![rm_psworkflow](assets/rm_psworkflow.png)

Die Abbildung zeigt die folgenden Schritte:

1. Die für das Dokument verantwortliche Person erstellt Richtlinien mithilfe der Web-Seiten. Dokumentverantwortliche können persönliche Richtlinien erstellen, auf die nur sie zugreifen dürfen. Admins und Richtliniensatzkoordinatorinnen bzw. -koordinatoren können innerhalb von Richtliniensätzen freigegebene Richtlinien erstellen, auf die autorisierte Benutzende zugreifen können.
1. Die Dokumentverantwortlichen wenden die Richtlinie an, speichern das Dokument und verteilen es. Das Dokument kann per E-Mail, über einen Netzwerkordner oder über eine Website verteilt werden.
1. Die Empfängerin bzw. der Empfänger öffnet das Dokument in der entsprechenden Client-Anwendung. und kann es gemäß der dafür geltenden Richtlinie verwenden.
1. Dokumentverantwortliche, Richtliniensatzkoordinatoren oder Admins können Dokumente nachverfolgen und den Zugriff darauf über die Web-Seiten ändern.

## Informationen zu Document Security-Benutzenden {#about-document-security-users}

Verschiedene Typen von Benutzenden arbeiten mit Document Security, um verschiedene Aufgaben auszuführen:

* Systemadmins oder andere IT-Personen installieren und konfigurieren Document Security. Diese Person kann auch für die Konfiguration globaler Einstellungen für den Server, die Web-Seiten sowie Richtlinien und Dokumente verantwortlich sein.

  Zu diesen Einstellungen können beispielsweise eine Document Security-URL, Auditing- und Datenschutzbenachrichtigungen, Registrierungshinweise für eingeladene Benutzende und die standardmäßige Offline-Nutzungsdauer gehören.

* Document Security-Admins erstellen Richtlinien und Richtliniensätze, und sie verwalten nach Bedarf richtliniengeschützte Dokumente für Benutzende. Sie erstellen auch Konten eingeladener Benutzender und überwachen System-, Dokument-, Benutzer-, Richtlinien-, Richtliniensatz- und benutzerdefinierte Ereignisse. Möglicherweise sind sie auch zusammen mit Systemadmins für die Konfiguration des globalen Servers sowie der Web-Seiten- und Richtlinieneinstellungen zuständig.

  Im Bereich „Benutzerverwaltung“ von Administration-Console können Admins Benutzenden die folgenden Rollen zuweisen. Benutzende, denen diese Rollen zugewiesen sind, führen ihre Aufgaben im Bereich der Document Security-Benutzeroberfläche von Administration-Console aus.

  **Document Security-Superadmin**

  Benutzende mit dieser Rolle haben Zugriff auf alle Document Security-Einstellungen in Administration-Console. Die folgenden Berechtigungen sind mit der Rolle verknüpft:

   * Konfiguration verwalten
   * Richtlinie verwalten
   * Richtliniensätze verwalten
   * Dokumente verwalten
   * Dokumentherausgeber verwalten
   * Eingeladene und lokale Benutzende verwalten
   * Ereignisse anzeigen
   * Delegieren
   * Externe Benutzende einladen

  **Document Security-Admin**

  Benutzende mit dieser Rolle können den Document Security-Server mithilfe der Seite „Konfiguration“ im Abschnitt „Document Security“ von Administration-Console konfigurieren. Diese Berechtigung ist mit der Rolle „Konfiguration verwalten“ verknüpft.

  >[!NOTE]
  >
  >Benutzende mit dieser Rolle müssen auch über die Rolle „Administration-Console-Benutzer“ verfügen, um sich bei Administration-Console anzumelden und Konfigurationseinstellungen zu bearbeiten.

  **Document Security-Richtliniensatz-Admin**

  Benutzende mit dieser Rolle können den Abschnitt „Document Security“ von Administration-Console verwenden, um die Richtlinien anderer Benutzender zu bearbeiten und Richtliniensätze zu erstellen, zu bearbeiten und zu löschen. Wenn Richtliniensatz-Admins einen Richtliniensatz erstellen, können sie diesem Richtliniensatz eine Richtliniensatz-Koordinatorin bzw. einen -Koordinator zuweisen. Die folgenden Berechtigungen sind mit der Rolle verknüpft:

   * Richtlinie verwalten
   * Richtliniensätze verwalten
   * Dokumente verwalten
   * Dokumentherausgeber verwalten
   * Ereignisse anzeigen
   * Delegieren

  >[!NOTE]
  >
  >Benutzende mit dieser Rolle müssen auch über die Rolle „Administration-Console-Benutzer“ verfügen, um sich bei Administration-Console anzumelden und Konfigurationseinstellungen zu bearbeiten.

  **Document Security verwaltet eingeladene und lokale Benutzer**

  Benutzende mit dieser Rolle können Aufgaben ausführen, die zur Verwaltung aller eingeladenen und lokalen Benutzenden auf den entsprechenden Document Security-Web-Seiten erforderlich sind. Die folgenden Berechtigungen sind mit der Rolle verknüpft:

   * Eingeladene und lokale Benutzende verwalten
   * Externe Benutzende einladen
   * Zugriff auf Web-Seiten für Endbenutzende

  >[!NOTE]
  >
  >Benutzende mit dieser Rolle müssen auch über die Rolle „Administration-Console-Benutzer“ verfügen, um sich bei Administration-Console anzumelden und Konfigurationseinstellungen zu bearbeiten.

  **Document Security – Benutzende einladen**

  Benutzende mit dieser Rolle können Benutzende einladen. Die folgenden Berechtigungen sind mit der Rolle verknüpft:

   * Externe Benutzende einladen
   * Zugriff auf Web-Seiten für Endbenutzende

  **Document Security-Endbenutzer**

  Benutzende mit dieser Rolle können auf Document Security-Web-Seiten für Endbenutzende zugreifen. Diese Rolle kann auch Admins zugewiesen werden, damit diese unter Verwendung der Endbenutzerseiten Richtlinien erstellen können. Diese Berechtigung ist mit der Rolle „Zugriff auf Web-Seiten für Endbenutzende“ verknüpft.

* Benutzende innerhalb der Organisation, die über gültige Document Security-Konten verfügen, erstellen ihre eigenen Richtlinien, verwenden Richtlinien zum Schutz von Dokumenten, verfolgen und verwalten ihre richtliniengeschützten Dokumente und überwachen Ereignisse, die mit ihren Dokumenten zusammenhängen.
* Richtliniensatz-Koordinatorinnen und -Koordinatoren verwalten Dokumente, zeigen Ereignisse an und verwalten andere Richtliniensatz-Koordinatorinnen und -Koordinatoren (basierend auf ihren Berechtigungen). Admins bestimmen Benutzende als Richtliniensatz-Koordinatorinnen oder -Koordinatoren für bestimmte Richtliniensätze.
* Benutzende, die nicht zu Ihrer Organisation gehören (z. B. Geschäftspartner), können richtliniengeschützte Dokumente verwenden, wenn sie sich im Document Security-Verzeichnis befinden, wenn Admins ein Konto für sie erstellen oder wenn sie sich über einen automatischen E-Mail-Einladungsprozess bei Document Security registrieren. Je nachdem, wie Admins die Zugriffseinstellungen aktivieren, können eingeladenen Benutzende auch berechtigt sein, Richtlinien auf Dokumente anzuwenden, Richtlinien zu erstellen, zu ändern und zu löschen und andere externe Benutzende zur Verwendung ihrer richtliniengeschützten Dokumente einzuladen.
* Entwickler können die AEM Forms-SDK verwenden, um benutzerdefinierte Anwendungen mit Document Security zu integrieren.

Document Security-Admins können benutzerdefinierte Rollen mithilfe der folgenden Berechtigungen in User Management erstellen:

* Document Security – Konfiguration verwalten
* Document Security – eingeladene und lokale Benutzende verwalten
* Document Security – Richtliniensätze verwalten
* Document Security – Richtliniensätze verwalten
* Document Security – Server-Ereignisse anzeigen
* Document Security – Richtlinieneigentümer oder -eigentümerinnen ändern

## Richtlinien und richtliniengeschützte Dokumente {#policies-and-policy-protected-documents}

Eine *Richtlinie* definiert einen Satz von Vertraulichkeitseinstellungen sowie die Benutzenden, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Eine Richtlinie ermöglicht auch eine dynamische Änderung der Berechtigungen für ein Dokument. Dadurch erhält die Person, die das Dokument sichert, die Berechtigung, die Vertraulichkeitseinstellungen zu ändern, um den Zugriff auf das Dokument zu widerrufen oder die Richtlinie zu wechseln.

Der Richtlinienschutz kann mithilfe von Adobe Acrobat® Pro und Acrobat Standard auf ein PDF-Dokument angewendet werden. Der Richtlinienschutz kann auch für andere Dateitypen, z. B. Microsoft® Word-, Excel- und PowerPoint-Dateien aktiviert werden. Verwenden Sie hierfür die Client-Anwendung, wobei die entsprechende Acrobat Reader DC Extensions installiert sein muss.

### Funktionsweise von Richtlinien {#how-policies-work}

Richtlinien enthalten Informationen über die autorisierten Benutzenden und die Vertraulichkeitseinstellungen, die auf Dokumente anzuwenden sind. Benutzende können beliebige Personen in Ihrer Organisation sein oder Personen, die außerhalb Ihrer Organisation sind und über ein Konto verfügen. Wenn Admins die Einladungsfunktion für Benutzende aktivieren, können sogar neue Benutzende zu Richtlinien hinzugefügt werden, wodurch ein E-Mail-basierter Einladungsprozess zur Registrierung eingeleitet wird.

Die Vertraulichkeitseinstellungen in einer Richtlinie bestimmen, wie Empfängerinnen und Empfänger das Dokument verwenden können. So können Sie beispielsweise angeben, ob Empfängerinnen und Empfänger Text drucken oder kopieren, Änderungen vornehmen oder geschützten Dokumenten Signaturen und Kommentare hinzufügen können. Dieselbe Richtlinie kann auch für bestimmte Personen unterschiedliche Vertraulichkeitseinstellungen festlegen.

>[!NOTE]
>
>Vertraulichkeitseinstellungen, die über eine Richtlinie angewendet werden, setzen Einstellungen außer Kraft, die möglicherweise mithilfe der Passwort- oder Zertifikatsicherheitsoptionen auf ein PDF-Dokument in Acrobat angewendet wurden. (Weitere Informationen finden Sie in der Acrobat-Hilfe.)

Benutzende und Admins erstellen Richtlinien über die Web-Seiten für Document Security. Auf ein Dokument kann jeweils nur eine Richtlinie angewendet werden. Sie können eine Richtlinie mit einer der folgenden Methoden anwenden:

* Öffnen Sie das Dokument in Acrobat oder einer anderen Client-Anwendung und wählen Sie eine Richtlinie zum Schützen des Dokuments aus.
* Senden Sie in Microsoft® Outlook ein Dokument als E-Mail-Anlage. In diesem Fall können Sie eine Richtlinie aus einer Liste von Richtlinien auswählen. Alternativ können Sie eine automatisch generierte Richtlinie auswählen, die Acrobat mit einem Standardsatz von Vertraulichkeitseinstellungen erstellt, um das Dokument nur für die Empfängerinnen und Empfänger der E-Mail-Nachricht zu schützen.

Eine Richtlinie kann mithilfe der Client-Anwendung aus einem Dokument entfernt werden.

![rm_psonline_policy](assets/rm_psonline_policy.png)

Gehen Sie wie folgt vor:

1. Die für das Dokument verantwortliche Person sichert das Dokument in einer unterstützten Client-Anwendung mit einer Richtlinie, die die Online-Nutzung ermöglicht.
1. Document Security erstellt eine Dokumentlizenz und einen Dokumentschlüssel und verschlüsselt die Richtlinie. Die Dokumentlizenz, die verschlüsselte Richtlinie und der Dokumentschlüssel werden an die Client-Anwendung zurückgegeben.
1. Das Dokument wird mit dem Dokumentschlüssel verschlüsselt, der anschließend gelöscht wird. Die Lizenz und die Richtlinie sind nun im Dokument eingebettet. Diese Aufgaben werden in der unterstützten Client-Anwendung ausgeführt.

Wenn Sie eine Richtlinie auf ein Dokument anwenden, werden die darin enthaltenen Informationen, einschließlich aller in PDF-Dokumenten enthaltenen Dateien (Text, Audio oder Video), durch die in der Richtlinie angegebenen Vertraulichkeitseinstellungen geschützt. Document Security generiert eine Lizenz sowie Verschlüsselungsinformationen, die anschließend im Dokument eingebettet werden. Wenn Sie das Dokument verteilen, kann Document Security die Empfängerinnen und Empfänger authentifizieren, die versuchen, das Dokument zu öffnen, und den Zugriff entsprechend den in der Richtlinie festgelegten Berechtigungen autorisieren.

Wenn die Offline-Nutzung aktiviert ist, können Empfängerinnen und Empfänger richtliniengeschützte Dokumente auch offline (ohne aktive Internet- oder Netzwerkverbindung) für den in der Richtlinie angegebenen Zeitraum nutzen.

### Funktionsweise richtliniengeschützter Dokumente {#how-policy-protected-documents-work}

Um richtliniengeschützte Dokumente öffnen und verwenden zu können, muss die Richtlinie Ihren Namen als Empfängerin bzw. Empfänger enthalten, und weiterhin müssen Sie über ein gültiges Document Security-Konto verfügen. Für PDF-Dokumente benötigen Sie Acrobat oder Adobe Reader®. Für andere Dateitypen müssen sowohl das entsprechende Programm als auch die Acrobat Reader DC-Erweiterungen für dieses Programm installiert sein.

Wenn Sie ein richtliniengeschütztes Dokument öffnen, stellen Acrobat, Adobe Reader oder die Acrobat Reader DC-Erweiterungen eine Verbindung zu Document Security her, um Sie zu authentifizieren. Anschließend können Sie sich anmelden. Wenn die Dokumentnutzung überwacht wird, wird eine Benachrichtigung angezeigt. Nachdem Document Security bestimmt hat, welche Dokumentberechtigungen erteilt werden sollen, verwaltet sie die Entschlüsselung des Dokuments. Anschließend können Sie das Dokument gemäß den Vertraulichkeitseinstellungen der Richtlinie verwenden.

![rm_psopen_online](assets/rm_psopen_online.png)

Gehen Sie wie folgt vor:

1. Die Person, die das Dokument benutzt, öffnet das Dokument in einer unterstützten Client-Anwendung und authentifiziert sich beim Server. Die Dokument-ID wird an den Document Security-Server gesendet.
1. Document Security authentifiziert Benutzende, prüft die Richtlinie auf Autorisierung und erstellt einen Beleg. Der Beleg (mit dem Dokumentschlüssel und den Berechtigungen) wird zurück an die Client-Anwendung gesendet.
1. Das Dokument wird mit dem Dokumentschlüssel entschlüsselt, der anschließend gelöscht wird. Das Dokument kann anschließend gemäß den Vertraulichkeitseinstellungen der Richtlinie genutzt werden. Diese Aufgaben werden in der unterstützten Client-Anwendung ausgeführt.

Sie können ein Dokument unter folgenden Bedingungen weiterhin verwenden:

* Unbegrenzt oder für die in der Richtlinie angegebene Gültigkeitsdauer
* Bis durch Admins oder die Person, die die Richtlinie angewendet hat, entweder der Zugriff auf die Datei widerrufen oder die Richtlinie geändert wird

Sie können richtliniengeschützte Dokumente auch offline (ohne Internet- oder Netzwerkverbindung) verwenden, wenn die Richtlinie den Offline-Zugriff zulässt. Sie müssen sich zuerst bei Document Security anmelden, um das Dokument zu synchronisieren. Anschließend können Sie das Dokument für die in der Richtlinie angegebene Offline-Nutzungsdauer verwenden.

Wenn die Offline-Nutzungsdauer endet, synchronisieren Sie das Dokument erneut mit Document Security, indem Sie entweder online gehen und ein richtliniengeschütztes Dokument öffnen oder indem Sie einen Befehl in der Client-Anwendung verwenden. Weitere Informationen finden Sie in der *Hilfe zu Acrobat* oder der entsprechenden *Hilfe zu den Acrobat Reader DC-Erweiterungen.*

Wenn Sie eine Kopie eines richtliniengeschützten Dokuments mit dem Menübefehl „Speichern“ oder „Speichern unter“ speichern, wird die Richtlinie automatisch angewendet und für das neue Dokument durchgesetzt. Ereignisse wie z. B. der Versuch, das neue Dokument zu öffnen, werden auch für das Originaldokument geprüft und aufgezeichnet.

## Richtliniensätze {#policy-sets}

*Richtliniensätze* dienen zum Gruppieren verschiedener Richtlinien mit einem gemeinsamen Zweck. Diese Richtliniensätze werden dann einer Untergruppe von Benutzenden im System zur Verfügung gestellt.

Jedem Richtliniensatz können ein oder mehrere Richtliniensatz-Koordinatorinnen oder -Koordinatoren zugeordnet sein. Der Richtliniensatzkoordinator ist ein Administrator oder Benutzer mit zusätzlichen Berechtigungen. Die *Richtliniensatz-Koordinatorinnen und -Koordinatoren* sind in der Regel spezialisierte Personen in der Organisation, die die Richtlinien eines bestimmten Richtliniensatzes am besten erstellen können.

Richtliniensatz-Koordinatorinnen und -Koordinatoren können die folgenden Aufgaben ausführen:

* Erstellen von Richtlinien
* Bearbeiten und Löschen einer beliebigen Richtlinie im Richtliniensatz
* Bearbeiten von Einstellungen für Richtliniensätze
* Hinzufügen und Entfernen von Richtliniensatz-Koordinatorinnen und -Koordinatoren
* Anzeigen von Richtlinien- und Dokumentereignissen für jede Richtlinie oder jedes Dokument innerhalb des Richtliniensatzes
* Widerrufen des Zugangs zu Dokumenten
* Wechseln der Richtlinien für das Dokument

>[!NOTE]
>
>Sie können maximal 1.000 Richtliniensatznamen aus der Datenbank abrufen, indem Sie die `getAllPolicysetnames()`-API verwenden.

Richtliniensätze werden auf den Web-Seiten zur Verwaltung von Document Security durch Admins und Richtliniensatz-Koordinatorinnen bzw. -Koordinatoren erstellt und gelöscht, die dazu berechtigt sind.

Richtliniensätze werden einer begrenzten Anzahl von Benutzenden zur Verfügung gestellt, indem festgelegt wird, welche Benutzenden oder Gruppen innerhalb einer Domain die Richtlinien des Richtliniensatzes zum Schutz von Dokumenten verwenden dürfen.

Bei der Installation von Document Security wird ein Standardrichtliniensatz mit der Bezeichnung *Globaler Richtliniensatz* erstellt. Dieser Richtliniensatz wird von den Admins verwaltet, die die Software installiert haben.

## Best Practices {#best-practices}

Richtlinien sind wiederverwendbare Sätze von Berechtigungen und Benutzergruppen, die auf verschiedene Dokumente angewendet werden können. Für die geschützten Dokumente. Diese Richtlinien stellen sicher, dass die jeweiligen Funktionen nur von zulässigen Benutzern verwendet werden können. Es ist davon auszugehen, dass die Anzahl der Richtlinien und Richtliniensätze mit einem Anstieg der verschiedenen Benutzerrollen und Dokumente in einer Abteilung wächst. Hier finden Sie einige Überlegungen und Best Practices zum Erstellen und Verwalten von Richtlinien:

* **Wiederverwendbare Richtlinien erstellen**: Adobe empfiehlt die Wiederverwendung von Richtlinien über verschiedene Dokumente hinweg. Dies trägt dazu bei, die Anzahl der Richtlinien auf ein Minimum zu beschränken, eine optimale Leistung zu erzielen und die Verwaltung der Richtlinien zu vereinfachen. So erstellen Sie eine wiederverwendbare Richtlinie:

1. Identifizierung und Definition der Anforderungen an die Zugriffskontrolle auf Abteilungs- und Organisationsebene.

1. Erstellen Sie Benutzergruppen und fügen Sie diesen Gruppen Benutzer hinzu.

1. Erstellen Sie einen Richtliniensatz.

1. Öffnen Sie den Richtliniensatz und erstellen Sie eine Richtlinie. Fügen Sie Benutzergruppen hinzu und legen Sie Einstellungen zur Vertraulichkeit (Zugriffskontrolle) für die Richtlinie fest.

Fügen Sie zu Richtlinien Benutzergruppen anstelle einzelner Benutzer hinzu. Dies erleichtert die Verwaltung und Anwendung von Richtlinien für viele Benutzende.

* **Benutzerdefinierte Richtliniensätze erstellen**: Ein Richtliniensatz kombiniert mehrere Richtlinien zu einer verwaltbaren Entität. Erstellen Sie benutzerdefinierte Richtliniensätze für Ihre Organisation oder Abteilung, verwenden Sie sie zur Gruppierung verwandter Richtlinien und stellen Sie sie einer Untergruppe von Benutzern im System zur Verfügung.

  Die Verwendung von Richtliniensätzen erleichtert die Zuweisung und Verwaltung von verwandten Richtlinien zu bestimmten Benutzern in einer Organisation oder Abteilung. So können beispielsweise separate Richtliniensätze für die Finanz- und Personalabteilung dazu beitragen, die damit verbundenen Richtlinien einfach zu verwalten und auf Dokumente anzuwenden, die für die jeweiligen Abteilungen bestimmt sind.

* **Verwenden Sie einen externen Autorisierer, um Berechtigungen dynamisch anzuwenden**: Sie können [externe Autorisierer](https://help.adobe.com/de_DE/livecycle/11.0/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-6f26.2.html) verwenden, um Berechtigungen basierend auf externen Bedingungen zu bewerten und dynamisch anzuwenden. Wenn die Berechtigungen dynamisch anhand externer Bedingungen ausgewertet werden, können Sie:

   * Eine zentralisierte Zugriffskontrolle für Dokumente in Ihrer Organisation ermöglichen.

   * Den Zugriff auf richtliniengeschützte Dokumente kontrollieren, indem dynamisch bestimmt wird, ob ein Benutzer auf ein richtliniengeschütztes Dokument zugreifen kann. Zum Beispiel kann dynamisch entschieden werden, ob ein Benutzer ein richtliniengeschütztes Dokument drucken darf.

   * Verwenden Sie zusätzlich zum standardmäßigen Prozess zur Richtlinienbewertung einen Zugriffskontrollmechanismus, den Ihr Content-Management-System verwendet. Wenn der Dienst beispielsweise bestimmt, ob eine Person ein richtliniengeschütztes Dokument drucken kann, kann er den standardmäßigen Prozess zur Richtlinienbewertung verwenden. Außerdem kann er den Zugriffskontrollmechanismus verwenden, den Ihr Content-Management-System verwendet.

  Obwohl es möglich ist, den Richtlinienbewertungsprozess von Document Security vollständig durch einen externen Autorisierungs-Handler zu ersetzen, wird empfohlen, dass Sie einen externen Autorisierungs-Handler in Verbindung mit dem Richtlinienbewertungsprozess verwenden. Dann kann der Dokumentzugriff über denselben Kontrollmechanismus gesteuert werden, den Ihr Content Management-System verwendet. Wenn beispielsweise der Document Security-Dienst bestimmt, ob eine Person ein richtliniengeschütztes Dokument drucken kann, wird der standardmäßige Prozess zur Richtlinienbewertung verwendet. Außerdem wird der Zugriffssteuerungsmechanismus verwendet, den Ihr Content-Management-System verwendet. Weitere Informationen finden Sie unter [Erstellen externer Autorisierungs-Handler](https://help.adobe.com/de_DE/livecycle/11.0/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-6f26.2.html).

* **Beschränken Sie die Anzahl der Richtliniensätze auf ein Minimum**: Es gibt mehrere Faktoren, die zu einer ständigen Zunahme von Richtlinien und Richtliniensätzen führen. Einige häufige Faktoren sind:

   * Zunahme der Benutzerrollen, Abteilungen und Dokumente innerhalb einer Organisation über einen bestimmten Zeitraum.
   * Die Abteilungen einer Organisation arbeiten isoliert und halten die abteilungsspezifischen Richtlinien streng unter Kontrolle. Dies führt zu identischen Richtlinien innerhalb einer Organisation.

  Adobe empfiehlt, die Anzahl der Richtlinien und Richtliniensätze auf ein Minimum zu beschränken. Dies erleichtert die einfache Verwaltung von Richtlinien und Richtliniensätzen und sorgt für eine bessere Leistung. So halten Sie die Anzahl auf ein Minimum beschränkt:

   * Erstellen Sie wiederverwendbare Richtlinien. Diese Richtlinien können über mehrere Abteilungen hinweg gemeinsam genutzt werden.
   * Erwägen Sie die Erstellung von unternehmensweiten Richtliniensätzen, wenn einige Richtlinien für mehrere Abteilungen gelten, und nicht für jeden Bereich einen individuellen Richtliniensatz.
   * Gruppieren Sie zusammengehörige Richtlinien in einem Richtliniensatz. Erstellen Sie nicht für jede Richtlinie einen separaten Richtliniensatz.
   * Verwenden Sie einen externen Autorisierer, um Benutzerberechtigungen dynamisch zu steuern.

  >[!NOTE]
  >
  >Sie können die API [getAllPolicysetnames()](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/PolicyManager.html) verwenden, um bis zu 1000 Richtliniensatznamen abzurufen. Intern ruft die API maximal 1.000 Richtlinien ab, für die der API-Aufrufer über die Berechtigung des Dokumentherausgebers verfügt, erstellt dann eine Liste eindeutiger Richtliniensatznamen, die mit abgerufenen Richtlinien verknüpft sind, und gibt diese an Sie zurück. Wenn die API beispielsweise 1.000 Richtlinien abruft und die abgerufenen Richtlinien insgesamt 200 Richtliniensätzen zugeordnet sind, gibt die API nur 200 Richtliniensatznamen zurück.
