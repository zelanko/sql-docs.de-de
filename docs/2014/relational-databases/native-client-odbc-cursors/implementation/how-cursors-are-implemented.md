---
title: Implementieren von Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80b3df4fd3b4e6e515de68b8e5f1a7af034bdb42
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423049"
---
# <a name="how-cursors-are-implemented"></a>Implementieren von Cursorn
  ODBC-Anwendungen steuern das Cursorverhalten, indem mindestens ein Anweisungsattribut festgelegt wird, bevor eine SQL-Anweisung ausgeführt wird. ODBC bietet zwei verschiedene Möglichkeiten, die Merkmale eines Cursors anzugeben:  
  
-   Cursortyp  
  
     Cursortypen werden festgelegt, mit dem SQL_ATTR_CURSOR_TYPE-Attribut des [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md). Die ODBC-Cursortypen sind vorwärts, statisch, keysetgesteuert, gemischt und dynamisch. Durch Festlegen des Cursortyps wurden Cursor in ODBC ursprünglich angegeben.  
  
-   Cursorverhalten  
  
     Das Verhalten für Standardcursor festgelegt ist, mithilfe der Attribute SQL_ATTR_CURSOR_SCROLLABLE und SQL_ATTR_CURSOR_SENSITIVITY des **SQLSetStmtAttr**. Diese Attribute werden anhand der Schlüsselwörter SCROLL und SENSITIVE modelliert, die für die DECLARE CURSOR-Anweisung in ISO-Standards definiert wurde. Diese beiden ISO-Optionen wurden in ODBC Version 3.0 eingeführt.  
  
 Die Merkmale eines ODBC-Cursors sollten mit einer der beiden Methoden angegeben werden, wobei die ODBC-Cursortypen vorzuziehen sind.  
  
 Neben dem Cursortyp legen ODBC-Anwendungen noch andere Optionen fest, z. B. die Anzahl der bei jedem Abruf zurückgegebenen Zeilen, Parallelitätsoptionen und Transaktionsisolationsstufen. Diese Optionen können entweder für ODBC-Cursor (vorwärts, statisch, keysetgesteuert, gemischt und dynamisch) oder ISO-Cursor (Bildlauffähigkeit und Sensitivität) festgelegt werden.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt mehrere Möglichkeiten, die die verschiedenen Cursortypen physisch zu implementieren. Der Treiber implementiert einige Cursortypen mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standardresultset und andere als Servercursor oder mit der ODBC-Cursorbibliothek.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von SQL Server-Standardresultsets](using-sql-server-default-result-sets.md)  
  
-   [Verwenden von Servercursorn](using-server-cursors.md)  
  
-   [ODBC-Cursorbibliothek](odbc-cursor-library.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Cursorn &#40;ODBC&#41;](../using-cursors-odbc.md)  
  
  
