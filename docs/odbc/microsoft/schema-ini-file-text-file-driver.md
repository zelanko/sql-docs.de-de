---
title: Schema.ini-Datei (Textdateitreiber) | Microsoft Docs
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
ms.openlocfilehash: 365351724f27205e7d460c757f1268d042cefc76
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305511"
---
# <a name="schemaini-file-text-file-driver"></a>Datei „Schema.ini“ (Textdateitreiber)
Wenn der Texttreiber verwendet wird, wird das Format der Textdatei mithilfe einer Schemainformationsdatei bestimmt. Die Schemainformationsdatei trägt immer den Namen Schema.ini und wird immer im selben Verzeichnis wie die Textdatenquelle gespeichert. Die Schemainformationsdatei stellt dem IISAM Informationen über das allgemeine Format der Datei, den Spaltennamen und die Datentypinformationen sowie mehrere andere Datenmerkmale bereit. Für den Zugriff auf Daten fester Länge ist immer eine Datei Schema.ini erforderlich. Sie sollten eine Schema.ini-Datei verwenden, wenn ihre Texttabelle DateTime-, Währungs- oder Dezimaldaten enthält oder jederzeit mehr Kontrolle über die Verarbeitung der Daten in der Tabelle haben soll.  
  
> [!NOTE]  
>  Der Text-ISAM ruft anfängliche Werte aus der Registrierung ab, nicht von Schema.ini. Das gleiche Standarddateiformat gilt für alle neuen Textdatentabellen. Alle Dateien, die von der CREATE TABLE-Anweisung erstellt wurden, erben dieselben Standardformatwerte, die durch \<Auswählen von Dateiformatwerten im Dialogfeld **Textformat** definieren mit Standard> in der Liste **Tabellen** ausgewählt werden. Wenn sich die Werte in der Registrierung von den Werten in Schema.ini unterscheiden, werden die Werte in der Registrierung durch die Werte von Schema.ini überschrieben.  
  
## <a name="understanding-schemaini-files"></a>Grundlegendes zu Schema.ini-Dateien  
 Schema.ini-Dateien stellen Schemainformationen zu den Datensätzen in einer Textdatei bereit. Jeder Schema.ini-Eintrag gibt eines von fünf Merkmalen der Tabelle an:  
  
-   Der Textdateiname  
  
-   Das Dateiformat  
  
-   Die Feldnamen, Breiten und Typen  
  
-   Der Zeichensatz  
  
-   Spezielle Datentypkonvertierungen  
  
 In den folgenden Abschnitten werden diese Merkmale erläutert.  
  
## <a name="specifying-the-file-name"></a>Angeben des Dateinamens  
 Der erste Eintrag in Schema.ini ist immer der Name der Textquelldatei, die in eckige Klammern eingeschlossen ist. Das folgende Beispiel veranschaulicht den Eintrag für die Datei Sample.txt:  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Angeben des Dateiformats  
 Die Option **Format** in Schema.ini gibt das Format der Textdatei an. Der Text-IISAM kann das Format automatisch aus den meisten durch Zeichen getrennten Dateien lesen. Sie können jedes einzelne Zeichen als Trennzeichen in der Datei mit Ausnahme des doppelten Anführungszeichens (") verwenden. Die **Formateinstellung** in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Datei für Datei. In der folgenden Tabelle sind die gültigen Werte für die Option **Format** aufgeführt.  
  
|Formatbezeichner|Tabellenformat|Schema.ini Format-Anweisung|  
|----------------------|------------------|---------------------------------|  
|**Tab getrennt**|Felder in der Datei werden durch Registerkarten getrennt.|Format=TabDelimited|  
|**CSV-Abgrenzer**|Felder in der Datei werden durch Kommas (durch Kommas getrennte Werte) getrennt.|Format=CSVDelimited|  
|**Benutzerdefinierte abgegrenzt**|Felder in der Datei werden durch jedes Zeichen getrennt, das Sie in das Dialogfeld eingeben möchten. Alle mit Ausnahme der doppelten Anführungszeichen (") sind zulässig, einschließlich leer.|Format=Getrennt (*benutzerdefiniertes Zeichen*)<br /><br /> - oder -<br /><br /> Ohne Trennzeichen angegeben:<br /><br /> Format=Getrennt( )|  
|**Feste Länge**|Die Felder in der Datei haben eine feste Länge.|Format=FixedLength|  
  
## <a name="specifying-the-fields"></a>Angeben der Felder  
 Sie können Feldnamen in einer textgetrennten Textdatei auf zwei Arten angeben:  
  
-   Fügen Sie die Feldnamen in die erste Zeile der Tabelle ein, und legen Sie **ColNameHeader** auf **True fest.**  
  
-   Geben Sie jede Spalte nach Zahl an, und legen Sie den Spaltennamen und den Datentyp fest.  
  
 Sie müssen jede Spalte nach Zahl angeben und den Spaltennamen, den Datentyp und die Breite für Dateien mit fester Länge angeben.  
  
> [!NOTE]  
>  Die **ColNameHeader-Einstellung** in Schema.ini überschreibt die **FirstRowHasNames-Einstellung** in der Windows-Registrierung, Datei für Datei.  
  
 Die Datentypen der Felder können ebenfalls bestimmt werden. Verwenden Sie die Option **MaxScanRows,** um anzugeben, wie viele Zeilen beim Bestimmen der Spaltentypen gescannt werden sollen. Wenn Sie **MaxScanRows** auf 0 setzen, wird die gesamte Datei gescannt. Die **Einstellung MaxScanRows** in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Datei für Datei.  
  
 Der folgende Eintrag weist darauf hin, dass Microsoft Jet die Daten in der ersten Zeile der Tabelle verwenden sollte, um Feldnamen zu bestimmen, und die gesamte Datei untersuchen sollte, um die verwendeten Datentypen zu bestimmen:  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 Der nächste Eintrag bezeichnet Felder in einer Tabelle mithilfe der Option Spaltennummer (**Kol**_n_), die für dateiendurchgrenzte Dateien mit Zeichengetrennt optional ist und für Dateien mit fester Länge erforderlich ist. Das Beispiel zeigt die Schema.ini-Einträge für zwei Felder, ein 10-stelliges CustomerNumber-Textfeld und ein 30-stelliges CustomerName-Textfeld:  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 Die Syntax von **Col**_n_ lautet:  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle werden die einzelnen Teile des **Eintrags "Col**_n"_ beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*ColumnName*|Der Textname der Spalte. Wenn der Spaltenname eingebettete Leerzeichen enthält, müssen Sie ihn in doppelte Anführungszeichen einschließen.|  
|*type*|Die Datentypen lauten wie folgt:<br /><br /> **Microsoft Jet-Datentypen**<br /><br /> bit<br /><br /> Byte<br /><br /> Short<br /><br /> Long<br /><br /> Währung<br /><br /> Single<br /><br /> Double<br /><br /> Datetime<br /><br /> Text<br /><br /> Memo<br /><br /> **ODBC-Datentypen** Char (wie Text)<br /><br /> Float (wie Double)<br /><br /> Ganzzahl (wie Short)<br /><br /> LongChar (wie Memo)<br /><br /> *Datumsdatumsformat*|  
|**Width**|Der Literalzeichenfolgenwert `Width`. Gibt an, dass die folgende Zahl die Breite der Spalte angibt (optional für Dateien mit zeichentrennung; erforderlich für Dateien mit fester Länge).|  
|*#*|Der Ganzzahlwert, der die Breite der Spalte angibt (erforderlich, wenn **Breite** angegeben ist).|  
  
## <a name="selecting-a-character-set"></a>Auswählen eines Zeichensatzes  
 Sie können aus zwei Zeichensätzen auswählen: ANSI und OEM. Die **CharacterSet-Einstellung** in Schema.ini überschreibt die Einstellung in der Windows-Registrierung, Datei für Datei. Das folgende Beispiel zeigt den Schema.ini-Eintrag, der den Zeichensatz auf ANSI festlegt:  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Angeben von Datentypformaten und Konvertierungen  
 Die Datei Schema.ini enthält mehrere Optionen, mit denen Sie angeben können, wie Daten konvertiert oder angezeigt werden. In der folgenden Tabelle sind alle diese Optionen aufgeführt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**DateTimeFormat**|Kann auf eine Formatzeichenfolge festgelegt werden, die Datums- und Uhrzeitangaben angibt. Sie sollten diesen Eintrag angeben, wenn alle Datums-/Uhrzeitfelder im Import/Export im gleichen Format behandelt werden. Alle Microsoft Jet-Formate außer A.M. und Nachmittag werden unterstützt. Wenn keine Formatzeichenfolge vorhanden ist, werden die Optionen für das kurze Datumsbild und die Uhrzeit optionen für die Windows-Systemsteuerung verwendet.|  
|**DecimalSymbol**|Kann auf ein beliebiges einzelnes Zeichen gesetzt werden, das verwendet wird, um die ganze Zahl vom Bruchteil einer Zahl zu trennen.|  
|**NumberDigits**|Gibt die Anzahl der Dezimalstellen im Bruchteil einer Zahl an.|  
|**NumberLeadingZeros**|Gibt an, ob ein Dezimalwert kleiner als 1 und mehr als -1 führende Nullen enthalten soll. Dieser Wert kann entweder False (keine führenden Nullen) oder True sein.|  
|**CurrencySymbol**|Gibt das Währungssymbol an, das für Währungswerte in der Textdatei verwendet werden kann. Beispiele hierfür sind das Dollarzeichen () und dm.|  
|**CurrencyPosFormat**|Kann auf einen der folgenden Werte festgelegt werden:<br /><br /> - Währungssymbol-Präfix ohne Trennung<br />- Währungssymbol-Suffix ohne Trennung (1)<br />- Währungssymbolpräfix mit einer Zeichentrennung<br />- Währungssymbol-Suffix mit einer Zeichentrennung (1 )|  
|**CurrencyDigits**|Gibt die Anzahl der Ziffern an, die für den Bruchteil eines Währungsbetrags verwendet werden.|  
|**CurrencyNegFormat**|Es kann sich um einen der folgenden Werte handeln:<br /><br /> - (Nr. 1)<br />- -1 $<br />- Nr. 1<br />- 1 $<br />- (1 $)<br />- -1$<br />- 1-$<br />- 1.-<br />- -1 $<br />- -$ 1<br />- 1<br />- $ 1-<br />- -1 $<br />- 1- $<br />- ($ 1)<br />- (1 $)<br /><br /> In diesem Beispiel wird das Dollarzeichen angezeigt, aber Sie sollten es durch den entsprechenden **CurrencySymbol-Wert** im eigentlichen Programm ersetzen.|  
|**WährungThousandSymbol**|Gibt das einstellige Symbol an, das zum Trennen von Währungswerten in der Textdatei durch Tausende verwendet werden kann.|  
|**WährungDecimalSymbol**|Kann auf ein beliebiges einzelnes Zeichen gesetzt werden, das verwendet wird, um das Ganze vom Bruchteil eines Währungsbetrags zu trennen.|  
  
> [!NOTE]  
>  Wenn Sie einen Eintrag weglassen, wird der Standardwert in der Windows-Systemsteuerung verwendet.
