---
title: Wie kann AEM SDK neu gestartet werden?
description: Best Practices für den Neustart AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: f5d69d04-b842-4329-b1b3-57b88266d13d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 15%

---

# Neustart des AEM SDK

Wenn Sie das AEM SDK neu starten, indem Sie die Java™-Prozesse stoppen, kann dies zu Inkonsistenzen in der AEM Entwicklungsumgebung führen. Es tritt ein Fehler auf, wie:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Neustart-aem-sdk-error](/help/forms/using/assets/restart-sdk-error.png)

## Lösung

Um das AEM SDK neu zu starten, wechseln Sie zum aktiven Befehlsfenster und drücken Sie die `Ctrl + C` -Befehl zum Neustart des SDK.

Es wird empfohlen, den Befehl „Strg + C“ zu verwenden, um das SDK neu zu starten. Das Neustart des AEM SDK mithilfe alternativer Methoden, z. B. das Beenden von Java™-Prozessen, kann zu Inkonsistenzen in der AEM Entwicklungsumgebung führen.
