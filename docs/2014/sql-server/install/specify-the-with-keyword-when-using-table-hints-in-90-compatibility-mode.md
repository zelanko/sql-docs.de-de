---
title: Das WITH-Schlüsselwort angeben, wenn Sie Tabellenhinweise im Kompatibilitätsmodus ' 90 ' verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: de4abebf061d2eaa419d8b71c9cf5a50d3e505db
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582943"
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
  
  
