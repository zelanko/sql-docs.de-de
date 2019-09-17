---
title: Erstellen eines Datenbank-Hauptschlüssels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.reviewer: carlrab
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 757b6c62d63da2b8f1fa33e5d704d7a2c4fabd38
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978368"
---
# <a name="create-a-database-master-key"></a>Erstellen eines Datenbank-Hauptschlüssels

In diesem Thema wird beschrieben, wie Sie in `master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe [!INCLUDE[tsql](../../../includes/tsql-md.md)]von einen Datenbank-Hauptschlüssel in der-Datenbank erstellen.

**In diesem Thema**

- **Vorbereitungen:**

  [Sicherheit](#Security)

- [So erstellen Sie mithilfe von Transact-SQL einen Datenbank-Hauptschlüssel](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Vorbereitungen

### <a name="Security"></a> Sicherheit

#### <a name="Permissions"></a> Berechtigungen

Erfordert die CONTROL-Berechtigung für die Datenbank.

## <a name="TsqlProcedure"></a> Verwenden von Transact-SQL

### <a name="to-create-a-database-master-key"></a>So erstellen Sie einen Datenbank-Hauptschlüssel

1. Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird.
2. Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.
3. Erweitern Sie **System Datenbanken**, klicken Sie `master` mit der rechten Maustaste und klicken Sie dann auf **neue Abfrage**.
4. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Weitere Informationen finden Sie unter [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).
