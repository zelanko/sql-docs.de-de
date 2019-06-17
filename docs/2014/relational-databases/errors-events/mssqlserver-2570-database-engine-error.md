---
title: MSSQLSERVER_2570 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5169e030246b8f5a834e6a2526232907a7e22526
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914429"
---
# <a name="mssqlserver2570"></a>MSSQLSERVER_2570
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2570|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Meldungstext|Seite P_ID, Slot S_ID in Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (TYPE-Typ). Der Wert der COLUMN_NAME-Spalte liegt für den "DATATYPE"-Datentyp außerhalb des gültigen Bereichs. Aktualisieren Sie die Spalte auf einen gültigen Wert.|  
  
## <a name="explanation"></a>Erklärung  
 Der Spaltenwert, der in der angegebenen Spalte enthalten ist, liegt außerhalb des Bereichs der möglichen Werte für den Spaltendatentyp.  
  
## <a name="user-action"></a>Benutzeraktion  
 Der Fehler kann nicht behoben werden. Aktualisieren Sie die Spalte auf einen Wert innerhalb des Bereichs für den Datentyp der Spalte, und führen Sie den Befehl erneut aus.  Weitere Informationen finden Sie im KB-Artikel [923247](https://support.microsoft.com/kb/923247).  
  
## <a name="see-also"></a>Siehe auch  
 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
