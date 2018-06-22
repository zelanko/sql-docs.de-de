---
title: WITH ROWS wird in CREATE STATISTICS-Anweisungen im Kompatibilitätsmodus 90 oder höher nicht unterstützt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d509352d99cab9359e7ea222f5fb2d5d7e28075
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147806"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Im Kompatibilitätsmodus 90 oder höher wird WITH ROWS in CREATE STATISTICS-Anweisungen nicht unterstützt
  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen und der Kompatibilitätsmodus auf 90 oder höher festgelegt ist, wird die Angabe von WITH ROWS in CREATE STATISTICS-Anweisungen nicht unterstützt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie CREATE STATISTICS-Anweisungen, die WITH ROWS enthalten, durch Angabe von WITH SAMPLE *Anzahl* Zeilen oder andere Optionen, die entsprechen der dokumentierten Syntax angeben. Weitere Informationen hierzu finden Sie im Thema "CREATE STATISTICS (Transact-SQL) in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
