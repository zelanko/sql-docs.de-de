---
title: srv_rpcoptions (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
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
ms.openlocfilehash: 0c97262ab6b3ee42b070511a813fcb4498b78d60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62745819"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
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
  
## <a name="returns"></a>Rückgabe  
 Eine Bitmap mit den in einer logischen Darstellung ODER für die derzeit remote gespeicherte Prozedur verbundenen Laufzeitflags. Wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird 0 zurückgegeben und eine Meldung generiert.  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle werden die einzelnen Laufzeitflags beschrieben.  
  
|Laufzeitflag|BESCHREIBUNG|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Der Client hat Ergebnisse ohne Metadateninformationen angefordert. Dieses Flag wird nur verwendet, wenn der Client mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kommuniziert. Eine Anwendung der API für erweiterte gespeicherte Prozeduren kann Metadateninformationen nicht auslassen.|  
|SRV_RECOMPILE|Der Client hat vor der Ausführung der remote gespeicherten Prozedur eine erneute Kompilierung angefordert. Dieses Flag gilt möglicherweise nicht für eine Anwendung der API für erweiterte gespeicherte Prozeduren.|  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
