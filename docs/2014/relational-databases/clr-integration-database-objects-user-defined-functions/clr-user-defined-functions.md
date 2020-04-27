---
title: Benutzerdefinierte CLR-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f48a62e1dff2fbc1d226077c2271e8a8a71efb2e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874490"
---
# <a name="clr-user-defined-functions"></a>CLR-benutzerdefinierte Funktionen
  Benutzerdefinierte Funktionen sind Routinen, die Parameter annehmen, Berechnungen oder andere Aktionen ausführen und Ergebnisse zurückgeben können. Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] können Sie benutzerdefinierte Funktionen in jeder beliebigen [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Programmiersprache schreiben, beispielsweise in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Es sind zwei Arten von Funktionen verfügbar: Skalarfunktionen, die einen einzigen Wert zurückgeben, und Tabellenwertfunktionen, die einen Satz Zeilen zurückgeben.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [CLR-Skalarwertfunktionen](clr-scalar-valued-functions.md)  
 Beschreibt Implementierungsanforderungen und führt Beispiele für Skalarwertfunktionen an.  
  
 [CLR-Tabellenwertfunktionen](clr-table-valued-functions.md)  
 Erörtert, wie Tabellenwertfunktionen (Table-Valued Functions, TVFs) implementiert und verwendet werden, und beschreibt die Unterschiede zwischen [!INCLUDE[tsql](../../includes/tsql-md.md)]- und CLR-TVFs.  
  
 [Benutzerdefinierte CLR-Aggregate](clr-user-defined-aggregates.md)  
 Beschreibt die Implementierung und Verwendung von benutzerdefinierten Aggregaten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Funktionen](../user-defined-functions/user-defined-functions.md)  
  
  
