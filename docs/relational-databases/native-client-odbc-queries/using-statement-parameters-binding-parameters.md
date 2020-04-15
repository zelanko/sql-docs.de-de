---
title: Bindungsparameter | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 01e179d2abc6ef786f94b6d7938f0e21938c5a59
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304628"
---
# <a name="using-statement-parameters---binding-parameters"></a>Verwenden von Anweisungsparametern: Binden von Parametern
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Jede Parametermarkierung in einer SQL-Anweisung muss mit einer Variablen in der Anwendung verknüpft oder an diese gebunden werden, bevor die Anweisung ausgeführt wird. Dies geschieht durch Aufrufen der [SQLBindParameter-Funktion.](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) **SQLBindParameter** beschreibt die Programmvariable (Adresse, C-Datentyp usw.) für den Treiber. Ferner identifiziert sie die Parametermarkierung durch Angabe ihres Ordinalwerts und beschreibt anschließend die Eigenschaften des SQL-Objekts, das sie darstellt (SQL-Datentyp, Genauigkeit usw.).  
  
 Parametermarkierungen können vor der Ausführung einer Anweisung jederzeit gebunden bzw. neu gebunden werden. Eine Parameterbindung bleibt wirksam, bis eines der folgenden Ereignisse eintritt:  
  
-   Ein Aufruf von [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) mit dem *Option-Parameter,* der auf SQL_RESET_PARAMS festgelegt ist, gibt alle Parameter frei, die an das Anweisungshandle gebunden sind.  
  
-   Ein Aufruf von **SQLBindParameter** mit *ParameterNumber,* der auf die Ordnung einer gebundenen Parametermarkierung festgelegt ist, gibt automatisch die vorherige Bindung frei.  
  
 Eine Anwendung kann ferner Parameter an Arrays von Programmvariablen binden, um eine SQL-Anweisung batchweise zu verarbeiten. Es gibt zwei Arten der Arraybindung:  
  
-   Die spaltenweise Bindung ist fertig gestellt, wenn jeder einzelne Parameter an sein eigenes Array von Variablen gebunden wurde.  
  
     Die spaltenweise Bindung wird durch Aufrufen von [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) angegeben, wobei *Das Attribut* auf SQL_ATTR_PARAM_BIND_TYPE festgelegt ist und *ValuePtr* auf SQL_PARAM_BIND_BY_COLUMN festgelegt ist.  
  
-   Die zeilenweise Beendung ist fertig gestellt, wenn alle Parameter in der SQL-Anweisung als Einheit an ein Array von Strukturen gebunden wurden, die die einzelnen Variablen für die Parameter enthalten.  
  
     Die zeilenweise Bindung wird durch Aufrufen von **SQLSetStmtAttr** angegeben, wobei *Das Attribut* auf SQL_ATTR_PARAM_BIND_TYPE festgelegt ist und *ValuePtr* auf die Größe der Struktur festgelegt ist, die die Programmvariablen enthält.  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der native Client ODBC-Treiber Zeichen- oder Binärzeichenfolgenparameter an den Server sendet, werden die Werte auf die im Parameter **SQLBindParameter** *ColumnSize* angegebene Länge aufgepolstert. Wenn eine ODBC 2.x-Anwendung 0 für *ColumnSize*angibt, legt der Treiber den Parameterwert auf die Genauigkeit des Datentyps fest. Die Genauigkeit beträgt bei einer Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 8000, bei einer Verbindung zu älteren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 255. *ColumnSize* ist in Bytes für Variantenspalten.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt definierende Namen für gespeicherte Prozedurparameter. ODBC 3.5 hat ebenfalls Unterstützung für benannte Parameter eingeführt, die verwendet werden, wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozeduren aufgerufen werden. Diese Unterstützung kann für Folgendes verwendet werden:  
  
-   Zum Aufrufen einer gespeicherten Prozedur und Eingeben von Werten für eine Teilmenge der für die gespeicherte Prozedur definierten Parameter  
  
-   Zum Angeben der Parameter in einer anderen Reihenfolge in der Anwendung als in der Reihenfolge, in der sie bei der Erstellung der gespeicherten Prozedur angegeben wurden  
  
 Benannte Parameter werden nur [!INCLUDE[tsql](../../includes/tsql-md.md)] unterstützt, wenn die **EXECUTE-Anweisung** oder die ODBC CALL-Escapesequenz zum Ausführen einer gespeicherten Prozedur verwendet wird.  
  
 Wenn **SQL_DESC_NAME** für einen gespeicherten Prozedurparameter festgelegt ist, sollten alle gespeicherten Prozedurparameter in der Abfrage auch **SQL_DESC_NAME**festlegen.  Wenn Literale in gespeicherten Prozeduraufrufen verwendet werden, bei denen Parameter **SQL_DESC_NAME** festgelegt haben, sollten die Literale das @p1Format=*"Nameswert"* verwenden, wobei *Name* der Parametername der gespeicherten Prozedur ist (z. B. ). *'name* Weitere Informationen finden Sie unter [Bindungsparameter nach Name (Benannte Parameter)](https://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Anweisungsparametern](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
