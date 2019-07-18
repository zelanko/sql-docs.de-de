---
title: bcp-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server]
- exporting data
- row exporting [SQL Server]
- copying data [SQL Server], bcp utility
- command prompt utilities [SQL Server], bcp
- tables [SQL Server], importing data
- column importing [SQL Server]
- bcp utility [SQL Server], command options
- file exporting [SQL Server]
- bulk copy [SQL Server]
- bcp utility [SQL Server], about bcp utility
- tables [SQL Server], exporting data
- row importing [SQL Server]
- importing data, bcp utility
- file importing [SQL Server]
- column exporting [SQL Server]
ms.assetid: c0af54f5-ca4a-4995-a3a4-0ce39c30ec38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24367bfec4b0e25fec60eb49c77a74e1ccd54f46
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68187136"
---
# <a name="bcp-utility"></a>Hilfsprogramms bcp
  Die **Bcp** Utility Bulk kopiert Daten zwischen einer Instanz von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und einer Datendatei in eine vom Benutzer angegebenes Format. Das Hilfsprogramm **bcp** kann verwendet werden, um große Mengen neuer Zeilen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Tabellen zu importieren oder um Daten aus Tabellen in Datendateien zu exportieren. Außer in Verbindung mit der Option **queryout** sind für das Hilfsprogramm keine Kenntnisse von [!INCLUDE[tsql](../includes/tsql-md.md)] erforderlich. Um Daten in eine Tabelle zu importieren, müssen Sie entweder eine für diese Tabelle erstellte Formatdatei verwenden oder die Struktur der Tabelle und die Art der Daten kennen, die in den Tabellenspalten zulässig sind.  
  
 ![Artikellinksymbol](../../2014/database-engine/media/topic-link.gif "Topic link icon") Informationen zu den **bcp**-Syntaxkonventionen finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
> [!NOTE]  
>  Wenn Sie Ihre Daten mit **bcp** sichern, müssen Sie zum Aufzeichnen des Datenformats eine Formatdatei erstellen. **bcp**-Datendateien enthalten keine Schema- oder Formatinformationen. Daher können Sie die Daten möglicherweise nicht mehr importieren, wenn Sie eine Tabelle löschen und keine Formatdatei vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
   bcp [database_name.] schema.{table_name | view_name | "query" {indata_file | outdata_file | queryoutdata_file | format nul}  
  
[-apacket_size]  
[-bbatch_size]  
[-c]  
[-C { ACP | OEM | RAW | code_page } ]  
[-ddatabase_name]  
[-eerr_file]  
[-E]  
[-fformat_file]  
[-Ffirst_row]  
[-h"hint [,...n]"]   
[-iinput_file]  
[-k]  
[-Kapplication_intent]  
[-Llast_row]  
[-mmax_errors]  
[-n]  
[-N]  
[-ooutput_file]  
[-Ppassword]  
[-q]  
[-rrow_term]  
[-R]  
[-S [server_name[\instance_name]]  
[-tfield_term]  
[-T]  
[-Ulogin_id]  
[-v]  
[-V (80 | 90 | 100 | 110)]  
[-w]  
[-x]  
/?  
```  
  
## <a name="arguments"></a>Argumente  
 *data_file*  
 Der vollständige Pfad der Datendatei. Wenn Daten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] massenimportiert werden, enthält die Datendatei die Daten, die in die angegebene Tabelle oder Sicht kopiert werden sollen. Beim Massenexportieren aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] enthält die Datendatei die Daten, die aus der Tabelle oder Sicht kopiert wurden. Der Pfad kann 1 bis 255 Zeichen enthalten. Die Datendatei kann maximal 2<sup>63</sup>- 1 Zeilen enthalten.  
  
 *database_name*  
 Der Name der Datenbank, in der die angegebene Tabelle oder Sicht vorhanden ist. Wenn kein Name angegeben ist, wird diese Datenbank als Standarddatenbank des Benutzers verwendet.  
  
 Sie können den Datenbanknamen mit `d-` auch explizit angeben.  
  
 **in** _Datendatei_ | **out**_Datendatei_ | **queryout**_Datendatei_ | **format nul**  
 Gibt die Richtung des Massenkopierens wie folgt an:  
  
-   Mit **in** werden Daten aus einer Datei in die Datenbanktabelle oder -sicht kopiert.  
  
-   Mit **out** werden Daten aus der Datenbanktabelle oder -sicht in eine Datei kopiert. Wenn Sie eine vorhandene Datei angeben, wird die Datei überschrieben. Beachten Sie, dass das Hilfsprogramm **bcp** beim Extrahieren von Daten leere Zeichenfolgen als NULL-Zeichenfolgen und NULL-Zeichenfolgen als leere Zeichenfolgen darstellt.  
  
-   Mit **queryout** werden Daten aus einer Abfrage kopiert. Diese Option muss nur beim Massenkopieren von Daten über eine Abfrage angegeben werden.  
  
-   **Format** erstellt eine Formatdatei basierend auf der angegebenen Option ( **- n**, `-c`, `-w`, oder **-N**) und den Tabellen- bzw. Sichttrennzeichen. Beim Massenkopieren von Daten kann der Befehl **bcp** auf eine Formatdatei verweisen. Dies erspart Ihnen die wiederholte interaktive Eingabe von Formatinformationen. Für die Option **format** ist die Option **-f** erforderlich. Zum Erstellen einer XML-Formatdatei muss zudem die Option **-x** angegeben werden. Weitere Informationen finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md). Sie müssen **nul** als Wert angeben (**format nul**).  
  
 *Besitzer*  
 Dies ist der Namen des Besitzers der Tabelle oder Sicht. *owner* ist optional, wenn der Benutzer, der den Vorgang ausführt, der Besitzer der angegebenen Tabelle oder Sicht ist. Wenn *owner* nicht angegeben wird und der Benutzer, der den Vorgang ausführt, nicht Besitzer der angegebenen Tabelle oder Sicht ist, gibt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Fehlermeldung zurück, und der Vorgang wird abgebrochen.  
  
 **"** _query_ **"**  
 Eine [!INCLUDE[tsql](../includes/tsql-md.md)]-Abfrage, die ein Resultset zurückgibt. Wenn die Abfrage mehrere Resultsets zurückgibt, wird nur das erste Resultset in die Datendatei kopiert; nachfolgende Resultsets werden nicht berücksichtigt. Schließen Sie die Abfrage in doppelte Anführungszeichen und alle Elemente, die in die Abfrage eingebettet sind, in einfache Anführungszeichen ein. **queryout** muss auch angegeben werden, wenn Sie Daten aus einer Abfrage massenkopieren.  
  
 Die Abfrage kann auf eine gespeicherte Prozedur verweisen, sofern alle Tabellen, auf die innerhalb der gespeicherten Prozedur verwiesen werden, vor der Ausführung der bcp-Anweisung vorhanden sind. Wenn die gespeicherte Prozedur beispielsweise eine temporäre Tabelle generiert, tritt bei der **bcp** -Anweisung ein Fehler auf, da die temporäre Tabelle nur zur Laufzeit und nicht zum Zeitpunkt der Anweisungsausführung verfügbar ist. Ziehen Sie in diesem Fall in Erwägung, die Ergebnisse der gespeicherten Prozedur in eine Tabelle einzufügen und dann **bcp** zum Kopieren der Daten aus der Tabelle in eine Datendatei zu verwenden.  
  
 *table_name*  
 Der Name der Zieltabelle, wenn Daten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] importiert werden (**in**), oder der Name der Quelltabelle, wenn Daten aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] exportiert werden (**out**).  
  
 *view_name*  
 Der Name der Zielsicht, wenn Daten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] kopiert werden (**in**), oder der Name der Quellsicht, wenn Daten aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] kopiert werden (**out**). Als Zielsichten können nur Sichten verwendet werden, in denen alle Spalten auf dieselbe Tabelle verweisen. Weitere Informationen zu den Einschränkungen beim Kopieren von Daten in Sichten finden Sie unter [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).  
  
 **-a** _packet_size_  
 Gibt an, wie viele Bytes pro Netzwerkpaket an den Server bzw. vom Server gesendet werden. Eine Serverkonfigurationsoption kann mithilfe von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (oder der gespeicherten Systemprozedur **sp_configure** ) festgelegt werden. Die Serverkonfigurationsoption kann jedoch mithilfe dieser Option einzeln überschrieben werden. *packet_size* kann einen Wert von 4096 bis 65535 Bytes annehmen. Der Standardwert ist 4096.  
  
 Durch einen höheren Wert für die Paketgröße kann die Leistung von Massenkopiervorgängen verbessert werden. Wenn eine größere Paketgröße angefordert, aber nicht erteilt wird, wird die Standardeinstellung verwendet. Die vom Hilfsprogramm **bcp** generierte Leistungsstatistik zeigt die verwendete Paketgröße an.  
  
 **-b** _batch_size_  
 Gibt die Anzahl von Zeilen pro importierten Datenbatch an. Jeder Batch wird als separate Transaktion importiert und protokolliert, für die erst dann ein Commit ausgeführt wird, nachdem der gesamte Batch importiert wurde. Standardmäßig werden alle Zeilen in der Datendatei als jeweils ein Batch importiert. Um die Zeilen auf mehrere Batches aufzuteilen, geben Sie mit *batch_size* eine Batchgröße an, die kleiner ist als die Anzahl von Zeilen in der Datendatei. Wenn die Transaktion für einen Batch einen Fehler erzeugt, wird nur für die Einfügungen aus dem aktuellen Batch ein Rollback ausgeführt. Auf Batches, die bereits durch Transaktionen importiert wurden, für die ein Commit ausgeführt wurde, wirken sich spätere Fehler nicht aus.  
  
 Verwenden Sie diese Option nicht in Verbindung mit der **-h "** ROWS_PER_BATCH  **= *`bb`* "** Option.  
  
 `-c`  
 Führt den Vorgang mithilfe eines Zeichendatentyps aus. Diese Option fordert nicht für jedes Feld; Er verwendet `char` als Speichertyp, keine Präfixe, **\t** (Tabstoppzeichen) als Feldtrennzeichen und **\r\n** (Zeilenumbruchzeichen) als Zeilenabschlusszeichen. `-c` ist nicht kompatibel mit `-w`.  
  
 Weitere Informationen finden Sie unter [Verwenden des Zeichenformats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).  
  
 **-C** { **ACP** | **OEM** | **RAW** | *Codepage* }  
 Gibt die Codepage für die in der Datendatei enthaltenen Daten an. *Codepage* ist nur relevant, wenn die Daten enthält `char`, `varchar`, oder `text` -Spalten mit Zeichenwerten enthalten, die größer als 127 oder kleiner als 32.  
  
> [!NOTE]  
>  Sie sollten für jede Spalte einen Sortierungsnamen in einer Formatdatei angeben.  
  
|Codepagewert|Beschreibung|  
|---------------------|-----------------|  
|ACP|[!INCLUDE[vcpransi](../includes/vcpransi-md.md)]/Microsoft Windows (ISO 1252).|  
|OEM|Standardcodepage, die vom Client verwendet wird. Die Standardcodepage, die verwendet wird, wenn **-C** nicht angegeben wird.|  
|RAW|Es erfolgt keine Konvertierung von einer Codepage zu einer anderen. Dies ist die schnellste Option, da keine Konvertierung vorgenommen wird.|  
|*Codepage*|Bestimmte Codepagenummer, z. B. 850.<br /><br /> **&#42;&#42;Wichtige &#42; &#42;**  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt nicht Codepage 65001 (UTF-8-Codierung).|  
  
 `-d` *Datenbankname*  
 Gibt die Datenbank an, mit der eine Verbindung hergestellt werden soll. bcp.exe stellt standardmäßig eine Verbindung mit der Standarddatenbank des Benutzers her. Wenn `-d` *Database_name* und ein dreiteiliger Name (*database_name.schema.table*, als der erste Parameter an bcp.exe übergeben) angegeben ist, wird ein Fehler tritt auf, da Sie nicht angeben können die der Datenbankname zweimal. Wenn *Database_name* beginnt mit einem Bindestrich (-) oder einem Schrägstrich (/), fügen Sie keine Leerzeichen zwischen `-d` und den Datenbanknamen an.  
  
 **-e** _Fehlerdatei_  
 Gibt den vollständigen Pfad einer Fehlerdatei an, in der alle Zeilen gespeichert werden, die das **bcp**-Hilfsprogramm nicht von der Datei in die Datenbank übertragen kann. Die durch den **bcp** -Befehl generierten Fehlermeldungen werden an die Arbeitsstation des Benutzers gesendet. Wenn diese Option nicht verwendet wird, wird keine Fehlerdatei erstellt.  
  
 Wenn *Fehlerdatei* mit einem Bindestrich (-) oder einem Schrägstrich (/) beginnt, darf kein Leerzeichen zwischen **-e** und dem *Fehlerdatei* -Wert enthalten sein.  
  
 **-E**  
 Gibt an, dass der oder die Identitätswerte in der importierten Datendatei für die Identitätsspalte verwendet werden sollen. Wenn **-E** nicht angegeben wird, werden die Identitätswerte für diese Spalte in der zu importierenden Datendatei ignoriert. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] weist automatisch eindeutige Werte zu, basierend auf den Ausgangswerten und den inkrementellen Werten, die beim Erstellen der Tabelle angegeben wurden.  
  
 Wenn die Datendatei keine Werte für die Identitätsspalte in der Tabelle oder Sicht enthält, geben Sie mithilfe einer Formatdatei an, dass die Identitätsspalte der Tabelle oder Sicht beim Importieren von Daten ausgelassen werden soll. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] weist der Spalte automatisch eindeutige Werte zu. Weitere Informationen finden Sie unter [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
 Für die Option **-E** sind besondere Berechtigungen erforderlich. Weitere Informationen finden Sie unter "Hinweise" weiter unten in diesem Thema.  
  
 **-f** _Formatdatei_  
 Gibt den vollständigen Pfad einer Formatdatei an. Die Bedeutung dieser Option hängt von der Umgebung ab, in der sie verwendet wird. Folgende Bedeutungen sind möglich:  
  
-   Wird **-f** mit der Option **format** verwendet, wird die angegebene *Formatdatei* für die angegebene Tabelle oder Sicht erstellt. Zum Erstellen einer XML-Formatdatei müssen Sie zudem die Option **-x** angeben. Weitere Informationen finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).  
  
-   Wird **-f** mit der Option **in** oder **out** verwendet, ist eine bereits vorhandene Formatdatei erforderlich.  
  
    > [!NOTE]  
    >  Die Verwendung einer Formatdatei mit der Option **in** oder **out** ist optional. In Ermangelung der **-f** option **- n**, `-c`, `-w`, oder **-N** nicht angegeben ist, mit dem Befehl werden die Formatinformationen aufgefordert und können Sie speichern Ihre Antworten in einer Formatdatei (Standardnamen Bcp.fmt ist).  
  
 Wenn *Fehlerdatei* mit einem Bindestrich (-) oder einem Schrägstrich (/) beginnt, darf kein Leerzeichen zwischen **-f** und dem *Fehlerdatei* -Wert enthalten sein.  
  
 **-F** _erste_Zeile_  
 Gibt die Nummer der ersten Zeile an, die aus einer Tabelle exportiert oder von einer Datendatei importiert werden soll. Dieser Parameter muss ein Wert größer als (>) 0 jedoch kleiner als (\<) oder gleich (=) die gesamte Anzahl der Zeilen. Fehlt dieser Parameter, wird standardmäßig die erste Zeile der Datei angenommen.  
  
 *erste_Zeile* kann eine positive ganze Zahl mit einem Wert bis zu 2^63-1 sein. **-F**_erste_Zeile_ ist 1-basiert.  
  
 **-h"** _Hinweis_[ **,** ... *n*] **"**  
 Gibt den oder die Hinweise an, die beim Massenimportieren von Daten in eine Tabelle oder Sicht verwendet werden sollen.  
  
 ORDER **(** _Spalte_[ASC | DESC] [ **,** ...*n*] **)**  
 Die Sortierreihenfolge der Daten in der Datendatei. Die Leistung des Massenkopierens wird verbessert, wenn die zu importierenden Daten entsprechend dem gruppierten Index der Tabelle (falls vorhanden) sortiert sind. Wenn die Datendatei in einer anderen Reihenfolge, d. h. nicht nach einem gruppierten Indexschlüssel sortiert ist, oder wenn es keinen gruppierten Index für die Tabelle gibt, wird die ORDER-Klausel ignoriert. Die angegebenen Spaltennamen müssen gültige Spaltennamen in der Zieltabelle sein. Standardmäßig geht **bcp** davon aus, dass die Datendatei nicht sortiert ist. Beim optimierten Massenimport wird in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auch überprüft, ob die importierten Daten sortiert sind.  
  
 ROWS_PER_BATCH **=** _bb_  
 Die Anzahl von Datenzeilen pro Batch (als *bb*). Dieser Hinweis wird verwendet, wenn **-b** nicht angegeben wird. Er bewirkt, dass die gesamte Datendatei in einer einzigen Transaktion an den Server gesendet wird. Der Server optimiert das Massenladen entsprechend dem Wert von *bb*. Standardmäßig ist ROWS_PER_BATCH unbekannt.  
  
 KILOBYTES_PER_BATCH **=** _cc_  
 Die ungefähre Anzahl von Kilobytes (KB) an Daten pro Batch (als *cc*). In der Standardeinstellung ist KILOBYTES_PER_BATCH unbekannt.  
  
 TABLOCK  
 Gibt an, dass eine Massenupdatesperre auf Tabellenebene für die Dauer des Massenladens aktiviert wird. Andernfalls wird eine Sperre auf Zeilenebene aktiviert. Dieser Hinweis verbessert die Leistung beträchtlich, da weniger Sperrkonflikte für die Tabelle auftreten, wenn diese während des Massenkopiervorgangs gesperrt wird. Eine Tabelle kann gleichzeitig von mehreren Clients geladen werden, wenn die Tabelle keine Indizes aufweist und **TABLOCK** angegeben ist. Standardmäßig wird das Sperrverhalten durch die Tabellenoption **table lock on bulk load** bestimmt.  
  
 CHECK_CONSTRAINTS  
 Gibt an, dass alle Einschränkungen, die für die Zieltabelle oder -sicht gelten, während des Massenimportvorgangs überprüft werden müssen. Ohne den CHECK_CONSTRAINTS-Hinweis werden alle CHECK- und FOREIGN KEY-Einschränkungen ignoriert. Nach dem Vorgang wird die Einschränkung für die Tabelle als nicht vertrauenswürdig markiert.  
  
> [!NOTE]  
>  UNIQUE-, PRIMARY KEY- und NOT NULL-Einschränkungen werden immer erzwungen.  
  
 Zu einem bestimmten Zeitpunkt sollten Sie allerdings die Einschränkungen für die gesamte Tabelle überprüfen. Wenn die Tabelle vor dem Massenimportvorgang nicht leer war, überschreitet der Aufwand der erneuten Überprüfung möglicherweise denjenigen der Anwendung von CHECK-Einschränkungen auf die inkrementellen Daten. Daher empfiehlt es sich normalerweise, die Einschränkungsüberprüfung beim inkrementellen Massenimportieren zu aktivieren.  
  
 Die Deaktivierung von Einschränkungen (das Standardverhalten) kann z. B. erwünscht sein, wenn die Eingabedaten Zeilen enthalten, die Einschränkungen verletzen. Wenn CHECK-Einschränkungen deaktiviert sind, können Sie die Daten importieren und anschließend [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen verwenden, um ungültige Daten zu entfernen.  
  
> [!NOTE]  
>  **bcp** erzwingt nun Datenüberprüfungen, die dazu führen können, dass Skripts einen Fehler erzeugen, wenn sie für ungültige Daten in einer Datendatei ausgeführt werden.  
  
> [!NOTE]  
>  Der Schalter **-m** _max_errors_ gilt nicht für die Einschränkungsüberprüfung.  
  
 FIRE_TRIGGERS  
 Wird mit dem **in**-Argument angegeben und bewirkt, dass jeder INSERT-Trigger, der für die Zieltabelle definiert ist, während des Massenkopiervorgangs ausgeführt wird. Wenn FIRE_TRIGGERS nicht angegeben wird, werden keine INSERT-Trigger ausgeführt. FIRE_TRIGGERS wird für die Argumente **out**, **queryout** und **format** ignoriert.  
  
 **-i** _input_file_  
 Gibt den Namen einer Antwortdatei, die Antworten auf die Fragen der Eingabeaufforderung für jedes Datenfeld enthält, wenn ein Massenkopiervorgang im interaktiven Modus ausgeführt wird ( **- n**, `-c`, `-w`, oder **- N** nicht angegeben).  
  
 Wenn *Eingabedatei* mit einem Bindestrich (-) oder einem Schrägstrich (/) beginnt, darf kein Leerzeichen zwischen **-i** und dem *Eingabedatei* -Wert enthalten sein.  
  
 **-k**  
 Gibt an, dass während des Vorgangs keine Standardwerte in leere Spalten eingefügt werden, sondern ein NULL-Wert für diese Spalten beibehalten werden soll. Weitere Informationen finden Sie unter [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).  
  
 **-K** _Anwendungszweck_  
 Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Der einzig mögliche Wert ist **ReadOnly**. Wenn **-K** nicht angegeben wird, unterstützt das bcp-Hilfsprogramm keine Konnektivität zu einem sekundären Replikat in einer AlwaysOn-Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Aktive sekundäre Replikate: Lesbare sekundäre Replikate (AlwaysOn-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 **-L** _letzte_Zeile_  
 Gibt die Nummer der letzten Zeile an, die aus einer Tabelle exportiert oder von einer Datendatei importiert werden soll. Dieser Parameter muss ein Wert größer als (>) 0 jedoch kleiner als (\<) oder gleich (=) die Anzahl der letzten Zeile. Fehlt dieser Parameter, wird standardmäßig die letzte Zeile der Datei angenommen.  
  
 *letzte_Zeile* kann eine positive ganze Zahl mit einem Wert bis zu 2^63-1 sein.  
  
 **-m** _max_Fehler_  
 Gibt an, wie viele Syntaxfehler maximal auftreten können, bevor der **bcp**-Vorgang abgebrochen wird. Ein Syntaxfehler setzt einen Fehler bei der Datenkonvertierung in den Zieldatentyp voraus. Der Wert von *max_Fehler* schließt alle Fehler aus, die nur auf dem Server erkannt werden können, z.B. Einschränkungsverletzungen.  
  
 Eine Zeile, die vom Hilfsprogramm **bcp** nicht kopiert werden kann, wird ignoriert und als ein Fehler gezählt. Wenn diese Option nicht enthalten ist, wird der Standardwert 10 verwendet.  
  
> [!NOTE]  
>  Die **-m** Option gilt nicht für die Konvertierung der `money` oder `bigint` -Datentypen.  
  
 **-n**  
 Führt das Massenkopieren mithilfe der systemeigenen (Datenbank-)Datentypen der Daten aus. Diese Option fordert für keines der Felder zu einer Eingabe auf; es werden die systemeigenen Werte verwendet.  
  
 Weitere Informationen finden Sie unter [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).  
  
 **-N**  
 Führt den Massenkopiervorgang mithilfe der systemeigenen (Datenbank-)Datentypen für Daten, die keinen Zeichendatentyp haben, und mithilfe von Unicode-Zeichen für Zeichendaten aus. Diese Option bietet ein besseres Leistungsverhalten als die Option `-w` und sollte verwendet werden, um Daten mithilfe einer Datendatei zwischen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen zu übertragen. Die Option fordert nicht für jedes Feld zu einer Eingabe auf. Verwenden Sie diese Option, wenn Sie Daten mit erweiterten ANSI-Zeichen übertragen und die Leistungsvorteile des einheitlichen Modus nutzen möchten.  
  
 Weitere Informationen finden Sie unter [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).  
  
 Wenn Sie exportieren und importieren Sie dann die Daten, die demselben Tabellenschema unter Verwendung von bcp.exe mit **-N**, möglicherweise eine Warnung angezeigt, wenn es sich bei vorhanden ist, eine feste Länge, die Spalte mit nicht-Unicode-Zeichen (z. B. `char(10)`).  
  
 Die Warnung kann ignoriert werden. Eine Möglichkeit zum Auflösen dieser Warnung besteht darin, **-n** anstelle von **-N** zu verwenden.  
  
 **-o** _Ausgabedatei_  
 Gibt den Namen einer Datei an, in die die Ausgabe geschrieben wird, die von der Eingabeaufforderung umgeleitet wurde.  
  
 Wenn *Ausgabedatei* mit einem Bindestrich (-) oder einem Schrägstrich (/) beginnt, darf kein Leerzeichen zwischen **-o** und dem *Ausgabedatei*-Wert enthalten sein.  
  
 **-P** _password_  
 Gibt das Kennwort für die Anmelde-ID an. Wenn diese Option nicht verwendet wird, fordert der Befehl **bcp** zur Eingabe eines Kennworts auf. Wenn diese Option am Ende der Befehlszeile ohne Kennwort verwendet wird, verwendet **bcp** das Standardkennwort (NULL).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../includes/ssnotestrongpass-md.md)]  
  
 Zum Maskieren des Kennworts sollten Sie die Option **-P** nicht in Verbindung mit der Option **-U** angeben. Drücken Sie stattdessen nach der Angabe von **bcp** mit der Option **-U** und anderen Schaltern (geben Sie **-P**nicht an) die EINGABETASTE. Sie werden daraufhin zur Angabe eines Kennworts aufgefordert. Durch diese Methode wird sichergestellt, dass das Kennwort bei der Eingabe maskiert wird.  
  
 Wenn *Kennwort* mit einem Bindestrich (-) oder einem Schrägstrich (/) beginnt, darf kein Leerzeichen zwischen **-P** und dem *Kennwort* -Wert enthalten sein.  
  
 `-q`  
 Führt die SET QUOTED_IDENTIFIERS ON-Anweisung in der Verbindung zwischen dem **bcp** -Hilfsprogramm und einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz aus. Verwenden Sie diese Option, wenn Sie einen Datenbank-, Besitzer-, Tabellen- oder Sichtnamen angeben möchten, der ein Leerzeichen oder ein einfaches Anführungszeichen enthält. Schließen Sie den gesamten dreiteiligen Tabellen- oder Sichtnamen in Anführungszeichen ("") ein.  
  
 Um einen Datenbanknamen anzugeben, der ein Leerzeichen oder ein einfaches Anführungszeichen enthält, müssen Sie die Option **-q** verwenden.  
  
 `-q` gilt nicht für Werte, die an `-d` übergeben wurden.  
  
 Weitere Informationen finden Sie unter "Hinweise" weiter unten in diesem Thema.  
  
 **-r** _Zeilenabschluss_  
 Gibt das Zeilenabschlusszeichen an. Der Standardwert ist **\n** (Zeilenumbruchzeichen). Mit diesem Parameter können Sie das standardmäßige Zeilenabschlusszeichen überschreiben. Weitere Informationen finden Sie unter [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  
  
 Wenn Sie das Zeilenabschlusszeichen in Hexadezimalschreibweise in einem bcp.exe-Befehl angeben, wird der Wert bei 0x00 abgeschnitten. Wenn Sie 0x410041 angeben, wird z. B. 0x41 verwendet.  
  
 Wenn *Zeilenabschluss* mit einem Bindestrich (-) oder einem Schrägstrich (/) beginnt, darf kein Leerzeichen zwischen **-r** und dem *Zeilenabschluss* -Wert enthalten sein.  
  
 **-R**  
 Gibt an, dass beim Massenkopieren von Währungs-, Datums- und Zeitdaten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] das Länderformat verwendet wird, das durch die Gebietsschemaeinstellung des Clientcomputers definiert wird. Standardmäßig werden Ländereinstellungen ignoriert.  
  
 **-S** _Servername_[ **\\** _Instanzname_]  
 Gibt die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz an, mit der eine Verbindung hergestellt wird. Wenn kein Server angegeben wird, stellt das Hilfsprogramm **bcp** eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem lokalen Computer her. Diese Option ist erforderlich, wenn **bcp** von einem Remotecomputer im Netzwerk oder von einer lokalen benannten Instanz ausgeführt wird. Um eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Server herzustellen, geben Sie lediglich *Servername*an. Um eine Verbindung mit der benannten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]herzustellen, geben Sie *Servername  ** _\\_** Instanzname*an.  
  
 `-t` *feldabschluss*  
 Gibt das Feldabschlusszeichen an. Der Standardwert ist **\t** (Tabstoppzeichen). Mit diesem Parameter können Sie das standardmäßige Feldabschlusszeichen überschreiben. Weitere Informationen finden Sie unter [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  
  
 Wenn Sie das Feldabschlusszeichen in Hexadezimalschreibweise in einem bcp.exe-Befehl angeben, wird der Wert bei 0x00 abgeschnitten. Wenn Sie 0x410041 angeben, wird z. B. 0x41 verwendet.  
  
 Wenn *feldabschluss* beginnt mit einem Bindestrich (-) oder einem Schrägstrich (/), darf kein Leerzeichen zwischen `-t` und *feldabschluss* Wert.  
  
 **-T**  
 Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Die Anmeldeinformationen des Netzwerkbenutzers ( *Anmelde-ID*und *Kennwort* ) sind nicht erforderlich. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.  
  
 **-U** _Anmelde-ID_  
 Gibt die Anmelde-ID an, die zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet wird.  
  
> [!IMPORTANT]  
>  Wenn das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt, verwenden Sie die Option **-T** (vertrauenswürdige Verbindung) anstelle der Kombination aus *Benutzername* und *Kennwort* .  
  
 **-v**  
 Meldet die Versionsnummer und Copyrightinformationen des **bcp** -Hilfsprogramms.  
  
 **-V** (**80** | **90** | **100**| **110**)  
 Führt den Massenkopiervorgang mithilfe von Datentypen aus einer früheren Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aus. Diese Option fordert nicht für jedes Feld zu einer Eingabe auf. Es werden die Standardwerte verwendet.  
  
 **80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]  
  
 **90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]  
  
 **110 = [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**  
  
 Verwenden Sie die Option "-V80", um beispielsweise Daten für Typen zu erstellen, die nicht von [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]unterstützt werden, jedoch in spätere Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]integriert wurden.  
  
 Weitere Informationen finden Sie unter [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 `-w`  
 Führt den Massenkopiervorgang mithilfe von Unicode-Zeichen aus. Diese Option fordert nicht für jedes Feld; Er verwendet `nchar` als Speichertyp, keine Präfixe, **\t** (Tabstoppzeichen) als Feldtrennzeichen und **\n** (Zeilenumbruchzeichen) als Zeilenabschlusszeichen. `-w` ist nicht kompatibel mit `-c`.  
  
 Weitere Informationen finden Sie unter [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
 **-x**  
 Bei Verwendung mit den Optionen **format** und **-f**_Formatdatei_ wird anstelle der standardmäßigen Nicht-XML-Formatdatei eine XML-basierte Formatdatei generiert. Beim Importieren oder Exportieren von Daten hat **-x** keine Funktion. Wird die Option weder mit **format** noch mit **-f**_Formatdatei_ verwendet, wird ein Fehler generiert.  
  
## <a name="remarks"></a>Hinweise  
 Die **Bcp** 12.0-Client ist installiert, bei der Installation [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Tools. Wenn sowohl für [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] als auch für eine frühere Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Tools installiert werden, verwenden Sie möglicherweise anstatt des **bcp** 12.0-Clients die frühere Version des **bcp**-Clients. Dies wird durch den Wert der PATH-Umgebungsvariablen bestimmt. Diese Umgebungsvariable definiert die Verzeichnisse, in denen von Windows nach ausführbaren Dateien gesucht wird. Führen Sie an der Windows-Befehlszeile den Befehl **bcp /v** aus, um zu ermitteln, welche Version Sie verwenden. Informationen zum Festlegen des Befehlspfads in der PATH-Umgebungsvariablen finden Sie in der Windows-Hilfe.  
  
 XML-Formatdateien werden nur unterstützt, wenn die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tools zusammen mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client installiert werden.  
  
 Informationen zum Speicherort und zum Verwenden des Hilfsprogramms **bcp** sowie zu den für Eingabeaufforderungs-Hilfsprogramme geltenden Syntaxkonventionen finden Sie unter [Referenz zum Eingabeaufforderungs-Hilfsprogramm &#40;Datenbank-Engine&#41;](../tools/command-prompt-utility-reference-database-engine.md).  
  
 Informationen zum Vorbereiten von Daten für Massenimport- oder Massenexportvorgänge finden Sie unter [Vorbereiten von Daten für den Massenexport oder -import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 Informationen dazu, wann Zeileneinfügevorgänge, die durch den Massenimport ausgeführt werden, im Transaktionsprotokoll protokolliert werden, finden Sie unter [Voraussetzungen für die minimale Protokollierung beim Massenimport](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
## <a name="native-data-file-support"></a>Systemeigene Datendateiunterstützung  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]unterstützt das **bcp** -Hilfsprogramm nur native Datendateien, die mit [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]und [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]kompatibel sind.  
  
## <a name="computed-columns-and-timestamp-columns"></a>Berechnete Spalten und Zeitstempel-Spalten  
 In der zu importierenden Datendatei enthaltene Werte für berechnete oder `timestamp`-Spalten werden ignoriert. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] weist Werte automatisch zu. Wenn die Datendatei keine Werte für die berechneten oder `timestamp`-Spalten der Tabelle enthält, geben Sie mithilfe einer Formatdatei an, dass die berechneten oder `timestamp`-Spalten beim Importieren von Daten ausgelassen werden sollen. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] weist diesen Spalten automatisch Werte zu.  
  
 Berechnete und `timestamp`-Spalten werden wie gewohnt aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine Datendatei massenkopiert.  
  
## <a name="specifying-identifiers-that-contain-spaces-or-quotation-marks"></a>Angeben von Bezeichnern mit Leerzeichen oder Anführungszeichen  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Bezeichner können Zeichen wie z.B. eingebettete Leerzeichen und Anführungszeichen enthalten. Diese Bezeichner müssen folgendermaßen behandelt werden:  
  
-   Wenn Sie an der Eingabeaufforderung einen Bezeichner oder Dateinamen angeben, der ein Leerzeichen oder ein Anführungszeichen enthält, müssen Sie den Bezeichner in Anführungszeichen ("") einschließen.  
  
     Mit dem Befehl `bcp out` wird beispielsweise die Datendatei `Currency Types.dat`erstellt:  
  
    ```  
    bcp AdventureWorks2012.Sales.Currency out "Currency Types.dat" -T -c  
    ```  
  
-   Sie müssen die Option `-q` verwenden, um einen Datenbanknamen anzugeben, der ein Leerzeichen oder Anführungszeichen enthält.  
  
-   Bei Besitzer-, Tabellen- oder Sichtnamen, die eingebettete Leerzeichen oder Anführungszeichen enthalten, ist Folgendes möglich:  
  
    -   Angeben der Option `-q`.  
  
    -   Einschließen des Besitzer-, Tabellen- oder Sichtnamens in eckige Klammern ([]) innerhalb der Anführungszeichen.  
  
## <a name="data-validation"></a>Datenüberprüfung  
 **bcp** erzwingt nun Datenüberprüfungen, die dazu führen können, dass Skripts einen Fehler erzeugen, wenn sie für ungültige Daten in einer Datendatei ausgeführt werden. So wird durch **bcp** jetzt Folgendes überprüft:  
  
-   Die systemeigene Darstellung der Datentypen `float` oder `real` ist gültig.  
  
-   Unicode-Daten besitzen eine gerade Bytelänge.  
  
 Formulare mit ungültigen Daten, die in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] noch massenimportiert werden konnten, werden nun möglicherweise nicht mehr geladen. In früheren Versionen trat der Fehler erst auf, wenn ein Client versuchte, auf die ungültigen Daten zuzugreifen. Durch die zusätzliche Überprüfung werden überraschende Ergebnisse beim Abfragen der Daten nach dem Massenladen minimiert.  
  
## <a name="bulk-exporting-or-importing-sqlxml-documents"></a>Massenexportieren und -importieren von SQLXML-Dokumenten  
 Verwenden Sie in der Formatdatei einen der folgenden Datentypen für den Massenexport oder -import von SQLXML-Daten.  
  
|Datentyp|Wirkung|  
|---------------|------------|  
|SQLCHAR oder SQLVARYCHAR|Die Daten werden in der Clientcodepage gesendet bzw. in der durch die Sortierung implizierten Codeseite. Der Effekt ist derselbe, als wenn der Schalter `-c` ohne eine Formatdatei angegeben wird.|  
|SQLNCHAR oder SQLNVARCHAR|Die Daten werden im Unicode-Format gesendet. Der Effekt ist derselbe, als wenn der Schalter `-w` ohne eine Formatdatei angegeben wird.|  
|SQLBINARY oder SQLVARYBIN|Die Daten werden ohne Konvertierung gesendet.|  
  
## <a name="permissions"></a>Berechtigungen  
 Ein **bcpout**-Vorgang erfordert SELECT-Berechtigungen für die Quelltabelle.  
  
 Ein **bcpin**-Vorgang erfordert mindestens SELECT/INSERT-Berechtigungen für die Zieltabelle. Darüber hinaus sind ALTER TABLE-Berechtigungen erforderlich, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Es sind Einschränkungen vorhanden, und der CHECK_CONSTRAINTS-Hinweis wurde nicht angegeben.  
  
    > [!NOTE]  
    >  Die Deaktivierung von Einschränkungen wurde als Standardverhalten festgelegt. Verwenden Sie die Option **-h** mit dem CHECK_CONSTRAINTS-Hinweis, wenn Einschränkungen explizit aktiviert werden sollen.  
  
-   Es sind Trigger vorhanden, und der FIRE_TRIGGER-Hinweis wurde nicht angegeben.  
  
    > [!NOTE]  
    >  Standardmäßig werden Trigger nicht ausgelöst. Verwenden Sie die Option **-h** mit dem FIRE_TRIGGERS-Hinweis, wenn Trigger explizit ausgelöst werden sollen.  
  
-   Mithilfe der Option **-E** importieren Sie Identitätswerte aus einer Datendatei.  
  
> [!NOTE]  
>  ALTER TABLE-Berechtigungen für die Zieltabelle sind erst seit [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]erforderlich. Diese neue Anforderung kann dazu führen, dass **bcp** -Skripts, die keine Trigger und Einschränkungsüberprüfungen erzwingen, einen Fehler erzeugen, wenn das Benutzerkonto nicht über ALTER TABLE-Berechtigungen für die Zieltabelle verfügt.  
  
## <a name="character-mode--c-and-native-mode--n-best-practices"></a>Zeichenmodus (-c)- und einheitlicher Modus (-n) – Bewährte Methoden  
 Dieser Abschnitt beinhaltet Empfehlungen für den Zeichenmodus (-c) und den einheitlichen Modus (-n).  
  
-   (Administrator/Benutzer) Wenn möglich, verwenden Sie das einheitliche Format (-n), um das Trennzeichenproblem zu vermeiden. Verwenden Sie das einheitliche Format für Export- und Importvorgänge mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Exportieren Sie Daten aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit der -c- oder -w-Option, wenn die Daten in eine Nicht-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank importiert werden.  
  
-   (Administrator) überprüfen Sie Daten, wenn Sie BCP OUT verwenden. Wenn Sie z. B. BCP OUT, BCP IN und dann BCP OUT verwenden, überprüfen Sie, ob die Daten ordnungsgemäß exportiert werden, und ob die Abschlusszeichenwerte nicht als Teil eines Datenwerts verwendet werden. Erwägen Sie, die Standardabschlusszeichen (mithilfe von -t- und -r-Optionen) mit zufälligen Hexadezimalwerten zu überschreiben, um Konflikte zwischen Abschlusszeichenwerten und Datenwerten zu vermeiden.  
  
-   (Benutzer) Verwenden Sie ein langes und eindeutiges Abschlusszeichen (eine Byte- oder Zeichensequenz), um die Wahrscheinlichkeit eines Konflikts mit dem tatsächlichen Zeichenfolgenwert zu minimieren. Verwenden Sie dazu die -t-Option und die -r-Option.  
  
## <a name="examples"></a>Beispiele  
 Dieser Abschnitt enthält die folgenden Beispiele:  
  
-   A. Kopieren von Tabellenzeilen in eine Datendatei (mit einer vertrauenswürdigen Verbindung)  
  
-   B. Kopieren von Tabellenzeilen in eine Datendatei (mit Authentifizierung im gemischten Modus)  
  
-   C. Kopieren von Daten aus einer Datei in eine Tabelle  
  
-   D. Kopieren einer bestimmten Spalte in eine Datendatei  
  
-   E. Kopieren einer bestimmten Zeile in eine Datendatei  
  
-   F. Kopieren von Daten aus einer Abfrage in eine Datendatei  
  
-   G. Erstellen einer Nicht-XML-Formatdatei  
  
-   H. Erstellen einer XML-Formatdatei  
  
-   I. Verwenden einer Formatdatei für einen Massenimport mithilfe von **bcp**  
  
### <a name="a-copying-table-rows-into-a-data-file-with-a-trusted-connection"></a>A. Kopieren von Tabellenzeilen in eine Datendatei (mit einer vertrauenswürdigen Verbindung)  
 Im folgenden Beispiel wird die Verwendung der Option **out** in der `AdventureWorks2012.Sales.Currency` -Tabelle veranschaulicht. In diesem Beispiel wird die Datendatei `Currency.dat` erstellt, und die Tabellendaten werden mithilfe eines Zeichenformats in die Datendatei kopiert. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie folgenden Befehl an der Eingabeaufforderung ein:  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -T -c  
```  
  
### <a name="b-copying-table-rows-into-a-data-file-with-mixed-mode-authentication"></a>B. Kopieren von Tabellenzeilen in eine Datendatei (mit Authentifizierung im gemischten Modus)  
 Im folgenden Beispiel wird die Verwendung der Option **out** in der `AdventureWorks2012.Sales.Currency` -Tabelle veranschaulicht. In diesem Beispiel wird die Datendatei `Currency.dat` erstellt, und die Tabellendaten werden mithilfe eines Zeichenformats in die Datendatei kopiert.  
  
 Bei diesem Beispiel wird vorausgesetzt, dass Sie die Authentifizierung im gemischten Modus verwenden. Sie müssen daher den Schalter **-U** verwenden, um die Anmelde-ID anzugeben. Sofern Sie keine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem lokalen Computer herstellen, müssen Sie außerdem mit dem Schalter **-S** den Systemnamen und optional einen Instanznamen angeben.  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -c -U<login_id> -S<server_name\instance_name>  
```  
  
 Das System fordert Sie zur Eingabe des Kennworts auf.  
  
### <a name="c-copying-data-from-a-file-to-a-table"></a>C. Kopieren von Daten aus einer Datei in eine Tabelle  
 Im folgenden Beispiel wird die Verwendung der Option **in** mithilfe der Datei veranschaulicht, die im vorherigen Beispiel erstellt wurde (`Currency.dat`). Zuerst wird in diesem Beispiel jedoch eine leere Kopie der `AdventureWorks2012 Sales.Currency`-Tabelle (`Sales.Currency2`) erstellt, in die die Daten kopiert werden. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie den folgenden Befehl im Abfrage-Editor ein, um die leere Tabelle zu erstellen:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO AdventureWorks2012.Sales.Currency2   
FROM AdventureWorks2012.Sales.Currency WHERE 1=2;  
```  
  
 Geben Sie den folgenden Befehl an der Eingabeaufforderung ein, um die Zeichendaten per Massenvorgang in die neue Tabelle zu kopieren (d. h. um die Daten zu importieren):  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -c  
```  
  
 Zeigen Sie den Inhalt der Tabelle im Abfrage-Editor ein und geben Sie Folgendes ein, um zu überprüfen, ob der Befehl erfolgreich ausgeführt wurde:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM Sales.Currency2  
```  
  
### <a name="d-copying-a-specific-column-into-a-data-file"></a>D. Kopieren einer bestimmten Spalte in eine Datendatei  
 Zum Kopieren einer bestimmten Spalte können Sie die Option **queryout** verwenden. Im folgenden Beispiel wird nur die `Name`-Spalte der `Sales.Currency`-Tabelle in eine Datendatei kopiert. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp "SELECT Name FROM AdventureWorks.Sales.Currency" queryout Currency.Name.dat -T -c  
```  
  
### <a name="e-copying-a-specific-row-into-a-data-file"></a>E. Kopieren einer bestimmten Zeile in eine Datendatei  
 Zum Kopieren einer bestimmten Zeile können Sie die Option **queryout** verwenden. Im folgenden Beispiel wird nur die Zeile für den Kontakt mit dem Namen `Jarrod Rana` aus der Tabelle `AdventureWorks2012.Person.Person` in eine Datendatei (`Jarrod Rana.dat`) kopiert. In dem Beispiel wird davon ausgegangen, dass Sie die Windows-Authentifizierung verwenden und dass eine vertrauenswürdige Verbindung zu der Serverinstanz besteht, auf der der **bcp**-Befehl ausgeführt wird.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp "SELECT * FROM AdventureWorks2012.Person.Person WHERE FirstName='Jarrod' AND LastName='Rana' "  queryout "Jarrod Rana.dat" -T -c  
```  
  
### <a name="f-copying-data-from-a-query-to-a-data-file"></a>F. Kopieren von Daten aus einer Abfrage in eine Datendatei  
 Zum Kopieren des Resultsets einer [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung in eine Datendatei verwenden Sie die Option **queryout**. Im folgenden Beispiel werden die Namen aus der `AdventureWorks2012.Person.Person`-Tabelle nach Nachnamen und dann nach Vornamen geordnet in die Datendatei `Contacts.txt` kopiert. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp "SELECT FirstName, LastName FROM AdventureWorks2012.Person.Person ORDER BY LastName, Firstname" queryout Contacts.txt -c -T  
```  
  
### <a name="g-creating-a-non-xml-format-file"></a>G. Erstellen einer Nicht-XML-Formatdatei  
 Im folgenden Beispiel wird die XML-Formatdatei `Currency.fmt` für die `Sales.Currency`-Tabelle in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Datenbank erstellt. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c  -f Currency.fmt  
```  
  
 Weitere Informationen finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)unterstützt wird.  
  
### <a name="h-creating-an-xml-format-file"></a>H. Erstellen einer XML-Formatdatei  
 In dem folgenden Beispiel wird die XML-Formatdatei `Currency.xml` für die `Sales.Currency`-Tabelle in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Datenbank erstellt. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c -x -f Currency.xml  
```  
  
> [!NOTE]  
>  Um die Option **-x** zu verwenden, müssen Sie über einen **bcp** 9.0-Client verfügen. Informationen zum Verwenden des **bcp** 9.0-Clients finden Sie unter „Hinweise“.  
  
 Weitere Informationen finden Sie unter [XML-Formatdateien &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).  
  
### <a name="i-using-a-format-file-to-bulk-import-with-bcp"></a>I. Verwenden einer Formatdatei für einen Massenimport mithilfe von bcp  
 Wenn Sie eine zuvor erstellte Formatdatei zum Importieren von Daten in eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz verwenden möchten, müssen Sie den Schalter **-f** mit der Option **in** verwenden. So wird beispielsweise durch den folgenden Befehl der Inhalt der Datendatei `Currency.dat` in eine Kopie der `Sales.Currency`-Tabelle (`Sales.Currency2`) massenkopiert, wobei die zuvor erstellte Formatdatei `Currency.xml` verwendet wird. Bei diesem Beispiel wird vorausgesetzt, dass Sie die Windows-Authentifizierung verwenden und über eine vertrauenswürdige Verbindung mit der Serverinstanz verfügen, auf der Sie den **bcp**-Befehl ausführen.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -f Currency.xml  
```  
  
> [!NOTE]  
>  Formatdateien erweisen sich besonders dann als nützlich, wenn die Felder in der Datendatei z. B. hinsichtlich Anzahl, Reihenfolge oder Datentypen von den Tabellenspalten abweichen. Weitere Informationen finden Sie unter [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)erforderlich.  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
 Die folgenden Themen enthalten Beispiele zur Verwendung von **bcp**:  
  
-   [Erstellen einer Formatdatei &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)  
  
-   [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Beibehalten von Identitätswerten beim Massenimport von Daten &#40;SQL Server&#41;](../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Vorbereiten von Daten für den Massenexport oder -import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [sp_tableoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)   
 [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
