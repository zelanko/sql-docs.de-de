---
title: SetServiceAccount-Methode (SqlService-Klasse) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 74f296fd52640c950d7d2c4b227a1c3aedb17df7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046848"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>SetServiceAccount-Methode (SqlService-Klasse)
  Versucht, den Benutzernamen und das Kennwort zu ändern, unter denen die Dienstinstanz ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
#### <a name="parameters"></a>Parameter  
 *ServiceStartName*  
 Ein Zeichenfolgenwert, der den Kontonamen angibt, unter dem der Dienst ausgeführt wird. Abhängig vom Diensttyp könnte der Kontoname die Form "DomainName\Username" aufweisen. Wenn er ausgeführt wird, wird der Dienstprozess in einer von zwei Formen protokolliert:  
  
-   Wenn das Konto zur integrierten Domäne gehört, kann "\Username" angegeben werden.  
  
-   Wenn NULL angegeben wird, wird der Dienst als **LocalSystem** -Konto angemeldet.  
  
 Bei Kernel- oder Systemtreibern enthält *StartName* den Treiberobjektnamen, entweder "\FileSystem\Rdr" oder "\Driver\Xns", den das E/A-System zum Laden des Gerätetreibers verwendet. Bei Angabe von NULL wird der Treiber mit einem Standardobjektnamen ausgeführt, den das E/A-System auf Basis des Dienstnamens erstellt, zum Beispiel "DWDOM\Admin".  
  
 *ServiceStartPassword*  
 Ein Zeichenfolgenwert, der das Kennwort für den Kontonamen im *StartName* -Parameter angibt. Geben Sie NULL an, wenn Sie das Kennwort nicht ändern. Geben Sie eine leere Zeichenfolge an, wenn der Dienst kein Kennwort besitzt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird. Jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  