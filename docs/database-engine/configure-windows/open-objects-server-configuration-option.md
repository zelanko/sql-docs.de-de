---
title: Geöffnete Objekte (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die deaktivierte Konfigurationsoption „Geöffnete Objekte“. Außerdem erfahren Sie, wie SQL Server nun die Anzahl geöffneter Datenbankobjekte verwaltet.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0bbcb11a80f06eae10e5481c965e9216cc84695e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773619"
---
# <a name="open-objects-server-configuration-option"></a>Geöffnete Objekte (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Diese Option ist in **sp_configure** weiterhin vorhanden, obwohl die zugehörige Funktionalität in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deaktiviert wurde. (Die Einstellung hat keine Auswirkungen.) In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die Anzahl von geöffneten Datenbankobjekten dynamisch verwaltet und nur durch den verfügbaren Arbeitsspeicher beschränkt. Die Option **Geöffnete Objekte** wurde in **sp_configure** belassen, um die Abwärtskompatibilität mit vorhandenen Skripts sicherzustellen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
