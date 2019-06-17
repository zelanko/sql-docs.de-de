---
title: Komponenten von SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 329ffa78471ead02b1431a41d898cfc43ca65684
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213513"
---
# <a name="components-of-sql-server-native-client"></a>Komponenten von SQL Server Native Client
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält die folgenden Komponenten:  
  
|Komponente|Description|  
|---------------|-----------------|  
|sqlncli11.dll|Die DLL-Datei (Dynamic-Link Library, DLL), die die gesamte Funktionalität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält. Dies umfasst auch den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.|  
|sqlnclir11.rll|Die begleitende Ressourcendatei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Bibliothek.|  
|s10ch_sqlncli.chm|Die Hilfedatei des Datenquellen-Assistenten, in der dokumentiert wird, wie Sie eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenquelle unter Verwendung des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers oder des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters erstellen.|  
|sqlncli.h|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei, die alle neuen, zur Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client erforderlichen Definitionen enthält. Diese Headerdatei ersetzt die Headerdateien odbcss.h und sqloledb.h. **Hinweis**:  Sie können nicht auf sqlncli.h und odbcss.h im selben Programm verweisen, aber Sie können sqlncli.h und sqloledb.h im selben Programm verweisen, solange sqloledb.h zuerst definiert wird.|  
|sqlncli11.lib|Die Bibliotheksdatei, die für den direkten Aufruf erforderlich sind die **Bcp** Hilfsfunktionen, die Teil der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber. **Hinweis**:  Wenn Sie in Ihrem Programmcode die Datei sqlncli11.lib verweisen, müssen Sie sicherstellen, dass die Datei sqlncli11.dll ist in Ihrem Systempfad sowie im Systempfad der Benutzer, die Stellen der Anwendung verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
