---
title: srv_paramset (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramset
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: f2b4864ac13d431c3507930abc1e774b4ac6adaa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119722"
---
# <a name="srvparamset-extended-stored-procedure-api"></a>srv_paramset (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Legt den Wert eines Aufrufrückgabeparameters für eine remote gespeicherte Prozedur fest. Diese Funktion wurde durch die **srv_paramsetoutput**-Funktion ersetzt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das den Aufruf der remote gespeicherten Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *n*  
 Gibt die Nummer des festzulegenden Parameters an. Der erste Parameter ist 1.  
  
 *data*  
 Ist ein Zeiger auf den Datenwert, der als Rückgabeparameter der remote gespeicherten Prozedur zurück an den Client gesendet werden soll.  
  
 *len*  
 Gibt die tatsächliche Länge der zurückzugebenden Daten an. Wenn der Datentyp des Parameters eine konstante Länge aufweist und keine NULL-Werte zulässt (z.B. *srvbit* oder *srvint1*), wird *len* ignoriert.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED, wenn der Parameterwert erfolgreich festgelegt wurde; andernfalls FAIL. Es wird FAIL zurückgegeben, wenn es keine aktuelle remote gespeicherte Prozedur oder keinen *n*-ten Parameter für die remote gespeicherte Prozedur gibt, oder wenn der Parameter kein Rückgabeparameter oder das *len*-Argument ungültig ist.  
  
 Wenn *len* 0 ist, wird NULL zurückgegeben. *len* auf 0 festzulegen ist die einzige Möglichkeit, NULL an den Client zurückzugeben.  
  
 Diese Funktion gibt die folgenden Werte zurück, wenn der Parameter einem der Datentypen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] entspricht.  
  
|Neue Datentypen|Länge der Rückgabedaten|  
|--------------------|------------------------|  
|**BITN**|**NULL**: _len_ = 0, data = IG, RET = 0<br /><br /> **ZERO:** –<br /><br /> **>=255:** –<br /><br /> **<255:** –|  
|**BIGVARCHAR**|**NULL**: _len_ = 0, data = IG, RET = 1<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = max8k, data = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, data = valid, RET = 1|  
|**BIGCHAR**|**NULL**: _len_ = 0, data = IG, RET = 1<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = max8k, data = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, data = valid, RET = 1|  
|**BIGBINARY**|**NULL**: _len_ = 0, data = IG, RET = 1<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = max8k, data = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, data = valid, RET = 1|  
|**BIGVARBINARY**|**NULL**: _len_ = 0, data = IG, RET = 1<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = max8k, data = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, data = valid, RET = 1|  
|NCHAR|**NULL**: _len_ = 0, data = IG, RET = 1<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = max8k, data = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, data = valid, RET = 1|  
|NVARCHAR|**NULL**: _len_ = 0, data = IG, RET = 1<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = max8k, data = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, data = valid, RET = 1|  
|**NTEXT**|**NULL**: _len_ = IG, data = IG, RET = 0<br /><br /> **ZERO**: _len_ = IG, data = IG, RET = 0<br /><br /> **>=255:** _len_ = IG, data = IG, RET = 0<br /><br /> **\<255:** _len_ = IG, data = IG, RET = 0|  
|RET = Rückgabewert von srv_paramset||  
|IG = Wert wird ignoriert||  
|valid = ein beliebiger gültiger Zeiger auf Daten||  
  
## <a name="remarks"></a>Remarks  
 Parameter enthalten die zwischen Clients und der Anwendung mit remote gespeicherten Prozeduren übergebenen Daten. Der Client kann bestimmte Parameter als Rückgabeparameter angeben. Diese Rückgabeparameter können Werte enthalten, die die Open Data Services-Anwendung wieder an den Client übergibt. Die Verwendung von Rückgabeparametern entspricht der Übergabe von Parametern nach Verweis.  
  
 Sie können den Rückgabewert für einen Parameter nicht festlegen, der nicht als Rückgabeparameter aufgerufen wurde. Verwenden Sie **srv_paramstatus**, um zu bestimmen, wie der Parameter aufgerufen wurde.  
  
 Diese Funktion legt zwar den Rückgabewert für einen Parameter fest, sendet den Rückgabewert jedoch nicht an den Client. Alle Rückgabeparameter werden unabhängig davon, ob die Rückgabewerte mit **srv_paramset** festgelegt wurden, automatisch an den Client gesendet, wenn **srv_senddone** mit dem festgelegtem Statusflag „SRV_DONE_FINAL“ aufgerufen wird.  
  
 Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherten Prozedur einige Parameter über ihren Namen und andere über ihre Position übergeben, so tritt ein Fehler auf. Der SRV_RPC-Handler wird trotzdem aufgerufen, scheinbar jedoch ohne Parameter, und **srv_rpcparams** gibt 0 (null) zurück.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://www.microsoft.com/en-us/msrc?rtc=1).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_paramsetoutput (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
