---
title: 'Clientprotokolle: Named Pipes-Eigenschaften (Registerkarte „Protokoll“) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1038c92fe24d0629766ba38086e69d0277e9be0f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198550"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Clientprotokolle - Named Pipes-Eigenschaften (Registerkarte Protokoll)
  Verwenden Sie im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager im Dialogfeld **Named Pipes-Eigenschaften** die Registerkarte **Protokoll** , um die Beschreibung der Standardpipe anzuzeigen oder zu ändern. Um eine Verbindung mit einer anderen Pipe herzustellen, geben Sie die Pipe im Dialogfeld **Standardpipe** ein. Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md).  
  
## <a name="options"></a>Tastatur  
 **Standardpipe**  
 Gibt die Standardpipe an, die von der Named Pipes-Netzwerkbibliothek zum Herstellen einer Verbindung mit der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Standardmäßig überwacht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : `\\.\pipe\sql\query`  
  
 Geben Sie `sql\query`  
  
 **Aktiviert**  
 Mögliche Werte sind **Yes** und **No**.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
