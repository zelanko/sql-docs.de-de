---
title: Format der XML-Ausgabedatei
description: In SQL Server kann das Hilfsprogramm „ssbdiagnose“ seine Ausgabe als XML-Datei bereitstellen. Erstellen Sie eine Anwendung, um Fehler zu analysieren oder zu melden oder sie in einem XML-Editor anzuzeigen.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 1b039d5441ed39c85a8cf1e9468eddfe165aad1c
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83150508"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
