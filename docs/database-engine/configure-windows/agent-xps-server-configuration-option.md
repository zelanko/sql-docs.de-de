---
title: Agent XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e7e2e655be19ac8f84378930e1dfada525007504
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68013164"
---
# <a name="agent-xps-server-configuration-option"></a>Agent XPs (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Mithilfe der Option **Agent XPs** können Sie die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents auf diesem Server aktivieren. Wenn diese Option nicht aktiviert ist, ist der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nicht verfügbar.  
  
 Wenn Sie den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Agent-Dienst mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools starten, werden diese erweiterten gespeicherten Prozeduren automatisch aktiviert. Weitere Informationen finden Sie unter [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Wenn diese erweiterten gespeicherten Prozeduren nicht aktiviert sind, wird der Inhalt des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Knotens im Objekt-Explorer von Management Studio, unabhängig vom Status des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Diensts, nicht angezeigt.  
  
 Mögliche Werte:  
  
-   **0** gibt an, dass die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents nicht verfügbar sind (Standardeinstellung).  
  
-   **1** gibt an, dass die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verfügbar sind.  
  
 Die Einstellung tritt ohne Beenden und Neustarten des Servers sofort in Kraft.  
  
## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents aktiviert.  

1. Stellen Sie von Microsoft SQL Server Management Studio eine Verbindung mit der Datenbank-Engine her.

2.  Klicken Sie auf der Standardleiste auf **Neue Abfrage**.

3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. 
  
```sql 
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](https://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Diensts](https://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  
