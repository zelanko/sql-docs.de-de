---
title: Benutzerdefinierte Eigenschaften der Rohdatendatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 38acf6fd70bebf5033fde5dcf33fe5b2a6ac6722
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754822"
---
# <a name="raw-file-custom-properties"></a>Benutzerdefinierte Eigenschaften der Rohdatendatei
  **Benutzerdefinierte Eigenschaften von Quellen**  
  
 Die Rohdatendatei-Quelle verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der Rohdatendatei-Quelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Ganze Zahl (Enumeration)|Der zum Zugreifen auf die Rohdaten verwendete Modus. Die möglichen Werte sind `File name` (0) und `File name from variable` (1). Der Standardwert ist `File name` (0).|  
|FileName|Zeichenfolge|Der Pfad und der Dateiname der Quelldatei.|  
  
 Die Ausgabe und die Ausgabespalten der Rohdatendatei-Quelle verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Raw File Source](raw-file-source.md).  
  
 **Benutzerdefinierte Eigenschaften von Zielen**  
  
 Das Rohdatendatei-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Rohdatendatei-Ziels. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Ganze Zahl (Enumeration)|Ein Wert, der angibt, ob die FileName-Eigenschaft einen Dateinamen oder den Namen einer Variablen enthält, die einen Dateinamen enthält. Die Optionen sind `File name` (0) und `File name from variable` (1).|  
|FileName|Zeichenfolge|Der Name der Datei, in die das Rohdatendatei-Ziel schreibt.|  
|WriteOption|Ganze Zahl (Enumeration)|Ein Wert, der angibt, ob das Rohdatendatei-Ziel eine vorhandene Datei mit demselben Namen löscht. Die Optionen sind `Create Always` (0), `Create Once` (1), `Truncate and Append` (3) und `Append` (2). Der Standardwert dieser Eigenschaft ist `Create Always` (0).|  
  
> [!NOTE]  
>  Zum Anfügen müssen die Metadaten der angefügten Daten mit den Metadaten der in der Datei vorhandenen Daten übereinstimmen.  
  
 Die Eingabe und die Eingabespalten des Rohdatendatei-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Raw File Destination](raw-file-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](../common-properties.md)  
  
  
