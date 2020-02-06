---
title: Erstellen von Synonymen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql13.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b6ccdce58ca96a26a607996943e6d48d9bac1d8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "72909739"
---
# <a name="create-synonyms"></a>Erstellen von Synonymen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie ein Synonym in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie ein Synonym mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Zum Erstellen eines Synonyms in einem Schema muss ein Benutzer über die CREATE SYNONYM-Berechtigung verfügen und entweder der Besitzer des Schemas sein oder über die ALTER SCHEMA-Berechtigung verfügen. Die CREATE SYNONYM-Berechtigung ist eine erteilbare Berechtigung.  
  
####  <a name="Permissions"></a> Berechtigungen  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-synonym"></a>So erstellen Sie ein Synonym  
  
1.  Erweitern Sie im **Objekt-Explorer**die Datenbank, in der Sie die neue Sicht erstellen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Synonyme**, und klicken Sie dann auf **Neues Synonym…** .  
  
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
  
  
