---
title: Database Mail XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: f350a5027957acba7e9e8689b8650bb545368030
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66767921"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs (Serverkonfigurationsoption)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Verwenden Sie die Option **DatabaseMail XPs** , um Datenbank-E-Mail auf diesem Server zu aktivieren. Die folgenden Werte sind möglich:  
  
- `0`: Datenbank-E-Mail ist nicht verfügbar (Standard).  
  
- `1`: Datenbank-E-Mail ist verfügbar.  
  
 Die Einstellung tritt ohne Beenden und Neustarten des Servers sofort in Kraft.  
  
 Nachdem Sie Datenbank-E-Mail aktiviert haben, müssen Sie zum Verwenden von Datenbank-E-Mail eine Hostdatenbank für Datenbank-E-Mail konfigurieren.  
  
 Durch das Konfigurieren von Datenbank-E-Mail mithilfe des **Assistenten zum Konfigurieren von Datenbank-E-Mail** werden die erweiterten gespeicherten Prozeduren von Datenbank-E-Mail in der `msdb`-Datenbank aktiviert. Wenn Sie den **Assistenten zum Konfigurieren von Datenbank-E-Mail**verwenden, müssen Sie das unten angeführte `sp_configure`-Beispiel nicht verwenden.  
  
 Das Festlegen der Option **Database Mail XPs** auf `0` verhindert das Starten von Datenbank-E-Mail. Wird Datenbank-E-Mail mit dem Wert `0` ausgeführt, wird die Ausführung und das Senden von E-Mails bis zur in der Option `DatabaseMailExeMinimumLifeTime` konfigurierten Leerlaufzeit fortgesetzt.  
  
## <a name="examples"></a>Beispiele
 Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren von Datenbank-E-Mail aktiviert.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  

Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren von Datenbank-E-Mail aktiviert, falls noch nicht geschehen.

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>Weitere Informationen
[Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
