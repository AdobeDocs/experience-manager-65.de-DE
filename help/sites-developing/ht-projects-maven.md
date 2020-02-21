---
title: Erstellen von AEM-Projekten mit Apache Maven
seo-title: Erstellen von AEM-Projekten mit Apache Maven
description: In diesem Dokument wird beschrieben, wie Sie ein AEM-Projekt einrichten, das auf Apache Maven basiert
seo-description: In diesem Dokument wird beschrieben, wie Sie ein AEM-Projekt einrichten, das auf Apache Maven basiert
uuid: 5db68639-7393-48b7-9d81-5b19b596ff21
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 3ebc1d22-a7a2-4375-9aa5-a18a7ceb446a
docset: aem65
translation-type: tm+mt
source-git-commit: 9d42526ff4c7b7d8a31690ebfb8b45d0e951ebac

---


# Erstellen von AEM-Projekten mit Apache Maven{#how-to-build-aem-projects-using-apache-maven}

## Überblick {#overview}

This document describes how to set up an AEM project based on [Apache Maven](https://maven.apache.org/).

Apache Maven ist ein Open-Source-Werkzeug für die Verwaltung von Software-Projekten, das Builds automatisiert und hochwertige Projektinformationen bereitstellt. Wir empfehlen es zur Build-Verwaltung für AEM-Projekte.

Wenn Sie Ihr AEM-Projekt mit Maven erstellen, haben Sie mehrere Vorteile:

* Eine IDE-agnostische Entwicklungsumgebung
* Verwendung von Maven-Archetypen und Artefakten, die von Adobe bereitgestellt werden
* Verwendung der Werkzeugsets Apache Sling und Apache Felix für Maven-basierte Entwicklungsumgebungen
* Einfacher Import in ein IDE, z. B. Eclipse und/oder IntelliJ
* Einfache Integration mit kontinuierlichen Integrationssystemen

### Maven-Projekt-Archetypen {#maven-project-archetypes}

Adobe stellt zwei Maven-Archetypen bereit, die als Grundlage für Ihre AEM-Projekte dienen können. Weitere Informationen finden Sie unter den folgenden Links:

* [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
* [Archetyp für Einseitige Anwendungen - Starterkit](https://github.com/adobe/aem-spa-project-archetype)

## API-Abhängigkeiten von Experience Manager {#experience-manager-api-dependencies}

### Was ist das UberJar? {#what-is-the-uberjar}

&quot;UberJar&quot;ist der informelle Name, der der speziellen Java-Archivdatei (JAR) von Adobe gegeben wird. Diese JAR-Dateien enthalten alle öffentlichen Java-APIs, die von Adobe Experience Manager bereitgestellt werden. Dazu gehören auch eingeschränkte externe Bibliotheken, insbesondere alle in AEM verfügbaren öffentlichen APIs, die von Apache Sling, Apache Jackrabbit, Apache Lucene, Google Guava stammen, und zwei Bibliotheken, die für die Bildverarbeitung verwendet werden (Werner Randelshofers CYMK JPEG ImageIO-Bibliothek und die TformerMonkeys-Bildbibliothek). Die UberJars enthalten nur API-Schnittstellen und -Klassen, d. h. sie enthalten nur Schnittstellen und Klassen, die von einem OSGi-Bundle in AEM exportiert werden. They also contain a *MANIFEST.MF* file containing the correct package export versions for all of these exported packages, thus ensuring that projects built against the UberJar have the correct package import ranges.

### Why did Adobe create the UberJars? {#why-did-adobe-create-the-uberjars}

Früher mussten Entwickler recht viele einzelne Abhängigkeiten von verschiedenen AEM-Bibliotheken verwalten. Jedes Mal, wenn sie eine neue API verwendeten, mussten sie eine oder mehrere einzelne Abhängigkeiten zum Projekt hinzufügen. Bei einem Projekt führte die Einführung des UberJar dazu, dass 30 verschiedene Abhängigkeiten aus dem Projekt entfernt werden konnten.

Ab AEM 6.5 stellt Adobe zwei UberJars bereit: eine, die veraltete Schnittstellen enthält, und eine, die diese veralteten Schnittstellen entfernt. Wenn Kunden während der Buildzeit explizit auf einen Code verweisen, werden sie sicher verstehen, ob sie von veraltetem Code abhängig sind.

Mit der zweiten Uber-Jar werden alle nicht mehr unterstützten Klassen, Methoden und Eigenschaften entfernt, damit Kunden mit ihnen kompilieren können und verstehen, ob der benutzerdefinierte Code zukünftig als Beweis dient.

### Welches UberJar sollte verwendet werden? {#which-uberjar-to-use}

AEM 6.5 ist in zwei Varianten von Uber Jar erhältlich:

1. Uber Jar - Umfasst nur die öffentlichen Schnittstellen, die nicht als veraltet markiert sind. Dies ist die **empfohlene** Verwendung von UberJar, da es die Codebasis für die Zukunft daran hindert, sich auf veraltete APIs zu verlassen.
1. Uber Jar mit veralteten APIs - Umfasst alle öffentlichen Schnittstellen, einschließlich derjenigen, die in einer zukünftigen Version von AEM als veraltet markiert wurden.

### How to I use the UberJars? {#how-to-i-use-the-uberjars}

If you are using Apache Maven as a build system (which is the case for most AEM Java projects), you will need to add one or two elements to your *pom.xml* file. The first is a *dependency* element adding the actual dependency to your project:

**Uber-Jar-Abhängigkeit *(ohne veraltete APIs)***

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

**Uber-Jar-Abhängigkeit mit veralteten APIs**

>[!CAUTION]
>
>Adobe empfiehlt die Bereitstellung mit Uber Jar, wenn **die veralteten APIs *nicht* **enthalten, um sicherzustellen, dass Ihre Anwendungen auf zukünftigen Versionen von AEM ordnungsgemäß ausgeführt werden.
>
>Verwenden Sie Uber Jar mit nicht mehr unterstützten API-Support nur, wenn der Code, der auf den veralteten APIs basiert, nicht entsprechend den Änderungen geändert werden kann.

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis-with-deprecations</classifier>
    <scope>provided</scope>
</dependency>
```

Wenn Ihr Unternehmen bereits einen Maven Repository Manager wie Sonatype Nexus, Apache Archiva oder JFrog Artifactory verwendet, fügen Sie die entsprechende Konfiguration zum Projekt hinzu, um auf diesen Repository-Manager zu verweisen, und fügen Sie das Maven-Repository von Adobe ([https://repo.adobe.com/nexus/content/groups/public/](https://repo.adobe.com/nexus/content/groups/public/)) zu Ihrem Repository-Manager hinzu.

If you are not using a repository manager, then you will need to add a *repository* element to your *pom.xml* file:

```xml
<repositories>
    <repository>
        <id>adobe-public-releases</id>
        <name>Adobe Public Repository</name>
        <url>https://repo.adobe.com/nexus/content/groups/public/</url>
        <layout>default</layout>
    </repository>
</repositories>
<pluginRepositories>
    <pluginRepository>
        <id>adobe-public-releases</id>
        <name>Adobe Public Repository</name>
        <url>https://repo.adobe.com/nexus/content/groups/public/</url>
        <layout>default</layout>
    </pluginRepository>
</pluginRepositories>
```

### Was ist mit dem UberJar möglich? {#what-can-i-do-with-the-uberjar}

Mit dem UberJar können Sie Projektcode kompilieren, der von AEM-APIs (und den APIs der oben erwähnten Projekte) abhängt. Sie können auch Informationen zu OSGi Service Component Runtime (SCR) and OSGi Metatype generieren. Mit einigen Einschränkungen können Sie auch Unit-Tests schreiben und ausführen.

### Was ist mit dem UberJar nicht möglich? {#what-can-t-i-do-with-the-uberjar}

Because the UberJar contains **only** APIs, it is not executable and cannot be used to **run** Adobe Experience Manager. Um AEM auszuführen, benötigen Sie AEM Quickstart – entweder eigenständig oder als Web Application Archive (WAR).

### Sie haben Einschränkungen zu Unit-Tests erwähnt. Erläutern Sie das bitte genauer. {#you-mentioned-limitations-on-unit-tests-please-explain-further}

Unit-Tests interagieren im Allgemeinen mit Produkt-APIs auf drei verschiedene Arten, die jeweils etwas unterschiedlich vom UberJar beeinflusst werden.

#### Anwendungsfall 1: benutzerdefinierter Code, der eine API-Schnittstelle aufruft {#use-case-custom-code-which-calls-a-api-interface}

In diesem Fall, der am häufigsten auftritt, führt benutzerdefinierter Code Methoden auf einer Java-Schnittstelle aus, die von der AEM-API definiert wird. Die Implementierung dieser Schnittstelle kann entweder direkt bereitgestellt oder mithilfe des Abhängigkeitsinjektionsmusters eingeführt werden. **Dieser Anwendungsfall kann mit dem UberJar durchgeführt werden.**

Ein Beispiel für den ersteren Fall:

```java
public class ClassWhichHasAEMInterfacePassedIn {
    /**
     * Get the first length characters of the page title.
     */
    public String getTrimmedTitle(Page page, int length) {
         String title = page.getTitle();
         return StringUtils.left(title, length);
    }
}
```

Ein Beispiel für den letzteren Fall:

```java
@Component
@Service
public class ComponentWhichHasAEMInterfaceInjected implements TitleTrimmer {
    @Reference
    private PageManagerFactory pageManagerFactory;

    /**
     * Get the first length characters of the title of the page containing the provided Resource.
     */
    public String getTrimmedTitle(Resource resource, int length) {
        PageManager pageManager = pageManagerFactory.getPageManager(resource.getResourceResolver());
        Page page = pageManager.getContainingPage(resource);
        if (page == null) {
           return null;
        }
        String title = page.getTitle();
        return StringUtils.left(title, length);
    }
}
```

To unit test either of these methods, a developer would use a mocking framework such as [JMockit](http://jmockit.github.io), [Mockito](https://mockito.org/), [JMock](https://www.jmock.org/), or [Easymock](https://easymock.org/) to create a mock object for the AEM API referenced. Diese Beispiele verwenden JMockit, aber für diesen Verwendungsfall liegt der Unterschied zwischen diesen Frameworks hauptsächlich in der Syntax.

```java
@RunWith(JMockit.class)
public class ClassWhichHasAEMInterfacePassedInTest {

    @Tested
    private ClassWhichHasAEMInterfacePassedIn instance;

    @Mocked
    private Page page;

    @Test
    public void test_that_long_string_is_trimmed() {
        new Expectations() {{
            page.getTitle();
            result = "a really really really really really long string";
        }};
        assertEquals("a really", instance.getTrimmedTitle(page, 8));
    }
}
```

```java
@RunWith(JMockit.class)
public class ComponentWhichHasAEMInterfaceInjectedTest {

    @Tested
    private ComponentWhichHasAEMInterfaceInjected instance;

    @Mocked
    private Page page;

    @Mocked
    private PageManager pageManager;

    @Injectable
    private PageManagerFactory pageManagerFactory;

    @Mocked
    private Resource resource;

    @Mocked
    private ResourceResolver resourceResolver;

    @Test
    public void test_that_long_string_is_trimmed() {
        new Expectations() {{
            resource.getResourceResolver();
            result = resourceResolver;
            pageManagerFactory.getPageManager(resourceResolver);
            result = pageManager;
            pageManager.getContainingPage(resource);
            result = page;
            page.getTitle();
            result = "a really really really really really long string";
        }};
        assertEquals("a really", instance.getTrimmedTitle(resource, 8));
    }
}
```

#### Anwendungsfall 2: benutzerdefinierter Code der eine API-Implementierungsklasse aufruft {#use-case-custom-code-which-calls-an-api-implementation-class}

Bei diesem Anwendungsfall wird ein Aufruf an eine statische oder Instanzmethode einer Klasse in der AEM-API getätigt. Dabei referenzieren Sie anders als in Anwendungsfall 1 eine konkrete Klasse.

```java
public class ClassWhichUsesAStaticMethodFromAPI {

    /**
     * Get a map of asset titles to asset objects.
     *
     * @param resource either an asset resource or a folder containing assets.
     * @return an map of titles to assets. if an asset doesn't have a title, the name is used instead.
     */
    public Map<String, Asset> getAssetTitles(Resource resource) {
        Iterator<Asset> assets = DamUtil.getAssets(resource);
        Map<String, Asset> result = new HashMap<String, Asset>();
        while (assets.hasNext()) {
            Asset asset = assets.next();
            String title = asset.getMetadataValue(DamConstants.DC_TITLE);
            if (title == null) {
                title = asset.getName();
            }
            result.put(title, asset);
        }
        return result;
    }
}
```

```java
public class ClassWhichUsesAnInstanceMethodFromAPI {

    /**
     * Count the number of paragraphs in a parsys.
     *
     * @param resource the parsys resource
     * @return the count
     */
    public int countParagraphs(Resource resource) {
        return new ParagraphSystem(resource).paragraphs().size();
    }
}
```

 **Dieser Anwendungsfall kann mit dem UberJar durchgeführt werden.** Allerdings wird ein API-Modell nach Möglichkeit dennoch empfohlen, um die Testleistung zu verbessern.

```java
@RunWith(JMockit.class)
public class ClassWhichUsesAStaticMethodFromAPITest {

    @Tested
    private ClassWhichUsesAStaticMethodFromAPI instance;

    @Mocked(stubOutClassInitialization = true)
    private DamUtil unusedDamUtil = null;

    @Mocked
    private Resource resource;

    @Test
    public void test_that_empty_iterator_produces_empty_map() {
        new Expectations() {
            {
                DamUtil.getAssets(resource);
                result = Collections.<Asset> emptySet().iterator();
            }
        };
        Map<String, Asset> result = new ClassWhichUsesAStaticMethodFromAPI().getAssetTitles(resource);
        assertNotNull(result);
        assertEquals(0, result.size());
    }
    @Test
    public void test_with_reference_search() {
        assertTrue(true);
    }
}
```

```java
@RunWith(JMockit.class)
public class ClassWhichUsesAnInstanceMethodFromAPITest {

    @Tested
    private ClassWhichUsesAnInstanceMethodFromAPI instance;

    @Mocked
    private Resource parsys;

    @Mocked
    private Paragraph firstPar;

    @Mocked
    private Paragraph secondPar;

    @Test
    public void test_empty_parsys_returns_zero() {
        new MockUp<ParagraphSystem>() {
            @Mock
            public void $init(Resource resource) {
                assertEquals(parsys, resource);
            }
            @Mock
            public List<Paragraph> paragraphs() {
                return Collections.<Paragraph> emptyList();
            }
        };
        assertEquals(0, instance.countParagraphs(parsys));
    }
}
```

#### Anwendungsfall 3 – Benutzerdefinierter Code, der eine Basisklasse aus der API erweitert {#use-case-custom-code-which-extends-a-base-class-from-the-api}

As with SCR Generation, if your code extends a base class (abstract or concrete) from the AEM API, you **must** use the UberJar in order to test it.

## Häufige Entwicklungsaufgaben mit Maven {#common-development-tasks-with-maven}

### Hinzufügen von Pfaden zum Content-Modul {#how-to-add-paths-to-the-content-module}

Das Content-Modul enthält die Datei src/main/content/META-INF/vault/filter.xml, die die Filter für das von Maven erstellte AEM-Paket definiert. Die vom Maven-Archetyp erstellte Datei sieht wie folgt aus:

#### src/main/content/META-INF/vault/filter.xml {#src-main-content-meta-inf-vault-filter-xml}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/apps/myproject"/>
</workspaceFilter>
```

Diese Datei wird auf verschiedene Arten verwendet:

* durch das `content-package-maven-plugin`, um zu bestimmen, welcher Content im Paket enthalten sein soll
* durch das VLT-Werkzeug, um zu bestimmen, welche Pfade berücksichtigt werden sollen
* Wenn das Paket in AEM Package Manager neu erstellt wird, wird dabei auch die Liste der einzubeziehenden Pfade definiert.

Abhängig von den Anforderungen Ihrer Anwendung sollten Sie weitere Pfade hinzufügen, um weitere Inhalte hinzuzufügen, z. B.:

* Rollout-Konfigurationen
* Blueprints
* Workflow-Modelle
* Design-Seiten
* Beispielinhalt

To add to the paths, add more `<filter>` elements:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/apps/myproject"/>
    <filter root="/etc/msm/rolloutconfigs/myrolloutconfig"/>
    <filter root="/etc/blueprints/mysite/globalsite"/>
    <filter root="/etc/workflow/models/myproject"/>
    <filter root="/etc/designs/myproject"/>
    <filter root="/content/myproject/sample-content"/>
</workspaceFilter>
```

#### Hinzufügen von Pfaden zum Paket ohne Synchronisierung {#adding-paths-to-the-package-without-syncing-them}

If you have files that should be added to the package that is built by the content-package-maven-plugin but that should not be synchronized between the file system and the repository, you can use `.vltignore` files. Diese Dateien haben die gleiche Syntax wie [.gitignore](https://www.kernel.org/pub/software/scm/git/docs/gitignore.html)-Dateien.

For example, the archetype uses a `.vltignore` file to prevent the JAR file that is installed as part of the bundle from being synced back to the file system:

#### src/main/content/jcr_root/apps/myproject/install/.vltignore {#src-main-content-jcr-root-apps-myproject-install-vltignore}

```xml
*.jar
```

#### Synchronisieren von Pfaden ohne Hinzufügen zum Paket {#syncing-paths-without-adding-them-to-the-package}

In einigen Fällen möchten Sie vielleicht bestimmte Pfade zwischen dem Dateisystem und dem Repository synchronisieren, aber nicht in das Paket aufnehmen, das in AEM installiert werden soll.

A typical case is the `/libs/foundation` path. For development purposes, you may want to have the contents of this path available in your file system, so that e.g. your IDE can resolve JSP inclusions that include JSPs in `/libs`. However, you don&#39;t want to include that part in the package you build, as the `/libs` part contains product code that must not be modified by custom implementations.

To achieve this, you can provide a file `src/main/content/META-INF/vault/filter-vlt.xml`. If this file exists, it will be used by the VLT tool, e.g. when you perform `vlt up` and `vlt ci`, or when you have set `vlt sync` set up. The content-package-maven-plugin will continue to use the file `src/main/content/META-INF/vault/filter.xml` when creating the package.

For example, to make `/libs/foundation` available locally for development, but only include `/apps/myproject` in the package, use the following two files.

#### src/main/content/META-INF/vault/filter.xml {#src-main-content-meta-inf-vault-filter-xml-1}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/apps/myproject"/>
</workspaceFilter>
```

#### src/main/content/META-INF/vault/filter-vlt.xml {#src-main-content-meta-inf-vault-filter-vlt-xml}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/libs/foundation"/>
    <filter root="/apps/myproject"/>
</workspaceFilter>
```

Außerdem müssen Sie das maven-resources-plugin neu konfigurieren, damit diese Dateien nicht in das Paket eingebunden werden – die filter.xml-Datei wird nicht angewendet, wenn das Paket installiert ist, sondern nur, wenn das Paket erneut mit dem Package Manager erstellt wird.

Change the `<resources>` section in the content pom accoringly:

#### src/main/content/pom.xml {#src-main-content-pom-xml}

```xml
<!-- ... -->
<resources>
 <resource>
  <directory>src/main/content/jcr_root</directory>
  <filtering>false</filtering>
  <excludes>
   <exclude>**/.vlt</exclude>
   <exclude>**/.vltignore</exclude>
   <exclude>libs/</exclude>
  </excludes>
 </resource>
</resources>
<!-- ... -->
```

### Arbeiten mit JSPs {#how-to-work-with-jsps}

Bei der bisher beschriebenen Maven-Einrichtung wird ein Inhaltspaket erstellt, das auch Komponenten und ihre entsprechenden JSPs enthalten kann. Allerdings behandelt Maven sie wie jede andere Datei, die zum Inhaltspaket gehört, und erkennt sie nicht einmal als JSPs.

Die resultierenden Komponenten funktionieren dennoch in AEM, aber es hat zwei große Vorteile, Maven auf die JSPs hinzuweisen:

* Maven kann fehlschlagen, wenn die JSPs Fehler enthalten, sodass diese während des Builds und nicht erst beim ersten Kompilieren in AEM entdeckt werden
* Für IDEs, die Maven-Projekte importieren können, werden außerdem Codevervollständigung und Unterstützung für Tag-Bibliotheken in den JSPs ermöglicht

Zwei Schritte sind hierfür erforderlich:

1. Tag-Bibliotheks-Abhängigkeiten hinzufügen
1. Die JSPs im Rahmen des Maven-Kompilierungsvorgangs kompilieren

#### Hinzufügen von Tag-Bibliotheks-Abhängigkeiten {#adding-tag-library-dependencies}

Below dependencies need to be added to the `content` modules&#39;s POM.

>[!NOTE]
>
>Unless you are importing the product dependencies as described in [Importing AEM Product Dependencies](#importingaemproductdependencies) above, they also need to be added to the parent POM along with the version matching your AEM setup as described in [Adding Dependencies](#addingdependencies) above. Die Kommentare in jedem folgenden Eintrag zeigen das Paket, nach dem Sie in der Abhängigkeitssuche suchen müssen.

>[!NOTE]
>
>Das `com.adobe.granite.xssprotection`-Artefakt ist nicht im POM cq-quickstart-product-dependencies enthalten und benötigt vollständige Maven-Koordinaten, die Sie in der Abhängigkeitssuche erhalten.

#### Kompilierung von JSPs während der Maven-Kompilierungsphase {#compiling-jsps-as-part-of-the-maven-compile-phase}

To compile JSPs in Maven&#39;s `compile` phase, we use Apache Sling&#39;s [Maven JspC Plugin](https://sling.apache.org/documentation/development/jspc.html) as shown below:

* we set up an execution for the `jspc` goal (which by default binds to the `compile` phase, so we don&#39;t need to specify the phase explicitly)

* we tell it to compile any JSPs in `${project.build.directory}/jsps-to-compile`
* and output the result to `${project.build.directory}/ignoredjspc` (which translates to `myproject/content/target/ignoredjspc`)

* we set up maven-resources-plugin to copy the JSPs to `${project.build.directory}/jsps-to-compile` in the generate-sources phase and configure it to not copy the `libs/` folder (because that is AEM product code and we neither want to incur the dependencies for compilation for our project, nor do we need to validate that it compiles.

Unser Hauptziel besteht darin, wie oben beschrieben, die JSPs zu validieren und sicherzustellen, dass der Build-Vorgang fehlschlägt, wenn sie Fehler enthalten. Daher kompilieren wir sie in einem separaten Verzeichnis, das ignoriert wird (und sofort anschließend gelöscht wird, wie Sie in einem Moment sehen werden).

Das Ergebnis des Maven-JspC-Plug-ins kann auch als Teil eines OSGi-Pakets gebündelt und bereitgestellt werden, aber dies hat andere Auswirkungen und Nebeneffekte und geht über unser Ziel der Validierung der JSPs hinaus.

Um die aus den JSPs kompilierten Klassen zu löschen, richten wir das Maven-Clean-Plug-in wie unten gezeigt ein. If you want to inspect the result of the Maven JspC Plugin, run `mvn compile` in `myproject/content` -- after that, you will find the result in `myproject/content/target/ignoredjspc`).

#### myproject/content/pom.xml {#myproject-content-pom-xml}

```xml
<build>
  <!-- ... -->
  <plugins>
    <!-- ... -->
    <plugin>
      <artifactId>maven-resources-plugin</artifactId>
      <executions>
        <execution>
          <id>copy-resources</id>
          <phase>generate-sources</phase>
          <goals>
            <goal>copy-resources</goal>
          </goals>
          <configuration>
            <outputDirectory>${project.build.directory}/jsps-to-compile</outputDirectory>
            <resources>
              <resource>
                <directory>src/main/content/jcr_root</directory>
                <excludes>
                  <exclude>libs/**</exclude>
                </excludes>
              </resource>
            </resources>
          </configuration>
        </execution>
      </executions>
    </plugin>
    <plugin>
      <groupId>org.apache.sling</groupId>
      <artifactId>maven-jspc-plugin</artifactId>
      <version>2.0.6</version>
      <executions>
        <execution>
          <id>compile-jsp</id>
          <goals>
            <goal>jspc</goal>
          </goals>
          <configuration>
            <jasperClassDebugInfo>false</jasperClassDebugInfo>
            <sourceDirectory>${project.build.directory}/jsps-to-compile</sourceDirectory>
            <outputDirectory>${project.build.directory}/ignoredjspc</outputDirectory>
          </configuration>
        </execution>
      </executions>
    </plugin>
    <plugin>
      <artifactId>maven-clean-plugin</artifactId>
      <executions>
        <execution>
          <id>remove-compiled-jsps</id>
          <goals>
            <goal>clean</goal>
          </goals>
          <phase>process-classes</phase>
          <configuration>
            <excludeDefaultDirectories>true</excludeDefaultDirectories>
            <filesets>
              <fileset>
                <directory>${project.build.directory}/jsps-to-compile</directory>
                <directory>${project.build.directory}/ignoredjspc</directory>
              </fileset>
            </filesets>
          </configuration>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

>[!NOTE]
>
>Depending on whether you actually make use of JSP code in `/libs` (i.e. include JSPs from there), you will need to refine which JSPs are copied for compilation.
>
>E.g. if you include `/libs/foundation/global.jsp`, you can use the following configuration for the `maven-resources-plugin` instead of the configuration above which completely skips over `/libs`.
>
>
```
> <resource>  
>           <directory>src/main/content/jcr_root</directory>  
>           <includes>  
>                   <include>apps/**</include>  
>                   <include>libs/foundation/global.jsp</include>
>       </includes>  
>   </resource>  
>```

### Arbeit mit SCM-Systemen {#how-to-work-with-scm-systems}

Beim Arbeiten mit Quellkonfigurationsmanagement (SCM) sollten Sie Folgendes sicherstellen:

* Das VCS ignoriert Nichtquellartefakte im Dateisystem
* VLT ignoriert Artefakte des VCS und checkt sie nicht in das Repository ein

>[!NOTE]
>
>In dieser Beschreibung wird die Konfiguration von Maven für Kompatibilität mit Ihrem SCM nicht erläutert. Dies wird ausführlich in der [Maven-POM-Referenz](https://maven.apache.org/pom.html#SCM) und der [Dokumentation zum Maven-SCM-Plug-in](https://maven.apache.org/scm/) erläutert.

#### Von SCM auszuschließende Muster {#patterns-to-exclude-from-scm}

Hier ist eine typische Liste der Muster, die aus SCM ausgeschlossen werden sollten. E.g., if you are using git, you can add these to your project&#39;s `.gitignore` file.

#### .gitignore-Beispiel{#sample-gitignore}

```shell
# Ignore VLT files
.vlt
.vlt-sync.log
.vlt-sync-config.properties

# Ignore Quickstart launches in the source tree
license.properties
crx-quickstart

# Ignore compilation results
target

# Ignore IDE and Operating System artifacts
.idea
.classpath
.metadata
.project
.settings
maven-eclipse.xml
*.iml
*.ipr
*.iws
.DS_Store
```

#### Ignorieren von SCM-Steuerdateien in VLT {#ignoring-scm-control-files-in-vlt}

In einigen Fällen haben Sie möglicherweise SCM-Steuerdateien in der Content-Quellbaumstruktur, die nicht in das Repository eingecheckt werden sollen.

Betrachten Sie die folgende Situation:

Der Archetyp hat bereits eine .vltignore-Datei erstellt, um zu verhindern, dass die installierte Bundle-jar-Datei wieder mit dem Dateisystem synchronisiert wird:

#### src/main/content/jcr_root/apps/myproject/install/.vltignore {#src-main-content-jcr-root-apps-myproject-install-vltignore-1}

```shell
*.jar
```

Selbstverständlich möchten Sie diese Datei auch nicht in Ihrem SCM haben. Wenn Sie also z. B. git verwenden, müssen Sie eine entsprechende `gitignore` file:

#### src/main/content/jcr_root/apps/myproject/install/.gitignore {#src-main-content-jcr-root-apps-myproject-install-gitignore}

```shell
*.jar
```

Da die . `gitignore`-Datei auch nicht zum Repository hinzugefügt werden soll, muss die . `vltignore`-Datei erweitert werden, um die . `gitignore` file:

#### src/main/content/jcr_root/apps/myproject/install/.vltignore {#src-main-content-jcr-root-apps-myproject-install-vltignore-2}

```shell
*.jar
.gitignore
```

### Arbeit mit Bereitstellungsprofilen {#how-to-work-with-deployment-profiles}

Wenn Ihr Build-Vorgang ein Teil eines umfassenden Entwicklungslebenszyklus-Managements ist, z. B. eines kontinuierlichen Integrationsvorgangs, müssen Sie oft Bereitstellungen auf anderen Geräten durchführen als nur auf der lokalen Instanz des Entwicklers.

In solchen Fällen können Sie dem POM des Projekts einfach neue [Maven-Build-Profile](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) hinzufügen.

Im folgenden Beispiel wird ein Profil-`integrationServer` hinzugefügt, der die Hostnamen und Ports für die Autoren- und Veröffentlichungsinstanzen neu definiert. Sie können auf diese Server bereitstellen, indem Sie Maven wie unten gezeigt im Hauptverzeichnis des Projekts ausführen.

```shell
# install on integration test author
$ mvn -PautoInstallPackage -PintegrationServer install

# install on integration test publisher
$ mvn -PautoInstallPackagePublish -PintegrationServer install
```

#### myproject/pom.xml {#myproject-pom-xml}

```xml
<profiles>

    <!-- ... -->

    <profile>
        <id>integrationServer</id>
        <properties>
            <crx.host>dev-author.intranet</crx.host>
            <crx.port>5502</crx.port>
            <publish.crx.host>dev-publish.intranet</publish.crx.host>
            <publish.crx.port>5503</publish.crx.port>
        </properties>
    </profile>
</profiles>
```

### Arbeit mit AEM Communities {#how-to-work-with-aem-communities}

Bei einer Lizenzierung für Kompatibilität mit AEM Communities ist ein zusätzliches API-jar erforderlich.

Weitere Details finden Sie unter [Verwendung von Maven für Communities](/help/communities/maven.md)
