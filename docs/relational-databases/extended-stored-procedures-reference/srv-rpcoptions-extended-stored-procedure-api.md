---
title: srv_rpcoptions (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
description: Erfahren Sie, wie srv_rpcoptions in der API für erweiterte gespeicherte Prozeduren Laufzeitoptionen für die aktuelle remote gespeicherte Prozedur zurückgibt.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcoptions
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d4bd331b54b4bb555fcc6cdbe59155a553332eb
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87332469"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API für erweiterte gespeicherte Prozeduren)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
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
  
## <a name="returns"></a>Rückgabe  
 Eine Bitmap mit den in einer logischen Darstellung ODER für die derzeit remote gespeicherte Prozedur verbundenen Laufzeitflags. Wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird 0 zurückgegeben und eine Meldung generiert.  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle werden die einzelnen Laufzeitflags beschrieben.  
  
|Laufzeitflag|BESCHREIBUNG|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Der Client hat Ergebnisse ohne Metadateninformationen angefordert. Dieses Flag wird nur verwendet, wenn der Client mit einer Instanz von kommuniziert [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Eine Anwendung der API für erweiterte gespeicherte Prozeduren kann Metadateninformationen nicht auslassen.|  
|SRV_RECOMPILE|Der Client hat vor der Ausführung der remote gespeicherten Prozedur eine erneute Kompilierung angefordert. Dieses Flag gilt möglicherweise nicht für eine Anwendung der API für erweiterte gespeicherte Prozeduren.|  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
