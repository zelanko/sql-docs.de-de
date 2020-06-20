---
title: Format der XML-Ausgabedatei (ssbdiagnose) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56758f15a3bd2a71221c936a80f7455d9e1c1cd9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057617"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Format der XML-Ausgabedatei (ssbdiagnose)
  Wenn Sie das Hilfsprogramm **ssbdiagnose** mit der Option **-XML** ausführen, wird die Ausgabe als XML-Datei bereitgestellt. Die XML-Ausgabedatei enthält Headerinformationen und die Fehler, die in der analysierten [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Konfiguration oder Konversation gefunden wurden. Sie können eine Anwendung schreiben, um die in der Datei aufgelisteten Fehler zu analysieren oder einen entsprechenden Bericht zu erstellen. Die XML-Datei kann auch in einem allgemeinen XML-Editor wie XML Editor angezeigt werden.  
  
 Eine **ssbdiangose** -Ausgabedatei enthält ein DiagnosticInformation-Stammelement mit zwei untergeordneten Typen:  
  
-   Einem Banner-Element mit Headerinformationen  
  
-   Einem Issue-Element für jedes Problem, das von **ssbdiagnose**gemeldet wird  
  
## <a name="diagnosticinformation-root-element"></a>DiagnosticInformation-Stammelement  
  
-   [DiagnosticInformation-Element &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Banner-Element  
  
-   [Banner-Element &#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Issue-Element  
  
-   [Issue-Element &#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
