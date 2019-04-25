---
title: srv_alloc (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8677bb878094bf2345f00b7c6838a43b653faac6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939635"
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Weist dynamisch Arbeitsspeicher zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *size*  
 Legt die Anzahl der zuzuweisenden Bytes fest.  
  
## <a name="returns"></a>Rückgabewert  
 Ein Zeiger auf den neu zugeordneten Speicherplatz. Wenn *size*-Bytes nicht zugeordnet werden können, wird ein NULL-Zeiger zurückgegeben.  
  
## <a name="remarks"></a>Remarks  
 Die **srv_alloc**-Funktion entspricht der **GlobalAlloc**-Funktion der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-API. Normale C-Laufzeitspeicher-Verwaltungsfunktionen der Windows API können in einer Anwendung mit der API für erweiterte gespeicherte Prozeduren verwendet werden.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
