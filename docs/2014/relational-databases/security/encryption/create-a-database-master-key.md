---
title: Erstellen eines Datenbank-Hauptschlüssels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.reviewer: carlrab
ms.openlocfilehash: cc0b3e0dccd1ecf674d583e4d1b7adc1a85341d2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758886"
---
# <a name="create-a-database-master-key"></a>Erstellen eines Datenbank-Hauptschlüssels

In diesem Thema wird beschrieben, wie `master` Sie in mithilfe von einen Datenbank-Hauptschlüssel in der-Datenbank erstellen [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] .

**In diesem Thema**

- **Vorbereitungen:**

  [Security](#Security)

- [So erstellen Sie mithilfe von Transact-SQL einen Datenbank-Hauptschlüssel](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen

### <a name="security"></a><a name="Security"></a> Sicherheit

#### <a name="permissions"></a><a name="Permissions"></a> Berechtigungen

Erfordert die CONTROL-Berechtigung für die Datenbank.

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL

### <a name="to-create-a-database-master-key"></a>So erstellen Sie einen Datenbank-Hauptschlüssel

1. Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird.
2. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.
3. Erweitern Sie **Systemdatenbanken**, klicken Sie mit der rechten Maustaste auf `master`, und klicken Sie anschließend auf **Neue Abfrage**.
4. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Weitere Informationen finden Sie unter [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).
