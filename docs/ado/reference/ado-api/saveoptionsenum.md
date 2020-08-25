---
description: SaveOptionsEnum
title: Saveoptionsenum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: edac11f61b003307703ec13daed8022b8af31bae
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777559"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Gibt an, ob eine Datei beim Speichern aus einem [Streamobjekt](./stream-object-ado.md) erstellt oder überschrieben werden soll. Die Werte können " **adsavecreatenotexist** " oder " **adsavecreateüberschreibung**" lauten.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adsavecreatenotexist**|1|Standard. Erstellt eine neue Datei, wenn die durch den *filename* -Parameter angegebene Datei nicht bereits vorhanden ist.|  
|**adsavecreateüberschreibung**|2|Überschreibt die Datei mit den Daten aus dem momentan geöffneten Daten **Strom** Objekt, wenn die durch den *filename* -Parameter angegebene Datei bereits vorhanden ist. Wenn die durch den *filename* -Parameter angegebene Datei nicht vorhanden ist, wird eine neue Datei erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [SaveToFile-Methode](./savetofile-method.md)