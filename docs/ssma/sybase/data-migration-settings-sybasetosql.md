---
description: Einstellungen für die Datenmigration (SybaseToSQL)
title: Einstellungen für die Daten Migration (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 6fcca84f52f5a6b9b8c033c00980374a0c17d7be
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036684"
---
# <a name="data-migration-settings-sybasetosql"></a>Einstellungen für die Datenmigration (SybaseToSQL)
  
## <a name="data-migration-settings"></a>Einstellungen für die Datenmigration  
**Daten Migrations Einstellungen** ermöglichen es dem Benutzer, benutzerdefinierte Abfragen für die Datenmigration zu schreiben.  
  
-   Diese Registerkarte ist verfügbar, wenn **Erweiterte Daten Migrations Optionen** auf **anzeigen** festgelegt ist und ausgeblendet ist, wenn die Einstellung in den Projekteinstellungen **Ausblenden** festgelegt ist. Weitere Informationen zu den Einstellungen für die Projekt Migration finden Sie unter [Project Settings (Migration)](./project-settings-migration-sybasetosql.md) .  
  
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
[Migrieren von Sybase-Daten zu SQL Server/SQL Azure](./migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md)  
