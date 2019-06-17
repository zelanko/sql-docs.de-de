---
title: Verwenden von Autofetch mit ODBC-Cursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7959068d5e24aa38157525ec133ab071611b5e85
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013641"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Verwenden von Autofetch mit ODBC-Cursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Autofetch-Option aus, wenn Server-Cursortyp zu verwenden. Mit automatischer Abrufoption die **SQLExecute** oder **SQLExecDirect** -Funktion, die den Cursor öffnen verfügt auch über einen impliziten [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)-Funktion (SQL_FIRST). Die Zeilen des ersten Rowsets werden während der Ausführung der Anweisung an die gebundenen Anwendungsvariablen zurückgegeben, wodurch ein weiterer Roundtrip über das Netzwerk bis zum Server vermieden wird. [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt, wenn die automatische Abrufoption aktiviert ist, müssen die Resultsetspalten an Programmvariablen gebunden sein.  
  
 Autofetch wird von Anwendungen angefordert, wenn für das treiberspezifische SQL_SOPT_SS_CURSOR_OPTIONS-Anweisungsattribut SQL_CO_AF festgelegt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zur Programmierung von Cursor &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
