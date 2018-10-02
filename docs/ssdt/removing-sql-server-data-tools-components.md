---
title: Entfernen von SQL Server Data Tools-Komponenten | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b114b99b816e10bc004cea8d60c56d296053c7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685468"
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
  
