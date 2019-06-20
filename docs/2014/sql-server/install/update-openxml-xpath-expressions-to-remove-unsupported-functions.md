---
title: Aktualisieren Sie OPENXML für XPath-Ausdrücke, um nicht unterstützte Funktionen entfernen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec0edb2e72143fd41709355a3e9cc338544289a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66091687"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a>Aktualisieren von OPENXML-XPath-Ausdrücken, um nicht unterstützte Funktionen zu entfernen
  Der Upgrade Advisor hat die Verwendung der XPath-Funktionalität erkannt. Durch das Upgrade kommt es möglicherweise zu Problemen durch die Änderungen der Xpath-Funktionalität für OPENXML-Funktionen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 MSXML 3.0 ist jetzt die zugrunde liegende Engine, die zur Verarbeitung von XPath-Ausdrücken verwendet wird, die in OPENXML-Abfragen verwendet werden. MSXML 3.0 beinhaltet eine strengere XPath 1.0-Engine, in der die folgenden Funktionen nicht mehr unterstützt werden:  
  
-   format-number()  
  
-   formatNumber()  
  
-   current()  
  
-   element-available()  
  
-   function-available()  
  
-   system-property()  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Was format-number() und formatNumber() betrifft, so können Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] verwenden. Für die anderen nicht unterstützten Funktionen, die weiter oben aufgeführt sind, gibt es keine direkte Problemumgehung.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
