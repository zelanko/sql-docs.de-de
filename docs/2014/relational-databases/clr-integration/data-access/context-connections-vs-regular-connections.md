---
title: Reguläre vs. Kontextverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f4255e17f7cd76cf402c10d84b015a1324d7d6f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874050"
---
# <a name="regular-vs-context-connections"></a>Reguläre vs. Kontextverbindungen
  Wenn Sie eine Verbindung mit einem Remoteserver herstellen, verwenden Sie stets reguläre Verbindungen anstelle von Kontextverbindungen. Wenn Sie eine Verbindung mit dem Server herstellen müssen, auf dem die gespeicherte Prozedur oder Funktion ausgeführt wird, verwenden Sie in den meisten Fällen Kontextverbindungen. Dies hat Vorteile, etwa das Ausführen im gleichen Transaktionsbereich, ohne dass eine erneute Authentifizierung erforderlich ist.  
  
 Darüber hinaus führt das Verwenden der Kontextverbindung in der Regel zu einer höheren Leistung und geringeren Ressourcenverwendung. Die kontextverbindung ist eine in-Process-Verbindung, die nur kontaktieren, können den Server "direkt", indem Sie die vermittlungsschichten protokollkanäle und zum Senden von Transact-SQL-Anweisungen und Empfangen von Ergebnissen umgehen. Der Authentifizierungsprozess wird ebenfalls umgangen. Die folgende Abbildung zeigt die primären Komponenten des `SqlClient`-verwalteten Anbieters und beschreibt, wie die verschiedenen Komponenten bei der Verwendung einer regulären und bei der Verwendung einer Kontextverbindung interagieren.  
  
 ![Codepfade einer Kontext-und einer regulären Verbindung. ](../../../database-engine/dev-guide/media/clrintdataaccess.gif "Codepfade einer Kontext-und einer regulären Verbindung.")  
  
 Die Kontextverbindung folgt einem kürzeren Codepfad und schließt weniger Komponenten ein, sodass Sie mit schnelleren Anforderungen und Ergebnissen an den Server und vom Server rechnen können als bei einer regulären Verbindung. Die Abfrageausführungszeit auf dem Server ist bei Kontext- und reguläre Verbindungen die gleiche.  
  
 In einigen Fällen müssen Sie möglicherweise eine separate reguläre Verbindung mit dem gleichen Server herstellen. Beispielsweise stehen bestimmte Einschränkungen für die mithilfe der kontextverbindung, die in beschriebenen [Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen](context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Kontextverbindung](context-connection.md)  
  
  
