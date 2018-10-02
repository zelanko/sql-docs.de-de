---
title: Abgeleitete Dimensionselemente (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumente
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ef72801df3a375822b83ec44389d7c7a5d18b634
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612128"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Abgeleitete Dimensionselemente (Assistent für langsam veränderliche Dimensionen)
  Mithilfe des Dialogfelds **Abgeleitete Dimensionselemente** können Sie Optionen für das Verwenden von abgeleiteten Elementen angeben. Abgeleitete Elemente sind vorhanden, wenn eine Faktentabelle auf noch nicht geladene Dimensionselemente verweist. Wenn für das abgeleitete Element Daten geladen sind, können Sie den vorhandenen Datensatz aktualisieren, aber keinen neuen erstellen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Unterstützung für abgeleitete Elemente aktivieren**  
 Wenn Sie abgeleitete Elemente aktivieren, müssen Sie eine der beiden folgenden Optionen auswählen.  
  
 **Alle Spalten mit einem Änderungstyp weisen den Wert NULL auf**  
 Gibt an, dass in allen Spalten des neuen Datensatzes des abgeleiteten Elements, die einen Änderungstyp aufweisen, NULL-Werte eingetragen werden.  
  
 **Mithilfe einer booleschen Spalte anzeigen, ob der aktuelle Datensatz ein abgeleitetes Element ist**  
 Gibt an, dass eine vorhandene boolesche Spalte verwendet wird, um anzuzeigen, dass der aktuelle Datensatz ein abgeleitetes Element ist.  
  
 **Indikator für abgeleitetes Element**  
 Wenn eine boolesche Spalte verwendet wird, um abgeleitete Elemente wie oben beschrieben anzuzeigen, wählen Sie die Spalte aus der Liste aus.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
