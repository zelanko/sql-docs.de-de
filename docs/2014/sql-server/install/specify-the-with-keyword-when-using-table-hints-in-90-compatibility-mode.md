---
title: Das WITH-Schlüsselwort angeben, wenn Sie Tabellenhinweise im Kompatibilitätsmodus ' 90 ' verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ff2fee26c6f71cc398f8dbacf91f3ad8dbdb3358
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092161"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a>Angeben des WITH-Schlüsselworts bei Verwendung von Tabellenhinweisen im Kompatibilitätsmodus 90
  Bis auf einige Ausnahmen werden Tabellenhinweise nur dann in der FROM-Klausel einer Abfrage unterstützt, wenn die Hinweise mithilfe des WITH-Schlüsselworts angegeben werden. Weitere Informationen hierzu finden Sie in den Themen "FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])" und "Tabellenhinweis ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie Abfragen, die Tabellenhinweise in der FROM-Klausel enthalten, indem Sie das WITH-Schlüsselwort vor den Tabellenhinweisen einfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
