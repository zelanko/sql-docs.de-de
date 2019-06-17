---
title: Löschen eines SQL Server-Index | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eadcd1de5bfc3eea254bb134b963c2b4be094eaa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63283777"
---
# <a name="dropping-a-sql-server-index"></a>Löschen eines SQL Server-Index
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **Iindexdefinition** Funktion. Mit dieser Funktion können Consumer einen Index aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle entfernen.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt einige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PRIMARY KEY- und UNIQUE-Einschränkungen als Indizes. Der Tabellenbesitzer, der Datenbankbesitzer sowie bestimmte Inhaber von Administrationsfunktionen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellen bearbeiten und Einschränkungen löschen. Standardmäßig kann nur der Tabellenbesitzer einen vorhandenen Index löschen. Aus diesem Grund hängt es nicht nur von den Zugriffsrechten des Anwendungsbenutzers, sondern auch von der Art des angegebenen Indexes ab, ob **DropIndex** erfolgreich verläuft oder fehlschlägt.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Consumer geben den Indexnamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pIndexID*-Parameters ein. Das *eKind*-Element von *pIndexID* muss DBKIND_NAME sein. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt nicht die OLE DB-Funktion von löschen Sie alle Indizes für eine Tabelle beim *pIndexID* ist null. Wenn *pIndexID* NULL ist, wird E_INVALIDARG zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
