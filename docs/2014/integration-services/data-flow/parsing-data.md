---
title: Analysieren von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b0de9927de85a161261d55de1de9ad9dcc46e4be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805442"
---
# <a name="parsing-data"></a>Analysieren von Daten
  Mit Datenflüssen in Paketen werden Daten zwischen heterogenen Datenspeichern extrahiert und geladen, die eine Reihe von standardmäßigen und benutzerdefinierten Datentypen verwenden können. In einem Datenfluss werden mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Quellen Daten extrahiert, Zeichenfolgendaten analysiert und Daten in einen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentyp konvertiert. Nachfolgende Transformationen können Daten analysieren, um sie in einen anderen Datentyp zu konvertieren oder um Spaltenkopien mit anderen Datentypen zu erstellen. Mit Ausdrücken in Komponenten können außerdem Argumente und Operanden in andere Datentypen umgewandelt werden. Wenn die Daten in einen Datenspeicher geladen werden, kann schließlich das Ziel die Daten analysieren, um sie in einen vom Ziel verwendeten Datentyp zu konvertieren. Weitere Informationen finden Sie unter [Integration Services Datentypen](integration-services-data-types.md).  
  
## <a name="types-of-parsing"></a>Analysetypen  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bietet zwei Arten der Analyse von Daten zu konvertieren: Die schnelle Analyse und Standardanalyse.  
  
-   Die schnelle Analyse besteht aus schnellen, einfachen Analyseroutinen, die keine gebietsschemaspezifischen Datentypkonvertierungen unterstützen, sondern nur die am häufigsten verwendeten Datums- und Zeitformate. Weitere Informationen finden Sie unter [Fast Parse](../fast-parse.md).  
  
-   Die Standardanalyse enthält viele Analyseroutinen, die alle Datentypkonvertierungen der APIs für die automatische Datentypkonvertierung in Oleaut32.dll und Ole2dsip.dll unterstützen. Weitere Informationen finden Sie unter [Standard Parse](../standard-parse.md).  
  
  
