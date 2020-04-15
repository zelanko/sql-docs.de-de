---
title: Löschen einer Datenquelle (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 93ea12968c92f7849876d29d31207b8028714482
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294527"
---
# <a name="configuring-the-sql-server-odbc-driver---delete-a-data-source"></a>Konfigurieren des SQL Server-ODBC-Treibers: Löschen einer Datenquelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bevor Sie ODBC-Anwendungen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher verwenden können, müssen Sie wissen, wie Sie die Katalogversion der gespeicherten Prozeduren aus älteren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren und Datenquellen hinzufügen, löschen und testen.  
  
  Sie können eine Datenquelle auf folgende Arten löschen: mithilfe des ODBC-Administrators, programmgesteuert (mit [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)) oder durch Löschen einer Datei (bei einem Dateiquellennamen).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>So löschen Sie eine Datenquelle mit dem ODBC-Administrator  
  
1.  Öffnen Sie in **der Systemsteuerung** **administrative Tools**, und doppelklicken Sie dann entweder auf **ODBC-Datenquellen (64-Bit)** oder **ODBC-Datenquellen (32-Bit).** Stattdessen können Sie auch odbcad32.exe über die Eingabeaufforderung ausführen:  
  
2.  Klicken Sie auf die Registerkarte **Benutzer-DSN**, **System-DSN**oder **Datei-DSN** .  
  
3.  Wählen Sie die zu löschende Datenquelle aus.  
  
4.  Klicken Sie auf **Entfernen**, und bestätigen Sie dann das Löschen.  

## <a name="example"></a>Beispiel  
 Rufen Sie [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) entweder mit ODBC_REMOVE_DSN oder mit ODBC_REMOVE_SYS_DSN als zweitem Parameter auf, um eine Datenquelle programmgesteuert zu löschen.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie eine Datenquelle programmgesteuert löschen können.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include \<windows.h>  
#include \<odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen einer Datenquelle &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-add-a-data-source.md)  
  
  
