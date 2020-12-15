---
title: "\"dwloader-Command-Line Lade Modul"
description: "\"dwloader ist ein Befehlszeilen Tool für parallele Data Warehouse (PDW), das Tabellenzeilen in einem Massen Vorgang in eine vorhandene Tabelle lädt."
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3635aff3c3dad371c969acd3d72b2fb738748ecc
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489690"
---
# <a name="dwloader-command-line-loader-for-parallel-data-warehouse"></a>"dwloader Command-Line Loader für parallele Data Warehouse
**"dwloader** ist ein Befehlszeilen Tool für parallele Data Warehouse (PDW), das Tabellenzeilen in einem Massen Vorgang in eine vorhandene Tabelle lädt. Beim Laden von Zeilen können Sie alle Zeilen am Ende der Tabelle (*Anfügen* -oder *vom fastappend Lademodus-Modus*) hinzufügen, neue Zeilen anfügen und vorhandene Zeilen aktualisieren (*Upsert-Modus*) oder alle vorhandenen Zeilen vor dem Laden löschen und dann alle Zeilen in eine leere Tabelle (erneuten *laden Modus*) einfügen.  
  
**Prozess zum Laden von Daten**  
  
1.  Vorbereiten der Quelldaten.  
  
    Verwenden Sie Ihren eigenen ETL-Prozess zum Erstellen der Quelldaten, die Sie laden möchten. Die Quelldaten müssen so formatiert werden, dass Sie dem Schema der Ziel Tabelle entsprechen. Speichern Sie die Quelldaten in einer oder mehreren Textdateien, und kopieren Sie die Textdateien in dasselbe Verzeichnis auf dem Lade Server. Weitere Informationen zum Lade Server finden Sie unter Abrufen [und Konfigurieren eines Lade Servers](acquire-and-configure-loading-server.md) .  
  
2.  Bereiten Sie die Lade Optionen vor.  
  
    Entscheiden Sie, welche Lade Optionen verwendet werden sollen. Speichert die Lade Optionen in einer Konfigurationsdatei. Kopieren Sie die Konfigurationsdatei an einen lokalen Speicherort auf dem Lade Server. Die **"dwloader** -Konfigurationsoptionen werden in diesem Thema beschrieben.  
  
3.  Bereiten Sie die Optionen für den Ladefehler vor.  
  
    Entscheiden Sie, wie **"dwloader** Zeilen verarbeiten soll, die nicht geladen werden können. Zum Ausführen der Last lädt **"dwloader** zuerst die Daten in eine Stagingtabelle und überträgt dann die Daten in die Ziel Tabelle. Wenn das Lade Modul Daten in die Stagingtabelle lädt, wird die Anzahl der Zeilen nachverfolgt, die nicht geladen werden können. Beispielsweise können Zeilen, die nicht ordnungsgemäß formatiert sind, nicht geladen werden. Fehlgeschlagene Zeilen werden in eine Ablehnungs Datei kopiert. Standardmäßig wird die Last nach der ersten Ablehnung abgebrochen, es sei denn, Sie geben einen anderen Ablehnungs Schwellenwert an.  
  
4.  Installieren von **"dwloader**.  
  
    Installieren Sie "dwloader auf dem Server, auf dem der Server nicht bereits installiert ist. 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  Führen Sie **"dwloader** aus.  
  
    Melden Sie sich beim Lade Server an, und führen Sie die ausführbare **dwloader.exe** mit den entsprechenden Befehlszeilenoptionen aus.  
  
6.  Überprüfen Sie die Ergebnisse.  
  
    Sie können die Datei mit den fehlgeschlagenen Zeilen (angegeben mit-R) überprüfen, um festzustellen, ob Zeilen nicht geladen werden konnten. Wenn diese Datei leer ist, wurden alle Zeilen erfolgreich geladen. **"dwloader** ist transaktional. Wenn also ein Schritt fehlschlägt (außer abgelehnte Zeilen), werden alle Schritte in den ursprünglichen Zustand zurückgesetzt.  
  
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
    [ -l ]   
}  
```  
  
## <a name="arguments"></a>Argumente  
**-h**  
Zeigt einfache Hilfe Informationen zur Verwendung des Lade Moduls an. Hilfe wird nur angezeigt, wenn keine anderen Befehlszeilenparameter angegeben sind.  
  
**-U** *login_name*  
Eine gültige SQL Server-Authentifizierungs Anmeldung mit den entsprechenden Berechtigungen zum Ausführen der Last.  
  
**-P** *Kennwort*  
Das Kennwort für eine SQL Server Authentifizierungs *login_name*.  
  
**-W**  
Windows-Authentifizierung verwenden. (Weder *login_name* noch *ein Kennwort* erforderlich.) 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *parameter_file_name*  
Verwenden Sie eine Parameterdatei ( *parameter_file_name*) anstelle von Befehlszeilen Parametern. *parameter_file_name* können jeden beliebigen Befehlszeilenparameter mit Ausnahme von *user_name* und *Kennwort* enthalten. Wenn ein Parameter in der Befehlszeile und in der Parameterdatei angegeben ist, überschreibt die Befehlszeile den file-Parameter.  
  
Die Parameterdatei enthält einen Parameter ohne das **-** Präfix pro Zeile.  
  
Beispiele:  
  
`rt=percentage`  
  
`rv=25`  
  
**-S** *target_appliance*  
Gibt die SQL Server PDW Appliance an, die die geladenen Daten empfängt.  
  
*Bei Infiniband-Verbindungen* wird *target_appliance* als <Appliance-Name>-SQLCTL01 angegeben. Informationen zum Konfigurieren dieser benannten Verbindung finden Sie unter [Konfigurieren von InfiniBand-Netzwerkadaptern](configure-infiniband-network-adapters.md).  
  
Bei Ethernet-Verbindungen ist *target_appliance* die IP-Adresse für den Steuerelement Knoten Cluster.  
  
Wenn der Wert nicht angegeben wird, verwendet "dwloader standardmäßig den Wert, der bei der Installation von" dwloader angegeben wurde. 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *target_database_name.* [*Schema*]. *table_name*  
Der dreiteilige Name der Ziel Tabelle.  
  
**-I** *source_data_location*  
Der Speicherort für eine oder mehrere zu ladende Quelldateien. Jede Quelldatei muss eine Textdatei oder eine Textdatei sein, die mit gzip komprimiert ist. In jeder GZIP-Datei kann nur eine Quelldatei komprimiert werden.  
  
So formatieren Sie eine Quelldatei:  
  
-   Die Quelldatei muss entsprechend den Lade Optionen formatiert werden.  
  
-   Jede Zeile in einer Quelldatei enthält die Daten für eine Tabellenzeile. Die Quelldaten müssen dem Schema der Ziel Tabelle entsprechen. Die Spaltenreihenfolge und die Datentypen müssen ebenfalls Stimmen. Jedes Feld in der Zeile stellt eine Spalte in der Ziel Tabelle dar.  
  
-   Standardmäßig sind die Felder variabler Länge und werden durch ein Trennzeichen getrennt. Um den Trenn Zeichentyp anzugeben, verwenden Sie die Befehlszeilenoptionen <variable_length_column_options>. Um Felder mit fester Länge anzugeben, verwenden Sie die Befehlszeilenoptionen <fixed_width_column_options>.  
  
So geben Sie den Quelldaten Speicherort an  
  
-   Beim Quelldaten Speicherort kann es sich um einen Netzwerkpfad oder einen lokalen Pfad zu einem Verzeichnis auf dem Lade Server handeln.  
  
-   Wenn Sie alle Dateien in einem Verzeichnis angeben möchten, geben Sie den Verzeichnispfad ein, gefolgt von dem Platzhalter Zeichen *.  Das Lade Modul lädt keine Dateien aus Unterverzeichnissen, die sich am Quelldaten Speicherort befinden. Das Lade Modul ist fehlerhaft, wenn ein Verzeichnis in einer GZIP-Datei vorhanden ist.  
  
-   Um einige der Dateien in einem Verzeichnis anzugeben, verwenden Sie eine Kombination aus Zeichen und dem Platzhalter *.  
  
So laden Sie mehrere Dateien mit einem Befehl:  
  
-   Alle Dateien müssen im gleichen Verzeichnis vorhanden sein.  
  
-   Die Dateien müssen alle Textdateien, alle gzip-Dateien oder eine Kombination aus Text-und gzip-Dateien sein.  
  
-   Keine der Dateien kann Header Informationen enthalten.  
  
-   Für alle Dateien muss derselbe Zeichen Codierungstyp verwendet werden. Weitere Informationen finden Sie unter der Option-e.  
  
-   Alle Dateien müssen in dieselbe Tabelle geladen werden.  
  
-   Alle Dateien werden verkettet und geladen, als ob es sich um eine Datei handelt, und die abgelehnten Zeilen werden in einer einzelnen Ablehnungs Datei angezeigt.  
  
Beispiele:  
  
-   -i \\ \loadserver\loads\daily \\ *. gz  
  
-   -i \\ \loadserver\loads\daily \\ *. txt  
  
-   -i \\ \loadserver\loads\daily\monday. *  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   -i \\ \loadserver\loads\daily\\*  
  
**-R** *load_failure_file_name*  
Wenn Ladefehler auftreten, speichert **"dwloader** die Zeile, die nicht geladen werden konnte, und die Fehlerbeschreibung in einer Datei mit dem Namen *load_failure_file_name*. Wenn diese Datei bereits vorhanden ist, wird die vorhandene Datei von "dwloader überschrieben. *load_failure_file_name* wird erstellt, wenn der erste Fehler auftritt. Wenn alle Zeilen erfolgreich geladen wurden, wird *load_failure_file_name* nicht erstellt.  
  
**-FH** *number_header_rows*  
Die Anzahl der Zeilen (Zeilen), die am Anfang *source_data_file_name* ignoriert werden sollen. Die Standardeinstellung ist 0.  
  
<variable_length_column_options>  
Die Optionen für eine *source_data_file_name* , die über Zeichen getrennte Spalten mit variabler Länge verfügt. Standardmäßig enthält *source_data_file_name* ASCII-Zeichen in Spalten variabler Länge.  
  
Bei ASCII-Dateien werden Nullen durch das aufeinanderfolgende Platzieren von Trennzeichen dargestellt. Beispielsweise wird in einer durch Trennzeichen getrennten Datei ("|") ein NULL-Wert durch "| |" angegeben. In einer durch Trennzeichen getrennten Datei wird ein NULL-Wert durch ",," angegeben. Außerdem muss die Option **-E** (--emptystringasnull) angegeben werden. Weitere Informationen zu-E finden Sie unten.  
  
**-e** *character_encoding*  
Gibt einen Zeichen Codierungstyp für die Daten an, die aus der Datendatei geladen werden sollen. Bei den Optionen handelt es sich um ASCII (Standard), UTF8, UTF16 oder UTF16BE, wobei UTF16 Little Endian und UTF16BE der Big Endian ist. Diese Optionen Unterscheidung nach Groß-/Kleinschreibung  
  
**-t** *field_delimiter*  
Das Trennzeichen für jedes Feld (Spalte) in der Zeile. Das Feld Trennzeichen ist mindestens ein ASCII-Escapezeichen oder ASCII-Hexadezimalwert.  
  
|Name|Escape-Zeichen|Hex-Zeichen|  
|--------|--------------------|-----------------|  
|Registerkarte|\t|0x09|  
|Wagen Rücklauf (CR)|\r|0x0D|  
|Zeilenvorschub (LF)|\n|0x0A|  
|CRLF|\r\n|0x0d0x0a|  
|Komma|','|0x2c|  
|Doppeltes Anführungszeichen|\\"|0x22|  
|Einfaches Anführungszeichen|\\'|0x27|  
  
Um das Pipezeichen in der Befehlszeile anzugeben, müssen Sie es mit doppelten Anführungszeichen ("|") einschließen. Dadurch wird die Fehlinterpretation durch den Befehlszeilen Parser vermieden. Andere Zeichen sind in einfache Anführungszeichen eingeschlossen.  
  
Beispiele:  
  
-t "|"  
  
-t ' '  
  
-t 0x0A  
  
-t \t  
  
-t ' ~ | ~ '  
  
**-r** *row_delimiter*  
Das Trennzeichen für jede Zeile der Quell Datendatei. Das Zeilen Trennzeichen ist ein oder mehrere ASCII-Werte.  
  
Wenn Sie ein Wagen Rücklauf Zeichen (CR), Zeilenvorschub Zeichen (LF) oder Tabstopp Zeichen als Trennzeichen angeben möchten, können Sie die Escapezeichen (\r, \n, \t) oder Ihre hexadezimal Werte (0x, 0d, 09) verwenden. Wenn Sie andere Sonderzeichen als Trennzeichen angeben möchten, verwenden Sie den Hexadezimalwert.  
  
Beispiele für CR + LF:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Beispiele für CR:  
  
-r \r  
  
-r 0x0D  
  
Beispiele für LF:  
  
-r \n  
  
-r 0x0A  
  
Für UNIX ist ein LF erforderlich. Für Windows ist eine CR erforderlich.  
  
**-s** *string_delimiter*  
Das Trennzeichen für das Zeichen folgen-Datentyp Feld einer Text getrennten Eingabedatei. Das Zeichen folgen Trennzeichen ist ein oder mehrere ASCII-Werte.  Sie kann als Zeichen (z. b.-s *) oder als Hexadezimalwert (z. b.-s 0x22 für ein doppeltes Anführungszeichen) angegeben werden.  
  
Beispiele:  
  
Hymnen  
  
-s 0x22  
  
< fixed_width_column_options>  
Die Optionen für eine Quell Datendatei mit Spalten fester Länge. Standardmäßig enthält *source_data_file_name* ASCII-Zeichen in Spalten variabler Länge.  
  
Spalten mit fester Breite werden nicht unterstützt, wenn-e UTF8 ist.  
  
**-w** *fixed_width_config_file*  
Der Pfad und der Name der Konfigurationsdatei, die die Anzahl der Zeichen in jeder Spalte angibt. Jedes Feld muss angegeben werden.  
  
Diese Datei muss sich auf dem Lade Server befinden. Der Pfad kann ein UNC-, relativer oder absoluter Pfad sein. Jede Zeile in *fixed_width_config_file* enthält den Namen einer Spalte und die Anzahl der Zeichen für diese Spalte. Es gibt eine Zeile pro Spalte, wie im folgenden dargestellt, und die Reihenfolge in der Datei muss mit der Reihenfolge in der Ziel Tabelle übereinstimmen:  
  
*column_name* = *num_chars*  
  
*column_name* = *num_chars*  
  
Beispiel für eine Konfigurationsdatei mit fester Breite:  
  
Salescode = 3  
  
SalesID = 10  
  
Beispiel Zeilen in *source_data_file_name*:  
  
230shiran 0056  
  
320um wels1356  
  
Im vorherigen Beispiel enthält die erste geladene Zeile Salescode = "230" und "SalesID = ' Shirts0056 '". Die zweite geladene Zeile weist "Salescode = ' 320 '" und "SaleID = ' Towels1356 '" auf.  
  
Informationen dazu, wie führende und nachfolgende Leerzeichen oder die Datentyp Konvertierung im Modus mit fester Breite behandelt werden, finden Sie unter [Datentyp-Konvertierungsregeln für "dwloader](dwloader-data-type-conversion-rules.md).  
  
**-e** *character_encoding*  
Gibt einen Zeichen Codierungstyp für die Daten an, die aus der Datendatei geladen werden sollen. Bei den Optionen handelt es sich um ASCII (Standard), UTF8, UTF16 oder UTF16BE, wobei UTF16 Little Endian und UTF16BE der Big Endian ist. Diese Optionen Unterscheidung nach Groß-/Kleinschreibung  
  
Spalten mit fester Breite werden nicht unterstützt, wenn-e UTF8 ist.  
  
**-r** *row_delimiter*  
Das Trennzeichen für jede Zeile der Quell Datendatei. Das Zeilen Trennzeichen ist ein oder mehrere ASCII-Werte.  
  
Wenn Sie ein Wagen Rücklauf Zeichen (CR), Zeilenvorschub Zeichen (LF) oder Tabstopp Zeichen als Trennzeichen angeben möchten, können Sie die Escapezeichen (\r, \n, \t) oder Ihre hexadezimal Werte (0x, 0d, 09) verwenden. Wenn Sie andere Sonderzeichen als Trennzeichen angeben möchten, verwenden Sie den Hexadezimalwert.  
  
Beispiele für CR + LF:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Beispiele für CR:  
  
-r \r  
  
-r 0x0D  
  
Beispiele für LF:  
  
-r \n  
  
-r 0x0A  
  
Für UNIX ist ein LF erforderlich. Für Windows ist eine CR erforderlich.  
  
**-D** { **YMD** \| ydm \| MDY \| MYD \| DMY \| dym \| *custom_date_format* }  
Gibt die Reihenfolge von Monat (m), Tag (d) und Jahr (y) für alle DateTime-Felder in der Eingabedatei an. Die Standard Reihenfolge ist YMD. Verwenden Sie die Option-dt, um mehrere Bestell Formate für dieselbe Quelldatei anzugeben.  
  
YMD- \| DMY  
ydm und DMY lassen dieselben Eingabeformate zu. Beide ermöglichen es, dass das Jahr am Anfang oder am Ende des Datums liegt. Beispielsweise können sowohl für **ydm** -als auch für **DMY** -Datumsformate in der Eingabedatei 2013-02-03 oder 02-03-2013 vorhanden sein.  
  
ydm  
Sie können nur als ydm formatierte Eingaben in Spalten vom Datentyp DateTime und smalldatetime laden. Ydm-Werte können nicht in eine Spalte des Datentyps datetime2, Date oder DateTimeOffset geladen werden.  
  
dmy  
MDY ermöglicht \<month> \<space> \<day> \<comma> \<year> .  
  
Beispiele für MDY-Eingabedaten für den 1. Januar 1975:  
  
-   1. Januar 1975  
  
-   Jan 01, 75  
  
-   Jan/1/75  
  
-   01011975  
  
myd  
Beispiele für die Eingabedatei für den 04. März 2010:03-2010-04, 3/2010/4  
  
dym  
Beispiele für die Eingabedatei für den 04. März, 2010:04-2010-03, 4/2010/3  
  
*custom_date_format*  
*custom_date_format* ist ein benutzerdefiniertes Datumsformat (z. b. mm/dd/yyyy) und wird nur aus Gründen der Abwärtskompatibilität eingeschlossen. das benutzerdefinierte Datumsformat wird von "dwloader nicht erzwungen. Wenn Sie ein benutzerdefiniertes Datumsformat angeben, wird es stattdessen von **"dwloader** in die entsprechende Einstellung von ymd, ydm, MDY, MYD, dym oder DMY konvertiert.  
  
Wenn Sie z. b. "-D mm/dd/yyyy" angeben, erwartet "dwloader, dass alle Datums Eingaben mit" Month First "," Day "und" Year "(MDY) geordnet sind. Es werden nicht zwei Zeichen Monate, zweistellige Tage und vierstellige Jahre durch das benutzerdefinierte Datumsformat erzwungen. Im folgenden finden Sie einige Beispiele dafür, wie Datumsangaben in der Eingabedatei formatiert werden können, wenn das Datumsformat-D mm/dd/yyyy lautet: 01/02/2013, Jan. 02.2013, 1/2/2013  
  
Umfassendere Formatierungsinformationen finden Sie unter [Datentyp-Konvertierungsregeln für "dwloader](dwloader-data-type-conversion-rules.md).  
  
**-dt** *datetime_format_file*  
Jedes DateTime-Format wird in einer Datei mit dem Namen *datetime_format_file* angegeben. Im Gegensatz zu den Befehlszeilen Parametern dürfen Datei Parameter, die Leerzeichen enthalten, nicht in doppelte Anführungszeichen eingeschlossen werden. Das DateTime-Format kann beim Laden von Daten nicht geändert werden. Die Quell Datendatei und die zugehörige Spalte in der Ziel Tabelle müssen das gleiche Format aufweisen.  
  
Jede Zeile enthält den Namen einer Spalte in der Ziel Tabelle und deren DateTime-Format.  
  
Beispiele:  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *staging_database_name*  
Der Datenbankname, der die Stagingtabelle enthalten soll. Der Standardwert ist die Datenbank, die mit der Option-T angegeben wird. Hierbei handelt es sich um die Datenbank für die Ziel Tabelle. Weitere Informationen zur Verwendung einer Stagingdatenbank finden Sie unter [Create the Staging Database](staging-database.md).  
  
**-M** *load_mode_option*  
Gibt an, ob Daten angefügt, Upsert oder neu geladen werden sollen. Der Standardmodus ist "append".  
  
append  
Das Lade Modul fügt Zeilen am Ende der vorhandenen Zeilen in der Ziel Tabelle ein.  
  
vom fastappend Lademodus  
Das Lade Modul fügt Zeilen direkt, ohne eine temporäre Tabelle zu verwenden, an das Ende der vorhandenen Zeilen in der Ziel Tabelle ein. vom fastappend Lademodus erfordert die Option "Multi-Transaction (-m)". Eine Stagingdatenbank kann bei Verwendung von fastappend nicht angegeben werden. Es ist kein Rollback mit fastappend vorhanden. Dies bedeutet, dass die Wiederherstellung von einem fehlerhaften oder abgebrochenen Ladevorgang durch ihren eigenen Ladevorgang verarbeitet werden muss.  
  
Upsert **-K**  *merge_column* [,... *n* ]  
Das Lade Tool verwendet die SQL Server MERGE-Anweisung, um vorhandene Zeilen zu aktualisieren und neue Zeilen einzufügen.  
  
Die Option "-K" gibt die Spalten an, auf denen der Merge basieren soll. Diese Spalten bilden einen Merge-Schlüssel, der eine eindeutige Zeile darstellen sollte. Wenn der Merge-Schlüssel in der Ziel Tabelle vorhanden ist, wird die Zeile aktualisiert. Wenn der Merge-Schlüssel in der Ziel Tabelle nicht vorhanden ist, wird die Zeile angefügt.  
  
Bei Tabellen mit Hash Verteilung muss der Merge-Schlüssel die Verteilungs Spalte oder enthalten.  
  
Bei replizierten Tabellen ist der Merge-Schlüssel die Kombination aus einer oder mehreren Spalten. Diese Spalten werden entsprechend den Anforderungen der Anwendung angegeben.  
  
Mehrere Spalten müssen durch Kommas getrennt werden, ohne Leerzeichen oder durch Trennzeichen getrennte Leerzeichen und in einfache Anführungszeichen eingeschlossen zu werden.  
  
Wenn zwei Zeilen in der Quell Tabelle übereinstimmende mergeschlüsselwerte aufweisen, müssen die entsprechenden Zeilen identisch sein.  
  
brauchte  
Das Lade Modul verkürzt die Ziel Tabelle, bevor die Quelldaten eingefügt werden.  
  
**-b** *BatchSize*  
Wird nur für die Verwendung durch Microsoft-Support empfohlen, *BatchSize* ist die SQL Server Batch Größe für das Massen kopieren, das DMS in SQL Server Instanzen auf den Computeknoten ausführt.  Wenn *BatchSize* angegeben wird, überschreibt SQL Server PDW die Batch Lade Größe, die für jede Last dynamisch berechnet wird.  
  
Ab SQL Server 2012 PDW berechnet der Steuer Knoten standardmäßig dynamisch eine Batch Größe für jede Last. Diese automatische Berechnung basiert auf mehreren Parametern, wie z. b. der Arbeitsspeicher Größe, dem Ziel Tabellentyp, dem Ziel Tabellen Schema, dem Auslastungstyp, der Dateigröße und der Ressourcen Klasse des Benutzers.  
  
Wenn der Lademodus beispielsweise fastappend ist und die Tabelle über einen gruppierten columnstore--Index verfügt, wird SQL Server PDW standardmäßig versuchen, eine Batch Größe von 1.048.576 zu verwenden, damit Zeilen Gruppen geschlossen werden und direkt in den columnstore-geladen werden, ohne den Delta Speicher zu durchlaufen. Wenn der Arbeitsspeicher die Batch Größe von 1.048.576 nicht zulässt, wählt "dwloader eine kleinere Batch Größe aus.  
  
Wenn der Auslastungstyp fastappend ist, gilt der *BatchSize* -Wert für das Laden von Daten in die Tabelle; andernfalls gilt *BatchSize* für das Laden von Daten in die Stagingtabelle.  
  
<reject_options>  
Gibt Optionen zum Bestimmen der Anzahl von Lade Fehlern an, die das Lade Modul zulässt. Wenn die Ladefehler den Schwellenwert überschreiten, wird das Lade Modul angehalten und führt keinen Commit für Zeilen aus.  
  
**-RT** { **Wert** | Prozentsatz}  
Gibt an, ob das-*reject_value* in der Option **-RV** *reject_value* eine literalanzahl von Zeilen (Wert) oder eine Fehlerrate (Prozentsatz) ist. Der Standardwert ist value.  
  
Die Prozent Option ist eine echt Zeitberechnung, die in Intervallen gemäß der Option-RS erfolgt.  
  
Wenn das Lade Modul z. b. versucht, 100 Zeilen zu laden und 25 fehlschlägt und 75 erfolgreich ist, beträgt die Fehlerrate 25%.  
  
**-RV** *reject_value*  
Gibt die Anzahl oder den Prozentsatz der Zeilen Umschreibungen an, die zugelassen werden, bevor die Last angehalten wird. Die Option **-RT** bestimmt, ob *reject_value* auf die Anzahl der Zeilen oder den Prozentsatz der Zeilen verweist.  
  
Der Standard *reject_value* ist 0 (null).  
  
Bei Verwendung mit dem-RT-Wert stoppt das Lade Modul die Last, wenn die abgelehnte Zeilen Anzahl reject_value überschreitet.  
  
Wenn Sie mit einem Prozentsatz von-RT verwenden, berechnet das Lade Modul den Prozentsatz bei Intervallen (-RS-Option). Daher kann der Prozentsatz fehlerhafter Zeilen *reject_value* überschreiten.  
  
**-RS** *reject_sample_size*  
Wird mit der `-rt percentage` Option verwendet, um die inkrementellen Überprüfungen anzugeben. Wenn reject_sample_size z. b. 1000 ist, berechnet das Lade Modul den Prozentsatz fehlerhafter Zeilen, nachdem versucht wurde, 1000 Zeilen zu laden. Der Prozentsatz der fehlerhaften Zeilen wird neu berechnet, nachdem versucht wurde, jede weitere 1000 Zeilen zu laden.  
  
**-c**  
Entfernt Leerzeichen von der linken und rechten Seite der Felder Char, nchar, varchar und nvarchar. Konvertiert jedes Feld, das nur Leerraum Zeichen enthält, in die leere Zeichenfolge.  
  
Beispiele:  
  
"" wird auf "" gekürzt  
  
' abc ' wird auf ' abc ' gekürzt.  
  
Wenn-c mit-e verwendet wird, tritt der-e-Vorgang zuerst auf. Felder, die nur Leerraum Zeichen enthalten, werden in die leere Zeichenfolge und nicht in NULL konvertiert.  
  
**-E**  
Leere Zeichen folgen in NULL konvertieren. Standardmäßig werden diese Konvertierungen nicht durchgeführt.  
  
**-m**  
Multi-Transaction-Modus für die zweite Phase des Ladens verwenden; beim Laden von Daten aus der Stagingtabelle in eine verteilte Tabelle.  
  
Mit **-m** führt SQL Server PDW Ladevorgänge parallel aus und führt Sie aus. Dies ist wesentlich schneller als der standardmäßige Lade Modus, aber nicht transaktionssicher.  
  
Ohne **-m** führt SQL Server PDW Lasten seriale über die Verteilungen innerhalb der einzelnen Computeknoten und gleichzeitig über die Computeknoten hinweg aus. Diese Methode ist langsamer als der multitransaktionsmodus, aber ist transaktionssicher.  
  
**-m** ist für *Anfügen*, *Upload* und *Upsert* optional.  
  
**-m** ist für fastappend erforderlich.  
  
**-m** kann nicht mit replizierten Tabellen verwendet werden.  
  
**-m** gilt nur für die zweite Lade Phase. Dies gilt nicht für die erste Lade Phase. Laden von Daten in die Stagingtabelle.  
  
Es ist kein Rollback mit dem Multi-Transaction-Modus vorhanden. Dies bedeutet, dass die Wiederherstellung von einem fehlerhaften oder abgebrochenen Ladevorgang durch ihren eigenen Ladevorgang verarbeitet werden muss.  
  
Es wird empfohlen, **-m** nur beim Laden in eine leere Tabelle zu verwenden, damit Sie ohne Datenverlust wieder hergestellt werden können. So stellen Sie nach einem Ladefehler eine Wiederherstellung durch: Löschen Sie die Ziel Tabelle, beheben Sie das Lade Problem, erstellen Sie die Ziel Tabelle neu, und führen Sie die Last erneut aus.  
  
**-N**  
Vergewissern Sie sich, dass das Zielgerät ein gültiges SQL Server PDW Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle aufweist. Verwenden Sie diese Informationen, um sicherzustellen, dass Ihre Daten nicht von einem Angreifer getarnt und an einen nicht autorisierten Speicherort gesendet werden. Das Zertifikat muss bereits auf dem Gerät installiert sein. Die einzige Möglichkeit zum Installieren des Zertifikats besteht darin, dass der Geräte Administrator diese mithilfe des Configuration Manager Tools installiert. Wenden Sie sich an den Geräte Administrator, wenn Sie nicht sicher sind, ob auf dem Gerät ein vertrauenswürdiges Zertifikat installiert ist.  
  
**-SE**  
Das Laden leerer Dateien wird übersprungen. Dadurch wird auch die Dekomprimierung leerer gzip-Dateien überdies ausgelassen.

**-l**  
Verfügbar mit Cu 7.4 Update, gibt die maximale Zeilenlänge (in Byte) an, die geladen werden kann. Gültige Werte sind ganze Zahlen zwischen 32768 und 33554432. Verwenden Sie nur bei Bedarf, um große Zeilen (über 32 KB) zu laden, da dadurch auf dem Client und dem Server mehr Arbeitsspeicher belegt wird.
  
## <a name="return-code-values"></a>Rückgabecodewerte  
0 (Erfolg) oder andere ganzzahlige Werte (Fehler)  
  
Verwenden Sie in einem Befehlsfenster oder in einer Batchdatei, `errorlevel` um den Rückgabecode anzuzeigen. Beispiel:  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
Wenn Sie PowerShell verwenden, verwenden Sie `$LastExitCode` .  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Load-Berechtigung und die anwendbaren Berechtigungen (INSERT, Update, DELETE) in der Ziel Tabelle. Erfordert die CREATE-Berechtigung (zum Erstellen einer temporären Tabelle) für die Stagingdatenbank. Wenn keine Stagingdatenbank verwendet wird, ist die CREATE-Berechtigung für die Zieldatenbank erforderlich. 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
Informationen zu Datentyp Konvertierungen beim Laden mit "dwloader finden Sie unter [Datentyp-Konvertierungsregeln für" dwloader](dwloader-data-type-conversion-rules.md).  
  
Wenn ein Parameter ein oder mehrere Leerzeichen enthält, schließen Sie den Parameter in doppelte Anführungszeichen ein.  
  
Sie sollten das Lade Modul von seinem installierten Speicherort aus ausführen. Die ausführbare Datei "" dwloader "ist bereits mit dem Gerät installiert und befindet sich im Verzeichnis" c:\Programme\Microsoft SQL Server Data Warehouse-\dwloader ".  
  
Sie können einen Parameter, der in der Parameterdatei (-f-Option) angegeben ist, überschreiben, indem Sie ihn als Befehlszeilenparameter angeben.  
  
Sie können mehrere Instanzen des Lade Moduls gleichzeitig ausführen. Die maximale Anzahl der Lade Lade Instanzen ist vorkonfiguriert und kann nicht geändert werden. 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
Für geladene Daten ist möglicherweise mehr oder weniger Speicherplatz auf dem Gerät als am Quell Speicherort erforderlich. Sie können Test Importe mit Teilmengen von Daten ausführen, um den Datenträger Verbrauch zu schätzen.  
  
Obwohl es sich bei **"dwloader** um einen Transaktionsprozess handelt und ein Rollback bei einem Fehler ordnungsgemäß ausgeführt wird, kann kein Rollback ausgeführt werden, sobald der Massen Ladevorgang erfolgreich abgeschlossen wurde. Um einen aktiven **"dwloader** -Prozess abzubrechen, geben Sie STRG + C ein.  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
Die Gesamtgröße aller gleichzeitig auftretenden Ladevorgänge muss kleiner als LOG_SIZE für die Datenbank sein, und es wird empfohlen, dass die Gesamtgröße aller gleichzeitigen Ladevorgänge kleiner als 50% der LOG_SIZE ist. Um diese Größenbeschränkung zu erreichen, können Sie große Lasten in mehrere Batches aufteilen. Weitere Informationen zu LOG_SIZE finden Sie unter [Create Database](../t-sql/statements/create-database-transact-sql.md?view=aps-pdw-2016&preserve-view=true) .  
  
Beim Laden mehrerer Dateien mit einem Load-Befehl werden alle abgelehnten Zeilen in dieselbe Ablehnungs Datei geschrieben. Die Ablehnungs Datei zeigt nicht an, welche Eingabedatei jede abgelehnte Zeile enthält.  
  
Die leere Zeichenfolge sollte nicht als Trennzeichen verwendet werden. Wenn eine leere Zeichenfolge als Zeilen Trennzeichen verwendet wird, tritt ein Fehler auf. Wenn das Trennzeichen als Spalten Trennzeichen verwendet wird, ignoriert es das Trennzeichen und verwendet weiterhin den Standardwert "|" als Spalten Trennzeichen. Wenn die Zeichenfolge als Zeichen folgen Trennzeichen verwendet wird, wird die leere Zeichenfolge ignoriert und das Standardverhalten angewendet.  
  
## <a name="locking-behavior"></a>Sperrverhalten  
Das Sperr Verhalten von **"dwloader** variiert abhängig vom *load_mode_option*.  
  
-   **Anfügen** -Anfügen ist die empfohlene und häufigste Option. Append lädt Daten in eine Stagingtabelle. Die Sperrung wird im folgenden ausführlich beschrieben.  
  
-   **schnelles anfügen** -schnelles Anfügen von Ladevorgängen direkt in die letzte Tabelle, wobei eine exclusiveupdate-Tabellensperre verwendet wird, und ist der einzige Modus, der keine Stagingtabelle verwendet.  
  
-   durch erneutes Laden **Laden** Daten in eine Stagingtabelle geladen und erfordert eine exklusive Sperre für die Stagingtabelle und die letzte Tabelle. Das erneute Laden wird für gleichzeitige Vorgänge nicht empfohlen.  
  
-   **Upsert** -Upsert lädt Daten in eine Stagingtabelle und führt dann einen Zusammenarbeits Vorgang von der Stagingtabelle zur abschließenden Tabelle aus. Upsert erfordert keine exklusiven Sperren für die endgültige Tabelle. Die Leistung kann bei Verwendung von Upsert variieren. Testen Sie das Verhalten in Ihrer Umgebung.  
  
### <a name="locking-behavior"></a>Sperrverhalten  
**Sperren des Modus anfügen**  
  
Append kann im multitransaktionalen Modus (mit dem Argument-m) ausgeführt werden, ist jedoch nicht transaktionssicher. Daher sollte Anfügen als transaktionaler Vorgang verwendet werden (ohne das-m-Argument zu verwenden). Leider ist während des abschließenden INSERT-SELECT-Vorgangs der Transaktionsmodus momentan ungefähr sechs Mal langsamer als der multitransaktionsmodus.  
  
Der Anfügen-Modus lädt Daten in zwei Phasen. In Phase 1 werden Daten gleichzeitig aus der Quelldatei in eine Stagingtabelle geladen (Fragmentierung kann auftreten). In Phase 2 werden Daten aus der Stagingtabelle in die letzte Tabelle geladen. In der zweiten Phase wird eine **INSERT INTO... Wählen Sie with (TABLOCK)** -Vorgang aus. In der folgenden Tabelle wird das Sperr Verhalten für die abschließende Tabelle und das Protokollierungs Verhalten bei Verwendung des anfügen-Modus angezeigt:  
  
|Tabellentyp|Mehrere Transaktionen<br />Modus (-m)|Die Tabelle ist leer.|Unterstützte Parallelität|Protokollierung|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|Heap|Ja|Ja|Ja|Minimal|  
|Heap|Ja|Nein|Ja|Minimal|  
|Heap|Nein|Ja|Nein|Minimal|  
|Heap|Nein|Nein|Nein|Minimal|  
|Schl|Ja|Ja|Nein|Minimal|  
|Schl|Ja|Nein|Ja|Vollständig|  
|Schl|Nein|Ja|Nein|Minimal|  
|Schl|Nein|Nein|Ja|Vollständig|  
  
In der obigen Tabelle wird **"dwloader** mit dem Anfüge Modus in einen Heap oder einer CI-Tabelle (gruppierten Index) mit oder ohne das multitransaktionsflag und das Laden in eine leere Tabelle oder eine nicht leere Tabelle angezeigt. Das Sperr-und Protokollierungs Verhalten jeder solchen Kombination von Load wird in der Tabelle angezeigt. Wenn Sie zum Beispiel die Phase (2.) mit dem Anfügen-Modus in einen gruppierten Index ohne den multitransaktionalen Modus und in eine leere Tabelle laden, wird PDW eine exklusive Sperre für die Tabelle erstellen, und die Protokollierung ist minimal. Dies bedeutet, dass ein Kunde nicht in der Lage ist, (2.) Phase und Abfrage gleichzeitig in eine leere Tabelle zu laden. Wenn Sie jedoch mit der gleichen Konfiguration in eine nicht leere Tabelle laden, gibt PDW keine exklusive Sperre für die Tabelle aus, und Parallelität ist möglich. Leider erfolgt die vollständige Protokollierung, die den Prozess verlangsamt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-simple-dwloader-example"></a>A. Einfaches Beispiel für "dwloader  
Im folgenden Beispiel wird die Initiierung des **Lade** Moduls mit nur den erforderlichen Optionen gezeigt. Andere Optionen werden von der globalen Konfigurationsdatei, *loadparamfile.txt*, übernommen.  
  
Beispiel für die Verwendung SQL Server-Authentifizierung.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
Das gleiche Beispiel mit der Windows-Authentifizierung.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -W -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -W -f /configfiles/loadparamfile.txt  
```  
  
Beispiel für das Verwenden von Argumenten für eine Quelldatei und eine Fehler Datei.  
  
```  
--Load over Ethernet  
dwloader.exe -U mylogin -P 123jkl -S 10.192.63.148  -i C:\SQLData\AWDimEmployees.csv -T AdventureWorksPDW2012.dbo.DimEmployees -R C:\SQLData\LoadErrors  
```  
  
### <a name="b-load-data-into-an-adventureworks-table"></a>B. Laden von Daten in eine AdventureWorks-Tabelle  
Das folgende Beispiel ist Teil eines Batch Skripts, mit dem Daten in **AdventureWorksPDW2012** geladen werden.  Um das vollständige Skript anzuzeigen, öffnen Sie die Datei aw_create.bat, die im Lieferumfang des **AdventureWorksPDW2012** -Installationspakets enthalten ist. 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

Im folgenden Skript Ausschnitt wird "dwloader verwendet, um Daten in die DimAccount-und DimCurrency-Tabellen zu laden. Dieses Skript verwendet eine Ethernet-Adresse. Wenn InfiniBand verwendet wurde, wäre der Server *<appliance_name>* `-SQLCTL01` .  
  
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
  
Im folgenden finden Sie die DDL für die DimAccount-Tabelle.  
  
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
  
Im folgenden finden Sie ein Beispiel für die Datendatei, DimAccount.txt, die Daten enthält, die in die Tabelle "DimAccount" geladen werden sollen.  
  
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
  
-   *C:\Programme\Microsoft SQL Server parallel Data Warehouse\100\dwloader.exe* ist der installierte Speicherort dwloader.exe.  
  
-   Auf *-S* folgt die IP-Adresse des Steuerelement Knotens.  
  
-   *-E* gibt an, dass leere Zeichen folgen als NULL geladen werden.  
  
-   *-M neu laden* gibt an, dass die Ziel Tabelle abgeschnitten wird, bevor die Quelldaten eingefügt werden.  
  
-   *-e UTF16* gibt an, dass für die Quelldatei der kleine Endian-Zeichen Codierungstyp verwendet wird.  
  
-   *-i .\DimAccount.txt* gibt an, dass sich die Daten in einer Datei mit dem Namen DimAccount.txt befinden, die im aktuellen Verzeichnis vorhanden ist.  
  
-   *-T AdventureWorksPDW2012. dbo. DimAccount* gibt den dreiteiligen Namen der Tabelle an, die die Daten empfangen soll.  
  
-   *-R DimAccount. Bad* gibt an, dass die Zeilen, die nicht geladen werden können, in eine Datei mit dem Namen "DimAccount. Bad" geschrieben werden.  
  
-   *-t "|"* Gibt an, dass die Felder in der Eingabedatei (DimAccount.txt) durch das senkrechter Strich getrennt sind.  
  
-   *-r \r\n* gibt an, dass jede Zeile in DimAccount.txt mit einem Wagen Rücklauf und einem Zeilenvorschub Zeichen endet.  
  
-   *-U <login_name>-P <password>* Gibt den Anmelde Namen und das Kennwort für den Anmelde Namen an, der über Berechtigungen zum Ausführen der Last verfügt.  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
