---
title: Implementierung des übergeordneten Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parent packages [Integration Services]
ms.assetid: d8f94830-fa27-4151-88df-cbdc6bf0fc80
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2cec1f30ba728f1cf3b808acb2fb362e21d259a4
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058158"
---
# <a name="implementation-of-the-parent-package"></a>Implementierung des übergeordneten Pakets
  Beim Lastenausgleich von SSIS-Paketen über verschiedene Server ist der nächste Schritt das Erstellen des übergeordneten Pakets, nachdem die untergeordneten Pakete erstellt, bereitgestellt und für ihre Ausführung Remoteaufträge des SQL Server-Agents erstellt wurden. Das übergeordnete Paket enthält dann mehrere Tasks Auftrag des SQL Server-Agents ausführen, wobei die einzelnen Tasks jeweils einen Auftrag des SQL Server-Agents zum Ausführen eines der untergeordneten Pakete aufrufen. Die im übergeordneten Paket enthaltenen Tasks Auftrag des SQL Server-Agents ausführen führen wiederum die verschiedenen Aufträge des SQL Server-Agents aus. Jeder einzelne Task des übergeordneten Pakets enthält Informationen, z. B. über das Herstellen einer Verbindung zum Remoteserver sowie über den auf diesem Server auszuführenden Auftrag. Weitere Informationen finden Sie unter [Execute SQL Server Agent Job Task](control-flow/execute-sql-server-agent-job-task.md).  
  
 Um das übergeordnete Paket zu identifizieren, das untergeordnete Pakete ausführt, klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] mit der rechten Maustaste auf das Paket in Projektmappen-Explorer, und klicken Sie dann auf **Einstiegspunktpaket**.  
  
## <a name="listing-child-packages"></a>Auflisten untergeordneter Pakete  
 Wenn Sie ein Projekt, das ein übergeordnetes Paket und untergeordnete Pakete enthält, über den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitstellen, können Sie eine Liste der untergeordneten Pakete anzeigen lassen, die von den übergeordneten Paketen ausgeführt werden. Wenn Sie das übergeordnete Paket ausführen, wird automatisch für das übergeordnete Paket ein Bericht **Übersicht** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]erstellt. Der Bericht führt die untergeordneten Pakete auf, die vom Task "Paket ausführen" ausgeführt wurden, der sich im übergeordneten Paket befindet. Dies wird im folgenden Bild gezeigt.  
  
 ![Übersichtsbericht mit einer Liste von untergeordneten Paketen](media/overviewreport-childpackagelisting.png "Overview Report with list of child packages")  
  
 Weitere Informationen zum Zugreifen auf den Bericht **Übersicht** finden Sie unter [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
## <a name="precedence-constraints-in-the-parent-package"></a>Rangfolgeneinschränkungen im übergeordneten Paket  
 Wenn Sie im übergeordneten Paket zwischen den Tasks "Task 'Auftrag des SQL Server-Agents ausführen'" Rangfolgeneinschränkungen erstellen, steuern diese nur die Startzeit der Aufträge des SQL Server-Agents auf den Remoteservern. Rangfolgeneinschränkungen können keine Informationen bezüglich des Erfolgs oder Misserfolgs der untergeordneten Pakete empfangen, die in den Schritten der Aufträge des SQL Server-Agents ausgeführt werden.  
  
 Das bedeutet, dass der Erfolg oder Misserfolg eines untergeordneten Pakets nicht an das übergeordnete Paket weitergegeben wird, da die einzige Funktion des Tasks Auftrag des SQL Server-Agents ausführen im übergeordneten Paket darin besteht, den Auftrag des SQL Server-Agents für die Ausführung des untergeordneten Pakets anzufordern. Nach dem erfolgreichen Aufruf des Auftrags des SQL Server-Agents empfängt das übergeordnete Paket das Ergebnis <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success>.  
  
 Der Misserfolg dieses Szenarios bedeutet nur, dass beim Remoteaufruf des Tasks Auftrag des SQL Server-Agents ein Fehler aufgetreten ist. Dies kann z. B. vorkommen, wenn der Remoteserver ausgefallen ist und der Agent nicht antwortet. Allerdings kann das übergeordnete Paket seinen Task erfolgreich abschließen, solange der Agent ausgelöst wird.  
  
> [!NOTE]  
>  Sie können den Task „SQL ausführen“ verwenden, in dem die Transact-SQL-Anweisung **sp_start_job N'package_name'** enthalten ist. Weitere Informationen finden Sie unter [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
## <a name="debugging-environment"></a>Debugging-Umgebung  
 Verwenden Sie beim Testen des übergeordneten Pakets die Umgebung des Designers zum Debuggen, indem Sie im Menü Debuggen auf Debuggen starten klicken oder F5 drücken. Alternativ können Sie das Eingabeaufforderungs-Hilfsprogramm **dtexec**verwenden. Weitere Informationen finden Sie unter [dtexec Utility](packages/dtexec-utility.md).  
  
  
