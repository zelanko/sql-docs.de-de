---
title: Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 434b4251c51809c97744e7aaf954ac1f11c06cfa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63050674"
---
# <a name="errors"></a>Fehler
  OLE/COM-Objekte melden Fehler durch den HRESULT-Rückgabecode von Objektelementfunktionen. Ein OLE/COM HRESULT ist eine Bitgepackte Struktur. OLE stellt Makros bereit, die Strukturmember dereferenzieren.  
  
 OLE/COM gibt die **IErrorInfo**-Schnittstelle an. Die Schnittstelle macht Methoden wie **GetDescription** verfügbar. Dies ermöglicht es Clients, Fehlerdetails aus OLE/COM-Servern zu extrahieren. OLE DB erweitert **IErrorInfo**, um die Rückgabe von mehreren Fehlerinformationspaketen bei der Ausführung einer Einzelmemberfunktion zu unterstützen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann mehrere Fehler zurückgeben. Eine Anwendung kann Serverfehler einzeln abrufen, indem [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) in Kombination mit ISQLErrorInfo und IErrorRecords aufgerufen wird.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt der OLE DB-Datensätze erweiterte **IErrorInfo**, die benutzerdefinierte `ISQLErrorInfo`, und die anbieterspezifische [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) -Fehlerobjekt. Schnittstellen.  
  
 Informationen zur Ablaufverfolgung von Fehlern finden Sie unter [Data Access Tracing (Ablaufverfolgung für den Datenzugriff)](https://go.microsoft.com/fwlink/?LinkId=125805). Informationen zu Verbesserungen hinzugefügten fehlerablaufverfolgung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], finden Sie unter [den Zugriff auf Diagnoseinformationen im Protokoll für erweiterte Ereignisse](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Rückgabecodes](return-codes.md)  
  
-   [Informationen in Fehlerschnittstellen](information-in-error-interfaces.md)  
  
-   [SQL Server-Fehlerdetail](sql-server-error-detail.md)  
  
-   [Abrufen von Fehlerinformationen](retrieving-error-information.md)  
  
-   [SQL Server-Meldungsergebnisse](sql-server-message-results.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
