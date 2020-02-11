---
title: Erteilen von Berechtigungen für eine gespeicherte Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47b8e4b87ab3150ae7bf67d3c3a2f9c5e0732294
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63015582"
---
# <a name="grant-permissions-on-a-stored-procedure"></a>Erteilen von Berechtigungen für eine gespeicherte Prozedur
  In diesem Thema wird beschrieben, wie Sie Berechtigungen für eine gespeicherte Prozedur in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erteilen. Berechtigungen können einem vorhandenen Benutzer, einer Datenbankrolle oder einer Anwendungsrolle in der Datenbank erteilt werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **Erteilen von Berechtigungen für eine gespeicherte Prozedur mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] kann nicht verwendet werden, um Berechtigungen für Systemprozeduren oder Systemfunktionen zu erteilen. Verwenden Sie stattdessen [GRANT-Objektberechtigungen](/sql/t-sql/statements/grant-object-permissions-transact-sql) .  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der Berechtigende (oder der mit der AS-Option angegebene Prinzipal) benötigt entweder die Berechtigung selbst mit GRANT OPTION oder eine höhere Berechtigung, die die erteilte Berechtigung impliziert. Erfordert die ALTER-Berechtigung im Schema, zu der die Prozedur gehört, oder die CONTROL-Berechtigung für die Prozedur. Weitere Informationen finden Sie unter [GRANT (Objektberechtigungen) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)erteilen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>So erteilen Sie Berechtigungen für eine gespeicherte Prozedur  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, zu der die Prozedur gehört, und erweitern Sie dann **Programmierbarkeit**.  
  
3.  Erweitern Sie **Gespeicherte Prozeduren**, klicken Sie mit der rechten Maustaste auf die Prozedur, für die Sie Berechtigungen erteilen möchten, und klicken Sie anschließend auf **Eigenschaften**.  
  
4.  Wählen Sie in **Eigenschaften der gespeicherten Prozedur**die Seite **Berechtigungen** aus.  
  
5.  Klicken Sie auf **Suchen**, um einem Benutzer, einer Datenbankrolle oder einer Anwendungsrolle Berechtigungen zu erteilen.  
  
6.  Klicken Sie in **Benutzer oder Rollen auswählen**auf **Objekttypen** , um die gewünschten Benutzer und Rollen hinzuzufügen bzw. zu löschen.  
  
7.  Klicken Sie auf **Durchsuchen** , um die Liste der Benutzer oder Rollen anzuzeigen. Wählen Sie die Benutzer bzw. Rollen aus, denen Berechtigungen gewährt werden sollen.  
  
8.  Wählen Sie im Raster **Explizite Berechtigungen** die Berechtigungen aus, die Sie dem angegebenen Benutzer bzw. der angegebenen Rolle erteilen möchten. Eine Beschreibung der Berechtigungen finden Sie unter [Berechtigungen &#40;Datenbank-Engine&#41;](../security/permissions-database-engine.md).  
  
 Durch Auswahl von **Erteilen** wird angegeben, dass der Empfänger die angegebene Berechtigung erhält. Durch Auswahl von **Mit Erteilung** wird angegeben, dass der Empfänger außerdem die angegebene Berechtigung anderen Prinzipalen erteilen kann.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>So erteilen Sie Berechtigungen für eine gespeicherte Prozedur  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im folgenden Beispiel wird die `EXECUTE` -Berechtigung für die gespeicherte Prozedur `HumanResources.uspUpdateEmployeeHireInfo` einer Anwendungsrolle mit dem Namen `Recruiting11`erteilt.  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [GRANT (Objektberechtigungen) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)   
 [Erstellen einer gespeicherten Prozedur](../stored-procedures/create-a-stored-procedure.md)   
 [Ändern einer gespeicherten Prozedur](modify-a-stored-procedure.md)   
 [Löschen einer gespeicherten Prozedur](../stored-procedures/delete-a-stored-procedure.md)   
 [Umbenennen einer gespeicherten Prozedur](rename-a-stored-procedure.md)  
  
  
