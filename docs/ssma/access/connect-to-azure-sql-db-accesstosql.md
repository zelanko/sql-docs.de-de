---
title: Verbinden mit Azure SQL-Datenbank (AccessToSQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 57a745385de80a3040897310ddc5b43b1301ea86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717478"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Verbinden Sie mit Azure SQL-Datenbank (AccessToSQL)
Verwenden Sie die Connect SQL Azure-Dialogfeld zur Verbindung mit der SQL Azure-Datenbank, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Azure**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung zu SQL Azure.**  
  
## <a name="options"></a>Tastatur  
**Servername**  
  
Wählen Sie aus, oder geben Sie den Servernamen für die Verbindung mit SQL Azure.  
  
**Datenbank**  
  
Wählen Sie aus, geben Sie ein oder **Durchsuchen** der Name der Datenbank.  
  
> [!IMPORTANT]  
> SSMA für Access unterstützt keine Verbindung mit der master-Datenbank in SQL Azure.  
  
**Benutzername**  
  
Geben Sie den Benutzernamen, mit der SSMA mit der SQL Azure-Datenbank herstellen  
  
**Kennwort**  
  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**Encrypt**  
  
SSMA empfiehlt verschlüsselte Verbindung für SQL Azure.  
  
## <a name="create-azure-database"></a>Erstellen von Azure-Datenbank  
Führen Sie die folgenden Schritte aus, um eine neue Azure-Datenbank zu erstellen,  
  
1.  Klicken Sie auf die Schaltfläche zum Durchsuchen, die in Verbindung zu SQL Azure (Dialogfeld) vorhanden ist  
  
2.  Wenn keine Datenbanken vorhanden sind, werden zwei Menüelemente angezeigt.  
  
    1.  **(keine Datenbanken gefunden.)**  die deaktiviert und ausgegraut, ständig  
  
    2.  **Erstellen Sie neue Datenbank** die immer aktiviert ist, aktiviert des Benutzers eine neue Azure-Datenbank in SQL Azure-Konto zu erstellen. Nach dem Klicken auf dieses Menüelement aus, erstellen Sie im Dialogfeld Azure-Datenbank vorhanden ist und über Datenbank- und Größe.  
  
3.  Zum Zeitpunkt der Erstellung der Datenbank dass diese beiden Parameter als Eingabe erhält.  
  
    1.  **Datenbankname:** Geben Sie den Datenbanknamen.  
  
    2.  **Datenbankgröße:** wählen Sie die Größe der Datenbank, die in SQL Azure-Konto erstellen müssen.  
  
