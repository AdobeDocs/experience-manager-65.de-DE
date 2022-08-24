---
title: Grundlagen zu AEM Forms-Prozessen
seo-title: Understanding AEM Forms Processes
description: Grundlagen zu AEM Forms-Prozessen
uuid: 7cbebe7d-f222-42fa-8eb6-d2443458a791
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools, coding
discoiquuid: ac9fe461-63e7-442b-bd1c-eb9576ef55aa
role: Developer
exl-id: 434ac316-8a01-43a6-844b-1b792f60fa21
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---

# Grundlagen zu AEM Forms-Prozessen {#understanding-aem-forms-processes}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Ein gängiges Anwendungsbeispiel besteht darin, dass eine Reihe von AEM Forms-Services mit einem einzigen Dokument arbeiten kann. Sie können eine Anfrage an den Service-Container senden, indem Sie einen Prozess mithilfe von Workbench erstellen. Ein Workflow stellt einen Geschäftsprozess dar, den Sie automatisieren. Informationen zum Erstellen von Prozessen finden Sie unter [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).

Sobald ein Prozess aktiviert wird, wird er zu einem Service und kann wie andere Services aufgerufen werden. Ein Unterschied zwischen einem Standard-Service, wie dem Verschlüsselungs-Service, und einem Service, der aus einem Prozess entstanden ist, besteht darin, dass letzterer einen Vorgang hat, die viele Aktionen ausführt. Ein Standard-Service weist dagegen viele Vorgänge auf. Jeder Vorgang führt in der Regel nur eine Aktion durch, z. B. das Anwenden einer Richtlinie auf ein Dokument oder das Verschlüsseln eines Dokuments.

Prozesse können kurzlebig oder langlebig sein. Ein kurzlebiger Prozess ist ein Vorgang, der synchron und in demselben Ausführungs-Thread ausgeführt wird, von dem aus er aufgerufen wurde. Kurzlebige Vorgänge sind mit dem Standardverhalten in den meisten Programmiersprachen vergleichbar, bei dem ein Client-Programm eine Methode aufruft und auf einen Rückgabewert wartet.

Es gibt jedoch Situationen, in denen ein Prozess aufgrund von Faktoren wie den folgenden nicht synchron abgeschlossen werden kann:

* Ein Prozess kann eine erhebliche Zeitspanne umfassen.
* Ein Prozess kann organisatorische Grenzen überschreiten.
* Zur Beendigung eines Prozesses ist eine externe Eingabe erforderlich. Angenommen, ein Formular wird an einen Manager gesendet, der nicht im Büro ist. In diesem Fall ist der Prozess erst abgeschlossen, wenn der Manager das Formular zurückgibt und ausfüllt.

   Diese Arten von Prozessen werden als langlebige Prozesse bezeichnet. Ein langlebiger Prozess wird asynchron ausgeführt, sodass Systeme so interagieren können, wie es die Ressourcen zulassen, und das Tracking und die Überwachung des Vorgangs ermöglicht wird. Wenn ein langlebiger Prozess aufgerufen wird, erstellt AEM Forms einen Aufrufkennungswert als Teil eines Datensatzes, der den langlebigen Prozessstatus verfolgt. Der Datensatz wird in der AEM Forms-Datenbank gespeichert. Sie können langlebige Prozesseinträge löschen, wenn sie nicht mehr benötigt werden.

>[!NOTE]
>
>AEM Forms erstellt keinen Datensatz, wenn ein kurzlebiger Prozess aufgerufen wird.

Mithilfe des Werts für die Aufrufkennung können Sie den Status des langlebigen Prozesses verfolgen. Sie können zum Beispiel den Wert der Prozessaufrufskennung verwenden, um Vorgänge in Process Manager durchzuführen, z. B. um eine laufende Prozessinstanz zu beenden.

**Beispiel für einen kurzlebigen Prozess**

Die folgende Abbildung zeigt ein Beispiel für einen kurzlebigen Prozess mit dem Namen *MyApplication/EncryptDocument*.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um den Code-Beispielen zum Aufrufen dieses Prozesses zu folgen, erstellen Sie mithilfe von Workbench einen Prozess namens `MyApplication/EncryptDocument`. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser kurzlebige Prozess aufgerufen wird, führt er die folgenden Aktionen durch:

1. Ruft das ungesicherte PDF-Dokument ab, das als Eingabewert an den Prozess übergeben wird.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Der Name des Eingabeparameters für diesen Prozess lautet `inDoc`, und der Datentyp ist „document“.
1. Speichert das kennwortverschlüsselte PDF-Dokument als PDF-Datei im lokalen Dateisystem. Dieser Prozess gibt das verschlüsselte PDF-Dokument als Ausgabewert zurück. Der Name des Ausgabeparameters für diesen Prozess lautet `outDoc`, und der Datentyp ist „document“.

   Dieser Prozess wird synchron im selben Ausführungs-Thread abgeschlossen, von dem aus er aufgerufen wurde. Der Name dieses kurzlebigen Prozesses lautet `MyApplication/EncryptDocument`, und sein Vorgang ist `invoke`.

   >[!NOTE]
   >
   >In der Regel besteht ein kurzlebiger Prozess aus mehr als drei Aktionen. Sie erstellen einen Prozess mithilfe von Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   *Programmieren mit AEM Forms* beschreibt die folgenden Methoden, mit denen Sie diesen kurzlebigen Prozess programmgesteuert aufrufen können:

   * [Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mithilfe von AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) (Verwenden eines Flex-Programms)
   * [Aufrufen eines kurzlebigen Prozesses mithilfe der Aufruf-API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api) (Java Invocation API)
   * [Aufrufen von AEM Forms mithilfe der Base64-Codierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding) (Beispiel für einen Webservice)
   * [Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) (Beispiel für einen Webservice)
   * [Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref) (Beispiel für einen Webservice)
   * [Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http) (Beispiel für einen Webservice)
   * [Aufrufen von AEM Forms mithilfe von DIME](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime) (Beispiel für einen Webservice)
   * [Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST](/help/forms/developing/invoking-aem-forms-using-rest.md)

**Beispiel für einen langlebigen Prozess**

Die folgende Abbildung zeigt ein Beispiel für einen langlebigen Prozess.

Dieser Prozess wird aufgerufen, wenn ein Antragsteller ein Darlehensformular einreicht. Das Verfahren ist erst abgeschlossen, wenn ein Kreditsachbearbeiter den Kreditantrag genehmigt oder ablehnt. Der Name dieses langlebigen Prozesses lautet *FirstAppSolution/PreLoanProcess*, und sein Vorgang ist `invoke_Async`. Dieser Prozess muss asynchron aufgerufen werden. Informationen zum programmgesteuerten Aufrufen dieses langlaufenden Prozesses finden Sie unter [Aufrufen von an Menschen orientierten langlaufenden Prozessen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>Dieser Prozess kann durch Befolgen des in [Erstellen der ersten AEM Forms-Anwendung](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63) angegebenen Tutorials erstellt werden.
