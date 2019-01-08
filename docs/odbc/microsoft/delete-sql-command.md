---
title: SQL‑Befehl "löschen"-| Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dac94d8bfb0e2bc0ab91f6a18e6f18606481b112
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53202029"
---
# <a name="delete---sql-command"></a>DELETE (SQL-Befehl)
Datensätze zum Löschen markiert.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die systemeigene Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie in den Hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Argumente  
 AUS [ *DatabaseName!*] *TableName*  
 Gibt die Tabelle, in der Datensätze zum Löschen markiert sind.  
  
 *DatabaseName!* Gibt den Namen einer Datenbank, die in der Tabelle enthält, wenn die enthaltene Datenbank nicht mit der Datenbank, mit der Datenquelle angegeben ist. Sie müssen den Namen einer Datenbank enthalten, die in der Tabelle enthält, wenn die Datenbank nicht mit der Datenbank, mit der Datenquelle angegeben ist. Schließen Sie das Ausrufezeichen (!)-Trennzeichen an, nach dem Datenbanknamen und vor dem Tabellennamen.  
  
 WO *FilterCondition1*[AND &#124; oder *FilterCondition2*...]  
 Gibt an, dass es sich bei Visual FoxPro nur bestimmte Datensätze zum Löschen markiert.  
  
 *FilterCondition* gibt die Kriterien, die Datensätze erfüllen müssen, um zum Löschen markiert werden. Sie können wie viele Bedingungen filtern, wie bei AND werden sollen, einschließen oder OR-Operator. Sie können auch den NOT-Operator verwenden, um den Wert eines logischen Ausdrucks umzukehren, Sie können auch **leere**(), um für ein leeres Feld zu überprüfen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn SET DELETED auf ON festgelegt ist, werden zum Löschen markierte Einträge von allen Befehlen, die einen Bereich enthalten, ignoriert.  
  
 Löschen Sie: SQL verwendet, geöffnet datensatzsperrung, wenn mehrere Datensätze in Tabellen zum Löschen markieren, für den gemeinsamen Zugriff. Dies verringert Datensatz Konflikte in mehrbenutzerumgebungen Situationen jedoch kann die Leistung reduzieren. Öffnen Sie in der Tabelle für die ausschließliche Verwendung zur Optimierung der Leistung.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung DELETE an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl in der Visual FoxPro-DELETE-Befehl ohne Übersetzung an.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl SET DELETED](../../odbc/microsoft/set-deleted-command.md)
