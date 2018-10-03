---
title: Reguläre vs. Kontextverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
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
ms.openlocfilehash: 63fd25aa796be6f0fce27bfbfa5b7da36d35e2d8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619598"
---
# <a name="context-connections-vs-regular-connections"></a>Kontextverbindungen vs. reguläre Verbindungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn Sie eine Verbindung mit einem Remoteserver herstellen, verwenden Sie stets reguläre Verbindungen anstelle von Kontextverbindungen. Wenn Sie eine Verbindung mit dem Server herstellen müssen, auf dem die gespeicherte Prozedur oder Funktion ausgeführt wird, verwenden Sie in den meisten Fällen Kontextverbindungen. Dies hat Vorteile, etwa das Ausführen im gleichen Transaktionsbereich, ohne dass eine erneute Authentifizierung erforderlich ist.  
  
 Darüber hinaus führt das Verwenden der Kontextverbindung in der Regel zu einer höheren Leistung und geringeren Ressourcenverwendung. Die Kontextverbindung ist eine Verbindung, die nur innerhalb von Prozessen verwendet wird. Sie kann den Server "direkt" kontaktieren, indem sie das Netzwerkprotokoll und die Transportebenen umgeht, um Transact-SQL-Anweisungen zu senden und Ergebnisse zu empfangen. Der Authentifizierungsprozess wird ebenfalls umgangen. Die folgende Abbildung zeigt die primären Komponenten von der **SqlClient** verwalteten Anbieter als auch wie die verschiedenen Komponenten miteinander interagieren, wenn eine reguläre Verbindung verwenden und mithilfe der kontextverbindung.  
  
 ![Codepfade einer Kontext-und einer regulären Verbindung. ](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Codepfade einer Kontext-und einer regulären Verbindung.")  
  
 Die Kontextverbindung folgt einem kürzeren Codepfad und schließt weniger Komponenten ein, sodass Sie mit schnelleren Anforderungen und Ergebnissen an den Server und vom Server rechnen können als bei einer regulären Verbindung. Die Abfrageausführungszeit auf dem Server ist bei Kontext- und reguläre Verbindungen die gleiche.  
  
 In einigen Fällen müssen Sie möglicherweise eine separate reguläre Verbindung mit dem gleichen Server herstellen. Beispielsweise stehen bestimmte Einschränkungen für die mithilfe der kontextverbindung, die in beschriebenen [Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Kontextverbindung](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
