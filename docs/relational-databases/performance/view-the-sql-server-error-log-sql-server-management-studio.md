---
title: Anzeigen des SQL Server-Fehlerprotokolls (SSMS)
description: Anzeigen des SQL Server-Fehlerprotokolls in SQL Server Management Studio (SSMS)
ms.custom: seo-dt-2019
ms.date: 09/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: a10948a63d119ec86c156b79d925f1b905b152f4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737077"
---
# <a name="view-the-sql-server-error-log-in-sql-server-management-studio-ssms"></a>Anzeigen des SQL Server-Fehlerprotokolls in SQL Server Management Studio (SSMS)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll enthält benutzerdefinierte Ereignisse und bestimmte Systemereignisse, die für die Problembehandlung nützlich sind. 

## <a name="view-the-logs"></a>Anzeigen der Protokolle

1. Wählen Sie in SQL Server Management Studio die Option **Objekt-Explorer** aus. Um den **Objekt-Explorer** zu öffnen, wählen Sie F8 aus. Alternativ klicken Sie im Hauptmenü auf **Ansicht**, und wählen Sie dann **Objekt-Explorer** aus:
    
    ![Object_Explorer](../../relational-databases/performance/media/object-explorer.png) 

2. Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von SQL Server her, und erweitern Sie dann diese Instanz.
  
3. Suchen und erweitern Sie den Abschnitt **Verwaltung** (unter der Voraussetzung, dass Sie über Berechtigungen zum Anzeigen verfügen).

4. Klicken Sie mit der rechten Maustaste auf **SQL Server-Protokolle**, wählen Sie erst **Ansicht** und anschließend **SQL Server-Protokoll** aus.

    ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5. Der **Protokolldatei-Viewer** wird geöffnet, und es wird eine Liste der verfügbaren Protokolle angezeigt (dies kann einen Moment dauern).

  ## <a name="see-also"></a>Weitere Informationen
  Weitere Informationen finden Sie in dem nützlichen [MSSQLTips.com](https://www.mssqltips.com/)-Beitrag [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/) (Bestimmen des Speicherorts der SQL Server-Fehlerprotokolldatei).

