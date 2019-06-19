---
title: Datenquellen-Beispiel | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f427074f7cd7153f448aaef43bc4ac5dca84c01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186311"
---
# <a name="data-source-example"></a>Beispiel für Datenquellen
Auf Computern unter Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional oder Microsoft Windows® 95/98, Computerdaten ist Quellinformationen in der Registrierung gespeichert. Je nach der Registrierung Schlüssel die Informationen in einem gespeichert ist, wird die Datenquelle als bezeichnet ein *Benutzerdatenquelle* oder *Systemdatenquelle*. Benutzer-Datenquellen werden unter dem Schlüssel HKEY_CURRENT_USER gespeichert und sind nur für den aktuellen Benutzer verfügbar. System-Datenquellen werden unter dem Schlüssel HKEY_LOCAL_MACHINE gespeichert und können von mehr als ein Benutzer auf einem Computer verwendet werden. Sie können auch von systemweiten Services verwendet die klicken Sie dann die Datenquelle zugreifen können, auch wenn kein Benutzer mit dem Computer angemeldet ist. Weitere Informationen zu Benutzer- und Systemdatenquellen finden Sie unter [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Nehmen wir an, dass ein Benutzer verfügt über drei Benutzerdatenquellen: Mitarbeiter und Inventar, die eine Oracle-DBMS zu verwenden; und Gehaltsabrechnungen, das eine Microsoft SQL Server-DBMS verwendet. Die Registrierungswerte für Datenquellen können Folgendes sein:  
  
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
  
 und die Registrierungswerte für die Datenquelle für Gehaltsabrechnungen möglicherweise:  
  
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
