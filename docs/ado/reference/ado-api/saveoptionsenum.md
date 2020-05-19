---
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
ms.openlocfilehash: 3423d215fa4a52286509769bb2ac0b75d2283a02
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755841"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Gibt an, ob eine Datei beim Speichern aus einem [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) erstellt oder überschrieben werden soll. Die Werte können " **adsavecreatenotexist** " oder " **adsavecreateüberschreibung**" lauten.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adsavecreatenotexist**|1|Standard. Erstellt eine neue Datei, wenn die durch den *filename* -Parameter angegebene Datei nicht bereits vorhanden ist.|  
|**adsavecreateüberschreibung**|2|Überschreibt die Datei mit den Daten aus dem momentan geöffneten Daten **Strom** Objekt, wenn die durch den *filename* -Parameter angegebene Datei bereits vorhanden ist. Wenn die durch den *filename* -Parameter angegebene Datei nicht vorhanden ist, wird eine neue Datei erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [SaveToFile-Methode](../../../ado/reference/ado-api/savetofile-method.md)
