---
title: Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3b721409f0915cb1e13861f6481909e02af37cb2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919170"
---
# <a name="restrictions-on-regular-and-context-connections"></a>Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen
  In diesem Thema wird erläutert, die Einschränkungen im Zusammenhang mit der Ausführung von Code in die [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] -Prozess durch kontextverbindungen und reguläre Verbindungen.  
  
## <a name="restrictions-on-context-connections"></a>Einschränkungen für Kontextverbindungen  
 Berücksichtigen Sie bei der Anwendungsentwicklung die folgenden Einschränkungen, die für Kontextverbindungen gelten:  
  
-   Zu einem bestimmten Zeitpunkt kann in einer gegebenen Verbindung nur eine Kontextverbindung bestehen. Wenn in verschiedenen Verbindungen mehrere Anweisungen gleichzeitig ausgeführt werden, kann jede dieser Verbindungen eine eigene Kontextverbindung erhalten. Die Einschränkung wirkt sich nicht auf gleichzeitige Anforderungen verschiedener Verbindungen aus, sondern sie gilt nur für eine gegebene Anforderung für eine gegebene Verbindung.  
  
-   MARS (Multiple Active Result Set) wird in einer Kontextverbindung nicht unterstützt.  
  
-   Die `SqlBulkCopy`-Klasse funktioniert in Kontextverbindungen nicht.  
  
-   Die Batchverarbeitung von Updates wird in Kontextverbindungen nicht unterstützt  
  
-   `SqlNotificationRequest` kann nicht mit Befehlen verwendet werden, die für eine Kontextverbindung ausgeführt werden.  
  
-   Befehle, die für die Kontextverbindung ausgeführt werden, können nicht abgebrochen werden. Die `SqlCommand.Cancel`-Methode ignoriert die Anforderung stillschweigend.  
  
-   Wenn "context connection=true" verwendet wird, können keine anderen Schlüsselwörter in Verbindungszeichenfolgen angegeben werden.  
  
-   Die `SqlConnection.DataSource`-Eigenschaft gibt NULL zurück, wenn in der Verbindungszeichenfolge für `SqlConnection` "context connection=true" statt des Namens der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz angegeben wird.  
  
-   Die Festlegung der `SqlCommand.CommandTimeout`-Eigenschaft hat keine Auswirkungen, wenn der Befehl für eine Kontextverbindung ausgeführt wird.  
  
## <a name="restrictions-on-regular-connections"></a>Einschränkungen für reguläre Verbindungen  
 Berücksichtigen Sie bei der Anwendungsentwicklung die folgenden Einschränkungen, die für reguläre Verbindungen gelten:  
  
-   Die asynchrone Befehlsausführung mit internen Servern wird nicht unterstützt. Wenn in der Verbindungszeichenfolge eines Befehls "async=true" angegeben wird, dann führt die Ausführung des Befehls dazu, dass die `System.NotSupportedException`-Ausnahme ausgelöst wird. Diese Meldung wird angezeigt: "Asynchroner Verarbeitung wird nicht unterstützt, wenn die Ausführung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Prozess."  
  
-   Das `SqlDependency`-Objekt wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Kontextverbindung](context-connection.md)  
  
  
