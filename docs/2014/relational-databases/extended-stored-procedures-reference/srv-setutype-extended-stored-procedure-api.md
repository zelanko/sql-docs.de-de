---
title: srv_setutype (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b5f1b038d574da6e04fa934d4f4c599966341a7c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217396"
---
# <a name="srvsetutype-extended-stored-procedure-api"></a>srv_setutype (API für erweiterte gespeicherte Prozeduren)
    
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
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL. Wenn die Spalte nicht vorhanden ist, wird FAIL zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Eine Spalte verfügt über zwei Datentypen: ihren tatsächlichen Datentyp und ihren benutzerdefinierten Datentyp. Der benutzerdefinierte Datentyp wird von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, um, falls vorhanden, den tatsächlichen benutzerdefinierten Datentyp der Spalte sowie Spaltenbeschreibungsinformationen wie NULL-Zulässigkeit und Aktualisierbarkeit der Spalte zu speichern.  
  
 Die **srv_setutype** -Funktion kann jedes Mal aufgerufen werden, wenn *column* mit **srv_describe** definiert ist, und bevor die letzte Zeile gesendet wurde.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Siehe auch  
 [srv_describe (API für erweiterte gespeicherte Prozeduren)](srv-describe-extended-stored-procedure-api.md)  
  
  
