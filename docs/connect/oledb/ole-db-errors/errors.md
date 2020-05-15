---
title: OLE DB Errors
description: Erfahren Sie, wie Fehler im OLE DB-Treiber für SQL Server zurückgegeben werden und wie Sie Informationen zu ihnen abrufen können.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 82fe76b5a7ab2445884f7741abc81bfa0b400ed1
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922406"
---
# <a name="errors"></a>Errors
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE/COM-Objekte melden Fehler durch den HRESULT-Rückgabecode von Objektelementfunktionen. Ein OLE/COM HRESULT ist eine Bitgepackte Struktur. OLE stellt Makros bereit, die Strukturmember dereferenzieren.  
  
 OLE/COM gibt die **IErrorInfo**-Schnittstelle an. Die Schnittstelle macht Methoden wie **GetDescription** verfügbar. Dies ermöglicht es Clients, Fehlerdetails aus OLE/COM-Servern zu extrahieren. OLE DB erweitert **IErrorInfo**, um die Rückgabe von mehreren Fehlerinformationspaketen bei der Ausführung einer Einzelmemberfunktion zu unterstützen.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann mehrere Fehler zurückgeben. Eine Anwendung kann Serverfehler einzeln abrufen, indem [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) in Kombination mit ISQLErrorInfo und IErrorRecords aufgerufen wird.  
  
 Der OLE DB-Treiber für SQL Server stellt die durch OLE DB-Datensätze erweiterte **IErrorInfo**-, die benutzerdefinierte **ISQLErrorInfo**- und die anbieterspezifische [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)-Fehlerobjektschnittstelle bereit.  
  
 Informationen zur Ablaufverfolgung von Fehlern finden Sie unter [Data Access Tracing (Ablaufverfolgung für den Datenzugriff)](https://go.microsoft.com/fwlink/?LinkId=125805). Informationen zu Verbesserungen der in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] hinzugefügten Fehlerablaufverfolgung finden Sie unter [Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Rückgabecodes](../../oledb/ole-db-errors/return-codes.md)  
  
-   [Informationen in Fehlerschnittstellen](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [SQL Server-Fehlerdetail](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [Abrufen von Fehlerinformationen](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [SQL Server-Meldungsergebnisse](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
