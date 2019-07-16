---
title: Spalten aus einer Tabelle löschen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/11/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06847b9eeb2c01ae7b3e5d512a01f87adafdeb42
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67731948"
---
# <a name="delete-columns-from-a-table"></a>Spalten aus einer Tabelle löschen

[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

In diesem Thema wird beschrieben, wie Tabellenspalten in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]gelöscht werden können.

> [!CAUTION]
> Wenn Sie eine Spalte aus einer Tabelle löschen, wird die Spalte mit allen darin enthaltenen Daten gelöscht.

 **In diesem Thema**

- **Vorbereitungen:**

   [Einschränkungen](#Restrictions)

   [Security](#Security)

- **So entfernen Sie eine Spalte aus der Tabelle mithilfe von:**

   [SQL Server Management Studio](#SSMSProcedure)

   [Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Vorbereitungen

### <a name="Restrictions"></a> Einschränkungen

Sie können keine Spalte löschen, die eine CHECK-Einschränkung hat. Sie müssen zuerst die Einschränkung löschen.

Eine Spalte, für die PRIMARY KEY- oder FOREIGN KEY-Einschränkungen oder andere Abhängigkeiten bestehen, können Sie nur mit dem Tabellen-Designer löschen. Wenn Sie den Objekt-Explorer oder [!INCLUDE[tsql](../../includes/tsql-md.md)]verwenden, müssen Sie zuerst alle Abhängigkeiten von der Spalte entfernen.

### <a name="Security"></a> Sicherheit

#### <a name="Permissions"></a> Berechtigungen

Erfordert die ALTER-Berechtigung für die Tabelle.

## <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio

### <a name="to-delete-columns-by-using-object-explorer"></a>So löschen Sie Spalten mit dem Objekt-Explorer

1. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.
2. Suchen Sie im **Objekt-Explorer** die Tabelle, aus der Sie Spalten löschen möchten, und erweitern Sie diese, um die Spaltennamen anzuzeigen.
3. Klicken Sie mit der rechten Maustaste auf die Spalte, die Sie löschen möchten, und wählen Sie anschließend **Löschen** aus.
4. Klicken Sie im Dialogfeld **Objekt löschen** auf **OK**.

Wenn die Spalte Einschränkungen oder andere Abhängigkeiten enthält, wird eine Fehlermeldung im Dialogfeld **Objekt löschen** angezeigt. Beheben Sie den Fehler, indem Sie die Einschränkungen löschen, auf die verwiesen wird.

### <a name="to-delete-columns-by-using-table-designer"></a>So löschen Sie Spalten mit dem Tabellen-Designer

1. Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, aus der Sie Spalten löschen möchten, und wählen Sie **Entwurf**aus.
2. Klicken Sie mit der rechten Maustaste auf die zu löschende Spalte, und wählen Sie im Kontextmenü die Option **Spalte löschen** aus.
3. Wenn die betreffende Spalte in eine Beziehung eingebunden ist (FOREIGN KEY oder PRIMARY KEY), werden Sie in einer Meldung aufgefordert, das Löschen der ausgewählten Spalten und der zugehörigen Beziehungen zu bestätigen. Klicken Sie auf **Ja**.

## <a name="TsqlProcedure"></a> Verwenden von Transact-SQL

### <a name="to-delete-columns"></a>So löschen Sie Spalten

Im folgenden Beispiel wird veranschaulicht, wie eine Spalte gelöscht wird.

```sql
ALTER TABLE dbo.doc_exb DROP COLUMN column_b;
```

Wenn die Spalte Einschränkungen oder andere Abhängigkeiten enthält, wird eine Fehlermeldung zurückgegeben. Beheben Sie den Fehler, indem Sie die Einschränkungen löschen, auf die verwiesen wird.

Weitere Beispiele finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).

## <a name="FollowUp"></a>
