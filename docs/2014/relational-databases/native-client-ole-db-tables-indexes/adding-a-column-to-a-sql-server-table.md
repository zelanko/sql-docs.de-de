---
title: Hinzufügen einer Spalte zu einer SQL Server Tabelle | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046495"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Hinzufügen einer Spalte zu einer SQL Server-Tabelle
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **ITableDefinition:: AddColumn** -Funktion zur Verfügung. Mit dieser Funktion können Consumer einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle eine Spalte hinzufügen.  
  
 Wenn Sie einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle eine Spalte hinzufügen, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Consumer des Native Client OLE DB-Anbieters wie folgt eingeschränkt:  
  
-   Wenn DBPROP_COL_AUTOINCREMENT VARIANT_TRUE ist, muss DBPROP_COL_NULLABLE VARIANT_FALSE sein.  
  
-   Wenn die Spalte mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**-Datentyp definiert wird, muss DBPROP_COL_NULLABLE auf VARIANT_FALSE festgelegt sein.  
  
-   Für alle anderen Spaltendefinitionen muss DBPROP_COL_NULLABLE  VARIANT_TRUE sein.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das Element *pwszName* der Vereinigung *uName* des Parameters *pTableID* ein. Das Element *eKind* von *pTableID* muss DBKIND_NAME sein.  
  
 Der neue Spaltenname wird als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *dbcid*-Elements des DBCOLUMNDESC-Parameters *pColumnDesc* angegeben. Das *eKind*-Element muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
