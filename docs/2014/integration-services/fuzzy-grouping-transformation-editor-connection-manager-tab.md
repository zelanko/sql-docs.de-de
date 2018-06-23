---
title: Für die Fuzzysuche Transformations-Editor (Registerkarte "Verbindungs-Manager") | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b3327aa60445bf3cb75d43d04652566cb886e331
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050352"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>Transformations-Editor für Fuzzygruppierung (Registerkarte Verbindungs-Manager)
  Mithilfe der Registerkarte **Verbindungs-Manager** des Dialogfelds **Transformations-Editor für Fuzzygruppierung** können Sie eine vorhandene Verbindung auswählen oder eine neue erstellen.  
  
> [!NOTE]  
>  Auf dem von der Verbindung angegebenen Server muss [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ausgeführt werden. Die Transformation für Fuzzygruppierung erstellt temporäre Datenobjekte in tempdb, die so groß sein können wie die gesamte Eingabe der Transformation. Während die Transformation ausgeführt wird, werden Abfragen für diese temporären Objekte ausgegeben. Dadurch kann die Gesamtleistung des Servers beeinträchtigt werden.  
  
 Weitere Informationen zur Transformation für Fuzzygruppierung finden Sie unter [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Teilcache**  
 Wählen Sie einen vorhandenen OLE DB-Verbindungs-Manager aus dem Listenfeld aus, oder erstellen Sie mithilfe der Schaltfläche **Neu** eine neue Verbindung.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** eine neue Verbindung.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifizieren ähnlicher Datenzeilen mithilfe der Transformation für Fuzzygruppierung](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  