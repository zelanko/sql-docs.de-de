---
title: Konfigurieren eines Servers für das Überwachen eines bestimmten TCP-Ports | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/25/2017
ms.prod: sql
ms.prod_service: high-availability
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
manager: craigg
ms.openlocfilehash: a990088feab172954f82b3be34a505202626c7d0
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132800"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port"></a>Konfigurieren eines Servers für das Überwachen eines bestimmten TCP-Ports
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In diesem Thema wird beschrieben, wie eine Instanz der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] konfiguriert wird, um mit dem SQL Server-Konfigurations-Manager einen bestimmten festen Port zu überwachen. Falls aktiviert, überwacht die Standardinstanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] TCP-Port 1433. Benannte Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssEW](../../includes/ssew-md.md)] sind für [dynamische Ports](../../tools/configuration-manager/tcp-ip-properties-ip-addresses-tab.md)konfiguriert. Dies bedeutet, dass sie einen verfügbaren Port auswählen, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst gestartet wird. Wenn Sie die Verbindung mit einer benannten Instanz über eine Firewall herstellen, konfigurieren Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] so, dass an einem bestimmten Port gelauscht wird, damit der entsprechende Port in der Firewall geöffnet werden kann.  

Da Port 1433 der bekannte Standard für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist, legen einige Organisationen fest, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Portnummer geändert werden soll, um die Sicherheit zu verbessern. Dies kann in einigen Umgebungen hilfreich sein. Allerdings ermöglicht die TCP/IP-Architektur, dass ein [Portscanner](https://wikipedia.org/wiki/Port_scanner) nach offenen Ports fragt. Deshalb stellt das Ändern der Portnummer keine robuste Sicherheitsmaßnahme dar.

 Weitere Informationen zu den Standardeinstellungen der Windows-Firewall und eine Beschreibung der TCP-Ports, die sich auf Datenbank-Engine, Analysis Services, Reporting Services und Integration Services auswirken, finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
> [!TIP]  
>  Beachten Sie bei der Auswahl von Portnummern die Liste registrierter Ports, die bestimmten Anwendungen fest zugeordnet sind. Diese Liste finden Sie auf der Website [https://www.iana.org/assignments/port-numbers](https://www.iana.org/assignments/port-numbers). Wählen Sie eine nicht zugewiesene Portnummer aus. Weitere Informationen finden Sie unter [Der dynamische Standardportbereich für TCP/IP hat sich in Windows Vista und Windows Server 2008 geändert](https://support.microsoft.com/kb/929851).  
  
> [!WARNING]  
>  Nach einem Neustart lauscht die Datenbank-Engine an einem neuen Port. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browserdienst überwacht jedoch die Registrierung und meldet die neue Portnummer, sobald die Konfiguration geändert wird, obwohl die Portnummer von der Datenbank-Engine u. U. gar nicht verwendet wird. Starten Sie die Datenbank-Engine erneut, um Konsistenz zu gewährleisten und Verbindungsfehler zu vermeiden.  
  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a>So weisen Sie der SQL Server-Datenbank-Engine einen TCP/IP-Port zu  
  
1.  Erweitern Sie im Konsolenbereich des SQL Server-Konfigurations-Managers **SQL Server-Netzwerkkonfiguration** und **Protokolle für \<Instanzname>**. Klicken Sie dann doppelt auf **TCP/IP**.  
  
    > [!NOTE]  
    >  Wenn Sie Probleme beim Öffnen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers haben, lesen Sie die Informationen unter [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md).  
  
2.  Im Dialogfeld **TCP/IP-Eigenschaften** auf der Registerkarte **IP-Adressen** werden mehrere IP-Adressen im Format **IP1**, **IP2**und bis zu **IPAll**angezeigt. Eine dieser Angaben ist die IP-Adresse des Loopbackadapters (127.0.0.1). Bei den anderen IP-Adressen handelt es sich um die einzelnen IP-Adressen auf dem Computer. (Wahrscheinlich werden sowohl IPv4- als auch IPv6-Adressen angezeigt.) Klicken Sie mit der rechten Maustaste auf die einzelnen Adressen, und klicken Sie dann auf **Eigenschaften**, um die IP-Adresse zu identifizieren, die Sie konfigurieren möchten.  
  
3.  Wenn im Dialogfeld **Dynamische TCP-Ports** durch den Wert **0**angezeigt wird, dass [!INCLUDE[ssDE](../../includes/ssde-md.md)] dynamische Ports überwacht, löschen Sie die Null.  
  
     ![TCP_Ports](../../database-engine/configure-windows/media/tcp-ports.png "TCP_ports")  
  
4.  Geben Sie im Dialogfeld **Eigenschaften** von **IP**_n_ im Feld **TCP-Port** box, type the port number you want this Eigenschaften von IP address to listen on, and then click **OK**. Sie können mehrere Ports angegeben, indem Sie sie durch ein Komma trennen.

    > [!NOTE] 
    > Wenn die Einstellung **Alle überwachen** auf der Registerkarte **Protokoll** auf „Ja“ festgelegt ist, werden nur die Werte **TCP Port** (TCP-Port) und **TCP Dynamic Port** (Dynamischer TCP-Port) unter **IPAll** verwendet, und individuelle **IP**_n_-Abschnitte werden ignoriert. Wenn die Einstellung **Alle überwachen** auf „Nein“ festgelegt ist, werden die Werte**TCP Port** und **TCP Dynamic Port** unter **IPAll** ignoriert, und die Einstellungen **TCP Port**, **TCP Dynamic Port** und **Enabled** (Aktiviert) werden stattdessen für die jeweiligen **IP**_n_-Abschnitte verwendet.
    > Jeder **IP**_n_-Abschnitt verfügt über die Einstellung **Aktiviert** mit dem Standardwert „Nein“, wodurch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diese IP-Adresse ignoriert, auch wenn dafür ein Port definiert ist.  
  
5.  Klicken Sie im Konsolenbereich auf **SQL Server-Dienste**.  
  
6.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server (**\<Instanzname>**)**, und klicken Sie dann auf **Neu starten**, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu beenden und neu zu starten.  
  
## <a name="connecting"></a>Verbindung  
Nachdem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert haben, dass an einem bestimmten Port gelauscht wird, gibt es drei Möglichkeiten, um über die Clientanwendung eine Verbindung mit einem bestimmten Port herzustellen:  
  
-   Führen Sie auf dem Server den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst aus, um die Verbindung zur Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] nach dem Namen herzustellen.  
-   Erstellen Sie einen Alias auf dem Client, und geben Sie die Portnummer an.  
-   Programmieren Sie den Client so, dass die Verbindung mithilfe einer benutzerdefinierten Verbindungszeichenfolge hergestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen oder Löschen eines Serveralias für die Verwendung durch einen Client &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [SQL Server-Browserdienst](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
