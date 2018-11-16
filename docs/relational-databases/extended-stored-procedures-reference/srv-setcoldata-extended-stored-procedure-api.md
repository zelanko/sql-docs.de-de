---
title: srv_setcoldata (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setcoldata
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cfb3c62f5b0e5f24c84f02e3eba7a9eebb7977fe
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663189"
---
# <a name="srvsetcoldata-extended-stored-procedure-api"></a>srv_setcoldata (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die aktuelle Adresse für die Daten einer Spalte an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc *  
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *column*  
 Gibt die Nummer der Spalte an, für die die Adresse angegeben wird. Die Spalten sind fortlaufend nummeriert, beginnend mit 1.  
  
 *data*  
 Ist ein Zeiger für die Daten einer Spalte. Der *data* zugewiesene Speicher sollte erst freigegeben werden, wenn die Spaltendaten durch einen anderen Aufruf von **srv_setcoldata**ersetzt wurden oder wenn **srv_senddone** aufgerufen wird.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Remarks  
 Jede Spalte der Zeile muss zuerst mit **srv_describe**definiert werden. Spaltendatenadressen werden anfänglich mit **srv_describe**festgelegt. Wenn sich die Adresse der Spaltendaten ändert, muss **srv_setcoldata** aufgerufen werden, um die neue Adresse der Daten anzugeben. Für jede geänderte Spalte muss **srv_setcoldata** separat aufgerufen werden.  
  
 NULL-Daten werden dargestellt, indem die Länge der Spalte mit **srv_setcollen**auf 0 festgelegt wird. Die Datenadresse wird dann ignoriert.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [srv_describe (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
