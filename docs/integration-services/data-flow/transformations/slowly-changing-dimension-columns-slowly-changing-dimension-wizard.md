---
title: Spalten von langsam veränderlichen Dimensionen (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 92ae77d412ad318a01b437382b6d4557811c2b33
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919480"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Spalten von langsam veränderlichen Dimensionen (Assistent für langsam veränderliche Dimensionen)

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Im Dialogfeld **Spalten von langsam veränderlichen Dimensionen** können Sie für jede Spalte einer langsam veränderlichen Dimension einen Änderungstyp auswählen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Dimensionsspalten**  
 Wählen Sie eine Dimensionsspalte aus der Liste aus.  
  
 **Änderungstyp**  
 Wählen Sie ein **Festes Attribut**oder einen der beiden Typen von veränderlichen Attributen aus. Verwenden Sie **Festes Attribut** , wenn sich der Wert in einer Spalte nicht ändern soll; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] behandelt Änderungen dann als Fehler. Verwenden Sie **Veränderliches Attribut** , wenn vorhandene Werte von geänderten Werten überschrieben werden sollen. Verwenden Sie **Verlaufsattribut** , wenn geänderte Werte in neuen Datensätzen gespeichert werden sollen, während die vorigen Datensätze gleichzeitig als veraltet gekennzeichnet werden.  
  
 **Remove**  
 Wählen Sie eine Dimensionsspalte aus, und entfernen Sie sie aus der Liste der zugeordneten Spalten, indem Sie auf **Entfernen**klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
