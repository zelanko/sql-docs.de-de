---
title: Arguments for External Tools
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 80b7d5e3eec617f82cb49b67a80d928cb3df9328
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75252225"
---
# <a name="arguments-for-external-tools"></a>Arguments for External Tools
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Argumente sind Variablen, für die die SQL Server Management Studio-Umgebung Werte bereitstellt, wenn ein externes Tool aus dem Menü **Extras** gestartet wird. Externe Tools, z. B. Editor, lassen sich mit dem Dialogfeld **Externe Tools** zum Menü **Extras** hinzufügen.  
  
In der folgenden Tabelle sind die Argumente für externe Tools aufgeführt.  
  
|Name|Argument|BESCHREIBUNG|  
|--------|------------|---------------|  
|**Elementpfad**|$(ItemPath)|Der vollständige Dateiname der aktuellen Quelle (definiert als Laufwerk + Pfad + Dateiname); leer, wenn ein Fenster aktiv ist, das nicht zur Quelle gehört.|  
|**Elementverzeichnis**|$(ItemDir)|Das Verzeichnis der aktuellen Quelle (definiert als Laufwerk + Pfad); leer, wenn ein Fenster aktiv ist, das nicht zur Quelle gehört.|  
|**Elementdateiname**|$(ItemFilename)|Der Dateiname der aktuellen Quelle (definiert als Dateiname); leer, wenn ein Fenster aktiv ist, das nicht zur Quelle gehört.|  
|**Elementerweiterung**|$(ItemExt)|Die Dateinamenerweiterung der aktuellen Quelle.|  
|**Aktuelle Zeile***|$(CurLine)|Die aktuelle Zeilenposition des Cursors im Editor.|  
|**Aktuelle Spalte***|$(CurCol)|Die aktuelle Spaltenposition des Cursors im Editor.|  
|**Aktueller Text***|$(CurText)|Der aktuelle Text (das Wort unter der aktuellen Cursorposition oder eine einzeilige Auswahl, sofern vorhanden).|  
|**Zielpfad**|$(TargetPath)|Der vollständige Dateiname des Ziels (definiert als Laufwerk + Pfad + Dateiname).|  
|**Zielverzeichnis**|$(TargetDir)|Das Verzeichnis des Ziels.|  
|**Zielname**|$(TargetName)|Der Dateiname des Ziels.|  
|**Zielerweiterung**|$(TargetExt)|Die Dateinamenerweiterung des Ziels.|  
|**Projektverzeichnis**|$(ProjDir)|Das Verzeichnis des aktuellen Projekts (definiert als Laufwerk + Pfad).|  
|**Projektdateiname**|$(ProjFileName)|Der Dateiname des aktuellen Projekts (definiert als Laufwerk + Pfad + Dateiname).|  
|**Projektmappenverzeichnis**|$(SolutionDir)|Das Verzeichnis der aktuellen Projektmappe (definiert als Laufwerk + Pfad).|  
|**Projektmappen-Dateiname**|$(SolutionFileName)|Der Dateiname der aktuellen Projektmappe (definiert als Laufwerk + Pfad + Dateiname).|  
  
\* Die aktuelle Zeile oder Spalte bzw. der aktuelle Text hängt von der Position des Cursors im Text-Editor ab, wie in der Statusleiste dargestellt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Externe Tools (Dialogfeld)](../ssms/external-tools-dialog-box.md)  
[Allgemeine Benutzeroberflächenelemente](../ssms/general-user-interface-elements.md)  
  
