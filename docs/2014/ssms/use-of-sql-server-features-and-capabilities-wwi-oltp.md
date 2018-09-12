---
title: Argumente für externe Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84f8cf4caad7b08be1d3e88197c2c3240a3ad95e
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809116"
---
# <a name="arguments-for-external-tools"></a>Arguments for External Tools
  Argumente sind Variablen, für die die SQL Server Management Studio-Umgebung Werte bereitstellt, wenn ein externes Tool aus dem Menü **Extras** gestartet wird. Externe Tools, z. B. Editor, lassen sich mit dem Dialogfeld **Externe Tools** zum Menü **Extras** hinzufügen.  
  
 In der folgenden Tabelle sind die Argumente für externe Tools aufgeführt.  
  
|Name|Argument|Description|  
|----------|--------------|-----------------|  
|**Elementpfad**|$(ItemPath)|Der vollständige Dateiname der aktuellen Quelle (definiert als Laufwerk + Pfad + Dateiname); leer, wenn ein Fenster aktiv ist, das nicht zur Quelle gehört.|  
|**Elementverzeichnis**|$(ItemDir)|Das Verzeichnis der aktuellen Quelle (definiert als Laufwerk + Pfad); leer, wenn ein Fenster aktiv ist, das nicht zur Quelle gehört.|  
|**Elementdateiname**|$(ItemFilename)|Der Dateiname der aktuellen Quelle (definiert als Dateiname); leer, wenn ein Fenster aktiv ist, das nicht zur Quelle gehört.|  
|**Elementerweiterung**|$(ItemExt)|Die Dateinamenerweiterung der aktuellen Quelle.|  
|**Aktuelle Zeile** <sup>1</sup>|$(CurLine)|Die aktuelle Zeilenposition des Cursors im Editor.|  
|**Aktuelle Spalte**1|$(CurCol)|Die aktuelle Spaltenposition des Cursors im Editor.|  
|**Aktueller Text**1|$(CurText)|Der aktuelle Text (das Wort unter der aktuellen Cursorposition oder eine einzeilige Auswahl, sofern vorhanden).|  
|**Zielpfad**|$(TargetPath)|Der vollständige Dateiname des Ziels (definiert als Laufwerk + Pfad + Dateiname).|  
|**Zielverzeichnis**|$(TargetDir)|Das Verzeichnis des Ziels.|  
|**Zielname**|$(TargetName)|Der Dateiname des Ziels.|  
|**Zielerweiterung**|$(TargetExt)|Die Dateinamenerweiterung des Ziels.|  
|**Projektverzeichnis**|$(ProjDir)|Das Verzeichnis des aktuellen Projekts (definiert als Laufwerk + Pfad).|  
|**Projektdateiname**|$(ProjFileName)|Der Dateiname des aktuellen Projekts (definiert als Laufwerk + Pfad + Dateiname).|  
|**Projektmappenverzeichnis**|$(SolutionDir)|Das Verzeichnis der aktuellen Projektmappe (definiert als Laufwerk + Pfad).|  
|**Projektmappen-Dateiname**|$(SolutionFileName)|Der Dateiname der aktuellen Projektmappe (definiert als Laufwerk + Pfad + Dateiname).|  
  
 <sup>1</sup> die aktuelle Zeile, die aktuelle Spalte oder den aktuellen Text basiert auf der Position des Cursors im Text-Editor wie in der Statusleiste dargestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Externe Tools (Dialogfeld)](external-tools-dialog-box.md)   
 [Allgemeine Benutzeroberflächenelemente](general-user-interface-elements.md)  
  
  
