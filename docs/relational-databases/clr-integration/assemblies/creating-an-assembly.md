---
title: Erstellen einer Assembly | Microsoft-Dokumentation
description: Mithilfe von Create Assembly können Sie eine Assembly in SQL Server registrieren und deren Sicherheitseinstellungen angeben. Registrieren Sie eine Assembly, um ihre Funktionalität zu verwenden.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 724f0fc6a38388d9366f3c46090ddaf22cd64a34
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85887808"
---
# <a name="creating-an-assembly"></a>Erstellen von Assemblys
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Verwaltete Datenbankobjekte wie beispielsweise gespeicherte Prozeduren und Trigger werden kompiliert und dann in so genannten Assemblys bereitgestellt. Verwaltete DLL-Assemblys müssen in registriert werden, damit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die von der Assembly bereitgestellte Funktionalität verwendet werden kann. Assemblys werden über die CREATE ASSEMBLY-Anweisung in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank registriert. In diesem Thema wird erläutert, wie Sie eine Assembly mithilfe der CREATE ASSEMBLY-Anweisung in einer Datenbank registrieren und wie Sie die Sicherheitseinstellungen für die Assembly festlegen.  
  
## <a name="the-create-assembly-statement"></a>Die CREATE ASSEMBLY-Anweisung  
 Die CREATE ASSEMBLY-Anweisung dient zum Erstellen einer Assembly in einer Datenbank. Beispiel:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Die FROM-Klausel legt den Pfadnamen der zu erstellenden Assembly fest. Bei diesem Pfad kann es sich entweder um einen UNC-Pfad (Universal Naming Convention) oder einen physischen Dateipfad handeln, der sich lokal auf dem Rechner befindet.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist es nicht zulässig, verschiedene Versionen einer Assembly mit demselben Namen, derselben Kultur und demselben öffentlichen Schlüssel zu registrieren.  
  
 Es ist möglich, Assemblys zu erstellen, die auf andere Assemblys verweisen. Wenn eine Assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]erstellt wird, erstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] außerdem die in der Stammebenen-Assembly referenzierten Assemblys, falls die referenzierten Assemblys nicht bereits in der Datenbank vorhanden sind.  
  
 Datenbankbenutzer oder Benutzerrollen erhalten Berechtigungen zum Erstellen von Assemblys in einer Datenbank, deren Besitzer sie dann sind. Um Assemblys zu erstellen, benötigt der Datenbankbenutzer oder die Rolle die CREATE ASSEMBLY-Berechtigung.  
  
 Eine Assembly kann nur unter folgenden Voraussetzungen erfolgreich auf andere Assemblys verweisen:  
  
-   Die Assembly, die aufgerufen wird oder auf die verwiesen wird, gehört dem gleichen Benutzer oder der Rolle.  
  
-   Die Assembly, die aufgerufen wird oder auf die verwiesen wird, wurde in derselben Datenbank erstellt.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Festlegen der Sicherheit beim Erstellen von Assemblys  
 Wenn Sie eine Assembly in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank erstellenerstellt wird, erstellt können Sie eine von drei verschiedenen Sicherheitsstufen festlegenerstellt wird, erstellt mit der der Code ausgeführt werden soll: **SAFE**erstellt wird, erstellt **EXTERNAL_ACCESS**erstellt wird, erstellt or **UNSAFE**. Beim Ausführen der **CREATE ASSEMBLY** -Anweisung werden bestimmte Überprüfungen für die Code-Assembly durchgeführt, aufgrund derer die Assembly möglicherweise nicht beim Server registriert werden kann. Weitere Informationen finden Sie unter dem Beispiel für den Identitätswechsel auf [CodePlex](https://msftengprodsamples.codeplex.com/).  
  
 **SAFE** ist der Standardberechtigungssatz und funktioniert für die meisten Szenarien. Um eine bestimmte Sicherheitsstufe anzugeben, ändern Sie die Syntax der CREATE ASSEMBLY-Anweisung wie folgt:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Sie können eine Assembly mit eingestellter **SAFE** -Berechtigung auch erstellen, indem Sie einfach die dritte Zeile des oben angegeben Codes auslassen:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Wird der Code in einer Assembly mit eingestellter **SAFE** -Berechtigung ausgeführt, können Berechnungen und Datenzugriffe im Server ausschließlich über den prozessinternen verwalteten Anbieter erfolgen.  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a>Erstellen von EXTERNAL_ACCESS- und UNSAFE-Assemblys  
 **EXTERNAL_ACCESS** wird für Szenarien verwendet, in denen der Code auf Ressourcen außerhalb des Servers zugreift, z. B. Datei-, Netzwerk-, Registrierungs- und Umgebungsvariablen. Immer wenn der Server auf eine externe Ressource zugreift, verwendet er den Sicherheitskontext des Benutzers, der den verwalteten Code aufruft.  
  
 **UNSAFE** wird für Situationen verwendet, in denen eine Assembly nicht eindeutig als sicher eingestuft werden kann oder zusätzlichen Zugriff auf beschränkte Ressourcen benötigt, z. B. die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32-API.  
  
 Zum Erstellen einer **EXTERNAL_ACCESS** - oder **UNSAFE** -Assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]muss eine der folgenden Bedingungen zutreffen:  
  
1.  Die Assembly wurde mit einem starken Namen oder Authenticode mit Zertifikat signiert. Der starke Name (oder das Zertifikat) wird in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als asymmetrischer Schlüssel (oder Zertifikat) erstellt und verfügt über eine zugehörige Anmeldung mit **EXTERNAL ACCESS ASSEMBLY** -Berechtigung (für Assemblys mit externem Zugriff) oder **UNSAFE ASSEMBLY** -Berechtigung (für unsichere Assemblys).  
  
2.  Der Datenbankbesitzer (DBO) hat die Berechtigung **EXTERNAL ACCESS ASSEMBLY** (für **EXTERNAL ACCESS** -Assemblys) oder **UNSAFE ASSEMBLY** (für **UNSAFE** -Assemblys), und für die Datenbank ist [TRUSTWORTHY Database Property](../../../relational-databases/security/trustworthy-database-property.md) auf **ON**eingestellt.  

 Die beiden oben aufgeführten Bedingungen werden auch zur Assemblyladezeit (dazu gehört auch die Ausführung) überprüft. Mindestens eine der Bedingungen muss erfüllt sein, um die Assembly zu laden.  
  
 Die Eigenschaft [TRUSTWORTHY Database Property](../../../relational-databases/security/trustworthy-database-property.md) für die Datenbank sollte nicht auf **ON** gesetzt werden, um lediglich CLR-Code im Serverprozess auszuführen. Stattdessen empfiehlt es sich, dass ein asymmetrischer Schlüssel aus der Assemblydatei in der Masterdatenbank erstellt wird. Anschließend muss eine Anmeldung für diesen asymmetrischen Schlüssel erstellt werden, und die Anmeldung muss eine **EXTERNAL ACCESS ASSEMBLY** - oder **UNSAFE ASSEMBLY** -Berechtigung erhalten.  
  
 Mit den folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen werden die Schritte ausgeführt, die erforderlich sind, um einen asymmetrischen Schlüssel zu erstellen, diesem Schlüssel eine Anmeldung zuzuweisen und die **EXTERNAL_ACCESS** -Berechtigung für die Anmeldung zu erteilen. Sie müssen vor dem Ausführen der CREATE ASSEMBLY-Anweisung die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen ausführen.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  Sie müssen eine neue Anmeldung erstellen, die dem asymmetrischen Schlüssel zugeordnet wird. Diese Anmeldung dient nur zum Erteilen von Berechtigungen. Sie muss weder einem Benutzer zugeordnet noch innerhalb der Anwendung verwendet werden.  
  
 Um eine **EXTERNAL ACCESS** -Assembly zu erstellen, muss der Ersteller die **EXTERNAL ACCESS** -Berechtigung haben. Diese wird beim Erstellen der Assembly angegeben:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Mit den folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen werden die Schritte ausgeführt, die erforderlich sind, um einen asymmetrischen Schlüssel zu erstellen, diesem Schlüssel eine Anmeldung zuzuweisen und die **UNSAFE** -Berechtigung für die Anmeldung zu erteilen. Sie müssen vor dem Ausführen der CREATE ASSEMBLY-Anweisung die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen ausführen.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Um festzulegen, dass eine Assembly mit **UNSAFE** -Berechtigung geladen wird, geben Sie die **UNSAFE** -Berechtigung beim Laden der Assembly auf den Server an:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Weitere Informationen zu den Berechtigungen für die verschiedenen Einstellungen finden Sie unter [CLR Integration Security](../../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von CLR Integration](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Ändern einer Assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [Löschen einer Assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [Code Zugriffssicherheit für die CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](../../../relational-databases/security/trustworthy-database-property.md)   
 [Zulassen von teilweise vertrauenswürdigen Aufrufern](https://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
