---
title: Komponenten
description: Erfahren Sie mehr über Komponenten der SQL Server Native Client wie sqlncli11.dll, sqlnclir11. rll, sqlncli. h und sqlncli11. lib.
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6908497c7d296c5138b95c0f41d560123b75d943
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462081"
---
# <a name="components-of-sql-server-native-client"></a>Komponenten von SQL Server Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält die folgenden Komponenten:  
  
|Komponente|Beschreibung|  
|---------------|-----------------|  
|sqlncli11.dll|Die DLL-Datei (Dynamic-Link Library, DLL), die die gesamte Funktionalität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält. Dies umfasst auch den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.|  
|sqlnclir11.rll|Die begleitende Ressourcendatei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Bibliothek.|   
|sqlncli.h|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei, die alle neuen, zur Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client erforderlichen Definitionen enthält. Diese Headerdatei ersetzt die Headerdateien odbcss.h und sqloledb.h.<br /><br /> Hinweis: Sie können nicht im selben Programm auf sqlncli. h und odbcss. h verweisen. Sie können jedoch im selben Programm auf sqlncli. h und SQLOLEDB. h verweisen, solange SQLOLEDB. h zuerst definiert wird.|  
|sqlncli11.lib|Die Bibliotheksdatei, die zum direkten Abrufen der **bcp** -Hilfsprogrammfunktionen benötigt wird, die Teil des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treibers sind.<br /><br /> Hinweis: Wenn Sie im Programmiercode auf die Datei sqlncli11. lib verweisen, müssen Sie sicherstellen, dass sich die sqlncli11.dll Datei in Ihrem Systempfad und im Systempfad der Benutzer befindet, die Ihre Anwendung nutzen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
