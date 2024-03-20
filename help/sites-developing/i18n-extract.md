---
title: Extrahieren von Zeichenfolgen zum Übersetzen
description: Verwenden Sie xgettext-maven-plugin , um Zeichenfolgen aus Ihrem Quellcode zu extrahieren, die übersetzt werden müssen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
exl-id: 4acc5f7f-0bcb-4b5a-8531-52e146cffeae
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 56%

---

# Extrahieren von Zeichenfolgen zum Übersetzen{#extracting-strings-for-translating}

Verwenden Sie xgettext-maven-plugin , um Zeichenfolgen aus Ihrem Quellcode zu extrahieren, die übersetzt werden müssen. Das Maven-Plug-in extrahiert Zeichenfolgen in eine XLIFF-Datei, die Sie zur Übersetzung senden. Zeichenfolgen werden aus den folgenden Speicherorten extrahiert:

* Java-Quelldateien
* JavaScript-Quelldateien
* XML-Darstellungen von SVN-Ressourcen (JCR-Knoten)

## Konfigurieren der Zeichenfolgenextrahierung {#configuring-string-extraction}

Konfigurieren Sie, wie das xgettext-maven-plugin-Tool Zeichenfolgen für Ihr Projekt extrahiert.

```xml
/filter { }
/parsers {
   /vaultxml { }
   /javascript { }
   /regexp {
      /files {
         /java { }
         /jsp { }
         /extjstemplate { }
      }
   }
}
/potentials { }
```

| Abschnitt | Beschreibung |
|---|---|
| /filter | Identifiziert die analysierten Dateien. |
| /parsers/vaultxml | Konfiguriert das Analysieren von Vault-Dateien. Identifiziert die JCR-Knoten, die externalisierte Zeichenfolgen und Lokalisierungshinweise enthalten. Identifiziert auch zu ignorierende JCR-Knoten. |
| /parsers/javascript | Identifiziert die JavaScript-Funktionen, die Zeichenfolgen externalisieren. Sie müssen diesen Abschnitt nicht ändern. |
| /parsers/regexp | Konfiguriert das Parsing von Java-, JSP- und ExtJS-Vorlagedateien. Sie müssen diesen Abschnitt nicht ändern. |
| /potentials | Die Formel zur Erkennung von Zeichenfolgen, die internationalisiert werden sollen. |

### Identifizieren der zu analysierenden Dateien {#identifying-the-files-to-parse}

Der /filter -Abschnitt der Datei i18n.any identifiziert die Dateien, die das xgettext-maven-plugin-Tool analysiert. Fügen Sie mehrere ein- und ausschließende Regeln hinzu, um Dateien anzugeben, die geparst bzw. ignoriert werden sollen. Sie sollten alle Dateien einbeziehen und dann die Dateien ausschließen, die Sie nicht parsen möchten. Normalerweise schließen Sie Dateitypen aus, die nicht zur Benutzeroberfläche beitragen, oder Dateien, die die Benutzeroberfläche definieren, aber nicht übersetzt werden. Die Ein- und Ausschlussregeln haben das folgende Format:

```
{ /include "pattern" }
{ /exclude "pattern" }
```

Der Musterteil einer Regel wird verwendet, um mit den Namen der Dateien abzugleichen, die ein- oder ausgeschlossen werden sollen. Das Musterpräfix gibt an, ob Sie mit einem JCR-Knoten (dessen Darstellung in Vault) oder dem Dateisystem übereinstimmen.

| Präfix | Ergebnis |
|---|---|
| / | Gibt einen JCR-Pfad an. Daher gleicht dieses Präfix Dateien unter dem Verzeichnis jcr_root ab. |
| &amp;ast; | Gibt eine reguläre Datei im Dateisystem an. |
| none | Kein Präfix oder ein Muster, das mit einem Ordner oder einem Dateinamen beginnt, gibt eine reguläre Datei im Dateisystem an. |

In einem Muster steht das Zeichen / für ein Unterverzeichnis und das Zeichen &amp;ast; ist ein Platzhalter für eine beliebige Zeichenfolge. In der folgenden Tabelle sind einige Beispielregeln aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Beispielregel</th>
   <th>Ergebnis</th>
  </tr>
  <tr>
   <td><code>{ /include "*" }</code></td>
   <td>Einschließen aller Dateien.</td>
  </tr>
  <tr>
   <td><code>{ /exclude "*.pdf" }</code></td>
   <td>Ausschließen aller PDF-Dateien.</td>
  </tr>
  <tr>
   <td><code> { /exclude "*/pom.xml" }</code></td>
   <td>Ausschließen von POM-Dateien.</td>
  </tr>
  <tr>
   <td><code class="code">{ /exclude "/content/*" }
      { /include "/content/catalogs/geometrixx/templatepages" }
      { /include "/content/catalogs/geometrixx/templatepages/*" }</code></td>
   <td><p>Ausschließen aller Dateien unter dem Knoten /content.</p> <p>Den Knoten /content/catalogs/geometrixx/templatepages einbeziehen.</p> <p>Einschließen aller untergeordneten Knoten von /content/catalogs/geometrixx/templatepages.</p> </td>
  </tr>
 </tbody>
</table>

### Extrahieren der Zeichenfolgen  {#extracting-the-strings}

kein POM:

```shell
mvn -N com.adobe.granite.maven:xgettext-maven-plugin:1.2.2:extract  -Dxgettext.verbose=true -Dxgettext.target=out -Dxgettext.rules=i18n.any -Dxgettext.root=.
```

Mit POM: Fügen Sie dies zu POM hinzu:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.adobe.granite.maven</groupId>
            <artifactId>xgettext-maven-plugin</artifactId>
            <version>1.1</version>
            <configuration>
                <rules>i18n.any</rules>
                <root>jcr_root</root>
                <xliff>cq.xliff</xliff>
                <verbose>true</verbose>
            </configuration>
        </plugin>
    </plugins>
</build>
```

den Befehl:

```shell
mvn xgettext:extract
```

### Output Files {#output-files}

* `raw.xliff`: extrahierte Zeichenfolgen
* `warn.log`: Warnmeldungen (falls vorhanden), wenn die `CQ.I18n.getMessage()`-API falsch verwendet wird. In diesen Fällen ist immer eine Fehlerbehebung und anschließend eine Wiederholung erforderlich.

* `parserwarn.log`: Parser-Warnungen (falls vorhanden), z. B. js-Parser-Probleme
* `potentials.xliff`: „potenzielle“ Kandidaten, die nicht extrahiert werden, aber möglicherweise von Menschen lesbare Zeichenfolgen sind, die übersetzt werden müssen (kann ignoriert werden, da es noch eine große Menge an falsch positiven Ergebnissen findet)
* `strings.xliff`: Zusammengefasste xliff-Datei für den Import in ALF
* `backrefs.txt`: ermöglicht ein schnelles Nachschlagen der Position bestimmter Zeichenfolgen im Quell-Code
