---
title: Löschen eines SQL Server-Index | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 148565f2866e571ba783c58d1ff10413510ef6db
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422229"
---
# <a name="dropping-a-sql-server-index"></a>Löschen eines SQL Server-Index
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **Iindexdefinition** Funktion. Dieser Funktion können Consumer zum Löschen eines Index aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt einige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PRIMARY KEY- und UNIQUE-Einschränkungen als Indizes. Der Tabellenbesitzer, Datenbankbesitzer und einige Mitglieder der Administratorrolle können ändern, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle Löschen einer Einschränkung. Standardmäßig kann nur der Tabellenbesitzer einen vorhandenen Index löschen. Aus diesem Grund **DropIndex** Erfolg oder Misserfolg hängt nicht nur von Zugriffsrechte des Anwendungsbenutzers, sondern auch für den Typ des angegebenen Index ab.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in die *PwszName* Mitglied der *uName* -Vereinigung der *pTableID* Parameter. Die *eKind* Mitglied *pTableID* muss DBKIND_NAME sein.  
  
 Consumer geben den Indexnamen als Unicode-Zeichenfolge in die *PwszName* Mitglied der *uName* -Vereinigung der *pIndexID* Parameter. Die *eKind* Mitglied *pIndexID* muss DBKIND_NAME sein. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt nicht die OLE DB-Funktion von löschen Sie alle Indizes für eine Tabelle beim *pIndexID* ist null. Wenn *pIndexID* ist null, wird E_INVALIDARG zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
