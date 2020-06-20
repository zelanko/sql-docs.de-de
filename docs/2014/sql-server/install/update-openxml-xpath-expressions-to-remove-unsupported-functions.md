---
title: Aktualisieren von OPENXML-XPath-Ausdrücken, um nicht unterstützte Funktionen zu entfernen | Microsoft-Dokumentation
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
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041767"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a>Aktualisieren von OPENXML-XPath-Ausdrücken, um nicht unterstützte Funktionen zu entfernen
  Der Upgrade Advisor hat die Verwendung der XPath-Funktionalität erkannt. Durch das Upgrade kommt es möglicherweise zu Problemen durch die Änderungen der Xpath-Funktionalität für OPENXML-Funktionen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 MSXML 3.0 ist jetzt die zugrunde liegende Engine, die zur Verarbeitung von XPath-Ausdrücken verwendet wird, die in OPENXML-Abfragen verwendet werden. MSXML 3.0 beinhaltet eine strengere XPath 1.0-Engine, in der die folgenden Funktionen nicht mehr unterstützt werden:  
  
-   format-number()  
  
-   formatNumber()  
  
-   current()  
  
-   element-available()  
  
-   function-available()  
  
-   system-property()  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Was format-number() und formatNumber() betrifft, so können Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] verwenden. Für die anderen nicht unterstützten Funktionen, die weiter oben aufgeführt sind, gibt es keine direkte Problemumgehung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
