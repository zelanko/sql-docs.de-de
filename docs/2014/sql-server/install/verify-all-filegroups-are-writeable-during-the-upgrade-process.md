---
title: Überprüfen, ob während des Upgradevorgangs alle Dateigruppen beschreibbar sind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062318"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Überprüfen, ob während des Upgrades Schreibzugriff auf alle Dateigruppen möglich ist
  Upgrade Advisor hat eine Datenbank erkannt, die über eine oder mehrere schreibgeschützte Dateigruppen verfügt. Für die Dateigruppen aller Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss READ_WRITE festgelegt werden, bevor ein Upgrade durchgeführt werden kann.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie können eine Dateigruppe mithilfe von ALTER DATABASE auf READ_WRITE festlegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
