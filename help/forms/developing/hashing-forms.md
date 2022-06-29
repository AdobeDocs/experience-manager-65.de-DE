---
title: Wie lassen sich Hashes in dynamischen PDF-Formularen erzeugen und verwenden?
description: Erzeugen und Verwenden von Hashes in dynamischen PDF-Formularen
exl-id: 026f5686-39ea-4798-9d1f-031f15941060
source-git-commit: de38dbb9d0ce523543c11e665c02034f4b38f1e6
workflow-type: ht
source-wordcount: '1256'
ht-degree: 100%

---

# Erzeugen und Verwenden von Hashes in dynamischen PDF-Formularen {#generate-work-with-hashes-dynamic-pdf-forms}


## Vorausgesetztes Wissen {#prerequisite-knowledge}

Einige Erfahrung mit AEM Forms on JEE Designer ist erforderlich, ebenso wie die Fähigkeit, auf Funktionen in Skriptobjekten zuzugreifen und diese aufzurufen.

## Benutzerebene {#user-level}

Anfang

Wenn Sie ein Kennwort in Ihrem PDF-Formular verstecken möchten und es nicht im Quell-Code oder an einer anderen Stelle im PDF-Dokument als Klartext enthalten sein soll, ist es wichtig zu wissen, wie MD4-, MD5-, SHA-1- und SHA-256-Hashes erzeugt werden können und funktionieren.

Ziel ist es, das Kennwort zu verschleiern, indem ein eindeutiger Hash erzeugt und dieser Hash im PDF-Dokument gespeichert wird. Dieser einzigartige Hash kann von verschiedenen Hash-Funktionen erzeugt werden, und in diesem Artikel werde ich Ihnen zeigen, wie man sie innerhalb des PDF-Formulars erzeugt und wie man mit ihnen arbeitet.

Eine Hash-Funktion akzeptiert eine lange Zeichenfolge (oder Nachricht) beliebiger Länge als Eingabe und erzeugt eine Zeichenfolge mit fester Länge als Ausgabe, manchmal auch als Nachrichten-Digest oder digitaler Fingerabdruck bezeichnet.

Mit AEM Forms on JEE Designer können Sie die verschiedenen Hash-Funktionen als JavaScript in Skriptobjekte implementieren und innerhalb eines dynamischen PDF-Dokuments ausführen. Die Beispiel-PDFs, die in den Beispieldateien für diesen Artikel enthalten sind, verwenden Open-Source-Implementierungen der folgenden Hash-Funktionen:

* MD4 und MD5 – von Ronald Rivest entworfen

* SHA-1 und SHA-256 – wie von NIST definiert

Der größte Vorteil der Verwendung von Hashes besteht darin, dass Sie Kennwörter nicht direkt durch Vergleich klarer Textzeichenfolgen vergleichen müssen. Sie können stattdessen die beiden Hashes der beiden Kennwörter vergleichen. Da es sehr unwahrscheinlich ist, dass zwei verschiedene Zeichenfolgen denselben Hash aufweisen, können Sie bei beiden Hashes davon ausgehen, dass auch die verglichenen Zeichenfolgen (in diesem Fall die Kennwörter) identisch sind.

>[!NOTE]
>
>Es gibt einige bekannte Sicherheitsprobleme (so genannte Hash-Kollisionen) mit MD4 oder MD5. Aufgrund dieser Hash-Kollisionen und anderer SHA-1-Hacks (einschließlich Regenbogentabellen) beschloss ich, mich auf die SHA-256-Hash-Funktion im zweiten Beispiel zu konzentrieren.  Weitere Informationen finden Sie auf den Wikipedia-Seiten [Kollision](https://de.wikipedia.org/wiki/Hashkollision) und [Regenbogentabelle](https://de.wikipedia.org/wiki/Rainbow_Table).

## Überprüfen der Skriptobjekte {#examining-script-objects}

Wenn Sie eines der beiden angegebenen Beispiele in AEM Forms on JEE Designer öffnen, finden Sie die vier Skriptobjekte in der Palette „Hierarchie“ (siehe Abbildung unten).

![Variablen](assets/variables.jpg)

Um die JavaScript-Implementierung der Hash-Funktionen in diesen Skriptobjekten anzuzeigen, wählen Sie das Skriptobjekt aus und suchen Sie im Skript-Editor nach dem Code.  Sie können sehen, wie die folgenden Hash-Funktionen implementiert wurden:

* soHASHING_MD4.hex_md4()
* soHASHING_MD4.b64_md4()
* soHASHING_MD4.str_md4()
* soHASHING_MD5.hex_md5()
* soHASHING_MD5.b64_md5()
* soHASHING_MD5.str_md5()
* soHASHING_SHA1.hex_sha1()
* soHASHING_SHA1.b64_sha1( )
* soHASHING_SHA1.str_sha1( )
* soHASHING_SHA256.hex_sha256()
* soHASHING_SHA256.b64_sha256()
* soHASHING_SHA256.str_sha256()

Wie Sie aus dieser Liste sehen können, gibt es verschiedene Funktionen für die verschiedenen Ausgabetypen des Hash. Sie können zwischen `hex_` für Hexadezimalziffern, `b64_` für Base64-codierte Ausgabe und `str_` für einfache Zeichenfolgen-Codierung wählen.

Je nach ausgewählter Hash-Funktion variiert die Länge des Hash:

* MD4: 128 Bits
* MD5: 128 Bits
* SHA-1: 160 Bit
* SHA-256: 256 Bit

## Ausprobieren der PDF-Beispielformulare {#try-sample-pdf-forms}

Die Beispieldateien für diesen Artikel enthalten zwei PDF-Formulare. Im ersten Beispiel können Sie eine Zeichenfolge eingeben und dann MD4-, MD5-, SHA-1- und SHA-256-Hash-Werte für die Zeichenfolge generieren.  Das zweite Beispiel ist ein einfaches Formular, auf dem Textfelder entsperrt werden, wenn das korrekte Kennwort eingegeben wird.

### Beispiel 1: Generieren von Hash-Werten {#generating-dashes}

Gehen Sie wie folgt vor, um das erste Beispiel auszuprobieren:

1. Öffnen Sie nach dem Herunterladen und Entpacken der Beispieldateien die Datei „hashing_forms_sample1.pdf“ mit AEM Forms on JEE Designer. Stattdessen können Sie auch Adobe Reader oder Adobe Acrobat Professional verwenden, um das Beispiel zu öffnen und anzuzeigen. Allerdings können Sie dann den Quellcode nicht sehen.
1. Geben Sie im Textfeld mit der Beschriftung [!UICONTROL Klartext] ein Passwort oder eine andere Nachricht ein, für die Sie einen Hash-Wert generieren möchten.
1. Klicken Sie auf eine der vier Schaltflächen, um den MD4-, MD5-, SHA-1- oder SHA-256-Hash-Wert zu generieren. Je nachdem, auf welche Schaltfläche Sie geklickt haben, wird eine der vier Hash-Funktionen aufgerufen, die eine hexadezimale Ausgabe erzeugen, und Ihre Zeichenfolge oder Nachricht wird in einen Hash-Wert umgewandelt.

Das Ergebnis des Hash-Vorgangs wird im Feld mit der Bezeichnung [!UICONTROL Hash] angezeigt. Die Länge des Hash-Werts hängt von der gewählten Hash-Funktion ab.

In allen Beispielen werden Hexadezimalziffern als Ausgabetyp verwendet. Mit dem Skript-Editor können Sie die Beispiele ändern und den Ausgabetyp in Base64 oder eine einfache Zeichenfolge ändern.

### Beispiel 2: Abgleichen von Kennwörtern {#matching-passwords}

Das zweite Beispiel zeigt, wie Hash-Werte im Hintergrund verglichen werden, ohne das richtige Kennwort offenlegen zu müssen. Das von Ihnen eingegebene Kennwort wird in einen Hash-Wert umgewandelt. Das echte Kennwort, das in einem unsichtbaren Feld gespeichert ist, wird ebenfalls in einen Hash-Wert umgewandelt. Das Kennwort ist sicher, weil es in einen Hash-Wert umgewandelt wurde, nicht weil es unsichtbar ist. Da sich das Kennwort aus dem Hash-Wert nicht rekonstruieren lässt, ist es sicher, das Kennwort in Hash-Form anzuzeigen. Es werden nur die Hash-Werte und nicht die Kennwörter in Klartext verglichen. Wenn die beiden Hash-Werte identisch sind, können Sie davon ausgehen, dass die Kennwörter identisch sind.

Gehen Sie wie folgt vor, um das zweite Beispiel auszuprobieren:

1. Öffnen Sie `hashing_forms_sample2.pdf` mit AEM Forms on JEE Designer. Stattdessen können Sie auch Adobe Reader oder Adobe Acrobat Professional verwenden, um das Beispiel zu öffnen und anzuzeigen. Allerdings können Sie dann den Quellcode nicht sehen.
1. Wählen Sie eines der beiden Kennwortfelder mit der Beschriftung [!UICONTROL Password MAN] oder [!UICONTROL Password FRAU] und geben Sie die Kennwörter ein:
   1. Das Kennwort für den Mann lautet `bob`
   1. Das Kennwort für die Frau lautet `alice`
1. Wenn Sie den Fokus aus den Kennwortfeldern verschieben oder die Eingabetaste drücken, wird automatisch der Hash-Wert des eingegebenen Kennworts generiert und im Hintergrund mit dem gespeicherten Hash-Wert des richtigen Kennworts verglichen. Die richtigen, in Hash-Werte umgewandelten Kennwörter werden in unsichtbaren Textfeldern mit der Beschriftung `passwd_man_hashed` und `passwd_woman_hashed` gespeichert. Wenn Sie das richtige Kennwort für den Mann eingeben, dann werden die Textfelder mit der Beschriftung `Man 1` und `Man 2` verfügbar, sodass Sie Text eingeben können. Dasselbe Verhalten gilt für die Felder für das Kennwort der Frau.
1. Optional können Sie auf die Schaltfläche mit der Bezeichnung „Kennwörter löschen“ klicken, um die Textfelder zu deaktivieren und ihren Rahmen zu ändern.

Der Code zum Vergleichen der beiden Hash-Werte und zum Aktivieren der Textfelder ist einfach:

```xml
if (soHASHING_SHA256.hex_sha256(this.rawValue) == passwd_man_hashed.rawValue){
     VAL_man_1.access = "open";
     VAL_man_2.access = "open";
     VAL_man_1.borderColor = "0,255,0";
     VAL_man_2.borderColor = "0,255,0";
}
```

## Wie geht es jetzt weiter? {#next-steps}

Wo brauchen Sie so etwas? Stellen Sie sich ein PDF-Formular vor, das Felder enthält, die nur von autorisierten Personen ausgefüllt werden sollten. Durch das Schützen dieser Felder mit einem Kennwort, das wie im Beispielformular „Sample_2.pdf“ nirgends im Dokument im Klartext zu sehen ist, können Sie sicherstellen, dass diese Felder nur für Benutzer zugänglich sind, die das Kennwort kennen.

Ich empfehle Ihnen, die beiden PDF-Beispieldateien weiter zu studieren.  Sie können mit der Beispieldatei „Sample_1.pdf“ neue Hash-Werte generieren und die generierten Werte verwenden, um entweder das Kennwort oder die Hash-Funktion zu ändern, die in „Sample_2.pdf“ verwendet wird.  Die im Abschnitt „Zuschreibungen“ aufgelisteten Ressourcen enthalten auch zusätzliche Informationen zum Hashing und zu den spezifischen JavaScript-Implementierungen, die in diesem Artikel verwendet werden.

## Zuschreibungen {#attributions}

* [Ronald Rivest](https://de.wikipedia.org/wiki/Ronald_L._Rivest)
* [NIST](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)
* [Hash-Kollision](https://de.wikipedia.org/wiki/Hashkollision)
* [Regenbogentabelle](https://de.wikipedia.org/wiki/Rainbow_Table)
* [Startseite des JavaScript-MD5-Projekts](http://pajhome.org.uk/crypt/md5/)
* [jsSHA2-Projekt-Startseite](https://anmar.eu.org/projects/jssha2/)
