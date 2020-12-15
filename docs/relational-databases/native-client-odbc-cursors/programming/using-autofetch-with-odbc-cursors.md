---
description: Verwenden von Autofetch mit ODBC-Cursorn
title: Verwenden von Autofetch mit ODBC-Cursorn | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: abb1bb038273bfd2d1e9e4bdd2d6f130285361e1
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473741"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Verwenden von Autofetch mit ODBC-Cursorn
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Wenn eine Verbindung mit einer Instanz von besteht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt der Native Client ODBC-Treiber bei Verwendung eines beliebigen Server Cursor Typs eine Autofetch-Option. Mit Autofetch verfügt die **SQLExecute** -oder **SQLExecDirect** -Funktion, die den Cursor öffnet, auch über eine implizite [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST)-Funktion. Die Zeilen des ersten Rowsets werden während der Ausführung der Anweisung an die gebundenen Anwendungsvariablen zurückgegeben, wodurch ein weiterer Roundtrip über das Netzwerk bis zum Server vermieden wird. [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt, wenn die Autofetch-Option aktiviert ist. die Resultsetspalten müssen an Programmvariablen gebunden werden.  
  
 Autofetch wird von Anwendungen angefordert, wenn für das treiberspezifische SQL_SOPT_SS_CURSOR_OPTIONS-Anweisungsattribut SQL_CO_AF festgelegt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur Cursor Programmierung &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
