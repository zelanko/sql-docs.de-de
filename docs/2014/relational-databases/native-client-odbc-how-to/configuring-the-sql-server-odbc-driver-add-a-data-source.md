---
title: Hinzufügen einer Datenquelle (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e8d3c51595caa5a65f5ac175bdf16a4333511b5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431999"
---
# <a name="add-a-data-source-odbc"></a>Hinzufügen einer Datenquelle (ODBC)
  Sie können eine Datenquelle hinzufügen, indem Sie mithilfe des ODBC-Administrators, programmgesteuert (mit [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), oder erstellen eine Datei.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>So fügen Sie eine Datenquelle mit dem ODBC-Administrator hinzu  
  
1.  Von der **Systemsteuerung**, Zugriff **Verwaltung** und dann **Datenquellen (ODBC)**. Alternativ können Sie odbcad32.exe aufrufen.  
  
2.  Klicken Sie auf die Registerkarte **Benutzer-DSN**, **System-DSN**oder **Datei-DSN** , und klicken Sie dann auf **Hinzufügen**.  
  
3.  Klicken Sie auf **SQL Server**und dann auf **Fertig stellen**.  
  
4.  Führen Sie die Schritte im SQL Server-Assistenten zum Erstellen einer neuen Datenquelle aus.  
  
### <a name="to-add-a-data-source-programmatically"></a>So fügen Sie eine Datenquellen programmgesteuert hinzu  
  
1.  Rufen Sie [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) mit auf entweder ODBC_ADD_DSN oder ODBC_ADD_SYS_DSN festgelegtem zweiten Parameter.  
  
### <a name="to-add-a-file-data-source"></a>So fügen Sie eine Dateidatenquelle hinzu  
  
1.  Rufen Sie [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) mit einem SAVEFILE = File_name-Parameter in der Verbindungszeichenfolge. Wenn die Verbindung erfolgreich ist, erstellt der ODBC-Treiber eine Dateidatenquelle mit den Verbindungsparametern an dem Speicherort, auf den der SAVEFILE-Parameter zeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Themen zur Vorgehensweise: Konfigurieren des SQL Server-ODBC-Treibers](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
