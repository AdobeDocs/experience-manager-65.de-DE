---
title: C2PA-[!DNL Experience Manager Assets]
description: Erfahren Sie, wie [!DNL Experience Manager Assets] C2PA-Metadaten in hochgeladenen Assets erkennt, in der Benutzeroberfläche kennzeichnet und die von ihr generierten Ausgabedarstellungen für Gen-AI-Assets signiert.
role: User, Admin, Developer
feature: Asset Management, Metadata, Renditions, Workflow, Asset Processing
solution: Experience Manager, Experience Manager Assets
source-git-commit: f47205896ed512deadb4d31acbfe0fafa18515e7
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 6%
---

# C2PA-Metadaten in [!DNL Experience Manager Assets] {#c2pa-metadata}

Marken machen sich mehr denn je Gedanken um die Transparenz von Inhalten, die Offenlegung von KI und die Verhinderung der Manipulation von Assets. Die Content Authenticity Initiative (CAI) von Adobe erstellt Tools, die mit dem technischen Standard der [Coalition for Content Provenance and Authenticity](https://c2pa.org/specifications/specifications/2.2/specs/C2PA_Specification.html) (C2PA) konform sind. C2PA-Metadaten, eine neue Art manipulationssicherer Metadaten, helfen Betrachtern, die Herkunft von Inhalten zu verstehen und die Integrität von Marken-Assets sicherzustellen. Sie können eine breite Palette von Herkunftsdaten enthalten, die Einblicke in den Verlauf eines digitalen Assets bieten.

Hierzu gehört Folgendes:

* **Aussteller oder Unterzeichner:** Informationen über die Entität oder das Unternehmen, die bzw. das die digitale Signatur für das Asset ausgestellt hat.
* **Anfragedatum:** Das Datum, an dem die C2PA-Metadaten auf das Asset angewendet wurden.
* **Verlauf:** Die Dokumentation aller Bearbeitungen oder Änderungen, die am Asset vorgenommen wurden.
* **Gerätedetails:** Informationen über die App oder das Gerät, mit der bzw. dem das Asset erstellt oder bearbeitet wurde.
* **Verwendetes KI-Tool:** Wenn generative KI zum Bearbeiten oder Erstellen des Assets verwendet wurde, wird der Name des verwendeten Modells einbezogen.
* **Weitere relevante Informationen:** Zusätzliche Daten, die mehr Kontext über den Verlauf eines Assets bieten.

Weitere Informationen zum Verlauf eines Assets finden Sie unter [Überprüfen](https://contentcredentials.org/verify).

[!DNL Adobe Experience Manager Assets] erkennt C2PA-Metadaten beim Hochladen oder Aktualisieren eines Assets, kennzeichnet diese Assets in der [!DNL Assets]-Benutzeroberfläche und erhält die Gen-KI-Offenlegung in den von [!DNL Experience Manager] generierten Ausgabedarstellungen intakt. Jedes Mal, wenn [!DNL Experience Manager] eine Ausgabedarstellung eines Gen-AI-Assets erstellt oder ändert, z. B. eine Miniaturansicht, eine Web-Ausgabedarstellung, eine Kopie mit Wasserzeichen oder einen Videotranscode, signiert [!DNL Experience Manager] diese Ausgabedarstellung mit einer neuen C2PA-Metadaten, die auf das Original-Asset als übergeordnetes Element verweist. Ausgabedarstellungen, die Sie herunterladen, veröffentlichen oder freigeben, behalten ihre Herkunft bei.

## Voraussetzungen {#Prerequisites}

Für die Unterstützung von C2PA-Metadaten ist [!DNL Adobe Experience Manager] 6.5 Service Pack erforderlich. Installieren Sie auf Service Pack 6.5.25.0 den [AEM 6.5 SP25 - C2PA GenAI-Kompatibilitäts-Hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-ASSETS-75868-SP25-1.0.zip).

## Unterstützte Formate und Plattformen {#supported-formats}

### Formate {#formats}

[!DNL Experience Manager] signiert Ausgabedarstellungen in den Formaten, die [C2PA-Spezifikation](https://c2pa.org/specifications/specifications/2.2/specs/C2PA_Specification.html) für eingebettete Manifeste unterstützt.

| Typ | Formate | MIME-Typen |
|---|---|---|
| Bild | JPEG, PNG, GIF, TIFF, DNG, WebP, JPEG XL, AVIF, HEIC/HEIF, SVG | `image/jpeg`, `image/png`, `image/gif`, `image/tiff`, `image/x-adobe-dng`, `image/webp`, `image/jxl`, `image/avif`, `image/heic`, `image/heif`, `image/svg+xml` |
| Video | MP4, MOV, AVI | `video/mp4`, `video/quicktime`, `video/x-msvideo` |
| Audio | MP3, M4A, WAV, FLAC | `audio/mpeg`, `audio/mp4`, `audio/wav`, `audio/flac` |

[!DNL Experience Manager] erkennt auch allgemeine Aliase wie `image/jpg`, `image/pjpeg`, `image/x-png` und `video/mov`. [!DNL Experience Manager] prüft jedes hochgeladene Asset auf ein Manifest, unabhängig vom Dateiformat. Ausgabedarstellungen in anderen Formaten wie PSD oder EPS sind nicht signiert.

### Plattformen {#platforms}

Die Unterstützung von C2PA-Metadaten beruht auf einer nativen C2PA-Komponente, die im `cq-dam-core`-Bundle enthalten ist, mit einem Build für jede unterstützte Plattform. Beim Starten des Services extrahiert [!DNL Experience Manager] den Build für Ihre Plattform (`adobe_c2patool` oder `adobe_c2patool.exe` unter Windows) in den privaten Datenordner des Bundles, prüft die SHA-256-Prüfsumme und führt sie als separaten Prozess aus. Sie müssen nichts installieren oder `PATH` ändern.

| Betriebssystem | Architektur |
|---|---|
| Linux (glibc 2.28 oder höher, einschließlich Red Hat Enterprise Linux 8) | `x86_64`, `aarch64` |
| macOS | `x86_64`, `aarch64` (Apple-Chip) |
| Windows | `x86_64` |

Dies funktioniert bei [!DNL Adobe Managed Services]- und On-Premise-Bereitstellungen genauso. Stellen Sie sicher, dass der [!DNL Experience Manager] diese ausführbare Datei starten kann. Wenn Sie `noexec`-Bereitstellungen, Antivirenprogramme oder Endpunkt-Sicherheitssoftware verwenden, lassen Sie die Ausführung von `adobe_c2patool` über den `crx-quickstart`-Ordner zu. Andernfalls kann die Unterstützung von C2PA-Metadaten nicht gestartet werden.

## Funktionsweise von C2PA-Metadaten {#how-c2pa-metadata-works}

Die C2PA-Metadatenunterstützung besteht aus zwei Teilen: Erkennung, wann ein Asset hochgeladen oder aktualisiert wird, und erneutes Signieren, wenn [!DNL Experience Manager] eine Ausgabedarstellung generiert oder ändert.

### Workflow-Konfiguration {#workflow}

Der **[!UICONTROL C2PA-Anmeldeinformationen erkennen]** unter [C2PA-Metadaten erkennen](#detect) ist Teil des standardmäßigen **[!UICONTROL DAM Update Asset]**-Workflow-Modells. Wenn Sie eine benutzerdefinierte Kopie dieses Modells verwenden, fügen Sie den Schritt selbst hinzu:

1. Navigieren Sie auf der [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** und öffnen Sie Ihr Modell im ![Bearbeiten-Symbol](assets/edit.svg)**[!UICONTROL Bearbeiten]** Modus.
1. Fügen Sie den Schritt **[!UICONTROL C2PA-Anmeldeinformationen erkennen]** nach **[!UICONTROL Metadatenprozessor]** hinzu, bevor ein Schritt die Ausgabedarstellungen generiert.
1. Wählen Sie **[!UICONTROL Synchronisieren]** aus, um das Modell zu speichern.

Ausgabedarstellungsschritte signieren ihre Ausgabe nur, wenn die Erkennung für das Asset bereits ausgeführt wurde. Wenn sie von der Erkennung verfolgt werden, bleiben ihre Ausgabedarstellungen unsigniert, bis der Workflow erneut ausgeführt wird.

### Erkennen von C2PA-Metadaten {#detect}

Der **[!UICONTROL DAM Update Asset]**-Workflow enthält den Schritt **[!UICONTROL C2PA-Anmeldeinformationen erkennen]** der nach dem Schritt **[!UICONTROL Metadatenprozessor]** ausgeführt wird, wie in der folgenden Abbildung dargestellt. Er liest die ursprüngliche Binärdatei des Assets und zeichnet das Ergebnis im Metadatenknoten `jcr:content/metadata` des Assets auf.

![Workflow](assets/workflow.png)

In der folgenden Tabelle sind die wichtigsten Metadateneigenschaften im C2PA-Metadaten-Workflow aufgeführt.

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| `dam:hasC2PAManifest` | `boolean` | `true`, wenn die ursprüngliche Binärdatei ein eingebettetes C2PA-Manifest hat. Es wird immer geschrieben. |
| `dam:isAiGenerated` | `boolean` | `true`, wenn das Manifest das Asset in den Gültigkeitsbereich für die Kennzeichnung mit Gen-AI einbezieht. Es wird nur geschrieben, wenn ein Manifest vorhanden ist. |
| `dam:c2paValidationState` | `string` | Sie beschreibt den Validierungsstatus des Manifests: `TRUSTED`, `VALID`, `INVALID` oder `UNKNOWN`. Es wird nur geschrieben, wenn ein Manifest vorhanden ist. |

Wenn ein Manifest vorhanden ist, speichert [!DNL Experience Manager] es auch als `c2pa-manifest.json` (`application/json`).

Wenn Sie das ursprüngliche Asset durch eine Binärdatei ohne Manifest ersetzen, wird bei der nächsten Workflow-Ausführung `dam:hasC2PAManifest` auf `false` gesetzt und `dam:isAiGenerated`, `dam:c2paValidationState` und die `c2pa-manifest.json` Ausgabedarstellung werden entfernt.

>[!NOTE]
>
>Ein Erkennungsfehler blockiert nie die Erfassung eines Assets. Wenn beim Lesen des Manifests eine Zeitüberschreitung auftritt oder ein Fehler auftritt, protokolliert [!DNL Experience Manager] den Fehler, lässt die Metadaten unverändert und fährt mit dem Rest des Workflows fort.

### Anzeigen von C2PA-Metadaten in der [!DNL Assets]-Benutzeroberfläche {#view-c2pa-metadata}

Assets, die C2PA-Metadaten enthalten, zeigen in **Benutzeroberfläche von [!DNL Assets] das Badge** cr (C2PA-Metadaten) an. Navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]** und suchen Sie nach dem Abzeichen in der linken unteren Ecke von:

* Die Miniaturansicht des Assets in **[!UICONTROL Kartenansicht]**.
* Die Asset-Miniaturansicht in **[!UICONTROL Spaltenansicht]**. Wählen Sie das Asset aus, um seine Miniaturansicht anzuzeigen.
* Der Vorschaubereich der Asset-Detailseite.

Das **cr**-Badge, das in der folgenden Abbildung angezeigt wird, gibt an, ob ein Asset C2PA-Metadaten enthält. Das Manifest selbst wird nicht angezeigt. Um das vollständige Manifest anzuzeigen, laden Sie das Asset herunter und öffnen Sie es in [Überprüfen](https://contentcredentials.org/verify).

![CR-Badge](assets/cr.png)

[!DNL Experience Manager] speichert das erkannte Manifest als `c2pa-manifest.json` Ausgabedarstellung im Asset. Dieses Ausgabeformat ist intern. Sie wird nicht im Bedienfeld **[!UICONTROL Ausgabedarstellungen]** der Seite mit Asset-Details oder in der Ausgabedarstellungsauswahl angezeigt.

### Signieren von Ausgabedarstellungen {#sign-renditions}

Eine Ausgabedarstellung ist eine neue Binärdatei, sodass das im ursprünglichen Asset eingebettete Manifest sie nicht abdeckt. Um die Gen-AI-Offenlegung intakt zu halten, signiert [!DNL Experience Manager] jede geeignete Ausgabedarstellung als letzten Schritt des Prozesses, der sie erzeugt. Die neuen C2PA-Metadaten:

* Verweist auf das ursprüngliche Asset als seine **übergeordnete** Zutat.
* Zeichnet auf, wie die Ausgabedarstellung vom ursprünglichen Asset abgeleitet wurde, und zwar als eine der C2PA-Aktionen `c2pa.resized`, `c2pa.transcoded` oder `c2pa.edited`.
* `Adobe Experience Manager` als Software-Agent.

[!DNL Experience Manager] signiert eine Ausgabedarstellung nur, wenn Folgendes `true` ist:

* Für das Quell-Asset `dam:isAiGenerated` &quot;`true`&quot; festgelegt. Assets, die ein Manifest enthalten, aber nicht über KI generiert werden, weisen weiterhin das **cr**-Badge auf, [!DNL Experience Manager] ihre Ausgabedarstellungen jedoch nicht erneut signieren.
* Das Quellmanifest ist lesbar und sein Validierungsstatus ist nicht `INVALID`. [!DNL Experience Manager] verkettet nie eine neue Signatur in einem Manifest, dessen Validierung fehlgeschlagen ist, z. B. nachdem das Asset manipuliert wurde.
* Das Ausgabeformat unterstützt ein eingebettetes C2PA-Manifest. Weitere Informationen finden Sie unter [Unterstützte Formate](#supported-formats). [!DNL Experience Manager] überspringt die nicht unterstützten Formate fehlerfrei.

Die folgenden Schritte des Workflows **[!UICONTROL DAM-Update-Asset abgeschlossen]** Workflow, der unter &quot;[&#x200B; von C2PA-Metadaten“ angezeigt wird](#detect) signieren ihre Ausgabe.

| Workflow-Schritt | Signierte Ausgabedarstellungen | C2PA-Aktion aufgezeichnet |
|---|---|---|
| **[!UICONTROL Miniaturansichten verarbeiten]** | Miniaturansicht-Ausgabedarstellungen und das Web-fähige Bild. | `c2pa.resized` und `c2pa.transcoded`, wenn sich das Format ändert |
| **[!UICONTROL EPS-Miniaturansichten (unterstützt von ImageMagick)]** | Primäre Ausgabe, abgeleitete Miniaturen und Web-Ausgabedarstellungen. | `c2pa.resized`, `c2pa.transcoded`, oder `c2pa.edited` |
| **[!UICONTROL FFmpeg-Miniaturen]** | Video Poster Frames und Miniaturansichten. | `c2pa.resized` und `c2pa.transcoded` |
| **[!UICONTROL FFmpeg-Transkodierung]** | Videokodierungen | `c2pa.transcoded` |
| **[!UICONTROL Rastern der PDF-/AI-Bildvorschau-Ausgabedarstellung]** | Vorschau der Ausgabedarstellung anzeigen. (`cqdam.preview.png`) | `c2pa.transcoded` |

Die folgenden Workflow-Prozesse signieren ihre Ausgabe auch, wenn Sie sie im Workflow **[!UICONTROL DAM-Update-Asset abgeschlossen]**, in einem anderen Workflow oder in einem benutzerdefinierten Workflow-Modell verwenden. Wählen Sie sie in der **[!UICONTROL Miniaturansichten verarbeiten]** der Liste eines Workflow-Schritts aus, wie in [Erkennen von C2PA-Metadaten“ &#x200B;](#detect).

| Workflow-Prozess | Signierte Ausgabedarstellungen | C2PA-Aktion aufgezeichnet |
|---|---|---|
| **[!UICONTROL Miniaturansicht erstellen]** | Ausgabedarstellungen von Miniaturen. | `c2pa.resized` und `c2pa.transcoded`, wenn sich das Format ändert |
| **[!UICONTROL Web-fähiges Bild erstellen]** | Web-Ausgabedarstellungen | `c2pa.resized` und `c2pa.transcoded`, wenn sich das Format ändert |
| **[!UICONTROL Befehlszeile]** z. B. mit [!DNL ImageMagick] | Primäre Ausgabe, abgeleitete Miniaturen und Web-Ausgabedarstellungen. | `c2pa.resized`, `c2pa.transcoded`, oder `c2pa.edited` |
| **[!UICONTROL Bild-Wasserzeichenprozess]** | Mit Wasserzeichen versehene Ausgabedarstellung oder die ursprüngliche Ausgabedarstellung, wenn ein Wasserzeichen vorhanden ist. Weitere Informationen finden Sie unter [Wasserzeichen für Assets](/help/assets/watermarking.md). | `c2pa.edited` |
| **[!UICONTROL Video-Storyboard erstellen]** | Storyboard-Schlüsselbilder. | `c2pa.transcoded` |
| **[!UICONTROL XMP-Writeback]** | Die ursprüngliche Ausgabedarstellung, nachdem die Metadaten zurückgeschrieben wurden. Weitere Informationen finden Sie unter [XMP-Writeback in Ausgabedarstellungen](/help/assets/xmp-writeback.md). | `c2pa.edited` |

### Schützen der Originalbinärdatei während des XMP-Writebacks {#xmp-writeback}

XMP Writeback schreibt die Originalbinärdatei neu, wodurch das eingebettete Manifest unterbrochen wird. Bei Assets mit `dam:hasC2PAManifest`, die auf `true` eingestellt sind, ändert [!DNL Experience Manager] das Verhalten des Schritts **[!UICONTROL XMP-Writeback]** des Workflows **[!UICONTROL DAM]** Metadaten-Writeback) wie folgt:

* **Gen-KI** Assets (`dam:isAiGenerated` ist `true`): [!DNL Experience Manager] schreibt die XMP und signiert dann die Originalbinärdatei erneut, wobei die Pre-Writeback-Binärdatei das übergeordnete Element ist. Dadurch werden das Writeback und die neue Signatur zusammen gespeichert. Wenn das erneute Signieren fehlschlägt, werden sowohl als auch der Schritt verworfen.
* **Andere Assets, die ein Manifest enthalten**: [!DNL Experience Manager] überspringt das XMP-Writeback und protokolliert den Grund. Die ursprüngliche Binärdatei und ihr Manifest bleiben unverändert.

### Signiermodus {#signing-mode}

[!DNL Experience Manager] signiert Ausgabedarstellungen lokal auf der Instanz, die sie erzeugt, mit einem flüchtigen, selbstsignierten Zertifikat, das es selbst generiert. Für das Signieren ist kein Netzwerkzugriff und kein Zertifikat oder keine Konfiguration des privaten Schlüssels erforderlich.

>[!NOTE]
>
>Sie können kein eigenes Signaturzertifikat konfigurieren. Validatoren wie [Überprüfen](https://contentcredentials.org/verify) zeigen die Gen-AI-Offenlegung der Ausgabedarstellung und den Link zum Original an, identifizieren Ihr Unternehmen jedoch nicht als Unterzeichner.

## Konfigurieren von C2PA-Metadaten {#configure}

Die Unterstützung von C2PA-Metadaten ist standardmäßig aktiviert. Sie müssen nichts installieren oder konfigurieren.

### OSGi-Konfiguration {#osgi-configuration}

Um die Standardkonfiguration zu ändern, konfigurieren Sie den **[!UICONTROL Day CQ DAM C2PA Service]** (PID `com.day.cq.dam.core.impl.c2pa.C2PAServiceImpl`) in Configuration Manager unter `https://[aem_server]:[port]/system/console/configMgr`wie in der folgenden Abbildung dargestellt, oder fügen Sie Ihrem Projekt eine OSGi-Konfiguration hinzu. Weitere Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

![OSGi-Konfiguration](assets/OSGi.png)

In der folgenden Tabelle sind die Eigenschaften in der OSGi-Konfiguration Ihres Projekts aufgeführt.

| Eigenschaft | Name in Configuration Manager | Standard | Beschreibung |
|---|---|---|---|
| `enabled` | **[!UICONTROL Aktiviert]** | `true` | Schaltet die Unterstützung von C2PA-Metadaten ein oder aus. Wenn diese Option deaktiviert ist, erkennt [!DNL Experience Manager] keine Manifeste und signiert keine Ausgabedarstellungen. |
| `timeoutMillis` | **[!UICONTROL CLI-Zeitüberschreitung (ms)]** | `30000` | Gibt die maximale Zeit in Millisekunden an, die [!DNL Experience Manager] auf einen einzelnen Lese- oder Signiervorgang für eine Datei warten, bevor sie als Zeitüberschreitung behandelt wird. Erhöhen Sie diesen Wert für große Video- oder hochauflösende Bilddateien. |

Fügen Sie beispielsweise eine OSGi-Konfiguration unter `/apps/<your-project>/config/com.day.cq.dam.core.impl.c2pa.C2PAServiceImpl.config` hinzu.

```text
enabled=B"true"
timeoutMillis=L"60000"
```

### Deaktivieren der Unterstützung von C2PA-Metadaten {#disable}

Deaktivieren Sie in der **[!UICONTROL Day CQ DAM C2PA Service]**-Konfiguration, die unter [OSGi-](#osgi-configuration) angezeigt wird, die Option **[!UICONTROL Aktiviert]** und speichern Sie dann die Änderungen. Die Änderung wird sofort ohne Neustart wirksam:

* Der **[!UICONTROL C2PA-Anmeldeinformationen erkennen]** unter [C2PA-Metadaten erkennen](#detect) wird nicht mehr funktionsfähig.
* Mit Workflow-Schritten werden Ausgabedarstellungen erstellt, ohne sie zu signieren.
* Bereits verarbeitete Assets behalten ihre `dam:hasC2PAManifest` Eigenschaft und zeigen weiterhin das **cr**-Badge.

>[!CAUTION]
>
>Nach dem Deaktivieren der **[!UICONTROL Aktiviert]**-Option enthalten Ausgabedarstellungen von Gen-AI-Assets keine C2PA-Metadaten. Wenn Sie die Offenlegungsvorschriften der Gen AI einhalten möchten, aktivieren Sie die Option **[!UICONTROL Aktiviert]**.

## Anpassen der Verarbeitungs-Pipeline {#customize}

Gehen Sie wie folgt vor, um Schritte in **[!UICONTROL DAM Update Asset]** hinzuzufügen, zu entfernen oder neu anzuordnen und die Gen AI-Offenlegung weiterhin intakt zu halten:

* **Erkennung zuerst ausführen.** Halten Sie **[!UICONTROL C2PA-Berechtigung erkennen]** vor jedem Schritt, der die Ausgabedarstellungen erstellt oder ändert.
* **Letzte unterschreiben.** Jede Änderung an einer Binärdatei nach dem Signieren macht ihre Signatur ungültig. Führen Sie keine Schritte aus, die eine Ausgabedarstellung nach dem Schritt ändern, mit dem sie signiert wurde.
* **Verwenden Sie Schritte, die signieren.** Die in „Ausgabedarstellungen signieren“ aufgelisteten integrierten [&#x200B; signieren &#x200B;](#sign-renditions) Ausgabe. Benutzerdefinierte Schritte und Drittanbieter-Tools, die Sie mit etwas anderem als dem **[!UICONTROL Befehlszeilen]**-Prozess ausführen, signieren ihre Ausgabe nur, wenn das Signieren explizit hinzugefügt wird. Weitere Informationen finden Sie unter [Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows](/help/assets/media-handlers.md).
* **Ändern Sie das Original nicht an Ort und Stelle** es sei denn, der Schritt signiert es erneut, wie dies bei **[!UICONTROL XMP Writeback]** und **[!UICONTROL Image Watermarking Process]** der Fall ist.

### Signieren von Ausgabedarstellungen aus einem benutzerdefinierten Workflow-Schritt {#custom-step}

Benutzerdefinierte Workflow-Schritte, die Ausgabedarstellungen erzeugen, können diese über den `com.day.cq.dam.api.c2pa.C2PASigner` OSGi-Dienst signieren. Es wendet dieselben Eignungsregeln wie die integrierten Schritte an, meldet jedoch stattdessen das Ergebnis als `C2PASigningOutcome`.

```java
import java.util.Collections;

import org.osgi.service.component.annotations.Reference;
import org.osgi.service.component.annotations.ReferenceCardinality;
import org.osgi.service.component.annotations.ReferencePolicy;

import com.day.cq.dam.api.Asset;
import com.day.cq.dam.api.Rendition;
import com.day.cq.dam.api.c2pa.C2PAAction;
import com.day.cq.dam.api.c2pa.C2PAConstants;
import com.day.cq.dam.api.c2pa.C2PASigner;
import com.day.cq.dam.api.c2pa.C2PASigningOutcome;

// Inside your WorkflowProcess implementation:

@Reference(cardinality = ReferenceCardinality.OPTIONAL, policy = ReferencePolicy.DYNAMIC)
private volatile C2PASigner c2paSigner;

private void signRendition(Asset asset, Rendition rendition) {
    C2PASigner signer = c2paSigner;
    if (signer == null) {
        return;
    }
    C2PASigningOutcome outcome = signer.signIfEligible(asset, rendition,
            Collections.singletonList(
                    new C2PAAction(C2PAConstants.ACTION_RESIZED, C2PAConstants.SOFTWARE_AGENT, null)));
    if (outcome == C2PASigningOutcome.FAILED) {
        // Log, retry, or alert an operator.
    }
}
```

Rufen Sie `signIfEligible` erst auf, nachdem Ihr Schritt das Schreiben der Ausgabedarstellung abgeschlossen hat. Der OSGi-Service stellt die Methoden bereit, wie in der folgenden Tabelle aufgeführt.

| Methode | Verwenden Sie ihn, um |
|---|---|
| `signIfEligible(Asset, Rendition, List<C2PAAction>)` | Signieren Sie eine neue Ausgabedarstellung, wobei das Quell-Asset das übergeordnete Element ist. |
| `signIfEligible(Asset, Map<Rendition, List<C2PAAction>>)` | Signieren Sie mehrere Ausgabedarstellungen, die von demselben Asset abgeleitet sind. Diese Methode liest das Quellmanifest einmal. |
| `captureResignState(Asset)` | Nehmen Sie ein Bild des ursprünglichen Assets auf, bevor Sie es durch Ihren Schritt an Ort und Stelle ändern. Diese Methode gibt `null` zurück, wenn das Asset nicht geeignet ist. |
| `resign(Asset, Rendition, List<C2PAAction>)` | Signieren Sie das ursprüngliche Asset nach einer Änderung an Ort und Stelle erneut, wobei das Bild das übergeordnete Bild ist. |
| `discardResignState(Rendition)` | Platzieren Sie ein Bild, das Sie aufgenommen haben, aber nicht verwendet werden soll, z. B. weil Ihre Änderung fehlgeschlagen ist. |

Die Werte von `C2PASigningOutcome` sind in der folgenden Tabelle aufgeführt.

| Ergebnis | Beschreibung |
|---|---|
| `SIGNED` | [!DNL Experience Manager] hat die Ausgabedarstellung signiert. |
| `SKIPPED_SOURCE_NOT_AI_GENERATED` | Das Quell-Asset wird nicht als von KI generiertes Asset gekennzeichnet. |
| `SKIPPED_FORMAT_NOT_ELIGIBLE` | Das Format der Ausgabedarstellung unterstützt das eingebettete C2PA-Manifest nicht. |
| `SKIPPED_MANIFEST_UNREADABLE` | [!DNL Experience Manager] hat kein Manifest im Quell-Asset gefunden. |
| `SKIPPED_MANIFEST_NOT_VALID` | Die Validierung des Quellmanifests ist fehlgeschlagen. |
| `SKIPPED_SERVICE_UNAVAILABLE` | Die Unterstützung von C2PA-Metadaten ist deaktiviert oder nicht verfügbar. |
| `FAILED` | Das Lesen des Quellmanifests oder das Signieren der Ausgabedarstellung ist fehlgeschlagen. |

Um die Eignung zu überprüfen, bevor Sie eine teure Ausgabedarstellung erstellen, rufen Sie `C2PASupportedFormats.isEligible(...)` auf.

## Fehlerbehebung {#troubleshooting}

Legen Sie bei der Fehlerbehebung die folgenden Logger in der **[!UICONTROL Apache Sling Logging Logger-Konfiguration“ auf `DEBUG`]**.

* `com.day.cq.dam.core.impl.c2pa`: Extrahieren der nativen C2PA-Komponente, Lesen von Manifesten und Signieren.
* `com.day.cq.dam.core.process.DetectC2PACredentialProcess`: Erkennung.

| Symptom | Mögliche Ursache | Auflösung |
|---|---|---|
| Kein Asset zeigt das Abzeichen **cr**. | Die Unterstützung von C2PA-Metadaten ist deaktiviert oder Ihr Workflow-Modell umfasst den Erkennungsschritt nicht. | Überprüfen Sie, ob **[!UICONTROL Aktiviert]** in der Konfiguration **[!UICONTROL Day CQ DAM C2PA Service]** aktiviert ist und Ihr **[!UICONTROL DAM Update Asset]**-Modell **[!UICONTROL Detect C2PA Credential]**. |
| Ein bekanntes Asset hat ein Manifest, zeigt jedoch kein Abzeichen an. | Das Asset wurde hochgeladen, bevor die Funktion verfügbar war. | Führen Sie den **[!UICONTROL DAM Update Asset]** für das Asset erneut aus, z. B. über **[!UICONTROL Zeitleiste]** > **[!UICONTROL Workflow starten]**. |
| Der Dienst wird nicht gestartet. Das Fehlerprotokoll meldet, dass `adobe_c2patool` nicht extrahiert oder als ausführbar markiert werden können. | Für das Betriebssystem oder die Architektur ist keine Binärdatei vorhanden, oder das Dateisystem blockiert die ausführbaren Dateien. | Verwenden Sie eine unterstützte Plattform. Der [!DNL Experience Manager]-Prozess kann die ausführbaren Dateien von seinem `crx-quickstart` Ordner aus ausführen. |
| Das Fehlerprotokoll meldet `GLIBC_2.xx not found`. | Der Linux-Host führt eine glibc-Version älter als 2.28 aus. | Aktualisieren Sie das Host-Betriebssystem. |
| Zeitüberschreitung bei Erkennung oder Signierung. | Große Dateien benötigen länger als die standardmäßige 30-Sekunden-Zeitüberschreitung. | Erhöhen Sie **[!UICONTROL CLI-Zeitüberschreitung (ms)]**. |
| Die Ausgabedarstellungen eines Gen-KI-Assets sind nicht signiert. | Das Format wird nicht unterstützt, das Manifest ist `INVALID` oder die Erkennung wurde nach dem Schritt der Ausgabedarstellung ausgeführt. | Überprüfen Sie `dam:c2paValidationState` und das Format der Ausgabedarstellung. Verschieben Sie **[!UICONTROL C2PA-Berechtigung erkennen]** vor den Schritten zur Ausgabedarstellung. |
| XMP-Writeback aktualisiert kein Asset. | Das Asset enthält ein Manifest, wird jedoch nicht über KI generiert, sodass [!DNL Experience Manager] das Original unverändert lässt. | Dies ist ein erwartetes Verhalten. Weitere Informationen finden Sie unter [Schützen des Originals während des XMP-Writebacks](#xmp-writeback). |

## Einschränkungen {#limitations}

* Die [!DNL Assets] Benutzeroberfläche zeigt nur an, ob C2PA-Metadaten vorhanden sind. Es gibt kein Bedienfeld für die Manifestdetails.
* [!DNL Experience Manager] signiert Ausgabedarstellungen nur für Assets erneut, die über KI generiert wurden. Ausgabedarstellungen anderer Assets, die ein Manifest enthalten, werden ohne C2PA-Metadaten erstellt.
* [!DNL Experience Manager] Zeichen mit einem flüchtigen, selbstsignierten Zertifikat. Benutzerdefinierte oder organisationsspezifische Signaturzertifikate werden nicht unterstützt.


>[!MORELIKETHIS]
>
>* [C2PA-Metadaten in der Assets-Ansicht von [!DNL Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/c2pa-metadata-assets-view)
>* [C2PA-Metadaten in [!DNL Experience Manager Assets Essentials]](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/content-credentials)
>* [C2PA-Metadaten in [!DNL Dynamic Media]](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/c2pa-metadata)
>* [XMP-Writeback in Ausgabedarstellungen](/help/assets/xmp-writeback.md)
>* [Wasserzeichen für Assets](/help/assets/watermarking.md)
>* [Content Authenticity Initiative](https://contentauthenticity.org/)
>* [Überprüfen](https://contentcredentials.org/verify)
