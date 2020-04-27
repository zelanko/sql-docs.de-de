---
title: Schreibgeschützte Datenbanken können nicht aktualisiert werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 414b26cf860ab32bb11beaa1ccbef3316c68f557
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093371"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Schreibgeschützte Datenbanken können nicht aktualisiert werden
  Upgrade Advisor hat festgestellt, dass ein Upgrade einiger Datenbanken dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht durchgeführt werden kann.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Eine schreibgeschützte Datenbank wurde erkannt. Um die Datenbank zu aktualisieren, muss das Setupprogramm in die Datenbank schreiben können.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn Sie die Datenbank nicht verwenden, verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], oder die ALTER DATABASE-Anweisung, um die Datenbank in Lese-/Schreibzugriff zu ändern. Die folgende Anweisung gewährt Lese-/Schreibzugriff auf eine Datenbank.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Weitere Informationen über die ALTER DATABASE-Anweisung finden Sie im Thema "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
