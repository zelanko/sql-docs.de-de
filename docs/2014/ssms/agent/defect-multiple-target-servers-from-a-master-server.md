---
title: Vollziehen des Austritts mehrerer Zielserver aus einem Masterserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73d7af5a8f1fba0ec968bac12bf9c936b149f5f9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110510"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Defect Multiple Target Servers from a Master Server
  In diesem Thema wird beschrieben, wie Sie den Austritt mehrerer Zielserver aus einer Multiserver-Verwaltungskonfiguration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]vollziehen. Führen Sie die folgenden Schritte auf dem Masterserver aus.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>So tragen Sie bei einem Masterserver mehrere Zielserver aus  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server, der als Masterserver konfiguriert ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserververwaltung**, und klicken Sie dann auf **Zielserver verwalten**.  
  
3.  Klicken Sie auf **Anweisungen bereitstellen**, und klicken Sie in der Liste **Anweisungstyp** auf **Austragen**.  
  
4.  Führen Sie unter **Empfänger**eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Alle Zielserver** , um alle Zielserver dieses Masterservers auszutragen. Verwenden Sie diese Option, wenn die aktuelle Multiserververwaltungskonfiguration vollständig deinstalliert werden soll.  
  
    -   Klicken Sie auf **Diese Zielserver**, und klicken Sie dann auf das entsprechende Feld **Auswählen** , um einige, aber nicht alle Zielserver dieses Masterservers auszutragen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)   
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)   
 [Vollziehen des Austritts eines Zielservers aus einem Masterserver](defect-a-target-server-from-a-master-server.md)  
  
  
