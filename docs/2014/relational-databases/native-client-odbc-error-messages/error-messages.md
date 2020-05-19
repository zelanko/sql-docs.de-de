---
title: Fehlermeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bbf73940b92ef158e4e93b10c2142c9053703f5f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705416"
---
# <a name="error-messages"></a>Fehlermeldungen
  Der Text der Nachrichten, die vom Native Client-ODBC-Treiber zurückgegeben werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird im *MessageText* -Parameter von **SQLGetDiagRec**abgelegt. Die Quelle eines Fehlers wird im Header der Meldung angegeben:  
  
 [Microsoft][ODBC-Treiber-Manager]  
 Diese Fehler werden vom ODBC-Treiber-Manager ausgelöst.  
  
 [Microsoft][ODBC-Cursorbibliothek]  
 Diese Fehler werden von der ODBC-Cursorbibliothek ausgelöst.  
  
 [Microsoft][SQL Server Native Client]  
 Diese Fehler werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ausgelöst. Wenn keine anderen Knoten entweder mit den Namen einer Netzwerkbibliothek oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden sind, trat der Fehler im Treiber auf.  
  
 Microsoft [SQL Server Native Client] [*Net-TransportName*]  
 Diese Fehler werden von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Netzwerk Bibliothek ausgelöst, wobei *net-TransportName* der Anzeige Name eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Netzwerk Transports (z. b. Named Pipes, Shared Memory, TCP/IP Sockets oder via) ist. Die restliche Fehlermeldung enthält die aufgerufene Netzwerkbibliotheksfunktion und die von der TDS-Funktion in der zugrunde liegenden Netzwerk-API aufgerufene Funktion. Der mit diesen Fehlern zurückgegebene *pfNative* -Fehlercode ist der Fehlercode aus dem zugrunde liegenden Netzwerkprotokoll Stapel.  
  
 [Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Diese Fehler werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgelöst. Die übrige Fehlermeldung entspricht dem Text der Fehlermeldung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Der mit diesen Fehlern zurückgegebene *pfNative* Code ist die Fehlernummer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen zu einer Liste von Fehlermeldungen (und deren Zahlen), die von zurückgegeben werden können, finden Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Spalten "Description" und "Error" der **sysmmeages** -Systemtabelle in der **Master** -Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](handling-errors-and-messages.md)  
  
  
