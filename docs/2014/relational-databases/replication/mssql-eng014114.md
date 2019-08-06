---
title: MSSQL_ENG014114 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014114 error
ms.assetid: f5f04590-e1c6-40d8-ab2b-98c791a0fc44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0afebe3d8e974ac4920a6f75bf544a13027b360e
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811002"
---
# <a name="mssql_eng014114"></a>MSSQL_ENG014114
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14114|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|'%1!s!' ist nicht als Verteiler konfiguriert.|  
  
## <a name="explanation"></a>Erklärung  
 Wenn in der Fehlermeldung eine konkrete Instanz und nicht 'null' angegeben wird, wurde die genannte Instanz nicht so konfiguriert, dass sie als Verteiler erkannt wird.  
  
 Wenn in der Fehlermeldung als Verteiler 'null' angegeben wird, ist in der **master** -Datenbank kein Eintrag für den lokalen Server vorhanden, oder der Eintrag ist falsch (weil der Computer z. B. umbenannt worden ist). Die Replikation erwartet, dass alle Server in einer Topologie mithilfe des Computernamens mit einem optionalen Instanznamen (bei Clusterinstanzen mithilfe des virtuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Servernamens mit dem optionalen Instanznamen) registriert werden. Damit die Replikation ordnungsgemäß funktioniert, muss der von `SELECT @@SERVERNAME` für jeden Server in der Topologie zurückgegebene Wert mit dem Computernamen bzw. dem virtuellen Servernamen mit dem optionalen Instanznamen übereinstimmen.  
  
 Die Replikation wird nicht unterstützt, wenn Sie eine der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen über die IP-Adresse oder den vollqualifizierten Domänennamen registriert haben. Dieser Fehler kann ausgelöst werden, wenn beim Konfigurieren der Replikation eine der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen über die IP-Adresse oder den vollqualifizierten Domänennamen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] registriert war.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn in der Fehlermeldung eine konkrete Instanz genannt wird, konfigurieren Sie den Server als Verteiler. Weitere Informationen finden Sie unter [Konfigurieren der Verteilung](configure-distribution.md).  
  
 Wenn in der Fehlermeldung keine konkrete Instanz angegeben wird ('null'), überprüfen Sie, dass die Verteilerinstanz ordnungsgemäß registriert ist. Wenn der Netzwerkname des Computers und der Name der SQL Server-Instanz nicht identisch sind, gehen Sie wie folgt vor:  
  
-   Fügen Sie den SQL Server-Instanznamen als gültigen Netzwerknamen hinzu. Eine Möglichkeit, einen alternativen Netzwerknamen festzulegen, besteht darin, diesen Namen der lokalen Hostdatei hinzuzufügen. Die lokale Hostdatei befindet sich standardmäßig in WINDOWS\system32\drivers\etc oder WINNT\system32\drivers\etc. Weitere Informationen finden Sie in der Windows-Dokumentation.  
  
     Wenn der Computername z. B. comp1 ist und die IP-Adresse des Computers 10.193.17.129 lautet und wenn der Instanzname inst1/instname ist, ist der Hostdatei der folgende Eintrag hinzuzufügen:  
  
     10.193.17.129 inst1  
  
-   Deaktivieren Sie die Verteilung, registrieren Sie die Instanz, und stellen Sie dann die Verteilung wieder her. Wenn der Wert von @@SERVERNAME für eine nicht gruppierte Instanz nicht korrekt ist, führen Sie die folgenden Schritte aus:  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     Nachdem Sie die gespeicherte Prozedur [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)ausgeführt haben, müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst neu starten, damit die Änderung an @@SERVERNAME wirksam wird.  
  
     Wenn der @@SERVERNAME-Wert für eine in einem Cluster befindliche Instanz falsch ist, müssen Sie mithilfe der Clusterverwaltung den Namen ändern. Weitere Informationen finden Sie unter [ Always On-Failoverclusterinstanzen (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
