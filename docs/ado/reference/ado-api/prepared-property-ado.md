---
description: Prepared-Eigenschaft (ADO)
title: Vorbereitete Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
author: rothja
ms.author: jroth
ms.openlocfilehash: 050651b5c25fcfdfa6723936659b9a11772c2b03
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442692"
---
# <a name="prepared-property-ado"></a>Prepared-Eigenschaft (ADO)
Gibt an, ob eine kompilierte Version eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) vor der Ausführung gespeichert werden soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **booleschen** Wert fest, der, wenn er auf **true**festgelegt ist, angibt, dass der Befehl vorbereitet werden soll, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **vorbereitete** Eigenschaft, damit der Anbieter eine vorbereitete (oder kompilierte) Version der Abfrage speichert, die in der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft vor der ersten Ausführung eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts angegeben ist. Dadurch kann die erste Ausführung eines Befehls verlangsamt werden. Nachdem der Anbieter jedoch einen Befehl kompiliert hat, verwendet der Anbieter die kompilierte Version des Befehls für alle nachfolgenden Ausführungen, was zu einer verbesserten Leistung führt.  
  
 Wenn die Eigenschaft auf **false**gesetzt ist, führt der Anbieter das **Befehls** Objekt direkt aus, ohne eine kompilierte Version zu erstellen.  
  
 Wenn der Anbieter die Befehls Vorbereitung nicht unterstützt, gibt er möglicherweise einen Fehler zurück, wenn diese Eigenschaft auf **true**festgelegt ist. Wenn der Anbieter keinen Fehler zurückgibt, wird die Anforderung zum Vorbereiten des Befehls einfach ignoriert und die **vorbereitete** Eigenschaft auf **false**festgelegt.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine vorbereitete Eigenschaft (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Prepared-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
