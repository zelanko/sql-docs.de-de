---
title: 'Alternativen: Verwenden von SQL-Anweisungen | Microsoft-Dokumentation'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925991"
---
# <a name="alternatives-using-sql-statements"></a>Alternativen: Verwenden von SQL-Anweisungen
ADO ermöglicht außerdem die Verwendung von Befehlen als Alternativen zu den integrierten Eigenschaften und Methoden zum Bearbeiten von Daten. Abhängig von Ihrem Anbieter können auch alle in diesem Abschnitt erwähnten Vorgänge durch Übergeben von Befehlen an Ihre Datenquelle erreicht werden. Beispielsweise können SQL Update-Anweisungen verwendet werden, um Daten ohne Verwendung der **value** -Eigenschaft eines **Felds**zu ändern. SQL INSERT-Anweisungen können zum Hinzufügen neuer Datensätze zu einer Datenquelle anstelle der ADO-Methode **AddNew**verwendet werden. Weitere Informationen zu SQL oder zur Daten Bearbeitungs Sprache Ihres Anbieters finden Sie in der Dokumentation zu Ihrer Datenquelle.  
  
 Beispielsweise können Sie eine SQL-Zeichenfolge, die eine DELETE-Anweisung enthält, an eine Datenbank übergeben, wie im folgenden Code gezeigt:  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
