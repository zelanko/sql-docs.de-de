---
title: Vorbereitete Ausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3067d20bd9beb0c1cb40e584a0932976be80946e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43066063"
---
# <a name="prepared-execution"></a>Vorbereitete Ausführung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Die ODBC-API definiert eine vorbereitete Ausführung als einen Weg, den Analyse- und Kompilieraufwand, der mit dem wiederholten Ausführen einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung einhergeht, zu reduzieren. Die Anwendung erstellt eine Zeichenfolge, die eine SQL-Anweisung enthält, und führt diese Anweisung dann in zwei Phasen aus. Ruft [SQLPrepare-Funktion](http://go.microsoft.com/fwlink/?LinkId=59360) einmal, um die Anweisung analysiert und kompiliert zu einem Ausführungsplan von den [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Es ruft dann **SQLExecute** für jede Ausführung des vorbereiteten Ausführungsplans. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Bei den meisten Datenbanken ist die vorbereitete Ausführung schneller als eine direkte Ausführung von Anweisungen, die mehr als drei- oder viermal ausgeführt werden, hauptsächlich da die Anweisung nur einmal kompiliert wird, während die direkt ausgeführten Anweisungen bei jeder Ausführung kompiliert werden. Die vorbereitete Ausführung kann auch zu einer Reduzierung des Netzwerkverkehrs beitragen, da der Treiber bei jeder Ausführung der Anweisung eine Ausführungsplan-ID und die Parameterwerte an die Datenquelle senden kann, anstatt die gesamte SQL-Anweisung zu senden.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] reduziert den Leistungsunterschied zwischen direkter und vorbereiteter Ausführung mithilfe verbesserter Algorithmen zur Erkennung und Wiederverwendung von Ausführungsplänen aus **SQLExecDirect**. Dadurch stehen einige der Leistungsvorteile einer vorbereiteten Ausführung auch für direkt ausgeführte Anweisungen zur Verfügung. Weitere Informationen finden Sie unter [direkte Ausführung](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt außerdem auch eine systemeigene Unterstützung für die vorbereitete Ausführung bereit. Ein Ausführungsplan basiert auf **SQLPrepare** und höher ausgeführt wird, wenn **SQLExecute** aufgerufen wird. Da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist nicht erforderlich, das Erstellen temporär gespeicherter Prozeduren auf **SQLPrepare**, es gibt kein zusätzlicher Aufwand für die Systemtabellen in **Tempdb**.  
  
 Aus Leistungsgründen wird die anweisungsvorbereitung verzögert, bis **SQLExecute** aufgerufen wird oder ein metaeigenschaftsvorgang (z. B. [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) oder [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)in ODBC) ausgeführt wird. Dies ist das Standardverhalten. Fehler in der vorbereiteten Anweisung werden erst dann erkannt, wenn die Anweisung ausgeführt oder ein Metaeigenschaftsvorgang durchgeführt wird. Wenn Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-treiberspezifische Anweisungsattribut SQL_SOPT_SS_DEFER_PREPARE auf SQL_DP_OFF setzen, kann dieses Standardverhalten deaktiviert werden.  
  
 Verzögertem vorbereiten wird durch das Aufrufen **SQLDescribeCol** oder **SQLDescribeParam** vor dem Aufruf **SQLExecute** ein zusätzlicher Roundtrip zum Server. Auf **SQLDescribeCol**, der Treiber die WHERE-Klausel entfernt, aus der Abfrage und sendet sie an den Server mit SET FMTONLY ON, um die Beschreibung der Spalten in das erste Resultset, das von der Abfrage zurückgegebenen zu erhalten. Auf **SQLDescribeParam**, ruft der Treiber den Server rufen Sie eine Beschreibung der Ausdrücke oder Spalten, die von einem Parametermarker in der Abfrage verwiesen wird. Bei dieser Methode kommt es auch zu einigen Einschränkungen, z. B. können keine Parameter in Unterabfragen gelöst werden.  
  
 Übermäßige Verwendung von **SQLPrepare** mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber beeinträchtigt die Leistung, insbesondere wenn die Verbindung zu älteren Versionen von SQL Server. Die vorbereitete Ausführung sollte nicht für Anwendungen verwendet werden, die nur einmal ausgeführt werden. Die vorbereitete Ausführung dauert länger als eine direkte Ausführung für eine einzelne Ausführung einer Anweisung, da ein zusätzlicher Netzwerkroundtrip vom Client zum Server erforderlich ist. Auf früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird auch eine temporär gespeicherte Prozedur erstellt.  
  
 Vorbereitete Anweisungen können nicht zum Erstellen von temporären Objekten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden.  
  
 Einige ältere ODBC-Anwendungen verwendet **SQLPrepare** jederzeit [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) verwendet wurde. **SQLBindParameter** erfordert nicht die Verwendung von **SQLPrepare**, er kann verwendet werden, mit **SQLExecDirect**. Verwenden Sie z. B. **SQLExecDirect** mit **SQLBindParameter** zum Abrufen des Rückgabecodes oder um Ausgabeparameter aus einer gespeicherten Prozedur, die nur einmal ausgeführt wird. Verwenden Sie keine **SQLPrepare** mit **SQLBindParameter** , wenn die gleiche Anweisung mehrmals ausgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Anweisungen &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
