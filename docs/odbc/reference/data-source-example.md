---
title: Datenquellen Beispiel | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306521"
---
# <a name="data-source-example"></a>Beispiel für Datenquellen
Auf Computern, auf denen Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional oder Microsoft Windows® 95/98 ausgeführt wird, werden Informationen zur Computer Datenquelle in der Registrierung gespeichert. Abhängig von dem Registrierungsschlüssel, unter dem die Informationen gespeichert werden, wird die Datenquelle als *Benutzerdaten Quelle* oder als *Systemdaten Quelle*bezeichnet. Benutzerdaten Quellen werden unter dem HKEY_CURRENT_USER Schlüssel gespeichert und sind nur für den aktuellen Benutzer verfügbar. System Datenquellen werden unter dem HKEY_LOCAL_MACHINE Schlüssel gespeichert und können von mehreren Benutzern auf einem Computer verwendet werden. Sie können auch von systemweiten Diensten verwendet werden, die dann Zugriff auf die Datenquelle erhalten können, auch wenn kein Benutzer am Computer angemeldet ist. Weitere Informationen zu Benutzer-und Systemdaten Quellen finden Sie unter [sqlmanagedatasources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Angenommen, ein Benutzer verfügt über drei Benutzerdaten Quellen: Personal und Inventory, die ein Oracle-DBMS verwenden. und Gehaltsabrechnung, bei dem ein Microsoft SQL Server DBMS verwendet wird. Die Registrierungs Werte für Datenquellen können wie folgt lauten:  
  
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
  
 die Registrierungs Werte für die Datenquelle für die Abrechnung können wie folgt lauten:  
  
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
