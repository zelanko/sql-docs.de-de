---
title: Tabellenhinweise in indizierten Sichtdefinitionen werden im Kompatibilitätsmodus ' 80 ' ignoriert und sind nicht zulässig, im Modus 90 oder höher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93159a8c32f484fd9c734b4847dfd1e7fca854a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317430"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Tabellenhinweise in indizierten Sichtdefinitionen werden im Kompatibilitätsmodus 80 ignoriert und sind im Modus 90 oder höher nicht zulässig
  Tabellenhinweise in den Definitionen indizierter Sichten sind im Kompatibilitätsmodus 90 oder höher nicht zulässig. Weitere Informationen hierzu finden Sie in den folgenden Themen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation: "Entwerfen von indizierten Sichten" "Erstellen von indizierten Sichten" und "Abfragehinweis ([!INCLUDE[tsql](../../includes/tsql-md.md)])".  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Tabellenhinweise müssen aus den Definitionen indizierter Sichten entfernt werden. Unabhängig vom verwendeten Kompatibilitätsmodus empfehlen wir, dass Sie die Anwendung testen. Indem Sie die Anwendung testen, können Sie sicherstellen, dass sie korrekt funktioniert, wenn indizierte Sichten erstellt, aktualisiert oder Abfragen zugeordnet werden oder wenn auf sie zugegriffen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
