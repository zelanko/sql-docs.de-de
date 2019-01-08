---
title: Auswählen von Oracle-Tabellen und -Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af7f97d7d1671aada299b685981e81d62010df24
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52788343"
---
# <a name="select-oracle-tables-and-columns"></a>Auswählen von Oracle-Tabellen und -Spalten
  Verwenden Sie die Seite Select Oracle Tables and Columns, um die Tabellen aus der Oracle-Quelldatenbank auszuwählen, in der die Änderungen aufgezeichnet werden. Diese Seite verfügt über die folgenden Elemente:  
  
## <a name="options"></a>Optionen  
 **Tabellenliste**  
 Die Tabellenliste enthält drei Spalten:  
  
-   **Oracle Table Name**: Der Name der Tabelle, einschließlich des Tabellenschemas.  
  
-   **Aufzeichnungsinstanz**: Der Name der Aufzeichnungsinstanz verwendet, um Namen instanzspezifischen Change Data Capture-Objekte. Die Aufzeichnungsinstanz darf nicht NULL sein.  
  
     Wenn kein Name angegeben wird, wird der Name aus dem Quellschemanamen und dem Quelltabellennamen im Format `<schema-name>_<table-name>`abgeleitet. Der Name der Aufzeichnungsinstanz darf nicht länger als 100 Zeichen sein und muss innerhalb der Datenbank eindeutig sein.  
  
     Sie können in dieser Spalte in jede Zelle klicken, um die **capture_instance**manuell zu bearbeiten.  
  
-   **Rolle "Sicherheit"**: Der Name der Datenbank gatingrolle, die Zugriff auf Änderungsdaten gesteuert wird.  
  
     Sie können in dieser Spalte in jede Zelle klicken, um die **security_role**manuell zu bearbeiten.  
  
 **Tabellen hinzufügen**  
 Klicken Sie auf **Tabellen hinzufügen** , um das Dialogfeld „Tabellenauswahl“ zu öffnen und den Schritt [Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen](select-oracle-tables-for-capturing-changes.md)auszuführen.  
  
 **Bearbeiten**  
 Wählen Sie in der Liste eine Tabelle aus, und wählen Sie **Bearbeiten** aus, um das Dialogfeld **Eigenschaften** für die Tabelle zu öffnen, in dem Sie den Schritt [Vornehmen von Änderungen an den zum Aufzeichnen von Änderungen ausgewählten Tabellen](make-changes-to-the-tables-selected-for-capturing-changes.md)ausführen können.  
  
 **Entfernen**  
 Wählen Sie in der Liste eine Tabelle aus, und klicken Sie auf **Entfernen** , um die Tabelle aus der CDC-Instanz zu entfernen.  
  
 Klicken Sie nach dem [Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen](select-oracle-tables-for-capturing-changes.md) und/oder dem [Vornehmen von Änderungen an den zum Aufzeichnen von Änderungen ausgewählten Tabellen](make-changes-to-the-tables-selected-for-capturing-changes.md) in den entsprechenden Dialogfeldern auf **Weiter** , um den Schritt [Generieren und Ausführen des ergänzenden Protokollierungsskripts](generate-and-run-the-supplemental-logging-script.md)auszuführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](how-to-create-the-sql-server-change-database-instance.md)   
 [Bearbeiten von Tabellen](edit-tables.md)   
 [Hinzufügen von Tabellen zu einer CDC-Instanz](add-tables-to-a-cdc-instance.md)   
 [Bearbeiten der Tabelleneigenschaften](edit-the-table-properties.md)  
  
  
