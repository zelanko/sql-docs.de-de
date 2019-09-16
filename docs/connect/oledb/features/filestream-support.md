---
title: FILESTREAM-Unterstützung | Microsoft-Dokumentation
description: FILESTREAM-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 09/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a548cfda44d40ba7ac37aaf4465c589c7256ffe7
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978061"
---
# <a name="filestream-support"></a>FILESTREAM-Unterstützung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]Ab unterstützt OLE DB Treiber für SQL Server die erweiterte FILESTREAM-Funktion. Beispiele finden Sie unter [FileStream und OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

Die FILESTREAM-Funktion bietet eine Möglichkeit, große binäre Werte zu speichern und entweder über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder durch direkten Zugriff auf das Windows-Dateisystem darauf zuzugreifen. Ein großer Binärwert ist ein Wert, der größer als 2 Gigabyte (GB) ist. Weitere Informationen zur verbesserten FILESTREAM-Unterstützung finden Sie unter [FileStream &#40;-SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
Wenn eine Datenbankverbindung geöffnet wird, wird **@@TEXTSIZE** standardmäßig auf -1 („unbegrenzt“) festgelegt.  
  
Es ist auch möglich, mit Windows-Dateisystem-APIs auf FILESTREAM-Spalten zuzugreifen und diese zu aktualisieren.  
  
Weitere Informationen finden Sie unter [Zugreifen auf FILESTREAM-Daten mit OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md).  
  
## <a name="querying-for-filestream-columns"></a>Abfragen von FILESTREAM-Spalten  
Schemarowsets in OLE DB geben nicht an, ob eine Spalte eine FILESTREAM-Spalte ist. ITableDefinition in OLE DB kann nicht verwendet werden, um eine FILESTREAM-Spalte zu erstellen.    
  
Mithilfe der **is_filestream**-Spalte der [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)-Katalogsicht können Sie FILESTREAM-Spalten erstellen oder ermitteln, welche der vorhandenen Spalten FILESTREAM-Spalten sind.  
  
Es folgt ein Beispiel:  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Kompabilität mit früheren Versionen  
Wenn der Client für SQL Server mit OLE DB Treiber kompiliert wurde und die Anwendung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Verbindung mit ( [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]) herstellt, ist das **varbinary (max)** -Verhalten mit dem durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eingeführten Verhalten kompatibel. Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Das heißt, die Maximalgröße der zurückgegebenen Daten ist auf 2 GB beschränkt. Ergebniswerte, die größer als 2 GB sind, werden abgeschnitten, und es wird die Warnung „Zeichenfolgendaten werden rechts abgeschnitten“ zurückgegeben. 
  
Wenn Datentypkompatibilität auf 80 festgelegt wird, ist das Clientverhalten mit dem Verhalten von Clients früherer Versionen konsistent.  
  
Bei Clients, die SQLOLEDB oder andere Anbieter verwenden, die vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] veröffentlicht wurden, wird **varbinary(max)** dem Datentyp „image“ zugeordnet.  
  
## <a name="comments"></a>Kommentare
- Zum Senden und empfangen von **varbinary (max)** -Werten, die größer als 2 GB sind, verwendet eine Anwendung **DBTYPE_IUNKNOWN** in Parameter-und Ergebnis Bindungen. Für Parameter muss der Anbieter IUnknown:: QueryInterface für ISequentialStream und für Ergebnisse, die ISequentialStream zurückgeben, aufruft.  

-  Bei OLE DB wird die Überprüfung auf ISequentialStream-Werte gelockert. Wenn *wType* in der **DBBINDING** -Struktur **DBTYPE_IUNKNOWN** ist, kann die Längen Überprüfung entweder durch Weglassen von **DBPART_LENGTH** von *dwPart* oder durch Festlegen der Länge der Daten (bei Offset- *obLength* in den Daten) deaktiviert werden. Buffer) bis ~ 0. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  Diese Änderung wirkt sich auf alle Schnittstellen aus, die Daten übertragen, hauptsächlich IRowset:: GetData, ICommand:: Execute und IRowsetFastLoad:: InsertRow.
 

## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
