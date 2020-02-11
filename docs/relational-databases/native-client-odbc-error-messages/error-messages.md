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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73783459"
---
# <a name="error-messages"></a>Fehlermeldungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der Text der Nachrichten, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vom Native Client-ODBC-Treiber zurückgegeben werden, wird im *MessageText* -Parameter von **SQLGetDiagRec**abgelegt. Die Quelle eines Fehlers wird im Header der Meldung angegeben:  
  
 [Microsoft][ODBC-Treiber-Manager]  
 Diese Fehler werden vom ODBC-Treiber-Manager ausgelöst.  
  
 [Microsoft][ODBC-Cursorbibliothek]  
 Diese Fehler werden von der ODBC-Cursorbibliothek ausgelöst.  
  
 [Microsoft][SQL Server Native Client]  
 Diese Fehler werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ausgelöst. Wenn keine anderen Knoten entweder mit den Namen einer Netzwerkbibliothek oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden sind, trat der Fehler im Treiber auf.  
  
 Microsoft [SQL Server Native Client] [*Net-TransportName*]  
 Diese Fehler werden von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Netzwerk Bibliothek ausgelöst, wobei *net-TransportName* der Anzeige Name eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Netzwerk Transports (z. b. Named Pipes, Shared Memory, TCP/IP Sockets oder via) ist. Die restliche Fehlermeldung enthält die aufgerufene Netzwerkbibliotheksfunktion und die von der TDS-Funktion in der zugrunde liegenden Netzwerk-API aufgerufene Funktion. Der mit diesen Fehlern zurückgegebene *pfNative* -Fehlercode ist der Fehlercode aus dem zugrunde liegenden Netzwerkprotokoll Stapel.  
  
 Microsoft [SQL Server Native Client] [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Diese Fehler werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgelöst. Die übrige Fehlermeldung entspricht dem Text der Fehlermeldung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Der mit diesen Fehlern zurückgegebene *pfNative* Code ist die Fehlernummer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von. Weitere Informationen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu einer Liste von Fehlermeldungen (und deren Zahlen), die von zurückgegeben werden können, finden Sie in den Spalten "Description" und "Error" der **sysmmeages** -Systemtabelle in der **Master** -Datenbank in. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
