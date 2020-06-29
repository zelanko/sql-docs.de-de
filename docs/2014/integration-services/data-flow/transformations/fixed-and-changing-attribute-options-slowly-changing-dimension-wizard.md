---
title: Optionen für feste und veränderliche Attribute (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df654cd97b343179828ebd94dea40eacc90e003d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430567"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Optionen für feste und veränderliche Attribute (Assistent für langsam veränderliche Dimensionen)
  Geben Sie mithilfe des Dialogfelds **Optionen für feste und veränderliche Attribute** an, wie auf Änderungen bei festen und veränderlichen Attributen reagiert werden soll.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Feste Attribute**  
 Geben Sie für feste Attribute an, ob der Task fehlschlagen soll, wenn bei einem festen Attribut eine Änderung festgestellt wird.  
  
 **Veränderliche Attribute**  
 Geben Sie für veränderliche Attribute an, ob der Task zusätzlich zu aktuellen Datensätzen veraltete oder abgelaufene Datensätze ändern soll, wenn bei einem veränderlichen Attribut eine Änderung erkannt wird. Ein abgelaufener Datensatz ist ein Datensatz, der durch eine Änderung in einem Verlaufsattribut (eine Änderung vom Typ 2) durch einen neueren Datensatz ersetzt wurde. Das Auswählen dieser Option verursacht möglicherweise zusätzliche Verarbeitungsanforderungen für ein im relationalen Data Warehouse erstelltes mehrdimensionales Objekt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
