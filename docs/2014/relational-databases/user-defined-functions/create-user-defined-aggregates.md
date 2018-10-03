---
title: Erstellen benutzerdefinierter Aggregate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 23d5180928f4f3335aa17dff61b50e6fdd19549f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157140"
---
# <a name="create-user-defined-aggregates"></a>Erstellen benutzerdefinierter Aggregate
  Sie können ein Datenbankobjekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen, das in einer CLR-Assembly programmiert wird. Datenbankobjekte, die das reichhaltige Programmiermodell nutzen können, das von der CLR (Common Language Runtime) bereitgestellt wird, sind z. B. Trigger, gespeichert Prozeduren, Funktionen, Aggregatfunktionen und Typen.  
  
 Ebenso wie die integrierten Aggregatfunktionen, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]bereitgestellt werden, führen benutzerdefinierte Aggregatfunktionen Berechnungen für eine Menge von Werten aus und geben einen einzelnen Wert zurück.  
  
 Das Erstellen einer benutzerdefinierten Aggregatfunktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst die folgenden Schritte:  
  
-   Definieren der benutzerdefinierten Aggregatfunktion als Klasse in einer von [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework unterstützten Sprache. Weitere Informationen zum Programmieren benutzerdefinierter Aggregate in der CLR finden Sie unter [Benutzerdefinierte CLR-Aggregate](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md). Kompilieren dieser Klasse mithilfe des entsprechenden Sprachcompilers, um eine Assembly zu erstellen.  
  
-   Registrieren der Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der CREATE ASSEMBLY-Anweisung. Weitere Informationen zum Arbeiten mit Assemblys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Assemblys &amp;#40;Datenbank-Engine&amp;#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Erstellen des benutzerdefinierten Aggregats, das auf die registrierte Assembly verweist, mithilfe der CREATE AGGREGATE-Anweisung.  
  
> [!NOTE]  
>  Bei der Bereitstellung eines SQL Server-Projekts in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird eine Assembly in der Datenbank registriert, die für das Projekt angegeben wurde. Beim Bereitstellen des Projekts wird in der Datenbank auch ein benutzerdefiniertes Aggregat für alle Klassendefinitionen erstellt, die mit dem `SqlUserDefinedAggregate`-Attribut versehen sind. Weitere Informationen finden Sie unter [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Die Funktion zum Ausführen von CLR-Code ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standardmäßig deaktiviert. Sie können Datenbankobjekte, die auf verwaltete Codemodule verweisen, erstellen, ändern oder löschen; diese Verweise werden jedoch nur dann in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt, wenn die [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) -Option mithilfe von [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)aktiviert wird.  
  
 **So erstellen, ändern oder löschen Sie eine Assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **So erstellen Sie ein benutzerdefiniertes Aggregat**  
  
-   [CREATE AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
