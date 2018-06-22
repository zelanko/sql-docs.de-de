---
title: Index neu organisieren (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d14a348e0cf86c04e66afb1d008085877b63ab19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147950"
---
# <a name="reorganize-index-task"></a>Index neu organisieren (Task)
  Mit dem Task Index neu organisieren werden Indizes in Tabellen und Sichten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken neu organisiert. Weitere Informationen zum Verwalten von Indizes finden Sie unter [Neuorganisieren und Neuerstellen von Indizes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 Mithilfe des Tasks Index neu organisieren kann ein Paket Indizes in einer einzelnen Datenbank oder mehreren Datenbanken neu organisieren. Falls mit dem Task nur die Indizes in einer einzelnen Datenbank neu organisiert werden, können Sie die Sichten oder Tabellen auswählen, deren Indizes neu organisiert werden. Der Task Index neu organisieren schließt außerdem eine Option zum Komprimieren von großen Objekten ein. LOB-Daten sind Daten, mit der `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, oder `xml` -Datentyp. Weitere Informationen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
 Der Task Index neu organisieren kapselt die ALTER INDEX-Anweisung von Transact-SQL. Wenn Sie große Objekte komprimieren möchten, verwendet die Anweisung die REORGANIZE WITH (LOB_COMPACTION = ON)-Klausel. Andernfalls ist LOB_COMPACTION auf OFF festgelegt. Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
> [!IMPORTANT]  
>  Die Zeit, die der Task zum Erstellen der vom Task ausgeführten Transact-SQL-Anweisung benötigt, ist proportional zur Anzahl der vom Task neu organisierten Indizes. Falls für den Task konfiguriert ist, dass die Indizes in allen Tabellen und Sichten in einer Datenbank mit vielen Indizes neu organisiert werden, oder dass Indizes in mehreren Datenbanken neu organisiert werden, kann das Generieren der Transact-SQL-Anweisung lange dauern.  
  
## <a name="configuration-of-the-reorganize-index-task"></a>Konfiguration des Tasks "Index neu organisieren"  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task „Index neu organisieren“ &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Weitere Informationen zum Anzeigen dieser Eigenschaften im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer finden Sie unter [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
