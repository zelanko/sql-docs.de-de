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
ms.openlocfilehash: d1ef5d07fe082d0eeb2c3484d6e99572d8fc80e5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954618"
---
# <a name="clr-user-defined-aggregates"></a>Benutzerdefinierte CLR-Aggregate
  Aggregatfunktionen führen eine Berechnung für eine Gruppe von Werten durch und geben einen einzelnen Wert zurück. Hat traditionell [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur integrierte Aggregatfunktionen unterstützt, wie z. b. `SUM` oder `MAX` , die für einen Satz von skalaren Eingabe Werten verwendet werden und einen einzelnen Aggregatwert aus diesem Satz generieren. Die Integration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-CLR (Common Language Runtime) ermöglicht Entwicklern jetzt, benutzerdefinierte Aggregatfunktionen in verwaltetem Code zu erstellen und diese Funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)] und anderen verwalteten Code zur Verfügung zu stellen.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Anforderungen für benutzerdefinierte CLR-Aggregate](clr-user-defined-aggregates-requirements.md)  
 Stellt eine Übersicht über die Anforderungen zum Implementieren von benutzerdefinierten CLR-Aggregatfunktionen bereit.  
  
 [Aufrufen von CLR-benutzerdefinierten Aggregatfunktionen](clr-user-defined-aggregate-invoking-functions.md)  
 Erläutert, wie benutzerdefinierte Aggregate aufgerufen werden.  
  
  
