---
title: Ausführen von Massen Kopier Vorgängen | Microsoft-Dokumentation
description: Ausführen von Massen Kopier Vorgängen mithilfe OLE DB Treibers für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- bulk copy [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], bulk copy operations
- OLE DB Driver for SQL Server, bulk copy operations
- MSOLEDBSQL, bulk copy operations
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c6b1d33f4a0a768d33ebe9613c0c0cb97c5e77c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988984"
---
# <a name="performing-bulk-copy-operations"></a>Durchführen von Massenkopiervorgängen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die Massenkopierfunktion von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt die Übertragung großer Datenmengen in bzw. aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle oder Sicht. Daten können auch mithilfe einer SELECT-Anweisung aus einer Tabelle oder Sicht übertragen werden. Die Daten können zwischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und einer Betriebssystemdatendatei verschoben werden, z. B. eine ASCII-Datei. Datendateien können verschiedene Formate aufweisen. Das Format wird in einer Formatdatei definiert. Optional können die Daten in Programmvariablen geladen und mithilfe von Massenkopierfunktionen und -methoden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] übertragen werden.  
  
 Eine Beispielanwendung, die diese Funktion veranschaulicht, finden [Sie unter Massen Daten kopieren mithilfe von &#40;IRowsetFastLoad OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 Eine Anwendung verwendet Massenkopiervorgänge in der Regel in einer der folgenden Arten:  
  
-   Massenkopieren aus einer Tabelle, Sicht oder dem Resultset einer Transact-SQL-Anweisung in eine Datendatei, in der die Daten im selben Format gespeichert werden wie in der Tabelle bzw. Sicht.  
  
     Diese Datei wird als Datendatei im einheitlichen Modus bezeichnet.  
  
-   Massenkopieren aus einer Tabelle, Sicht oder dem Resultset einer Transact-SQL-Anweisung in eine Datendatei, in der die Daten in einem anderen Format gespeichert werden als in der Tabelle bzw. Sicht.  
  
     In diesem Fall wird eine separate Formatdatei erstellt, in der die Charakteristika (Datentyp, Position, Länge, Abschlusszeichen, usw.) der einzelnen, in der Datendatei zu speichernden Spalten definiert werden. Wenn alle Spalten in Zeichenformat konvertiert werden, wird die resultierende Datei als Datendatei im Zeichenmodus bezeichnet.  
  
-   Massenkopieren aus einer Datendatei in eine Tabelle oder Sicht.  
  
     Gegebenenfalls wird eine Formatdatei verwendet, um das Layout der Datendatei zu bestimmen.  
  
-   Laden der Daten in Programmvariablen und anschließender Import der Daten in eine Tabelle oder Sicht unter Verwendung der Massenkopierfunktionen für das Massenkopieren von jeweils einer Zeile.  
  
 Datendateien, die von Massenkopierfunktionen verwendet werden, brauchen nicht von einem anderen Massenkopierprogramm erstellt worden sein. Beliebige andere Systeme können entsprechend den Massenkopierdefinitionen Datendateien und Formatdateien generieren. Diese Dateien können dann mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Massenkopierprogramm verwendet werden, um Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu importieren. Beispielsweise könnten Sie Daten aus einer Kalkulationstabelle in eine durch Tabstopps getrennte Datei exportieren, eine die durch Tabstopps getrennte Datei in einer Formatdatei beschreiben und schließlich mithilfe eines Massenkopierprogramms die Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] importieren. Datendateien, die mit einer Massenkopierfunktion generiert wurden, können auch in andere Anwendungen importiert werden. Beispielsweise könnten Sie Massenkopierfunktionen verwenden, um Daten aus einer Tabelle oder Sicht in eine durch Tabstopps getrennte Datei zu exportieren, die Sie dann in eine Kalkulationstabelle laden.  
  
 Programmierern von Anwendungen, die Massenkopierfunktionen verwenden, wird empfohlen, folgende allgemeine Regeln zu beachten, um die Leistung des Massenkopierens zu gewähren. Weitere Informationen zur Unterstützung von Massen Kopier Vorgängen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]in finden Sie unter [Massen Import und- &#40;Export&#41;von Daten SQL Server](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
 Ein CLR-benutzerdefinierter Typ (User Defined Type, UDT) muss als Binärdaten gebunden werden. Auch wenn eine Formatdatei SQLCHAR als Datentyp für eine Ziel-UDT-Spalte angibt, verarbeitet das BCP-Hilfsprogramm die Daten als Binärdaten.  
  
 SET FMTONLY OFF kann nicht mit Massenkopiervorgängen verwendet werden. SET FMTONLY OFF führt möglicherweise bei Massenkopiervorgängen zu unerwarteten Ergebnissen oder Fehlern.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server 
 Der OLE DB-Treiber für SQL Server implementiert zwei Methoden zum Ausführen von Massen Kopier Vorgängen mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank. Bei der ersten Methode kommt die [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)-Schnittstelle für speicherbasierte Massenkopiervorgänge zur Anwendung. Die zweite Methode stützt sich auf die [IBCPSession](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)-Schnittstelle für dateibasierte Massenkopiervorgänge.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Verwenden von speicherbasierten Massenkopiervorgängen  
 Der OLE DB-Treiber für SQL Server implementiert die **IRowsetFastLoad**-Schnittstelle, um die Unterstützung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-speicherbasierte Massenkopiervorgänge verfügbar zu machen. Die **IRowsetFastLoad**-Schnittstelle implementiert die Methoden [IRowsetFastLoad::Commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md) und [IRowsetFastLoad::InsertRow](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md).  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Aktivieren einer Sitzung für IRowsetFastLoad  
 Der Consumer benachrichtigt den OLE DB Treiber, dass er für das Massen kopieren SQL Server muss, indem er den OLE DB Treiber für SQL Server spezifische Datenquellen Eigenschaft SSPROP_ENABLEFASTLOAD auf VARIANT_TRUE festlegt. Wenn die-Eigenschaft für die Datenquelle festgelegt ist, erstellt der Consumer einen OLE DB Treiber für SQL Server Sitzung. Die neue Sitzung lässt den Zugriff des Consumers auf die **IRowsetFastLoad**-Schnittstelle zu.  
  
> [!NOTE]  
>  Wenn die **IDataInitialize**-Schnittstelle für die Initialisierung der Datenquelle verwendet wird, muss die SSPROP_IRowsetFastLoad-Eigenschaft im *rgPropertySets*-Parameter der **IOpenRowset::OpenRowset**-Methode festgelegt werden. Andernfalls gibt der Aufruf der **OpenRowset**-Methode E_NOINTERFACE zurück.  
  
 Durch das Aktivieren einer Sitzung für das Massen kopieren wird der OLE DB-Treiber auf SQL Server Unterstützung für Schnittstellen in der Sitzung eingeschränkt. Eine Sitzung mit aktivierter Massenkopierfunktion bietet lediglich die folgenden Schnittstellen:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Um die Erstellung massenkopierter Rowsets zu deaktivieren und die Sitzung des OLE DB-Treibers für SQL Server auf die Standardverarbeitungsweise zurückzusetzen, setzen Sie SSPROP_ENABLEFASTLOAD auf VARIANT_FALSE zurück.  
  
#### <a name="irowsetfastload-rowsets"></a>IRowsetFastLoad Rowsets  
 Die massenkopierten Rowsets im OLE DB-Treiber für SQL Server weisen nur Schreibzugriff auf, machen jedoch Schnittstellen verfügbar, die dem Consumer ermöglichen, die Struktur einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle zu bestimmen. Die folgenden Schnittstellen werden auf einem Massen Kopier fähigen OLE DB Treiber für SQL Server Rowset verfügbar gemacht:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Die anbieterspezifischen Eigenschaften SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS und SSPROP_FASTLOADKEEPIDENTITY steuern die Verhaltensweisen des Massenkopierrowsets eines OLE DB-Treibers für SQL Server. Die Eigenschaften werden im *rgProperties*-Element eines *rgPropertySets* **IOpenRowset**-Parameterelements angegeben.  
  
|Eigenschafts-ID|und Beschreibung|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Spalte: No<br /><br /> R/W: Lesen/Schreiben<br /><br /> Typ: VT_BOOL<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Verwaltet vom Consumer angegebene Identitätswerte.<br /><br /> VARIANT_FALSE: Werte für eine Identitätsspalte in der Tabelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] generiert. Alle Werte, die für die Spalte gebunden sind, werden vom OLE DB Treiber für SQL Server ignoriert.<br /><br /> VARIANT_TRUE: Der Consumer bindet einen Accessor, der einen Wert für eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Identitätsspalte bereitstellt. Die IDENTITY-Eigenschaft ist nicht für Spalten verfügbar, die NULL-Werte akzeptieren, daher stellt der Consumer für jeden **IRowsetFastLoad::Insert**-Aufruf einen eindeutigen Wert bereit.|  
|SSPROP_FASTLOADKEEPNULLS|Spalte: No<br /><br /> R/W: Lesen/Schreiben<br /><br /> Typ: VT_BOOL<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Behält NULL-Werte für Spalten mit einer DEFAULT-Einschränkung bei. Betrifft nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Spalten, die NULL-Werte akzeptieren und eine DEFAULT-Einschränkung aufweisen.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fügt den Standardwert für die Spalte ein, wenn der Consumer des OLE DB-Treibers für SQL Server eine Zeile einfügt, die einen NULL-Wert für die Spalte enthält.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fügt einen NULL-Wert für den Spaltenwert ein, wenn der Consumer des OLE DB-Treibers für SQL Server eine Zeile einfügt, die einen NULL-Wert für die Spalte enthält.|  
|SSPROP_FASTLOADOPTIONS|Spalte: No<br /><br /> R/W: Lesen/Schreiben<br /><br /> Typ: VT_BSTR<br /><br /> Standardwert: keiner<br /><br /> Beschreibung: Diese Eigenschaft ist mit der Option **-h** "*hint*[,...*n*]" des **bcp**-Hilfsprogramms identisch. Die folgende(n) Zeichenfolge(n) kann/können beim Massenkopieren von Daten in eine Tabelle optional verwendet werden.<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,...*n*]): Sortierreihenfolge nach Daten in der Datendatei. Die Leistung des Massenkopierens wird verbessert, wenn die zu ladende Datendatei entsprechend dem gruppierten Index der Tabelle sortiert ist.<br /><br /> **ROWS_PER_BATCH** = *bb*: Anzahl der Datenzeilen pro Batch (als *bb*). Der Server optimiert das Massenladen entsprechend dem Wert von *bb*. Standardmäßig ist **ROWS_PER_BATCH** unbekannt.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: Die Anzahl der Kilobytes (KB) an Daten pro Batch (als cc). Standardmäßig ist **KILOBYTES_PER_BATCH** unbekannt.<br /><br /> **TABLOCK**: Eine Sperre auf Tabellenebene wird für die Dauer des Massenimportvorgangs aktiviert. Diese Option verbessert die Leistung beträchtlich, da weniger Sperrkonflikte für die Tabelle auftreten, wenn diese nur während des Massenkopiervorgangs gesperrt wird. Eine Tabelle kann gleichzeitig von mehreren Clients geladen werden, wenn die Tabelle keine Indizes aufweist und **TABLOCK** angegeben ist. Standardmäßig wird das Sperrverhalten durch die Tabellenoption **table lock on bulk load** bestimmt.<br /><br /> **CHECK_CONSTRAINTS**: Alle Einschränkungen für *table_name* werden während des Massenkopiervorgangs überprüft. Standardmäßig werden Einschränkungen ignoriert.<br /><br /> **FIRE_TRIGGER**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet die Zeilenversionsverwaltung für Trigger und speichert die Zeilenversionen im Versionsspeicher in **tempdb**. Deshalb sind Massenprotokollierungsoptimierungen verfügbar, auch wenn Trigger aktiviert sind. Bevor Sie einen Massenimport eines Batches mit einer großen Anzahl von Zeilen vornehmen, für die Trigger aktiviert sind, müssen Sie gegebenenfalls die Größe von **tempdb** erweitern.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Verwenden von dateibasierten Massenkopiervorgängen  
 Der OLE DB-Treiber für SQL Server implementiert die **IBCPSession**-Schnittstelle, um die Unterstützung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-dateibasierte Massenkopiervorgänge verfügbar zu machen. Die **IBCPSession**-Schnittstelle implementiert die Methoden [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) und [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md).  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Datenquelleneigenschaften &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Massenimport und -export von Daten &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Optimieren der Leistung des Massenimports](https://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  

