---
title: Clientprotokolle - Named Pipes-Eigenschaften (Registerkarte Protokoll)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: ddd0702ca583dbbaf89da470cf7a07700c873c9c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306538"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Clientprotokolle - Named Pipes-Eigenschaften (Registerkarte Protokoll)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Verwenden Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Configuration Manager im Dialogfeld **Named Pipes Properties** (Named Pipes-Eigenschaften) die Registerkarte **Protokoll**, um die Beschreibung der Standardpipe anzuzeigen oder zu bearbeiten. Um eine Verbindung mit einer anderen Pipe herzustellen, geben Sie die Pipe im Dialogfeld **Standardpipe** ein. Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Creating a Valid Connection String Using Named Pipes](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## <a name="options"></a>Tastatur  
 **Standardpipe**  
 Gibt die Standardpipe an, die von der Named Pipes-Netzwerkbibliothek zum Herstellen einer Verbindung mit der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Standardmäßig überwacht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : `\\.\pipe\sql\query`  
  
 Geben Sie `sql\query`  
  
 **Aktiviert**  
 Mögliche Werte sind **Yes** und **No**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen eines Netzwerkprotokolls](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
