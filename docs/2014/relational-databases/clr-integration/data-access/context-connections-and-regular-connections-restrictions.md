---
title: Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0d266b75dad229a0784606af112c249728a112c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151354"
---
# <a name="restrictions-on-regular-and-context-connections"></a>Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen
  In diesem Thema wird erläutert, die Einschränkungen im Zusammenhang mit der Ausführung von Code in die [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] -Prozess durch kontextverbindungen und reguläre Verbindungen.  
  
## <a name="restrictions-on-context-connections"></a>Einschränkungen für Kontextverbindungen  
 Berücksichtigen Sie bei der Anwendungsentwicklung die folgenden Einschränkungen, die für Kontextverbindungen gelten:  
  
-   Zu einem bestimmten Zeitpunkt kann in einer gegebenen Verbindung nur eine Kontextverbindung bestehen. Wenn in verschiedenen Verbindungen mehrere Anweisungen gleichzeitig ausgeführt werden, kann jede dieser Verbindungen eine eigene Kontextverbindung erhalten. Die Einschränkung wirkt sich nicht auf gleichzeitige Anforderungen verschiedener Verbindungen aus, sondern sie gilt nur für eine gegebene Anforderung für eine gegebene Verbindung.  
  
-   MARS (Multiple Active Result Set) wird in einer Kontextverbindung nicht unterstützt.  
  
-   Die `SqlBulkCopy` -Klasse funktioniert in kontextverbindungen nicht.  
  
-   Die Batchverarbeitung von Updates wird in Kontextverbindungen nicht unterstützt  
  
-   `SqlNotificationRequest` kann nicht mit Befehlen verwendet werden, die für eine Kontextverbindung ausgeführt werden.  
  
-   Befehle, die für die Kontextverbindung ausgeführt werden, können nicht abgebrochen werden. Die `SqlCommand.Cancel`-Methode ignoriert die Anforderung stillschweigend.  
  
-   Wenn "context connection=true" verwendet wird, können keine anderen Schlüsselwörter in Verbindungszeichenfolgen angegeben werden.  
  
-   Die `SqlConnection.DataSource` Eigenschaft gibt null, wenn die Verbindungszeichenfolge für die `SqlConnection` ist "kontextverbindung = True", anstelle des Namens der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Die Festlegung der `SqlCommand.CommandTimeout`-Eigenschaft hat keine Auswirkungen, wenn der Befehl für eine Kontextverbindung ausgeführt wird.  
  
## <a name="restrictions-on-regular-connections"></a>Einschränkungen für reguläre Verbindungen  
 Berücksichtigen Sie bei der Anwendungsentwicklung die folgenden Einschränkungen, die für reguläre Verbindungen gelten:  
  
-   Die asynchrone Befehlsausführung mit internen Servern wird nicht unterstützt. Einschließlich "Async = True" in der Verbindungszeichenfolge einen Befehl, und klicken Sie dann Ausführen der Befehl führt `System.NotSupportedException` ausgelöst wird. Die folgende Meldung wird angezeigt: "Die asynchrone Verarbeitung wird bei einer Ausführung im Rahmen des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Prozesses nicht unterstützt".  
  
-   `SqlDependency` Objekt wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Kontextverbindung](context-connection.md)  
  
  