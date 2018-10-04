---
title: XML-Format der Ausgabedatei (Ssbdiagnose) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6644b8da77f8ebb6e4e8d6b6fc23ce5d9e356dd6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070830"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Format der XML-Ausgabedatei (ssbdiagnose)
  Wenn Sie das Hilfsprogramm **ssbdiagnose** mit der Option **-XML** ausführen, wird die Ausgabe als XML-Datei bereitgestellt. Die XML-Ausgabedatei enthält Headerinformationen und die Fehler, die in der analysierten [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Konfiguration oder Konversation gefunden wurden. Sie können eine Anwendung schreiben, um die in der Datei aufgelisteten Fehler zu analysieren oder einen entsprechenden Bericht zu erstellen. Die XML-Datei kann auch in einem allgemeinen XML-Editor wie XML Editor angezeigt werden.  
  
 Eine **ssbdiangose** -Ausgabedatei enthält ein DiagnosticInformation-Stammelement mit zwei untergeordneten Typen:  
  
-   Einem Banner-Element mit Headerinformationen  
  
-   Einem Issue-Element für jedes Problem, das von **ssbdiagnose**gemeldet wird  
  
## <a name="diagnosticinformation-root-element"></a>DiagnosticInformation-Stammelement  
  
-   [DiagnosticInformation-Element &#40;Ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Banner-Element  
  
-   [Banner-Element &#40;Ssbdiagnose&#41;](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Issue-Element  
  
-   [Issue-Element &#40;Ssbdiagnose&#41;](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
