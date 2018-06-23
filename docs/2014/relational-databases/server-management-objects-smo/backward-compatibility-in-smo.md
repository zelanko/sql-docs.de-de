---
title: Abwärtskompatibilität in SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 65f779631e0671a00fedb9442dbe1e372e7a7db2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150762"
---
# <a name="backward-compatibility-in-smo"></a>Abwärtskompatibilität in SMO
  In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geschriebene SMO-Anwendungen können mithilfe von SMO in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] neu kompiliert werden.  
  
## <a name="migrating-smo-applications"></a>Migrieren von SMO-Anwendungen  
 Verweise auf SMO-DLLs in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] müssen entfernt werden, während Verweise auf die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthaltenen neuen SMO-DLLs eingeschlossen werden müssen.  
  
 Sie müssen mindestens einen Verweis auf folgende Dateien einschließen:  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Diese Dateien sind für Verbindungsklassen, SMO-Hilfsprogrammklassen und Foundation Classes erforderlich.  
  
> [!NOTE]  
>  Die Datei SmoEnum.dll wurde entfernt. Folglich müssen Verweise darauf aus dem SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Projekt entfernt werden.  
  
 Da sich die Namespaces ebenfalls geändert haben, können Sie Folgendes verwenden:  
  
##### <a name="for-visual-c"></a>Für Visual C#  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a>Für Visual Basic  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 Wenn im Code URN-Funktionen wie `Server.GetSqlSmoObject(Urn)` verwendet werden, müssen Sie eine Verknüpfung mit dem Microsoft.SqlServer.Management.Sdk.Sfc-Namespace herstellen.  
  
 Wenn im Code das Transfer-Objekt direkt verwendet wird, müssen Sie eine Verknüpfung mit dem Microsoft.SqlServer.Management.SmoExtended-Namespace herstellen.  
  
 Wenn Sie Code migrieren, müssen Sie ihn ggf. ändern. Dies liegt daran, dass einige [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] als veraltet markiert wurden. Weitere Informationen zu veralteten Funktionen finden Sie unter [veralteten Datenbankmodul-Funktionen in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.  
  
  