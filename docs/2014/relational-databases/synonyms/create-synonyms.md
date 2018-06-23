---
title: Erstellen von Synonymen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-synonyms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
caps.latest.revision: 6
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0a0d669a2fdbf1bab9d5b887e7e06d9793bbda9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046628"
---
# <a name="create-synonyms"></a>Erstellen von Synonymen
  In diesem Thema wird beschrieben, wie ein Synonym in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So erstellen Sie ein Synonym mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
 Zum Erstellen eines Synonyms in einem Schema muss ein Benutzer über die CREATE SYNONYM-Berechtigung verfügen und entweder der Besitzer des Schemas sein oder über die ALTER SCHEMA-Berechtigung verfügen. Die CREATE SYNONYM-Berechtigung ist eine erteilbare Berechtigung.  
  
####  <a name="Permissions"></a> Berechtigungen  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-synonym"></a>So erstellen Sie ein Synonym  
  
1.  Erweitern Sie im **Objekt-Explorer**die Datenbank, in der Sie die neue Sicht erstellen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Synonyme** , und klicken Sie dann auf **Neues Synonym…**.  
  
3.  Geben Sie im Dialogfeld **Synonym hinzufügen** die folgenden Informationen ein.  
  
     **Synonymname**  
     Geben Sie den neuen Namen ein, den Sie für dieses Objekt verwenden werden.  
  
     **Synonymschema**  
     Geben Sie das Schema des neuen Namens ein, das Sie für dieses Objekt verwenden werden.  
  
     **Servername**  
     Geben Sie die Serverinstanz ein, zu der eine Verbindung hergestellt werden soll.  
  
     **Datenbankname**  
     Geben Sie die Datenbank ein, die das Objekt enthält, bzw. wählen Sie sie aus.  
  
     **Schema**  
     Geben Sie das Schema ein, das das Objekt besitzt, bzw. wählen Sie es aus.  
  
     **Objekttyp**  
     Wählen Sie den Objekttyp aus.  
  
     **Objektname**  
     Geben Sie den Namen des Objekts ein, auf das das Synonym verweist.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-synonym"></a>So erstellen Sie ein Synonym  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie die folgenden Beispiele, fügen Sie sie in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird ein Synonym für eine vorhandene Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank erstellt. Das Synonym wird dann in nachfolgenden Beispielen verwendet.  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 Das folgende Beispiel fügt eine Zeile in die Basistabelle ein, auf die vom `MyAddressType` -Synonym verwiesen wird.  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 Das folgende Beispiel veranschaulicht, wie in dynamischem SQL auf ein Synonym verwiesen werden kann.  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  