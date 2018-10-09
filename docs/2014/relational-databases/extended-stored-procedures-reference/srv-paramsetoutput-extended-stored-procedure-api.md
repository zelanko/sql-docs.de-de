---
title: srv_paramsetoutput (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_paramsetoutput
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bf5e962de42509eab06e2077de19e668efbc754f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212470"
---
# <a name="srvparamsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Legt den Wert eines Rückgabeparameters fest. Diese Funktion setzt die **srv_paramset** -Funktion außer Kraft.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*   
 Ein Handle für eine Clientverbindung.  
  
 *n*  
 Die Ordnungszahl des festzulegenden Parameters. Der erste Parameter ist 1.  
  
 *pbData*  
 Ein Verweis auf den Datenwert, der als ein Prozedurrückgabeparameter an den Client zurückgesendet werden soll.  
  
 *cbLen*  
 Die tatsächliche Länge der zurückzugebenden Daten. Wenn der Datentyp des Parameters Werte einer konstanten Länge angibt und keine NULL-Werte zulässt (z. B. *srvbit* oder *srvint1*), wird *cbLen* ignoriert. Der Wert 0 gibt Daten der Länge 0 (null) an, wenn *fNull* FALSE ist.  
  
 *fNull*  
 Ein Flag, der angibt, ob der Wert des Rückgabeparameters NULL ist. Legen Sie dieses Flag auf TRUE fest, wenn der Parameter auf NULL gesetzt werden soll. Der Standardwert ist FALSE. Wenn *fNull* auf TRUE gesetzt ist, sollte *cbLen* auf 0 gesetzt werden, anderenfalls schlägt die Funktion fehl.  
  
## <a name="returns"></a>Rückgabewert  
 Wenn die Parameterinformationen erfolgreich festgelegt wurden, wird SUCCEED zurückgegeben, andernfalls FAIL. FAIL wird in den folgenden Fällen zurückgegeben:  
  
-   Der Parameter ist kein Rückgabeparameter.  
  
-   Das *cbLen* -Argument ist ungültig.  
  
## <a name="remarks"></a>Hinweise  
 **Sicherheitshinweis** Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren gründlich überprüfen. Außerdem sollten Sie die kompilierten DLLs vor der Installation auf einem Produktionsserver testen. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
