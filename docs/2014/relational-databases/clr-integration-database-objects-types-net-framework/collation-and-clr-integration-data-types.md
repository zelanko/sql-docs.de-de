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
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069900"
---
# <a name="collation-and-clr-integration-data-types"></a>Sortierung und Datentypen für die CLR-Integration
  In der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], `CompareInfo` Objekt verarbeitet die Sortierungen. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Application programming Interfaces (APIs) verwenden eine Zeichenfolge der `CompareInfo` zugeordnete Eigenschaft die `CultureInfo` Objekt des aktuellen Threads um Zeichenfolgenvergleiche durchzuführen. Die Standardeinstellung des `CultureInfo`-Objekts basiert auf der Einstellung für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema des Computers, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Dadurch wird bestimmt die standardvergleichssemantik, wenn keine explizite `CultureInfo` angegeben wird, bei Vergleichen von `System.String` Werte. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nimmt keine explizite Änderung der `CompareInfo` Eigenschaft, um die Datenbank- oder serversortierung. Wenn erforderlich, müssen Benutzer die entsprechenden legen `CompareInfo` -Eigenschaft in ihren Routinen.  
  
## <a name="parameter-collation"></a>Parametersortierung  
 Wenn Sie eine CLR-Routine (Common Language Runtime) erstellen, und ein an die Routine gebundener Parameter einer CLR-Methode den Typ `SQLString` aufweist, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Instanz des Parameters mit der Standardsortierung der Datenbank, die die aufrufende Routine enthält. Wenn ein Parameter nicht vom Typ `SqlType` ist (beispielsweise `String`, nicht `SQLString`), werden die Sortierungsinformationen der Datenbank nicht mit dem Parameter verknüpft.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
