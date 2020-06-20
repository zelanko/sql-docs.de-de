---
title: SqlServerAlias-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
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
ms.openlocfilehash: 46994409cc6a5119c9144eb7a3a4b9a8a9a22c44
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85002452"
---
# <a name="sqlserveralias-class"></a>SqlServerAlias-Klasse
  Die [SqlServerAlias Class](sqlserveralias-class.md) -Klasse stellt einen Serververbindungsalias dar.  
  
 Ein Serververbindungsalias ist erforderlich, wenn beide der folgenden Situationen eintreten:  
  
-   Der Client stellt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über einen Netzwerk Transport, der nicht der standardmäßige Netzwerk Transport ist, eine Verbindung mit einer Instanz von her.  
  
-   Die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mit der der Client verbunden ist, überwacht einen anderen Named Pipe.  
  
 **Hinweis:** Die [SqlServerAlias-Klasse](sqlserveralias-class.md) erbt die- `Put` Methode von der Provider-Klasse. Es werden jedoch keine Ergebnisse ausgegeben , wie von der `Provider::Put`-Methode angegeben. Weitere Informationen finden Sie in der WMI-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
