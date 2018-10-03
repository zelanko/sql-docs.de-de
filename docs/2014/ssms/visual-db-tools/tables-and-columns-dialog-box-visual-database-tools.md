---
title: Tabellen und Spalten (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a89dbc440cd47dc7ed951181c49d20d52097faa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165300"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>Tabellen und Spalten (Dialogfeld) (Visual Database Tools)
  In diesem Dialogfeld können Sie einen Primärschlüssel in einer Tabelle einem Fremdschlüssel in einer anderen Tabelle zuordnen. Sie können dieses Dialogfeld aufrufen, indem Sie im Menü **Tabellen-Designer** auf **Beziehungen**klicken. Klicken Sie im Dialogfeld **Fremdschlüsselbeziehungen** auf **Tabellen- und Spaltenspezifikation** , und klicken Sie anschließend auf die Auslassungspunkte **(…)** , die rechts neben der Eigenschaft angezeigt werden.  
  
> [!NOTE]  
>  Wenn die Tabelle zur Replikation veröffentlicht ist, müssen Sie mit der Transact-SQL-Anweisung [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) oder mit SMO (SQL Server Management Objects) Schemaänderungen ausführen. Wenn die Schemaänderungen mit dem Tabellen-Designer oder dem Datenbankdiagramm-Designer ausgeführt werden, wird versucht, die Tabelle zu entfernen und erneut zu erstellen. Da veröffentlichte Objekte nicht gelöscht werden können, schlägt die Schemaänderung fehl.  
  
## <a name="options"></a>Tastatur  
 **Beziehungsname**  
 Zeigt den Namen der Beziehung an.  
  
 **Primärschlüsseltabelle**  
 Listet die in der Datenbank enthaltenen Tabellen auf. Wählen Sie die Tabelle für die Primärschlüsselseite der Beziehung aus.  
  
 **Fremdschlüsseltabelle**  
 Zeigt die Tabelle an, die der Fremdschlüsselseite der Beziehung zugeordnet ist. Dabei handelt es sich um die aktuell im Tabellen-Designer ausgewählte Tabelle.  
  
 **Datenblatt unter der Primärschlüsseltabelle**  
 Listet die Spalten der in der Liste **Primärschlüsseltabelle** ausgewählten Tabelle auf. Geben Sie die Spalten ein, die für den Primärschlüssel dieser Tabelle verwendet werden sollen.  
  
 **Datenblatt unter der Fremdschlüsseltabelle**  
 Listet die Spalten der in der Liste **Fremdschlüsseltabelle** ausgewählten Tabelle auf. Geben Sie die Fremdschlüsselspalte der Fremdschlüsseltabelle ein, die der Primärschlüsselspalte entspricht.  
  
> [!NOTE]  
>  Die Spalten, die Sie für den Fremdschlüssel auswählen, müssen denselben Datentyp wie die entsprechenden Primärspalten aufweisen. Die Anzahl der Spalten muss in den jeweiligen Schlüsseln gleich sein. Wenn beispielsweise der Primärschlüssel der Tabelle auf der Primärseite der Beziehung aus zwei Spalten besteht, müssen Sie für jede Spalte eine entsprechende Spalte in der Tabelle für die Fremdschlüsselseite der Beziehung auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Fremdschlüssel-Beziehungen](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
