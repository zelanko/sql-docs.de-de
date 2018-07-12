---
title: Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac616813b3437c57a8e071ea876874880874f039
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424669"
---
# <a name="errors"></a>Fehler
  OLE/COM-Objekte melden Fehler durch den HRESULT-Rückgabecode von Objektelementfunktionen. Ein OLE/COM HRESULT ist eine Bitgepackte Struktur. OLE stellt Makros bereit, die Strukturmember dereferenzieren.  
  
 OLE/COM gibt die **IErrorInfo** Schnittstelle. Die Schnittstelle macht Methoden verfügbar, z. B. **GetDescription**. Dies ermöglicht es Clients, Fehlerdetails aus OLE/COM-Servern zu extrahieren. OLE DB erweitert **IErrorInfo** um die Rückgabe von mehreren fehlerinformationspaketen für die Ausführung einer einzelmemberfunktion zu unterstützen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann mehrere Fehler zurückgeben. Eine Anwendung kann Serverfehler zu einem Zeitpunkt abrufen, durch den Aufruf [IMultipleResults:: GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) mit ISQLErrorInfo und IErrorRecords kombiniert.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt der OLE DB-Datensätze erweiterte **IErrorInfo**, die benutzerdefinierte `ISQLErrorInfo`, und die anbieterspezifische [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) -Fehlerobjekt. Schnittstellen.  
  
 Informationen zur Ablaufverfolgung von Fehlern, finden Sie unter [Datenzugriffs-Ablaufverfolgung](http://go.microsoft.com/fwlink/?LinkId=125805). Informationen zu Verbesserungen hinzugefügten fehlerablaufverfolgung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], finden Sie unter [den Zugriff auf Diagnoseinformationen im Protokoll für erweiterte Ereignisse](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Rückgabecodes](return-codes.md)  
  
-   [Informationen in Fehlerschnittstellen](information-in-error-interfaces.md)  
  
-   [SQL Server-Fehlerdetail](sql-server-error-detail.md)  
  
-   [Abrufen von Fehlerinformationen](retrieving-error-information.md)  
  
-   [SQL Server-Meldungsergebnisse](sql-server-message-results.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
