---
title: Eintragen eines Zielservers bei einem Masterserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f3d0d91de95e82fcd174aa9290e208afda5bef91
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52786212"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Eintragen eines Zielservers bei einem Masterserver
  In diesem Thema wird die Vorgehensweise zum Hinzufügen eines Zielservers zu einer Multiserververwaltungskonfiguration beschrieben. Führen Sie die folgenden Schritte auf dem Masterserver aus. Die Schritte können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects (SMO) ausgeführt werden.  
  
 Informationen zu den Auswirkungen des für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst verwendeten Windows-Kontos auf eine Multiserverumgebung finden Sie unter [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md).  
  
 Die vollständige SSL-Verschlüsselung (Secure Sockets Layer) und die Zertifikatüberprüfung sind für Verbindungen zwischen Masterservern und Zielservern standardmäßig aktiviert. Weitere Informationen finden Sie unter [Festlegen von Verschlüsselungsoptionen auf Zielservern](set-encryption-options-on-target-servers.md).  
  
 **In diesem Thema**  
  
-   **Eintragen eines Zielservers mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>So tragen Sie einen Zielserver ein  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server, der als Masterserver konfiguriert ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserveradministration**, und klicken Sie dann auf **Zielserver hinzufügen**.  
  
3.  Schließen Sie den Zielservererstellungs-Assistenten ab, in dem Sie durch den Prozess geleitet werden.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>So tragen Sie einen Zielserver ein  
  
1.  Verwenden Sie die gespeicherte Prozedur `sp_msx_enlist`.  Weitere Informationen finden Sie unter [Sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
##  <a name="PowerShellProcedure"></a> Verwendung von SQL Server Management Objects (SMO)  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)  
  
  
