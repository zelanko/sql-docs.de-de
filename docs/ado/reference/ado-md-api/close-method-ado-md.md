---
description: Close-Methode (ADO MD)
title: Close-Methode (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 666cf9afc4f6f5df5d3e950948e60bd644a45cdb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778269"
---
# <a name="close-method-ado-md"></a>Close-Methode (ADO MD)
Schließt ein geöffnetes Cellset.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie ein [Cellset](./cellset-object-ado-md.md) -Objekt mithilfe der **Close** -Methode schließen, werden die zugehörigen Daten, einschließlich der Daten in verknüpften [Zellen](./cell-object-ado-md.md)-, [Achsen](./axis-object-ado-md.md)-, [Positions](./position-object-ado-md.md) [-oder Element](./member-object-ado-md.md) Objekten, freigegeben. Durch das Schließen eines **Cellsets** wird es nicht aus dem Arbeitsspeicher entfernt. Sie können die Eigenschaften Einstellungen ändern und Sie später erneut öffnen. Wenn Sie ein Objekt vollständig aus dem Arbeitsspeicher entfernen möchten, legen Sie die Objekt Variable auf **Nothing**fest.  
  
 Sie können später die [Open](./open-method-ado-md.md) -Methode aufzurufen, um das CellSet mit derselben oder einer anderen Quell **Zeichenfolge** erneut zu öffnen. Während das **Cellset** -Objekt geschlossen wird, generiert das Abrufen von Eigenschaften oder das Aufrufen von Methoden, die auf die zugrunde liegenden Daten oder Metadaten verweisen, einen Fehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Axis-Objekt (ADO MD)](./axis-object-ado-md.md)   
 [Cell-Objekt (ADO MD)](./cell-object-ado-md.md)   
 [Member-Objekt (ADO MD)](./member-object-ado-md.md)   
 [Open-Methode (ADO MD)](./open-method-ado-md.md)   
 [Positions Objekt (ADO MD)](./position-object-ado-md.md)   
 [State-Eigenschaft (ADO MD)](./state-property-ado-md.md)