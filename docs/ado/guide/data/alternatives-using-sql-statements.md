---
title: 'Alternativen: Mit SQL-Anweisungen | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f41ef7f0641877056a6e2f3d85fd6a40ff7826db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925991"
---
# <a name="alternatives-using-sql-statements"></a>Alternativen: Verwenden von SQL-Anweisungen
ADO kann auch mithilfe der Befehle als Alternative zu den integrierten Eigenschaften und Methoden zum Bearbeiten von Daten. Abhängig von Ihrem Anbieter, können alle Vorgänge, die in diesem Abschnitt aufgeführten auch erreichen, indem Befehle an die Datenquelle übergeben. Z. B. für die SQL UPDATE-Anweisungen verwendet werden können, zum Ändern von Daten ohne Verwendung der **Wert** Eigenschaft eine **Feld**. SQL-INSERT-Anweisungen können verwendet werden, um neue Datensätze zu einer Datenquelle, statt die ADO-Methode hinzufügen **AddNew**. Weitere Informationen zu SQL oder der Datenbearbeitungssprache Ihres Anbieters finden Sie in der Dokumentation zu Ihrer Datenquelle.  
  
 Beispielsweise können Sie eine SQL-Zeichenfolge, die mit einer DELETE-Anweisung mit einer Datenbank übergeben, wie im folgenden Code gezeigt:  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
