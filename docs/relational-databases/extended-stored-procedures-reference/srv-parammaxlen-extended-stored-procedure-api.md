---
title: srv_parammaxlen (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_parammaxlen
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: 8dfa779a664d398a6fb619bf17bf67bb52ab1bb0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005709"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a>srv_parammaxlen (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die maximale Datenlänge des Aufrufparameters für eine remote gespeicherte Prozedur zurück. Diese Funktion wurde durch die **srv_paraminfo**-Funktion ersetzt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das den Aufruf der remote gespeicherten Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *n*  
 Gibt die Anzahl der Parameter an. Der erste Parameter ist 1.  
  
## <a name="returns"></a>Rückgabe  
 Die maximale Länge der Parameterdaten in Byte. Wenn es keinen *n*-ten Parameter oder keine remote gespeicherte Prozedur gibt, wird -1 zurückgegeben.  
  
 Diese Funktion gibt die folgenden Werte zurück, wenn der-Parameter einem der folgenden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen entspricht.  
  
|Neue Datentypen|Länge der Eingabedaten|  
|--------------------|-----------------------|  
|**BITN**|**Null:** 1<br /><br /> **Null:** 1<br /><br /> **>= 255:** nicht zutreffend<br /><br /> **<255:** nicht zutreffend|  
|**BIGVARCHAR**|**Null:** 255<br /><br /> **Null:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGCHAR**|**Null:** 255<br /><br /> **Null:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGBINARY**|**Null:** 255<br /><br /> **Null:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGVARBINARY**|**Null:** 255<br /><br /> **Null:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NCHAR**|**Null:** 255<br /><br /> **Null:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NVARCHAR**|**Null:** 255<br /><br /> **Null:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NTEXT**|**Null:** -1<br /><br /> **Null:** -1<br /><br /> **>= 255:** -1<br /><br /> 255:-1 ** \<**|  
  
## <a name="remarks"></a>Bemerkungen  
 Parameter einer remote gespeicherten Prozedur haben eine tatsächliche und eine maximale Datenlänge. Bei Standarddatentypen fester Länge, die keine Nullwerte zulassen, ist die tatsächliche Länge mit der maximalen Länge identisch. Bei Datentypen variabler Länge können die Längen unterschiedlich sein. Ein als **varchar(30)** deklarierter Parameter kann beispielsweise über Daten verfügen, die nur 10 Byte lang sind. Die tatsächliche Länge des Parameters ist 10, die maximale Länge jedoch 30. Die Funktion **srv_parammaxlen** ruft die maximale Datenlänge einer remote gespeicherten Prozedur ab. Zum Abrufen der tatsächlichen Datenlänge eines Parameters verwenden Sie **srv_paramlen**.  
  
 Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherten Prozedur einige Parameter über ihren Namen und andere über ihre Position übergeben, so tritt ein Fehler auf. Der SRV_RPC Handler wird weiterhin aufgerufen, wird jedoch so angezeigt, als ob keine Parameter vorhanden wären und **srv_rpcparams** 0 zurückgibt.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_paraminfo &#40;API für erweiterte gespeicherte Prozeduren&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams &#40;API für erweiterte gespeicherte Prozeduren&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
