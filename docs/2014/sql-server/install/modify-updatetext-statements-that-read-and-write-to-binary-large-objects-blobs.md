---
title: Ändern Sie UPDATETEXT-Anweisungen, die Lese- und Schreibberechtigungen für binary large Object (BLOBs) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7bcf5b59aa79e471ef0fc7949990b9782550ec32
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582000"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Ändern der UPDATETEXT-Anweisungen, die BLOBs (Binary Large Objects) lesen bzw. in BLOBs schreiben
  Der Upgrade Advisor hat UPDATETEXT-Anweisungen erkannt, die mithilfe des gleichen Textzeigers die gleichen BLOB-Daten (Binary Large Object) lesen bzw. in die gleichen BLOB-Daten schreiben. Von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird die Verwendung von Textzeigern auf diese Weise nicht unterstützt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Kopieren Sie das BLOB in eine temporäre Tabelle oder eine Tabellenvariable, und weisen Sie den Wert dann erneut der ursprünglichen Spalte zu.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
