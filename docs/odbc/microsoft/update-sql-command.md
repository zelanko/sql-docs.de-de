---
title: SQL-UPDATE - Befehl | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 3fbd5ec98791d782fe7ad1fdb1e1884b646dcf9f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632557"
---
# <a name="update---sql-command"></a>UPDATE (SQL-Befehl)
Datensätze in einer Tabelle mit neuen Werten aktualisiert.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die systemeigene Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie **Treiber "Hinweise"**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Argumente  
 UPDATE [ *DatabaseName1!*] *TableName1*  
 Gibt die Tabelle, die in der Datensätze mit neuen Werten aktualisiert werden.  
  
 *DatabaseName1!* Gibt den Namen einer Datenbank als der Datenbank, die mit der Datenquelle, die die Tabelle angegeben. Sie müssen den Namen der Datenbank, die in der Tabelle enthält, wenn die Datenbank nicht mit dem aktuellen Objekt ist einschließen. Schließen Sie das Ausrufezeichen (!)-Trennzeichen an, nach dem Datenbanknamen und vor dem Tabellennamen.  
  
 SET *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Gibt an, die Spalten, die aktualisiert werden und die neuen Werte. Wenn Sie die WHERE-Klausel auslassen, wird jede Zeile in der Spalte mit den gleichen Wert aktualisiert.  
  
 WO *FilterCondition1*[AND &#124; oder *FilterCondition2*...]  
 Gibt an, die Datensätze, die mit neuen Werten aktualisiert werden.  
  
 *FilterCondition* gibt die Kriterien, die Datensätze erfüllen müssen, um mit neuen Werten aktualisiert werden. Sie können enthalten, wie viele Bedingungen filtern, wie Sie bei der AND oder OR-Operator. Sie können auch den NOT-Operator verwenden, um den Wert eines logischen Ausdrucks umzukehren, Sie können auch **leere**(), um für ein leeres Feld zu überprüfen.  
  
## <a name="remarks"></a>Hinweise  
 UPDATE - SQL kann nur die Datensätze in einer einzelnen Tabelle-update.  
  
 Im Gegensatz zu ersetzen verwendet die SQL-UPDATE – datensatzsperrung beim Aktualisieren von mehreren Datensätzen in Tabellen, die für den gemeinsamen Zugriff geöffnet. Dies verringert Datensatz Konflikte in mehrbenutzerumgebungen Situationen jedoch kann die Leistung verringern. Öffnen Sie die Tabelle zur Optimierung der Leistung für exklusive verwenden oder **Bestand**(), um die Tabelle zu sperren.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung UPDATE an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl in der Visual FoxProUPDATE-Befehl ohne Übersetzung an.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen Sie SQL‑Befehl ""](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (SQL-Befehl)](../../odbc/microsoft/insert-sql-command.md)
