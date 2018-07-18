---
title: Überprüfen, ob alle Dateigruppen geschrieben werden, während des Upgrades | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41ca2adb014d1cdaee23e32123772744fae76b68
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328970"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Überprüfen, ob während des Upgrades Schreibzugriff auf alle Dateigruppen möglich ist
  Upgrade Advisor hat eine Datenbank erkannt, die über eine oder mehrere schreibgeschützte Dateigruppen verfügt. Für die Dateigruppen aller Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss READ_WRITE festgelegt werden, bevor ein Upgrade durchgeführt werden kann.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie können eine Dateigruppe mithilfe von ALTER DATABASE auf READ_WRITE festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
