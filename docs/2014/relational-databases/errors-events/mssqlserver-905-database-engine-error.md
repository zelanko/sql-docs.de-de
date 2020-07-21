---
title: MSSQLSERVER_905 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2db51e80ebe7df5f8793dba3b2c09e2afc199b59
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553115"
---
# <a name="mssqlserver_905"></a>MSSQLSERVER_905
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|905|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBSTARTUP_EE_PARTITIONING|  
|Meldungstext|Die '%.*ls'-Datenbank kann in dieser Edition von SQL Server nicht gestartet werden, weil sie eine '%.\*ls'-Partitionsfunktion enthält. Das Partitionieren wird nur von SQL Server Enterprise Edition unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
 Die Datenbank enthält mindestens eine partitionierte Tabelle bzw. mindestens einen partitionierten Index. In dieser Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann keine Partitionierung verwendet werden. Deshalb kann die Datenbank nicht ordnungsgemäß gestartet werden. Partitionierte Tabellen und Indizes sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Trennen Sie die Datenbank mithilfe der gespeicherten Prozedur sp_detach_db. Verschieben Sie die Dateien bei Bedarf, und fügen Sie dann die Datenbank an eine Instanz der unterstützen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Edition an. Verwenden Sie dazu CREATE DATABASE mit der FOR ATTACH-Option oder der FOR ATTACH_REBUILD_LOG-Option. Deaktivieren Sie die Partitionierung für alle Tabellen, und entfernen Sie die Partitionierungsfunktionen. Trennen Sie die Datenbank wieder, und fügen Sie sie an den aktuellen Server an.  
  
  
