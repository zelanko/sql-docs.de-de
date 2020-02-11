---
title: Löschen einer Datenquelle (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff882caf0ce5d9ef7d2e9f059daed89ed4b50d82
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63126103"
---
# <a name="delete-a-data-source-odbc"></a>Löschen einer Datenquelle (ODBC)
  Sie können eine Datenquelle auf folgende Arten löschen: mithilfe des ODBC-Administrators, programmgesteuert (mit [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) oder durch Löschen einer Datei (bei einem Dateiquellennamen).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>So löschen Sie eine Datenquelle mit dem ODBC-Administrator  
  
1.  Öffnen Sie in der **Systemsteuerung**die Option **Verwaltung**, und doppelklicken Sie dann auf **Datenquellen (ODBC)**. Stattdessen können Sie auch odbcad32.exe über die Eingabeaufforderung ausführen:  
  
2.  Klicken Sie auf die Registerkarte **Benutzer-DSN**, **System-DSN**oder **Datei-DSN** .  
  
3.  Klicken Sie auf die zu löschende Datenquelle.  
  
4.  Klicken Sie auf **Entfernen**, und bestätigen Sie dann das Löschen.  
  
## <a name="example"></a>Beispiel  
 Rufen Sie [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) entweder mit ODBC_REMOVE_DSN oder mit ODBC_REMOVE_SYS_DSN als zweitem Parameter auf, um eine Datenquelle programmgesteuert zu löschen.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie eine Datenquelle programmgesteuert löschen können.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
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
 [Themen zur Vorgehensweise: Konfigurieren des SQL Server-ODBC-Treibers](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
