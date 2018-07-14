---
title: Durchführen von Transaktionen in ADOMD.NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04157786e3a3d9349c2f1e324291a3a0bda5928d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167593"
---
# <a name="performing-transactions-in-adomdnet"></a>Ausführen von Transaktionen in ADOMD.NET
  In ADOMD.NET verwenden Sie das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Objekt, um den Transaktionskontext für ein gegebenes <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt zu verwalten. Diese Funktionalität ermöglicht es Ihnen, mehrere Befehle vom gleichen Kontext auszuführen. Jeder Befehl liest die gleichen Daten, ohne dass sich die gelesenen Daten zwischen jeder Befehlsausführung ändern.  
  
> [!NOTE]  
>  Die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Klasse ist die Implementierung der `System.Data.IDbTransaction`-Schnittstelle, Teil der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Klassenbibliothek und wird von allen .NET Framework-Datenanbietern unterstützt, die Transaktionen unterstützen.  
  
 Um Dirty Reads zu vermeiden, unterstützt das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Objekt nur Read Committed-Transaktionen, in denen während des Lesens der Daten freigegebene Sperren aufrecht erhalten werden.  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> wird verwendet, um die Transaktion zu starten. Um die Transaktion zu verwenden, werden Befehle dann gegen die Verbindung ausgeführt, die die Transaktion gestartet hat. Wenn Sie mit der Transaktion fertig sind, können Sie entweder ein Rollback oder ein Commit für die Transaktion ausführen.  
  
## <a name="starting-a-transaction"></a>Starten einer Transaktion  
 Sie erstellen eine Instanz des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Objekts, indem Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts aufrufen. Im folgenden Beispiel wird veranschaulicht, wie eine Instanz des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Objekts erstellt wird:  
  
```  
Dim objTransaction As AdomdTransaction = objConnection.BeginTransaction()  
AdomdTransaction objTransaction = objConnection.BeginTransaction();  
```  
  
## <a name="rolling-back-a-transaction"></a>Ausführen von Rollbacks für eine Transaktion  
 Um ein Rollback für eine bestehende, unvollständige Transaktion auszuführen, rufen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Rollback%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Objekts auf. Wenn Sie diese Methode für eine bestehende, vollständige Transaktion aufrufen, wird eine Ausnahme ausgelöst.  
  
## <a name="committing-a-transaction"></a>Commitausführung für eine Transaktion  
 Nachdem Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A>-Methode aufgerufen haben, um eine Transaktion zu starten, können Sie die Transaktion abschließen, indem Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Commit%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>-Objekts aufrufen. Wird diese Methode für eine bestehende, vollständige Transaktion aufgerufen, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufbauen von Verbindungen in ADOMD.NET](connections-in-adomd-net.md)   
 [ADOMD.NET-Clientprogrammierung](adomd-net-client-programming.md)  
  
  
