---
title: SQL Server-Meldungsergebnisse (OLE DB-Treiber)
description: Erfahren Sie mehr über Transact-SQL-Anweisungen, die keine OLE DB-Treiber für SQL Server-Rowsets oder eine Anzahl generieren, und deren erwartete Rückgabewerte.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dc3701313f920eead650435ca40538ad8a4b6ef0
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862503"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen generieren weder Rowsets für den OLE DB-Treiber für SQL Server noch eine Angabe betroffener Zeilen, wenn sie ausgeführt werden:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei erfolgreicher Ausführung gibt der OLE DB-Treiber für SQL Server S_OK zurück, und die Meldungen sind für den Consumer des OLE DB-Treibers für SQL Server verfügbar.  
  
 Der OLE DB-Treiber für SQL Server gibt S_OK zurück und weist eine oder mehrere Informationsmeldungen auf, nachdem eine Elementfunktion des OLE DB-Treibers für SQL Server durch den Consumer oder zahlreiche [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen ausgeführt wurden.  
  
Der Consumer des OLE DB-Treibers für SQL Server darf den Abfragetext dynamisch angeben. Der Consumer muss Fehlerschnittstellen nach der Ausführung _jeder_ Memberfunktion prüfen. Diese Prüfungen sollten stets durchgeführt werden, und zwar unabhängig vom Wert des Rückgabecodes und davon, ob ein Schnittstellenverweis auf `IRowset` oder `IMultipleResults` zurückgegeben wird oder nicht, und von der Anzahl der betroffenen Zeilen.
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
