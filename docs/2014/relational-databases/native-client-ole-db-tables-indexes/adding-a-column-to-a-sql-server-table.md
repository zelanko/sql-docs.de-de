---
title: Hinzufügen einer Spalte zu einer SQL Server-Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32e78feae791788e0aad87079546ea8c7d49e734
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214240"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Hinzufügen einer Spalte zu einer SQL Server-Tabelle
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **addColumn** Funktion. Mit dieser Funktion können Consumer einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle eine Spalte hinzufügen.  
  
 Beim Hinzufügen einer Spalteninhalts in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer der Native Client OLE DB-Anbieter wird wie folgt eingeschränkt:  
  
-   Wenn DBPROP_COL_AUTOINCREMENT VARIANT_TRUE ist, muss DBPROP_COL_NULLABLE VARIANT_FALSE sein.  
  
-   Wenn die Spalte mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**-Datentyp definiert wird, muss DBPROP_COL_NULLABLE auf VARIANT_FALSE festgelegt sein.  
  
-   Für alle anderen Spaltendefinitionen muss DBPROP_COL_NULLABLE  VARIANT_TRUE sein.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der neue Spaltenname wird als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *dbcid*-Elements des DBCOLUMNDESC-Parameters *pColumnDesc* angegeben. Das *eKind*-Element muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
