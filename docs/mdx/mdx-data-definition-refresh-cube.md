---
title: REFRESH CUBE-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dafc13dda1f8ecab1400a88d1ca66eff5f317e43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63285081"
---
# <a name="mdx-data-definition---refresh-cube"></a>MDX-Datendefinition – REFRESH CUBE


  Aktualisiert den Clientcache für einen Cube.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Cubenamen bereitstellt.  
  
## <a name="remarks"></a>Hinweise  
 Für Clientanwendungen, die Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], diese Anweisung bewirkt, dass den Arbeitsspeicher, die zwischengespeichert werden, in der Clientanwendung mit dem Server synchronisiert werden. Erkennung und Update erfolgen zwar normalerweise automatisch, die zeitlichen Abstände hängen aber von den Einstellungen der Clientverbindungszeichenfolge ab. Die REFRESH CUBE-Anweisung aktualisiert die Daten sofort.  
  
 Bei Clientanwendungen, die eine Verbindung zu einem lokalen Cube besitzen, veranlasst die REFRESH CUBE-Anweisung die Neuerstellung der lokalen Cubedatei.  
  
> [!IMPORTANT]  
>  Auf dem Server gespeicherte benannte Mengen werden nicht aktualisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Datendefinitionsanweisungen &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
