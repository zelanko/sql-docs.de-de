---
description: DefaultDatabase-Eigenschaft
title: DefaultDatabase-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
author: rothja
ms.author: jroth
ms.openlocfilehash: 86a8b283880f0765100c5a36eb63954f232c565a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974191"
---
# <a name="defaultdatabase-property"></a>DefaultDatabase-Eigenschaft
Gibt die Standarddatenbank für ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen einer vom Anbieter verfügbaren Datenbank ergibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **DefaultDatabase** -Eigenschaft, um den Namen der Standarddatenbank für ein bestimmtes **Verbindungs** Objekt festzulegen oder zurückzugeben.  
  
 Wenn eine Standarddatenbank vorhanden ist, verwenden SQL-Zeichen folgen möglicherweise eine nicht qualifizierte Syntax für den Zugriff auf Objekte in dieser Datenbank. Für den Zugriff auf Objekte in einer anderen Datenbank als der, die in der **DefaultDatabase** -Eigenschaft angegeben ist, müssen Sie Objektnamen mit dem gewünschten Datenbanknamen qualifizieren. Bei der Verbindung schreibt der Anbieter Standarddaten Bankinformationen in die **DefaultDatabase** -Eigenschaft. Einige Anbieter lassen nur eine Datenbank pro Verbindung zu. in diesem Fall können Sie die **DefaultDatabase** -Eigenschaft nicht ändern.  
  
 Einige Datenquellen und Anbieter unterstützen diese Funktion möglicherweise nicht und geben möglicherweise einen Fehler oder eine leere Zeichenfolge zurück.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Diese Eigenschaft ist für ein Client seitiges **Verbindungs** Objekt nicht verfügbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Anbieter und DefaultDatabase-Eigenschaften (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider- und DefaultDatabase-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
