---
title: Hinzufügen einer Datenquelle (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 784c08ea9a251587d156de9f2d209308c6fda5e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73781689"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Konfigurieren des SQL Server-ODBC-Treibers: Hinzufügen einer Datenquelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bevor Sie ODBC-Anwendungen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher verwenden können, müssen Sie wissen, wie Sie die Katalogversion der gespeicherten Prozeduren aus älteren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren und Datenquellen hinzufügen, löschen und testen.  
  
  Sie können eine Datenquelle auf folgende Arten hinzufügen: mithilfe des ODBC-Administrators, programmgesteuert (mit [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)) oder durch das Erstellen einer Datei.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>So fügen Sie eine Datenquelle mit dem ODBC-Administrator hinzu  
  
1.  Greifen Sie in der **Systemsteuerung**auf **Verwaltung** und dann auf **ODBC-Datenquellen (64-Bit)** oder **ODBC-Datenquellen (32 Bit)** zu. Alternativ können Sie odbcad32.exe aufrufen.  
  
2.  Klicken Sie auf die Registerkarte **Benutzer-DSN**, **System-DSN**oder **Datei-DSN** , und klicken Sie dann auf **Hinzufügen**.  
  
3.  Klicken Sie auf **SQL Server**und dann auf **Fertig stellen**.  
  
4.  Führen Sie die Schritte im Assistenten **zum Erstellen einer neuen Datenquelle in SQL Server** aus.  
  
### <a name="to-add-a-data-source-programmatically"></a>So fügen Sie eine Datenquellen programmgesteuert hinzu  
  
1.  Rufen Sie [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) mit auf entweder ODBC_ADD_DSN oder ODBC_ADD_SYS_DSN festgelegtem zweiten Parameter auf.  
  
### <a name="to-add-a-file-data-source"></a>So fügen Sie eine Dateidatenquelle hinzu  
  
1.  Rufen Sie [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) mit einem SAVEFILE=file_name-Parameter in der Verbindungszeichenfolge auf. Wenn die Verbindung erfolgreich ist, erstellt der ODBC-Treiber eine Dateidatenquelle mit den Verbindungsparametern an dem Speicherort, auf den der SAVEFILE-Parameter zeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Löschen einer Datenquelle &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
