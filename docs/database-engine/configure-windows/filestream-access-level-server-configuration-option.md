---
title: Filestream-Zugriffsebene (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c45a971793b03d30305adbb92d04e890f4dbc220
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863835"
---
# <a name="filestream-access-level-server-configuration-option"></a>Filestream-Zugriffsebene (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Verwenden Sie die Option FILESTREAM-Zugriffsebene, um die FILESTREAM-Zugriffsebene für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu ändern.  
  
> [!NOTE]  
>  Damit diese Option wirksam wird, müssen die Windows-Verwaltungseinstellungen für FILESTREAM aktiviert sein. Sie können diese Einstellungen bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager aktivieren.  
  
|value|Definition|  
|-----------|----------------|  
|0|Deaktiviert die FILESTREAM-Unterstützung für diese Instanz.|  
|1|Aktiviert FILESTREAM für den [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff.|  
|2|Aktiviert FILESTREAM für [!INCLUDE[tsql](../../includes/tsql-md.md)] und für den Win32-Streamingzugriff.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 
  [Konfiguration der Datenbank-Engine - Filestream](http://msdn.microsoft.com/library/641a10a1-ae52-4d26-8f1c-a032a4aeff02)   
 [Aktivieren und Konfigurieren von FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
