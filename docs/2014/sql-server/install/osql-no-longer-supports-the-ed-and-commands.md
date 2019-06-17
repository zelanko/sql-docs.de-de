---
title: osql unterstützt nicht länger 'ED'- und '!!'- Befehle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ce7bfa0bbeec5c5ca83b7139f0ff28e3994021d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093715"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql unterstützt nicht länger 'ED'- und '!!'- Befehle
  Die **Osql** Hilfsprogramm bietet keine Unterstützung der **ED** und **!!** nicht.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie Verweise auf die **ED** und **!!** aus den Skripts.  
  
 Wenn Sie verwenden möchten. die **ED** und **!!** Befehle verwenden die **Sqlcmd** anstelle von Hilfsprogramm **Osql**.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
