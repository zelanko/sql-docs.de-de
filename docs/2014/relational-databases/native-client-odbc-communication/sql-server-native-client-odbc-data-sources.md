---
title: SQL Server Native Client ODBC-Datenquellen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b74f989db617c2fcd86e0d823b9bb563c7dcda1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050751"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>SQL Server Native Client ODBC-Datenquellen
  Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquellenname (DSN) identifiziert eine ODBC-Datenquelle, die alle Informationen enthält, die eine ODBC-Anwendung zur Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank auf einem bestimmten Server benötigt. Es gibt zwei Methoden, wie Sie einen ODBC-Datenquellennamen definieren können:  
  
-   Klicken Sie auf einem Clientcomputer Verwaltung in der Systemsteuerung öffnen, und doppelklicken Sie auf **Datenquellen (ODBC)**. Daraufhin wird der ODBC-Datenquellen-Administrator geöffnet, mit dem Sie einen DSN erstellen können.  
  
-   Rufen Sie in einer ODBC-Anwendung [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).  
  
 Eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle enthält Folgendes:  
  
-   Den Namen der Datenquelle.  
  
-   Informationen, die zur Verbindung mit einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigt werden.  
  
-   Die Standarddatenbank, die auf einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden soll (optional).  
  
-   Einstellungen, z. B. welche ANSI-Optionen verwendet werden, ob Leistungsstatistiken protokolliert werden (optional) usw.  
  
 Eine ODBC-Anwendung muss nicht unbedingt über eine Datenquelle eine Verbindung herstellen. Die Anwendung muss jedoch dieselben Verbindungsinformationen an die ODBC-Verbindungsfunktion liefern, die der Treiber andernfalls im DSN finden würde.  
  
## <a name="see-also"></a>Siehe auch  
 [Bei der Kommunikation mit SQLServer &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  