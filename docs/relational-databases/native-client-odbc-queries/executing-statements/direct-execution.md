---
title: Direkte Ausführung | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a89888ac055e83ab38588646f2f9b38ecd6444d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297987"
---
# <a name="direct-execution"></a>Direkte Ausführung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die direkte Ausführung ist die grundlegendste Art und Weise, um eine Anweisung auszuführen. Eine Anwendung erstellt eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Zeichenfolge, die eine Anweisung enthält, und sendet sie zur Ausführung mit der **SQLExecDirect-Funktion.** Wenn die Anweisung beim Server eingeht, kompiliert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie zu einem Ausführungsplan, der unmittelbar ausgeführt wird.  
  
 Die direkte Ausführung wird im Allgemeinen von Anwendungen verwendet, die Anweisungen zur Laufzeit erstellen und ausführen. Es ist zugleich die effektivste Methode, Anweisungen, die nur einmal ausgeführt werden, auszuführen. Bei vielen Datenbanken muss jedoch die SQL-Anweisung bei jeder Ausführung analysiert und kompiliert werden, sodass ein zusätzlicher Aufwand entsteht, wenn die Anweisung mehrmals ausgeführt wird.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wurde die Leistung bei der direkten Ausführung von häufig ausgeführten Anweisungen in Mehrbenutzerumgebungen wesentlich verbessert. Durch den Einsatz von SQLExecDirect mit Parametermarkierungen für häufig ausgeführte SQL-Anweisungen wird zudem beinahe die gleiche Effizienz wie bei der vorbereiteten Ausführung erzielt.  
  
 Wenn eine Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einer Instanz von besteht, verwendet der native Client-ODBC-Treiber [sp_executesql,](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) um die sql-Anweisung oder den Inbatch zu übertragen, die in **SQLExecDirect**angegeben sind. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]hat Logik, um schnell zu bestimmen, ob eine SQL-Anweisung oder ein Batch, der mit **sp_executesql** ausgeführt wird, mit der Anweisung oder dem Batch übereinstimmt, die einen Ausführungsplan generiert haben, der bereits im Arbeitsspeicher vorhanden ist. Wenn eine Übereinstimmung gefunden wird, nutzt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den vorhandenen Plan, anstatt einen neuen Plan zu kompilieren. Dies bedeutet, dass häufig ausgeführte SQL-Anweisungen, die mit **SQLExecDirect** in einem System mit vielen Benutzern ausgeführt werden, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]von vielen der Vorteile der Planwiederverwendung profitieren, die nur für gespeicherte Prozeduren in früheren Versionen von verfügbar waren.  
  
 Die Vorteile der erneuten Nutzung von Ausführungsplänen können jedoch nur umgesetzt werden, wenn mehrere Benutzer die gleiche SQL-Anweisungen oder den gleichen Batch ausführen. Befolgen Sie diese Codierungskonventionen, um die Wahrscheinlichkeit zu erhöhen, dass die SQL-Anweisungen, die von unterschiedlichen Clients ausgeführt werden, sich soweit ähneln, dass die Ausführungspläne wiederverwendet werden können:  
  
-   Schließen Sie keine Datenkonstanten in die SQL-Anweisungen ein, verwenden Sie stattdessen an Programmvariablen gebundene Parametermarkierungen. Weitere Informationen finden Sie unter [Verwenden von Anweisungsparametern](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md).  
  
-   Verwenden Sie vollqualifizierte Objektnamen. Ausführungspläne werden nicht wiederverwendet, wenn Objektnamen nicht qualifiziert sind.  
  
-   Sorgen Sie dafür, dass Anwendungsverbindungen sofern möglich einen gemeinsamen Satz an Verbindungs- und Anweisungsoptionen verwenden. Ausführungspläne, die für eine Verbindung mit einem Optionssatz (z. B. ANSI_NULLS) generiert werden, werden nicht für Verbindungen mit einem anderen Optionssatz wiederverwendet. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber und der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter haben die gleichen Standardeinstellungen für diese Optionen.  
  
 Wenn alle mit **SQLExecDirect** ausgeführten Anweisungen mithilfe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dieser Konventionen codiert werden, können Ausführungspläne wiederverwendet werden, wenn die Verkaufschance besteht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
