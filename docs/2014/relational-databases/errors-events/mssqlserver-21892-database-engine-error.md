---
title: MSSQLSERVER_21892 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18916e8287841015727c37ed8833fbc29b1e6ba2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62869147"
---
# <a name="mssqlserver_21892"></a>MSSQLSERVER_21892
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21892|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21892|  
|Meldungstext|„sys.availability_replicas“ kann beim primären Replikat der Verfügbarkeitsgruppe, das dem virtuellen Netzwerknamen '%s' für die Servernamen der Mitgliedsreplikate zugeordnet ist, nicht abgefragt werden: Fehler =%d, Fehlermeldung =% s.'|  
  
## <a name="explanation"></a>Erklärung  
 
  `sp_validate_replica_hosts_as_publishers` fragt das aktuelle Primäre der Verfügbarkeitsgruppe ab, das dem umgeleiteten Verleger zugeordnet ist, um die Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu bestimmen, welche die Mitgliedsreplikate hosten.  Wenn diese Abfrage fehlschlägt, wird Fehler 21892 zurückgegeben.  
  
 In dem `sp_validate_replica_hosts_as_publishers`Aufruf wird der temporäre Verbindungsserver in der Regel zum ersten Mal verwendet. Wenn Verbindungsprobleme vorliegen, ist es daher wahrscheinlich, dass diese zuerst beim Aufruf von `sp_validate_replica_hosts_as_publishers` augenscheinlich werden. Im Gegensatz zu `sp_validate_redirected_publisher` verwendet der von `sp_validate_replica_hosts_as_publishers` verwendete Verbindungsserver beim Herstellen einer Verbindung mit Replikathost der Verfügbarkeitsgruppen immer die Anmeldeinformationen des Aufrufers.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie beim Ausführen dieser gespeicherten Prozedur sicher, dass Sie eine Anmeldung verwenden, die bei allen Replikaten gültig ist. Die Anmeldung muss dazu autorisiert sein, Verfügbarkeitsgruppenmetadatentabellen abzufragen sowie die Abonnementmetadatentabellen im Verlegerdatenbankreplikat abzufragen.  
  
 Überprüfen Sie ursprünglich angegebene Fehlermeldung, um die Fehlerursache zu bestimmen und entsprechende Korrekturmaßnahmen zu ergreifen.  
  
  
