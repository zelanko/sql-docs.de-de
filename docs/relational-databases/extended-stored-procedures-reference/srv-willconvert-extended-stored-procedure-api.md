---
title: srv_willconvert (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
description: Erfahren Sie, wie srv_willconvert bestimmen, ob eine bestimmte Datentyp Konvertierung innerhalb der ODS-Bibliothek verfügbar ist.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_willconvert
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: ef515b200221a6bb439a65a02e546017046dd0e4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248218"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a>srv_willconvert (API für erweiterte gespeicherte Prozeduren)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Bestimmt, ob eine bestimmte Datentypkonvertierung innerhalb der ODS-Bibliothek verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srctype*  
 Gibt den Datentyp der zu konvertierenden Daten an. Dieser Parameter kann ein beliebiger in der API für erweiterte gespeicherte Prozeduren verfügbarer Datentyp sein.  
  
 *desttype*  
 Gibt den Datentyp an, in den die Quelldaten konvertiert werden. Dieser Parameter kann ein beliebiger in der API für erweiterte gespeicherte Prozeduren verfügbarer Datentyp sein.  
  
## <a name="returns"></a>Rückgabe  
 TRUE, wenn die Datentypkonvertierung unterstützt wird; FALSE, wenn die Datentypkonvertierung nicht unterstützt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Beschreibung der einzelnen Datentypen finden Sie in [Data Types (Extended Stored Procedure API) (Datentypen (API für erweiterte gespeicherte Prozeduren))](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://www.microsoft.com/msrc?rtc=1).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_convert (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-convert-extended-stored-procedure-api.md)  
  
  
