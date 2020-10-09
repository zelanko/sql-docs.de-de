---
description: Vorbereitete Ausführung
title: Vorbereitete Ausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f1eb4580f3654b12f09b39e2fadf2167a9f9e561
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91869329"
---
# <a name="prepared-execution"></a>Vorbereitete Ausführung
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die ODBC-API definiert eine vorbereitete Ausführung als einen Weg, den Analyse- und Kompilieraufwand, der mit dem wiederholten Ausführen einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung einhergeht, zu reduzieren. Die Anwendung erstellt eine Zeichenfolge, die eine SQL-Anweisung enthält, und führt diese Anweisung dann in zwei Phasen aus. Sie ruft die [SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md) einmal auf, damit die-Anweisung vom analysiert und in einen Ausführungsplan kompiliert wird [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . Anschließend wird für jede Ausführung des vorbereiteten Ausführungs Plans **SQLExecute** aufgerufen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Bei den meisten Datenbanken ist die vorbereitete Ausführung schneller als eine direkte Ausführung von Anweisungen, die mehr als drei- oder viermal ausgeführt werden, hauptsächlich da die Anweisung nur einmal kompiliert wird, während die direkt ausgeführten Anweisungen bei jeder Ausführung kompiliert werden. Die vorbereitete Ausführung kann auch zu einer Reduzierung des Netzwerkverkehrs beitragen, da der Treiber bei jeder Ausführung der Anweisung eine Ausführungsplan-ID und die Parameterwerte an die Datenquelle senden kann, anstatt die gesamte SQL-Anweisung zu senden.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verringert den Leistungsunterschied zwischen direkter und vorbereiteter Ausführung durch verbesserte Algorithmen zum erkennen und wieder verwenden von Ausführungsplänen von **SQLExecDirect**. Dadurch stehen einige der Leistungsvorteile einer vorbereiteten Ausführung auch für direkt ausgeführte Anweisungen zur Verfügung. Weitere Informationen finden Sie unter [direkte Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt außerdem auch eine systemeigene Unterstützung für die vorbereitete Ausführung bereit. Ein Ausführungsplan wird auf **SQLPrepare** erstellt und später ausgeführt, wenn **SQLExecute** aufgerufen wird. Da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht zum Erstellen temporärer gespeicherter Prozeduren auf **SQLPrepare**erforderlich ist, wird in den Systemtabellen in **tempdb**kein zusätzlicher mehr Aufwand geboten.  
  
 Aus Leistungsgründen wird die Anweisungs Vorbereitung verzögert, bis **SQLExecute** aufgerufen wird oder ein Metaeigenschaftsvorgang (z. b. [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) oder [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) in ODBC) ausgeführt wird. Dies ist das Standardverhalten. Fehler in der vorbereiteten Anweisung werden erst dann erkannt, wenn die Anweisung ausgeführt oder ein Metaeigenschaftsvorgang durchgeführt wird. Wenn Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-treiberspezifische Anweisungsattribut SQL_SOPT_SS_DEFER_PREPARE auf SQL_DP_OFF setzen, kann dieses Standardverhalten deaktiviert werden.  
  
 Bei einer verzögerten Vorbereitung wird durch das Aufrufen von **SQLDescribeCol** oder **SQLDescribeParam** vor dem Aufrufen von **SQLExecute** ein zusätzlicher Roundtrip zum Server generiert. In **SQLDescribeCol**entfernt der Treiber die WHERE-Klausel aus der Abfrage und sendet Sie an den Server mit SET FMTONLY ON, um die Beschreibung der Spalten im ersten Resultset zu erhalten, das von der Abfrage zurückgegeben wird. In **SQLDescribeParam**ruft der Treiber den Server auf, um eine Beschreibung der Ausdrücke oder Spalten zu erhalten, auf die von beliebigen Parameter Markierungen in der Abfrage verwiesen wird. Bei dieser Methode kommt es auch zu einigen Einschränkungen, z. B. können keine Parameter in Unterabfragen gelöst werden.  
  
 Die übermäßige Verwendung von **SQLPrepare** mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber beeinträchtigt die Leistung, insbesondere, wenn eine Verbindung mit früheren Versionen von SQL Server besteht. Die vorbereitete Ausführung sollte nicht für Anwendungen verwendet werden, die nur einmal ausgeführt werden. Die vorbereitete Ausführung dauert länger als eine direkte Ausführung für eine einzelne Ausführung einer Anweisung, da ein zusätzlicher Netzwerkroundtrip vom Client zum Server erforderlich ist. Auf früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird auch eine temporär gespeicherte Prozedur erstellt.  
  
 Vorbereitete Anweisungen können nicht zum Erstellen von temporären Objekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden.  
  
 Einige frühe ODBC-Anwendungen haben **SQLPrepare** bei jeder Verwendung von [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) verwendet. **SQLBindParameter** erfordert nicht die Verwendung von **SQLPrepare**, sondern kann mit **SQLExecDirect**verwendet werden. Verwenden Sie z. b. **SQLExecDirect** mit **SQLBindParameter** , um den Rückgabecode oder die Ausgabeparameter aus einer gespeicherten Prozedur abzurufen, die nur einmal ausgeführt wird. Verwenden Sie **SQLPrepare** nicht mit **SQLBindParameter** , es sei denn, dieselbe Anweisung wird mehrmals ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
