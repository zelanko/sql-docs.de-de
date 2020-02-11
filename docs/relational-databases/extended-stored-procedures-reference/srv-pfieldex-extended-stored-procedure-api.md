---
title: srv_pfieldex (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_pfieldex
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1333cfc819b8027260c715ed3398c0099f96a854
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005555"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a>srv_pfieldex (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt einen Zeiger auf Daten zurück, die das angeforderte SRV_PROC-Feld enthalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *Flächen*  
 Gibt das zurückzugebende *srvproc*-Feld an  
  
|Feld|BESCHREIBUNG|Rückgabetyp|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|Aktuelle Sitzungsmeldung-LCID|ULONG*|  
|SRV_INSTANCENAME|Instanzname (wenn genannt); gibt andernfalls NULL zurück|WCHAR*|  
  
 *Nest*  
 Ein Zeiger auf eine **int**-Variable, die die Länge des zurückgegebenen *field*-Werts in Byte enthält. Wenn *len* NULL ist, wird die Länge nicht zurückgegeben. Wenn NULL zurückgegeben wird, wird **len* auf 0 (null) festgelegt.  
  
## <a name="returns"></a>Rückgabe  
 Ein Zeiger auf Daten, deren Typ von *field* abhängt. NULL wird zurückgegeben, wenn *len* oder *srvproc* NULL ist. Ist *field* unbekannt, wird NULL zurückgegeben. Wenn NULL zurückgegeben wird, wird **len* auf 0 (null) festgelegt.  
  
> [!IMPORTANT]  
>  Der vom Server zurückgegebene Puffer sollte schreibgeschützt sein. Andernfalls ist der Serverstatus möglicherweise beschädigt.  
  
## <a name="remarks"></a>Bemerkungen  
 **Sicherheitshinweis** Sie sollten den Quellcode erweiterter gespeicherter Prozeduren gründlich überprüfen, und Sie sollten die kompilierten DLLs vor der Installation auf einem Produktionsserver testen. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
