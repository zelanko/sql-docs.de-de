---
description: Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter
title: Ausgeben von Befehlen an die zugrunde liegende Datenanbieter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: d4f1db51d54b69bf42fe185d30b78df57b89df39
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980431"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter
Alle Befehle, die nicht mit Shape beginnen, werden an den Datenanbieter übermittelt. Dies entspricht dem Ausgeben eines Shape-Befehls im Format "Shape {Provider Command}". Diese Befehle müssen *kein* **Recordset**enthalten. Beispielsweise ist "Shape {DROP TABLE MyTable}" ein vollständig gültiger SHAPE-Befehl, vorausgesetzt, der Datenanbieter unterstützt DROP TABLE.  
  
 Diese Funktion ermöglicht es, dass sowohl normale Anbieter Befehle als auch Shape-Befehle dieselbe Verbindung und Transaktion gemeinsam verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Daten Strukturierung](./data-shaping-example.md)   
 [Formale Form Grammatik](./formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](./shape-commands-in-general.md)