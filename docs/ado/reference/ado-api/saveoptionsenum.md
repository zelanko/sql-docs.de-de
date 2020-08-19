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
ms.openlocfilehash: 27284d84bb89c0e742c5166589a60fdc949e7b2e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442192"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Gibt an, ob eine Datei beim Speichern aus einem [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) erstellt oder überschrieben werden soll. Die Werte können " **adsavecreatenotexist** " oder " **adsavecreateüberschreibung**" lauten.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adsavecreatenotexist**|1|Standard. Erstellt eine neue Datei, wenn die durch den *filename* -Parameter angegebene Datei nicht bereits vorhanden ist.|  
|**adsavecreateüberschreibung**|2|Überschreibt die Datei mit den Daten aus dem momentan geöffneten Daten **Strom** Objekt, wenn die durch den *filename* -Parameter angegebene Datei bereits vorhanden ist. Wenn die durch den *filename* -Parameter angegebene Datei nicht vorhanden ist, wird eine neue Datei erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
