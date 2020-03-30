---
title: Angeben von Standardwerten für Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2020
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1544242905645fed5cb00fda3f7da0a06809326c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "79448483"
---
# <a name="specify-default-values-for-columns"></a>Angeben von Standardwerten für Spalten

[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Sie können mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einen Standardwert angeben, der in die Tabellenspalte eingegeben wird. Sie können einen Standardwert festlegen, indem Sie entweder den Objekt-Explorer auf der Benutzeroberfläche verwenden oder [!INCLUDE[tsql](../../includes/tsql-md.md)] übermitteln.

Wenn Sie der Spalte keinen Standardwert zuweisen und der Benutzer die Spalte leer lässt, passiert Folgendes:

- Wenn NULL-Werte zugelassen sind, wird NULL in die Spalte eingefügt.

- Wenn NULL-Werte nicht zugelassen sind, bleibt die Spalte leer. Die Zeile kann jedoch erst dann gespeichert werden, wenn ein Wert in die Spalte eingegeben wird.

## <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen

Bevor Sie beginnen sollten Sie die folgenden Einschränkungen kennen:

- Wenn die Eingabe im Feld **Standardwert** einen gebundenen Standardwert ersetzt (der ohne Klammern angezeigt wird), werden Sie aufgefordert, die Bindung des Standardwerts aufzuheben und ihn durch den neuen Standardwert zu ersetzen.

- Werte für Zeichenfolgen müssen in einfache Anführungszeichen (') gesetzt werden. Verwenden Sie keine doppelten Anführungszeichen ("), da diese für in Anführungszeichen gesetzte Bezeichner reserviert sind.

- Um einen numerischen Standardwert einzugeben, geben Sie die Zahl ohne Anführungszeichen ein.

- Wenn Sie ein Objekt bzw. eine Funktion eingeben, geben Sie den Namen des Objekts bzw. der Funktion ein, ohne ihn in Anführungszeichen einzuschließen.

### <a name="security-permissions"></a><a name="Security"></a> Sicherheitsberechtigungen

In diesem Artikel beschriebenen Aktionen erfordern die ALTER-Berechtigung für die Tabelle.

## <a name="use-ssms-to-specify-a-default"></a><a name="SSMSProcedure"></a> Angeben eines Standardwerts mit SSMS

Sie können im Objekt-Explorer einen Standardwert für eine Tabellenspalte angeben.

### <a name="object-explorer"></a>Objekt-Explorer

1. Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle mit den Spalten, für die Sie Dezimalstellen ändern möchten, und klicken Sie auf **Entwerfen**.

2. Wählen Sie die Spalte aus, für die Sie einen Standardwert angeben möchten.

3. Geben Sie den neuen Standardwert auf der Registerkarte **Spalteneigenschaften** in der Eigenschaft **Standardwert oder -bindung** ein.

   > [!NOTE]
   > Um einen numerischen Standardwert einzugeben, geben Sie die Zahl ein. Geben Sie bei einem Objekt oder einer Funktion den entsprechenden Namen ein. Geben Sie für einen alphanumerischen Standardwert den Wert in einfachen Anführungszeichen ein.

4. Klicken Sie im Menü **Datei** auf **Tabellenname** _speichern_.

## <a name="use-transact-sql-to-specify-a-default"></a><a name="TsqlProcedure"></a> Angeben eines Standardwerts mit Transact-SQL

Es gibt verschiedene Möglichkeiten, wie Sie mit SSMS und T-SQL-Übermittlung einen Standardwert für eine Spalte angeben können.

### <a name="alter-table-t-sql"></a>ALTER TABLE (T-SQL)

1. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.

2. Klicken Sie in der Standardleiste auf **Neue Abfrage**.

3. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.

   ```sql
   CREATE TABLE dbo.doc_exz (column_a INT, column_b INT); -- Allows nulls.
   GO
   INSERT INTO dbo.doc_exz (column_a) VALUES (7);
   GO
   ALTER TABLE dbo.doc_exz
     ADD CONSTRAINT DF_Doc_Exz_Column_B
     DEFAULT 50 FOR column_b;
   GO
   ```

<!--
The following two T-SQL code examples were offered by 'nycdotnet' (Steve) via public PR 1660, Feb 2019.
-->

### <a name="create-table-t-sql"></a>CREATE TABLE (T-SQL)

```sql
    CREATE TABLE dbo.doc_exz (
      column_a INT,
      column_b INT DEFAULT 50);
```

### <a name="named-constraint-t-sql"></a>Named CONSTRAINT (T-SQL)

```sql
    CREATE TABLE dbo.doc_exz (
      column_a INT,
      column_b INT CONSTRAINT DF_Doc_Exz_Column_B DEFAULT 50);
```

Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).
