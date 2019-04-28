---
title: Stellen Sie sicher, dass keine Datenbankdateien auf komprimierten Laufwerken, während des Upgradevorgangs befinden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dd8a5524c5aede5538d77709f7b0ae7303d8191c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990138"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a>Vergewissern Sie sich, dass sich während des Upgradevorgangs keine Datenbankdateien auf komprimierten Laufwerken befinden
  Der Upgrade Advisor hat Datenbankdateien auf einem komprimierten Laufwerk erkannt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann Datenbanken auf komprimierten Laufwerken nicht erstellen oder aktualisieren.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installieren, wählen Sie ein unkomprimiertes Laufwerk für Systemdatenbanken aus, und stellen Sie sicher, dass sich die zu aktualisierenden Datenbanken nicht auf komprimierten Laufwerken befinden. Sie müssen allerdings beachten, dass Sie nach dem Aktualisieren der Datenbank schreibgeschützte Datenbanken und schreibgeschützte sekundäre Dateigruppen in einem komprimierten NTFS-Dateisystem speichern können.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
