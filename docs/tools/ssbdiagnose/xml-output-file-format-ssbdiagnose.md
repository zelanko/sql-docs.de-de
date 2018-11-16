---
title: XML-Format der Ausgabedatei (Ssbdiagnose) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 32ab693accaa1bf89884053a2716dc89ca2b8256
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51292926"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Format der XML-Ausgabedatei (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn Sie das Hilfsprogramm **ssbdiagnose** mit der Option **-XML** ausführen, wird die Ausgabe als XML-Datei bereitgestellt. Die XML-Ausgabedatei enthält Headerinformationen und die Fehler, die in der analysierten [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Konfiguration oder Konversation gefunden wurden. Sie können eine Anwendung schreiben, um die in der Datei aufgelisteten Fehler zu analysieren oder einen entsprechenden Bericht zu erstellen. Die XML-Datei kann auch in einem allgemeinen XML-Editor wie XML Editor angezeigt werden.  
  
 Eine **ssbdiangose** -Ausgabedatei enthält ein DiagnosticInformation-Stammelement mit zwei untergeordneten Typen:  
  
-   Einem Banner-Element mit Headerinformationen  
  
-   Einem Issue-Element für jedes Problem, das von **ssbdiagnose**gemeldet wird  
  
## <a name="diagnosticinformation-root-element"></a>DiagnosticInformation-Stammelement  
  
-   [DiagnosticInformation-Element &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Banner-Element  
  
-   [Banner-Element &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Issue-Element  
  
-   [Issue-Element &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
