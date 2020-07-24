---
title: Anzeigen des SQL Server-Fehlerprotokolls (SSMS)
description: Hier lernen Sie das SQL Server-Fehlerprotokoll kennen, das benutzerdefinierte Ereignisse und bestimmte Systemereignisse enthält, die für die Problembehandlung nützlich sind.
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
ms.openlocfilehash: 54aa4b48837f171406edbbe4cbadcacf5b910a99
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458052"
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

