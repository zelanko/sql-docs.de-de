---
description: IsolationLevel-Eigenschaft
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f46199512521e6fe6fda6dc40fe894ba113c0229
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774719"
---
# <a name="isolationlevel-property"></a>IsolationLevel-Eigenschaft
Gibt die Isolationsstufe für ein [Verbindungs](./connection-object-ado.md) Objekt an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [IsolationLevelEnum](./isolationlevelenum.md) -Wert fest oder gibt ihn zurück. Der Standardwert ist **adxactreadcommit**.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **IsolationLevel** -Eigenschaft, um die Isolationsstufe eines **Verbindungs** Objekts festzulegen. Die-Einstellung wird erst beim nächsten Aufrufen der [BeginTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) -Methode wirksam. Wenn die Isolationsstufe, die Sie anfordern, nicht verfügbar ist, gibt der Anbieter möglicherweise die nächsthöhere Isolationsstufe zurück, ohne die **IsolationLevel** -Eigenschaft zu aktualisieren.  
  
 Die **IsolationLevel** -Eigenschaft ist Lese-/Schreibzugriff.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Wenn die **IsolationLevel** -Eigenschaft für ein Client seitiges **Verbindungs** Objekt verwendet wird, kann Sie nur auf **adxactunused**festgelegt werden. Da Benutzer mit getrennten recordsetobjekten in einem Client seitigen Cache arbeiten, treten möglicherweise multibenutzerprobleme auf. **Recordset** Wenn beispielsweise zwei verschiedene Benutzer versuchen, denselben Datensatz zu aktualisieren, gestattet der Remote Data Service einfach den Benutzer, der den Datensatz zuerst aktualisiert, auf "Win". Die Aktualisierungs Anforderung des zweiten Benutzers schlägt mit einem Fehler fehl.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](./connection-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [IsolationLevel-und Mode-Eigenschaften (Beispiel) (VB)](./isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel-und Mode-Eigenschaften (Beispiel) (VC + +)](./isolationlevel-and-mode-properties-example-vc.md)