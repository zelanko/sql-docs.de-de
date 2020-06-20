---
title: srv_rpcowner (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcowner
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
ms.openlocfilehash: b589d55c8e30e3882ebb25bc46c51bc382e3e2df
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050575"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a>srv_rpcowner (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Besitzerkomponente für die derzeit remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das die remote gespeicherte Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *Nest*  
 Ist ein Zeiger auf eine ganzzahlige Variable, die die Länge des Besitzernamens empfängt. Der Parameter *len* kann NULL sein. In diesem Fall wird die Länge der Besitzerkomponente nicht zurückgegeben.  
  
## <a name="returns"></a>Gibt zurück  
 Ein DBCHAR-Zeiger auf die NULL-terminierte Besitzerkomponente für die aktuelle remote gespeicherte Prozedur. Wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird NULL zurückgegeben, und *len* wird auf –1 festgelegt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt nur die Besitzerkomponente der remote gespeicherten Prozedur zurück. Nicht eingeschlossen sind die optionalen Spezifizierer für Name sowie Name und Nummer der remote gespeicherten Prozedur.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
