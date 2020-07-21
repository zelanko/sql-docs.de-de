---
title: MSSQLSERVER_948 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a554f8cdd312f08e8e0930c0d3eb49776cbc4e8
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553100"
---
# <a name="mssqlserver_948"></a>MSSQLSERVER_948
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|948|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|Nicht verfügbar|  
|Meldungstext|Die '%.*ls'-Datenbank kann nicht geöffnet werden, weil sie die Version %d aufweist. Dieser Server unterstützt Version %d und früher. Ein Herabstufungspfad wird nicht unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
 Bestimmte funktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirken sich auf die Struktur der Datenbankdateien aus. Wenn Sie eine Datenbank an eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anfügen, ist das Dateiformat möglicherweise mit einer anderen Version von [!INCLUDE[ssDE](../../includes/ssde-md.md)] nicht kompatibel.  
  
 Dieser Fehler kann beispielsweise verursacht werden, wenn das vardecimal-Speicherformat in einer höheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird und dann versucht wird, die Datenbankdateien in einer niedrigeren Version als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 anzufügen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ermitteln Sie die Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die auf dem ursprünglichen Server ausgeführt wird. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Klicken Sie in entweder mit der rechten Maustaste auf den Server, und klicken Sie dann auf **Eigenschaften** , oder geben Sie `SELECT @@VERSION` ein Abfragefenster ein. Öffnen Sie die Datenbank mithilfe der ursprünglichen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ermitteln Sie die funktionen, die für die ursprüngliche Datenbank in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktiviert sind. Ändern Sie diese Einstellungen, um mit der Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu arbeiten, in der die Datenbank angefügt wird.  
  
  
