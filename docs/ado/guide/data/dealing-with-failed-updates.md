---
title: Umgang mit fehlerhaften Updates | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ba4b4189691bf907b3ad67db91a8534268a8ec0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616428"
---
# <a name="dealing-with-failed-updates"></a>Umgang mit fehlerhaften Updates
Wenn ein Update mit Fehlern abgeschlossen ist, hängt wie Sie die Fehler beheben von der Art und Schweregrad der Fehler und die Logik Ihrer Anwendung. Wenn die Datenbank für andere Benutzer freigegeben ist, ist ein typischer Fehler jedoch, dass eine andere Person auf das Feld ändert, vor dem Ausführen. Diese Art von Fehler ist einen Konflikt wird aufgerufen. ADO erkennt dies und meldet einen Fehler.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Update-Fehler vorliegen, werden sie in einer Fehlerbehandlungsroutine aufgefangen werden. Filtern Sie das Recordset mit der Konstante vorliegt, sodass nur die in Konflikt stehende Zeilen angezeigt werden. In diesem Beispiel die Fehlerbehebung Strategie ist es lediglich des Autors des ersten und letzten Namen (Au_fname und Au_lname).  
  
 Der Code aus, um dem Benutzer, die Update-Konflikt aufmerksam sieht folgendermaßen aus:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)
