---
title: SQLNumResultCols | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88edec63a97ff6c463f07add895ff8399fc4268a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046755"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Bei ausgeführten Anweisungen nimmt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber den Server nicht an, um die Anzahl der Spalten in einem Resultset zu melden. In diesem Fall verursacht `SQLNumResultCols` keinen Serverroundtrip. Wie [SQLDescribeCol](sqldescribecol.md) und [SQLColAttribute](sqlcolattribute.md)wird durch `SQLNumResultCols` den Aufruf von für vorbereitete, aber nicht ausgeführte Anweisungen ein Serverroundtrip generiert.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsbatch mehrere Resultsets für Zeilen zurückgibt, kann die Anzahl der Resultset-Spalten sich von einem Set zum nächsten ändern. `SQLNumResultCols`muss für jeden Satz aufgerufen werden. Wenn sich die Anzahl der Spalten ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Verarbeiten mehrerer Resultsets finden Sie unter [SQLMoreResults](sqlmoreresults.md).  
  
 Verbesserungen in der Datenbank- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Engine, die mit beginnen, ermöglichen SQLNumResultCols, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von SQLNumResultCols in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]früheren Versionen von zurückgegeben wurden. Weitere Informationen finden Sie unter [metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLNumResultCols-Funktion](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
