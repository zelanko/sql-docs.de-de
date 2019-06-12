---
title: Sqlsrv_configure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ae32c7693b724deec25c8d923e02cdf929e893ef
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796980"
---
# <a name="sqlsrvconfigure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ändert die Einstellungen für die Fehlerbehandlung und Protokollierungsoptionen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>Parameter  
*$setting*: Name der zu konfigurierenden Einstellung. Siehe Tabelle unten für eine Liste der Einstellungen.  
  
*$value*: Wert, der der Einstellung hinzugefügt werden soll, die im *$setting* Parameter angegeben ist. Die möglichen Werte für diesen Parameter hängen von der angegebenen Einstellung ab. In der folgenden Tabelle sind die Kombinationsmöglichkeiten aufgelistet:  
  
|Einstellung|Mögliche Werte für $value-Parameter (entsprechende Ganzzahl in Klammern)|Standardwert|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|Eine nicht negative Zahl, bis hin zur PHP-Speichergrenze.<br /><br />0 (null) und negative Zahlen sind nicht zulässig.|10240 KB|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF(0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF(0)|  
|WarningsReturnAsErrors<sup>3</sup>|**true** (1) oder **false** (0)|**TRUE** (1)|  
  
## <a name="return-value"></a>Rückgabewert  
Wenn **sqlsrv_configure** mit nicht unterstützten Einstellungen oder Werten aufgerufen wird, gibt die Funktion **false**zurück. Andernfalls gibt die Funktion **true**zurück.  
  
## <a name="remarks"></a>Remarks  
(1) Weitere Informationen zu clientseitigen Abfragen finden Sie unter [Cursortypen &#40;SQLSRV-Treiber&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
(2) Weitere Informationen zur Protokollierung von Aktivitäten finden Sie unter [Protokollieren von Aktivitäten](../../connect/php/logging-activity.md).  
  
(3) Weitere Informationen zum Konfigurieren der Fehler- und Warnungsbehandlung finden Sie unter [Gewusst wie: Konfigurieren der Behandlung von Fehlern und Warnungen unter Verwendung des SQLSRV-Treibers](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[Programmierhandbuch für den Microsoft-Treiber für PHP für SQLServer](../../connect/php/programming-guide-for-php-sql-driver.md) 
  
