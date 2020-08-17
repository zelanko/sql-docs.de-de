---
description: dBASE-Indizes
title: dBASE-Indizes | Microsoft-Dokumentation
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
ms.openlocfilehash: 30a6390f0e187cc063b2a650af2da3b9fcc87d57
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340956"
---
# <a name="dbase-indexes"></a>dBASE-Indizes
Der ODBC-dBase-Treiber öffnet und aktualisiert automatisch dBASE IV-Indexdateien. Sie müssen das durch den ODBC-Datenquellen-Administrator angezeigte Dialogfeld **Indizes auswählen** verwenden, um dBASE III. NDX-Dateien mit dBASE-Dateien zuzuordnen.  
  
 Die folgenden Einschränkungen gelten für die Erstellung von dBASE-Indizes:  
  
-   Alle Spaltennamen müssen gültig sein.  
  
-   Alle Spalten müssen sich in der gleichen aufsteigenden oder absteigenden Reihenfolge befinden.  
  
-   Die Länge einer einzelnen Text Spalte muss kleiner als 100 Bytes sein.  
  
-   Wenn mehr als eine Spalte vorhanden ist, müssen alle Spalten Textspalten sein, und die Summe der Spaltengrößen muss kleiner als 100 Bytes sein.  
  
-   Memo Felder können nicht indiziert werden.  
  
-   Für den aktuellen Satz von Feldern darf kein Index angegeben werden (d. h. doppelte Indizes sind nicht zulässig).  
  
-   Der Indexname muss der Benennungs Konvention für den dBASE-Index entsprechen. dBASE III erfordert, dass sich jeder Index in einer separaten Datei mit der Erweiterung. NDX befinden muss. In dBASE IV werden Indizes als Tagnamen erstellt, die in einer einzelnen MDX-Datei gespeichert werden. Die MDX-Datei weist den gleichen Basis Namen wie die Datenbankdatei auf (z. b. ist "EMP. MDX" die Indexdatei für die Datenbank "EMP. dbf").  
  
-   dBASE definiert einen eindeutigen Index als einen, bei dem nur ein Datensatz aus einer Menge mit identischen Schlüsselwerten dem Index hinzugefügt wird.
