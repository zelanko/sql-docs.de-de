---
title: Festlegen der Sortierung benutzerdefinierter Datenbanken zur Übereinstimmung mit Master- und Modelldatenbanken
description: Hier erfahren Sie, wie Sie eine Richtlinie aktivieren, um zu überprüfen, ob die Sortierungen von benutzerdefinierten Datenbanken und Systemdatenbanken identisch sind.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 905accc62afdc12152110d44a18e61d4c8a9bcef
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284989"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-master-and-model-databases"></a>Festlegen der Sortierung benutzerdefinierter Datenbanken zur Übereinstimmung mit Master- und Modelldatenbanken
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob benutzerdefinierte Datenbanken unter Verwendung einer Datenbanksortierung definiert sind, die mit der Sortierung der master- oder model-Datenbank übereinstimmt.
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Es wird empfohlen, dass die Sortierungen benutzerdefinierter Datenbanken mit der Sortierung der Datenbanken 'master' oder 'model' übereinstimmen. Andernfalls können Sortierungskonflikte auftreten, die verhindern könnten, dass Code ausgeführt wird. Wenn beispielsweise eine gespeicherte Prozedur eine Tabelle mit einer temporären Tabelle verknüpft und die Sortierungen der benutzerdefinierten Datenbank und der Modelldatenbank unterschiedlich sind, kann SQL Server den Batch beenden und einen Fehler ausgeben, dass ein Sortierungskonflikt vorliegt. Dies ist darauf zurückzuführen, dass temporäre Tabellen in der tempdb-Datenbank erstellt werden, deren Sortierung auf der der model-Datenbank basiert.

  Wenn Sortierungskonfliktfehler auftreten, ziehen Sie eine der folgenden Lösungen in Betracht:

  - Exportieren Sie die Daten aus der Benutzerdatenbank, und importieren Sie sie in neue Tabellen, die dieselbe Sortierung aufweisen wie die master- und model-Datenbanken.

  - Erstellen Sie die Systemdatenbanken so neu, dass sie eine Sortierung verwenden, die mit der Sortierung der Benutzerdatenbank übereinstimmt. Weitere Informationen zum Neuerstellen der Systemdatenbanken finden Sie unter [Neuerstellen von Systemdatenbanken](../databases/rebuild-system-databases.md).

  - Ändern Sie alle gespeicherten Prozeduren, die Benutzertabellen mit Tabellen in der tempdb-Datenbank verknüpfen so, dass die Tabellen in der tempdb-Datenbank unter Verwendung der Sortierung der Benutzerdatenbank erstellt werden. Fügen Sie zu diesem Zweck den Spaltendefinitionen der temporären Tabelle die Klausel COLLATE database_default hinzu. Dies wird im folgenden Beispiel veranschaulicht:
  
    ```
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )
    ```

## <a name="see-also"></a>Weitere Informationen
  
 [Festlegen oder Ändern der Serversortierung](../collations/set-or-change-the-server-collation.md)  

 [Festlegen oder Ändern der Datenbanksortierung](../collations/set-or-change-the-database-collation.md)

 [Festlegen oder Ändern der Spaltensortierung](../collations/set-or-change-the-column-collation.md)
 
 [Anzeigen von Sortierungsinformationen](../collations/view-collation-information.md)    
  
  
