---
title: Mithilfe von Seiten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6afd68ddf99799288939eeb0c6522275ec4d273f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704538"
---
# <a name="using-pages"></a>Verwenden von Seiten
Verwenden der **PageCount** Eigenschaft, um zu bestimmen, wie viele Seiten mit Daten in sind die **Recordset** Objekt. *Seiten* sind Gruppen von Datensätzen, deren Größe entspricht, der **PageSize** Einstellung der Eigenschaft. Auch wenn die letzte Seite unvollständig ist, da weniger als Datensätze die **PageSize** Wert, es zählt als eine zusätzliche Seite in der **PageCount** Wert. Wenn die **Recordset** Objekt unterstützt diese Eigenschaft nicht **PageCount** beträgt-1, um anzugeben, dass die **PageCount** nicht bestimmt werden.  
  
 Verwenden der **PageSize** Eigenschaft, um zu bestimmen, wie viele Datensätze eine logische Seite der Daten zu stellen. Eine Seitengröße festlegen, können Sie mit der **AbsolutePage** Eigenschaft, um zu den ersten Datensatz einer bestimmten Seite wechseln. Dies ist nützlich in Szenarien mit Web-Server, wenn Sie den Benutzer auf der Seite durch die Daten, zulassen, eine bestimmte Anzahl von Datensätzen zu einem Zeitpunkt anzuzeigen möchten.  
  
 Diese Eigenschaft kann zu einem beliebigen Zeitpunkt festgelegt werden, und der Wert für die Berechnung des Speicherort des ersten Datensatzes einer bestimmten Seite verwendet werden.  
  
 Verwenden der **AbsolutePage** Eigenschaft, um die Nummer der Seite zu identifizieren, auf dem der aktuelle Datensatz gespeichert ist. In diesem Fall muss der Anbieter die erforderlichen Funktionen für diese Eigenschaft zur Verfügung stehen unterstützen.  
  
 **AbsolutePage** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz den ersten Datensatz in ist die **Recordset**. Legen Sie diese Eigenschaft auf den ersten Datensatz einer bestimmten Seite verschoben. Abrufen der Gesamtanzahl von Seiten aus der **PageCount** Eigenschaft.
