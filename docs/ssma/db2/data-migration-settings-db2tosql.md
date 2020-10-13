---
description: Daten Migrations Einstellungen (DB2ToSQL)
title: Daten Migrations Einstellungen (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 573e673e-a194-4cb2-9aba-aaac6e1a225c
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 0646fc033f73134a4dfcba62e574ba08e378b9cc
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91984876"
---
# <a name="data-migration-settings-db2tosql"></a>Daten Migrations Einstellungen (DB2ToSQL)
  
## <a name="data-migration-settings"></a>Einstellungen für die Datenmigration  
**Daten Migrations Einstellungen** ermöglichen es dem Benutzer, benutzerdefinierte Abfragen für die Datenmigration zu schreiben.  
  
-   Diese Registerkarte ist verfügbar, wenn **Erweiterte Daten Migrations Optionen** auf **anzeigen** festgelegt ist und ausgeblendet ist, wenn die Einstellung in den Projekteinstellungen **Ausblenden** festgelegt ist. Weitere Informationen zu den Einstellungen für die Projekt Migration finden Sie unter [Project Settings (Migration)](./project-settings-migration-db2tosql.md) .  
  
-   Die Verarbeitung von benutzerdefinierten SQL-Anweisungen wird auf der Registerkarte **Daten Migrations Einstellungen** des Tabellen Knotens implementiert.  
  
-   Im folgenden finden Sie die beiden Kontrollkästchen, die in den Einstellungen für die **Daten Migration** angezeigt werden:  
  
    1.  SQL Server Tabelle abschneiden  
  
    2.  Benutzerdefinierte Auswahl verwenden  
  
1.  **SQL Server Tabelle abschneiden:**  
     Diese Option ermöglicht dem Benutzer eine klare Ansicht der migrierten Daten in der Zieldatenbank.  
  
    -   Standardmäßig ist dieses Textfeld aktiviert.  
  
    -   Wenn dieses Textfeld nicht aktiviert ist, werden die migrierten Daten den vorhandenen Daten in der Zieldatenbank hinzugefügt.  
  
2.  **Benutzerdefinierte Select-Option verwenden:**  
     Mit dieser Option kann der Benutzer die vorhandene **Select** -Anweisung ändern (die**Select** -Anweisung ermöglicht es Benutzern, die Daten auszuwählen, die in der Zieldatenbank angezeigt werden sollen).  
  
    1.  Standardmäßig ist dieses Textfeld deaktiviert.  
  
    2.  Wenn dieses Textfeld aktiviert ist, können die Benutzer die vorhandene **Select** -Anweisung ändern.  
  
Es stehen zwei Schaltflächen zur Verfügung:  
  
-   **Anwenden:** Klicken Sie auf **anwenden** , um die Einstellungen zu übernehmen, die geändert wurden.  
  
-   **Abbrechen:** Klicken Sie auf **Abbrechen** , um die vorhandenen Einstellungen wiederherzustellen, bevor die Änderungen vorgenommen wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Daten zu SQL Server](./migrating-db2-data-into-sql-server-db2tosql.md)  
