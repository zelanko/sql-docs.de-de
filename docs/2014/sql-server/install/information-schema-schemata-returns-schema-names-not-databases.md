---
title: INFORMATION_SCHEMA. SCHEMAS gibt Schemanamen in einer Datenbank ist nicht in einer Instanz Datenbanken | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e624597090ab6a7efdb21ebbff6785b1471d7367
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161471"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA gibt Schemanamen in einer Datenbank, nicht Datenbanken in einer Instanz zurück
  Der Upgrade Advisor hat Anweisungen erkannt, die auf die INFORMATION_SCHEMA.SCHEMATA-Sicht verweisen. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gab diese Sicht alle Datenbanken in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher gibt die Sicht alle Schemas in einer Datenbank zurück.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gab die INFORMATION_SCHEMA.SCHEMATA-Sicht alle Datenbanken in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. Jetzt gibt die Sicht alle Schemas in einer Datenbank zurück, die dem SQL-Standard entsprechen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Anwendung auf die **sys.databases** Katalogsicht, um alle Datenbanken in einer Instanz von zurückgeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
