---
title: Ändern einer Assembly | Microsoft-Dokumentation
description: Verwenden Sie Alter Assembly, um in SQL Server registrierte Assemblys zu aktualisieren. Sie können auch den Berechtigungs Satz ändern und Quellcode oder andere Dateien für eine Assembly hinzufügen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: d9ec69415e270770360b6901d8c3117790b5e16d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717945"
---
# <a name="altering-an-assembly"></a>Ändern einer Assembly
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] registrierte Assemblys können von einer aktuelleren Version aus mithilfe der ALTER ASSEMBLY-Anweisung aktualisiert werden. Zum Aktualisieren einer Assembly verwenden Sie die ALTER ASSEMBLY-Anweisung mit der folgenden Syntax:  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 Mit ALTER ASSEMBLY werden zurzeit ausgeführte Prozesse, die die Assembly verwenden, nicht unterbrochen. Die Prozesse werden mit der unveränderten Assembly weiterhin ausgeführt. Mit ALTER ASSEMBLY können die Signaturen gängiger CLR-Funktionen (Common Language Runtime), Aggregatfunktionen, gespeicherter Prozeduren und Trigger nicht geändert werden. Neue öffentliche Methoden können der Assembly hinzugefügt werden. Private Methoden können beliebig bearbeitet werden, während öffentliche Methoden nur so lange bearbeitet werden können, wie die Signaturen oder Attribute unverändert bleiben. Felder, die in einem systemeigenen serialisierten benutzerdefinierten Typ enthalten sind, einschließlich Datenelemente oder Basisklassen, können nicht mithilfe von ALTER ASSEMBLY geändert werden. Alle anderen Änderungen werden nicht unterstützt. Weitere Informationen finden Sie unter [Alter Assembly &#40;Transact-SQL-&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Ändern des Berechtigungssatzes einer Assembly  
 Der Berechtigungssatz einer Assembly kann auch mit der ALTER ASSEMBLY-Anweisung geändert werden. Mit der folgenden Anweisung wird der Berechtigungs Satz der SQLCLRTest-Assembly in " **EXTERNAL_ACCESS**" geändert.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Wenn der Berechtigungs Satz einer Assembly von **sicher** in **EXTERNAL_ACCESS** oder **unsicher**geändert wird, müssen zunächst ein asymmetrischer Schlüssel und eine zugehörige Anmeldung mit **externer zugriffsassemblyberechtigung** oder eine **unsichere** Assemblyberechtigung für die Assembly erstellt werden. Weitere Informationen finden Sie unter [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Hinzufügen des Quellcodes einer Assembly  
 Die ADD FILE-Klausel in der ALTER ASSEMBLY-Syntax ist nicht in CREATE ASSEMBLY vorhanden. Sie können sie verwenden, um Quellcode oder beliebige andere Dateien hinzuzufügen, die einer Assembly zugeordnet sind. Die Dateien werden von ihren ursprünglichen Speicherorten kopiert und in Systemtabellen in der Datenbank gespeichert. Dadurch wird sichergestellt, dass stets der Quellcode oder andere Dateien verfügbar sind, wenn Sie die aktuelle Version des UDT neu erstellen oder dokumentieren müssen.  
  
 Die folgende Anweisung fügt der Point.cs-Klasse Quellcode für den Point-UDT hinzu. Dadurch wird der in der Datei Point.cs enthaltene Text kopiert und unter dem Namen "PointSource" in der Datenbank gespeichert.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von CLR Integration](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Erstellen einer Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Löschen einer Assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
