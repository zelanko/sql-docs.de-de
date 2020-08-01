---
title: Schema.ini Datei (Text Datei Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema.ini file [ODBC]
- text file driver [ODBC], schema.ini file
ms.assetid: 0c4625c4-c730-4984-b430-9051b7bc0451
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed041e43a211f58a34b4e2476d9e0b62ff5d162b
ms.sourcegitcommit: 039fb38c583019b3fd06894160568387a19ba04e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87442884"
---
# <a name="schemaini-file-text-file-driver"></a>Datei „Schema.ini“ (Textdateitreiber)
Wenn der Text Treiber verwendet wird, wird das Format der Textdatei mithilfe einer Schema Informationsdatei festgelegt. Die Schema Informationsdatei wird immer Schema.ini benannt und immer im gleichen Verzeichnis wie die Text Datenquelle gespeichert. Die Schema Informationsdatei stellt dem IISAM Informationen über das allgemeine Format der Datei, den Spaltennamen und Datentyp Informationen sowie verschiedene weitere Daten Merkmale bereit. Für den Zugriff auf Daten mit fester Länge ist immer eine Schema.ini Datei erforderlich. Sie sollten eine Schema.ini Datei verwenden, wenn die Text Tabelle DateTime-, Currency-oder decimal-Daten enthält, oder wenn Sie eine bessere Kontrolle über die Verarbeitung der Daten in der Tabelle wünschen.  
  
> [!NOTE]  
>  Der Text-ISAM erhält Anfangswerte aus der Registrierung und nicht aus Schema.ini. Das gleiche Standarddatei Format gilt für alle neuen Text Datentabellen. Alle Dateien, die von der CREATE TABLE-Anweisung erstellt wurden, erben dieselben Standardformat Werte. Diese werden festgelegt, indem die Dateiformat Werte im Dialogfeld **Text Format definieren** \<default> ausgewählt und in der Liste **Tabellen** ausgewählt werden. Wenn sich die Werte in der Registrierung von den Werten in Schema.ini unterscheiden, werden die Werte in der Registrierung von den Werten aus Schema.ini überschrieben.  
  
## <a name="understanding-schemaini-files"></a>Grundlegendes zu Schema.ini Dateien  
 Schema.ini Dateien stellen Schema Informationen zu den Datensätzen in einer Textdatei bereit. Jeder Schema.ini Eintrag gibt eine von fünf Merkmalen der Tabelle an:  
  
-   Der Name der Textdatei.  
  
-   Das Dateiformat  
  
-   Feldnamen, breiten und Typen  
  
-   Der Zeichensatz  
  
-   Besondere Datentyp Konvertierungen  
  
 In den folgenden Abschnitten werden diese Eigenschaften erläutert.  
  
## <a name="specifying-the-file-name"></a>Angeben des Datei namens  
 Der erste Eintrag in Schema.ini ist immer der Name der Text Quelldatei, die in eckigen Klammern eingeschlossen ist. Im folgenden Beispiel wird der Eintrag für die Datei Sample.txt veranschaulicht:  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Angeben des Datei Formats  
 Die **Format** -Option in Schema.ini gibt das Format der Textdatei an. Der Text IISAM kann das Format automatisch aus den meisten Zeichen getrennten Dateien lesen. Sie können ein beliebiges einzelnes Zeichen als Trennzeichen in der Datei verwenden, ausgenommen das doppelte Anführungszeichen ("). Die **Format** Einstellung in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Datei nach Datei. In der folgenden Tabelle sind die gültigen Werte für die Option **Format** aufgeführt.  
  
|Formatbezeichner|Tabellenformat|Schema.ini Format-Anweisung|  
|----------------------|------------------|---------------------------------|  
|**Tabstopp-getrennt**|Felder in der Datei werden durch Registerkarten getrennt.|Format = tabdelikt|  
|**CSV-getrennt**|Felder in der Datei werden durch Kommas (durch Trennzeichen getrennte Werte) getrennt.|Format = csvdelic|  
|**Benutzerdefiniertes Trennzeichen**|Felder in der Datei werden durch ein beliebiges Zeichen getrennt, das Sie in das Dialogfeld eingeben. Alle außer den doppelten Anführungszeichen (") sind zulässig, einschließlich Leerzeichen.|Format = mit Trenn*Zeichen (benutzerdefiniertes Zeichen*)<br /><br /> - oder -<br /><br /> Ohne festgelegtes Trennzeichen:<br /><br /> Format = mit Trennzeichen ()|  
|**Länge mit fester Länge**|Felder in der Datei haben eine Länge mit fester Länge.|Format = FixedLength|  
  
## <a name="specifying-the-fields"></a>Angeben der Felder  
 Sie können Feldnamen in einer durch Trennzeichen getrennten Textdatei auf zwei Arten angeben:  
  
-   Fügen Sie die Feldnamen in die erste Zeile der Tabelle ein, und legen Sie **ColNameHeader** auf "true" fest **.**  
  
-   Geben Sie jede Spalte nach Nummer an, und geben Sie den Spaltennamen und den Datentyp an.  
  
 Sie müssen jede Spalte nach Zahl angeben und den Spaltennamen, den Datentyp und die Breite für Dateien mit fester Länge festlegen.  
  
> [!NOTE]  
>  Die **ColNameHeader** -Einstellung in Schema.ini überschreibt die Einstellung " **firstrowhasnames** " in der Windows-Registrierung, Datei nach Datei.  
  
 Die Datentypen der Felder können auch bestimmt werden. Verwenden Sie die Option **MaxScanRows** , um anzugeben, wie viele Zeilen beim Bestimmen der Spaltentypen gescannt werden sollen. Wenn Sie **MaxScanRows** auf 0 festlegen, wird die gesamte Datei gescannt. Die Einstellung " **MaxScanRows** " in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Datei nach Datei.  
  
 Der folgende Eintrag gibt an, dass Microsoft Jet die Daten in der ersten Zeile der Tabelle verwenden soll, um Feldnamen zu bestimmen, und die gesamte Datei überprüfen sollte, um die verwendeten Datentypen zu bestimmen:  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 Im nächsten Eintrag werden Felder in einer Tabelle mithilfe der Option Spaltennummer (**Col**_n_) angegeben, die für Zeichen getrennte Dateien optional ist und für Dateien mit fester Länge erforderlich ist. Das Beispiel zeigt die Schema.ini Einträge für zwei Felder, ein 10-Zeichen-Textfeld "customernumber" und ein 30-Zeichen-Textfeld "CustomerName":  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 Die Syntax von **Col**_n_ lautet wie folgt:  
  
```  
  
n=ColumnName type [Width] [#]  
```  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle werden die einzelnen Teile des " **Col**_n_ "-Eintrags beschrieben.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*ColumnName*|Der Textname der Spalte. Wenn der Spaltenname eingebettete Leerzeichen enthält, müssen Sie ihn in doppelte Anführungszeichen einschließen.|  
|*type*|Die Datentypen lauten wie folgt:<br /><br /> **Microsoft Jet-Datentypen**<br /><br /> bit<br /><br /> Byte<br /><br /> Short<br /><br /> Long<br /><br /> Währung<br /><br /> Single<br /><br /> Double<br /><br /> Datetime<br /><br /> Text<br /><br /> Memo<br /><br /> **ODBC-Datentypen** Char (identisch mit Text)<br /><br /> Float (identisch mit Double)<br /><br /> Ganzzahl (identisch mit Short)<br /><br /> LongChar (identisch mit Memo)<br /><br /> Datums *Format* für Datum|  
|**Width**|Der literale Zeichen folgen Wert `Width` . Gibt an, dass die folgende Zahl die Breite der Spalte festlegt (optional für Zeichen getrennte Dateien; erforderlich für Dateien mit fester Länge).|  
|*#*|Der ganzzahlige Wert, der die Breite der Spalte festlegt (erforderlich, wenn die **Breite** angegeben ist).|  
  
## <a name="selecting-a-character-set"></a>Auswählen eines Zeichensatzes  
 Sie können aus zwei Zeichensätzen auswählen: ANSI und OEM. Die Einstellung für die **Kenn** Zeichnung in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Datei nach Datei. Das folgende Beispiel zeigt den Schema.ini Eintrag, mit dem der Zeichensatz auf ANSI festgelegt wird:  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Angeben von Datentyp Formaten und-Konvertierungen  
 Die Schema.ini-Datei enthält mehrere Optionen, mit denen Sie angeben können, wie Daten konvertiert oder angezeigt werden. In der folgenden Tabelle sind die einzelnen Optionen aufgeführt.  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**DateTimeFormat**|Kann auf eine Format Zeichenfolge festgelegt werden, die Datumsangaben und Uhrzeiten angibt. Sie sollten diesen Eintrag angeben, wenn alle Datums-/Uhrzeitfelder im Import/Export im gleichen Format behandelt werden. Alle Microsoft Jet-Formate außer Uhr und Nachmittag werden unterstützt. Wenn keine Format Zeichenfolge vorhanden ist, werden die Windows-Systemsteuerung kurz Datums Bild und Uhrzeit Optionen verwendet.|  
|**Decimalsymbol**|Kann auf ein beliebiges einzelnes Zeichen festgelegt werden, das zum Trennen der Ganzzahl vom Bruchteil einer Zahl verwendet wird.|  
|**Nummerier Ziffern**|Gibt die Anzahl der Dezimalstellen im Bruchteil einer Zahl an.|  
|**"Numleadingzeros"**|Gibt an, ob ein Dezimalwert, der kleiner als 1 und größer als-1 ist, führende Nullen enthalten soll. Dieser Wert kann entweder "false" (keine führenden Nullen) oder "true" sein.|  
|**CurrencySymbol**|Gibt das Währungssymbol an, das für Währungswerte in der Textdatei verwendet werden kann. Beispiele hierfür sind das Dollarzeichen ($) und DM.|  
|**"Currency cyposformat"**|Kann auf einen der folgenden Werte festgelegt werden:<br /><br /> -Währungssymbol Präfix ohne Trennung ($1)<br />-Währungssymbol Suffix ohne Trennung ($1)<br />-Währungssymbol Präfix mit einer Zeichen Trennung ($1)<br />-Währungssymbol Suffix mit einer Zeichen Trennung ($1)|  
|**Vorkommnisse**|Gibt die Anzahl der Ziffern an, die für die Bruchteile einer Währungs Menge verwendet werden.|  
|**Currency-Format**|Es kann sich um einen der folgenden Werte handeln:<br /><br /> -($1)<br />--$1<br />-$-1<br />-$1-<br />-($1)<br />--$1<br />-1-$<br />-$1-<br />--$1<br />--$1<br />-$1-<br />-$1-<br />-$-1<br />-1-$<br />-($1)<br />-($1)<br /><br /> In diesem Beispiel wird das Dollarzeichen gezeigt, aber Sie sollten es durch den entsprechenden Wert für "Currency **Symbol** " im eigentlichen Programm ersetzen.|  
|**"Uscytausendandsymbol"**|Gibt das Einzelzeichen Symbol an, das zum Trennen von Währungswerten in der Textdatei durch Tausende verwendet werden kann.|  
|**"", "".**|Kann auf ein beliebiges einzelnes Zeichen festgelegt werden, das verwendet wird, um das ganze von dem Bruchteil einer Währungs Menge zu trennen.|  
  
> [!NOTE]  
>  Wenn Sie einen Eintrag weglassen, wird der Standardwert in der Windows-Systemsteuerung verwendet.
