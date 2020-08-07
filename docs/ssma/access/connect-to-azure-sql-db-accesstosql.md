---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 34e25824ee95745bd5069a6ed601318d47a96e81
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87865248"
---
# <a name="connect-to-azure-sql-database-accesstosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (accesstosql)
Verwenden Sie das Dialogfeld mit SQL Azure verbinden, um eine Verbindung mit der SQL Azure Datenbank herzustellen, die Sie migrieren möchten.  
  
Um auf dieses Dialogfeld zuzugreifen, wählen Sie im Menü **Datei** die Option **mit SQL Azure verbinden**aus. Wenn Sie bereits eine Verbindung hergestellt haben, stellt der Befehl **erneut eine Verbindung mit SQL Azure her.**  
  
## <a name="options"></a>Optionen  
**Servername**  
  
Geben Sie den Server Namen für die Verbindung mit SQL Azure ein  
  
**Datenbank**  
  
Wählen **Sie den Daten** Banknamen aus, oder geben Sie ihn ein.  
  
> [!IMPORTANT]  
> SSMA für Access unterstützt keine Verbindung mit der Master-Datenbank in SQL Azure.  
  
**Benutzername**  
  
Geben Sie den Benutzernamen ein, den SSMA zum Herstellen einer Verbindung mit der SQL Azure Datenbank verwendet.  
  
**Kennwort**  
  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**Encrypt**  
  
SSMA empfiehlt eine verschlüsselte Verbindung mit SQL Azure.  
  
## <a name="create-database"></a>Erstellen einer Datenbank  
Führen Sie die folgenden Schritte aus, um eine neue Datenbank zu erstellen.  
  
1.  Klicken Sie auf die Schaltfläche Durchsuchen, die im Dialogfeld Verbindung mit SQL Azure herstellen vorhanden ist.  
  
2.  Wenn keine Datenbanken vorhanden sind, werden zwei Menü Elemente angezeigt.  
  
    1.  **(keine Datenbanken gefunden)** , die deaktiviert und ständig ausgegraut sind  
  
    2.  **Erstellen Sie eine neue Datenbank** , die immer aktiviert ist und es dem Benutzer ermöglicht, eine neue Datenbank zu erstellen. Wenn Sie auf dieses Menü Element klicken, ist das Dialogfeld Datenbank erstellen mit dem Datenbanknamen und der Größe vorhanden.  
  
3.  Zum Zeitpunkt der Erstellung der Datenbank werden diese beiden Parameter als Eingabe angegeben.  
  
    1.  **Datenbankname:** Geben Sie den Datenbanknamen ein.  
  
    2.  **Datenbankgröße:** Wählen Sie die Datenbankgröße aus, die Sie in SQL Azure Konto erstellen müssen.  
  
