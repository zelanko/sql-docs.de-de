---
title: MSSQLSERVER_21892 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4ca49ebb4a7481fc7fd23e916d10a185632280cd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68056652"
---
# <a name="mssqlserver_21892"></a>MSSQLSERVER_21892
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21892|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21892|  
|Meldungstext|Von "sys.availability_replicas" auf dem primären Verfügbarkeitsgruppenobjekt, das dem Namen "%s" des virtuellen Netzwerks zugeordnet ist, können keine Servernamen der Mitgliedsreplikate abgefragt werden: Fehler =%d, Fehlermeldung =%s.|  
  
## <a name="explanation"></a>Erklärung  
**sp_validate_replica_hosts_as_publishers** fragt das aktuelle Primäre der Verfügbarkeitsgruppe ab, das dem umgeleiteten Verleger zugeordnet ist, um die Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu bestimmen, die die Mitgliedsreplikate hosten.  Wenn diese Abfrage fehlschlägt, wird Fehler 21892 zurückgegeben.  
  
In dem **sp_validate_replica_hosts_as_publishers**-Aufruf wird der temporäre Verbindungsserver in der Regel zum ersten Mal verwendet. Wenn Verbindungsprobleme vorliegen, ist es daher wahrscheinlich, dass diese zuerst beim Aufruf von **sp_validate_replica_hosts_as_publishers** auftreten. Im Gegensatz zu **sp_validate_redirected_publisher** verwendet der von **sp_validate_replica_hosts_as_publishers** verwendete Verbindungsserver beim Herstellen einer Verbindung mit Replikathost der Verfügbarkeitsgruppen immer die Anmeldeinformationen des Aufrufers.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie beim Ausführen dieser gespeicherten Prozedur sicher, dass Sie eine Anmeldung verwenden, die bei allen Replikaten gültig ist. Die Anmeldung muss dazu autorisiert sein, Verfügbarkeitsgruppenmetadatentabellen abzufragen sowie die Abonnementmetadatentabellen im Verlegerdatenbankreplikat abzufragen.  
  
Überprüfen Sie ursprünglich angegebene Fehlermeldung, um die Fehlerursache zu bestimmen und entsprechende Korrekturmaßnahmen zu ergreifen.  
  
