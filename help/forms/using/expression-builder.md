---
title: Remote-Funktionen im Ausdrucksgenerator
description: Mit dem Ausdrucksgenerator in Correspondence Management können Sie Ausdrücke und Remote-Funktionen erstellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: b41af9fe-c698-44b3-9ac6-97d42cdc02d4
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 44%

---

# Remote-Funktionen im Ausdrucksgenerator{#remote-functions-in-expression-builder}

Mithilfe des Ausdrucksgenerators können Sie Ausdrücke oder Bedingungen erstellen, die Berechnungen mit Datenwerten durchführen, die vom Datenwörterbuch oder von Endbenutzern bereitgestellt werden. Correspondence Management nutzt das Ergebnis der Ausdrucksberechnung, um Assets wie Text, Bilder, Listen und Bedingungen auszuwählen und sie nach Bedarf in der Korrespondenz einzufügen.

## Erstellen von Ausdrücken und Remote-Funktionen mit dem Ausdrucksgenerator {#creating-expressions-and-remote-functions-with-expression-builder}

Der Ausdrucksgenerator verwendet intern JSP EL-Bibliotheken, damit der Ausdruck die JSPEL-Syntax einhält. Weitere Informationen finden Sie unter [Beispielausdrücke](#exampleexpressions).

![Ausdrucksgenerator](assets/expressionbuilder.png)

### Operatoren  {#operators}

Die Operatoren, die zur Verwendung in Ausdrücken verfügbar sind, sind in der oberen Leiste des Ausdruckseditors verfügbar.

### Beispielausdrücke {#exampleexpressions}

Im Folgenden finden Sie einige häufig verwendete JSP EL-Beispiele, die Sie in Ihrer Correspondence Management-Lösung verwenden können:

* Addieren zweier Zahlen: ${number1 + number2}
* Verketten zweier Zeichenketten: ${str1} ${str2}
* Vergleichen zwei Zahlen: ${age &lt; 18}

Weitere Informationen finden Sie in der [JSP-EL-Spezifikation](https://download.oracle.com/otn-pub/jcp/jsp-2.1-fr-spec-oth-JSpec/jsp-2_1-fr-spec-el.pdf). Der Client-seitige Expression Manager unterstützt nicht alle Variablen und Funktionen in der JSP-EL-Spezifikation. Dabei gilt:

* Sammlungsindizes und Zuordnungsschlüssel (bei Verwendung der []-Schreibweise) werden in Variablennamen für Ausdrücke, die Client-seitig ausgewertet werden, nicht unterstützt.
* Die folgenden Parameter sind als Parametertypen oder Rückgabetypen für in Ausdrücken verwendete Funktionen unterstützt:

   * java.lang.String
   * java.lang.Character
   * Char
   * java.lang.Boolean
   * Boolesch
   * java.lang.Integer
   * Int
   * java.util.list
   * java.lang.Short
   * Short
   * java.lang.Byte
   * byte
   * java.lang.Double
   * Double
   * java.lang.Long
   * Long
   * java.lang.Float
   * Fließkommazahl
   * java.util.Calendar
   * java.util.Date
   * java.util.List

### Remote-Funktion {#remote-function}

Remote-Funktionen bieten die Möglichkeit, benutzerdefinierte Logik in Ausdrücken zu verwenden. Sie können benutzerdefinierte Logik schreiben, die in Ausdrücken als Methode in Java verwendet wird. Dieselbe Funktion kann innerhalb von Ausdrücken verwendet werden. Verfügbare Remote-Funktionen werden unter der Registerkarte „Remote-Funktionen“ auf der linken Seite des Ausdruckseditors aufgelistet.

![Remote-Funktion](assets/remotefunction.png)

#### Benutzerdefinierte Remote-Funktionen hinzufügen {#adding-custom-remote-functions}

Sie können ein benutzerdefiniertes Bundle erstellen, um Ihre eigenen Remote-Funktionen zur Verwendung in Ausdrücken zu exportieren. Um ein benutzerdefiniertes Bundle zum Exportieren Ihrer eigenen Remote-Funktionen zu erstellen, führen Sie die folgenden Aufgaben aus. Es wird gezeigt, wie eine benutzerdefinierte Funktion geschrieben wird, die ihre Eingabezeichenfolge großschreibt.

1. Definieren Sie eine Schnittstelle für den OSGi-Dienst mit Methoden, die zur Verwendung durch Expression Manager exportiert werden.
1. Deklarieren Sie Methoden in der Schnittstelle A und versehen Sie sie mit der Anmerkung „@ServiceMethod“ (com.adobe.exm.expeval.ServiceMethod). Expression Manager ignoriert alle Methoden, bei denen keine Anmerkungen vorhanden sind. Die ServiceMethod-Anmerkung verfügt über die folgenden optionalen Attribute, die ebenfalls festgelegt werden können:

   1. **Aktiviert**: Bestimmt, ob diese Methode aktiviert ist. Expression Manager ignoriert deaktivierte Methoden.
   1. **familyId**: Gibt die Familie (Gruppe) der Methode an. Wenn dieses Feld leer ist, geht Expression Manager davon aus, dass die Methode zur Standardfamilie gehört. Es gibt keine Register der Familien (außer der Standardfamilie), aus denen Funktionen ausgewählt werden. Expression Manager erstellt die Registrierung dynamisch, indem es eine Vereinigung aller Familien-IDs verwendet, die von allen von den verschiedenen Bundles exportierten Funktionen angegeben werden. Stellen Sie sicher, dass die hier angegebene ID angemessen lesbar ist, da sie auch in der Authoring-Benutzeroberfläche für Ausdrücke angezeigt wird.
   1. **displayName**: Ein für Menschen lesbarer Name für die Funktion. Dieser Name wird für Anzeigezwecke in der Authoring-Benutzeroberfläche verwendet. Wenn dieses Feld leer ist, erstellt Expression Manager einen Standardnamen mithilfe des Präfixes und des lokalen Namens der Funktion.
   1. **Beschreibung**: Eine ausführliche Beschreibung der Funktion. Diese Beschreibung wird für Anzeigezwecke in der Authoring-Benutzeroberfläche verwendet. Wenn leer, erstellt Expression Manager eine Standardbeschreibung mit dem Präfix und dem lokalen Namen der Funktion.

   ```java
   package mergeandfuse.com;
   import com.adobe.exm.expeval.ServiceMethod;
   
   public interface RemoteFunction {
    @ServiceMethod(enabled=true,displayName="Returns_all_caps",description="Function to convert to all CAPS", familyId="remote")
    public String toAllCaps(String name);
   
   }
   ```

   Die Parameter der Methoden können ebenfalls mit Anmerkungen versehen werden (optional). Verwenden Sie hierfür die Anmerkung „@ServiceMethodParameter“ (com.adobe.exm.expeval.ServiceMethodParameter). Diese Anmerkung wird nur zur Angabe von für Menschen lesbaren Namen und Beschreibungen von Methodenparametern verwendet, die in der Authoring-Benutzeroberfläche verwendet werden können. Stellen Sie sicher, dass die Parameter und Rückgabewerte der Schnittstellenmethoden zu einem der folgenden Typen gehören:

   * java.lang.String
   * java.lang.Character
   * Char
   * java.lang.Boolean
   * Boolesch
   * java.lang.Integer
   * Int
   * java.lang.Short
   * Short
   * java.lang.Byte
   * byte
   * java.lang.Double
   * Double
   * java.lang.Long
   * Long
   * java.lang.Float
   * Fließkommazahl
   * java.util.Calendar
   * java.util.Date
   * java.util.List

1. Definieren Sie die Implementierung der Schnittstelle, konfigurieren Sie sie als OSGI-Service und definieren Sie die folgenden Service-Eigenschaften:

```jsp
@org.apache.felix.scr.annotations.Properties({
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker", boolValue = true),
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker.alias", value = "<service_id>"),
  @org.apache.felix.scr.annotations.Property(name = "exm.service", boolValue = true)})
```

Der Eintrag exm.service=true weist Expression Manager an, dass der Dienst Remote-Funktionen enthält, die für die Verwendung in Ausdrücken geeignet sind. Die &lt;service_id> -Wert muss eine gültige Java-Kennung sein (alphanumerisch,$, _ ohne weitere Sonderzeichen). Dieser Wert, dem das Schlüsselwort REMOTE_ vorangestellt ist, bildet das Präfix, das in Ausdrücken verwendet wird. Beispielsweise kann eine Schnittstelle mit einer kommentierten Methode bar() und der Dienst-ID-foo in den Diensteigenschaften in Ausdrücken mithilfe von REMOTE_foo:bar() referenziert werden.

```java
package mergeandfuse.com;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

@Component(metatype = true, immediate = true, label = "RemoteFunctionImpl")
@Service(value = RemoteFunction.class)
@org.apache.felix.scr.annotations.Properties({
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker", boolValue = true),
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker.alias", value = "test1"),
  @org.apache.felix.scr.annotations.Property(name = "exm.service", boolValue = true)})
public class RemoteFuntionImpl implements RemoteFunction {

 @Override
 public String toAllCaps(String name) {
  System.out.println("######Got######"+name);
  
  return name.toUpperCase();
 }
 
}
```

Im Folgenden finden Sie Beispiel-Archive, die verwendet werden sollen:

* **GoodFunctions.jar.zip** ist die JAR-Datei mit Bundle, die eine Definition für eine Muster-Remote-Funktion enthält. Laden Sie die GoodFunctions.jar.zip-Datei herunter und dekomprimieren Sie diese, um die JAR-Datei zu erhalten.
* **GoodFunctions.zip** ist das Paket des Quellcodes zum Definieren einer benutzerdefinierten Remote-Funktion und eines Bundles dafür.

GoodFunctions.jar.zip

[Datei laden](assets/goodfunctions.jar.zip)

GoodFunctions.zip

[Datei laden](assets/goodfunctions.zip)
