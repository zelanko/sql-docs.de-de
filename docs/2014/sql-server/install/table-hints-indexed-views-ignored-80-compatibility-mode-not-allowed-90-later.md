---
title: Tabellenhinweise in indizierten Sichtdefinitionen werden im Kompatibilitätsmodus ' 80 ' ignoriert und sind nicht zulässig, im Modus 90 oder höher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69a6bae06b1cb5d7a727ff2582f10bccf1e21ca8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091806"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Tabellenhinweise in indizierten Sichtdefinitionen werden im Kompatibilitätsmodus 80 ignoriert und sind im Modus 90 oder höher nicht zulässig
  Tabellenhinweise in den Definitionen indizierter Sichten sind im Kompatibilitätsmodus 90 oder höher nicht zulässig. Weitere Informationen finden Sie unter den folgenden Themen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation: "Entwerfen von indizierten Sichten", "Erstellen von indizierten Sichten," und "Abfragehinweis ([!INCLUDE[tsql](../../includes/tsql-md.md)])."  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Tabellenhinweise müssen aus den Definitionen indizierter Sichten entfernt werden. Unabhängig vom verwendeten Kompatibilitätsmodus empfehlen wir, dass Sie die Anwendung testen. Indem Sie die Anwendung testen, können Sie sicherstellen, dass sie korrekt funktioniert, wenn indizierte Sichten erstellt, aktualisiert oder Abfragen zugeordnet werden oder wenn auf sie zugegriffen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
