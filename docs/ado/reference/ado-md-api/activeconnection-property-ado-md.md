---
title: ActiveConnection-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6ad7cdfdfc3c08175faf0584f2ae5069fcd39acb
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719018"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection-Eigenschaft (ADO MD)
Gibt an, welche ADO [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt das aktuelle Cellset oder Katalog derzeit gehört.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Variant** , das eine Zeichenfolge, die eine Verbindung zu definieren oder **Verbindung** Objekt. Der Standardwert ist leer.  
  
## <a name="remarks"></a>Hinweise  
 Sie können diese Eigenschaft festlegen, um eine gültige ADO **Verbindung** Objekt oder eine gültige Verbindungszeichenfolge. Wenn diese Eigenschaft auf eine Verbindungszeichenfolge festgelegt ist, erstellt der Anbieter einen neuen **Verbindung** Objekt mit dieser Definition und öffnet die Verbindung.  
  
 Bei Verwendung der *ActiveConnection* Argument der [öffnen](../../../ado/reference/ado-md-api/open-method-ado-md.md) Methode zum Öffnen eine [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekt, die **ActiveConnection** Eigenschaft wird erben Sie den Wert des Arguments.  
  
 Festlegen der **ActiveConnection** Eigenschaft eine [Katalog](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) -Objekt **nichts** frei die zugehörigen Daten, einschließlich der Daten in die [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) Sammlung und allen verknüpften [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md), und [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekte. Schließen einer **Verbindung** -Objekt, das zum Öffnen verwendet wurde eine **Katalog** hat dieselbe Wirkung wie das Festlegen der **ActiveConnection** Eigenschaft **nichts**.  
  
 Ändern die Standarddatenbank für die Verbindung auf die verwiesen wird durch die **ActiveConnection** Eigenschaft eine **Katalog** Objekt erklärt den Inhalt des der **Katalog**.  
  
 Wird ein Fehler auftreten, wenn Sie versuchen, Sie ändern die **ActiveConnection** -Eigenschaft für ein offenes **Cellset** Objekt.  
  
> [!NOTE]
>  In Visual Basic Denken Sie daran, mit der **festgelegt** Schlüsselwort beim Festlegen der **ActiveConnection** Eigenschaft, um eine **Verbindung** Objekt. Wenn Sie weglassen der **festgelegt** -Schlüsselwort, Sie tatsächlich Festlegen der **ActiveConnection** -Eigenschaft gleich den **Verbindung** Standardeigenschaft des Objekts,  **"ConnectionString"** . Der Code funktioniert. Erstellen Sie jedoch eine zusätzliche Verbindung zu der Datenquelle, die Auswirkungen auf die Leistung haben können.  
  
 Wenn Sie den MSOLAP-Datenanbieter verwenden, legen Sie die Datenquelle in einer Verbindungszeichenfolge auf einen Servernamen ein, und legen Sie den ersten Katalog auf den Namen des Katalogs aus der Datenquelle. Verbindung mit einer Cubedatei, die von einem Server getrennt ist, legen Sie den Speicherort auf den vollständigen Pfad zu der. CUB-Datei. In beiden Fällen wird den Anbieter auf der Name des Anbieters fest. Die folgende Zeichenfolge verwendet beispielsweise den MSOLAP-Anbieter für die Verbindung mit einem Katalog mit dem Namen Bobs Video Store auf einem Server mit dem Namen **Servername**:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 Die folgende Zeichenfolge eine Verbindung mit einer lokalen Cubedatei an der Position C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub her:  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Katalogobjekt (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Cellset-Beispiel (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open-Methode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
