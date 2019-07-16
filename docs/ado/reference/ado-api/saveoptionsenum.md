---
title: SaveOptionsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 807a8d7e5757a2caf76f100a1ae51c4a8a3f4e98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931148"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Gibt an, ob eine Datei erstellt oder überschrieben, wenn von gespeichert werden sollte eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt. Die Werte unter Umständen **AdSaveCreateNotExist** oder **AdSaveCreateOverWrite**...  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Standard. Erstellt eine neue Datei, wenn die Datei, wird angegeben die *FileName* Parameter noch nicht vorhanden.|  
|**adSaveCreateOverWrite**|2|Überschreibt die Datei mit den Daten aus der aktuell geöffneten **Stream** Objekt, wenn die Datei, durch angegeben die *Filename* Parameter bereits vorhanden ist. Wenn die Datei, wird angegeben die *Filename* Parameter ist nicht vorhanden, wird eine neue Datei erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
