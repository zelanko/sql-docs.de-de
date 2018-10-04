---
title: Erstellen von CLR-Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b68531b962b10785927c6212b2483f2d9c1d7d3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049200"
---
# <a name="create-clr-triggers"></a>Erstellen von CLR-Triggern
  Sie können in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Datenbankobjekt erstellen, das in einer Assembly programmiert wird, die in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -CLR (Common Language Runtime) erstellt wurde. Datenbankobjekte, die das reichhaltige Programmiermodell nutzen können, das von der CLR (Common Language Runtime) bereitgestellt wird, sind z. B. DML-Trigger, DDL-Trigger, gespeicherte Prozeduren, Funktionen, Aggregatfunktionen und Typen.  
  
 Das Erstellen eines CLR-Triggers (DML oder DDL) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst folgende Schritte:  
  
-   Definieren des Triggers als Klasse in einer von .NET Framework unterstützten Sprache. Weitere Informationen zum Programmieren von Triggern in der CLR finden Sie unter [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md). Kompilieren Sie die Klasse mithilfe des entsprechenden Sprachcompilers, um eine Assembly in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] zu erstellen.  
  
-   Registrieren der Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der CREATE ASSEMBLY-Anweisung. Weitere Informationen zum Arbeiten mit Assemblys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Assemblys &amp;#40;Datenbank-Engine&amp;#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Erstellen Sie den Trigger, der auf die registrierte Assembly verweist.  
  
> [!NOTE]  
>  Bei der Bereitstellung eines SQL Server-Projekts in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird eine Assembly in der Datenbank registriert, die für das Projekt angegeben wurde. Bei der Bereitstellung des Projekts werden in der Datenbank auch CLR-Trigger für alle Methoden erstellt, die mit dem `SqlTrigger`-Attribut versehen sind. Weitere Informationen finden Sie unter [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Die Funktion zum Ausführen von CLR-Code ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standardmäßig deaktiviert. Sie können Datenbankobjekte, die auf verwaltete Codemodule verweisen, erstellen, ändern oder löschen. Diese Verweise werden jedoch nur dann in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt, wenn die Option [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) mithilfe von [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)aktiviert wird.  
  
 **So erstellen, ändern oder löschen Sie eine Assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **So erstellen Sie einen CLR-Trigger**  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [DML-Trigger](dml-triggers.md)   
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [Datenzugriff von CLR-Datenbankobjekten aus](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
