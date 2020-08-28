---
description: Prompt – dynamische Eigenschaft (ADO)
title: Prompt Property-Dynamic (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: rothja
ms.author: jroth
ms.openlocfilehash: 67e8df1a59edecaf601f0ec4c5fd4b7782877e8d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990011"
---
# <a name="prompt-property-dynamic-ado"></a>Prompt – dynamische Eigenschaft (ADO)
Gibt an, ob der OLE DB Anbieter den Benutzer zur Eingabe von Initialisierungs Informationen auffordern soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [connectpromptenum](./connectpromptenum.md) -Wert fest und gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Eingabeaufforderung** ist eine dynamische Eigenschaft, die vom OLE DB Anbieter an die [Eigenschaften](./properties-collection-ado.md) Auflistung des [Verbindungs](./connection-object-ado.md) Objekts angehängt werden kann. Um Initialisierungs Informationen einzugeben, wird OLE DB Anbietern in der Regel ein Dialogfeld für den Benutzer angezeigt.  
  
 Dynamische Eigenschaften eines [Verbindungs](./connection-object-ado.md) Objekts gehen verloren, wenn die **Verbindung** geschlossen wird. Die **prompt** -Eigenschaft muss zurückgesetzt werden, bevor die **Verbindung** erneut geöffnet wird, um einen anderen Wert als den Standardwert zu verwenden.  
  
> [!NOTE]
>  Geben Sie nicht an, dass der Anbieter den Benutzer in Szenarios auffordern soll, in denen der Benutzer nicht auf das Dialogfeld reagieren kann. Der Benutzer kann beispielsweise nicht Antworten, wenn die Anwendung auf einem Server System statt auf dem Client des Benutzers ausgeführt wird oder wenn die Anwendung auf einem System ausgeführt wird, auf dem kein Benutzer angemeldet ist. In diesen Fällen wartet die Anwendung unbegrenzt auf eine Antwort und scheint eine Sperre zu erhalten.  
  
## <a name="usage"></a>Verwendung  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](./connection-object-ado.md)