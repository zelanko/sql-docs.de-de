---
title: Verbinden mit SQLServer (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ceb77a97-d6d5-4a92-90a6-342e97d12b54
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7a3e6b18377f01d93dfb4bdda840bc6abc0dafee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63139057"
---
# <a name="connect-to-sql-server-accesstosql"></a>Verbinden Sie mit SQLServer (AccessToSQL)
Verwenden der **Herstellen einer Verbindung mit SQL Server** im Dialogfeld für die Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die Sie zum migrieren möchten. Für den Zugriff auf die **Herstellen einer Verbindung mit SQL Server** Dialogfeld auf die **Datei** Menü klicken Sie auf **Herstellen einer Verbindung mit SQL Server**.  
  
## <a name="options"></a>Optionen  
**Servername**  
Geben Sie an, oder wählen Sie die Instanz von SQL Server für die Verbindung. Standardmäßig wird die Instanz, der Sie zuletzt verbunden.  
  
-   Wenn Sie mit der Standardinstanz auf dem lokalen Computer herstellen, geben Sie entweder **"localhost"** oder einen Punkt ( **.** ).  
  
-   Wenn Sie mit der Standardinstanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
-   Wenn Sie die zu einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers, einen umgekehrten Schrägstrich und der Instanzname z. B. *"myserver"* \\*MyInstance*.  
  
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
> So aktivieren Sie **dem Serverzertifikat vertrauen**, "Verschlüsseln" müssen festgelegt werden, um **"true"** .  
  
