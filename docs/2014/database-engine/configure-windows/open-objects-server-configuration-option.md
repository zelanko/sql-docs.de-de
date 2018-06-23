---
title: Geöffnete Objekte (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 29a9cd7490142659b8201aca67c7ae9bd6f7df0f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162092"
---
# <a name="open-objects-server-configuration-option"></a>Geöffnete Objekte (Serverkonfigurationsoption)
  Diese Option ist in **sp_configure**weiterhin vorhanden, obwohl die zugehörige Funktionalität in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]deaktiviert wurde. (Die Einstellung hat keine Auswirkungen.) In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die Anzahl von geöffneten Datenbankobjekten dynamisch verwaltet und nur durch den verfügbaren Arbeitsspeicher beschränkt. Die Option **Geöffnete Objekte** wurde in **sp_configure** belassen, um die Abwärtskompatibilität mit vorhandenen Skripts sicherzustellen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  