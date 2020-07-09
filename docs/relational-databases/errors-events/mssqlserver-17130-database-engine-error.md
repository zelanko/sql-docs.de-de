---
title: MSSQLSERVER_17130 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 19fdbd6e3c8870e57acb81b4d1b923516da2b5a7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780866"
---
# <a name="mssqlserver_17130"></a>MSSQLSERVER_17130
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|17130|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|INIT_NOLOCKSPACE|  
|Meldungstext|Nicht genügend Arbeitsspeicher für die konfigurierte Anzahl von Sperren. Das Starten wird mit einer kleineren Sperrhashtabelle versucht. Dies kann Auswirkungen auf die Leistung haben. Bitten Sie den Datenbankadministrator, mehr Arbeitsspeicher für diese Instanz der Datenbank-Engine zu konfigurieren.|  
  
## <a name="explanation"></a>Erklärung  
Nicht genug Arbeitsspeicher für die gewünschte Hashtabellengröße des Sperren-Managers.  Es wird versucht, eine kleinere Hashtabelle zuzuordnen.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie die Konfigurationsparameter des Serverarbeitsspeichers (minimaler/maximaler Serverarbeitsspeicher) und die Arbeitsspeicherauslastung. Stellen Sie für SQL Server mehr Arbeitsspeicher zur Verfügung.  
  
