---
description: Open-Methode (ADO MD)
title: Open-Methode (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5c7b403ed89ae9933b4169af4e53921205318ccd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986231"
---
# <a name="open-method-ado-md"></a>Open-Methode (ADO MD)
Ruft die Ergebnisse einer mehrdimensionalen Abfrage ab und gibt die Ergebnisse in einem [Cellset](./cellset-object-ado-md.md)zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Eine **Variante** , die eine gültige mehrdimensionale Abfrage ergibt, z. b. eine MDX-Abfrage (Multidimensional Expression). Das *Source* -Argument entspricht der [Source](./source-property-ado-md.md) -Eigenschaft. Weitere Informationen zu MDX finden Sie im [OLE DB für die Online Analytical Processing (OLAP)-](/previous-versions/windows/desktop/ms717005(v=vs.85)) Dokumentation im Microsoft Data Access Components SDK.  
  
 *ActiveConnection*  
 Optional. Eine **Variante** , die zu einer Zeichenfolge ausgewertet wird, die entweder einen gültigen ADO- [Verbindungs](../ado-api/connection-object-ado.md) Objektvariablen Namen oder eine Definition für eine Verbindung angibt. Das *ActiveConnection* -Argument gibt die Verbindung an, in der das [Cellset](./cellset-object-ado-md.md) -Objekt geöffnet werden soll. Wenn Sie eine Verbindungs Definition für dieses Argument übergeben, öffnet ADO mit den angegebenen Parametern eine neue Verbindung. Das *ActiveConnection* -Argument entspricht der [ActiveConnection](./activeconnection-property-ado-md.md) -Eigenschaft.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Open** -Methode generiert einen Fehler, wenn einer der Parameter ausgelassen wird und der zugehörige Eigenschafts Wert nicht festgelegt wurde, bevor versucht wird, das **Cellset**zu öffnen.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cellset-Beispiel (VB)](./cellset-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADO MD)](./activeconnection-property-ado-md.md)   
 [Close-Methode (ADO MD)](./close-method-ado-md.md)   
 [Verbindungs Objekt (ADO)](../ado-api/connection-object-ado.md)   
 [Source-Eigenschaft (ADO MD)](./source-property-ado-md.md)   
 [State-Eigenschaft (ADO MD)](./state-property-ado-md.md)