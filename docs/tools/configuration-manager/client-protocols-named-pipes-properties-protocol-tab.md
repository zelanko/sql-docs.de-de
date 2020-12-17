---
title: Clientprotokolle - Named Pipes-Eigenschaften (Registerkarte Protokoll)
description: In diesem Artikel erfahren Sie, wie Sie die Beschreibung der Standardpipe im SQL Server-Konfigurations-Manager anzeigen oder bearbeiten. Außerdem erfahren Sie, wie Sie eine Verbindung zu einer anderen Pipe herstellen.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: 6e637bb0dd5979e5149ef70cba59ed8a4ac7f583
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463878"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Clientprotokolle - Named Pipes-Eigenschaften (Registerkarte Protokoll)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Verwenden Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Configuration Manager im Dialogfeld **Named Pipes Properties** (Named Pipes-Eigenschaften) die Registerkarte **Protokoll**, um die Beschreibung der Standardpipe anzuzeigen oder zu bearbeiten. Um eine Verbindung mit einer anderen Pipe herzustellen, geben Sie die Pipe im Dialogfeld **Standardpipe** ein. Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Creating a Valid Connection String Using Named Pipes](/previous-versions/sql/sql-server-2016/ms189307(v=sql.130)).  
  
## <a name="options"></a>Tastatur  
 **Standardpipe**  
 Gibt die Standardpipe an, die von der Named Pipes-Netzwerkbibliothek zum Herstellen einer Verbindung mit der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Standardmäßig überwacht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : `\\.\pipe\sql\query`  
  
 Geben Sie `sql\query`  
  
 **Aktiviert**  
 Mögliche Werte sind **Yes** und **No**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen eines Netzwerkprotokolls](/previous-versions/sql/sql-server-2016/ms187892(v=sql.130))  
  
