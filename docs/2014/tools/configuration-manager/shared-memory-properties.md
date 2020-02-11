---
title: Shared Memory-Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bea56ada3ef490225fd08892128abb482b9342a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62999536"
---
# <a name="shared-memory-properties"></a>Shared Memory-Eigenschaften
  Verwenden Sie die Seite **Protokoll**des Dialogfeldes **Eigenschaften von Shared Memory** , um das Shared Memory-Protokoll zu aktivieren oder zu deaktivieren. Shared Memory ist das am einfachsten zu verwendende Protokoll. Es weist keine konfigurierbaren Einstellungen auf. Da Clients, die das Shared Memory-Protokoll verwenden, nur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit einer-Instanz herstellen können, die auf demselben Computer ausgeführt wird, ist Sie für die meisten Daten Bankaktivitäten nicht hilfreich Verwenden Sie das Shared Memory-Protokoll zur Problembehandlung, wenn Sie vermuten, dass die anderen Protokolle nicht ordnungsgemäß konfiguriert sind.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss neu gestartet werden, um das Protokoll zu aktivieren oder zu deaktivieren.  
  
## <a name="options"></a>Tastatur  
 **Aktiviert**  
 Mögliche Werte sind **Yes** und **No**. Das Shared Memory-Protokoll ist standardmäßig aktiviert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
