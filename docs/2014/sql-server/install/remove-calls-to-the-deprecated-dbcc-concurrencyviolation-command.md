---
title: Entfernen Sie Aufrufe des veralteten DBCC CONCURRENCYVIOLATION-Befehls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2486546efae7daa63441e12fa350ef878c7daa77
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261896"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Entfernen von Aufrufen des veralteten DBCC CONCURRENCYVIOLATION-Befehls
  Der Upgrade Advisor hat die Verwendung des Befehls DBCC CONCURRENCYVIOLATION erkannt. Dieser Befehl ist nicht mehr verfügbar. Wenn Sie diesen Befehl ausführen, wird Fehler 2526 zurückgegeben.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Keine aktuelle Version der Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält eine Arbeitsauslastungskontrolle. Deshalb wurde der Befehl entfernt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Aktualisieren Sie die Anwendungen und Skripts, um Verweise auf diesen veralteten Befehl zu entfernen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
