---
title: Ausführen von Anweisungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a367d5ee7def19ffdfd40e24860ebf95f642fae9
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82700430"
---
# <a name="executing-statements-odbc"></a>Ausführen von Anweisungen (ODBC)
  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber bietet eine Vielzahl von Möglichkeiten zum Ausführen von SQL-Anweisungen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank:  
  
-   Direkte Ausführung  
  
-   Vorbereitete Ausführung  
  
 Die direkte Ausführung umfasst die Verwendung einer Zeichenfolge, [!INCLUDE[tsql](../../../includes/tsql-md.md)] die eine-Anweisung enthält, und die Übermittlung mit der **SQLExecDirect** -Funktion zur Ausführung. Die vorbereitete Ausführung erfordert die Bildung einer Zeichenfolge, die eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung enthält, und die Ausführung dieser Anweisung in zwei Phasen. In der ersten Phase wird die [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) verwendet, um den Ausführungsplan für die Anweisung im zu analysieren und zu kompilieren [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . In der zweiten Phase wird die **SQLExecute** -Funktion verwendet, um den zuvor vorbereiteten Ausführungsplan auszuführen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Sowohl bei der direkten als auch bei der vorbereiteten Ausführung können einzelne [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen oder Batches von SQL-Anweisungen ausgeführt oder gespeicherte Prozeduren aufgerufen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Direkte Ausführung](direct-execution.md)  
  
-   [Vorbereitete Ausführung](prepared-execution.md)  
  
-   [Verfahren](procedures.md)  
  
-   [Batches von Anweisungen](batches-of-statements.md)  
  
-   [Effekte von ISO-Optionen](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../executing-queries-odbc.md)  
  
  
