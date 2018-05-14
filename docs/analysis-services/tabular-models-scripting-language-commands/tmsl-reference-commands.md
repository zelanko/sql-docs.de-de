---
title: Befehle im tabellarischen Modell Scripting Language (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9c36ba09aa19aa8abc1c21ea8c870dbfe2d24c9e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="tmsl-reference---commands"></a>TMSL-Verweis - Befehle
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Sie können Befehle in einem XMLA-Endpunkt ausführen, das Formulieren von Definitionen von Systemobjekten im JSON-Format mit dem tabellarischen Tabular Model Scripting Language (TMSL), für tabellenmodelldatenbanken.   Finden Sie unter [Objektdefinitionen in Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) eine Liste von Objekten, die mit den folgenden Befehlen verwendet.  
  
## <a name="object-operations"></a>Objektvorgänge  
  
|||  
|-|-|  
|[Alter-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|Stellen Sie Inline-Änderungen auf ein Objekt, ohne die vollständige Definition angeben zu müssen.|  
|[CREATE-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|Erstellt ein neues Objekt, einschließlich seiner Nachfolger.|  
|[CreateOrReplace-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|Erstellen oder Teile einer Objektdefinition ersetzen. Die vollständige Definition muss angegeben werden.|  
|[Delete-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|Löschen eines Objekts, einschließlich seiner Nachfolger.|  
  
## <a name="data-refresh-operations"></a>Datenaktualisierungsvorgänge  
  
|||  
|-|-|  
|[MergePartitions-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|Eine Quelle Zusammenführen Sie eine Zielpartition und löschen Sie das Ziel.|  
|[Refresh-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|Eine Datenbank, Tabelle oder Partition zu verarbeiten.|  
  
## <a name="scripting"></a>Skripterstellung  
  
|||  
|-|-|  
|[Sequence-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|Batch-Vorgänge sequenziell oder parallel|  
  
## <a name="database-management-operations"></a>Datenbank-Management-Vorgänge  
  
|||  
|-|-|  
|[Befehl "Anfügen" &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|Fügt eine Datei mit dem Server.|  
|[Detach-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|Entfernt eine Datei vom Server an.|  
|[Backup-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|Erstellt eine Sicherungsdatei mit einer Datenbank an.|  
|[RESTORE-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|Stellt die Datenbank mit dem Server wieder her.|  
|[Synchronize-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Synchronisiert eine Analysis Services-Datenbank mit einer anderen vorhandenen Datenbank.|  
  
## <a name="see-also"></a>Siehe auch  
 [Tabular Model Scripting Language &#40;TMSL&#41; – Referenz](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Installieren von Analysis Services-Datenanbietern &#40;AMO, ADOMD.NET, MSOLAP&#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Kompatibilitätsgrad für tabellarische Modelle in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
