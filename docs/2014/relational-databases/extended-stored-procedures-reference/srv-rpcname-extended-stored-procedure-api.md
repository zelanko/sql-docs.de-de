---
title: srv_rpcname (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab357fd57d16f822d9490f52d2e57852bf7f8bb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058708"
---
# <a name="srvrpcname-extended-stored-procedure-api"></a>srv_rpcname (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Prozedurnamenskomponente für die derzeit remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBCHAR * srv_rpcname (  
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
  
 *len*  
 Ist ein Zeiger auf eine ganzzahlige Variable, die die Länge des Datenbanknamens empfängt. Wenn *len* NULL ist, wird die Länge des Namens der remote gespeicherten Prozedur nicht zurückgegeben.  
  
## <a name="returns"></a>Rückgabewert  
 Ein DBCHAR-Zeiger auf die NULL-terminierte Zeichenfolge für die Prozedurnamenskomponente der aktuellen remote gespeicherten Prozedur. Wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist, wird NULL zurückgegeben, und *len* wird auf -1 festgelegt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt nur den Namen der remote gespeicherten Prozedur zurück. Sie schließt die optionalen Spezifizierer für Besitzer, Datenbanknamen und Name der remote gespeicherten Prozedur nicht ein.  
  
 Weil ein Aufruf von **srv_rpcname** auch zulässig ist, wenn keine remote gespeicherte Prozedur vorhanden ist (es tritt kein Informationsfehler auf), stellt diese Funktion eine Methode zur Verfügung, mit der ermittelt werden kann, ob eine remote gespeicherte Prozedur vorhanden ist.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  