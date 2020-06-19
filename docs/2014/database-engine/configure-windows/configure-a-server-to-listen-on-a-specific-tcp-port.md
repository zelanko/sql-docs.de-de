---
title: Konfigurieren eines Servers für das lauschen an einem bestimmten TCP-Port (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfe8a35e9ba0a23edb3fc08833ab015ddbd2f119
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935829"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a>Konfigurieren eines Servers zur Überwachung eines bestimmten TCP-Ports (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie eine Instanz der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] konfiguriert wird, um mit dem SQL Server-Konfigurations-Manager einen bestimmten festen Port zu überwachen. Falls aktiviert, überwacht die Standardinstanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] TCP-Port 1433. Benannte Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssEW](../../includes/ssew-md.md)] sind für dynamische Ports konfiguriert. Dies bedeutet, dass sie einen verfügbaren Port auswählen, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst gestartet wird. Wenn Sie die Verbindung mit einer benannten Instanz über eine Firewall herstellen, konfigurieren Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] so, dass an einem bestimmten Port gelauscht wird, damit der entsprechende Port in der Firewall geöffnet werden kann.  
  
 Weitere Informationen zu den Standardeinstellungen der Windows-Firewall und eine Beschreibung der TCP-Ports, die sich auf Datenbank-Engine, Analysis Services, Reporting Services und Integration Services auswirken, finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
> [!TIP]  
>  Wenn Sie eine Portnummer auswählen, informieren [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) Sie sich über eine Liste der Portnummern, die bestimmten Anwendungen zugewiesen sind. Wählen Sie eine nicht zugewiesene Portnummer aus. Weitere Informationen finden Sie unter [Der dynamische Standardportbereich für TCP/IP hat sich in Windows Vista und Windows Server 2008 geändert](https://support.microsoft.com/kb/929851).  
  
> [!WARNING]  
>  Nach einem Neustart lauscht die Datenbank-Engine an einem neuen Port. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browserdienst überwacht jedoch die Registrierung und meldet die neue Portnummer, sobald die Konfiguration geändert wird, obwohl die Portnummer von der Datenbank-Engine u. U. gar nicht verwendet wird. Starten Sie die Datenbank-Engine erneut, um Konsistenz zu gewährleisten und Verbindungsfehler zu vermeiden.  
  
 **In diesem Thema**  
  
-   **So konfigurieren Sie einen Server zum Lauschen an einem bestimmten TCP-Port**  
  
     [SQL Server-Konfigurations-Manager](#SSMSProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a>So weisen Sie der SQL Server-Datenbank-Engine einen TCP/IP-Port zu  
  
1.  Erweitern Sie in SQL Server-Konfigurations-Manager im Konsolenfenster **SQL Server Netzwerkkonfiguration**, erweitern Sie ** \<instance name> Protokolle für **, und doppelklicken Sie dann auf **TCP/IP**.  
  
2.  Im Dialogfeld **TCP/IP-Eigenschaften** auf der Registerkarte **IP-Adressen** werden mehrere IP-Adressen im Format **IP1**, **IP2**und bis zu **IPAll**angezeigt. Eine dieser Angaben ist die IP-Adresse des Loopbackadapters (127.0.0.1). Bei den anderen IP-Adressen handelt es sich um die einzelnen IP-Adressen auf dem Computer. Klicken Sie mit der rechten Maustaste auf die einzelnen Adressen, und klicken Sie dann auf **Eigenschaften**, um die IP-Adresse zu identifizieren, die Sie konfigurieren möchten.  
  
3.  Wenn im Dialogfeld **Dynamische TCP-Ports** durch den Wert **0**angezeigt wird, dass [!INCLUDE[ssDE](../../includes/ssde-md.md)] dynamische Ports überwacht, löschen Sie die Null.  
  
4.  Geben Sie im Feld **Eigenschaften** von **IP**_n_ im Feld **TCP-Port** die Port Nummer ein, an der diese IP-Adresse lauschen soll, und klicken Sie dann auf **OK**.  
  
5.  Klicken Sie im Konsolenbereich auf **SQL Server-Dienste**.  
  
6.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server (** \<instance name> **)** , und klicken Sie dann auf **neu starten**, um anzuhalten und neu zu starten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Nachdem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert haben, dass an einem bestimmten Port gelauscht wird, gibt es drei Möglichkeiten, um über die Clientanwendung eine Verbindung mit einem bestimmten Port herzustellen:  
  
-   Führen Sie auf dem Server den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst aus, um die Verbindung zur Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] nach dem Namen herzustellen.  
  
-   Erstellen Sie einen Alias auf dem Client, und geben Sie die Portnummer an.  
  
-   Programmieren Sie den Client so, dass die Verbindung mithilfe einer benutzerdefinierten Verbindungszeichenfolge hergestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen oder Löschen eines Serveralias für die Verwendung durch einen Client &#40;SQL Server-Konfigurations-Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
