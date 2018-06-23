---
title: Entfernen Sie Aufrufe des veralteten DBCC CONCURRENCYVIOLATION-Befehls | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a17b3c844afb6b8b804da258b0330d45dc7208e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148312"
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
  