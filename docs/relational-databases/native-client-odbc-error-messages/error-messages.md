---
description: Fehlermeldungen
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a814c4b1c1d0de7843803863f7587cbc11ddcf16
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438485"
---
# <a name="error-messages"></a>Fehlermeldungen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der Text der Nachrichten, die vom Native Client-ODBC-Treiber zurückgegeben werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird im *MessageText* -Parameter von **SQLGetDiagRec** abgelegt. Die Quelle eines Fehlers wird im Header der Meldung angegeben:  
  
 [Microsoft][ODBC-Treiber-Manager]  
 Diese Fehler werden vom ODBC-Treiber-Manager ausgelöst.  
  
 [Microsoft][ODBC-Cursorbibliothek]  
 Diese Fehler werden von der ODBC-Cursorbibliothek ausgelöst.  
  
 [Microsoft][SQL Server Native Client]  
 Diese Fehler werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ausgelöst. Wenn keine anderen Knoten entweder mit den Namen einer Netzwerkbibliothek oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden sind, trat der Fehler im Treiber auf.  
  
 Microsoft [SQL Server Native Client] [*Net-TransportName*]  
 Diese Fehler werden von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Netzwerk Bibliothek ausgelöst, wobei *net-TransportName* der Anzeige Name eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Netzwerk Transports (z. b. Named Pipes, Shared Memory, TCP/IP Sockets oder via) ist. Die restliche Fehlermeldung enthält die aufgerufene Netzwerkbibliotheksfunktion und die von der TDS-Funktion in der zugrunde liegenden Netzwerk-API aufgerufene Funktion. Der mit diesen Fehlern zurückgegebene *pfNative* -Fehlercode ist der Fehlercode aus dem zugrunde liegenden Netzwerkprotokoll Stapel.  
  
 Microsoft [SQL Server Native Client] [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Diese Fehler werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgelöst. Die übrige Fehlermeldung entspricht dem Text der Fehlermeldung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Der mit diesen Fehlern zurückgegebene *pfNative* Code ist die Fehlernummer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen zu einer Liste von Fehlermeldungen (und deren Zahlen), die von zurückgegeben werden können, finden Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Spalten "Description" und "Error" der **sysmmeages** -Systemtabelle in der **Master** -Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
