---
title: Angeben des WITH-Schlüsselworts bei Verwendung von Tabellenhinweisen im Kompatibilitätsmodus ' 90 ' | Microsoft Docs
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
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da01cc9f626f88c63a10da37540eb6fa00f1b0c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048201"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a>Angeben des WITH-Schlüsselworts bei Verwendung von Tabellenhinweisen im Kompatibilitätsmodus 90
  Bis auf einige Ausnahmen werden Tabellenhinweise nur dann in der FROM-Klausel einer Abfrage unterstützt, wenn die Hinweise mithilfe des WITH-Schlüsselworts angegeben werden. Weitere Informationen hierzu finden Sie in den Themen "FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])" und "Tabellenhinweis ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie Abfragen, die Tabellenhinweise in der FROM-Klausel enthalten, indem Sie das WITH-Schlüsselwort vor den Tabellenhinweisen einfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
