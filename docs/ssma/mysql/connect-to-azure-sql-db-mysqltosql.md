---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 12da1aa42f468b92e1833410e635183aabf3a384
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103246"
---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Herstellen einer Verbindung mit Azure SQL-DB (MySQLToSQL)
Verwenden Sie das Dialogfeld mit SQL Azure verbinden, um eine Verbindung mit der SQL Azure Datenbank herzustellen, die Sie migrieren möchten.  
  
Um auf dieses Dialogfeld zuzugreifen, wählen Sie im Menü **Datei** die Option **mit SQL Azure verbinden**aus. Wenn Sie bereits eine Verbindung hergestellt haben, stellt der Befehl **erneut eine Verbindung mit SQL Azure her.**  
  
## <a name="options"></a>Tastatur  
**Server Name**  
  
Geben Sie den Server Namen für die Verbindung mit SQL Azure ein  
  
**Datenbank**  
  
Wählen **Sie den Daten** Banknamen aus, oder geben Sie ihn ein.  
  
> [!IMPORTANT]  
> SSMA für MySQL unterstützt keine Verbindung mit der Master-Datenbank in SQL Azure.  
  
**Benutzername**  
  
Geben Sie den Benutzernamen ein, den SSMA zum Herstellen einer Verbindung mit der SQL Azure Datenbank verwendet.  
  
**Kennwort**  
  
Geben Sie das Kennwort für den Benutzernamen ein,  
  
**Eingegebenen**  
  
SSMA empfiehlt eine verschlüsselte Verbindung mit SQL Azure.  
  
## <a name="create-azure-database"></a>Azure-Datenbank erstellen  
Wenn das SQL Azure-Konto keine Datenbanken enthält, können Sie die erste Datenbank erstellen.  
  
Führen Sie die folgenden Schritte aus, um eine neue Datenbank zum ersten Mal zu erstellen:  
  
1.  Klicken Sie auf die Schaltfläche Durchsuchen, die im Dialogfeld Verbindung mit SQL Azure herstellen vorhanden ist.  
  
2.  Wenn keine Datenbanken vorhanden sind, werden die folgenden zwei Menü Elemente angezeigt.  
  
    1.  **(keine Datenbanken gefunden)** , die deaktiviert und ständig ausgegraut sind  
  
    2.  **Erstellen Sie eine neue Datenbank** , die nur aktiviert ist, wenn keine Datenbanken auf SQL Azure Konto vorhanden sind. Wenn Sie auf dieses Menü Element klicken, ist das Dialogfeld Azure-Datenbank erstellen mit Datenbankname und-Größe vorhanden.  
  
3.  Zum Zeitpunkt der Erstellung der Datenbank werden die folgenden beiden Parameter als Eingabe angegeben:  
  
    1.  **Datenbankname:** Geben Sie den Datenbanknamen ein.  
  
    2.  **Datenbankgröße:** Wählen Sie die Datenbankgröße aus, die Sie in SQL Azure Konto erstellen müssen.  
  
