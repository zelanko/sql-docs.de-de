---
title: Direkte Ausführung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 292b0f787819a52eb5759ead41bde80fc3a72acf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779764"
---
# <a name="direct-execution"></a>Direkte Ausführung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die direkte Ausführung ist die grundlegendste Art und Weise, um eine Anweisung auszuführen. Eine Anwendung erstellt eine Zeichenfolge, die [!INCLUDE[tsql](../../../includes/tsql-md.md)] eine-Anweisung enthält, und sendet Sie mithilfe der **SQLExecDirect** -Funktion zur Ausführung. Wenn die Anweisung beim Server eingeht, kompiliert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie zu einem Ausführungsplan, der unmittelbar ausgeführt wird.  
  
 Die direkte Ausführung wird im Allgemeinen von Anwendungen verwendet, die Anweisungen zur Laufzeit erstellen und ausführen. Es ist zugleich die effektivste Methode, Anweisungen, die nur einmal ausgeführt werden, auszuführen. Bei vielen Datenbanken muss jedoch die SQL-Anweisung bei jeder Ausführung analysiert und kompiliert werden, sodass ein zusätzlicher Aufwand entsteht, wenn die Anweisung mehrmals ausgeführt wird.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wurde die Leistung bei der direkten Ausführung von häufig ausgeführten Anweisungen in Mehrbenutzerumgebungen wesentlich verbessert. Durch den Einsatz von SQLExecDirect mit Parametermarkierungen für häufig ausgeführte SQL-Anweisungen wird zudem beinahe die gleiche Effizienz wie bei der vorbereiteten Ausführung erzielt.  
  
 Wenn eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]von besteht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , verwendet der Native Client ODBC-Treiber [sp_executesql](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) , um die SQL-Anweisung oder den Batch zu übertragen, die in **SQLExecDirect**angegeben ist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verfügt über Logik, um schnell festzustellen, ob eine SQL-Anweisung oder ein Batch, der mit **sp_executesql** ausgeführt wird, mit der Anweisung oder dem Batch übereinstimmt, die einen Ausführungsplan generiert hat Wenn eine Übereinstimmung gefunden wird, nutzt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den vorhandenen Plan, anstatt einen neuen Plan zu kompilieren. Dies bedeutet, dass häufig ausgeführte SQL-Anweisungen, die mit **SQLExecDirect** in einem System mit vielen Benutzern ausgeführt werden, von vielen der Vorteile der Plan Wiederverwendung profitieren, die nur für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gespeicherte Prozeduren in früheren Versionen von verfügbar waren.  
  
 Die Vorteile der erneuten Nutzung von Ausführungsplänen können jedoch nur umgesetzt werden, wenn mehrere Benutzer die gleiche SQL-Anweisungen oder den gleichen Batch ausführen. Befolgen Sie diese Codierungskonventionen, um die Wahrscheinlichkeit zu erhöhen, dass die SQL-Anweisungen, die von unterschiedlichen Clients ausgeführt werden, sich soweit ähneln, dass die Ausführungspläne wiederverwendet werden können:  
  
-   Schließen Sie keine Datenkonstanten in die SQL-Anweisungen ein, verwenden Sie stattdessen an Programmvariablen gebundene Parametermarkierungen. Weitere Informationen finden Sie unter [Verwenden von Anweisungs Parametern](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md).  
  
-   Verwenden Sie vollqualifizierte Objektnamen. Ausführungspläne werden nicht wiederverwendet, wenn Objektnamen nicht qualifiziert sind.  
  
-   Sorgen Sie dafür, dass Anwendungsverbindungen sofern möglich einen gemeinsamen Satz an Verbindungs- und Anweisungsoptionen verwenden. Ausführungspläne, die für eine Verbindung mit einem Optionssatz (z. B. ANSI_NULLS) generiert werden, werden nicht für Verbindungen mit einem anderen Optionssatz wiederverwendet. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber und der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter haben die gleichen Standardeinstellungen für diese Optionen.  
  
 Wenn alle-Anweisungen, die mit **SQLExecDirect** ausgeführt werden, mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] diesen Konventionen codiert werden, kann Ausführungspläne wieder verwenden, wenn die Gelegenheit eintritt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
