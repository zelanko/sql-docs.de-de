---
title: Ausführen von Anweisungen (ODBC) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: efd0b9ba46975512491dadccb5a44940af52ec28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73791023"
---
# <a name="executing-statements-odbc"></a>Ausführen von Anweisungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber bietet eine Vielzahl von Möglichkeiten zum Ausführen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL-Anweisungen in einer Datenbank:  
  
-   Direkte Ausführung  
  
-   Vorbereitete Ausführung  
  
 Die direkte Ausführung umfasst die Verwendung einer Zeichenfolge [!INCLUDE[tsql](../../../includes/tsql-md.md)] , die eine-Anweisung enthält, und die Übermittlung mit der **SQLExecDirect** -Funktion zur Ausführung. Die vorbereitete Ausführung erfordert die Bildung einer Zeichenfolge, die eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung enthält, und die Ausführung dieser Anweisung in zwei Phasen. In der ersten Phase wird die [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) verwendet, um den Ausführungsplan für die Anweisung im zu analysieren [!INCLUDE[ssDE](../../../includes/ssde-md.md)]und zu kompilieren. In der zweiten Phase wird die **SQLExecute** -Funktion verwendet, um den zuvor vorbereiteten Ausführungsplan auszuführen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Sowohl bei der direkten als auch bei der vorbereiteten Ausführung können einzelne [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen oder Batches von SQL-Anweisungen ausgeführt oder gespeicherte Prozeduren aufgerufen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Direkte Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Vorbereitete Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Prozeduren](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Batches von Anweisungen](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Effekte von ISO-Optionen](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
