---
title: Recordsetziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cdf206c36bdb9956c6444fe6b22f229ef4fdf6e0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805022"
---
# <a name="recordset-destination"></a>Recordsetziel
  Das Recordsetziel erstellt ein ADO-Recordset im Arbeitsspeicher und füllt es auf. Die Form des Recordsets wird durch die Eingabe im Recordsetziel zur Entwurfszeit definiert.  
  
## <a name="configuration-of-the-recordset-destination"></a>Konfiguration des Recordsetziels  
 Zum Konfigurieren des Recordsetziels geben Sie die Variable an, die das ADO-Recordset speichert.  
  
 Zur Laufzeit wird ein ADO-Recordset in die Variable des Typs „Object“ geschrieben, die in der „VariableName“-Eigenschaft des „Recordset“-Ziels angegeben ist. Die Variable stellt dann das Recordset außerhalb des Datenflusses zur Verfügung, wo es von Skripts und sonstigen Paketelementen verwendet werden kann.  
  
 Diese Quelle hat nur eine Eingabe. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Allgemeine Eigenschaften](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Recordsetziels](recordset-destination-custom-properties.md)  
  
 Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Verwenden eines Recordsetziels](recordset-destination.md)  
  
  
