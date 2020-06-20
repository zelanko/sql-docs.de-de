---
title: Ausführen von Windows PowerShell über SQL Server Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20a5d709cf570aad6e5805d5bf57428a9f7e7ae6
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960188"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Ausführen von Windows PowerShell über SQL Server Management Studio
  Sie können Windows PowerShell-Sitzungen aus dem **Objekt-Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]starten. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]gestartet Windows PowerShell, lädt das `sqlps` -Modul und legt den Pfad Kontext auf den zugeordneten Knoten in der **Objekt-Explorer** Struktur fest.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Wenn Sie die Ausführung von PowerShell für ein Objekt in **Objekt-Explorer**angeben, wird von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] eine Windows PowerShell-Sitzung gestartet, in der die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Snap-Ins geladen und registriert wurden. Der Pfad für die Sitzung ist auf den Speicherort des Objekts, auf das Sie mit der rechten Maustaste geklickt haben, voreingestellt. Wenn Sie beispielsweise im Objekt-Explorer mit der rechten Maustaste auf das Datenbankobjekt [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] klicken und dann **PowerShell starten**auswählen, wird der Windows PowerShell-Pfad folgendermaßen festgelegt:  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a>So führen Sie PowerShell in SQL Server Management Studio aus 
  
1.  Öffnen Sie **Objekt-Explorer**.  
  
2.  Navigieren Sie zum Knoten für das zu verarbeitende Objekt.  
  
3.  Klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **PowerShell starten**aus.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn PowerShell in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]geöffnet wurde, wird das Programm nicht mit Administratorrechten ausgeführt, wodurch einige Aktivitäten möglicherweise verhindert werden, z. B. Aufrufe der WMI.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-PowerShell](sql-server-powershell.md)  
