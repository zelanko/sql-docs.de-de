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
ms.openlocfilehash: dfebd7443b24d09e6bf7696caba5449c1890e0d2
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "85998286"
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
  
 Wenn der Consumer des OLE DB-Treibers für SQL Server die dynamische Angabe von Abfragetext zulässt, sollten die Fehlerschnittstellen nach jeder Ausführung einer Elementfunktion überprüft werden. Dabei spielen der Wert des Rückgabecodes, die Anwesenheit oder Abwesenheit eines zurückgegebenen **IRowset**- oder **IMultipleResults**-Schnittstellenverweises oder die Angabe betroffener Zeilen keine Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
