---
title: Verbinden mit Azure Sqldb (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 057a39fd393be6cce9232d787b0d110a4be2035a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640908"
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Herstellen einer Verbindung mit Azure SQL-DB (SybaseToSQL)
Verwenden Sie die Connect zu Azure SQL-Datenbank (Dialogfeld), für die Verbindung der Azure SQL-Datenbank, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit Azure SQL-Datenbank**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung zur Azure SQL-Datenbank.**  
  
## <a name="options"></a>Tastatur  
**Servername**  
  
Wählen Sie aus, oder geben Sie den Servernamen für die Verbindung mit Azure SQL-Datenbank.  
  
**Datenbank**  
  
Wählen Sie aus, geben Sie ein oder **Durchsuchen** der Name der Datenbank.  
  
> [!IMPORTANT]  
> SSMA für Sybase unterstützt keine Verbindung mit der master-Datenbank in Azure SQL-Datenbank.  
  
**Benutzername**  
  
Geben Sie den Benutzernamen, mit der SSMA mit der Azure SQL-Datenbank verbinden  
  
**Kennwort**  
  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**Encrypt**  
  
SSMA empfiehlt verschlüsselte Verbindung für Azure SQL-Datenbank.  
  
## <a name="create-azure-database"></a>Erstellen von Azure-Datenbank  
Wenn keine Datenbanken in Azure SQL-DB-Konto vorhanden sind, können Sie die erste Datenbank erstellen.  
  
Führen Sie die folgenden Schritte aus, um eine neue Datenbank zum ersten Mal erstellen,  
  
1.  Klicken Sie auf die Schaltfläche zum Durchsuchen, die in Verbindung zu Azure SQL-Datenbank (Dialogfeld) vorhanden ist  
  
2.  Wenn keine Datenbanken vorhanden sind, werden die folgenden zwei Menüelemente angezeigt.  
  
    1.  **(keine Datenbanken gefunden.)**  die deaktiviert und ausgegraut, ständig  
  
    2.  **Erstellen Sie neue Datenbank** die ist nur aktiviert, wenn keine Datenbanken für Azure SQL-DB-Konto vorhanden sind. Nach dem Klicken auf dieses Menüelement, für Azure-Datenbank erstellen (Dialogfeld) mit Datenbanknamen und Größe vorhanden ist.  
  
3.  Zum Zeitpunkt der Erstellung der Datenbank sind die folgenden beiden Parameter als Eingabe übergeben:  
  
    1.  **Datenbankname:** Geben Sie den Datenbanknamen.  
  
    2.  **Datenbankgröße:** wählen Sie die Größe der Datenbank, die Sie benötigen, um in Azure SQL-DB-Konto zu erstellen.  
  
