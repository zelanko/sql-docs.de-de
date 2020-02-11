---
title: Herstellen einer Verbindung mit SQL Server (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d73abd3a-80df-4293-b973-1723069db049
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8dc64c84a8d14ea86893d52044894e0af2b1a3bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103216"
---
# <a name="connect-to-sql-server-mysqltosql"></a>Herstellen einer Verbindung mit SQL Server (MySqlToSql)
Verwenden Sie das Dialogfeld **mit SQL Server verbinden** , um eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Instanz von herzustellen, zu der Sie migrieren möchten. Um auf das Dialogfeld **Verbindung mit SQL Server herstellen** zuzugreifen, klicken Sie im Menü **Datei** auf **Verbinden mit SQL Server**.  
  
## <a name="options"></a>Tastatur  
**Servername**  
Geben Sie die SQL Server-Instanz ein, mit der eine Verbindung hergestellt werden soll. Standardmäßig wird die Instanz angezeigt, mit der Sie zuletzt eine Verbindung hergestellt haben.  
  
-   Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie entweder **localhost** oder einen Punkt (**.**) eingeben.  
  
-   Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
-   Wenn Sie eine Verbindung mit einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen, einen umgekehrten Schrägstrich und den Instanznamen ein, z. b. *myserver*\\*MyInstance*.  
  
**Serverport**  
Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht für die Annahme von Verbindungen am Standardport (1433) konfiguriert ist, geben Sie die Portnummer ein. Andernfalls lassen Sie diesen Wert leer.  
  
**Datenbank**  
Gibt die Datenbank an, zu der Objekte und Daten migriert werden sollen. Diese Option ist nicht verfügbar, wenn Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erneute Verbindung mit herstellen.  
  
**Authentifizierung**  
Wählen Sie die Authentifizierungsmethode aus, die zum Herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]einer Verbindung mit verwendet wird. Um Ihr aktuelles Windows-Konto zu verwenden, wählen Sie Windows-Authentifizierung aus. Wählen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus, um einen Anmelde Namen und ein Kennwort anzugeben.  
  
**Benutzername**  
Wenn Sie die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung verwenden, geben Sie den-Anmelde Namen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]für diese Instanz von ein. Wenn Sie die Windows-Authentifizierung verwenden, ist diese Option nicht verfügbar.  
  
**Kennwort**  
Wenn Sie die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung verwenden, geben Sie das Kennwort für die Anmeldung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dieser Instanz von ein. Wenn Sie die Windows-Authentifizierung verwenden, ist diese Option nicht verfügbar.  
  
**Verbindung verschlüsseln**  
Wenn Sie eine sichere Verbindung mit SQL Server herstellen möchten, verwenden Sie die Option Verbindung verschlüsseln, indem Sie das Kontrollkästchen **Verbindung verschlüsseln** aktivieren.  
  
**Server Zertifikat vertrauen**  
Wenn Sie diese Option verwenden möchten, aktivieren Sie das Kontrollkästchen **Server Zertifikat vertrauen** .  
  
> [!NOTE]  
> Zum Aktivieren des **Trust Server-Zertifikats**muss "verschlüsseln" auf " **true**" festgelegt sein.  
  
