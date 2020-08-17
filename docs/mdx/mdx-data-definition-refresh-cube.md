---
description: MDX-Datendefinition – REFRESH CUBE
title: REFRESH CUBE-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 05ae95c97ae21d3b8ff7b4e457cf3ddf8cc38989
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387054"
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
  
## <a name="remarks"></a>Bemerkungen  
 Bei Client Anwendungen, die mit einer Instanz von verbunden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sind, bewirkt diese Anweisung, dass der in der Client Anwendung zwischengespeicherte Arbeitsspeicher mit dem Server synchronisiert wird. Erkennung und Update erfolgen zwar normalerweise automatisch, die zeitlichen Abstände hängen aber von den Einstellungen der Clientverbindungszeichenfolge ab. Die REFRESH CUBE-Anweisung aktualisiert die Daten sofort.  
  
 Bei Clientanwendungen, die eine Verbindung zu einem lokalen Cube besitzen, veranlasst die REFRESH CUBE-Anweisung die Neuerstellung der lokalen Cubedatei.  
  
> [!IMPORTANT]  
>  Auf dem Server gespeicherte benannte Mengen werden nicht aktualisiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
