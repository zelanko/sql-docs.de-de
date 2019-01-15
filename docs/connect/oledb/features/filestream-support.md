---
title: FILESTREAM-Unterstützung | Microsoft-Dokumentation
description: FILESTREAM-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
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
manager: craigg
ms.openlocfilehash: afc794e19ecc93f7275427760df78004a0f1fb13
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53211549"
---
# <a name="filestream-support"></a>FILESTREAM-Unterstützung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Beginnend mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], OLE DB-Treiber für SQL Server unterstützt die verbesserte FILESTREAM-Funktion. Beispiele finden Sie [Filestream und OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

Die FILESTREAM-Funktion bietet eine Möglichkeit, große binäre Werte zu speichern und entweder über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder durch direkten Zugriff auf das Windows-Dateisystem darauf zuzugreifen. Ein großer Binärwert ist ein Wert, der größer als 2 Gigabyte (GB) ist. Weitere Informationen über die verbesserte FILESTREAM-Unterstützung finden Sie unter [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
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
Wenn Ihr Client kompiliert wurde, mithilfe von OLE DB-Treiber für SQL Server und die Anwendung eine Verbindung, um herstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] über [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), klicken Sie dann **'varbinary(max)'** Verhalten wird mit dem Verhalten kompatibel sein von eingeführte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Das heißt, die Maximalgröße der zurückgegebenen Daten ist auf 2 GB beschränkt. Ergebniswerte, die größer als 2 GB sind, werden abgeschnitten, und es wird die Warnung „Zeichenfolgendaten werden rechts abgeschnitten“ zurückgegeben. 
  
Wenn Datentypkompatibilität auf 80 festgelegt wird, ist das Clientverhalten mit dem Verhalten von Clients früherer Versionen konsistent.  
  
Bei Clients, die SQLOLEDB oder andere Anbieter verwenden, die vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] veröffentlicht wurden, wird **varbinary(max)** dem Datentyp „image“ zugeordnet.  
  
## <a name="comments"></a>Kommentare
- Zum Senden und Empfangen von **'varbinary(max)'** Werte, die größer als 2 GB sind, eine Anwendung verwendet **DBTYPE_IUNKNOWN** in Parameter- und ergebnisbindungen. Für Parameter muss der Anbieter IUnknown:: QueryInterface aufrufen, einer ISequentialStream-Schnittstelle und für Ergebnisse, die einer ISequentialStream-Schnittstelle zurückzugeben.  

-  Für OLE DB wird überprüfen im Zusammenhang mit ISequentialStream-Werte erhöht. Wenn *wType* ist **DBTYPE_IUNKNOWN** in die **DBBINDING** Struktur längenüberprüfung möglich deaktiviert, entweder durch Auslassen **DBPART_LENGTH** von *DwPart* oder durch Festlegen der Länge der Daten (bei Offset *ObLength* im Datenpuffer) auf ~ 0. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  Diese Änderung wirkt sich auf alle Schnittstellen, die Daten, die hauptsächlich IRowset:: GetData ICommand:: Execute und IRowsetFastLoad:: InsertRow übertragen.
 

## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
