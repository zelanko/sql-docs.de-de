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
ms.openlocfilehash: 1ad92a32c47002c8f56e56a5b3695d42d3bdd671
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012072"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql unterstützt nicht länger 'ED'- und '!!'- commands
  Das Hilfsprogramm **osql** unterstützt nicht die Funktionen " **Ed** " und " **!!** " nicht.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie Verweise auf das **Ed** -und das **!!** aus den Skripts.  
  
 Wenn Sie " **Ed** " und " **!!** " verwenden möchten Verwenden Sie das Hilfsprogramm **sqlcmd** anstelle von **osql**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
