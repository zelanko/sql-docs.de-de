---
title: SQL Server-Meldungsergebnisse | Microsoft-Dokumentation
description: SQL Server-Meldungsergebnisse
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: e13ec74572e04e210b312e19d1e04aa1423d26db
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028837"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen generieren weder Rowsets für den OLE DB-Treiber für SQL Server noch eine Angabe betroffener Zeilen, wenn sie ausgeführt werden:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei einer erfolgreichen Ausführung der OLE DB-Treiber für SQL Server gibt S_OK zurück, und die Nachrichten für den OLE DB-Treiber für SQL Server-Consumer verfügbar sind.  
  
 Der OLE DB-Treiber für SQL Server gibt S_OK zurück, und verfügt über eine oder mehrere informationsmeldungen nach der Ausführung von vielen [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen oder die Ausführung Consumer ein OLE DB-Treiber für SQL Server-Member-Funktion.  
  
 Wenn der Consumer des OLE DB-Treibers für SQL Server die dynamische Angabe von Abfragetext zulässt, sollten die Fehlerschnittstellen nach jeder Ausführung einer Elementfunktion überprüft werden. Dabei spielen der Wert des Rückgabecodes, die Anwesenheit oder Abwesenheit eines zurückgegebenen **IRowset**- oder **IMultipleResults**-Schnittstellenverweises oder die Angabe betroffener Zeilen keine Rolle.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
