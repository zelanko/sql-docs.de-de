---
title: IsolationLevel-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2557c5859f10c7651cfc97fc3c849c00c26e985
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027920"
---
# <a name="isolationlevel-property"></a>IsolationLevel-Eigenschaft
Gibt die Ebene der Isolation für eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt eine [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) Wert. Der Standardwert ist **AdXactReadCommitted**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **IsolationLevel** die Isolation der festzulegenden Eigenschaft eine **Verbindung** Objekt. Die Einstellung wird wirksam, bis das nächste Mal Sie rufen die [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Methode. Wenn die Ebene der Isolation, die Sie anfordern, nicht verfügbar ist, kann der Anbieter der nächsten größere Maß an Isolation zurückgegeben, ohne Aktualisierung der **IsolationLevel** Eigenschaft.  
  
 Die **IsolationLevel** Eigenschaft schreibgeschützt ist.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Verbindung** -Objekt, das **IsolationLevel** Eigenschaft kann nur festgelegt werden **AdXactUnspecified**. Da Benutzer mit nicht verbundenen arbeiten **Recordset** Objekte auf einem clientseitigen Cache möglicherweise sind mehrere Benutzer Probleme. Z. B. wenn zwei verschiedene Benutzer versuchen, denselben Datensatz zu aktualisieren, können Remote Data Service einfach der Benutzer, der den Datensatz zuerst aktualisiert, um "win" an. Die zweite Anforderung des Benutzers Update schlägt mit einem Fehler fehl.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [IsolationLevel und Mode Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel und Mode Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
