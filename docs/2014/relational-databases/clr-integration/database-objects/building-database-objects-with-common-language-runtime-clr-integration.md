---
title: Aufbauen von Datenbankobjekten mit CLR (Common Language Runtime)-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: dd5717b545913bd9e5ee98debe670a1af616fc61
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953606"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>Erstellen von Datenbankobjekten mit CLR-Integration (Common Language Runtime)
  Sie können Datenbankobjekte mithilfe [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von erstellen, die als "CLR-Routine" bezeichnet wird. Es gibt folgende Routinen:  
  
-   Benutzerdefinierte Skalarwertfunktionen (Skalar-UDFs)  
  
-   Benutzerdefinierte Tabellenwertfunktionen (TVFs)  
  
-   Benutzerdefinierte Prozeduren (UDPs)  
  
-   Benutzerdefinierte Trigger  
  
 CLR-Routinen haben in verwaltetem Code dieselbe Struktur. Sie werden öffentlichen, statischen (freigegeben in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) Methoden einer Klasse zugeordnet. Außer Routinen können auch benutzerdefinierte Typen (UDTs) und benutzerdefinierte Aggregatfunktionen mithilfe von .NET Framework definiert werden. UDTs und benutzerdefinierte Aggregatfunktionen werden ganzen .NET Framework-Klassen zugeordnet.  
  
 Jeder Typ .NET Framework Routine verfügt über einen [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] , der [!INCLUDE[tsql](../../../includes/tsql-md.md)] verwendet werden kann. Skalar-UDFs können beispielsweise in jedem Skalarausdruck verwendet werden. Eine TVF kann in jeder FROM-Klausel verwendet werden. Eine Prozedur kann in einer EXEC-Anweisung oder von einer Clientanwendung aufgerufen werden.  
  
> [!NOTE]  
>  CLR-Objekte (benutzerdefinierte Funktion, benutzerdefinierter Typ oder Trigger)können auf der Common Language Runtime auf mehreren Threads (paralleler Plan) ausgeführt werden, wenn der Abfrageoptimierer feststellt, dass dies vorteilhaft ist. Benutzerdefinierte Funktionen, die auf Daten zugreifen, werden jedoch auf einem seriellen Plan ausgeführt. Bei Ausführung auf einer Serverversion vor [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] müssen benutzerdefinierte Funktionen, die LOB-Parameter oder Rückgabewerte enthalten, ebenfalls nach einem seriellen Plan ausgeführt werden.  
  
 In der folgenden Tabelle sind die in diesem Abschnitt behandelten Themen aufgeführt.  
  
 [Erste Schritte mit der CLR-Integration](getting-started-with-clr-integration.md)  
 Enthält eine kurze Übersicht über die Bibliotheken und Namespaces, die benötigt werden, um Objekte mithilfe der CLR-Integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu kompilieren. Enthält das Beispiel "Hello World" für eine CLR-gespeicherte Prozedur.  
  
 [Unterstützte .NET Framework-Bibliotheken](supported-net-framework-libraries.md)  
 Enthält Informationen zu den durch die CLR-Integration unterstützten .NET Framework-Bibliotheken.  
  
 [Beschränkungen des Programmiermodells für die CLR-Integration](clr-integration-programming-model-restrictions.md)  
 Enthält Informationen zu Beschränkungen des Programmiermodells für die CLR-Integration.  
  
 [SQL Server-Datentypen in .NET Framework](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 Eine Übersicht über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen und die .NET Framework-Entsprechungen.  
  
 [Übersicht über benutzerdefinierte Attribute der CLR-Integration](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 Enthält Informationen zu benutzerdefinierten Attributen der CLR-Integration.  
  
 [CLR-benutzerdefinierte Funktionen](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 Beschreibt die Implementierung und Verwendung der unterschiedlichen CLR-Funktionstypen: Tabellenwertfunktionen, Skalarfunktionen und benutzerdefinierte Aggregatfunktionen.  
  
 [Benutzerdefinierte CLR-Typen](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Beschreibt die Implementierung und Verwendung von CLR-benutzerdefinierten Typen.  
  
 [Gespeicherte CLR-Prozeduren](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 Beschreibt die Implementierung und Verwendung von CLR-gespeicherten Prozeduren.  
  
 [CLR-Trigger](../../../database-engine/dev-guide/clr-triggers.md)  
 Beschreibt die Implementierung und Verwendung von CLR-Triggern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über die CLR-&#41; Integration in Common Language Runtime &#40;](../common-language-runtime-integration-overview.md)  
  
  
