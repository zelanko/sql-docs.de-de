---
title: srv_rpcnumber (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
description: Erfahren Sie, wie srv_rpcnumber in der API für erweiterte gespeicherte Prozeduren die Number-Komponente für den aktuellen remote gespeicherten Prozedur-Befehl zurückgibt.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcnumber
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8a58274af4be774698b8fd8b987e7d05c055e3
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87332489"
---
# <a name="srv_rpcnumber-extended-stored-procedure-api"></a>srv_rpcnumber (API für erweiterte gespeicherte Prozeduren)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Nummernkomponente für den derzeit remote gespeicherten Prozeduraufruf zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das die remote gespeicherte Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
## <a name="returns"></a>Gibt zurück  
 Die Nummernkomponente für die derzeit remote gespeicherte Prozedur. Wenn der Client beim Ausführen der remote gespeicherten Prozedur keine Nummernkomponente verwendet oder wenn derzeit keine remote gespeicherte Prozedur vorhanden ist, wird -1 zurückgegegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion gibt nur die Nummernkomponente der remote gespeicherten Prozedur zurück. Sie schließt die optionalen Spezifizierer für den Besitzer, den remote gespeicherten Prozedurnamen und den Datenbanknamen nicht ein.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
