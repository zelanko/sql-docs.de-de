---
title: Ändern Sie UPDATETEXT-Anweisungen, die Lese- und Schreibberechtigungen für binary large Objects (BLOBs) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5b0c6df5c9324a35f1f642d366ef8f2780341592
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150274"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Ändern der UPDATETEXT-Anweisungen, die BLOBs (Binary Large Objects) lesen bzw. in BLOBs schreiben
  Der Upgrade Advisor hat UPDATETEXT-Anweisungen erkannt, die mithilfe des gleichen Textzeigers die gleichen BLOB-Daten (Binary Large Object) lesen bzw. in die gleichen BLOB-Daten schreiben. Von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird die Verwendung von Textzeigern auf diese Weise nicht unterstützt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Kopieren Sie das BLOB in eine temporäre Tabelle oder eine Tabellenvariable, und weisen Sie den Wert dann erneut der ursprünglichen Spalte zu.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
