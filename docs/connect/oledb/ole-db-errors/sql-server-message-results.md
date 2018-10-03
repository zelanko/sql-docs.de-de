---
title: SQL Server-Meldungsergebnisse | Microsoft-Dokumentation
description: SQL Server-Meldungsergebnisse
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: be796d00763c4004be121ae6ee25ef849d871cc5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619068"
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
  
  
