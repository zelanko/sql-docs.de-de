---
title: Entfernen von SQL Server Data Tools-Komponenten | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 124b4f4f591966d8dc5294f3150892091f71ba74
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094291"
---
# <a name="removing-sql-server-data-tools-components"></a>Entfernen von SQL Server Data Tools-Komponenten
Einige SSDT-Komponenten (SQL Server Data Tools) werden bei der Deinstallation von SSDT bzw. Visual Studio nicht entfernt.  
  
Die folgenden Windows Installer-Pakete (.msi) werden bei der Deinstallation von SSDT bzw. Visual Studio nicht vom Computer entfernt. Das Entfernen dieser Komponenten kann dazu führen, dass andere Visual Studio-Versionen nicht mehr unterstützt werden. Zum Entfernen dieser Komponenten verwenden Sie die Windows-Option zum Hinzufügen/Entfernen von Programmen:  
  
-   Microsoft SQL Server Data Tools (SSDT.msi)  
  
-   Microsoft SQL Server Data Tools-Buildhilfsprogramme (SSDTBuildUtilities.msi)  
  
-   Erforderliche Komponenten für SSDT (SSDTDBSvcExternals.msi)  
  
Die folgenden freigegebenen Komponenten werden möglicherweise von anderen Produkten verwendet und verbleiben nach der Deinstallation von SSDT auf dem Computer.  
  
-   SQL Server Data-Tier Application Framework (DACFramework.msi)  
  
-   SQL Server Management Objects (SharedManagementObjects.msi)  
  
-   SQL Server Transact\-SQL-Sprachdienst (TSqlLanguageService.msi)  
  
-   Microsoft SQL Server-System-CLR-Typen für SQL Server (SQLSysClrTypes.msi)  
  
-   SQL Server Transact\-SQL ScriptDom (SQLDom.msi)  
  
-   Transact\-SQL-Compilerdienst für SQL Server (SQLLs.msi)  
  
