---
title: Vorbereitete Ausführung | Microsoft Docs
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
ms.openlocfilehash: 8265ed80028d5d8ac9696853a29474552f401f3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297918"
---
# <a name="prepared-execution"></a>Vorbereitete Ausführung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die ODBC-API definiert eine vorbereitete Ausführung als einen Weg, den Analyse- und Kompilieraufwand, der mit dem wiederholten Ausführen einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung einhergeht, zu reduzieren. Die Anwendung erstellt eine Zeichenfolge, die eine SQL-Anweisung enthält, und führt diese Anweisung dann in zwei Phasen aus. Es ruft [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) einmal auf, damit die Anweisung analysiert [!INCLUDE[ssDE](../../../includes/ssde-md.md)]und in einen Ausführungsplan von der kompiliert wird. Anschließend wird **SQLExecute** für jede Ausführung des vorbereiteten Ausführungsplans auf. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Bei den meisten Datenbanken ist die vorbereitete Ausführung schneller als eine direkte Ausführung von Anweisungen, die mehr als drei- oder viermal ausgeführt werden, hauptsächlich da die Anweisung nur einmal kompiliert wird, während die direkt ausgeführten Anweisungen bei jeder Ausführung kompiliert werden. Die vorbereitete Ausführung kann auch zu einer Reduzierung des Netzwerkverkehrs beitragen, da der Treiber bei jeder Ausführung der Anweisung eine Ausführungsplan-ID und die Parameterwerte an die Datenquelle senden kann, anstatt die gesamte SQL-Anweisung zu senden.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]reduziert den Leistungsunterschied zwischen direkter und vorbereiteter Ausführung durch verbesserte Algorithmen zum Erkennen und Wiederverwenden von Ausführungsplänen von **SQLExecDirect**. Dadurch stehen einige der Leistungsvorteile einer vorbereiteten Ausführung auch für direkt ausgeführte Anweisungen zur Verfügung. Weitere Informationen finden Sie unter [Direkte Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt außerdem auch eine systemeigene Unterstützung für die vorbereitete Ausführung bereit. Ein Ausführungsplan wird auf **SQLPrepare** erstellt und später ausgeführt, wenn **SQLExecute** aufgerufen wird. Da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zum Erstellen temporärer gespeicherter Prozeduren in **SQLPrepare**nicht erforderlich ist, gibt es für die Systemtabellen in **tempdb**keinen zusätzlichen Overhead.  
  
 Aus Leistungsgründen wird die Anweisungsvorbereitung verschoben, bis **SQLExecute** aufgerufen wird oder ein Metaproperty-Vorgang (z. B. [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) oder [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) in ODBC) ausgeführt wird. Dies ist das Standardverhalten. Fehler in der vorbereiteten Anweisung werden erst dann erkannt, wenn die Anweisung ausgeführt oder ein Metaeigenschaftsvorgang durchgeführt wird. Wenn Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-treiberspezifische Anweisungsattribut SQL_SOPT_SS_DEFER_PREPARE auf SQL_DP_OFF setzen, kann dieses Standardverhalten deaktiviert werden.  
  
 Bei verzögerter Vorbereitung generiert der Aufruf von **SQLDescribeCol** oder **SQLDescribeParam** vor dem Aufruf von **SQLExecute** einen zusätzlichen Roundtrip zum Server. Auf **SQLDescribeCol**entfernt der Treiber die WHERE-Klausel aus der Abfrage und sendet sie an den Server mit SET FMTONLY ON, um die Beschreibung der Spalten im ersten Resultset abzurufen, die von der Abfrage zurückgegeben werden. In **SQLDescribeParam**ruft der Treiber den Server auf, um eine Beschreibung der Ausdrücke oder Spalten abzurufen, auf die von Parametermarkierungen in der Abfrage verwiesen wird. Bei dieser Methode kommt es auch zu einigen Einschränkungen, z. B. können keine Parameter in Unterabfragen gelöst werden.  
  
 Die übermäßige Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **SQLPrepare** mit dem nativen Client-ODBC-Treiber beeinträchtigt die Leistung, insbesondere wenn eine Verbindung mit früheren Versionen von SQL Server hergestellt wird. Die vorbereitete Ausführung sollte nicht für Anwendungen verwendet werden, die nur einmal ausgeführt werden. Die vorbereitete Ausführung dauert länger als eine direkte Ausführung für eine einzelne Ausführung einer Anweisung, da ein zusätzlicher Netzwerkroundtrip vom Client zum Server erforderlich ist. Auf früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird auch eine temporär gespeicherte Prozedur erstellt.  
  
 Vorbereitete Anweisungen können nicht zum Erstellen von temporären Objekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden.  
  
 Einige frühe ODBC-Anwendungen verwendeten **SQLPrepare** jedes Mal, wenn [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) verwendet wurde. **SQLBindParameter** erfordert nicht die Verwendung von **SQLPrepare**, es kann mit **SQLExecDirect**verwendet werden. Verwenden Sie beispielsweise **SQLExecDirect** mit **SQLBindParameter,** um den Rückgabecode oder die Ausgabeparameter aus einer gespeicherten Prozedur abzurufen, die nur einmal ausgeführt wird. Verwenden Sie **SQLPrepare** nicht mit **SQLBindParameter,** es sei denn, dieselbe Anweisung wird mehrmals ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
