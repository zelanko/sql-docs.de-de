---
title: SqlServerAlias-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d913f28415c708ad09b419732ebef4e26b607ecb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221410"
---
# <a name="sqlserveralias-class"></a>SqlServerAlias-Klasse
  Die [SqlServerAlias Class](sqlserveralias-class.md) -Klasse stellt einen Serververbindungsalias dar.  
  
 Ein Serververbindungsalias ist erforderlich, wenn beide der folgenden Situationen eintreten:  
  
-   Der Client stellt über einen Netzwerktransport, der nicht der standardmäßige Netzwerktransport ist, ein Verbindung zu einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] her.  
  
-   Die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mit der der Client verbunden ist, überwacht einen anderen Named Pipe.  
  
 **Hinweis:** der [SqlServerAlias-Klasse](sqlserveralias-class.md) erbt die `Put` Methode aus der Provider-Klasse. Allerdings es ist keine Ergebnisse zurück wie durch die `Provider::Put` Methode. Weitere Informationen finden Sie in der WMI-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
