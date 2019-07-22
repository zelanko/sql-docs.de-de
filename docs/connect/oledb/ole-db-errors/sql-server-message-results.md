---
title: Ergebnisse der SQL Server Meldung | Microsoft-Dokumentation
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
ms.openlocfilehash: 05d731f418bad21f9e8ec32c620b352c5663994a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994922"
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
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei erfolgreicher Ausführung gibt der OLE DB Treiber für SQL Server S_OK zurück, und die Nachrichten sind für den OLE DB Treiber für SQL Server Consumer verfügbar.  
  
 Der OLE DB Treiber für SQL Server gibt S_OK zurück und verfügt über eine oder mehrere Informationsmeldungen, die nach der [!INCLUDE[tsql](../../../includes/tsql-md.md)] Ausführung vieler Anweisungen oder der Consumer-Ausführung eines OLE DB Treibers für SQL Server Member-Funktion verfügbar sind.  
  
 Wenn der Consumer des OLE DB-Treibers für SQL Server die dynamische Angabe von Abfragetext zulässt, sollten die Fehlerschnittstellen nach jeder Ausführung einer Elementfunktion überprüft werden. Dabei spielen der Wert des Rückgabecodes, die Anwesenheit oder Abwesenheit eines zurückgegebenen **IRowset**- oder **IMultipleResults**-Schnittstellenverweises oder die Angabe betroffener Zeilen keine Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
