---
title: MSSQL_ENG018456 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 343abeb430a09eb1dcd6375266bb314e5f61c509
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149037"
---
# <a name="mssqleng018456"></a>MSSQL_ENG018456
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|18456|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Fehler bei der Anmeldung für den Benutzer '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Erklärung  
 Der Fehler MSSQL_ENG018456 wird ausgelöst, wenn ein Anmeldeversuch einen Fehler erzeugt. Enthält die Fehlermeldung das Konto **distributor_admin** (Fehler bei der Anmeldung des Benutzers 'distributor_admin'.), liegt das Problem an einem Konto, das durch die Replikation verwendet wird. Die Replikation erstellt einen Remoteserver **repl_distributor**, der die Kommunikation zwischen dem Verteiler und dem Verleger ermöglicht. Die Anmeldung **distributor_admin** wird diesem Remoteserver zugeordnet und muss ein gültiges Kennwort besitzen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass Sie ein Kennwort für dieses Konto angegeben haben. Weitere Informationen finden Sie unter [Schützen des Verteilers](security/secure-the-distributor.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  