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
manager: craigg
ms.openlocfilehash: 288168b2a4b47c8a73612bd89a6f1987e2808475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788761"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Gibt an, ob eine Datei erstellt oder überschrieben, wenn von gespeichert werden sollte eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt. Die Werte unter Umständen **AdSaveCreateNotExist** oder **AdSaveCreateOverWrite**...  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Standard. Erstellt eine neue Datei, wenn die Datei, wird angegeben die *FileName* Parameter noch nicht vorhanden.|  
|**adSaveCreateOverWrite**|2|Überschreibt die Datei mit den Daten aus der aktuell geöffneten **Stream** Objekt, wenn die Datei, durch angegeben die *Filename* Parameter bereits vorhanden ist. Wenn die Datei, wird angegeben die *Filename* Parameter ist nicht vorhanden, wird eine neue Datei erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
