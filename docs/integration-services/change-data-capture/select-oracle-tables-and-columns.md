---
title: Auswählen von Oracle-Tabellen und -Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0d550361063bd051e146b8fc350ae63b0b57c399
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728557"
---
# <a name="select-oracle-tables-and-columns"></a>Auswählen von Oracle-Tabellen und -Spalten

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Verwenden Sie die Seite Select Oracle Tables and Columns, um die Tabellen aus der Oracle-Quelldatenbank auszuwählen, in der die Änderungen aufgezeichnet werden. Diese Seite verfügt über die folgenden Elemente:  
  
## <a name="options"></a>enthalten  
 **Tabellenliste**  
 Die Tabellenliste enthält drei Spalten:  
  
-   **Oracle Table Name**: Der Name der Tabelle, einschließlich des Tabellenschemas.  
  
-   **Capture Instance**: Der Name der Aufzeichnungsinstanz, die für die Benennung der instanzspezifischen Change Data Capture-Objekte verwendet wird. Die Aufzeichnungsinstanz darf nicht NULL sein.  
  
     Wenn kein Name angegeben wird, wird der Name aus dem Quellschemanamen und dem Quelltabellennamen im Format `<schema-name>_<table-name>`abgeleitet. Der Name der Aufzeichnungsinstanz darf nicht länger als 100 Zeichen sein und muss innerhalb der Datenbank eindeutig sein.  
  
     Sie können in dieser Spalte in jede Zelle klicken, um die **capture_instance**manuell zu bearbeiten.  
  
-   **Security Role**: Der Name der Datenbank-Gatingrolle, mit deren Hilfe der Zugriff auf die Änderungsdaten gesteuert wird.  
  
     Sie können in dieser Spalte in jede Zelle klicken, um die **security_role**manuell zu bearbeiten.  
  
 **Tabellen hinzufügen**  
 Klicken Sie auf **Tabellen hinzufügen** , um das Dialogfeld „Tabellenauswahl“ zu öffnen und den Schritt [Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen](../../integration-services/change-data-capture/select-oracle-tables-for-capturing-changes.md)auszuführen.  
  
 **Bearbeiten**  
 Wählen Sie in der Liste eine Tabelle aus, und wählen Sie **Bearbeiten** aus, um das Dialogfeld **Eigenschaften** für die Tabelle zu öffnen, in dem Sie den Schritt [Vornehmen von Änderungen an den zum Aufzeichnen von Änderungen ausgewählten Tabellen](../../integration-services/change-data-capture/make-changes-to-the-tables-selected-for-capturing-changes.md)ausführen können.  
  
 **Entfernen**  
 Wählen Sie in der Liste eine Tabelle aus, und klicken Sie auf **Entfernen** , um die Tabelle aus der CDC-Instanz zu entfernen.  
  
 Klicken Sie nach dem [Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen](../../integration-services/change-data-capture/select-oracle-tables-for-capturing-changes.md) und/oder dem [Vornehmen von Änderungen an den zum Aufzeichnen von Änderungen ausgewählten Tabellen](../../integration-services/change-data-capture/make-changes-to-the-tables-selected-for-capturing-changes.md) in den entsprechenden Dialogfeldern auf **Weiter** , um den Schritt [Generieren und Ausführen des ergänzenden Protokollierungsskripts](../../integration-services/change-data-capture/generate-and-run-the-supplemental-logging-script.md)auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Bearbeiten von Tabellen](../../integration-services/change-data-capture/edit-tables.md)   
 [Hinzufügen von Tabellen zu einer CDC-Instanz](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)   
 [Bearbeiten der Tabelleneigenschaften](../../integration-services/change-data-capture/edit-the-table-properties.md)  
  
  
