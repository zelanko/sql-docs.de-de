---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 73ac3425eab1a4c19130352ef566153eb6c34e53
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048718"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Bei ausgeführten Anweisungen geht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ist nicht besuchen Sie den Server aus, um die Anzahl der Spalten in einem Resultset zu melden. In diesem Fall `SQLNumResultCols` keinen Serverroundtrip herbei. Wie [SQLDescribeCol](sqldescribecol.md) und [SQLColAttribute](sqlcolattribute.md)Aufrufen `SQLNumResultCols` für vorbereitete, aber nicht ausgeführte Anweisungen generiert eine Server-Roundtrip erstellt.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsbatch mehrere Resultsets für Zeilen zurückgibt, kann die Anzahl der Resultset-Spalten sich von einem Set zum nächsten ändern. `SQLNumResultCols` sollte für jede Gruppe aufgerufen werden. Wenn sich die Anzahl der Spalten ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Finden Sie weitere Informationen zum Arbeiten mit mehreren resultsetergebnissen [SQLMoreResults](sqlmoreresults.md).  
  
 Verbesserungen im Datenbankmodul ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLNumResultCols genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheidet sich möglicherweise von der Rückgabewerte SQLNumResultCols in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLNumResultCols-Funktion](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  