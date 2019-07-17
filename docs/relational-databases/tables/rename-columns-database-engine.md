---
title: Umbenennen von Spalten (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 36b7c385f3722a1db86899c749ee8310e7596e1e
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727780"
---
# <a name="rename-columns-database-engine"></a>Umbenennen von Spalten (Datenbank-Engine)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Tabellenspalte in [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.

**In diesem Thema**

- **Vorbereitungen:**

   [Einschränkungen](#Restrictions)

   [Security](#Security)

- **So benennen Sie Spalten um mit**

   [SQL Server Management Studio](#SSMSProcedure)

   [Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Vorbereitungen

### <a name="Restrictions"></a> Einschränkungen

Durch die Umbenennung einer Spalte werden nicht automatisch auch die Verweise auf diese Spalte umbenannt. Sie müssen Objekte, die auf die umbenannte Spalte verweisen, manuell ändern. Wenn Sie z. B. eine Tabellenspalte umbenennen und in einem Trigger auf diese Spalte verwiesen wird, müssen Sie den Trigger ändern, sodass er den neuen Spaltennamen wiedergibt. Verwenden Sie [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) , um Abhängigkeiten vom Objekt aufzulisten, bevor Sie es umbenennen.

### <a name="Security"></a> Sicherheit

#### <a name="Permissions"></a> Berechtigungen

Erfordert die ALTER-Berechtigung für das Objekt.

## <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio

### <a name="to-rename-a-column-using-object-explorer"></a>So benennen Sie eine Spalte mit Objekt-Explorer um

1. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.
2. Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, in der Sie Spalten umbenennen möchten, und klicken Sie dann auf **Umbenennen**.
3. Geben Sie einen neuen Spaltennamen ein.

### <a name="to-rename-a-column-using-table-designer"></a>So benennen Sie eine Spalte mit dem Tabellen-Designer um

1. Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, in der Sie Spalten umbenennen möchten, und klicken Sie dann auf **Entwerfen**.
2. Wählen Sie unter **Spaltenname**den zu ändernden Namen aus, und geben Sie einen neuen Namen ein.
3. Klicken Sie im Menü **Datei** auf **Speichern** > _Tabellenname_.

> [!NOTE]
> Sie können den Spaltennamen auch auf der Registerkarte **Spalteneigenschaften** ändern. Wählen Sie die Spalte aus, deren Name geändert werden soll, und geben Sie für **Name**einen neuen Wert ein.

## <a name="TsqlProcedure"></a> Verwenden von Transact-SQL

**So benennen Sie eine Spalte um**

### <a name="to-rename-a-column"></a>So benennen Sie eine Spalte um

Im folgenden Beispiel wird die Spalte `TerritoryID` in der Tabelle `Sales.SalesTerritory` in der AdventureWorks-Datenbank in `TerrID` umbenannt.

```sql
EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';
```

Weitere Informationen finden Sie unter [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).
