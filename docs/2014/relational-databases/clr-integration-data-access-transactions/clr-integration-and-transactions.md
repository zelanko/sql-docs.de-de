---
title: CLR-Integration und Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955054"
---
# <a name="clr-integration-and-transactions"></a>CLR-Integration und Transaktionen
  Durch den `System.Transactions`-Namespace wird ein neues Transaktionsframework bereitgestellt, das voll in ADO.NET und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR (Common Language Runtime) integriert ist. `System.Transactions` und ADO.NET greifen ineinander, um die Verwendung lokaler und verteilter Transaktionen in verwalteten Anwendungen zu erweitern und zu vereinfachen.  
  
> [!NOTE]  
>  Eine CLR-benutzerdefinierte Prozedur (UDP) kann keine Verbindung zu dem gleichen Server herstellen, auf dem sie ausgeführt wird (Loopbackverbindung), und sich in die gleiche Transaktion eintragen. Wird ein solcher Versuch unternommen, wird die Verbindung blockiert und die Kontrolle nicht wieder an die benutzerdefinierte Prozedur übergeben. Dies führt für die benutzerdefinierte Prozedur zu einem Timeoutfehler (Msg 1206).  
  
 Weitere Informationen zu Transaktionen und .NET Framework finden Sie in den Abschnitten zum Ausführen von Transaktionen und zur Nutzung von Transaktionen im .NET Framework SDK.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Transaktionshöherstufung](transaction-promotion.md)  
 Beschreibt die Möglichkeit der Höherstufung von Transaktionen und die Verwendung dieser Funktion.  
  
 [Zugriff auf die aktuelle Transaktion](accessing-the-current-transaction.md)  
 Beschreibt, wie auf eine Transaktion, die gerade auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prozessintern ausgeführt wird, zugegriffen wird.  
  
 [Verwenden von 'System.Transactions'](../native-client-ole-db-transactions/transactions.md)  
 Beschreibt, wie die `System.Transactions`-Anwendungsprogrammierschnittstelle (API) in der verwalteten Anwendung verwendet wird.  
  
 [Lebensdauer von Transaktionen](transaction-lifetimes.md)  
 Beschreibt den Unterschied in der Lebensdauer von Transaktionen, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]-gespeicherten Prozeduren gestartet wurden, und Transaktionen, die in CLR-Anwendungen gestartet wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Access from CLR Database Objects](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
