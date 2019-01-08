---
title: Dwloader Command-Line-Ladeprogramm – Parallel Data Warehouse | Microsoft-Dokumentation
description: Dwloader ist ein Befehlszeilentool Parallel Data Warehouse (PDW), die Tabellenzeilen in einem in einer vorhandenen Tabelle lädt.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: fbfc160f495f9717645c8417f11f67f572271d9b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52512993"
---
# <a name="dwloader-command-line-loader-for-parallel-data-warehouse"></a>Dwloader Command-Line-Ladeprogramm für Parallel Data Warehouse
**Dwloader** ist ein Befehlszeilentool Parallel Data Warehouse (PDW), die Tabellenzeilen in einem in einer vorhandenen Tabelle lädt. Beim Laden von Zeilen können Sie alle Zeilen am Ende der Tabelle hinzufügen (*append-Modus* oder *Fastappend-Modus*), neue Zeilen angefügt, und Aktualisieren von vorhandenen Zeilen (*Upsert-Modus*), oder löschen Sie alle vorhandene Zeilen vor dem Laden, und klicken Sie dann alle Zeilen in eine leere Tabelle einfügen (*laden Modus*).  
  
**Prozess zum Laden von Daten**  
  
1.  Vorbereiten der Quelldaten an.  
  
    Verwenden Sie Ihre eigenen ETL-Prozess, um die Daten zu erstellen, die Sie laden möchten. Die Quelldaten müssen das Schema der Zieltabelle entsprechend formatiert sein. Die Quelldaten in eine oder mehrere Textdateien Store, und Kopieren der Dateien in dasselbe Verzeichnis auf dem Server geladen. Informationen über den Server laden können, finden Sie unter [abrufen und Konfigurieren eines Servers werden geladen](acquire-and-configure-loading-server.md)  
  
2.  Bereiten Sie die Optionen für das Laden vor.  
  
    Entscheiden Sie, welche Optionen für das Laden Sie verwenden möchten. Store Optionen für das Laden in einer Konfigurationsdatei. Kopieren Sie die Konfigurationsdatei in einen lokalen Speicherort auf dem Server geladen. Die **Dwloader** Konfigurationsoptionen werden in diesem Thema beschrieben.  
  
3.  Bereiten Sie die Last-Optionen vor.  
  
    Festlegen, wie **Dwloader** zur Verarbeitung von Zeilen, die nicht geladen werden. Zum Ausführen der Auslastung **Dwloader** lädt zunächst die Daten in eine Stagingtabelle ein, und überträgt die Daten dann an die Zieltabelle. Wie das Ladeprogramm Daten in die Stagingtabelle geladen wurden, überwacht er die Anzahl der Zeilen, die nicht geladen werden. Beispielsweise können Zeilen, die nicht korrekt formatiert sind nicht geladen. Fehlerhafte Zeilen werden in einer Ablehnung-Datei kopiert. Standardmäßig wird die Last nach der ersten Ablehnung abgebrochen, wenn Sie einen anderen Ablehnung Schwellenwert angeben.  
  
4.  Installieren Sie **Dwloader**.  
  
    Installieren Sie Dwloader auf dem Server geladen, wenn es nicht bereits installiert ist. 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  Führen Sie **Dwloader**.  
  
    Melden Sie sich an den Server geladen, und führen Sie die ausführbare Datei **dwloader.exe** mit den entsprechenden Befehlszeilenoptionen.  
  
6.  Überprüfen Sie die Ergebnisse aus.  
  
    Sehen Sie sich die fehlerhaften Zeilen Datei (angegeben mit -R), um festzustellen, ob alle Zeilen konnte nicht geladen. Wenn diese Datei leer ist, werden alle Zeilen erfolgreich geladen. **Dwloader** transaktional ist, also wenn einer fehlschlägt (außer abgelehnten Zeilen) und befinden alle Schritte in ihren ursprünglichen Zustand Rollback ausgeführt werden.  
  
<!-- 
![Topic link icon](media/topic-link.gif "Topic_Link")[Syntax Conventions](syntax-conventions-sql-server-pdw.md)  
-->  


## <a name="syntax"></a>Syntax  
  
```  
dwloader.exe { -h }  
  
dwloader.exe   
    {  
        { -U login_name  -P password  }  
        | -W  
    }  
    [ -f parameter_file ]  
    [ -S target_appliance ]  
    { -T target_database_name . [ schema ] . table_name }   
    { -i source_data_location } [ <source_data_options> ]  
    { -R load_failure_file_name } [ <load_failure_options> ]  
    [ <loading_options> ]  
}  
  
<source_data_options> ::=  
{  
    [ -fh number_header_rows ]  
    [ < variable_length_column_options > | < fixed_width_column_options > ]  
    [ -D { mdy | myd | ymd | ydm | dmy | dym | custom_date_format } ]  
    [ -dt datetime_format_file ]  
}  
  
<variable_length_column_options> ::=  
{  
    [ -e character_encoding ]  
    -r row_delimiter   
    [ -s string_delimiter ]  
    -t field_delimiter   
}  
  
<fixed_width_column_options> ::=  
{  
    -w fixed_width_config_file   
    [ -e character_encoding ]   
    -r row_delimiter   
}  
  
<load_failure_options> ::=  
{  
    [ -rt { value | percentage } ]  
    [ -rv reject_value ]  
    [ -rs reject_sample_value ]  
}  
  
<loading_options> ::=  
{  
    [ -d staging_database_name ]  
    [ -M { append | fastappend | upsert -K merge_column [ ,...n ] | reload } ]  
    [ -b batchsize ]   
    [ -c ]  
    [ -E ]  
    [ -m ]  
    [ -N ]  
    [ -se ]   
}  
```  
  
## <a name="arguments"></a>Argumente  
**-h**  
Zeigt die einfache Hilfe-Informationen zur Verwendung von des Ladeprogramms. Hilfe wird nur angezeigt, wenn keine anderen Befehlszeilenparametern angegeben werden.  
  
**-U** *Login_name*  
Eine gültige SQL Server-authentifizierungsanmeldung mit entsprechenden Berechtigungen, um den Ladevorgang durchzuführen.  
  
**-P** *password*  
Das Kennwort für eine SQL Server-Authentifizierung *Login_name*.  
  
**-W**  
Windows-Authentifizierung verwenden. (Keine *Login_name* oder *Kennwort* erforderlich.) 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *Parameter_file_name*  
Verwenden Sie eine Parameterdatei *Parameter_file_name*, anstelle von Befehlszeilenparametern. *Parameter_file_name* darf Befehlszeilenparameter, mit Ausnahme von *User_name* und *Kennwort*. Wenn ein Parameter in der Befehlszeile und in der Parameterdatei angegeben wird, überschreibt der Befehlszeile den File-Parameter.  
  
Die Parameterdatei enthält einen Parameter, ohne die **-** Präfix pro Zeile.  
  
Beispiele:  
  
`rt=percentage`  
  
`rv=25`  
  
**-S *** Target_appliance*  
Gibt an, die SQL Server-PDW-Appliance, die die geladenen Daten erhält.  
  
*Infiniband-Verbindungen*, *Target_appliance* als < Appliance-Name > angegeben wird – SQLCTL01. Verbindung mit dem Namen für diese Konfiguration finden Sie unter [InfiniBand-Netzwerkadapter konfigurieren](configure-infiniband-network-adapters.md).  
  
Für Ethernet-Verbindungen *Target_appliance* ist die IP-Adresse für den Steuerelement-Knoten-Cluster.  
  
Wenn nicht angegeben, wird standardmäßig Dwloader auf den Wert, der bei der Installation Dwloader angegeben wurde. 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *Target_database_name.* [*Schema*]. *Table_name*  
Der dreiteilige Name für die Zieltabelle.  
  
**-I***source_data_location*  
Der Speicherort des einen oder mehrere Quelldateien zu laden. Jede Quelldatei muss eine Textdatei oder einer Textdatei, die mit Gzip komprimiert wird. Nur eine Quelldatei kann in jede Gzip-Datei komprimiert werden.  
  
So formatieren Sie eine Quelldatei:  
  
-   Die Quelldatei muss in Übereinstimmung mit den Optionen für das Laden formatiert sein.  
  
-   Jede Zeile in einer Quelldatei enthält, die Daten für eine Tabellenzeile wird. Die Quelldaten müssen das Schema der Zieltabelle übereinstimmen. Zusätzlich müssen die Spalte Reihenfolge und Datentypen übereinstimmen. Jedes Feld in der Zeile stellt eine Spalte in der Zieltabelle dar.  
  
-   Standardmäßig werden die Felder variabler Länge sind und durch ein Trennzeichen getrennt. Um die Trennzeichentyp anzugeben, verwenden Sie die < Variable_length_column_options >-Befehlszeilenoptionen. Um Felder mit fester Länge anzugeben, verwenden Sie die < Fixed_width_column_options >-Befehlszeilenoptionen.  
  
So geben Sie den Quellspeicherort für die Daten an:  
  
-   Der Quellspeicherort für die Daten kann es sich um einen Netzwerkpfad oder einen lokalen Pfad zu einem Verzeichnis auf dem Server geladen sein.  
  
-   Um alle Dateien in einem Verzeichnis anzugeben, geben Sie in den Verzeichnispfad an, gefolgt von den * Platzhalterzeichen.  Das Ladeprogramm lädt nicht Dateien in sämtlichen Unterverzeichnissen, die den Quellspeicherort für die Daten werden... Das Ladeprogramm-Fehler, wenn ein Verzeichnis in einer Gzip-Datei vorhanden ist.  
  
-   Um einige der Dateien in einem Verzeichnis anzugeben, verwenden Sie eine Kombination von Zeichen und die * Platzhalter.  
  
So laden Sie mehrere Dateien mit einem Befehl:  
  
-   Alle Dateien müssen im gleichen Verzeichnis vorhanden sind.  
  
-   Die Dateien müssen alle Textdateien, alle Gzip-Dateien oder eine Kombination von sowohl Text als auch Gzip-Dateien sein.  
  
-   Keine der Dateien kann es sich um Headerinformationen enthalten.  
  
-   Alle Dateien müssen den gleichen Zeichencodierungstyp verwenden. Die -e-Option wird angezeigt.  
  
-   Alle Dateien müssen in derselben Tabelle geladen werden.  
  
-   Alle Dateien werden verkettet und geladen werden, als ob sie eine Datei, und der abgelehnten Zeilen in eine einzelne Reject-Datei gelangen.  
  
Beispiele:  
  
-   -i \\\loadserver\loads\daily\\*.gz  
  
-   -i \\\loadserver\loads\daily\\*.txt  
  
-   -i \\\loadserver\loads\daily\monday.*  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   -i \\\loadserver\loads\daily\\*  
  
**-R** *Load_failure_file_name*  
Treten Fehler beim Laden von **Dwloader** speichert die Zeile, die geladen und die Beschreibung des Fehlers die Fehlerinformationen in einer Datei namens Fehler *Load_failure_file_name*. Wenn diese Datei bereits vorhanden ist, wird die Dwloader die vorhandene Datei überschrieben. *Load_failure_file_name* wird erstellt, wenn der erste Fehler auftritt. Wenn alle Zeilen erfolgreich laden *Load_failure_file_name* wird nicht erstellt.  
  
**-Fh** *Number_header_rows*  
Die Anzahl der Zeilen (Reihen), um am Anfang des ignorieren *Source_data_file_name*. Die Standardeinstellung ist 0.  
  
<variable_length_column_options>  
Die Optionen für eine *Source_data_file_name* , die Zeichen getrennten Spalten mit variabler Länge hat. In der Standardeinstellung *Source_data_file_name* ASCII-Zeichen in Spalten variabler Länge enthält.  
  
Für ASCII-Dateien werden NULL-Werte dargestellt, durch Trennzeichen nacheinander zu platzieren. Z. B. in eine Pipe getrennte Datei ("|"), ein NULL-Wert wird angegeben, indem "||". In einer durch Trennzeichen getrennte Datei, ein NULL-Wert angegeben ist, von ",". Darüber hinaus die **-E** (--EmptyStringAsNull) Option muss angegeben werden. Weitere Informationen zum -E finden Sie unten.  
  
**-e:** *Character_encoding*  
Gibt einen Typ zeichencodierung für die Daten aus der Datendatei geladen werden. Stehen, ASCII (Standard) "," UTF8 "," UTF16 "oder" UTF16BE, wobei UTF16-Format little-endian und UTF16BE ist big-Endian. Diese Optionen, die Groß-/Kleinschreibung beachtet werden.  
  
**-t** *Field_delimiter*  
Das Trennzeichen für jedes Feld (Spalte) in der Zeile. Das Feldtrennzeichen ist eine oder mehrere dieser ASCII-Escape-Zeichen oder ASCII-hex-Werten...  
  
|Name|Escapezeichen|Hexadezimale Zeichen|  
|--------|--------------------|-----------------|  
|Registerkarte|\t|0x09|  
|Wagenrücklauf (CR)|\r|0x0D|  
|Zeilenvorschubzeichen (LF)|\n|0x0a|  
|CRLF|\r\n|0x0d0x0a|  
|Komma|','|0x2c|  
|Doppeltes Anführungszeichen|\\"|0x22|  
|einfaches Anführungszeichen|\\'|0x27|  
  
Um den senkrechten Strich in der Befehlszeile angeben, müssen Sie ihn in doppelte Anführungszeichen "|". Dies wird vom Befehlszeilenparser zu Fehlinterpretation vermeiden. Andere Zeichen sind einfache Anführungszeichen eingeschlossen.  
  
Beispiele:  
  
-t "|"  
  
-t ""  
  
-t 0x0a  
  
-t \t  
  
-t ' ~ | ~'  
  
**-R** *Row_delimiter*  
Das Trennzeichen für jede Zeile der Datendatei der Quelle. Das Zeilentrennzeichen ist mindestens eine ASCII-Werten.  
  
Um ein Wagenrücklauf (CR), Zeilenvorschubzeichen (LF) oder Tabstoppzeichen als Trennzeichen angeben, können Sie die Escape-Zeichen ("\r", "\n", "\t") oder ihre Hexadezimalwerte (0 X, 0d, 09) verwenden. Um ein anderes Sonderzeichen als Trennzeichen angeben, verwenden Sie ihren Hexadezimalwert.  
  
Beispiele für CR -LF:  
  
-R-\r\n  
  
-R-0x0d0x0a  
  
Beispiele für CR:  
  
-R-\r  
  
-R 0x0d  
  
Beispiele für LF:  
  
-R \n  
  
-R 0x0a  
  
Ein LF ist erforderlich für Unix. Ein CR ist für Windows erforderlich.  
  
**-s** *String_delimiter*  
Das Trennzeichen für Zeichenfolgendaten Typfeld der eine Datei mit Texttrennzeichen an. Das Zeichenfolgen-Trennzeichen ist eine oder mehrere ASCII-Werten.  Er kann als Zeichen angegeben werden (z. B. -s *) oder als einen hexadezimalen Wert (z. B. -s 0 x 22 für ein doppeltes Anführungszeichen).  
  
Beispiele:  
  
-s *  
  
-s 0 x 22  
  
< Fixed_width_column_options >  
Die Optionen für eine Quelldatei für die Daten, die Spalten fester Länge aufweist. In der Standardeinstellung *Source_data_file_name* ASCII-Zeichen in Spalten variabler Länge enthält.  
  
Spalten mit fester Breite werden nicht unterstützt, wenn – e UTF8 ist.  
  
**-w** *Fixed_width_config_file*  
Pfad und Name der Konfigurationsdatei, die die Anzahl der Zeichen in jeder Spalte angibt. Jedes Feld muss angegeben werden.  
  
Diese Datei muss auf dem Server laden befinden. Der Pfad kann es sich um einen UNC-relativer oder absoluter Pfad sein. Jede Zeile in *Fixed_width_config_file* enthält den Namen einer Spalte und die Anzahl der Zeichen für diese Spalte. Ist es eine Zeile pro Spalte wie folgt, und die Reihenfolge, in die Datei muss die Reihenfolge, in der Zieltabelle übereinstimmen:  
  
*Column_name*=*Num_chars*  
  
*Column_name*=*Num_chars*  
  
Beispiel für feste Breite Config-Datei:  
  
SalesCode = 3  
  
SalesID = 10  
  
Beispiel für Zeilen in *Source_data_file_name*:  
  
230Shirts0056  
  
320Towels1356  
  
Im vorherigen Beispiel hat die erste geladene Zeile SalesCode = "230" und SalesID = "Shirts0056". Die zweite geladene Zeile müssen SalesCode = "320" und SaleID = "Towels1356".  
  
Informationen zum Behandeln der führende und nachfolgende Leerzeichen oder Daten typkonvertierung im Modus mit fester Breite finden Sie unter [Datentyp Konvertierungsregeln für Dwloader](dwloader-data-type-conversion-rules.md).  
  
**-e:** *Character_encoding*  
Gibt einen Typ zeichencodierung für die Daten aus der Datendatei geladen werden. Stehen, ASCII (Standard) "," UTF8 "," UTF16 "oder" UTF16BE, wobei UTF16-Format little-endian und UTF16BE ist big-Endian. Diese Optionen, die Groß-/Kleinschreibung beachtet werden.  
  
Spalten mit fester Breite werden nicht unterstützt, wenn – e UTF8 ist.  
  
**-R** *Row_delimiter*  
Das Trennzeichen für jede Zeile der Datendatei der Quelle. Das Zeilentrennzeichen ist mindestens eine ASCII-Werten.  
  
Um ein Wagenrücklauf (CR), Zeilenvorschubzeichen (LF) oder Tabstoppzeichen als Trennzeichen angeben, können Sie die Escape-Zeichen ("\r", "\n", "\t") oder ihre Hexadezimalwerte (0 X, 0d, 09) verwenden. Um ein anderes Sonderzeichen als Trennzeichen angeben, verwenden Sie ihren Hexadezimalwert.  
  
Beispiele für CR -LF:  
  
-R-\r\n  
  
-R-0x0d0x0a  
  
Beispiele für CR:  
  
-R-\r  
  
-R 0x0d  
  
Beispiele für LF:  
  
-R \n  
  
-R 0x0a  
  
Ein LF ist erforderlich für Unix. Ein CR ist für Windows erforderlich.  
  
**-D** { **Ymd** | Ydm | Mdy | Myd |  DMY | Dym | *Custom_date_format* }  
Gibt die Reihenfolge der Monat (m), (d) Tag und Jahr (y) für alle Datetime-Felder in der Eingabedatei an. Die Standardreihenfolge ist Ymd. Um mehrere Order-Formate für die gleiche Quelldatei anzugeben, verwenden Sie die -dt-Option.  
  
YMD | DMY  
Das Ydm und Dmy können die gleichen Eingabeformate. Beide ermöglichen das Jahr am Anfang oder Ende des Datums sein. Z. B. für beide **Ydm** und **Dmy** Datumsformate, Sie können die 2013-02-03 oder 02-03-2013 haben, in der Eingabedatei.  
  
Das ydm  
Sie können nur als Ydm in Spalten vom Datentyp Datetime und Smalldatetime formatierte Eingabe laden. Sie können nicht das Ydm-Werte in eine Spalte mit dem datetime2, Datums- oder Datetimeoffset-Datentyp laden.  
  
dmy  
ermöglicht das Mdy <month> <space> <day> <comma> <year>.  
  
Beispiele für Mdy Eingabedaten für den 1. Januar 1975:  
  
-   Ab dem 1. Januar 1975  
  
-   Jan 01, 75  
  
-   Jan/1/75  
  
-   01011975  
  
myd  
Geben Sie Beispiele für März 04,2010: 03-2010-04, 3/2010/4  
  
dym  
Beispiele für die Eingabedatei für 04 März 2010: 04-2010-03, 4/2010/3  
  
*custom_date_format*  
*Custom_date_format* ist einem benutzerdefinierten Datumsformat entsprechen (z. B. MM/TT/JJJJ) und nur für Abwärtskompatibilität enthalten. Dwloader führt nicht Enfoce das benutzerdefinierte Datumsformat aus. Wenn Sie stattdessen ein benutzerdefiniertes Datumsformat angeben **Dwloader** konvertiert sie in die entsprechende Einstellung der Ymd Ydm, Mdy, MYD-, Dym oder Dmy.  
  
Wenn Sie den -D MM/TT/JJJJ angeben, erwartet Dwloader z. B. alle Geben Sie zunächst mit Monat bestellt werden Datum und Tag und anschließend im Jahr (Mdy). 2 Monate für Zeichen, 2 Ziffern Tage und 4 Ziffern Jahre laut das benutzerdefinierte Datumsformat erzwungen nicht. Hier sind einige Beispiele für die Datumsangaben in der Eingabedatei formatiert werden können, wenn das Datum das Format ' -D MM/TT/JJJJ ist: 01/02/2013, Jan.02.2013, 1/2/2013  
  
Eine umfassendere Formatierungsinformationen, finden Sie unter [Datentyp Konvertierungsregeln für Dwloader](dwloader-data-type-conversion-rules.md).  
  
**-dt** *Datetime_format_file*  
Jede Datetime-Format wird angegeben, in einer Datei namens *Datetime_format_file*. Im Gegensatz zu den Befehlszeilenparametern benötigen müssen die Parameter der Datei, die Leerzeichen enthalten nicht in doppelte Anführungszeichen eingeschlossen werden. Sie können das Datetime-Format nicht ändern, wie Sie Daten laden. Die Quelldatei und der entsprechenden Spalte in die Zieltabelle müssen das gleiche Format aufweisen.  
  
Jede Zeile enthält den Namen einer Spalte in der Zieltabelle und das Datetime-Format.  
  
Beispiele:  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *Staging_database_name*  
Der Name der Datenbank, die die Stagingtabelle enthalten soll. Der Standardwert ist die Datenbank mit der Option "-T", d.h. der Datenbank für die Zieltabelle angegeben werden. Weitere Informationen zur Verwendung einer Stagingdatenbank finden Sie unter [erstellen Sie die Staging-Datenbank](staging-database.md).  
  
**-M** *Load_mode_option*  
Gibt an, ob anzufügen, "Upsert", oder die Daten erneut zu laden. Der Standardmodus ist angefügt.  
  
Anfügen  
Das Ladeprogramm Zeilen am Ende der vorhandenen Zeilen in der Zieltabelle eingefügt.  
  
fastappend  
Das Ladeprogramm Zeilen direkt ohne Verwendung einer temporären Tabelle am Ende der vorhandenen Zeilen in der Zieltabelle eingefügt. Fastappend erfordert die Multi-Transaktion (-m) Option. Eine Stagingdatenbank kann nicht angegeben werden, wenn Fastappend verwenden. Es ist kein Rollback mit Fastappend, was bedeutet, dass die Wiederherstellung nach einer fehlerhaften oder abgebrochenen Last durch Ihre eigenen Load-Prozess verarbeitet werden muss.  
  
"Upsert" **-K***Merge_column* [,... *n* ]    
Das Ladeprogramm verwendet die SQL Server-Merge-Anweisung zum Aktualisieren von vorhandener Zeilen aus, und fügen Sie neue Zeilen.  
  
Die Option ' -K ' gibt an, die Spalte oder Spalten, auf die Zusammenführung basieren. Diese Spalten bilden einen Merge-Schlüssel, der eine eindeutige Zeile darstellen soll. Wenn der Merge-Schlüssel in der Zieltabelle vorhanden ist, wird die Zeile aktualisiert. Wenn der Merge-Schlüssel in der Zieltabelle nicht vorhanden ist, wird die Zeile angefügt.  
  
Für Tabellen mit hashverteilung muss der Merge-Schlüssel werden oder die verteilungsspalte enthalten.  
  
Für replizierte Tabellen ist der Merge-Schlüssel die Kombination einer oder mehreren Spalten. Diese Spalten werden gemäß den Anforderungen der Anwendung angegeben.  
  
Mehrere Spalten müssen ohne Leerzeichen, Kommas oder Leerzeichen durch Kommas getrennt und in einfache Anführungszeichen eingeschlossen sein.  
  
Wenn zwei Zeilen in der Quelltabelle entsprechende Merge-Schlüsselwerte verfügen, müssen die entsprechenden Zeilen identisch sein.  
  
Erneut laden  
Das Ladeprogramm schneidet die Zieltabelle ab, bevor die Daten eingefügt.  
  
**-b** *batchsize*  
Nur für die Verwendung von Microsoft-Support, empfohlene *Batchsize* beträgt die Batchgröße für SQL Server für das Massenkopieren, die DMS in SQL Server-Instanzen auf den Computeknoten ausführt.  Wenn *Batchsize* angegeben ist, wird SQL Server PDW überschreibt die Batchgröße für das Laden, die bei jedem Laden der dynamisch berechnet wird.  
  
Ab SQL Server 2012 PDW, berechnet der Steuerelementknoten aus dynamisch eine Batchgröße bei jedem Laden standardmäßig. Diese automatische Berechnung basiert auf mehrere Parameter wie Größe des Speichers, Zieltyp für die Tabelle, Tabelle Zielschema, Art der Arbeitslast, Dateigröße und Ressourcenklasse des Benutzers.  
  
Z. B. wenn der Lademodus FASTAPPEND und die Tabelle einen gruppierten columnstore-Index besitzt, SQL Server PDW wird von versuchen standardmäßig, eine Batchgröße von 1.048.576 verwenden, sodass Zeilengruppen geschlossen werden, und Laden direkt in den columnstore-Index ohne Umweg über das deltastore. Wenn die Batchgröße von 1.048.576 von Arbeitsspeicher nicht möglich ist, wählt Dwloader eine kleinere Batchgröße.  
  
Wenn die Art der Arbeitslast FASTAPPEND, ist der *Batchsize* gilt für das Laden von Daten in die Tabelle, andernfalls *Batchsize* gilt für das Laden von Daten in die Stagingtabelle.  
  
<reject_options>  
Gibt Optionen zum Bestimmen der Anzahl der Fehler beim Laden von, denen das Ladeprogramm ermöglichen. Wenn der Fehler beim Laden von den Schwellenwert überschreiten, wird das Ladeprogramm angehalten und keinen commit für alle Zeilen.  
  
**-rt** { **Wert** | Prozentsatz}  
Gibt an, ob die -*Reject_value* in die **-rv** *Reject_value* Option ist eine literale Anzahl von Zeilen (Wert) oder einem Satz von Fehler (in Prozent). Der Standardwert ist.  
  
Die Prozentsatz-Option ist eine Echtzeit-Berechnung, die in Abständen gemäß der Option - Rs tritt ein, an.  
  
Beispielsweise ist, wenn der Loader beim Laden von 100 Zeilen und 25 Beschaffung und 75 erfolgreich ist, klicken Sie dann die Fehlerrate 25 %.  
  
**-rv** *Reject_value*  
Gibt an, die Anzahl oder den Prozentsatz der ablehnungen der Zeile, um vor dem Anhalten der Last zu ermöglichen. Die **-rt** Option bestimmt, ob *Reject_value* bezieht sich auf die Anzahl der Zeilen oder den Prozentsatz der Zeilen.  
  
Der Standardwert *Reject_value* ist 0.  
  
Bei Verwendung mit -rt-Wert wird das Ladeprogramm die Last beendet, wenn die Anzahl der abgelehnten Zeilen Reject_value überschreitet.  
  
Wenn mit -rt-Prozentsatz, das Ladeprogramm berechnet den Prozentsatz in Intervallen (-Rs-Option). Aus diesem Grund kann der Prozentsatz fehlerhafter Zeilen überschreiten *Reject_value*.  
  
**Rs -** *Reject_sample_size*  
Verwendung der `-rt percentage` Option aus, um die Überprüfungen inkrementelle Prozentsatz angeben. Z. B. wenn Reject_sample_size 1000 ist, wird das Ladeprogramm berechnet den Prozentsatz fehlerhafter Zeilen nach dem Laden von 1000 Zeilen. Es berechnet den Prozentsatz von fehlerhaften Zeilen neu, nachdem sie versucht, jede zusätzliche 1000 Zeilen zu laden.  
  
**-c**  
Entfernt Leerstellen vom linken und rechten Seite des Char, Nchar, Varchar und Nvarchar-Felder. Konvertiert jedes Feld, das nur Leerraumzeichen auf eine leere Zeichenfolge enthält.  
  
Beispiele:  
  
"" Ruft auf gekürzt. "  
  
auf 'Abc' Ruft 'Abc' gekürzt.  
  
Bei der -c mit -E, wird zuerst die -E-Operation. Felder, die nur Leerzeichen enthalten, werden auf eine leere Zeichenfolge und nicht auf NULL konvertiert.  
  
**-E**  
Konvertieren Sie leere Zeichenfolgen, auf NULL. Der Standardwert ist keine dieser Konvertierungen durchzuführen.  
  
**-m**  
Verwenden von mehreren Transaktionsmodus für die zweite Phase des Ladevorgangs; Beim Laden von Daten aus der Stagingtabelle in eine verteilte Tabelle.  
  
Mit **-m**, SQL Server PDW führt und führt einen Commit für Ladevorgänge parallel. Dies wird erheblich schneller als die standardmäßige laden Modus ausgeführt, aber es ist nicht Transaktion-sicher.  
  
Ohne **-m**, SQL Server PDW führt und führt einen Commit für Ladevorgänge seriell auf die Verteilungen in jedem Computeknoten aus, und gleichzeitig auf die Compute-Knoten. Diese Methode ist langsamer als die Multi-Transaktionsmodus, aber Transaktion threadsicher ist.  
  
**-m** ist optional für *Anfügen*, *laden*, und *Upsert*.  
  
**-m** für Fastappend ist erforderlich.  
  
**-m** bei replizierten Tabellen nicht verwendet werden.  
  
**-m** gilt nur für die zweite Phase der laden. Es gilt nicht für die erste Phase der laden; Laden von Daten in die Stagingtabelle ein.  
  
Es ist kein Rollback mit Multi-Transaktionsmodus, was bedeutet, dass die Wiederherstellung nach einer fehlerhaften oder abgebrochenen Last durch Ihre eigenen Load-Prozess verarbeitet werden muss.  
  
Es wird empfohlen, **-m** nur, wenn in eine leere Tabelle, geladen, sodass Sie ohne Datenverlust wiederherstellen können. Zur Wiederherstellung nach einem Fehler beim Laden des: die Zieltabelle löschen, das Load-Problem zu beheben, die Zieltabelle neu zu erstellen und führen Sie die Last dann erneut aus.  
  
**-N**  
Stellen Sie sicher, dass die zielappliance ein gültiges SQL Server-PDW-Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle verfügt. Verwenden Sie diese, um sicherzustellen, Ihre Daten wird nicht von einem Angreifer übernommen und an einen nicht autorisierten Speicherort gesendet. Das Zertifikat muss bereits auf dem Gerät installiert werden. Die einzige unterstützte Methode zum Installieren des Zertifikats ist für die applianceadministrator ihn mithilfe des Konfigurations-Manager installieren. Bitten Sie Ihren applianceadministrator, wenn Sie nicht sicher sind, gibt an, ob das Gerät ein vertrauenswürdiges Zertifikat installiert wurde.  
  
**Se-**  
Überspringen Sie das leere Dateien werden geladen. Dies lässt auch leere Gzip Dekomprimieren von Dateien.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
0 (Erfolg) oder andere ganzzahlige Wert (Fehler)  
  
Verwenden Sie in einer Befehlsdatei Fenster oder einen Batch `errorlevel` um den Rückgabecode anzuzeigen. Zum Beispiel:  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
Wenn Sie PowerShell verwenden möchten, verwenden Sie `$LastExitCode`.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert LOAD-Berechtigung und die entsprechenden Berechtigungen (INSERT, UPDATE, DELETE) für die Zieltabelle an. Erfordert die Berechtigung "erstellen" (zum Erstellen einer temporären Tabelle) für die staging-Datenbank. Wenn eine Stagingdatenbank nicht verwendet wird, ist der Berechtigung "erstellen" in der Zieldatenbank erforderlich. 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
Weitere Informationen zu datentypkonvertierungen beim Laden mit Dwloader, finden Sie unter [Datentyp Konvertierungsregeln für Dwloader](dwloader-data-type-conversion-rules.md).  
  
Wenn ein Parameter ein oder mehrere Leerzeichen enthält, müssen Sie den Parameter in doppelte Anführungszeichen ein.  
  
Sie sollten das Ladeprogramm aus dem Installationsverzeichnis ausführen. Die ausführbare Datei Dwloader ist mit dem Gerät vorinstalliert und befindet sich im Verzeichnis C:\Program Files\Microsoft SQL Server Data Warehouse\DWLoader.  
  
Sie können einen Parameter, der in der Parameterdatei angegeben wird überschreiben (-f-Option) durch Angabe als Befehlszeilenparameter.  
  
Sie können mehrere Instanzen des Ladeprogramms gleichzeitig ausführen. Die maximale Anzahl von Instanzen der Ladeprogramm ist vorkonfiguriert und kann nicht geändert werden. 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
Geladene Daten möglicherweise mehr oder weniger Speicherplatz auf dem Gerät als am Quellstandort. Sie können Test-Importen mit Teilmengen von Daten zum Schätzen der Datenträger ausführen.  
  
Obwohl **Dwloader** ist ein Prozess für die Transaktion und führt ein Rollback ordnungsgemäß bei einem Fehler, kann nicht zurückgesetzt werden, sobald das Massenladen erfolgreich abgeschlossen wurde. Zum Abbrechen von einer aktives **Dwloader** verarbeiten, STRG + C eingeben.  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
Die Gesamtgröße aller lädt, die gleichzeitig ausgeführt werden, muss kleiner sein als LOG_SIZE für die Datenbank, und es wird empfohlen, die Gesamtgröße aller paralleler Ladevorgänge ist weniger als 50 % von dem LOG_SIZE. Um diese maximale Größe zu erzielen, können Sie große Datenmengen in mehrere Batches aufteilen. Weitere Informationen zu LOG_SIZE, finden Sie unter [Datenbank erstellen](../t-sql/statements/create-database-parallel-data-warehouse.md)  
  
Wenn Sie mehrere Dateien mit einem Befehl zu laden, werden alle abgelehnte Zeilen in der gleichen Reject-Datei geschrieben. Die Reject-Datei zeigt nicht an die Eingabedatei jede abgelehnte Zeile enthält.  
  
Die leere Zeichenfolge sollte nicht als Trennzeichen verwendet werden. Wenn eine leere Zeichenfolge als ein Zeilentrennzeichen verwendet wird, schlägt der Ladevorgang fehl. Als Trennzeichen für Spalten verwendet, wird die Last ignoriert das Trennzeichen und weiterhin die Standardeinstellung verwenden "|" als Spaltentrennzeichen. Die leere Zeichenfolge wird ignoriert, wenn Sie als Zeichenfolgen-Trennzeichen verwendet wird, und das Standardverhalten angewendet.  
  
## <a name="locking-behavior"></a>Sperrverhalten  
**Dwloader** Sperrverhalten variiert je nach den *Load_mode_option*.  
  
-   **Fügen Sie** -Anfügen ist die empfohlene und am häufigsten verwendete Option. Fügen Sie lädt Daten in eine Stagingtabelle ein. Das Sperren wird unten im Detail beschrieben.  
  
-   **Fügen Sie schnell** -Fast-fügen Sie direkt in der endgültigen Tabelle eine ExclusiveUpdate-Tabellensperre dauert lädt und ist der einzige Modus, die eine Stagingtabelle nicht verwendet.  
  
-   **erneut laden** – erneutes Laden von Daten in eine Stagingtabelle geladen und erfordert eine exklusive Sperre auf die Stagingtabelle und die endgültige Tabelle. Erneut laden, sollte nicht für gleichzeitige Vorgänge.  
  
-   **"Upsert"** -Upsert-Vorgang Daten in eine Stagingtabelle geladen und führt dann einen Merge-Vorgang aus der Stagingtabelle in die endgültige Tabelle. "Upsert" ist keine exklusive Sperren für die endgültige Tabelle erforderlich. Leistung kann abweichen, wenn "Upsert" verwenden. Testen Sie das Verhalten in Ihrer Umgebung.  
  
### <a name="locking-behavior"></a>Sperrverhalten  
**Eine Append-Modus-sperren**  
  
Fügen Sie kann in mehreren im Transaktionsmodus ausgeführt wird (mit dem -m-Argument) ausgeführt werden aber nicht sicher Transaktion. Fügen Sie aus diesem Grund sollte als ein Transaktionsvorgang (ohne das -m-Argument) verwendet werden. Leider ist während des letzten INSERT-SELECT-Vorgangs im Transaktionsmodus derzeit ungefähr sechs Mal langsamer als die Multi-Transaktionsmodus.  
  
Die Append-Modus lädt Daten in zwei Phasen. Phase 1 lädt Daten aus der Quelldatei, in eine Stagingtabelle gleichzeitig (Fragmentierung erfolgen kann). Phase zwei Daten aus der Stagingtabelle in die endgültige Tabelle geladen. Die zweite Phase führt eine **INSERT INTO... Wählen Sie WITH (TABLOCK)** Vorgang. Die folgende Tabelle zeigt das Sperrverhalten für die endgültige Tabelle und Protokollierungsverhalten Verwendung append-Modus:  
  
|Tabellentyp|Multi-Transaktion<br />Modus (-m)|Tabelle ist leer|Parallelität unterstützt|Protokollierung|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|Heap|Ja|Ja|Ja|Minimale|  
|Heap|Ja|Nein|Ja|Minimale|  
|Heap|Nein|Ja|Nein|Minimale|  
|Heap|Nein|Nein|Nein|Minimale|  
|CL|Ja|Ja|Nein|Minimale|  
|CL|Ja|Nein|Ja|Vollständig|  
|CL|Nein|Ja|Nein|Minimale|  
|CL|Nein|Nein|Ja|Vollständig|  
  
Die obige Tabelle zeigt **Dwloader** im Append-Modus Laden in einen Heap oder gruppierten Index (CI) Table mit oder ohne das Flag mit mehreren Transaktionen und das Laden in eine leere Tabelle oder eine nicht leere Tabelle. Der Sperr- und Protokollierungsverhaltens Verhalten jeden solchen Kombination aus laden wird in der Tabelle angezeigt. Z. B., (2.) Phase mit der Append-Modus Laden in einen gruppierten Index ohne Multi-Transaktionsmodus ausgeführt wird und in eine leere Tabelle weist PDW eine exklusive Sperre für die Tabelle zu erstellen und Protokollierung ist minimal. Dies bedeutet, dass ein Kunde nicht (2.) Phase und die Abfrage in eine leere Tabelle gleichzeitig laden können. Jedoch wenn Sie mit der gleichen Konfiguration in eine nicht leere Tabelle zu laden, PDW keine exklusive Sperre für die Tabelle ausgeben und Parallelität möglich ist. Unpraktischerweise erfolgt vollständige Protokollierung, den Prozess verlangsamen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-simple-dwloader-example"></a>A. Beispiel für einfache dwloader  
Das folgende Beispiel zeigt die Initiierung der **Ladeprogramm** nur mit den erforderlichen Optionen ausgewählt haben. Andere Optionen für die globale XML-Konfigurationsdatei entnommen werden *loadparamfile.txt*.  
  
Beispiel für die Verwendung von SQL Server-Authentifizierung.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
Das gleiche Beispiel, das mithilfe der Windows-Authentifizierung.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -W -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -W -f /configfiles/loadparamfile.txt  
```  
  
Beispiel für die Verwendung der Argumente für eine Quelldatei und die Fehlerdatei.  
  
```  
--Load over Ethernet  
dwloader.exe -U mylogin -P 123jkl -S 10.192.63.148  -i C:\SQLData\AWDimEmployees.csv -T AdventureWorksPDW2012.dbo.DimEmployees -R C:\SQLData\LoadErrors  
```  
  
### <a name="b-load-data-into-an-adventureworks-table"></a>B. Laden von Daten in einer AdventureWorks-Tabelle  
Das folgende Beispiel ist Teil eines Batchskripts, die Daten in lädt **AdventureWorksPDW2012**.  Um das vollständige Skript anzuzeigen, öffnen Sie die "aw_create.bat"-Datei, die im Lieferumfang der **AdventureWorksPDW2012** Installationspaket. 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

Der folgende Codeausschnitt verwendet Dwloader zum Laden von Daten in die Tabellen DimAccount und DimCurrency. Dieses Skript wird eine Ethernet-Adresse verwendet. Wenn es InfiniBand verwendet hat, wäre Server *< Appliancename >*`-SQLCTL01`.  
  
```  
set server=10.193.63.134  
set user=<MyUser>  
set password=<MyPassword>  
  
set schema=AdventureWorksPDW2012.dbo  
set load="C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe"  
set mode=reload  
  
--Loads data into the AdventureWorksPDW2012.dbo.DimAccount table  
--Source data is stored in the file DimAccount.txt,   
--which is in the current directory.  
  
set t1=DimAccount  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%   
  
--Loads data from the DimCurrency.txt file into  
--AdventureWorksPDW2012.dbo.DimCurrency  
set t1=DimCurrency  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%  
```  
  
Im folgenden wird die DDL-Anweisungen für die DimAccount-Tabelle.  
  
```  
CREATE TABLE DimAccount(  
AccountKey int NOT NULL,  
ParentAccountKey int,  
AccountCodeAlternateKey int,  
ParentAccountCodeAlternateKey int,  
AccountDescription nvarchar(50),  
AccountType nvarchar(50),  
Operator nvarchar(50),  
CustomMembers nvarchar(300),  
ValueType nvarchar(50),  
CustomMemberOptions nvarchar(200))  
with (CLUSTERED INDEX(AccountKey),  
DISTRIBUTION = REPLICATE);  
```  
  
Folgendes ist ein Beispiel für die Datendatei DimAccount.txt, die Daten, die in die Tabelle DimAccount geladen werden sollen.  
  
```  
--Sample of data in the DimAccount.txt load file.  
  
1||1||Balance Sheet||~||Currency|  
2|1|10|1|Assets|Assets|+||Currency|  
3|2|110|10|Current Assets|Assets|+||Currency|  
4|3|1110|110|Cash|Assets|+||Currency|  
5|3|1120|110|Receivables|Assets|+||Currency|  
6|5|1130|1120|Trade Receivables|Assets|+||Currency|  
7|5|1140|1120|Other Receivables|Assets|+||Currency|  
8|3|1150|110|Allowance for Bad Debt|Assets|+||Currency|  
9|3|1160|110|Inventory|Assets|+||Currency|  
10|9|1162|1160|Raw Materials|Assets|+||Currency|  
11|9|1164|1160|Work in Process|Assets|+||Currency|  
12|9|1166|1160|Finished Goods|Assets|+||Currency|  
13|3|1170|110|Deferred Taxes|Assets|+||Currency|  
```  
  
### <a name="c-load-data-from-the-command-line"></a>C. Laden von Daten über die Befehlszeile  
Das Skript in Beispiel B kann ersetzt werden, indem Sie alle Parameter in der Befehlszeile eingeben, wie im folgenden Beispiel gezeigt.  
  
```  
C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe -S <Control node IP> -E -M reload -e UTF16 -i .\DimAccount.txt -T AdventureWorksPDW2012.dbo.DimAccount -R DimAccount.bad -t "|" -r \r\n -U <login> -P <password>  
```  
  
Beschreibung der Befehlszeilenparameter:  
  
-   *C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe* Installationsort der dwloader.exe ist.  
  
-   *-S* die IP-Adresse des steuerungsknotens folgt.  
  
-   *-E:* gibt an, dass Sie leere Zeichenfolgen als NULL laden.  
  
-   *Laden Sie -M* gibt an, dass die Zieltabelle abgeschnitten werden, bevor die Daten eingefügt.  
  
-   *-e: UTF16* gibt an, die Quelldatei verwendet Zeichencodierungstyp mit little-endian.  
  
-   *-i.\DimAccount.txt* gibt an, die Daten in einer Datei namens DimAccount.txt, die im aktuellen Verzeichnis vorhanden ist.  
  
-   *-T AdventureWorksPDW2012.dbo.DimAccount* gibt den Namen der 3-Teil der Tabelle, die die Daten zu empfangen.  
  
-   *-R DimAccount.bad* gibt an, die Zeilen, die nicht geladen werden in eine Datei namens DimAccount.bad geschrieben.  
  
-   *-t "|"*  gibt an, die Felder in der Eingabedatei DimAccount.txt, durch den senkrechten Strich getrennt sind.  
  
-   *-R-\r\n* gibt jede Zeile in DimAccount.txt endet mit einem Wagenrücklauf und ein Zeilenvorschubzeichen.  
  
-   *-U < Login_name > -P <password>*  gibt an, dem Anmeldenamen und Kennwort für die Anmeldung, die über Berechtigungen zum Ausführen der Last verfügt.  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
  
