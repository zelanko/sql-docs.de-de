---
title: Schreibgeschützte Datenbanken können nicht aktualisiert werden kann | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
caps.latest.revision: 13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8ce09bf818efcedca3fdfce7f138219236a254f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183827"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Schreibgeschützte Datenbanken können nicht aktualisiert werden
  Upgrade Advisor hat festgestellt, dass ein Upgrade einiger Datenbanken dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht durchgeführt werden kann.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Eine schreibgeschützte Datenbank wurde erkannt. Um die Datenbank zu aktualisieren, muss das Setupprogramm in die Datenbank schreiben können.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn niemand die Datenbank verwendet wird, verwenden Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], oder die ALTER DATABASE-Anweisung zum Ändern der Datenbank mit Lese-/ Schreibzugriff. Die folgende Anweisung gewährt Lese-/Schreibzugriff auf eine Datenbank.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Weitere Informationen über die ALTER DATABASE-Anweisung finden Sie im Thema "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
