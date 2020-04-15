---
title: UPDATE - SQL-Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 818811c18ed52cef5bdb1c4d97f947bb86e67422
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307641"
---
# <a name="update---sql-command"></a>UPDATE (SQL-Befehl)
Aktualisiert Datensätze in einer Tabelle mit neuen Werten.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie unter **Treiberhinweise**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Argumente  
 UPDATE [ *Datenbankname1!*] *TableName1*  
 Gibt die Tabelle an, in der Datensätze mit neuen Werten aktualisiert werden.  
  
 *DatabaseName1!* gibt den Namen einer anderen Datenbank als der Datenbank an, die mit der Datenquelle angegeben ist, die die Tabelle enthält. Sie müssen den Namen der Datenbank einschließen, die die Tabelle enthält, wenn die Datenbank nicht die aktuelle ist. Fügen Sie das Ausrufezeichen (!) nach dem Datenbanknamen und vor dem Tabellennamen ein.  
  
 SET *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Gibt die aktualisierten Spalten und ihre neuen Werte an. Wenn Sie die WHERE-Klausel weglassen, wird jede Zeile in der Spalte mit demselben Wert aktualisiert.  
  
 WO *FilterCondition1*[UND &#124; ODER *FilterCondition2*...]  
 Gibt die Datensätze an, die mit neuen Werten aktualisiert werden.  
  
 *FilterCondition* gibt die Kriterien an, die Datensätze erfüllen müssen, um mit neuen Werten aktualisiert zu werden. Sie können beeine teerviele Filterbedingungen einschließen und sie mit dem OPERATOR AND oder OR verbinden. Sie können auch den Operator NOT verwenden, um den Wert eines logischen Ausdrucks umzukehren, oder Sie können **EMPTY**( ) verwenden, um nach einem leeren Feld zu suchen.  
  
## <a name="remarks"></a>Bemerkungen  
 UPDATE - SQL kann nur Datensätze in einer einzelnen Tabelle aktualisieren.  
  
 Im Gegensatz zu REPLACE verwendet UPDATE - SQL die Datensatzsperrung, wenn mehrere Datensätze in Tabellen aktualisiert werden, die für den freigegebenen Zugriff geöffnet wurden. Dies reduziert Rekordkonflikte in Mehrbenutzersituationen, kann aber die Leistung reduzieren. Öffnen Sie die Tabelle für maximale Leistung, oder verwenden Sie **FLOCK**( ), um die Tabelle zu sperren.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Ihre Anwendung die ODBC SQL-Anweisung UPDATE an die Datenquelle sendet, konvertiert der Visual FoxPro ODBC-Treiber den Befehl ohne Übersetzung in den Befehl Visual FoxProUPDATE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DELETE - SQL-Befehl](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (SQL-Befehl)](../../odbc/microsoft/insert-sql-command.md)
