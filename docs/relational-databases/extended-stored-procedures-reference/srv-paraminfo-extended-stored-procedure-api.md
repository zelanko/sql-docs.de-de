---
title: srv_paraminfo (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paraminfo
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: 85efd235861522754cbcdc209d6cf28558907d76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058773"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a>srv_paraminfo (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt Informationen zu einem Parameter zurück. Diese Funktion ersetzt folgende Funktionen: [srv_paramtype](../../relational-databases/extended-stored-procedures-reference/srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](../../relational-databases/extended-stored-procedures-reference/srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](../../relational-databases/extended-stored-procedures-reference/srv-parammaxlen-extended-stored-procedure-api.md) und [srv_paramdata](../../relational-databases/extended-stored-procedures-reference/srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** unterstützt die Datentypen unter [Datentypen](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md) und Daten der Länge 0 (null).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ein Handle für eine Clientverbindung.  
  
 *n*  
 Die Ordnungszahl des festzulegenden Parameters. Der erste Parameter ist 1.  
  
 *pbType*  
 Der Datentyp des Parameters.  
  
 *pcbMaxLen*  
 Zeiger auf die maximale Länge des Parameters.  
  
 *pcbActualLen*  
 Zeiger auf die tatsächliche Länge des Parameters. Der Wert 0 (\* *pcbActualLen* == 0) gibt Daten der Länge 0 (null) an, wenn * *pfNull* auf FALSE festgelegt ist.  
  
 *pbData*  
 Zeiger auf den Puffer für Parameterdaten. Wenn *pbData* nicht NULL ist, schreibt die API für erweiterte gespeicherte Prozeduren \**pcbActualLen*-Datenbytes in \**pbData*. Wenn *pbData* NULL ist, werden keine Daten in \**pbData* geschrieben, die Funktion gibt jedoch \**pbType*, \**pcbMaxLen*, \**pcbActualLen*, und **pfNull* zurück. Der Arbeitsspeicher für diesen Puffer muss von der Anwendung verwaltet werden.  
  
 *pfNull*  
 Zeiger auf ein NULL-Flag. **pfNull* ist auf TRUE festgelegt, wenn der Wert des Parameters NULL ist.  
  
## <a name="returns"></a>Rückgabewert  
 Wenn die Parameterinformationen erfolgreich abgerufen wurden, wird SUCCEED zurückgegeben, andernfalls FAIL. Es wird FAIL zurückgegeben, wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist und wenn kein remote gespeicherter *n*-Prozedurparameter vorhanden ist.  
  
## <a name="remarks"></a>Bemerkungen  
 **Sicherheitshinweis** Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren gründlich überprüfen. Außerdem sollten Sie die kompilierten DLLs vor der Installation auf einem Produktionsserver testen. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierreferenz für erweiterte gespeicherte Prozeduren](../../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
  
  
