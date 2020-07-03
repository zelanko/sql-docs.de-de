---
title: Common Language Runtime (CLR)-Build-Datenbankobjekte
description: Erstellen Sie Datenbankobjekte mithilfe der SQL Server Integration in die .NET Framework Common Language Runtime (CLR).
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
ms.openlocfilehash: 75521866bd7fb151921e972bf4ee1d49089dd5a6
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85885911"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>Erstellen von Datenbankobjekten mit CLR-Integration (Common Language Runtime)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Datenbankobjekte können mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Integration in .NET Framework Common Language Runtime (CLR) erstellt werden. Verwalteter Code, der in ausgeführt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird, wird als "CLR-Routine" bezeichnet. Es gibt folgende Routinen:  
  
-   Benutzerdefinierte Skalarwertfunktionen (Skalar-UDFs)  
  
-   Benutzerdefinierte Tabellenwertfunktionen (TVFs)  
  
-   Benutzerdefinierte Prozeduren (UDPs)  
  
-   Benutzerdefinierte Trigger  
  
 CLR-Routinen haben in verwaltetem Code dieselbe Struktur. Sie werden öffentlichen, statischen (freigegeben in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) Methoden einer Klasse zugeordnet. Außer Routinen können auch benutzerdefinierte Typen (UDTs) und benutzerdefinierte Aggregatfunktionen mithilfe von .NET Framework definiert werden. UDTs und benutzerdefinierte Aggregatfunktionen werden ganzen .NET Framework-Klassen zugeordnet.  
  
 Jeder .NET Framework-Routinentyp verfügt über eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Deklaration und kann überall da in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden, wo die [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Entsprechung verwendet werden kann. Skalar-UDFs können beispielsweise in jedem Skalarausdruck verwendet werden. Eine TVF kann in jeder FROM-Klausel verwendet werden. Eine Prozedur kann in einer EXEC-Anweisung oder von einer Clientanwendung aufgerufen werden.  
  
> [!NOTE]  
>  CLR-Objekte (benutzerdefinierte Funktion, benutzerdefinierter Typ oder Trigger)können auf der Common Language Runtime auf mehreren Threads (paralleler Plan) ausgeführt werden, wenn der Abfrageoptimierer feststellt, dass dies vorteilhaft ist. Benutzerdefinierte Funktionen, die auf Daten zugreifen, werden jedoch auf einem seriellen Plan ausgeführt. Bei Ausführung auf einer Serverversion vor [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] müssen benutzerdefinierte Funktionen, die LOB-Parameter oder Rückgabewerte enthalten, ebenfalls nach einem seriellen Plan ausgeführt werden.  
  
 In der folgenden Tabelle sind die in diesem Abschnitt behandelten Themen aufgeführt.  
  
 [Erste Schritte mit der CLR-Integration](../../../relational-databases/clr-integration/database-objects/getting-started-with-clr-integration.md)  
 Enthält eine kurze Übersicht über die Bibliotheken und Namespaces, die benötigt werden, um Objekte mithilfe der CLR-Integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu kompilieren. Enthält das Beispiel "Hello World" für eine CLR-gespeicherte Prozedur.  
  
 [Unterstützte .NET Framework-Bibliotheken](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)  
 Enthält Informationen zu den durch die CLR-Integration unterstützten .NET Framework-Bibliotheken.  
  
 [Beschränkungen des Programmiermodells für die CLR-Integration](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
 Enthält Informationen zu Beschränkungen des Programmiermodells für die CLR-Integration.  
  
 [SQL Server-Datentypen in .NET Framework](../../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 Eine Übersicht über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen und die .NET Framework-Entsprechungen.  
  
 [Übersicht über benutzerdefinierte Attribute der CLR-Integration](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)  
 Enthält Informationen zu benutzerdefinierten Attributen der CLR-Integration.  
  
 [CLR-benutzerdefinierte Funktionen](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 Beschreibt die Implementierung und Verwendung der unterschiedlichen CLR-Funktionstypen: Tabellenwertfunktionen, Skalarfunktionen und benutzerdefinierte Aggregatfunktionen.  
  
 [Benutzerdefinierte CLR-Typen](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Beschreibt die Implementierung und Verwendung von CLR-benutzerdefinierten Typen.  
  
 [Gespeicherte CLR-Prozeduren](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)  
 Beschreibt die Implementierung und Verwendung von CLR-gespeicherten Prozeduren.  
  
 [CLR-Trigger](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
 Beschreibt die Implementierung und Verwendung von CLR-Triggern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über die CLR-&#41; Integration in Common Language Runtime &#40;](../../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
  
  
