---
title: Erstellen von CLR-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-udf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CLR functions [SQL Server]
- user-defined functions [SQL Server], CLR
ms.assetid: a82df075-2243-4e19-bfe1-ae6d65dabd0f
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 46858c9e7d5f05367d48dc55bce8ea29b22f8f2a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047343"
---
# <a name="create-clr-functions"></a>Erstellen von CLR-Funktionen
  Sie können ein Datenbankobjekt in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen, das in einer Assembly programmiert wird, die in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -CLR (Common Language Runtime) erstellt wird. Datenbankobjekte, die das reichhaltige Programmiermodell nutzen können, das von der Common Language Runtime bereitgestellt wird, sind z. B. Aggregatfunktionen, Funktionen, gespeicherte Prozeduren, Trigger und Typen.  
  
 Zum Erstellen einer CLR-Funktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] müssen folgende Schritte ausgeführt werden:  
  
-   Definieren der Funktion als statische Methode einer Klasse in einer Sprache, die von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]unterstützt wird. Weitere Informationen zum Programmieren von Funktionen in der Common Language Runtime finden Sie unter [Benutzerdefinierte CLR-Funktionen](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md). Kompilieren Sie die Klasse mithilfe des entsprechenden Sprachcompilers, um eine Assembly in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] zu erstellen.  
  
-   Registrieren der Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der CREATE ASSEMBLY-Anweisung. Weitere Informationen zum Arbeiten mit Assemblys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Assemblys &amp;#40;Datenbank-Engine&amp;#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Erstellen der Funktion, die auf die registrierte Assembly verweist, mithilfe der [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) -Anweisung.  
  
> [!NOTE]  
>  Bei der Bereitstellung eines SQL Server-Projekts in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird eine Assembly in der Datenbank registriert, die für das Projekt angegeben wurde. Bei der Bereitstellung des Projekts werden auch CLR-Funktionen in der Datenbank für alle Methoden erstellt, die mit dem `SqlFunction`-Attribut versehen sind. Weitere Informationen finden Sie unter [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Die Funktion zum Ausführen von CLR-Code ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standardmäßig deaktiviert. Sie können Datenbankobjekte, die auf verwaltete Codemodule verweisen, erstellen, ändern oder löschen; diese Verweise werden jedoch nur dann in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt, wenn die Option [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) mithilfe von [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)aktiviert wird.  
  
## <a name="accessing-external-resources"></a>Zugreifen auf externe Ressourcen  
 CLR-Funktionen können verwendet werden, um auf externe Ressourcen wie z. B. Dateien, Netzwerkressourcen, Webdienste oder andere Datenbanken (einschließlich Remoteinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) zuzugreifen. Hierzu können in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]verschiedene Klassen verwendet werden, wie `System.IO`, `System.WebServices`, `System.Sql`usw. Die Assembly, die solche Funktionen enthält, sollte für diesen Zweck mindestens mit der EXTERNAL_ACCESS-Berechtigung konfiguriert werden. Weitere Informationen finden Sie unter [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)unterstützt wird. Der verwaltete Anbieter von SQL Client kann für den Zugriff auf Remoteinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden. Loopbackverbindungen mit dem ursprünglichen Server werden in CLR-Funktionen jedoch nicht unterstützt.  
  
 **So erstellen, ändern oder löschen Sie Assemblys in SQL Server**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **So erstellen Sie eine CLR-Funktion**  
  
-   [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)  
  
## <a name="accessing-native-code"></a>Zugreifen auf systemeigenen Code  
 CLR-Funktionen können für den Zugriff auf nativen (nicht verwalteten) Code verwendet werden, z.B. in C oder C++ geschriebenen Code. Dazu wird PInvoke vom verwalteten Code aus ausgeführt (Einzelheiten finden Sie unter [Aufrufen nativer Funktionen aus verwaltetem Code](http://go.microsoft.com/fwlink/?LinkID=181929) ). Dies kann die Wiederverwendung von Legacycode als CLR-UDFs oder das Programmieren leistungskritischer UDFs in systemeigenem Code ermöglichen. Die Verwendung einer UNSAFE-Assembly wird in diesem Fall vorausgesetzt. Warnhinweise zur Verwendung von UNSAFE-Assemblys finden Sie unter [CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md) .  
  
## <a name="see-also"></a>Siehe auch  
 
  [Erstellen benutzerdefinierter Funktionen &amp;#40;Datenbank-Engine&amp;#41;](create-user-defined-functions-database-engine.md)   
 [Erstellen benutzerdefinierter Aggregate](create-user-defined-aggregates.md)   
 [Ausführen von benutzerdefinierten Funktionen](execute-user-defined-functions.md)   
 [Anzeigen benutzerdefinierter Funktionen](view-user-defined-functions.md)   
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
