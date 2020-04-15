---
title: dBASE Indizes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9300a38a0e36da771a238f73b77d3dda527334ae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307671"
---
# <a name="dbase-indexes"></a>dBASE-Indizes
Der ODBC dBASE-Treiber öffnet und aktualisiert dBASE IV-Indexdateien automatisch. Sie müssen das Dialogfeld **Indizes auswählen** verwenden, das über den ODBC-Datenquellenadministrator angezeigt wird, um dBASE III .ndx-Dateien dBASE-Dateien zuzuordnen.  
  
 Die folgenden Einschränkungen gelten für die Erstellung von dBASE-Indizes:  
  
-   Alle Spaltennamen müssen gültig sein.  
  
-   Alle Spalten müssen in derselben aufsteigenden oder absteigenden Reihenfolge sein.  
  
-   Die Länge einer einzelnen Textspalte muss kleiner als 100 Byte sein.  
  
-   Wenn mehr als eine Spalte vorhanden ist, müssen alle Spalten Textspalten sein, und die Summe der Spaltengrößen muss weniger als 100 Byte betragen.  
  
-   Memofelder können nicht indiziert werden.  
  
-   Für den aktuellen Satz von Feldern darf kein Index angegeben werden (d. h., doppelte Indizes sind nicht zulässig).  
  
-   Der Indexname muss mit der dBASE-Indexbenennungskonvention übereinstimmen. dBASE III erfordert, dass sich jeder Index in einer separaten Datei befindet, die jeweils eine .ndx-Erweiterung hat. In dBASE IV werden Indizes als Tag-Namen erstellt, die in einer einzelnen .mdx-Datei gespeichert werden. Die .mdx-Datei hat denselben Basisnamen wie die Datenbankdatei (z. B. Emp.mdx ist die Indexdatei für die Emp.dbf-Datenbank).  
  
-   dBASE definiert einen eindeutigen Index als einen Index, bei dem dem Index nur ein Datensatz aus einem Satz mit identischen Schlüsselwerten hinzugefügt wird.
