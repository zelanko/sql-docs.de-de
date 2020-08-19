---
description: Abwärtskompatibilität in SMO
title: Abwärtskompatibilität in SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d18b4d12b38627048fb5b8844685cd36541027dd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448102"
---
# <a name="backward-compatibility-in-smo"></a>Abwärtskompatibilität in SMO
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geschriebene SMO-Anwendungen können mithilfe von SMO in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]neu kompiliert werden.  
  
## <a name="migrating-smo-applications"></a>Migrieren von SMO-Anwendungen  
 Verweise auf SMO-DLLs in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] müssen entfernt werden, während Verweise auf die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthaltenen neuen SMO-DLLs eingeschlossen werden müssen.  
  
 Sie müssen mindestens einen Verweis auf folgende Dateien einschließen:  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Diese Dateien sind für Verbindungsklassen, SMO-Hilfsprogrammklassen und Foundation Classes erforderlich.  
  
> [!NOTE]  
>  Die Datei SmoEnum.dll wurde entfernt. Folglich müssen Verweise darauf aus dem SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Projekt entfernt werden.  
  
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
  
 Wenn im Code URN-Funktionen wie **Server.GetSqlSmoObject(Urn)** verwendet werden, müssen Sie eine Verknüpfung mit dem Microsoft.SqlServer.Management.Sdk.Sfc-Namespace herstellen.  
  
 Wenn im Code das Transfer-Objekt direkt verwendet wird, müssen Sie eine Verknüpfung mit dem Microsoft.SqlServer.Management.SmoExtended-Namespace herstellen.  
  
 Wenn Sie Code migrieren, müssen Sie ihn ggf. ändern. Dies liegt daran, dass einige [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] - und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]als veraltet markiert wurden. Weitere Informationen zu veralteten Funktionen finden Sie unter [veraltet Datenbank-Engine Features in SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Online Dokumentation.  
  
  
