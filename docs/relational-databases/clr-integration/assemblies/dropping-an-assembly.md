---
title: Löschen einer Assembly | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: f28f51f73faca8a72bdea3b8af70e14046d73f8d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074339"
---
# <a name="dropping-an-assembly"></a>Löschen von Assemblys
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Assemblys, die mithilfe der CREATE ASSEMBLY-Anweisung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] registriert wurden, können gelöscht oder verworfen werden, wenn die von ihnen bereitgestellte Funktionalität nicht mehr benötigt wird. Durch das Löschen einer Assembly werden die Assembly sowie alle zugehörigen Dateien, wie Debugdateien, aus der Datenbank entfernt. Zum Löschen einer Assembly verwenden Sie die DROP ASSEMBLY-Anweisung mit der folgenden Syntax:  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 Die DROP ASSEMBLY-Anweisung stört nicht die aktuelle Ausführung von Code, der auf die Assembly verweist, aber nach der Ausführung der DROP ASSEMBLY-Anweisung schlagen alle Versuche fehl, den Assemblycode aufzurufen.  
  
 DROP ASSEMBLY gibt einen Fehler zurück, wenn eine andere Assembly in der Datenbank auf die Assembly verweist oder diese von CLR-basierten Funktionen (Common Language Runtime), -Prozeduren, -Triggern, benutzerdefinierten Typen (User Defined Types, UDTs) oder Aggregaten in der aktuellen Datenbank verwendet wird. Löschen Sie zuerst die in der Assembly enthaltenen verwalteten Datenbankobjekte mit entsprechenden DROP AGGREGATE-, DROP FUNCTION-, DROP PROCEDURE-, DROP TRIGGER- und DROP TYPE-Anweisungen.  
  
## <a name="removing-a-udt-from-the-database"></a>Entfernen eines UDTs aus der Datenbank  
 Mit der DROP TYPE-Anweisung wird ein UDT aus der aktuellen Datenbank entfernt. Sobald der UDT entfernt wurde, können Sie die Assembly mit der DROP ASSEMBLY-Anweisung aus der Datenbank löschen.  
  
 Die DROP TYPE-Anweisung schlägt fehl, wenn Objekte vom UDT abhängen, wie in den folgenden Situationen:  
  
-   Tabellen in der Datenbank, die mit dem UDT definierte Spalten enthalten.  
  
-   Funktionen, gespeicherte Prozeduren oder Trigger, die Variablen und Parameter des UDT verwenden und in der Datenbank mit der WITH SCHEMABINDING-Klausel erzeugt wurden.  
  
### <a name="finding-udt-dependencies"></a>Ermitteln von UDT-Abhängigkeiten  
 Sie müssen zuerst alle abhängigen Objekte löschen und dann die DROP TYPE-Anweisung ausführen. Die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)] Abfrage verwendet alle Spalten und Parameter, die einen UDT in der **AdventureWorks** -Datenbank verwenden.  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von CLR Integration](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Ändern einer Assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [Erstellen einer Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Drop Aggregate &#40;Transact-SQL-&#41;](../../../t-sql/statements/drop-aggregate-transact-sql.md)   
 [Drop Function &#40;Transact-SQL-&#41;](../../../t-sql/statements/drop-function-transact-sql.md)   
 [DROP PROCEDURE &#40;Transact-SQL-&#41;](../../../t-sql/statements/drop-procedure-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Drop Type &#40;Transact-SQL-&#41;](../../../t-sql/statements/drop-type-transact-sql.md)  
  
  
