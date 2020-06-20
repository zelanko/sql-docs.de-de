---
title: Beispiel für eine einfache XML-Eingabedatei (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 5b00e4eb-1742-43ec-98d8-d84216b6b840
author: stevestein
ms.author: sstein
ms.openlocfilehash: 00a973732c296cadd3d38a6ac7d9c50b7da3c90b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007623"
---
# <a name="simple-xml-input-file-sample-dta"></a>Beispiel für eine einfache XML-Eingabedatei (DTA)
  Kopieren Sie dieses Beispiel einer einfachen XML-Eingabedatei, und fügen Sie sie in Ihren XML-Editor oder Text-Editor ein, um sie für die Optimierung der Arbeitsauslastungen zu verwenden. Ersetzen Sie anschließend die Werte für die **Server**-, **Database**-, **Schema**-, **Table**-, **Workload**- und **TuningOptions** -Elemente durch die Werte für Ihre bestimmte Optimierungssitzung. Weitere Informationen zu den Attributen und untergeordneten Elementen, die Sie zusammen mit diesen Elementen verwenden können, finden Sie unter [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md). Im folgenden Beispiel wird nur eine Teilmenge der verfügbaren Optionen für Attribute und untergeordnete Elemente verwendet.  
  
## <a name="code"></a>Code  
 [!code-xml[InputFileSamples#SimpleXMLInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#simplexmlinputfile)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
