---
title: Ausgeben von Befehlen an die zugrunde liegende Datenanbieter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bc30f35ebfe2ddc59e9ef1404253e9bc99d62e0
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82757806"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter
Alle Befehle, die nicht mit Shape beginnen, werden an den Datenanbieter übermittelt. Dies entspricht dem Ausgeben eines Shape-Befehls im Format "Shape {Provider Command}". Diese Befehle müssen *kein* **Recordset**enthalten. Beispielsweise ist "Shape {DROP TABLE MyTable}" ein vollständig gültiger SHAPE-Befehl, vorausgesetzt, der Datenanbieter unterstützt DROP TABLE.  
  
 Diese Funktion ermöglicht es, dass sowohl normale Anbieter Befehle als auch Shape-Befehle dieselbe Verbindung und Transaktion gemeinsam verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Daten Strukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
