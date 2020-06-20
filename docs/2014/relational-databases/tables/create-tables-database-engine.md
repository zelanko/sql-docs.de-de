---
title: Erstellen von Tabellen (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d84a4da6a10fbcbae311fe1bf738c03b85a4c6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056824"
---
# <a name="create-tables-database-engine"></a>Erstellen von Tabellen (Datenbank-Engine)
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine neue Tabelle erstellen, diese benennen und einer vorhandenen Datenbank in [!INCLUDE[tsql](../../includes/tsql-md.md)]hinzufügen.

> [!NOTE]
>  Wenn Sie mit einer SQL Azure-Datenbank verbunden sind, startet die neue Tabellenoption ein Vorlagenskript zum Erstellen einer Tabelle. Bearbeiten Sie die Parameter, und führen Sie dann das Skript aus, um eine neue Tabelle zu erstellen. Weitere Informationen finden Sie unter [SQL Azure-Übersicht](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx)(möglicherweise auf Englisch).

 **In diesem Thema**

-   **Vorbereitungen:**

     [Security](#Security)

-   **So erstellen Sie eine Tabelle mit:**

     [SQL Server Management Studio](#SSMSProcedure)

     [Transact-SQL](#TsqlProcedure)

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen

###  <a name="security"></a><a name="Security"></a> Sicherheit

####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen
 Es sind die CREATE TABLE-Berechtigung in der Datenbank und die ALTER-Berechtigung für das Schema erforderlich, in der die Tabelle erstellt wird.

 Wenn in der CREATE TABLE-Anweisung Spalten als CLR-benutzerdefinierter Typ definiert sind, ist entweder der Besitz des Typs oder die REFERENCES-Berechtigung für den Typ erforderlich.

 Wenn einer Spalte in der CREATE TABLE-Anweisung eine XML-Schemaauflistung zugeordnet ist, ist entweder der Besitz der XML-Schemaauflistung oder die REFERENCES-Berechtigung für die Auflistung erforderlich.

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio

#### <a name="to-create-a-table-with-table-designer"></a>So erstellen Sie eine Tabelle mit dem Tabellen-Designer

1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz her, in der die zu ändernde Datenbank enthalten ist.

2.  Erweitern Sie im **Objekt-Explorer**zuerst den Knoten **Datenbanken** und dann die Datenbank, in der die neue Tabelle angelegt werden soll.

3.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Knoten **Tabellen** der Datenbank, und klicken Sie auf **Neue Tabelle**.

4.  Geben Sie für die einzelnen Spalten Spaltennamen ein, wählen Sie Datentypen aus, und legen Sie fest, ob NULL-Werte zulässig sein sollen, wie in der folgenden Abbildung veranschaulicht.

     ![Spalten im Tabellen-Designer hinzufügen](../../database-engine/media/addcolumnsintabledesigner.gif "Spalten im Tabellen-Designer hinzufügen")

5.  Um weitere Eigenschaften für eine Spalte anzugeben, z. B. die Identität oder Werte für berechnete Spalten, klicken Sie auf die Spalte und wählen auf der Registerkarte mit den Spalteneigenschaften die geeigneten Eigenschaften aus. Weitere Informationen zu Spalteneigenschaften finden Sie unter [Tabellenspalteneigenschaften &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md).

6.  Um eine Spalte als Primärschlüssel festzulegen, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Primärschlüssel festlegen**aus. Weitere Informationen finden Sie unter [Create Primary Keys](../tables/create-primary-keys.md).

7.  Um Fremdschlüsselbeziehungen, CHECK-Einschränkungen oder Indizes zu erstellen, klicken Sie mit der rechten Maustaste in den Bereich des Tabellen-Designers und wählen ein Objekt aus der Liste aus, wie in der folgenden Abbildung veranschaulicht.

     ![Tabellenobjekte hinzufügen](../../database-engine/media/addtableobjects.gif "Tabellenobjekte hinzufügen")

     Weitere Informationen zu diesen Objekten finden Sie unter [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) und [Indexes](../indexes/indexes.md).

8.  Die Tabelle ist standardmäßig im **dbo** -Schema enthalten. Um ein anderes Schema für die Tabelle anzugeben, klicken Sie mit der rechten Maustaste in den Bereich des Tabellen-Designers, und wählen Sie **Eigenschaften** aus, wie in der folgenden Abbildung veranschaulicht. Wählen Sie in der Dropdownliste **Schema** das geeignete Schema aus.

     ![Tabellenschema angeben](../../database-engine/media/specifyatableschema.gif "Tabellenschema angeben")

     Weitere Informationen zu Schemas finden Sie unter [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).

9. Wählen Sie im Menü **Datei** den Befehl *Tabellennamen* **Speichern** aus.

10. Geben Sie im Dialogfeld **Namen auswählen** einen Namen für die Tabelle ein, und klicken Sie auf **OK**.

11. Zum Anzeigen der neuen Tabelle erweitern Sie im **Objekt-Explorer**den Knoten **Tabellen** und drücken **F5** , um die Objektliste zu aktualisieren. Die neue Tabelle wird in der Tabellenliste angezeigt.

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL

#### <a name="to-create-a-table-in-the-query-editor"></a>So erstellen Sie eine Tabelle im Abfrage-Editor

1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.

2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.

3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.

    ```
    CREATE TABLE dbo.PurchaseOrderDetail
    (
        PurchaseOrderID int NOT NULL
        ,LineNumber smallint NOT NULL
        ,ProductID int NULL
        ,UnitPrice money NULL
        ,OrderQty smallint NULL
        ,ReceivedQty float NULL
        ,RejectedQty float NULL
        ,DueDate datetime NULL
    );
    ```

 Weitere Beispiele finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).


