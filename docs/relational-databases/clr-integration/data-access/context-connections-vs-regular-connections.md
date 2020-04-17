---
title: Regelmäßige vs. Kontextverbindungen | Microsoft Docs
description: In SQL Server müssen Sie manchmal regelmäßige Verbindungen für Transact-SQL-Anweisungen verwenden, aber Kontextverbindungen bieten Vorteile bei der Leistung und Ressourcennutzung.
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
ms.openlocfilehash: 881b7463400665d22baaa9b19f13cb5949df0830
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485220"
---
# <a name="context-connections-vs-regular-connections"></a>Kontextverbindungen im Vergleich zu regulären Verbindungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn Sie eine Verbindung mit einem Remoteserver herstellen, verwenden Sie stets reguläre Verbindungen anstelle von Kontextverbindungen. Wenn Sie eine Verbindung mit dem Server herstellen müssen, auf dem die gespeicherte Prozedur oder Funktion ausgeführt wird, verwenden Sie in den meisten Fällen Kontextverbindungen. Dies hat Vorteile, etwa das Ausführen im gleichen Transaktionsbereich, ohne dass eine erneute Authentifizierung erforderlich ist.  
  
 Darüber hinaus führt das Verwenden der Kontextverbindung in der Regel zu einer höheren Leistung und geringeren Ressourcenverwendung. Die Kontextverbindung ist eine nur in-Process-Verbindung, sodass sie den Server "direkt" kontaktieren kann, indem sie das Netzwerkprotokoll und die Transportebenen umgeht, um Transact-SQL-Anweisungen zu senden und Ergebnisse zu empfangen. Der Authentifizierungsprozess wird ebenfalls umgangen. Die folgende Abbildung zeigt die primären Komponenten des **verwalteten SqlClient-Anbieters** sowie die Interaktion der verschiedenen Komponenten bei der Verwendung einer regulären Verbindung und bei verwendung der Kontextverbindung.  
  
 ![Codepfade einer Kontext- und einer regulären Verbindung](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Codepfade einer Kontext- und einer regulären Verbindung")  
  
 Die Kontextverbindung folgt einem kürzeren Codepfad und schließt weniger Komponenten ein, sodass Sie mit schnelleren Anforderungen und Ergebnissen an den Server und vom Server rechnen können als bei einer regulären Verbindung. Die Abfrageausführungszeit auf dem Server ist bei Kontext- und reguläre Verbindungen die gleiche.  
  
 In einigen Fällen müssen Sie möglicherweise eine separate reguläre Verbindung mit dem gleichen Server herstellen. Beispielsweise gibt es bestimmte Einschränkungen für die Verwendung der Kontextverbindung, die unter [Einschränkungen für reguläre und Kontextverbindungen](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)beschrieben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kontextverbindung](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
