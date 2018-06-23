---
title: Sortierung und CLR-Integrationsdatentypen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71b0c61678bff1be69cbb761dd00067150a30b0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160449"
---
# <a name="collation-and-clr-integration-data-types"></a>Sortierung und Datentypen für die CLR-Integration
  In der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]die `CompareInfo` Objekt verarbeitet die Sortierungen. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Zeichenfolge Application programming Interfaces (APIs) verwenden die `CompareInfo` zugeordnete Eigenschaft der `CultureInfo` Objekt des aktuellen Threads um Zeichenfolgenvergleiche durchzuführen. Die Standardeinstellung des `CultureInfo`-Objekts basiert auf der Einstellung für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema des Computers, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Dies bestimmt die standardvergleichssemantik, wenn keine explizite `CultureInfo` angegeben wird, für Vergleiche von `System.String` Werte. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nimmt keine explizite Änderung der `CompareInfo` Eigenschaft, um die Datenbank- oder serversortierung. Falls erforderlich, müssen Benutzer die entsprechenden festlegen `CompareInfo` -Eigenschaft in ihren Routinen.  
  
## <a name="parameter-collation"></a>Parametersortierung  
 Wenn Sie eine CLR-Routine (Common Language Runtime) erstellen, und ein an die Routine gebundener Parameter einer CLR-Methode den Typ `SQLString` aufweist, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Instanz des Parameters mit der Standardsortierung der Datenbank, die die aufrufende Routine enthält. Wenn ein Parameter nicht vom Typ `SqlType` ist (beispielsweise `String`, nicht `SQLString`), werden die Sortierungsinformationen der Datenbank nicht mit dem Parameter verknüpft.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  