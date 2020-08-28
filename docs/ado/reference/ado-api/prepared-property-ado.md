---
description: Prepared-Eigenschaft (ADO)
title: Vorbereitete Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 7352d21467061a38bd7e2443ecb52fdb59bd7696
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990041"
---
# <a name="prepared-property-ado"></a>Prepared-Eigenschaft (ADO)
Gibt an, ob eine kompilierte Version eines [Befehls](./command-object-ado.md) vor der Ausführung gespeichert werden soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **booleschen** Wert fest, der, wenn er auf **true**festgelegt ist, angibt, dass der Befehl vorbereitet werden soll, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **vorbereitete** Eigenschaft, damit der Anbieter eine vorbereitete (oder kompilierte) Version der Abfrage speichert, die in der [CommandText](./commandtext-property-ado.md) -Eigenschaft vor der ersten Ausführung eines [Befehls](./command-object-ado.md) Objekts angegeben ist. Dadurch kann die erste Ausführung eines Befehls verlangsamt werden. Nachdem der Anbieter jedoch einen Befehl kompiliert hat, verwendet der Anbieter die kompilierte Version des Befehls für alle nachfolgenden Ausführungen, was zu einer verbesserten Leistung führt.  
  
 Wenn die Eigenschaft auf **false**gesetzt ist, führt der Anbieter das **Befehls** Objekt direkt aus, ohne eine kompilierte Version zu erstellen.  
  
 Wenn der Anbieter die Befehls Vorbereitung nicht unterstützt, gibt er möglicherweise einen Fehler zurück, wenn diese Eigenschaft auf **true**festgelegt ist. Wenn der Anbieter keinen Fehler zurückgibt, wird die Anforderung zum Vorbereiten des Befehls einfach ignoriert und die **vorbereitete** Eigenschaft auf **false**festgelegt.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine vorbereitete Eigenschaft (VB)](./prepared-property-example-vb.md)   
 [Prepared-Eigenschaft – Beispiel (VC++)](./prepared-property-example-vc.md)