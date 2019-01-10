---
title: srv_rpcparams (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcparams
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 83f1368984737759eb64a5feaf31bd1ac7c79e37
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371102"
---
# <a name="srvrpcparams-extended-stored-procedure-api"></a>srv_rpcparams (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Anzahl von Parametern für die derzeit remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*   
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das die remote gespeicherte Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
## <a name="returns"></a>Rückgabewert  
 Die Anzahl von Parametern in der remote gespeicherten Prozedur. Wenn die remote gespeicherte Prozedur keine Parameter enthält oder keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird -1 zurückgegeben und ein Informationsfehler angezeigt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt die Anzahl von Parametern in der aktuellen remote gespeicherten Prozedur zurück. Sie wird normalerweise von der remote gespeicherten Prozedur aufgerufen.  
  
 Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherte Prozedur einige Parameter mit ihrem Namen und einige mit ihrer Position übergeben, so tritt ein Fehler auf. In diesem Fall wird der Handler der remote gespeicherten Prozedur aufgerufen, aber es werden keine remote gespeicherten Prozeduren empfangen, und **srv_rpcparams** gibt 0 zurück.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
