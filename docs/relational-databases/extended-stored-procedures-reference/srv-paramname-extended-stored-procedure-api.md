---
title: srv_paramname (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramname
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
author: rothja
ms.author: jroth
ms.openlocfilehash: f44209b2fb700bf885575f2ed4c0d2c65b82329b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005665"
---
# <a name="srv_paramname-extended-stored-procedure-api"></a>srv_paramname (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt den Namen des Aufrufparameters für eine remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das den Aufruf der remote gespeicherten Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *n*  
 Gibt die Anzahl der Parameter an. Der erste Parameter ist 1.  
  
 *Nest*  
 Stellt einen Zeiger auf eine **int**-Variable bereit, die die Länge des Parameternamens in Byte enthält. Wenn *len* NULL ist, wird die Länge des Parameternamens der remote gespeicherten Prozedur nicht zurückgegeben.  
  
## <a name="returns"></a>Rückgabe  
 Ein Zeiger auf eine auf NULL endende Zeichenfolge, die den Parameternamen enthält. Die Länge des Parameternamens wird in *len* gespeichert. Wenn es keinen *n*-ten Parameter oder keine remote gespeicherte Prozedur gibt, wird NULL zurückgegeben, *len* wird auf –1 festgelegt, und eine Informationsfehlermeldung wird gesendet. Wenn der Parametername gleich NULL ist, wird *len* auf 0 festgelegt, und es wird eine NULL-terminierte leere Zeichenfolge zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion ruft den Namen des Aufrufparameters einer remote gespeicherten Prozedur ab. Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherten Prozedur einige Parameter über ihren Namen und andere über ihre Position übergeben, so tritt ein Fehler auf. Der SRV_RPC-Handler wird trotzdem aufgerufen, scheinbar jedoch ohne Parameter, und **srv_rpcparams** gibt 0 (null) zurück.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_rpcparams (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
