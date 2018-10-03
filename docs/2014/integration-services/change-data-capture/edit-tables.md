---
title: Bearbeiten von Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f8945827cb4a0170ceac43c313554b9a88db478
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215010"
---
# <a name="edit-tables"></a>Bearbeiten von Tabellen
  Verwenden Sie die Registerkarte **Tabellen** , um Änderungen an den Tabellen und Spalten vorzunehmen, die Sie in der Oracle-Quelldatenbank ausgewählt haben. Diese Registerkarte verfügt über die folgenden Elemente:  
  
 **Liste 'Tabelle'**  
 Die Tabellenliste enthält drei Spalten:  
  
-   **Oracle Table Name**: Der Name der Tabelle, einschließlich des Tabellenschemas.  
  
-   **Capture Instance:** Der Name der Aufzeichnungsinstanz, die für die Benennung der instanzspezifischen Change Data Capture-Objekte verwendet wird. Die Aufzeichnungsinstanz darf nicht NULL sein. Wenn der Name nicht angegeben ist, wird er vom Namen des Quellschemas sowie vom Namen der Quelltabelle im Format `<schema-name>_<table-name>.` abgeleitet. Der Name der Aufzeichnungsinstanz darf maximal 100 Zeichen umfassen und muss innerhalb der Datenbank eindeutig sein. Sie können in dieser Spalte in jede Zelle klicken, um die **capture_instance**manuell zu bearbeiten.  
  
-   **Security Role**: Der Name der Datenbankrolle, mit deren Hilfe der Zugriff auf die Änderungsdaten erlangt wird. Sie können in dieser Spalte in jede Zelle klicken, um die **security_role**manuell zu bearbeiten.  
  
 **Tabellen hinzufügen**  
 Klicken Sie auf **Tabellen hinzufügen** , um das Dialogfeld „Tabellenauswahl“ zu öffnen und den Schritt [Hinzufügen von Tabellen zu einer CDC-Instanz](add-tables-to-a-cdc-instance.md)auszuführen. Bei der ersten Sitzung, bei der Sie auf die Oracle-Datenbank zugreifen, müssen Sie den Schritt [Connect to Oracle](connect-to-oracle.md)ausführen.  
  
 **Bearbeiten**  
 Wählen Sie in der Liste eine Tabelle aus, und wählen Sie **Bearbeiten** aus, um das Dialogfeld **Eigenschaften** für die Tabelle zu öffnen, in dem Sie den Schritt [Bearbeiten der Tabelleneigenschaften](edit-the-table-properties.md)ausführen können.  
  
> [!NOTE]  
>  Sie können die Typzuordnung nicht für Tabellen bearbeiten, die bereits über Spiegeltabellen verfügen. Dies ist nur für neue Tabellen möglich.  
  
 **Entfernen**  
 Wählen Sie in der Liste eine Tabelle aus, und klicken Sie auf **Entfernen** , um die Tabelle aus der CDC-Instanz zu entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Bearbeiten der CDC-Instanzeigenschaften](how-to-edit-the-cdc-instance-properties.md)   
 [Auswählen von Oracle-Tabellen und -Spalten](select-oracle-tables-and-columns.md)  
  
  
