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
manager: craigg
ms.openlocfilehash: b07f2e39421bdeb777af1e31fe414ec1fe2890c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62762425"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Ausführen von Windows PowerShell über SQL Server Management Studio
  Sie können Windows PowerShell-Sitzungen aus dem **Objekt-Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]starten. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] startet Windows PowerShell, lädt die `sqlps` -Modul, und legt den Pfadkontext auf den zugeordneten Knoten in der **Objekt-Explorer** Struktur.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Wenn Sie die Ausführung von PowerShell für ein Objekt im **Objekt-Explorer** angeben, startet [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] eine Windows PowerShell-Sitzung, in denen die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -PowerShell-Snap-Ins geladen und registriert wurden. Der Pfad für die Sitzung ist auf den Speicherort des Objekts, auf das Sie mit der rechten Maustaste geklickt haben, voreingestellt. Wenn Sie beispielsweise im Objekt-Explorer mit der rechten Maustaste auf das Datenbankobjekt [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] klicken und dann **PowerShell starten**auswählen, wird der Windows PowerShell-Pfad folgendermaßen festgelegt:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="run-powershell"></a>Ausführen von PowerShell  
 **So führen Sie PowerShell in SQL Server Management Studio aus**  
  
1.  Öffnen Sie den **Objekt-Explorer**.  
  
2.  Navigieren Sie zum Knoten für das zu verarbeitende Objekt.  
  
3.  Klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **PowerShell starten**aus.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn PowerShell in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]geöffnet wurde, wird das Programm nicht mit Administratorrechten ausgeführt, wodurch einige Aktivitäten möglicherweise verhindert werden, z. B. Aufrufe der WMI.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-PowerShell](sql-server-powershell.md)  
  
  
