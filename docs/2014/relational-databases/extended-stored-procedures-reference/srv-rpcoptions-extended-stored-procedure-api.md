---
title: srv_rpcoptions (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 97a30b223df8420ba67aef21d9b7837b2d4e5557
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905913"
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Laufzeitoptionen für die derzeit remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*   
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das die remote gespeicherte Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
## <a name="returns"></a>Rückgabewert  
 Eine Bitmap mit den in einer logischen Darstellung ODER für die derzeit remote gespeicherte Prozedur verbundenen Laufzeitflags. Wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird 0 zurückgegeben und eine Meldung generiert.  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle werden die einzelnen Laufzeitflags beschrieben.  
  
|Laufzeitflag|Description|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Der Client hat Ergebnisse ohne Metadateninformationen angefordert. Dieses Flag wird nur verwendet, wenn der Client mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kommuniziert. Eine Anwendung der API für erweiterte gespeicherte Prozeduren kann Metadateninformationen nicht auslassen.|  
|SRV_RECOMPILE|Der Client hat vor der Ausführung der remote gespeicherten Prozedur eine erneute Kompilierung angefordert. Dieses Flag gilt möglicherweise nicht für eine Anwendung der API für erweiterte gespeicherte Prozeduren.|  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
