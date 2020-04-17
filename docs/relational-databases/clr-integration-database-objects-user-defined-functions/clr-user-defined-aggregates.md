---
title: Benutzerdefinierte CLR-Aggregate | Microsoft Docs
description: Mit der SQL Server CLR-Integration können Sie benutzerdefinierte Aggregatfunktionen in verwaltetem Code erstellen, die eine Berechnung für eine Reihe von Werten durchführen und einen Wert zurückgeben.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: 9267e1e1e0b051dbbd8581b694aafacd2e5ce8a9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488289"
---
# <a name="clr-user-defined-aggregates"></a>Benutzerdefinierte CLR-Aggregate
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Aggregatfunktionen führen eine Berechnung für eine Gruppe von Werten durch und geben einen einzelnen Wert zurück. In der Vergangenheit hat [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur integrierte Aggregatfunktionen unterstützt, z. B. **SUM** oder **MAX**, die auf einem Satz von skalaren Eingabewerten basieren und einen einzelnen Aggregatwert aus diesem Satz generieren. Die Integration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-CLR (Common Language Runtime) ermöglicht Entwicklern jetzt, benutzerdefinierte Aggregatfunktionen in verwaltetem Code zu erstellen und diese Funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)] und anderen verwalteten Code zur Verfügung zu stellen.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Anforderungen für benutzerdefinierte CLR-Aggregate](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 Stellt eine Übersicht über die Anforderungen zum Implementieren von benutzerdefinierten CLR-Aggregatfunktionen bereit.  
  
 [Aufrufen von CLR-benutzerdefinierten Aggregatfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 Erläutert, wie benutzerdefinierte Aggregate aufgerufen werden.  
  
  
