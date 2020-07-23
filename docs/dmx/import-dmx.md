---
title: Importieren (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1bddae4cf71b30a2a1365d0d5748170c0d5bac53
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969808"
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Lädt ein Miningmodell oder eine Miningstruktur aus einer ABF-Datei (Analysis Services Backup File) auf den Server.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Argumente  
 *filename*  
 Eine Zeichenfolge, die den Namen und den Speicherort der Datei angibt, die importiert werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn keine Objekte angegeben sind, wird der gesamte Inhalt der DMB-Datei geladen. Wenn die DMB-Datei eine Datenbank enthält, die auf dem Server nicht vorhanden ist, wird die Datenbank erstellt.  
  
 Sie müssen Datenbank- oder Serveradministrator sein, damit Sie Objekte exportieren bzw. importieren können.  
  
## <a name="import-from-file-example"></a>Beispiel für das Importieren aus einer Datei  
 Im folgenden Beispiel wird der gesamte Inhalt der Datei, die das Zuordnungsmodell und die Struktur enthält, auf den aktuellen Server importiert.  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Exportieren &#40;DMX-&#41;](../dmx/export-dmx.md)   
 [Exportieren und Importieren von Data Mining-Objekten](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
