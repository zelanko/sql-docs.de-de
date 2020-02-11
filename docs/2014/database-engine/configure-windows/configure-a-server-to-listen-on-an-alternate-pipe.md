---
title: Konfigurieren eines Servers für das lauschen an einer alternativen Pipe (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 68b082d125650d150676d545cfdf6ab27bd25da2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62813523"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a>Konfigurieren eines Servers für die Überwachung einer alternativen Pipe (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie einen Server konfigurieren können, um eine alternative Pipe in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe des SQL Server-Konfigurations-Managers überwachen zu können. Standardmäßig lauscht die Standardinstanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] an der Named Pipe \\\\.\pipe\sql\query. Benannte Instanzen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [!INCLUDE[ssEW](../../includes/ssew-md.md)] überwachen andere Pipes.  
  
 Es gibt drei Möglichkeiten, mit einer Clientanwendung eine Verbindung mit einer bestimmten benannten Pipe herzustellen:  
  
-   Ausführen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienstes auf dem Server  
  
-   Erstellen eines Alias auf dem Client unter Angabe der benannten Pipe  
  
-   Programmieren Sie den Client so, dass die Verbindung mithilfe einer benutzerdefinierten Verbindungszeichenfolge hergestellt wird.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a>So konfigurieren Sie die von der SQL Server-Datenbank-Engine verwendete Named Pipe  
  
1.  Erweitern Sie im SQL Server-Konfigurations-Manager im Konsolenbereich **SQL Server-Netzwerkkonfiguration**, und klicken Sie dann auf **Protokolle für** *\<Instanzname>*.  
  
2.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **Named Pipes**, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Geben Sie auf der Registerkarte **Protokoll** im Feld **Pipename** die Pipe ein, an der [!INCLUDE[ssDE](../../includes/ssde-md.md)] gelauscht werden soll, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie im Konsolenbereich auf **SQL Server-Dienste**.  
  
5.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server (**\<Instanzname>**)** , und klicken Sie dann auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **neu starten**, um anzuhalten und neu zu starten.  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine alternative Pipe überwacht, können Sie auf drei Arten mit einer Clientanwendung eine Verbindung zu einer bestimmten benannten Pipe herstellen:  
  
-   Ausführen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienstes auf dem Server  
  
-   Erstellen eines Alias auf dem Client unter Angabe der benannten Pipe  
  
-   Programmieren Sie den Client so, dass die Verbindung mithilfe einer benutzerdefinierten Verbindungszeichenfolge hergestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen oder Löschen eines Serveralias für die Verwendung durch einen Client &#40;SQL Server-Konfigurations-Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [Server-Netzwerkkonfiguration](server-network-configuration.md)  
  
  
