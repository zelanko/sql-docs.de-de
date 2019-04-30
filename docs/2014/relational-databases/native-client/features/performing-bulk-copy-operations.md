---
title: Durchführen von Massenkopiervorgängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [SQL Server Native Client]
- data access [SQL Server Native Client], bulk copy operations
- SQL Server Native Client, bulk copy operations
- SQLNCLI, bulk copy operations
ms.assetid: 50d8456b-e6a1-4b25-bc7e-56946ed654a7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c33c5adeb748f3a714112faf7410684413cf0cd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225627"
---
# <a name="performing-bulk-copy-operations"></a>Durchführen von Massenkopiervorgängen
  Die Massenkopierfunktion von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt die Übertragung großer Datenmengen in bzw. aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle oder Sicht. Daten können auch mithilfe einer SELECT-Anweisung aus einer Tabelle oder Sicht übertragen werden. Die Daten können zwischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und einer Betriebssystemdatendatei verschoben werden, z. B. eine ASCII-Datei. Datendateien können verschiedene Formate aufweisen. Das Format wird in einer Formatdatei definiert. Optional können die Daten in Programmvariablen geladen und mithilfe von Massenkopierfunktionen und -methoden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] übertragen werden.  
  
 Eine beispielanwendung, die diese Funktion veranschaulicht wird, finden Sie unter [Bulk Daten mithilfe von IRowsetFastLoad &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/irowsetfastload-ole-db.md).  
  
 Eine Anwendung verwendet Massenkopiervorgänge in der Regel in einer der folgenden Arten:  
  
-   Massenkopieren aus einer Tabelle, Sicht oder dem Resultset einer Transact-SQL-Anweisung in eine Datendatei, in der die Daten im selben Format gespeichert werden wie in der Tabelle bzw. Sicht.  
  
     Diese Datei wird als Datendatei im einheitlichen Modus bezeichnet.  
  
-   Massenkopieren aus einer Tabelle, Sicht oder dem Resultset einer Transact-SQL-Anweisung in eine Datendatei, in der die Daten in einem anderen Format gespeichert werden als in der Tabelle bzw. Sicht.  
  
     In diesem Fall wird eine separate Formatdatei erstellt, in der die Charakteristika (Datentyp, Position, Länge, Abschlusszeichen, usw.) der einzelnen, in der Datendatei zu speichernden Spalten definiert werden. Wenn alle Spalten in Zeichenformat konvertiert werden, wird die resultierende Datei als Datendatei im Zeichenmodus bezeichnet.  
  
-   Massenkopieren aus einer Datendatei in eine Tabelle oder Sicht.  
  
     Gegebenenfalls wird eine Formatdatei verwendet, um das Layout der Datendatei zu bestimmen.  
  
-   Laden der Daten in Programmvariablen und anschließender Import der Daten in eine Tabelle oder Sicht unter Verwendung der Massenkopierfunktionen für das Massenkopieren von jeweils einer Zeile.  
  
 Datendateien, die von Massenkopierfunktionen verwendet werden, brauchen nicht von einem anderen Massenkopierprogramm erstellt worden sein. Beliebige andere Systeme können entsprechend den Massenkopierdefinitionen Datendateien und Formatdateien generieren. Diese Dateien können dann mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Massenkopierprogramm verwendet werden, um Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu importieren. Beispielsweise könnten Sie Daten aus einer Kalkulationstabelle in eine durch Tabstopps getrennte Datei exportieren, eine die durch Tabstopps getrennte Datei in einer Formatdatei beschreiben und schließlich mithilfe eines Massenkopierprogramms die Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] importieren. Datendateien, die mit einer Massenkopierfunktion generiert wurden, können auch in andere Anwendungen importiert werden. Beispielsweise könnten Sie Massenkopierfunktionen verwenden, um Daten aus einer Tabelle oder Sicht in eine durch Tabstopps getrennte Datei zu exportieren, die Sie dann in eine Kalkulationstabelle laden.  
  
 Programmierern von Anwendungen, die Massenkopierfunktionen verwenden, wird empfohlen, folgende allgemeine Regeln zu beachten, um die Leistung des Massenkopierens zu gewähren. Weitere Informationen zur Unterstützung für Massenkopiervorgänge in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], finden Sie unter [Massenimport und-Export von Daten &#40;SQL Server&#41;](../../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
 Ein CLR-benutzerdefinierter Typ (User Defined Type, UDT) muss als Binärdaten gebunden werden. Auch wenn eine Formatdatei SQLCHAR als Datentyp für eine Ziel-UDT-Spalte angibt, verarbeitet das BCP-Hilfsprogramm die Daten als Binärdaten.  
  
 SET FMTONLY OFF kann nicht mit Massenkopiervorgängen verwendet werden. SET FMTONLY OFF führt möglicherweise bei Massenkopiervorgängen zu unerwarteten Ergebnissen oder Fehlern.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert zwei Methoden zum Ausführen von Massenkopiervorgängen mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank. Bei der ersten Methode kommt die [IRowsetFastLoad](../../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)-Schnittstelle für speicherbasierte Massenkopiervorgänge zur Anwendung. Die zweite Methode stützt sich auf die [IBCPSession](../../native-client-ole-db-interfaces/ibcpsession-ole-db.md)-Schnittstelle für dateibasierte Massenkopiervorgänge.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Verwenden von speicherbasierten Massenkopiervorgängen  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert die **IRowsetFastLoad** Unterstützung für COM verfügbar gemacht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] speicherbasierte Massenkopiervorgänge. Die **IRowsetFastLoad**-Schnittstelle implementiert die Methoden [IRowsetFastLoad::Commit](../../native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) und [IRowsetFastLoad::InsertRow](../../native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md).  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Aktivieren einer Sitzung für IRowsetFastLoad  
 Der Consumer benachrichtigt den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter, dass ein Massenkopiervorgang erforderlich ist, indem er für die SSPROP_ENABLEFASTLOAD-Eigenschaft, die für den systemeigenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client-OLE DB-Anbieter spezifisch ist, VARIANT_TRUE festlegt. Wenn die Datenquelle für die Eigenschaft festgelegt wurde, erstellt der Consumer eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbietersitzung. Die neue Sitzung lässt den Zugriff des Consumers auf die **IRowsetFastLoad**-Schnittstelle zu.  
  
> [!NOTE]  
>  Wenn die **IDataInitialize**-Schnittstelle für die Initialisierung der Datenquelle verwendet wird, muss die SSPROP_IRowsetFastLoad-Eigenschaft im *rgPropertySets*-Parameter der **IOpenRowset::OpenRowset**-Methode festgelegt werden. Andernfalls gibt der Aufruf der **OpenRowset**-Methode E_NOINTERFACE zurück.  
  
 Das Aktivieren einer Sitzung zum Massenkopieren schränkt die Unterstützung des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieters für Schnittstellen in dieser Sitzung ein. Eine Sitzung mit aktivierter Massenkopierfunktion bietet lediglich die folgenden Schnittstellen:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Um die Erstellung massenkopierter Rowsets zu deaktivieren und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbietersitzung auf die Standardverarbeitungsweise zurückzusetzen, legen Sie für SSPROP_ENABLEFASTLOAD den Parameter VARIANT_FALSE fest.  
  
#### <a name="irowsetfastload-rowsets"></a>IRowsetFastLoad Rowsets  
 Die massenkopierten Rowsets im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter weisen nur Schreibzugriff auf, machen jedoch Schnittstellen verfügbar, die dem Consumer ermöglichen, die Struktur einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle zu bestimmen. Die folgenden Schnittstellen sind in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieterrowsets verfügbar, in denen die Massenkopierfunktion aktiviert ist:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Die anbieterspezifischen Eigenschaften SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS und SSPROP_FASTLOADKEEPIDENTITY steuern die Verhalten des Massenkopierrowsets eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieters. Die Eigenschaften angegeben werden, der *RgProperties* Mitglied einer _RgPropertySets_**IOpenRowset**Parameter-Element.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Spalte: Nein<br /><br /> R/W: Lese-/Schreibzugriff<br /><br /> Typ: VT_BOOL<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Verwaltet vom Consumer angegebene Identitätswerte.<br /><br /> VARIANT_FALSE: Werte für eine Identitätsspalte in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle werden generiert, indem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Jeder Wert gebunden werden, für die Spalte, durch ignoriert wird die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter.<br /><br /> VARIANT_TRUE: Der Consumer bindet einen Accessor, der ein Wert für eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Identity-Spalte. Die IDENTITY-Eigenschaft ist nicht für Spalten verfügbar, die NULL-Werte akzeptieren, daher stellt der Consumer für jeden **IRowsetFastLoad::Insert**-Aufruf einen eindeutigen Wert bereit.|  
|SSPROP_FASTLOADKEEPNULLS|Spalte: Nein<br /><br /> R/W: Lese-/Schreibzugriff<br /><br /> Typ: VT_BOOL<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Behält NULL-Werte für Spalten mit DEFAULT-Einschränkung. Betrifft nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Spalten, die NULL-Werte akzeptieren und eine DEFAULT-Einschränkung aufweisen.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fügt den Standardwert für die Spalte ein, wenn der Consumer des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieters eine Zeile einfügt, die einen NULL-Wert für die Spalte enthält.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fügt einen NULL-Wert in die Spalte ein, wenn der Consumer des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieters eine Zeile einfügt, die einen NULL-Wert für die Spalte enthält.|  
|SSPROP_FASTLOADOPTIONS|Spalte: Nein<br /><br /> R/W: Lese-/Schreibzugriff<br /><br /> Typ: VT_BSTR<br /><br /> Standardwert: keiner<br /><br /> Beschreibung: Diese Eigenschaft ist identisch mit der **-h** "*Hinweis*[,... *n*] "Möglichkeit, die **Bcp** Hilfsprogramm. Die folgende(n) Zeichenfolge(n) kann/können beim Massenkopieren von Daten in eine Tabelle optional verwendet werden.<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,...*n*]): Die Sortierreihenfolge der Daten in der Datendatei. Die Leistung des Massenkopierens wird verbessert, wenn die zu ladende Datendatei entsprechend dem gruppierten Index der Tabelle sortiert ist.<br /><br /> **ROWS_PER_BATCH** = *bb*: Die Anzahl von Datenzeilen pro Batch (als *bb*). Der Server optimiert das Massenladen entsprechend dem Wert von *bb*. Standardmäßig ist **ROWS_PER_BATCH** unbekannt.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: Die Anzahl der Kilobytes (KB) an Daten pro Batch (als cc). Standardmäßig ist **KILOBYTES_PER_BATCH** unbekannt.<br /><br /> **TABLOCK**: Eine Sperre auf Tabellenebene wird für die Dauer des Massenkopiervorgangs abgerufen. Diese Option verbessert die Leistung beträchtlich, da weniger Sperrkonflikte für die Tabelle auftreten, wenn diese nur während des Massenkopiervorgangs gesperrt wird. Eine Tabelle kann gleichzeitig von mehreren Clients geladen werden, wenn die Tabelle keine Indizes aufweist und **TABLOCK** angegeben ist. Standardmäßig wird das Sperrverhalten durch die Tabellenoption **table lock on bulk load** bestimmt.<br /><br /> **CHECK_CONSTRAINTS**: Alle Einschränkungen für *Table_name* werden während des Massenkopiervorgangs überprüft. Standardmäßig werden Einschränkungen ignoriert.<br /><br /> **FIRE_TRIGGER**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet die Zeilenversionsverwaltung für Trigger und speichert die Zeilenversionen im Versionsspeicher in **tempdb**. Deshalb sind Massenprotokollierungsoptimierungen verfügbar, auch wenn Trigger aktiviert sind. Bevor Sie einen Massenimport eines Batches mit einer großen Anzahl von Zeilen vornehmen, für die Trigger aktiviert sind, müssen Sie gegebenenfalls die Größe von **tempdb** erweitern.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Verwenden von dateibasierten Massenkopiervorgängen  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert die **IBCPSession** Unterstützung für COM verfügbar gemacht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dateibasierte Massenkopiervorgänge. Die **IBCPSession**-Schnittstelle implementiert die Methoden [IBCPSession::BCPColFmt](../../native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) und [IBCPSession::BCPWriteFmt](../../native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt Massenkopiervorgänge in derselben Weise wie in Vorgängerversionen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des ODBC-Treibers. Informationen über Massenkopiervorgänge mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber finden Sie unter [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)   
 [Datenquelleneigenschaften &#40;OLE DB&#41;](../../native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Massenimport und -export von Daten &#40;SQL Server&#41;](../../import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Optimieren der Leistung des Massenimports](https://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  
  
  
