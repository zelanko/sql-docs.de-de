---
title: Benutzerdefinierte Eigenschaften der Rohdatendatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ebc381b7698340f1fa91e01d9b8520c01f9d3128
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329174"
---
# <a name="raw-file-custom-properties"></a>Benutzerdefinierte Eigenschaften der Rohdatendatei
  **Benutzerdefinierte Eigenschaften von Quellen**  
  
 Die Rohdatendatei-Quelle verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der Rohdatendatei-Quelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|und Beschreibung|  
|-------------------|---------------|-----------------|  
|AccessMode|Ganze Zahl (Enumeration)|Der zum Zugreifen auf die Rohdaten verwendete Modus. Die möglichen Werte sind **Dateiname** (0) und **Dateiname aus Variable** (1). Der Standardwert ist **Dateiname** (0).|  
|FileName|Zeichenfolge|Der Pfad und der Dateiname der Quelldatei.|  
  
 Die Ausgabe und die Ausgabespalten der Rohdatendatei-Quelle verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Raw File Source](../../integration-services/data-flow/raw-file-source.md).  
  
 **Benutzerdefinierte Eigenschaften von Zielen**  
  
 Das Rohdatendatei-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Rohdatendatei-Ziels. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|und Beschreibung|  
|-------------------|---------------|-----------------|  
|AccessMode|Ganze Zahl (Enumeration)|Ein Wert, der angibt, ob die FileName-Eigenschaft einen Dateinamen oder den Namen einer Variablen enthält, die einen Dateinamen enthält. Die möglichen Werte sind **Dateiname** (0) und **Dateiname aus Variable** (1).|  
|FileName|Zeichenfolge|Der Name der Datei, in die das Rohdatendatei-Ziel schreibt.|  
|WriteOption|Ganze Zahl (Enumeration)|Ein Wert, der angibt, ob das Rohdatendatei-Ziel eine vorhandene Datei mit demselben Namen löscht. Die Optionen sind **Immer erstellen** (0), **Einmal erstellen** (1), **Abschneiden und anfügen** (3) und **Anfügen** (2). Der Standardwert dieser Eigenschaft ist **Immer erstellen** (0).|  
  
> [!NOTE]  
>  Zum Anfügen müssen die Metadaten der angefügten Daten mit den Metadaten der in der Datei vorhandenen Daten übereinstimmen.  
  
 Die Eingabe und die Eingabespalten des Rohdatendatei-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Raw File Destination](../../integration-services/data-flow/raw-file-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
