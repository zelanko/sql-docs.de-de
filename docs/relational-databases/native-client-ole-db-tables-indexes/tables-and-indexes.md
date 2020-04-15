---
title: Tabellen und Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 83757abfc78b5ffbee7a46a9f7c49c89daae7118
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305626"
---
# <a name="tables-and-indexes"></a>Tabellen und Indizes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter macht die **Schnittstellen IIndexDefinition** und **ITableDefinition** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar, sodass Verbraucher Tabellen und Indizes erstellen, ändern und löschen können. Gültige Tabellen- und Indexdefinitionen hängen von der Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab.  
  
 Die Möglichkeit, Tabellen und Indizes zu erstellen oder zu löschen, hängt von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zugriffsrechten des Benutzers der Consumeranwendung ab. Das Löschen einer Tabelle kann durch das Vorhandensein von Beschränkungen der deklarativen referenziellen Integrität oder anderer Faktoren weiter eingeschränkt sein.  
  
 Die meisten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anwendungen, die auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL-DMO anstelle dieser nativen Client-OLE-DB-Anbieterschnittstellen abzielen, verwenden SQL-DMO. SQL-DMO steht für eine Auflistung von OLE-Automatisierungsobjekten, die alle administrativen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen. Anwendungen, die auf mehrere OLE DB-Anbieter ausgerichtet sind, verwenden diese generischen OLE DB-Schnittstellen, die von den verschiedenen OLE DB-Anbietern unterstützt werden.  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERCOLUMN definiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die folgende Eigenschaft.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Typ: VT_BSTR<br /><br /> R/W: Schreiben<br /><br /> Default: NULL<br /><br /> Beschreibung: Diese Eigenschaft wird nur in **ITableDefinition** verwendet. Die in dieser Eigenschaft angegebene Zeichenfolge wird beim Erstellen einer [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)-Anweisung verwendet.<br /><br /> verwendet.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen von SQL Server-Tabellen](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Hinzufügen einer Spalte zu einer SQL Server-Tabelle](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Entfernen einer Spalte aus einer SQL Server-Tabelle](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Löschen einer SQL Server-Tabelle](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Erstellen von SQL Server-Indizes](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [Löschen eines SQL Server-Index](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
