---
title: Verbinden mit SQLServer (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: bc14a072-8949-4ee0-a4b4-ada55fe8df5c
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5765bc458f69fef3dc746bc1970c6555f7888b96
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40393839"
---
# <a name="connect-to-sql-server-db2tosql"></a>Verbinden Sie mit SQLServer (DB2ToSQL)
Verwenden der **Herstellen einer Verbindung mit SQL Server** im Dialogfeld für die Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die Sie zum migrieren möchten. Für den Zugriff auf die **Herstellen einer Verbindung mit SQL Server** Dialogfeld auf die **Datei** Menü klicken Sie auf **Herstellen einer Verbindung mit SQL Server**.  
  
## <a name="options"></a>Tastatur  
**Servername**  
Geben Sie an, oder wählen Sie die Instanz von SQL Server für die Verbindung. Standardmäßig wird die Instanz, der Sie zuletzt verbunden.  
  
-   Wenn Sie mit der Standardinstanz auf dem lokalen Computer herstellen, geben Sie entweder **"localhost"** oder einen Punkt (**.**).  
  
-   Wenn Sie mit der Standardinstanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
-   Wenn Sie die zu einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers, einen umgekehrten Schrägstrich und der Instanzname z. B. *"myserver"*\\*MyInstance*.  
  
**Serverport**  
Wenn Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist zum Akzeptieren von Verbindungen auf dem standardmäßigen Standardport (1433), geben Sie die Portnummer nicht konfiguriert. Andernfalls lassen Sie diesen Wert leer.  
  
**Datenbank**  
Geben Sie die Datenbank, um Objekte und Daten zu migrieren. Diese Option ist nicht verfügbar, wenn Sie zum Wiederherstellen der Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Authentifizierung**  
Wählen Sie die Authentifizierungsmethode, die verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Um das aktuelle Windows-Konto zu verwenden, wählen Sie Windows-Authentifizierung. Angeben einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldenamen und das Kennwort, wählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.  
  
**Benutzername**  
Bei Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie den Anmeldenamen für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie Windows-Authentifizierung verwenden, ist diese Option nicht verfügbar.  
  
**Kennwort**  
Bei Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, geben Sie das Kennwort für die Anmeldung auf dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie Windows-Authentifizierung verwenden, ist diese Option nicht verfügbar.  
  
**Verbindung verschlüsseln**  
Wenn Sie eine sichere Verbindung mit SQL Server möchten, stellen Verwendung der Verbindung verschlüsseln, indem Sie überprüfen die **Verbindung verschlüsseln** Kontrollkästchen.  
  
**TrustServerCertificate**  
Wenn Sie diese Option verwenden möchten, wählen Sie die **dem Serverzertifikat vertrauen** Kontrollkästchen.  
  
> [!NOTE]  
> So aktivieren Sie **dem Serverzertifikat vertrauen**, "Verschlüsseln" müssen festgelegt werden, um **"true"**.  
  
