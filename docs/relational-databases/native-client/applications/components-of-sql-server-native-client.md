---
title: Komponenten
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c824d145b6353f96a3756f28b7446799b303889
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388217"
---
# <a name="components-of-sql-server-native-client"></a>Komponenten von SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält die folgenden Komponenten:  
  
|Komponente|BESCHREIBUNG|  
|---------------|-----------------|  
|sqlncli11.dll|Die DLL-Datei (Dynamic-Link Library, DLL), die die gesamte Funktionalität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält. Dies umfasst auch den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.|  
|sqlnclir11.rll|Die begleitende Ressourcendatei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Bibliothek.|   
|sqlncli.h|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei, die alle neuen, zur Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client erforderlichen Definitionen enthält. Diese Headerdatei ersetzt die Headerdateien odbcss.h und sqloledb.h.<br /><br /> Hinweis: Sie können sqlncli.h und odbcss.h nicht im selben Programm referenzieren, aber Sie können sqlncli.h und sqloledb.h im selben Programm referenzieren, solange sqloledb.h zuerst definiert ist.|  
|sqlncli11.lib|Die Bibliotheksdatei, die zum direkten Aufrufen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **bcp-Dienstprogrammfunktionen** erforderlich ist, die Teil des Native Client ODBC-Treibers sind.<br /><br /> Hinweis: Wenn Sie auf die Datei sqlncli11.lib in Ihrem Programmiercode verweisen, müssen Sie sicherstellen, dass sich die Datei sqlncli11.dll im Systempfad und im Systempfad der Benutzer befindet, die Ihre Anwendung verwenden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
