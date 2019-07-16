---
title: Datei "Schema.ini" (Textdateitreiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dd95329c91c69af38b1ffc7951191498fcc40479
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987944"
---
# <a name="schemaini-file-text-file-driver"></a>Datei „Schema.ini“ (Textdateitreiber)
Wenn der Text-Treiber verwendet wird, wird das Format der Textdatei mit einer Schemadatei für die Informationen bestimmt. Die Schema-Informationsdatei ist immer mit dem Namen Schema.ini und immer im gleichen Verzeichnis wie die Text-Datenquelle gespeichert. Die Schemadatei für die Informationen enthält die IISAM mit Informationen über das allgemeine Format der Datei, den Namen der Spalte und Datentypinformationen und mehrere andere Datenmerkmale. Eine Schema.ini-Datei ist immer erforderlich, für den Zugriff auf Daten fester Länge. Sie sollten eine Schema.ini-Datei verwenden, wenn die Texttabelle enthält, DateTime, Währung oder Dezimaldaten oder jedes Mal, wenn Sie mehr Kontrolle über die Behandlung der Daten in der Tabelle möchten.  
  
> [!NOTE]  
>  Text-ISAM wird die ursprünglichen Werte erhalten, aus der Registrierung und nicht aus "Schema.ini". Das gleiche Standarddateiformat gilt für alle neuen Datentabellen von Text. Alle Dateien, die von der CREATE TABLE-Anweisung erstellt wurden, erben die gleichen Format Standardwerte, die festgelegt werden, durch Auswählen von Format dateiwerten in die **-Text-Format definieren** Dialogfeld mit \<standardmäßig > in der ausgewählt **Tabellen** Liste. Wenn sich die Werte in der Registrierung von den Werten in Schema.ini unterscheiden zu können, werden die Werte in der Registrierung durch die Werte aus "Schema.ini" überschrieben werden.  
  
## <a name="understanding-schemaini-files"></a>Grundlegendes zu Schema.ini-Dateien  
 Schema.ini-Dateien bieten die Schemainformationen zu den Datensätzen in einer Textdatei. Jeder Eintrag "Schema.ini" gibt einen der fünf Merkmale der Tabelle:  
  
-   Namen der Textdatei  
  
-   Das Dateiformat  
  
-   Die Feldnamen, Breite und Typen  
  
-   Der Zeichensatz  
  
-   Spezielle Konvertierung von Datentypen  
  
 Den folgenden Abschnitten werden diese Eigenschaften.  
  
## <a name="specifying-the-file-name"></a>Der Dateiname angeben  
 Der erste Eintrag in "Schema.ini" ist immer der Name der Quelltextdatei in eckige Klammern eingeschlossen. Das folgende Beispiel veranschaulicht den Eintrag für die Datei "Sample.txt":  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Das Dateiformat angeben  
 Die **Format** -Option in "Schema.ini" gibt das Format der Textdatei an. Der Text-IISAM können das Format automatisch die meisten Zeichen getrennten Dateien gelesen werden. Sie können jedem beliebigen einzelnes Zeichen als Trennzeichen in der Datei außer das doppelte Anführungszeichen (") verwenden. Die **Format** in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Dateien. Die folgende Tabelle enthält die gültigen Werte für die **Format** Option.  
  
|Formatbezeichner|Tabellenformat|"Schema.ini" Format-Anweisung|  
|----------------------|------------------|---------------------------------|  
|**Tabstopp-getrennt**|Felder in der Datei werden durch Tabulatoren getrennt.|Format = TabDelimited|  
|**CSV-Trennzeichen**|Felder in der Datei werden durch Kommas (durch Trennzeichen getrennte Werte) getrennt.|Format = CSVDelimited|  
|**Mit benutzerdefiniertem Trennzeichen**|Felder in der Datei von einem anderen Zeichen als Trennzeichen, die Sie in das Dialogfeld Eingabe auf. Alles außer das doppelte Anführungszeichen (") sind zulässig, einschließlich leer.|Format = mit Trennzeichen (*benutzerdefiniertes Zeichen*)<br /><br /> -oder-<br /><br /> Kein Trennzeichen angegeben:<br /><br /> Format = mit Trennzeichen)|  
|**Fester Länge**|Felder in der Datei sind eine feste Länge auf.|Format = FixedLength|  
  
## <a name="specifying-the-fields"></a>Die Felder angeben  
 Sie können die Feldnamen in einer Zeichen getrennten Textdatei auf zwei Arten angeben:  
  
-   Die Feldnamen in der ersten Zeile der Tabelle enthalten, und legen Sie **ColNameHeader** zu **"true".**  
  
-   Geben Sie jede Spalte nach Anzahl und die Spalte und der Typ.  
  
 Sie müssen festlegen, die Spaltennamen, Datentyp und Breite für Dateien mit fester Länge und jede Spalte nach Anzahl angeben.  
  
> [!NOTE]  
>  Die **ColNameHeader** Schema.ini Außerkraftsetzungen Festlegen der **FirstRowHasNames** Einstellung in der Windows-Registrierung, Dateien.  
  
 Die Datentypen der Felder können auch ermittelt werden. Verwenden der **MaxScanRows** Option, um anzugeben, wie viele Zeilen überprüft werden soll, wenn die Spaltentypen bestimmt. Setzen Sie **MaxScanRows** 0 ist, wird die gesamte Datei überprüft. Die **MaxScanRows** in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Dateien.  
  
 Der folgende Eintrag gibt an, dass Microsoft Jet die Daten in der ersten Zeile der Tabelle verwenden sollten, um zu bestimmen, Feldnamen und prüfen sollten, um zu bestimmen, die Daten die gesamte Datei verwendeten Typen:  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 Der nächste Eintrag kennzeichnet Felder in einer Tabelle mit der Nummer der Spalte (**Col**_n_) Option, die für Zeichen getrennten Dateien optional und für Dateien mit fester Länge erforderlich ist. Das Beispiel zeigt die Schema.ini-Einträge für zwei Felder, ein Textfeld von 10 Zeichen bestehende CustomerNumber und ein 30 Zeichen CustomerName-Textfeld:  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 Die Syntax der **Col**_n_ ist:  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Tabelle beschreibt die einzelnen Teile der **Col**_n_ Eintrag.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*ColumnName*|Der Textname der Spalte. Wenn der Spaltenname Leerzeichen enthält, müssen Sie ihn in doppelte Anführungszeichen setzen.|  
|*type*|Datentypen sind wie folgt aus:<br /><br /> **Microsoft Jet-Datentypen**<br /><br /> bit<br /><br /> Byte<br /><br /> Short<br /><br /> Long<br /><br /> Währung<br /><br /> Single<br /><br /> Double<br /><br /> DateTime<br /><br /> Text<br /><br /> Memo<br /><br /> **ODBC-Datentypen** Char (identisch mit Text)<br /><br /> "Float" (identisch mit Double)<br /><br /> Ganze Zahl (identisch mit Short)<br /><br /> LongChar (identisch mit Memo)<br /><br /> Datum *Datumsformat*|  
|**Width**|Der Wert der literalen Zeichenfolge `Width`. Gibt an, dass die folgende Anzahl die Breite der Spalte bestimmt (optional für Zeichen getrennten Dateien; für Dateien mit fester Länge erforderlich).|  
|*#*|Der ganzzahlige Wert, der die Breite der Spalte bestimmt (erforderlich, wenn **Breite** angegeben ist).|  
  
## <a name="selecting-a-character-set"></a>Auswählen eines Zeichensatzes  
 Sie können aus zwei Zeichensätze auswählen: ANSI- und OEM. Die **CharacterSet** in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Dateien. Das folgende Beispiel zeigt den Schema.ini-Eintrag, der den Zeichensatz an ANSI festlegt:  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Angeben von Datenformaten-Typ und Konvertierungen  
 Die Datei "Schema.ini" enthält mehrere Optionen, die Sie verwenden können, um anzugeben, wie die Daten konvertiert oder angezeigt werden. Die folgende Tabelle enthält jede dieser Optionen.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**DateTimeFormat**|Kann auf einer Formatzeichenfolge festgelegt werden, die Datums- und Uhrzeitangaben angibt. Sie sollten diesen Eintrag angeben, wenn alle Datum/Uhrzeit-Felder in den Import/Export mit dem gleichen Format verarbeitet werden. Alle Microsoft Jet-Formate, mit Ausnahme der Uhr und Uhr. werden unterstützt. Ist keine Formatzeichenfolge, werden die Optionen für das kurze Datum Windows-Systemsteuerung der Bild und die Uhrzeit verwendet.|  
|**DecimalSymbol**|Kann auf jedem beliebigen einzelnen Zeichen festgelegt werden, die verwendet wird, um die ganze Zahl von der Bruchteil einer Zahl zu trennen.|  
|**NumberDigits**|Gibt die Anzahl von Dezimalstellen in der Bruchteil einer Zahl.|  
|**NumberLeadingZeros**|Gibt an, ob ein decimal-Wert kleiner als 1 und mehr als 1, führende Nullen enthalten soll. Dieser Wert kann entweder "false" (ohne führenden Nullen) sein oder "true".|  
|**CurrencySymbol**|Gibt an, das Währungssymbol ein, das für die Currency-Werte in der Textdatei verwendet werden kann. Beispiele sind das Dollarzeichen ($) und Dm.|  
|**CurrencyPosFormat**|Kann auf eines der folgenden Werte festgelegt werden:<br /><br /> -Currency Symbol Präfix ohne Trennung ($1)<br />-Currency Symbol-Suffix ohne Trennung (1$)<br />-Currency Symbol-Präfix mit einem Zeichen getrenntem ($ 1)<br />-Currency Symbol-Suffix mit einem Trennung (1 $)|  
|**CurrencyDigits**|Gibt die Anzahl von Ziffern für den Bruchteil einen Währungsbetrag.|  
|**CurrencyNegFormat**|Kann einer der folgenden Werte sein:<br /><br /> -   ($1)<br />--$1<br />-$-1<br />-$1:<br />-   (1$)<br />-1 $<br />-1-$<br />-1-<br />-1 $<br />--$ 1<br />-1-<br />-$ 1:<br />-$-1<br />-1-$<br />-   ($ 1)<br />-   (1 $)<br /><br /> Dieses Beispiel zeigt das Dollarzeichen, aber ersetzen Sie es mit dem entsprechenden **CurrencySymbol** Wert im wirklichen Programm.|  
|**CurrencyThousandSymbol**|Gibt an, das einzelne Zeichen-Symbol, das für die Trennung von Währungswerten in der Textdatei von Tausenden verwendet werden kann.|  
|**CurrencyDecimalSymbol**|Kann auf jedem beliebigen einzelnen Zeichen festgelegt werden, die verwendet wird, um die gesamte von den Bruchteil einen Währungsbetrag zu trennen.|  
  
> [!NOTE]  
>  Wenn Sie einen Eintrag weglassen, ist der Standardwert in der Windows-Systemsteuerung verwendet.
