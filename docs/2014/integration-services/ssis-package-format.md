---
title: SSIS-Paketformat | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f59ed0eee86f17fdda568caa5c1a1dc7252c6d9c
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66055351"
---
# <a name="ssis-package-format"></a>SSIS-Paketformat
  In der aktuellen Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]wurden wichtige Änderungen am Paketformat (DTSX-Datei) vorgenommen, um das Format besser lesbar zu machen und Pakete besser vergleichen zu können. Sie können auch Zusammenführen von Paketen, die keine in Konflikt stehenden Änderungen oder im Binärformat gespeicherte Änderungen enthalten.  
  
 Um das aktuelle DTSX-Paketdateiformat anzuzeigen, finden Sie unter [ \[MS-DTSX\]: Data Transformation Services-Paket XML-Dateiformatspezifikation](https://go.microsoft.com/fwlink/?LinkId=233251).  
  
 In der folgenden Liste werden die Dateiformatänderungen beschrieben. Um Codebeispiele für diese Änderungen anzuzeigen, finden Sie weitere Informationen unter [Paketformatänderungen in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=233255).  
  
-   Formatierungskonventionen wurden übernommen, um die DTSX-Datei besser lesbar und verständlicher zu machen.  
  
-   Das Format ist präziser. Separate Elemente für jede Eigenschaft wurden als Attribute beibehalten, mit Ausnahme von PackageFormatVersion. Attribute sind alphabetisch aufgeführt, und Eigenschaften, die über Standardwerte verfügen, werden nicht mehr beibehalten. Außerdem sind Elemente, die mehrmals angezeigt werden können, jetzt innerhalb eines übergeordneten Elements enthalten.  
  
-   Die meisten Objekte in einem Paket, auf die von anderen Objekten verwiesen werden kann, verfügen jetzt über ein im Paket-XML definiertes `refId`-Attribut. Statt persistenter Herkunfts-IDs wird die `refID` jetzt beibehalten. Herkunfts-IDs werden immer noch zur Laufzeit verwendet und neu generiert, wenn das Paket geladen wird.  
  
     Der `refId`-Wert ist eine eindeutige Zeichenfolge, die im Vergleich zu GUIDS oder ganzzahligen Werten lesbar und verständlich ist. Die Zeichenfolge ist ähnlich wie Pfadwerte, die in vorherigen Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]für die Paketkonfigurationen verwendet wurden.  
  
     Wenn Sie Änderungen zwischen zwei Versionen eines Pakets zusammenführen, kann die `refId` in Such-/Ersetzungsvorgängen verwendet werden, um sicherzustellen, dass alle Verweise auf dieses Objekt ordnungsgemäß aktualisiert wurden.  
  
-   Die Layoutinformationen sind in einem CDATA-Abschnitt enthalten.  
  
-   Anmerkungen werden in Klartext beibehalten. Dies erleichtert es, die Informationen für die automatisierte Generierung der Dokumentation zu extrahieren.  
  
  
