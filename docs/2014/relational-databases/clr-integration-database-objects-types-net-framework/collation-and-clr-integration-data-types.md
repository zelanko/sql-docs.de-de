---
title: Sortierung und Datentypen für CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 56206f6273b413a66a72b2a2c72ed3593b2f9a66
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354682"
---
# <a name="collation-and-clr-integration-data-types"></a>Sortierung und Datentypen für die CLR-Integration
  In der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], `CompareInfo` Objekt verarbeitet die Sortierungen. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Application programming Interfaces (APIs) verwenden eine Zeichenfolge der `CompareInfo` zugeordnete Eigenschaft die `CultureInfo` Objekt des aktuellen Threads um Zeichenfolgenvergleiche durchzuführen. Die Standardeinstellung des `CultureInfo`-Objekts basiert auf der Einstellung für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema des Computers, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Dadurch wird bestimmt die standardvergleichssemantik, wenn keine explizite `CultureInfo` angegeben wird, bei Vergleichen von `System.String` Werte. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nimmt keine explizite Änderung der `CompareInfo` Eigenschaft, um die Datenbank- oder serversortierung. Wenn erforderlich, müssen Benutzer die entsprechenden legen `CompareInfo` -Eigenschaft in ihren Routinen.  
  
## <a name="parameter-collation"></a>Parametersortierung  
 Wenn Sie eine CLR-Routine (Common Language Runtime) erstellen, und ein an die Routine gebundener Parameter einer CLR-Methode den Typ `SQLString` aufweist, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Instanz des Parameters mit der Standardsortierung der Datenbank, die die aufrufende Routine enthält. Wenn ein Parameter nicht vom Typ `SqlType` ist (beispielsweise `String`, nicht `SQLString`), werden die Sortierungsinformationen der Datenbank nicht mit dem Parameter verknüpft.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
