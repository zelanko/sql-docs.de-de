---
title: Die Microsoft-Volltext-Engine für SQL Server lädt standardmäßig keine nicht signierte Komponenten von Drittanbietern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46632ec66e9ae17351cb10a65efbac9cedfb084a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62711405"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>Die Microsoft-Volltext-Engine für SQL Server lädt standardmäßig keine nicht signierten Komponenten von Drittanbietern
  Standardmäßig lädt die [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Komponenten, die nicht von [!INCLUDE[msCoName](../../includes/msconame-md.md)] signiert sind.  
  
## <a name="component"></a>Komponente  
 Volltextsuche  
  
## <a name="description"></a>Description  
 Ein Filter eines Drittanbieters, wie z. B. ein PDF-Filter, der derzeit auf dem Server installiert ist, wird nach dem Upgrade standardmäßig nicht von der [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um einen drittanbieterfilter zu laden, müssen Sie festlegen *Load_os_resource* und deaktivieren Sie *Verify_signature* für diese Instanz.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
