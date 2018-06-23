---
title: Shared Memory-Eigenschaften | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3ff71e8b8e4bfd3de68adc401c4871be92614acc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149528"
---
# <a name="shared-memory-properties"></a>Shared Memory-Eigenschaften
  Verwenden Sie die Seite **Protokoll**des Dialogfeldes **Eigenschaften von Shared Memory** , um das Shared Memory-Protokoll zu aktivieren oder zu deaktivieren. Shared Memory ist das am einfachsten zu verwendende Protokoll. Es weist keine konfigurierbaren Einstellungen auf. Da Clients, die das Shared Memory-Protokoll verwenden, nur eine Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen können, die auf demselben Computer ausgeführt wird, ist dieses Protokoll bei den meisten Datenbankaktivitäten nicht hilfreich. Verwenden Sie das Shared Memory-Protokoll zur Problembehandlung, wenn Sie vermuten, dass die anderen Protokolle nicht ordnungsgemäß konfiguriert sind.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss neu gestartet werden, um das Protokoll zu aktivieren oder zu deaktivieren.  
  
## <a name="options"></a>Tastatur  
 **Enabled**  
 Mögliche Werte sind **Yes** und **No**. Das Shared Memory-Protokoll ist standardmäßig aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  