---
title: Die AEM Forms-Prozesse
seo-title: Die AEM Forms-Prozesse
description: Die AEM Forms-Prozesse
uuid: 7cbebe7d-f222-42fa-8eb6-d2443458a791
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools, coding
discoiquuid: ac9fe461-63e7-442b-bd1c-eb9576ef55aa
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Die AEM Forms-Prozesse {#understanding-aem-forms-processes}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Ein gängiger Anwendungsfall besteht darin, dass eine Reihe von AEM Forms-Diensten auf einem einzigen Dokument betrieben wird. Sie können eine Anforderung an den Dienst-Container senden, indem Sie einen Prozess mit Workbench erstellen. Ein Prozess stellt einen Geschäftsprozess dar, den Sie automatisieren. Informationen zum Erstellen von Prozessen finden Sie unter [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63) verwenden.

Sobald ein Prozess aktiviert ist, wird er zu einem Dienst und kann wie andere Dienste aufgerufen werden. Ein Unterschied zwischen einem Standarddienst wie dem Encryption-Dienst und einem Dienst, der aus einem Prozess stammt, besteht darin, dass dieser einen Vorgang hat, der viele Aktionen ausführt. Im Gegensatz dazu verfügt ein Standarddienst über viele Vorgänge. Jeder Vorgang führt in der Regel eine Aktion aus, z. B. das Anwenden einer Richtlinie auf ein Dokument oder das Verschlüsseln eines Dokuments.

Prozesse können kurz oder lang dauern. Ein Prozess mit kurzer Lebensdauer ist ein Vorgang, der synchron und in demselben Ausführungsthread ausgeführt wird, von dem aus er aufgerufen wurde. Vorgänge mit kurzer Lebensdauer sind mit dem Standardverhalten in den meisten Programmiersprachen vergleichbar, bei denen eine Clientanwendung eine Methode aufruft und auf einen Rückgabewert wartet.

Es gibt jedoch Situationen, in denen ein Prozess nicht synchron abgeschlossen werden kann, z. B. aufgrund folgender Faktoren:

* Ein Prozess kann eine erhebliche Zeitspanne umfassen.
* Ein Prozess kann organisatorische Grenzen überschreiten.
* Ein Prozess benötigt externe Eingaben, damit er abgeschlossen werden kann. Angenommen, ein Formular wird an einen Manager gesendet, der nicht im Hause ist. In diesem Fall ist der Prozess erst abgeschlossen, wenn der Manager das Formular zurückgibt und ausfüllt.

   Diese Arten von Prozessen werden als Prozesse mit langer Lebensdauer bezeichnet. Ein Prozess mit langer Lebensdauer wird asynchron durchgeführt, sodass Systeme entsprechend den Ressourcen interagieren können und die Verfolgung und Überwachung des Vorgangs möglich ist. Wenn ein Prozess mit langer Lebensdauer aufgerufen wird, erstellt AEM Forms als Teil eines Datensatzes, der den Prozessstatus mit langer Lebensdauer verfolgt, einen Wert für die Aufrufkennung. Der Datensatz wird in der AEM Forms-Datenbank gespeichert. Sie können Prozessdatensätze mit langer Lebensdauer löschen, wenn sie nicht mehr benötigt werden.

>[!NOTE]
>
>AEM Forms erstellt keinen Datensatz, wenn ein Prozess mit kurzer Lebensdauer aufgerufen wird.

Mithilfe des Werts für die Aufrufkennung können Sie den Status des Prozesses mit langer Lebensdauer verfolgen. Beispielsweise können Sie den Wert für den Prozessaufruf verwenden, um Process Manager-Vorgänge wie das Beenden einer ausgeführten Prozessinstanz auszuführen.

**Beispiel für einen Prozess mit kurzer Lebensdauer**

Die folgende Abbildung zeigt ein Beispiel eines Prozesses mit kurzer Lebensdauer mit dem Namen *MyApplication/EncryptDocument*.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um zusammen mit den Codebeispielen zu folgen, die das Aufrufen dieses Prozesses beschreiben, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` mithilfe von Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess mit kurzer Lebensdauer aufgerufen wird, werden die folgenden Aktionen ausgeführt:

1. Ruft das ungesicherte PDF-Dokument ab, das als Eingabewert an den Prozess übergeben wird.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Der Name des Eingabeparameters für diesen Prozess ist `inDoc` und der Datentyp ist Dokument.
1. Speichert das kennwortverschlüsselte PDF-Dokument als PDF-Datei im lokalen Dateisystem. Dieser Vorgang gibt das verschlüsselte PDF-Dokument als Ausgabewert zurück. Der Name des Ausgabeparameters für diesen Prozess ist `outDoc` und der Datentyp ist Dokument.

   Dieser Prozess wird synchron mit demselben Ausführungsthread abgeschlossen, von dem aus er aufgerufen wurde. Der Name dieses Prozesses mit kurzer Lebensdauer ist `MyApplication/EncryptDocument`und sein Vorgang ist `invoke`.

   >[!NOTE]
   >
   >Normalerweise besteht ein Prozess mit kurzer Lebensdauer aus mehr als drei Aktionen. Sie erstellen einen Prozess mit Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   *Die Programmierung mit AEM* Formularen beschreibt die folgenden Methoden, mit denen Sie diesen Prozess mit kurzer Lebensdauer programmgesteuert aufrufen können:

   * [Aufrufen eines Prozesses mit kurzer Lebensdauer durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)  (mit einer Flex-Anwendung)
   * [Aufrufen eines Prozesses mit kurzer Lebensdauer mithilfe der AufrufAPI](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api) (Java-AufrufAPI)
   * [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mit DIME](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime)  (Webdienstbeispiel)
   * [Aufrufen des MyApplication/EncryptDocument-Prozesses mithilfe von REST](/help/forms/developing/invoking-aem-forms-using-rest.md)

**Beispiel für Prozesse mit langer Lebensdauer**

Die folgende Abbildung zeigt ein Beispiel für einen Prozess mit langer Lebensdauer.

Dieser Prozess wird aufgerufen, wenn ein Antragsteller ein Darlehensformular einreicht. Das Verfahren ist erst abgeschlossen, wenn ein Kreditsachbearbeiter den Kreditantrag genehmigt oder ablehnt. Der Name dieses Prozesses mit langer Lebensdauer ist *FirstAppSolution/PreLoanProcess* und sein Vorgang ist `invoke_Async`. Dieser Prozess muss asynchron aufgerufen werden. Weitere Informationen zum programmgesteuerten Aufrufen dieses langlebigen Prozesses finden Sie unter [Aufrufen von Prozessen mit menschlicher Zielgruppe und langer Lebensdauer](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>Dieser Vorgang kann anhand des unter [Erstellen Ihrer ersten AEM Forms-Anwendung](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63) angegebenen Lernprogramms erstellt werden.