---
title: Grundlagen zu AEM Forms-Prozessen
seo-title: Grundlagen zu AEM Forms-Prozessen
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
source-wordcount: '807'
ht-degree: 2%

---

# Verstehen der AEM Forms-Prozesse {#understanding-aem-forms-processes}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Ein gängiges Anwendungsbeispiel besteht darin, dass eine Reihe von AEM Forms-Diensten mit einem einzigen Dokument arbeiten kann. Sie können eine Anforderung an den Dienstcontainer senden, indem Sie einen Prozess mithilfe von Workbench erstellen. Ein Prozess stellt einen Geschäftsprozess dar, den Sie automatisieren. Informationen zum Erstellen von Prozessen finden Sie unter [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63) verwenden.

Sobald ein Prozess aktiviert wird, wird er zu einem Dienst und kann wie andere Dienste aufgerufen werden. Ein Unterschied zwischen einem Standarddienst wie dem Encryption-Dienst und einem Dienst, der von einem Prozess stammt, besteht darin, dass dieser einen Vorgang hat, der viele Aktionen ausführt. Ein Standarddienst weist dagegen viele Vorgänge auf. Jeder Vorgang führt in der Regel eine Aktion durch, z. B. das Anwenden einer Richtlinie auf ein Dokument oder das Verschlüsseln eines Dokuments.

Prozesse können kurzlebig oder langlebig sein. Ein kurzlebiger Prozess ist ein Vorgang, der synchron und in demselben Ausführungs-Thread ausgeführt wird, von dem aus er aufgerufen wurde. Kurzlebige Vorgänge sind mit dem Standardverhalten in den meisten Programmiersprachen vergleichbar, bei dem eine Client-Anwendung eine Methode aufruft und auf einen Rückgabewert wartet.

Es gibt jedoch Situationen, in denen ein Prozess aufgrund von Faktoren wie diesen nicht synchron abgeschlossen werden kann:

* Ein Prozess kann eine erhebliche Zeitspanne umfassen.
* Ein Prozess kann organisatorische Grenzen überschreiten.
* Ein Prozess benötigt eine externe Eingabe, damit er abgeschlossen werden kann. Angenommen, ein Formular wird an einen Manager gesendet, der nicht im Büro ist. In diesem Fall ist der Prozess erst abgeschlossen, wenn der Manager das Formular zurückgibt und ausfüllt.

   Diese Arten von Prozessen werden als langlebige Prozesse bezeichnet. Ein langlebiger Prozess wird asynchron ausgeführt, sodass Systeme so interagieren können, wie es die Ressourcen zulassen, und das Tracking und die Überwachung des Vorgangs ermöglichen. Wenn ein langlebiger Prozess aufgerufen wird, erstellt AEM Forms einen Aufrufkennungswert als Teil eines Datensatzes, der den langlebigen Prozessstatus verfolgt. Der Datensatz wird in der AEM Forms-Datenbank gespeichert. Sie können langlebige Prozessdatensätze bereinigen, wenn sie nicht mehr benötigt werden.

>[!NOTE]
>
>AEM Forms erstellt keinen Datensatz, wenn ein kurzlebiger Prozess aufgerufen wird.

Mithilfe des Werts für die Kennung des Aufrufs können Sie den Status des langlebigen Prozesses verfolgen. Beispielsweise können Sie den Wert für die Prozessaufruf-ID verwenden, um Prozesse in Manager auszuführen, z. B. um eine laufende Prozessinstanz zu beenden.

**Beispiel für einen kurzlebigen Prozess**

Die folgende Abbildung zeigt ein Beispiel für einen kurzlebigen Prozess mit dem Namen *MyApplication/EncryptDocument*.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um den Codebeispielen zu folgen, die besprechen, wie dieser Prozess aufgerufen wird, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` mithilfe von Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser kurzlebige Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das als Eingabewert an den Prozess übergeben wird.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Der Name des Eingabeparameters für diesen Prozess ist `inDoc` und der Datentyp ist &quot;document&quot;.
1. Speichert das kennwortverschlüsselte PDF-Dokument als PDF-Datei im lokalen Dateisystem. Dieser Prozess gibt das verschlüsselte PDF-Dokument als Ausgabewert zurück. Der Name des Ausgabeparameters für diesen Prozess ist `outDoc` und der Datentyp ist &quot;document&quot;.

   Dieser Prozess wird synchron im selben Ausführungs-Thread abgeschlossen, von dem aus er aufgerufen wurde. Der Name dieses kurzlebigen Prozesses ist `MyApplication/EncryptDocument`und sein Vorgang ist `invoke`.

   >[!NOTE]
   >
   >In der Regel besteht ein kurzlebiger Prozess aus mehr als drei Aktionen. Sie erstellen einen Prozess mit Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   *Die Programmierung mit AEM* beschreibt die folgenden Methoden, mit denen Sie diesen kurzlebigen Prozess programmgesteuert aufrufen können:

   * [Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mit AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)  (mithilfe einer Flex-Anwendung)
   * [Aufrufen eines kurzlebigen Prozesses mithilfe der Aufruf-API ](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api)  (Java Invocation API)
   * [Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http)  (Webdienstbeispiel)
   * [Aufrufen von AEM Forms mithilfe von DIME](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime)  (Webdienstbeispiel)
   * [Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST](/help/forms/developing/invoking-aem-forms-using-rest.md)

**Beispiel für langlebige Prozesse**

Die folgende Abbildung zeigt ein Beispiel für einen langlebigen Prozess.

Dieser Prozess wird aufgerufen, wenn ein Antragsteller ein Darlehensformular einreicht. Das Verfahren ist erst abgeschlossen, wenn ein Kreditsachbearbeiter den Kreditantrag genehmigt oder ablehnt. Der Name dieses langlebigen Prozesses ist *FirstAppSolution/PreLoanProcess* und sein Vorgang ist `invoke_Async`. Dieser Prozess muss asynchron aufgerufen werden. Informationen zum programmgesteuerten Aufrufen dieses langlebigen Prozesses finden Sie unter [Aufrufen von menschenzentrierten langlebigen Prozessen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>Dieser Prozess kann anhand des unter [Erstellen der ersten AEM Forms-Anwendung](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63) angegebenen Tutorials erstellt werden.
