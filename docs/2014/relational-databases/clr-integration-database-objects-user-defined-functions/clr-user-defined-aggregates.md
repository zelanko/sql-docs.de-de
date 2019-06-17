---
title: Benutzerdefinierte CLR-Aggregate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 59666e90a47d88762c6fc3bd1fabc0e71ea18f94
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919582"
---
# <a name="clr-user-defined-aggregates"></a>Benutzerdefinierte CLR-Aggregate
  Aggregatfunktionen führen Berechnungen für eine Wertemenge durch und geben einen einzelnen Wert zurück. In der Vergangenheit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt über nur integrierte Aggregatfunktionen unterstützt, z. B. `SUM` oder `MAX`, die auf einen Satz von skalaren Eingabewerten basieren und einen einzelnen Aggregatwert aus diesem Satz generieren. Die Integration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-CLR (Common Language Runtime) ermöglicht Entwicklern jetzt, benutzerdefinierte Aggregatfunktionen in verwaltetem Code zu erstellen und diese Funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)] und anderen verwalteten Code zur Verfügung zu stellen.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Anforderungen für benutzerdefinierte CLR-Aggregate](clr-user-defined-aggregates-requirements.md)  
 Stellt eine Übersicht über die Anforderungen zum Implementieren von benutzerdefinierten CLR-Aggregatfunktionen bereit.  
  
 [Aufrufen von benutzerdefinierten CLR-Aggregatfunktionen](clr-user-defined-aggregate-invoking-functions.md)  
 Erläutert, wie benutzerdefinierte Aggregate aufgerufen werden.  
  
  
