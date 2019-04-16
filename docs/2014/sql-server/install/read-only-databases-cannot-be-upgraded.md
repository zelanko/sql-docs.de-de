---
title: Schreibgeschützte Datenbanken können nicht aktualisiert werden kann | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f3f751f4058d29c6ce27a5a1d608f3fb076cc300
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583253"
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
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
