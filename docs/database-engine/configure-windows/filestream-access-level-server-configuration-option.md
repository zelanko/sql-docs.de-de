---
title: Filestream-Zugriffsebene (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Hier machen Sie sich mit der Option „filestream_access_level“ vertraut. Sie erfahren, wie die Option die FILESTREAM-Zugriffsebene für eine SQL Server-Instanz ändert.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 04205ee05e3c26cc807a3a6aa828152c20e4c3c7
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670953"
---
# <a name="filestream-access-level-server-configuration-option"></a>Filestream-Zugriffsebene (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwenden Sie die Option FILESTREAM-Zugriffsebene, um die FILESTREAM-Zugriffsebene für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu ändern.  
  
> [!NOTE]  
>  Damit diese Option wirksam wird, müssen die Windows-Verwaltungseinstellungen für FILESTREAM aktiviert sein. Sie können diese Einstellungen bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager aktivieren.  
  
|Wert|Definition|  
|-----------|----------------|  
|0|Deaktiviert die FILESTREAM-Unterstützung für diese Instanz.|  
|1|Aktiviert FILESTREAM für den [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff.|  
|2|Aktiviert FILESTREAM für [!INCLUDE[tsql](../../includes/tsql-md.md)] und für den Win32-Streamingzugriff.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration der Datenbank-Engine - Filestream](../install-windows/install-sql-server.md)   
 [Aktivieren und Konfigurieren von FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
