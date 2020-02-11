---
title: Update-SQL-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0230329d10d2414724379d4b9d38c4851a031bca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912336"
---
# <a name="update---sql-command"></a>UPDATE (SQL-Befehl)
Aktualisiert Datensätze in einer Tabelle mit neuen Werten.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiber spezifische Informationen finden Sie unter **Treiber Hinweise**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Argumente  
 Aktualisieren [ *DatabaseName1!*] *TableName1*  
 Gibt die Tabelle an, in der Datensätze mit neuen Werten aktualisiert werden.  
  
 *DatabaseName1!* Gibt den Namen einer anderen Datenbank als der Datenbank an, die mit der Datenquelle angegeben ist, in der die Tabelle enthalten ist. Wenn die Datenbank nicht die aktuelle Datenbank ist, müssen Sie den Namen der Datenbank einschließen, in der die Tabelle enthalten ist. Schließen Sie das Ausrufezeichen (!) nach dem Datenbanknamen und vor dem Tabellennamen ein.  
  
 Set *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Gibt die aktualisierten Spalten und ihre neuen Werte an. Wenn Sie die WHERE-Klausel weglassen, wird jede Zeile in der Spalte mit demselben Wert aktualisiert.  
  
 Where *FilterCondition1*[und &#124; oder *FilterCondition2*...]  
 Gibt die Datensätze an, die mit neuen Werten aktualisiert werden.  
  
 *Filtercondition* gibt die Kriterien an, die Datensätze erfüllen müssen, um mit neuen Werten aktualisiert zu werden. Sie können beliebig viele Filterbedingungen einschließen und diese mit dem and-Operator oder or-Operator verbinden. Sie können auch den Not-Operator verwenden, um den Wert eines logischen Ausdrucks umzukehren, oder Sie können **empty**() verwenden, um nach einem leeren Feld zu suchen.  
  
## <a name="remarks"></a>Bemerkungen  
 Update-SQL kann nur Datensätze in einer einzelnen Tabelle aktualisieren.  
  
 Anders als bei Replace verwendet Update-SQL die Datensatzsperre, wenn mehrere Datensätze in Tabellen aktualisiert werden, die für den freigegebenen Zugriff Dies reduziert Daten Satz Konflikte in mehr Benutzer Situationen, kann jedoch die Leistung beeinträchtigen. Um die maximale Leistung zu erzielen, öffnen Sie die Tabelle für die exklusive Verwendung, oder verwenden Sie zum Sperren der Tabelle " **Flock**()"  
  
## <a name="driver-remarks"></a>Hinweise zu Treibern  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisungs Aktualisierung an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl ohne Übersetzung in den Visual foxproupdate-Befehl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DELETE-SQL-Befehl](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (SQL-Befehl)](../../odbc/microsoft/insert-sql-command.md)
