---
title: Löschen eines SQL Server Indexes | Microsoft-Dokumentation
description: Löschen eines SQL Server-Indexes mithilfe OLE DB Treibers für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 708deecefe451115ca0fca97075f88311dec2f5a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015253"
---
# <a name="dropping-a-sql-server-index"></a>Löschen eines SQL Server-Index
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die **IIndexDefinition::D ropindex** -Funktion verfügbar. Mit dieser Funktion können Consumer einen Index aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle entfernen.  
  
 Der OLE DB-Treiber für SQL Server macht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einige PRIMARY KEY-und UNIQUE-Einschränkungen als Indizes verfügbar. Der Tabellenbesitzer, der Datenbankbesitzer sowie bestimmte Inhaber von Administrationsfunktionen können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabellen bearbeiten und Einschränkungen löschen. Standardmäßig kann nur der Tabellenbesitzer einen vorhandenen Index löschen. Aus diesem Grund hängt es nicht nur von den Zugriffsrechten des Anwendungsbenutzers, sondern auch von der Art des angegebenen Indexes ab, ob **DropIndex** erfolgreich verläuft oder fehlschlägt.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Consumer geben den Indexnamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pIndexID*-Parameters ein. Das *eKind*-Element von *pIndexID* muss DBKIND_NAME sein. Der OLE DB-Treiber für SQL Server unterstützt nicht das OLE DB-Feature, mit dem alle Indizes einer Tabelle gelöscht werden, wenn *pIndexID* NULL ist. Wenn *pIndexID* NULL ist, wird E_INVALIDARG zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
