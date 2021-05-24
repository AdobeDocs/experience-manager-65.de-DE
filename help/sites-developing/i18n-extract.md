---
title: Extrahieren von Zeichenfolgen zur Übersetzung
seo-title: Extrahieren von Zeichenfolgen zur Übersetzung
description: Verwenden Sie xgettext-maven-plugin, um Zeichenfolgen, die übersetzt werden müssen, aus Ihrem Quellcode zu extrahieren
seo-description: Verwenden Sie xgettext-maven-plugin, um Zeichenfolgen, die übersetzt werden müssen, aus Ihrem Quellcode zu extrahieren
uuid: 2c586ecb-8494-4f8f-b31a-1ed73644d611
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
discoiquuid: 034f70f1-fbd2-4f6b-b07a-5758f0461a5b
exl-id: 4acc5f7f-0bcb-4b5a-8531-52e146cffeae
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 71%

---

# Extrahieren von Zeichenfolgen zur Übersetzung{#extracting-strings-for-translating}

Verwenden Sie xgettext-maven-plugin, um Zeichenfolgen, die übersetzt werden müssen, aus Ihrem Quellcode zu extrahieren. Das Maven-Plug-in extrahiert Zeichenfolgen in eine XLIFF-Datei, die Sie zur Übersetzung senden. Zeichenfolgen werden aus den folgenden Quellen extrahiert:

* Java-Quelldateien
* JavaScript-Quelldateien
* XML-Darstellungen von SVN-Ressourcen (JCR-Knoten)

## Konfiguration der Zeichenfolgen-Extraktion  {#configuring-string-extraction}

Konfigurieren Sie, wie xgettext-maven-plugin Zeichenfolgen für Ihr Projekt extrahiert.

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
| /parsers/vaultxml | Konfiguriert das Parsen von Vault-Dateien. Gibt die JCR-Knoten an, die externalisierte Zeichenfolgen und Lokalisierungshinweise enthalten. Gibt außerdem JCR-Knoten an, die ignoriert werden sollen. |
| /parsers/javascript | Identifiziert die JavaScript-Funktionen, die Zeichenfolgen externalisieren. Sie müssen diesen Abschnitt nicht ändern. |
| /parsers/regexp | Konfiguriert das Parsen von Java-, JSP- und ExtJS-Vorlagendateien. Sie müssen diesen Abschnitt nicht ändern. |
| /potentials | Die Formel zur Erkennung von Zeichenfolgen, die internationalisiert werden sollen. |

### Bestimmung der zu parsenden Dateien {#identifying-the-files-to-parse}

Der /filter-Abschnitt der Datei i18n.any gibt die Datei an, die xgettext-maven-plugin parst. Fügen Sie mehrere ein- und ausschließende Regeln hinzu, um Dateien anzugeben, die geparst bzw. ignoriert werden sollen. Sie sollten alle Dateien einbeziehen und dann die Dateien ausschließen, die Sie nicht parsen möchten. Normalerweise sollten Dateitypen ausgeschlossen werden, die nicht Teil der Benutzeroberfläche sind oder die die Benutzeroberfläche definieren, jedoch nicht übersetzt werden. Die ein- und ausschließenden Regeln haben das folgende Format:

```
{ /include "pattern" }
{ /exclude "pattern" }
```

Das Muster einer Regel wird verwendet, um die Namen der Dateien abzugleichen, die ein- bzw. ausgeschlossen werden sollen. Das Musterpräfix gibt an, ob Sie einen JCR-Knoten (seine Darstellung in Vault) oder das Dateisystem abgleichen.

| Präfix | Ergebnis |
|---|---|
| / | Gibt einen JCR-Pfad an. Daher gleicht dieses Präfix Dateien unter dem Verzeichnis jcr_root ab. |
| &amp;ast; | Gibt eine reguläre Datei im Dateisystem an. |
| keine | Kein Präfix oder ein Muster, das mit einem Ordner oder Dateinamen beginnt, zeigt eine reguläre Datei im Dateisystem an. |

Wenn es in einem Muster verwendet wird, zeigt das Zeichen / ein Unterverzeichnis und das Zeichen &amp;ast an. entspricht allen Zeichen. In der folgenden Tabelle sind einige Beispielregeln aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Beispielregel</th>
   <th>Ergebnis</th>
  </tr>
  <tr>
   <td><code>{ /include "*" }</code></td>
   <td>Schließen Sie alle Dateien ein.</td>
  </tr>
  <tr>
   <td><code>{ /exclude "*.pdf" }</code></td>
   <td>Schließen Sie alle PDF-Dateien aus.</td>
  </tr>
  <tr>
   <td><code> { /exclude "*/pom.xml" }</code></td>
   <td>Ausschluss von POM-Dateien.</td>
  </tr>
  <tr>
   <td><code class="code">{ /exclude "/content/*" }
      { /include "/content/catalogs/geometrixx/templatepages" }
      { /include "/content/catalogs/geometrixx/templatepages/*" }</code></td>
   <td><p>Schließen Sie alle Dateien unter dem Knoten /content aus.</p> <p>Schließen Sie den Knoten /content/catalogs/geometrixx/templatepages ein.</p> <p>Schließen Sie alle untergeordneten Knoten von /content/catalogs/geometrixx/templatepages ein.</p> </td>
  </tr>
 </tbody>
</table>

### Extrahieren der Zeichenfolgen  {#extracting-the-strings}

Kein POM:

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

der Befehl:

```shell
mvn xgettext:extract
```

### Ausgabedateien {#output-files}

* `raw.xliff`: extrahierte Zeichenfolgen
* `warn.log`: (falls vorhanden), wenn die  `CQ.I18n.getMessage()` API falsch verwendet wird. In diesen Fällen ist immer eine Fehlerbehebung und anschließend eine Wiederholung erforderlich.

* `parserwarn.log`: Parser-Warnungen (falls vorhanden), z. B. js-Parserprobleme
* `potentials.xliff`: „potenzielle“ Kandidaten, die nicht extrahiert werden, aber möglicherweise von Menschen lesbare Zeichenfolgen sind, die übersetzt werden müssen (kann ignoriert werden, da es noch eine große Menge an falsch positiven Ergebnissen findet)
* `strings.xliff`: Zusammengefasste xliff-Datei für den Import in ALF
* `backrefs.txt`: ermöglicht ein schnelles Nachschlagen der Position bestimmter Zeichenfolgen im Quellcode
