---
title: Ausführen von Anweisungen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3489c26073da15fb41af6d1560cb48fe38897386
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297935"
---
# <a name="executing-statements-odbc"></a>Ausführen von Anweisungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native Client-ODBC-Treiber bietet eine Vielzahl [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von Möglichkeiten zum Ausführen von SQL-Anweisungen in einer Datenbank:  
  
-   Direkte Ausführung  
  
-   Vorbereitete Ausführung  
  
 Die direkte Ausführung umfasst das [!INCLUDE[tsql](../../../includes/tsql-md.md)] Erstellen einer Zeichenfolge, die eine Anweisung enthält, und das Übermitteln zur Ausführung mithilfe der **SQLExecDirect-Funktion.** Die vorbereitete Ausführung erfordert die Bildung einer Zeichenfolge, die eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung enthält, und die Ausführung dieser Anweisung in zwei Phasen. Die erste Phase verwendet die [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) Function-Funktion, um den [!INCLUDE[ssDE](../../../includes/ssde-md.md)]Ausführungsplan für die Anweisung im zu analysieren und zu kompilieren. Die zweite Phase verwendet die **SQLExecute-Funktion,** um den zuvor vorbereiteten Ausführungsplan auszuführen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Sowohl bei der direkten als auch bei der vorbereiteten Ausführung können einzelne [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen oder Batches von SQL-Anweisungen ausgeführt oder gespeicherte Prozeduren aufgerufen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Direkte Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Vorbereitete Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Prozeduren](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Batches von Anweisungen](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Effekte von ISO-Optionen](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
