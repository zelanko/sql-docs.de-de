---
title: Sortierung und Datentypen für CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 40c4abad803424ac9b274045f699785b85689644
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62874846"
---
# <a name="collation-and-clr-integration-data-types"></a>Sortierung und Datentypen für die CLR-Integration
  In [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] werden Sortierungen vom `CompareInfo`-Objekt gehandhabt. Die Zeichenfolgen-APIs (Application Programming Interface, API) von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] verwenden die `CompareInfo`-Eigenschaft zusammen mit dem `CultureInfo`-Objekt des aktuellen Threads, um Zeichenfolgenvergleiche durchzuführen. Die Standardeinstellung des `CultureInfo`-Objekts basiert auf der Einstellung für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema des Computers, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Dies bestimmt die Standardvergleichssemantik bei Vergleichen von `CultureInfo`-Werten, wenn `System.String` nicht explizit angegeben wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändert die `CompareInfo`-Eigenschaft nicht explizit in die Datenbank- oder Serversortierung. Falls erforderlich, müssen Benutzer die entsprechende `CompareInfo`-Eigenschaft in ihren Routinen festlegen.  
  
## <a name="parameter-collation"></a>Parametersortierung  
 Wenn Sie eine CLR-Routine (Common Language Runtime) erstellen, und ein an die Routine gebundener Parameter einer CLR-Methode den Typ `SQLString` aufweist, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Instanz des Parameters mit der Standardsortierung der Datenbank, die die aufrufende Routine enthält. Wenn ein Parameter nicht vom Typ `SqlType` ist (beispielsweise `String`, nicht `SQLString`), werden die Sortierungsinformationen der Datenbank nicht mit dem Parameter verknüpft.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
