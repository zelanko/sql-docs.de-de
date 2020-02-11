---
title: srv_paramsetoutput (API für erweiterte gespeicherte Prozeduren)
ms.custom: seo-dt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramsetoutput
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
ms.openlocfilehash: 9695f087557abe6c86369e2fddbd5bbd55cf7be5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74119383"
---
# <a name="srv_paramsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
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
  
## <a name="returns"></a>Rückgabe  
 Wenn die Parameterinformationen erfolgreich festgelegt wurden, wird SUCCEED zurückgegeben, andernfalls FAIL. FAIL wird in den folgenden Fällen zurückgegeben:  
  
-   Der Parameter ist kein Rückgabeparameter.  
  
-   Das *cbLen* -Argument ist ungültig.  
  
## <a name="remarks"></a>Bemerkungen  
 **Sicherheitshinweis** Sie sollten den Quellcode erweiterter gespeicherter Prozeduren gründlich überprüfen, und Sie sollten die kompilierten DLLs vor der Installation auf einem Produktionsserver testen. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
