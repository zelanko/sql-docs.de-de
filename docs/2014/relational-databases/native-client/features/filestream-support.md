---
title: FILESTREAM-Unterstützung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33e447048f7058ee81b0b144f0aa94a370f6d670
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046262"
---
# <a name="filestream-support"></a>FILESTREAM-Unterstützung
  Die FILESTREAM-Funktion bietet eine Möglichkeit, große binäre Werte zu speichern und entweder über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder durch direkten Zugriff auf das Windows-Dateisystem darauf zuzugreifen. Ein großer Binärwert ist ein Wert, der größer als 2 Gigabyte (GB) ist. Weitere Informationen zur verbesserten FILESTREAM-Unterstützung finden Sie unter [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).  
  
 Wenn eine Datenbankverbindung geöffnet wird, wird `@@TEXTSIZE` standardmäßig auf -1 ("unbegrenzt") festgelegt.  
  
 Es ist auch möglich, mit Windows-Dateisystem-APIs auf FILESTREAM-Spalten zuzugreifen und diese zu aktualisieren.  
  
 Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [FILESTREAM-Unterstützung &#40;OLE DB&#41;](../ole-db/filestream-support-ole-db.md)  
  
-   [FILESTREAM-Unterstützung &#40;ODBC-&#41;](../odbc/filestream-support-odbc.md)  
  
-   [ZUgreifen auf FILESTREAM-Daten mit OpenSqlFilestream](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Abfragen von FILESTREAM-Spalten  
 Schemarowsets in OLE DB geben nicht an, ob eine Spalte eine FILESTREAM-Spalte ist. ITableDefinition in OLE DB kann nicht verwendet werden, um eine FILESTREAM-Spalte zu erstellen.  
  
 Katalog Funktionen wie SQLColumns in ODBC melden nicht, ob eine Spalte eine FILESTREAM-Spalte ist.  
  
 Zum Erstellen von FILESTREAM-Spalten oder zum erkennen, welche vorhandenen Spalten FILESTREAM-Spalten sind, `is_filestream` können Sie die-Spalte der [sys. Columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) -Katalog Sicht verwenden.  
  
 Es folgt ein Beispiel:  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Kompabilität mit früheren Versionen  
 Wenn der Client mit der Version von Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kompiliert wurde, die im [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)]Lieferumfang `varbinary(max)` von enthalten war, wird [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]das Verhalten mit kompatibel sein. Das heißt, die Maximalgröße der zurückgegebenen Daten ist auf 2 GB beschränkt. Ergebniswerte, die größer als 2 GB sind, werden abgeschnitten, und es wird die Warnung „Zeichenfolgendaten werden rechts abgeschnitten“ zurückgegeben.  
  
 Wenn Datentypkompatibilität auf 80 festgelegt wird, ist das Clientverhalten mit dem Verhalten von Clients früherer Versionen konsistent.  
  
 Für Clients, die SQLOLEDB oder andere Anbieter verwenden, die vor dem [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client frei `varbinary(max)` gegeben wurden, wird Image zugeordnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)  
  
  
