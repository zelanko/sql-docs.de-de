---
title: Die Microsoft-Volltext-Engine für SQL Server lädt standardmäßig keine nicht signierten Komponenten von Drittanbietern. Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012481"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>Die Microsoft-Volltext-Engine für SQL Server lädt standardmäßig keine nicht signierten Komponenten von Drittanbietern
  Standardmäßig lädt die [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Komponenten, die nicht von [!INCLUDE[msCoName](../../includes/msconame-md.md)] signiert sind.  
  
## <a name="component"></a>Komponente  
 Volltextsuche  
  
## <a name="description"></a>BESCHREIBUNG  
 Ein Filter eines Drittanbieters, wie z. B. ein PDF-Filter, der derzeit auf dem Server installiert ist, wird nach dem Upgrade standardmäßig nicht von der [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um einen Drittanbieter Filter zu laden, müssen Sie *load_os_resource* festlegen und *verify_signature* für diese Instanz deaktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
