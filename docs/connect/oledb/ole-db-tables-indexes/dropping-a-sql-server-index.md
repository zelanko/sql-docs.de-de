---
title: Löschen eines SQL Server-Index | Microsoft-Dokumentation
description: Löschen eines Sql Server-Index mithilfe von OLE DB-Treiber für SQL Server
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
manager: jroth
ms.openlocfilehash: a426352059f0ca400091aec14589742ec592ea97
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801280"
---
# <a name="dropping-a-sql-server-index"></a>Löschen eines SQL Server-Index
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die **Iindexdefinition** Funktion. Mit dieser Funktion können Consumer einen Index aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle entfernen.  
  
 Der OLE DB-Treiber für SQL Server stellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PRIMARY KEY- und UNIQUE-Einschränkungen als Indizes. Der Tabellenbesitzer, der Datenbankbesitzer sowie bestimmte Inhaber von Administrationsfunktionen können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabellen bearbeiten und Einschränkungen löschen. Standardmäßig kann nur der Tabellenbesitzer einen vorhandenen Index löschen. Aus diesem Grund hängt es nicht nur von den Zugriffsrechten des Anwendungsbenutzers, sondern auch von der Art des angegebenen Indexes ab, ob **DropIndex** erfolgreich verläuft oder fehlschlägt.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Consumer geben den Indexnamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pIndexID*-Parameters ein. Das *eKind*-Element von *pIndexID* muss DBKIND_NAME sein. Der OLE DB-Treiber für SQL Server unterstützt nicht das OLE DB-Feature, mit dem alle Indizes einer Tabelle gelöscht werden, wenn *pIndexID* NULL ist. Wenn *pIndexID* NULL ist, wird E_INVALIDARG zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
