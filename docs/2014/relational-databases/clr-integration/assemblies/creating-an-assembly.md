---
title: Erstellen einer Assembly | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: e28871e93bd718063692a31a4a3462399517dfc9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129000"
---
# <a name="creating-an-assembly"></a>Erstellen von Assemblys
  Verwaltete Datenbankobjekte wie beispielsweise gespeicherte Prozeduren und Trigger werden kompiliert und dann in so genannten Assemblys bereitgestellt. Verwaltete DLL-Assemblys müssen registriert werden, [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] damit die von die Assembly bereitgestellte Funktion verwendet werden kann. Zum Registrieren einer Assembly in eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank, verwenden Sie die CREATE ASSEMBLY-Anweisung. In diesem Thema wird erläutert, wie Sie eine Assembly mithilfe der CREATE ASSEMBLY-Anweisung in einer Datenbank registrieren und wie Sie die Sicherheitseinstellungen für die Assembly festlegen.  
  
## <a name="the-create-assembly-statement"></a>Die CREATE ASSEMBLY-Anweisung  
 Die CREATE ASSEMBLY-Anweisung dient zum Erstellen einer Assembly in einer Datenbank. Beispiel:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Die FROM-Klausel legt den Pfadnamen der zu erstellenden Assembly fest. Bei diesem Pfad kann es sich entweder um einen UNC-Pfad (Universal Naming Convention) oder einen physischen Dateipfad handeln, der sich lokal auf dem Rechner befindet.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist es nicht zulässig, verschiedene Versionen einer Assembly mit demselben Namen, derselben Kultur und demselben öffentlichen Schlüssel zu registrieren.  
  
 Es ist möglich, Assemblys zu erstellen, die auf andere Assemblys verweisen. Wenn eine Assembly erstellt wird, im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erstellt außerdem die Assemblys, auf die verwiesen wird durch die Assembly auf Stammebene aus, wenn die referenzierten Assemblys nicht bereits in der Datenbank erstellt werden.  
  
 Datenbankbenutzer oder Benutzerrollen erhalten Berechtigungen zum Erstellen von Assemblys in einer Datenbank, deren Besitzer sie dann sind. Um Assemblys zu erstellen, benötigt der Datenbankbenutzer oder die Rolle die CREATE ASSEMBLY-Berechtigung.  
  
 Eine Assembly kann nur unter folgenden Voraussetzungen erfolgreich auf andere Assemblys verweisen:  
  
-   Die Assembly, die aufgerufen wird oder auf die verwiesen wird, gehört dem gleichen Benutzer oder der Rolle.  
  
-   Die Assembly, die aufgerufen wird oder auf die verwiesen wird, wurde in derselben Datenbank erstellt.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Festlegen der Sicherheit beim Erstellen von Assemblys  
 Wenn Sie eine Assembly in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank erstellen, können Sie eine von drei verschiedenen Sicherheitsstufen festlegen, mit der der Code ausgeführt werden soll: `SAFE`, `EXTERNAL_ACCESS` oder `UNSAFE`. Beim Ausführen der `CREATE ASSEMBLY`-Anweisung werden bestimmte Überprüfungen für die Code-Assembly durchgeführt, aufgrund derer die Assembly möglicherweise nicht beim Server registriert werden kann. Weitere Informationen finden Sie unter dem Beispiel für den Identitätswechsel auf [CodePlex](http://msftengprodsamples.codeplex.com/).  
  
 `SAFE` ist der Standardberechtigungssatz und funktioniert für die meisten Szenarien. Um eine bestimmte Sicherheitsstufe anzugeben, ändern Sie die Syntax der CREATE ASSEMBLY-Anweisung wie folgt:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Sie können eine Assembly mit eingestellter `SAFE`-Berechtigung auch erstellen, indem Sie einfach die dritte Zeile des oben angegeben Codes auslassen:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Wenn Code in einer Assembly ausgeführt wird, unter dem `SAFE` Berechtigung, kann nur erfolgen Berechnungen und Datenzugriffe im Server über den prozessinternen verwalteten Anbieter.  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>Erstellen von EXTERNAL_ACCESS- und UNSAFE-Assemblys  
 `EXTERNAL_ACCESS` Adressen Szenarien in der der Code den Zugriff auf Ressourcen außerhalb des Servers, z. B. Dateien, Netzwerk, Registrierung und Umgebungsvariablen. Immer wenn der Server auf eine externe Ressource zugreift, verwendet er den Sicherheitskontext des Benutzers, der den verwalteten Code aufruft.  
  
 `UNSAFE` wird für Situationen, in denen eine Assembly ist nicht sicher eingestuft werden kann, oder erfordert zusätzlichen Zugriff auf, Ressourcen, z. B. beschränkt die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32-API.  
  
 Zum Erstellen einer `EXTERNAL_ACCESS` oder `UNSAFE` Assembly im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], eine der folgenden Bedingungen muss erfüllt sein:  
  
1.  Die Assembly wurde mit einem starken Namen oder Authenticode mit Zertifikat signiert. Diese starken Namen (oder Zertifikat) wird in erstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als ein asymmetrischer Schlüssel (oder Zertifikat), und verfügt über einen entsprechenden Anmeldenamen mit `EXTERNAL ACCESS ASSEMBLY` -Berechtigung (für Assemblys mit externem Zugriff) oder `UNSAFE ASSEMBLY` -Berechtigung (für unsichere Assemblys).  
  
2.  Der Datenbankbesitzer (DBO) hat `EXTERNAL ACCESS ASSEMBLY` (für `EXTERNAL ACCESS` Assemblys) oder `UNSAFE ASSEMBLY` (für `UNSAFE` Assemblys) Berechtigung und die Datenbank hat die [TRUSTWORTHY-Datenbankeigenschaft](../../security/trustworthy-database-property.md) festgelegt `ON`.  
  
 Die beiden oben aufgeführten Bedingungen werden auch zur Assemblyladezeit (dazu gehört auch die Ausführung) überprüft. Mindestens eine der Bedingungen muss erfüllt sein, um die Assembly zu laden.  
  
 Es wird empfohlen, die [TRUSTWORTHY-Datenbankeigenschaft](../../security/trustworthy-database-property.md) für eine Datenbank nicht festgelegt werden `ON` nur zum Ausführen der common Language Runtime (CLR)-code im Serverprozess. Stattdessen empfiehlt es sich, dass ein asymmetrischer Schlüssel aus der Assemblydatei in der Masterdatenbank erstellt wird. Anschließend muss eine Anmeldung für diesen asymmetrischen Schlüssel erstellt werden, und die Anmeldung gewährt werden muss `EXTERNAL ACCESS ASSEMBLY` oder `UNSAFE ASSEMBLY` Berechtigung.  
  
 Die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisungen vor dem Ausführen von CREATE ASSEMBLY-Anweisung.  
  
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
  
 Zum Erstellen einer `EXTERNAL ACCESS` Assembly muss der Ersteller verfügen `EXTERNAL ACCESS` Berechtigung. Diese wird beim Erstellen der Assembly angegeben:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisungen vor dem Ausführen von CREATE ASSEMBLY-Anweisung.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Um festzulegen, dass eine Assembly mit `UNSAFE`-Berechtigung geladen wird, geben Sie die `UNSAFE`-Berechtigung beim Laden der Assembly auf den Server an:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Weitere Informationen zu den Berechtigungen für jede der Einstellungen finden Sie unter [CLR-Integrationssicherheit](../security/clr-integration-security.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von CLR-Integrationsassemblys](managing-clr-integration-assemblies.md)   
 [Ändern einer Assembly](altering-an-assembly.md)   
 [Löschen von Assemblys](dropping-an-assembly.md)   
 [Codezugriffssicherheit für CLR-Integration](../security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](../../security/trustworthy-database-property.md)   
 [Zulassen von teilweise vertrauenswürdigen Aufrufern](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
  
