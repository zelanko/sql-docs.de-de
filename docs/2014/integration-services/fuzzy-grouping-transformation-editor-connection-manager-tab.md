---
title: Editor für Fuzzygruppierung Transformation (Registerkarte Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ae31e32645c902912b80545f599fd9d187f6b052
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378888"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>Transformations-Editor für Fuzzygruppierung (Registerkarte Verbindungs-Manager)
  Mithilfe der Registerkarte **Verbindungs-Manager** des Dialogfelds **Transformations-Editor für Fuzzygruppierung** können Sie eine vorhandene Verbindung auswählen oder eine neue erstellen.  
  
> [!NOTE]  
>  Auf dem von der Verbindung angegebenen Server muss [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ausgeführt werden. Die Transformation für Fuzzygruppierung erstellt temporäre Datenobjekte in tempdb, die so groß sein können wie die gesamte Eingabe der Transformation. Während die Transformation ausgeführt wird, werden Abfragen für diese temporären Objekte ausgegeben. Dadurch kann die Gesamtleistung des Servers beeinträchtigt werden.  
  
 Weitere Informationen zur Transformation für Fuzzygruppierung finden Sie unter [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Teilcache**  
 Wählen Sie einen vorhandenen OLE DB-Verbindungs-Manager aus dem Listenfeld aus, oder erstellen Sie mithilfe der Schaltfläche **Neu** eine neue Verbindung.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** eine neue Verbindung.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifizieren ähnlicher Datenzeilen mithilfe der Transformation für Fuzzygruppierung](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
