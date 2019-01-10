---
title: srv_rpcdb (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7eb462881ab9ae5d6221498a84fc2b79e0524bc9
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369462"
---
# <a name="srvrpcdb-extended-stored-procedure-api"></a>srv_rpcdb (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Datenbanknamenskomponente für die derzeit remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*   
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *len*  
 Ist ein Zeiger auf eine `int`-Variable, die die Länge des Datenbanknamens empfängt. Wenn *len* NULL ist, wird die Länge des Datenbanknamens nicht zurückgegeben.  
  
## <a name="returns"></a>Rückgabewert  
 Ein DBCHAR-Zeiger auf die NULL-terminierte Zeichenfolge für den Datenbanknamensteil der aktuellen remote gespeicherten Prozedur. Wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird NULL zurückgegeben, und der *len*-Parameter wird auf –1 gesetzt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt nur die Datenbankkomponente des Objektnamens der remote gespeicherten Prozedur zurück. Sie schließt die optionalen Spezifizierer für Besitzer, den remote gespeicherten Prozedurnamen und die Nummer der remote gespeicherten Prozedur nicht ein.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
