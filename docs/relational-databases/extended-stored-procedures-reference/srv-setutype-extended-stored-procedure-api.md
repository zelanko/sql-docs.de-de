---
title: srv_setutype (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
description: Erfahren Sie mehr über srv_setutype. srv_setutype legt den benutzerdefinierten Datentyp für eine Spalte in einer Zeile fest.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setutype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ecdbaef663059146f3ca6bd4a88305e12d4f495
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248189"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a>srv_setutype (API für erweiterte gespeicherte Prozeduren)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Legt den benutzerdefinierten Datentyp für eine Spalte in einer Zeile fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *column*  
 Gibt an, welche Spalte festgelegt werden soll. Die Spalten sind fortlaufend nummeriert, beginnend mit 1.  
  
 *user_type*  
 Gibt den benutzerdefinierten Datentypcode an.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED oder FAIL. Wenn die Spalte nicht vorhanden ist, wird FAIL zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Spalte verfügt über zwei Datentypen: ihren tatsächlichen Datentyp und ihren benutzerdefinierten Datentyp. Der benutzerdefinierte Datentyp wird von verwendet, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um den tatsächlichen benutzerdefinierten Datentyp der Spalte, sofern vorhanden, und Spalten Beschreibungs Informationen (z. b. NULL-Zulässigkeit und Aktualisierbarkeit) für die Spalte zu speichern.  
  
 Die **srv_setutype** -Funktion kann jedes Mal aufgerufen werden, wenn *column* mit **srv_describe** definiert ist, und bevor die letzte Zeile gesendet wurde.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://www.microsoft.com/msrc?rtc=1).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_describe (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
