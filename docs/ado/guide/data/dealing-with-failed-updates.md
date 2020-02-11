---
title: Umgang mit fehlgeschlagenen Updates | Microsoft-Dokumentation
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
ms.openlocfilehash: d442a9c397ad184658f9101343e139697c9b3756
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925637"
---
# <a name="dealing-with-failed-updates"></a>Umgang mit fehlerhaften Updates
Wenn ein Update mit Fehlern beendet wird, hängt die Art und Weise, wie Sie die Fehler beheben, von der Art und dem Schweregrad der Fehler und der Logik der Anwendung ab. Wenn die Datenbank jedoch für andere Benutzer freigegeben wird, besteht ein typischer Fehler darin, dass ein anderer Benutzer das Feld ändert, bevor Sie dies tun. Diese Art von Fehler wird als Konflikt bezeichnet. ADO erkennt diese Situation und meldet einen Fehler.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Update Fehler vorliegen, werden Sie in einer Fehler Behandlungs Routine erfasst. Filtern Sie das Recordset mit der adFilterConflictingRecords-Konstante, sodass nur die in Konflikt stehenden Zeilen sichtbar sind. In diesem Beispiel besteht die Fehler Auflösungs Strategie darin, die vor-und Nachnamen des Autors (au_fname und au_lname) zu drucken.  
  
 Der Code zum Benachrichtigen des Benutzers für den Update Konflikt sieht wie folgt aus:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)
