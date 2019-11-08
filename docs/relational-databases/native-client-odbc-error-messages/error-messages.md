---
title: Fehlermeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 10308509004493ba68d23870a70bf878ae05b4a1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783459"
---
# <a name="error-messages"></a>Fehlermeldungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der Text der vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber zurückgegebenen Nachrichten wird in den *MessageText* -Parameter von **SQLGetDiagRec**eingefügt. Die Quelle eines Fehlers wird im Header der Meldung angegeben:  
  
 [Microsoft][ODBC-Treiber-Manager]  
 Diese Fehler werden vom ODBC-Treiber-Manager ausgelöst.  
  
 [Microsoft][ODBC-Cursorbibliothek]  
 Diese Fehler werden von der ODBC-Cursorbibliothek ausgelöst.  
  
 [Microsoft][SQL Server Native Client]  
 Diese Fehler werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ausgelöst. Wenn keine anderen Knoten entweder mit den Namen einer Netzwerkbibliothek oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden sind, trat der Fehler im Treiber auf.  
  
 Microsoft [SQL Server Native Client] [*Net-TransportName*]  
 Diese Fehler werden durch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library ausgelöst, wobei *net-TransportName* der Anzeige Name eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client-Netzwerk Transports (z. b. Named Pipes, Shared Memory, TCP/IP Sockets oder via) ist. Die restliche Fehlermeldung enthält die aufgerufene Netzwerkbibliotheksfunktion und die von der TDS-Funktion in der zugrunde liegenden Netzwerk-API aufgerufene Funktion. Der mit diesen Fehlern zurückgegebene *pfNative* -Fehlercode ist der Fehlercode aus dem zugrunde liegenden Netzwerkprotokoll Stapel.  
  
 Microsoft [SQL Server Native Client] [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Diese Fehler werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgelöst. Die übrige Fehlermeldung entspricht dem Text der Fehlermeldung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Der mit diesen Fehlern zurückgegebene *pfNative* Code ist die Fehlernummer aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zu einer Liste von Fehlermeldungen (und deren Zahlen), die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben werden können, finden Sie in der Beschreibung und den Fehler Spalten der **sysmess Ages** -Systemtabelle in der **Master** -Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
