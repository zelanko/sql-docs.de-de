---
title: Binden von Parametern | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9c78e5e26e967699c0bf69577bece7426461f0a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047369"
---
# <a name="binding-parameters"></a>Binden von Parametern
  Jede Parametermarkierung in einer SQL-Anweisung muss mit einer Variablen in der Anwendung verknüpft oder an diese gebunden werden, bevor die Anweisung ausgeführt wird. Dies erfolgt durch Aufrufen der [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) Funktion. **SQLBindParameter** beschreibt die Programmvariable (Adresse, C-Datentyp usw.) an den Treiber. Ferner identifiziert sie die Parametermarkierung durch Angabe ihres Ordinalwerts und beschreibt anschließend die Eigenschaften des SQL-Objekts, das sie darstellt (SQL-Datentyp, Genauigkeit usw.).  
  
 Parametermarkierungen können vor der Ausführung einer Anweisung jederzeit gebunden bzw. neu gebunden werden. Eine Parameterbindung bleibt wirksam, bis eines der folgenden Ereignisse eintritt:  
  
-   Ein Aufruf von [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) mit der *Option* -Parameter auf SQL_RESET_PARAMS festgelegt gibt alle an das Anweisungshandle gebundenen Parameter frei.  
  
-   Ein Aufruf von **SQLBindParameter** mit *ParameterNumber* auf die Ordinalzahl einer gebundenen parametermarkierung festgelegt werden automatisch die vorherige Bindung frei.  
  
 Eine Anwendung kann ferner Parameter an Arrays von Programmvariablen binden, um eine SQL-Anweisung batchweise zu verarbeiten. Es gibt zwei Arten der Arraybindung:  
  
-   Die spaltenweise Bindung ist fertig gestellt, wenn jeder einzelne Parameter an sein eigenes Array von Variablen gebunden wurde.  
  
     Die spaltenweise Bindung wird angegeben, durch den Aufruf [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) mit *Attribut* legen Sie SQL_ATTR_PARAM_BIND_TYPE und *ValuePtr* auf SQL_PARAM_BIND_BY_COLUMN festgelegt wird.  
  
-   Die zeilenweise Beendung ist fertig gestellt, wenn alle Parameter in der SQL-Anweisung als Einheit an ein Array von Strukturen gebunden wurden, die die einzelnen Variablen für die Parameter enthalten.  
  
     Zeilenweise Bindung wird angegeben, indem **SQLSetStmtAttr** mit *Attribut* legen Sie SQL_ATTR_PARAM_BIND_TYPE und *ValuePtr* legen Sie auf die Größe des Betriebs Struktur der Programmvariablen.  
  
 Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber Zeichen- oder Binärzeichenfolgen-Parameter an den Server sendet, werden die Werte der im angegebenen Länge **SQLBindParameter** *ColumnSize* Parameter. Wenn eine ODBC 2.x-Anwendung gibt 0 für an *ColumnSize*, der Treiber füllt den Wert des Parameters, um die Genauigkeit des Datentyps. Die Genauigkeit beträgt bei einer Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 8000, bei einer Verbindung zu älteren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 255. *ColumnSize* ist für variant-Spalten in Bytes.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt definierende Namen für gespeicherte Prozedurparameter. ODBC 3.5 hat ebenfalls Unterstützung für benannte Parameter eingeführt, die verwendet werden, wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozeduren aufgerufen werden. Diese Unterstützung kann für Folgendes verwendet werden:  
  
-   Zum Aufrufen einer gespeicherten Prozedur und Eingeben von Werten für eine Teilmenge der für die gespeicherte Prozedur definierten Parameter  
  
-   Zum Angeben der Parameter in einer anderen Reihenfolge in der Anwendung als in der Reihenfolge, in der sie bei der Erstellung der gespeicherten Prozedur angegeben wurden  
  
 Benannte Parameter werden nur unterstützt, wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` -Anweisung oder die ODBC CALL-Escapesequenz zum Ausführen einer gespeicherten Prozedur.  
  
 Wenn `SQL_DESC_NAME` für einen gespeicherten Prozedurparameter festgelegt wird, sollten alle gespeicherten Prozedurparameter in der Abfrage ebenfalls `SQL_DESC_NAME` festlegen.  Wenn Literale in gespeicherten Prozeduraufrufen verwendet werden, für den Parameter haben `SQL_DESC_NAME` festgelegt ist, sollten die Literale das Format verwendet *"Namen*=*Wert*", wobei *Namen* ist der Parametername der gespeicherten Prozedur (z. B. @p1). Weitere Informationen finden Sie unter [Bindungsparameter von Namen (Parameter genannt)](http://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Anweisungsparametern](using-statement-parameters.md)  
  
  