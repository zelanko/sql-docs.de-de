---
title: ADOMD.NET-Serverfunktionalität | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 622a7c51bfd6c2a8a9defba70a412967a48dee50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056355"
---
# <a name="adomdnet-server-functionality"></a>ADOMD.NET-Serverfunktionalität
  Alle ADOMD.NET-Serverobjekte ermöglichen schreibgeschützten Zugriff auf die Daten und Metadaten auf dem Server. Verwenden Sie das ADOMD.NET-Serverobjektmodell, um Daten und Metadaten abzurufen, da das Serverobjektmodell keine Schemarowsets unterstützt.  
  
 Mit ADOMD.NET-Serverobjekten können Sie eine benutzerdefinierte Funktion (UDF) oder eine gespeicherte Prozedur zum Erstellen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Diese prozessinternen Methoden werden durch Abfrageanweisungen aufgerufen, die in Sprachen wie Multidimensional Expressions (MDX), Data Mining Extensions (DMX) oder SQL erstellt wurden. Diese prozessinternen Methoden stellen zudem zusätzliche Funktionen bereit, die nicht den Wartezeiten eines Netzwerks unterworfen sind.  
  
> [!NOTE]  
>  Das <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand>-Objekt unterstützt nur DMX.  
  
## <a name="what-is-a-udf"></a>Was ist eine UDF?  
 Ein *UDF* ist eine Methode, die über die folgenden Eigenschaften verfügt:  
  
-   Sie können die UDF im Kontext einer Abfrage aufrufen.  
  
-   Die UDF unterstützt eine beliebige Anzahl von Parametern.  
  
-   Die UDF kann zahlreiche Datentypen zurückgeben.  
  
 Im folgenden Beispiel wird die fiktive UDF `FinalSalesNumber` verwendet:  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a>Was ist eine gespeichert Prozedur?  
 Ein *gespeicherte Prozedur* ist eine Methode, die über die folgenden Eigenschaften verfügt:  
  
-   Sie rufen Sie eine gespeicherte Prozedur auf eigene mit MDX [Aufrufen](/sql/mdx/mdx-data-manipulation-call) Anweisung.  
  
-   Eine gespeicherte Prozedur unterstützt eine beliebige Anzahl von Parametern.  
  
-   Eine gespeicherte Prozedur kann ein Dataset, einen `IDataReader` oder ein leeres Ergebnis zurückgeben.  
  
 Im folgenden Beispiel wird die fiktive gespeicherte Prozedur `FinalSalesNumbers` verwendet:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ADOMD.NET-Serverprogrammierung](adomd-net-server-programming.md)  
  
  
