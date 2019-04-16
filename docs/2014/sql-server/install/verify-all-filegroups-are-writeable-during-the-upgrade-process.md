---
title: Überprüfen, ob alle Dateigruppen geschrieben werden, während des Upgrades | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 98633674559feead48a5b1c3cbe997863ad0f18a
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583083"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Überprüfen, ob während des Upgrades Schreibzugriff auf alle Dateigruppen möglich ist
  Upgrade Advisor hat eine Datenbank erkannt, die über eine oder mehrere schreibgeschützte Dateigruppen verfügt. Für die Dateigruppen aller Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss READ_WRITE festgelegt werden, bevor ein Upgrade durchgeführt werden kann.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie können eine Dateigruppe mithilfe von ALTER DATABASE auf READ_WRITE festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
