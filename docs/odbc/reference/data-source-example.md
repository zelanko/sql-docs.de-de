---
title: Datenquellenbeispiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 48c87f0d9f0a48b7d216151178c15bb019c0cbaa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306521"
---
# <a name="data-source-example"></a>Beispiel für Datenquellen
Auf Computernmit Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional oder Microsoft Windows® 95/98 werden Computerdatenquelleninformationen in der Registrierung gespeichert. Je nachdem, unter welchem Registrierungsschlüssel die Informationen gespeichert sind, wird die Datenquelle als *Benutzerdatenquelle* oder *Systemdatenquelle*bezeichnet. Benutzerdatenquellen werden unter dem HKEY_CURRENT_USER-Schlüssel gespeichert und sind nur für den aktuellen Benutzer verfügbar. Systemdatenquellen werden unter dem HKEY_LOCAL_MACHINE-Schlüssel gespeichert und können von mehr als einem Benutzer auf einem Computer verwendet werden. Sie können auch von systemweiten Diensten verwendet werden, die dann auch dann zugriff auf die Datenquelle erhalten, wenn kein Benutzer am Computer angemeldet ist. Weitere Informationen zu Benutzer- und Systemdatenquellen finden Sie unter [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Angenommen, ein Benutzer verfügt über drei Benutzerdatenquellen: Personal und Inventar, die ein Oracle DBMS verwenden; und Payroll, die ein Microsoft SQL Server DBMS verwendet. Die Registrierungswerte für Datenquellen können wie ausfolgenden Werten bestehen:  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 und die Registrierungswerte für die Lohndatenquelle können sein:  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
