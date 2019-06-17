---
title: Entfernen Sie Aufrufe des veralteten DBCC CONCURRENCYVIOLATION-Befehls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0110d4bc138ad0da953eb83d3c81ec265d2fd3ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093208"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Entfernen von Aufrufen des veralteten DBCC CONCURRENCYVIOLATION-Befehls
  Der Upgrade Advisor hat die Verwendung des Befehls DBCC CONCURRENCYVIOLATION erkannt. Dieser Befehl ist nicht mehr verfügbar. Wenn Sie diesen Befehl ausführen, wird Fehler 2526 zurückgegeben.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Keine aktuelle Version der Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält eine Arbeitsauslastungskontrolle. Deshalb wurde der Befehl entfernt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Aktualisieren Sie die Anwendungen und Skripts, um Verweise auf diesen veralteten Befehl zu entfernen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
