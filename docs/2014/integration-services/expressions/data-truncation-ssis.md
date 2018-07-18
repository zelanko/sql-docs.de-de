---
title: Abschneiden von Daten (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5f80a51df610040e18dbdae7b1552c56d81cb084
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328090"
---
# <a name="data-truncation-ssis"></a>Abschneiden von Daten (SSIS)
  Ein Ausdruck kann versehentlich bewirken, dass Daten abgeschnitten werden. Dies ist in folgenden Situationen möglich:  
  
-   Zeichenfolgen. Beispielsweise gehen durch das Übersetzen von Zeichenfolgendaten mit dem DT_WSTR-Datentyp in eine Zeichenfolge mit der gleichen Länge (gemessen in Zeichen) und dem DT_STR-Datentyp Daten verloren, wenn die ursprüngliche Zeichenfolge Doppelbytezeichen enthält.  
  
-   Signifikante Ziffern. Beispielsweise das Umwandeln einer ganzen Zahl vom DT_I4-Datentyp in den DT_I2-Datentyp oder einer ganzen Zahl ohne Vorzeichen in eine ganze Zahl mit Vorzeichen.  
  
-   Insignifikante Ziffern. Beispielsweise das Umwandeln einer reellen Zahl vom DT_R8-Datentyp in den DT_R4-Datentyp oder einer ganzen Zahl vom DT_I4-Datentyp in den DT_R4-Datentyp.  
  
 Die Ausdrucksauswertung identifiziert explizite Umwandlungen, durch die Daten abgeschnitten werden könnten und gibt eine Warnung aus, wenn der Ausdruck analysiert wird. Beispielsweise werden Sie von der Ausdrucksauswertung gewarnt, falls eine Zeichenfolge mit 30 Zeichen in eine Zeichenfolge mit 20 Zeichen umgewandelt wird.  
  
> [!NOTE]  
>  Zur Laufzeit wird nicht überprüft, ob Daten abgeschnitten werden. Die Daten werden ohne Warnung abgeschnitten. Die meisten Datenadapter und Transformationen unterstützen jedoch Fehlerausgaben, die mit der Disposition von Fehlerzeilen umgehen können. Weitere Informationen zum Behandeln des Abschneidens von Daten finden Sie unter [Fehlerbehandlung in Daten](../data-flow/error-handling-in-data.md).  
  
  
