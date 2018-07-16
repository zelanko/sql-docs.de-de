---
title: Reguläre im Vergleich zu Kontextverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3ba21a813e019b94a51ad6a43e45faf64cd9f7b2
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352552"
---
# <a name="regular-vs-context-connections"></a>Reguläre im Vergleich zu Kontextverbindungen
  Wenn Sie eine Verbindung mit einem Remoteserver herstellen, verwenden Sie stets reguläre Verbindungen anstelle von Kontextverbindungen. Wenn Sie eine Verbindung mit dem Server herstellen müssen, auf dem die gespeicherte Prozedur oder Funktion ausgeführt wird, verwenden Sie in den meisten Fällen Kontextverbindungen. Dies hat Vorteile, etwa das Ausführen im gleichen Transaktionsbereich, ohne dass eine erneute Authentifizierung erforderlich ist.  
  
 Darüber hinaus führt das Verwenden der Kontextverbindung in der Regel zu einer höheren Leistung und geringeren Ressourcenverwendung. Die Kontextverbindung ist eine Verbindung, die nur innerhalb von Prozessen verwendet wird. Sie kann den Server "direkt" kontaktieren, indem sie das Netzwerkprotokoll und die Transportebenen umgeht, um Transact-SQL-Anweisungen zu senden und Ergebnisse zu empfangen. Der Authentifizierungsprozess wird ebenfalls umgangen. Die folgende Abbildung zeigt die primären Komponenten des `SqlClient`-verwalteten Anbieters und beschreibt, wie die verschiedenen Komponenten bei der Verwendung einer regulären und bei der Verwendung einer Kontextverbindung interagieren.  
  
 ![Codepfade einer Kontext-und einer regulären Verbindung. ] (../../../database-engine/dev-guide/media/clrintdataaccess.gif "Codepfade einer Kontext-und einer regulären Verbindung.")  
  
 Die Kontextverbindung folgt einem kürzeren Codepfad und schließt weniger Komponenten ein, sodass Sie mit schnelleren Anforderungen und Ergebnissen an den Server und vom Server rechnen können als bei einer regulären Verbindung. Die Abfrageausführungszeit auf dem Server ist bei Kontext- und reguläre Verbindungen die gleiche.  
  
 In einigen Fällen müssen Sie möglicherweise eine separate reguläre Verbindung mit dem gleichen Server herstellen. Beispielsweise stehen bestimmte Einschränkungen für die mithilfe der kontextverbindung, die in beschriebenen [Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen](context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Kontextverbindung](context-connection.md)  
  
  
