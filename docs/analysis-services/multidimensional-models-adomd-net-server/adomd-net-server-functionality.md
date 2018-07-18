---
title: ADOMD.NET-Serverfunktionalität | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 003e50efa8ed21720410830a3d02134df15c3c97
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023777"
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
  
-   Sie rufen Sie eine gespeicherte Prozedur auf eigene mit MDX [Aufrufen](../../mdx/mdx-data-manipulation-call.md) Anweisung.  
  
-   Eine gespeicherte Prozedur unterstützt eine beliebige Anzahl von Parametern.  
  
-   Eine gespeicherte Prozedur kann einen Dataset Zurückgeben einer **IDataReader**, oder ein leeres Ergebnis.  
  
 Im folgenden Beispiel wird die fiktive gespeicherte Prozedur `FinalSalesNumbers` verwendet:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ADOMD.NET-Serverprogrammierung](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
