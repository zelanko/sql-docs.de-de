---
title: Tabellen und Spalten (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce7a90a76547d579324fa61246b5b126be8f4b72
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52528008"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>Tabellen und Spalten (Dialogfeld) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In diesem Dialogfeld können Sie einen Primärschlüssel in einer Tabelle einem Fremdschlüssel in einer anderen Tabelle zuordnen. Sie können dieses Dialogfeld aufrufen, indem Sie im Menü **Tabellen-Designer** auf **Beziehungen**klicken. Klicken Sie im Dialogfeld **Fremdschlüsselbeziehungen** auf **Tabellen- und Spaltenspezifikation**, und klicken Sie anschließend auf die Auslassungspunkte **(…)**, die rechts neben der Eigenschaft angezeigt werden.  
  
> [!NOTE]  
> Wenn die Tabelle zur Replikation veröffentlicht ist, müssen Sie mit der Transact-SQL-Anweisung [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder mit SMO (SQL Server Management Objects) Schemaänderungen ausführen. Wenn die Schemaänderungen mit dem Tabellen-Designer oder dem Datenbankdiagramm-Designer ausgeführt werden, wird versucht, die Tabelle zu entfernen und erneut zu erstellen. Da veröffentlichte Objekte nicht gelöscht werden können, schlägt die Schemaänderung fehl.  
  
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
> Die Spalten, die Sie für den Fremdschlüssel auswählen, müssen denselben Datentyp wie die entsprechenden Primärspalten aufweisen. Die Anzahl der Spalten muss in den jeweiligen Schlüsseln gleich sein. Wenn beispielsweise der Primärschlüssel der Tabelle auf der Primärseite der Beziehung aus zwei Spalten besteht, müssen Sie für jede Spalte eine entsprechende Spalte in der Tabelle für die Fremdschlüsselseite der Beziehung auswählen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Vorgehensweise: Erstellen von Beziehungen zwischen Tabellen (Visual Database Tools)](https://msdn.microsoft.com/867a54b8-5be4-46e6-9702-49ae6dabf67c)  
  
