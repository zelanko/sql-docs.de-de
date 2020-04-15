---
title: Fehlermeldungen | Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7d632d1d22cd8439a3d787e22301ec06ec4e0d93
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291743"
---
# <a name="error-messages"></a>Fehlermeldungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der Text der vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC-Treiber systemeigener Client zurückgegebenen Nachrichten wird im *MessageText-Parameter* von **SQLGetDiagRec**abgelegt. Die Quelle eines Fehlers wird im Header der Meldung angegeben:  
  
 [Microsoft][ODBC-Treiber-Manager]  
 Diese Fehler werden vom ODBC-Treiber-Manager ausgelöst.  
  
 [Microsoft][ODBC-Cursorbibliothek]  
 Diese Fehler werden von der ODBC-Cursorbibliothek ausgelöst.  
  
 [Microsoft][SQL Server Native Client]  
 Diese Fehler werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vom Native Client ODBC-Treiber ausgelöst. Wenn keine anderen Knoten entweder mit den Namen einer Netzwerkbibliothek oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden sind, trat der Fehler im Treiber auf.  
  
 [Microsoft] [SQL Server Native Client] [*Netz-Transportname*]  
 Diese Fehler werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von der Net-Library ausgelöst, wobei *Net-Transportname* der Anzeigename eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clientnetzwerktransports ist (z. B. Named Pipes, Shared Memory, TCP/IP Sockets oder VIA). Die restliche Fehlermeldung enthält die aufgerufene Netzwerkbibliotheksfunktion und die von der TDS-Funktion in der zugrunde liegenden Netzwerk-API aufgerufene Funktion. Der *pfNative* Fehlercode, der mit diesen Fehlern zurückgegeben wird, ist der Fehlercode aus dem zugrunde liegenden Netzwerkprotokollstapel.  
  
 [Microsoft] [SQL Server Native Client] [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Diese Fehler werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgelöst. Die übrige Fehlermeldung entspricht dem Text der Fehlermeldung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Der *pfNative-Code, der* mit diesen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Fehlern zurückgegeben wird, ist die Fehlernummer von . Weitere Informationen zu einer Liste von Fehlermeldungen (und deren Nummern), die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von zurückgegeben werden können, finden Sie in den Beschreibungs- und Fehlerspalten der **Systemtabelle sysmessages** in der **Masterdatenbank** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
