---
title: CLR-Integration und Transaktionen | Microsoft-Dokumentation
description: Für CLR-Integration und-Transaktionen arbeiten System. Transactions und ADO.net zusammen, um die Verwendung lokaler und verteilter Transaktionen in verwalteten Anwendungen zu erweitern und zu vereinfachen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: bd65fce2f2a2bdf2ce25f4811063f7f9d56d2e15
ms.sourcegitcommit: 36fe62a3ccf34979bfde3e192cfa778505add465
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94521133"
---
# <a name="clr-integration-and-transactions"></a>CLR-Integration und Transaktionen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Durch den **System.Transactions** -Namespace wird ein neues Transaktionsframework bereitgestellt, das voll in ADO.NET und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR (Common Language Runtime) integriert ist. **System. Transactions** und ADO.NET arbeiten zusammen, um die Verwendung lokaler und verteilter Transaktionen in verwalteten Anwendungen zu erweitern und zu vereinfachen.  
  
> [!NOTE]  
>  Eine CLR-benutzerdefinierte Prozedur (UDP) kann keine Verbindung zu dem gleichen Server herstellen, auf dem sie ausgeführt wird (Loopbackverbindung), und sich in die gleiche Transaktion eintragen. Wird ein solcher Versuch unternommen, wird die Verbindung blockiert und die Kontrolle nicht wieder an die benutzerdefinierte Prozedur übergeben. Dies führt für die benutzerdefinierte Prozedur zu einem Timeoutfehler (Msg 1206).  
  
 Weitere Informationen zu Transaktionen und .NET Framework finden Sie in den Abschnitten zum Ausführen von Transaktionen und zur Nutzung von Transaktionen im .NET Framework SDK.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Transaktionshöherstufung](../../relational-databases/clr-integration-data-access-transactions/transaction-promotion.md)  
 Beschreibt die Möglichkeit der Höherstufung von Transaktionen und die Verwendung dieser Funktion.  
  
 [Zugriff auf die aktuelle Transaktion](../../relational-databases/clr-integration-data-access-transactions/accessing-the-current-transaction.md)  
 Beschreibt, wie auf eine Transaktion, die gerade auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prozessintern ausgeführt wird, zugegriffen wird.  
  
 [Verwenden von 'System.Transactions'](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)  
 Beschreibt die Verwendung der **System. Transactions** -API (Application Programming Interface) in der verwalteten Anwendung.  
  
 [Lebensdauer von Transaktionen](../../relational-databases/clr-integration-data-access-transactions/transaction-lifetimes.md)  
 Beschreibt den Unterschied in der Lebensdauer von Transaktionen, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]-gespeicherten Prozeduren gestartet wurden, und Transaktionen, die in CLR-Anwendungen gestartet wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
